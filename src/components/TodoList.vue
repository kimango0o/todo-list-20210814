<template>
    <section>
        <ul>
            <li>할 일 1</li>
            <li>할 일 2</li>
            <li>할 일 3</li>
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
        }
    }
</script>

<style scoped>

</style>