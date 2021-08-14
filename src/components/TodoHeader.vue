<!--
    TodoHeader.vue
     - 사용 용도 : 애플리케이션 이름 표시
-->

<template>
    <!-- [ 애플리케이션 제목 추가하기 ] -->
    <header>
        <h1>
            <a href="javascript:void(0);">ㅎ ㅐ ㅇ ㅑ ㅎ ㅏ ㄹ ㅇ ㅣ ㄹ</a>
        </h1>
    </header>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
    /* 어비 슬기로운생활체 */
    @font-face {
        font-family: 'UhBeeSeulvely';
        src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_five@.2.0/UhBeeSeulvely.woff') format('woff');
        font-weight: normal;
        font-style: normal;
    }

    /* 제목 부분 */
    h1 {
        font-family: 'UhBeeSeulvely';
        color: #2F3B52;
        font-weight: 900;
        margin: 2.5rem 0 1.5rem;
    }

    a:hover, a:focus { animation-duration: 3s; animation-name: rainbowLink; animation-iteration-count: infinite; } 
        @keyframes rainbowLink {     
        0% { color: #ff2a2a; }
        15% { color: #ff7a2a; }
        30% { color: #ffc52a; }
        45% { color: #43ff2a; }
        60% { color: #2a89ff; }
        75% { color: #202082; }
        90% { color: #6b2aff; } 
        100% { color: #e82aff; }
    }

    a {
        color: black;
        text-decoration: none;
    }
</style>