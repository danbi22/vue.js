<template>
  <section>
    <ul>
        <!-- v-for를 사용할 때 :key="키값"을 넣어주어야한다. Vue.js의 최적화 기법 -->
        <!-- v-for="(텍스트 값, 인덱스) in 뽑아올 객체나 자료구조 " :key="텍스트 값" 
            인덱스는 v-for에서 제공하는 변수 내부적으로 인덱스를 부여한다.-->
        <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
            <!-- i태그는 아이콘을 넣을 때 사용 -->
            <i class="checkBtn fa fa-check" aria-hidden="true"></i>
            {{ todoItem }}
            <!-- @click="실행할 메서드"
                v-on:click=""과 동일한 동작을 한다. -->
            <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                <i class="fa fa-trash-o" aria-hidden="true"></i>
            </span>
        </li>
    </ul>
  </section>
</template>

<script> 
export default {
    props: ['propsdata'],
    // data와 methods 속성이 정의되었기 때문에 데이터(todoItems)에 접근 할 수 있다.
    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
            // // localStorage.removeItem()는 로컬스토리지의 데이터를 삭제하는 메서드
            // localStorage.removeItem(todoItem);
            // // splice() : 배열의 특정 인덱스에서 부여한 숫자만큼의 인덱스를 삭제. 해당 배열을 깊은복사하여 값을 변경
            // // slice()와 혼동하면 안됨 slice는 새로운 배열을 반환하기 때문에 Reactivity 적용이 되지 않음.
            // this.todoItems.splice(index, 1);
        }
    }
}
</script>

<style>
    ul {
        /* 목록 아이템의 스타일을 지정 */
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }

    li {
        /* 비율 기준의 레이아웃 방식인 flex로 지정 */
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 0.5rem;
        margin: 0.5rem 0;
        padding: 0 0.09rem;
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