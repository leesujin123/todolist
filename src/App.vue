<template>
    <div id="app">
      <div>
        TodoList 수진
      </div>
      <div>
        inputBox + add Button<br />
        <input type="text" v-model="todoItem" placeholder="할 일을 입력해주세요" >
        <button @click="add">추가</button>
      </div>
      <div>
        List 출력 및 삭제버튼 만들기 + 상태변경 할수있게 만들기<br />
        <ul >
          <li v-for="(item,index) in todoItems" :key="index" >
            <input type="checkbox"  v-model="item.complete">
            {{ index }} | {{ item.todo }}  | {{item.complete}}
            <button @click="del(item, index)">삭제</button>
          </li>
        </ul>
        <hr/>
        <ul >
          <li v-for="(item,index) in completeTodo" :key="index" >
            <input type="checkbox"  v-model="item.complete">
            {{ index }} | {{ item.todo }}  | {{item.complete}}
            <button @click="del(item, index)">삭제</button>
          </li>
        </ul>
        <hr/>
        <ul>
          <li v-for="(item,index) in nonCompleteTodo" :key="index" >
            <input type="checkbox"  v-model="item.complete">
            {{ index }} | {{ item.todo }}  | {{item.complete}}
            <button @click="del(item, index)">삭제</button>
          </li>
        </ul>
      </div>
      <div>
        전체삭제버튼 만들기<br />
        <button @click="allDel">전체 삭제</button>
      </div>
  </div>
</template>

<script>

export default {
  data(){
    return{
      toggle: true,
      todoItem: "",
      todoItems: [],
    }
  },
  methods: {
    add() {
      if(this.todoItem !== "") {
        console.log(this.todoItem);
        this.todoItems.push({
          todo: this.todoItem,
          complete: false,
        })
        this.todoItem = "";
      }else {
        alert("값을 입력하세요")
      }
    },
    del(todoItem,index){
      this.todoItems.splice(index,1);
      console.log(this.todoItems);
    },
    allDel(){
      this.todoItems.splice(0);
      console.log(this.todoItems);
    }
  },
  computed:{
    completeTodo() {
      return this.todoItems.filter(item => item.complete)
    },
    nonCompleteTodo() {
      return this.todoItems.filter(item => !item.complete)

    }


  }

}
</script>
