<template>
  <div id="app">
    <!-- script에서 설정한 컴포넌트 태그 추가 -->
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
  /*
    특정 컴포넌트에서 다른 위치에 있는 컴포넌트의 내용을 불러오는 방법
    import 불러온 파일의 내용이 담길 객체 from '불러올 파일 위치'
      - 경로 헷갈리지 말고 정확하게 입력하기
  */
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter.vue'

  export default {
    // 지역 컴포넌트 등록
    components: {
      // template 에서 태그로 사용할 이름 : import 에서 설정한 객체
      'TodoHeader': TodoHeader,
      'TodoInput': TodoInput,
      'TodoList': TodoList,
      'TodoFooter': TodoFooter
    }
  }
</script>

<style>
  /* 애플리케이션 전체의 배경 색 및 텍스트 정렬 방식 정의 */
  body {
    text-align: center;
    background-color: #f9fabea9;
  }

  /* Input 박스의 테두리 모양 정의 */
  input {
    border-style: groove;
    width: 200px;
  }

  button {
    border-style: groove;
  }

  /* 그림자 정의 */
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.3);
  }
</style>