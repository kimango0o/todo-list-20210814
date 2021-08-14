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