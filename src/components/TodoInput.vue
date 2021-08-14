<template>
    <div>
        <input type="text" v-model="newTodoItem">
        <button v-on:click="addTodo">추가</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                newTodoItem: ''
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
                    */
                    localStorage.setItem(value, value);
                    // Input 박스의 입력 값을 초기화
                    this.clearInput();
                }
            },
            // Input 박스의 입력 값을 초기화 하기 위해 생성한 함수
            clearInput() {
                this.newTodoItem = '';
            }
        }
    }
</script>

<style scoped>

</style>