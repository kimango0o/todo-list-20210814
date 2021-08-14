<template>
    <div class="clearAllContainer shadow">
        <span class="clearAllBtn" @click="clearTodo">
            Clear All
        </span>
    </div>
</template>

<script>
    export default {
        methods: {
            // 로컬 스토리지의 데이터를 모두 삭제
            clearTodo() {
                localStorage.clear();
            }
        }
    }
</script>

<style scoped>
    .clearAllContainer {
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background-color: white;
        border-radius: 5px;
        margin: 0 auto;
    }

    .clearAllBtn {
        color: red;
        display: block;
    }
</style>