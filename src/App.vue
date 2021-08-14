<template>
  <div id="app">
    <!-- script에서 설정한 컴포넌트 태그 추가 -->
    <TodoHeader></TodoHeader>
    <!--
      할 일 추가 버튼을 클릭했을 때, App 컴포넌트로 이벤트를 전달할 수 있게
      v-on 디렉티브 추가
    -->
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <!--
      뷰 데이터에서 선언한 todoItems 속성을
      todoList 컴포넌트에 pops로 전달
    -->
    <TodoList v-bind:propsdata="todoItems"></TodoList>
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
    props: ['propsdata'],
    data() {
      return {
        // 데이터 속성 todoItems 선언
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
      addTodo(todoItem) {
        /*
          로컬 스토리지에 데이터를 추가하는 로직
           - todoItem : TodoInput 컴포넌트에서 올려 보낸 할 일 텍스트 값
           - 이 값을 로컬 스토리지에 저장하고, App 컴포넌트의 todoItems 데이터 속성에도 추가
           ( 뷰 데이터 )
        */
        localStorage.setItem(todoItem, todoItem);
        this.todoItems.push(todoItem);
      }
    },
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