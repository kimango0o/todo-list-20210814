<template>
    <div class="inputBox shadow">
        <!--
            v-model 속성
             - 입력 값이 자동으로 뷰 데이터 속성에 연결된다.
             ( 뷰 데이터 = script단에 있는 data() )
            
            v-model은 어떻게 동작할까?
             - v-bind와 v-on 기능의 조합으로 동작한다.
             - v-bind : 뷰 인스턴스의 데이터 속성을 해당 HTML 요소에 연결할 때 사용
             - v-on : 해당 HTML 요소의 이벤트를 뷰 인스턴스의 로직과 연결할 때 사용
             - 사용자 이벤트에 의해 실행된 뷰 메서드( methods ) 함수의 첫 번째 인자에는 해당 이벤트가 들어온다.

             ( 아래 코드 해석 )
             사용자가 입력한 값을 v-model 속성을 통해 data() newTodoItem 속성과 연결한다.
             <input> v-on:keyup.enter : Input 창에 키를 올리고 Enter 키를 눌렀을 때 작용하는 이벤트
              - addTodo 함수를 실행시켜준다.
             <span> v-on:click : 아이콘을 클릭했을 때 작용하는 이벤트
              - addTodo 함수를 실행시켜준다.
        -->
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do"
            v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3>
            <span slot="footer" @click="showModal = false">
                할 일을 입력해주세요!
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>

<script>
    import Modal from './common/Modal.vue'

    export default {
        data() {
            return {
                newTodoItem: '',
                showModal: false
            }
        },
        methods: {
            addTodo() {
                // Input 박스의 입력 값이 있을 때만 저장하기
                if (this.newTodoItem !== "") {
                    // Input 박스에 입력된 텍스트의 앞 뒤 공백 문자열 제거
                    var value = this.newTodoItem && this.newTodoItem.trim();
                    /*
                        [ Application → Local Storage → http://localhost:8080 ]
                        - Storage.setItem(key: string, value: string)
                         : 왼 쪽에 key, 오른쪽에 value 저장
                        localStorage.setItem(value, value);
                    */
                   /*
                        이벤트를 전달할 때 할 일 텍스트 값인 value 객체를 인자 값으로 전달
                   */
                    this.$emit('addTodo', value);
                    // Input 박스의 입력 값을 초기화
                    this.clearInput();
                } else {
                    this.showModal = !this.showModal;
                }
            },
            // Input 박스의 입력 값을 초기화 하기 위해 생성한 함수
            clearInput() {
                this.newTodoItem = '';
            }
        },
        components: {
            Modal: Modal
        }
    }
</script>

<style scoped>
    /* 할 일을 입력하는 Input 박스의 선 스타일 지정 */
    input:focus {
        outline: none;
    }

    /* Input 박스 설정 */
    .inputBox {
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }

    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }

    /* 클릭 이벤트 태그 ( span ) 설정 */
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }

    /* 아이콘 설정 */
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>