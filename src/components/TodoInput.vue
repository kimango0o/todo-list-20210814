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
                /*
                    [ Application → Local Storage → http://localhost:8080 ]
                     - Storage.setItem(key: string, value: string)
                     : 왼 쪽에 key, 오른쪽에 value 저장
                */
                localStorage.setItem(this.newTodoItem, this.newTodoItem);
            }
        }
    }
</script>

<style scoped>

</style>