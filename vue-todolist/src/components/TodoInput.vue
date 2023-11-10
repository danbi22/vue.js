<template>
  <div class="inputBox shadow">
    <!-- v-model="component메서드" 
        화면에 입력된 값을 인스턴스의 데이터 속성과 연결하여 갱신되게한다.

        v-on:keyup.enter="component메서드"
        인풋박스에서 enter키를 누르고 올라왔을 때 메서드가 실행되게 한다.
    -->
    <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo"/>
    <span class="addContainer" v-on:click="addTodo">
        <!-- fa fa-plus
            어썸 아이콘의 '+' 아이콘을 추가

            aria-hidden='true'
            시각장애인에게 화면을 읽어주는 화면판독기가 불필요한 정보인 해당 태그를 무시하는 속성이다.
        -->
        <i class="addBtn fa fa-plus" aria-hidden="true"></i>
    </span>
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
            // 인풋 박스의 입력 값이 있을 때만 저장
            // newTodoItem만 입력할 경우 해당 메서드 내에서 newTodoItem이 존재해야한다.
            // 인스턴스의 데이터인 newTodoItem을 가져오고 싶으면 this.newTodoItem을 붙여 data의 newTodoItem을 가리켜줘야한다.
            if (this.newTodoItem !== "") {

                // 인풋 박스에 입력된 텍스트의 앞뒤 공백 문자열 제거
                var value = this.newTodoItem && this.newTodoItem.trim();

                // value를 app인스턴스로 올린다.
                this.$emit('addTodo', value);
                
                // 인풋 박스의 입력 값을 초기화
                // 단일 책임 원칙 하나의 메서드는 주된 한 가지의 일만 처리해야한다. 결합도를 낮추고 재사용성을 높인다.
                // this.clearInput();의 기능을 메서드로 빼서 단일 책임 원칙을 지켰다. 
                this.clearInput();
            }
            // localStorage.setItem(키, 값); 로컬스토리지에 키, 값 형태로 저장한다.
            // localStorage.setItem(this.newTodoItem, this.newTodoItem);
            // console.log(this.newTodoItem);
        },
        clearInput() {
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
    input:focus {
        /* 선 스타일 지정 */
        outline: none;
    }

    .inputBox {
        background: white;
        height: 50px;
        /* 인풋 박스에 입력되는 텍스트의 중앙 정렬을 위해 설정 */
        line-height: 50px;
        /* 인풋 박스의 둥근 테두리 속성 설정 */
        border-radius: 50px;
    }

    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }

    .addContainer {
        /* 할 일 추가 버튼이 표시될 위치 정의 */
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }

    .addBtn {
        color: white;
        /* 할 일 추가 아이콘의 수직 정렬 정의 */
        vertical-align: middle;
    }
</style>