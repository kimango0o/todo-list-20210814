<template>
    <section>
        <ul>
            <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
    export default {
        data() {
            return {
                // localStorage의 데이터를 담을 빈 배열 선언
                todoItems: []
            }
        },
        created() {
            // localStorage에 저장된 데이터가 한 개라도 있는 경우
            if (localStorage.length > 0) {
                /*
                    localStorage에 저장된 모든 아이템을 한 번에 불러오는
                    API는 없기 때문에 반복문으로 아이템을 모두 불러와야 한다.
                */
                for (var i = 0; i < localStorage.length; i++) {
                    // push() : 배열의 끝 요소에 배열 아이템을 하나씩 추가하는 자바스크립트 내장 API
                    this.todoItems.push(localStorage.key(i));
                }
            }
        },
        methods: {
            removeTodo(todoItem, index) {
                // 로컬 스토리지의 데이터를 삭제
                localStorage.removeItem(todoItem);
                /*
                    splice() : 배열의 특정 인덱스를 삭제하는 API
                    할 일 삭제 처리
                */
                this.todoItems.splice(index, 1);
            }
        }
    }
</script>

<style scoped>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }

    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }

    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>