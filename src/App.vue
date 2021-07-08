<template>
  <div id="app">
    <div>
      TodoList 수진
    </div>
    <div >
      inputBox + add Button<br />
      <input type="text" v-model="todoItem" placeholder="할 일을 입력해주세요" >
      <button @click="add">추가</button>
    </div>
    <div>
      List 출력 및 삭제버튼 만들기 + 상태변경 할수있게 만들기<br />
      <ul id="List">
        <li v-for="(todoList,index) in todoItems" :key="todoList" >
          {{ index }} | {{ todoList }}
          <button @click="del(todoList, index)">삭제</button>
        </li>
      </ul>
    </div>
    <div>
      전체삭제버튼 만들기<br />
      <button @click="Alldel">전체 삭제</button>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return{
      todoItem: "",
      todoItems: [
          'a',
          'b',
          'c'
      ]
    }
  },
  methods: {
    add() {
      console.log(this.todoItem);
      this.todoItems.push(this.todoItem);
      this.todoItem = "";
    },
    del(todoItem,index){
      this.todoItems.splice(index,1);
      console.log(this.todoItems);
    }
  }

}
</script>

<style>

</style>
