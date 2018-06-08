<template>
  <div class="container">

    <div id="fixedStuff">
      <h1 id="appTitle">What's on?</h1>
      <input id="todoInput" @keyup.enter="addTodo" type="text" v-model="newTodo" placeholder="Add upcoming thing">
    </div>

    <div id="allTodos">

      <div v-for="(todo, index) in todos" class="todoCardOpen" :key="index">
        <h1>{{ todo }}</h1>
        <button @click="changeToDoing(index)" id="startBtn">Start</button>
      </div>

      <div v-for="(todo, index) in doing" class="todoCardDoing" :key="index">
        <h1>{{ todo }}</h1>
        <button @click="changeToDone(index)" id="endBtn">End</button>
      </div>

      <div v-for="(todo, index) in done" class="todoCardDone" :key="index">
        <h1>{{ todo }}</h1>
        <button @click="deleteTodo(index)" id="deleteBtn">Delete</button>
      </div>

    </div>

  </div>
</template>

<script>
export default {
  data: () => ({
    todos: [],
    doing: [],
    done: [],
    newTodo: ''
  }),
  methods: {
    addTodo() {
      if(this.newTodo !== '') this.todos.push(this.newTodo);
      this.newTodo = ''
    },
    changeToDoing(val) {
      this.doing.push(this.todos[val]);
      this.todos.splice(val, 1);
    },
    changeToDone(val) {
      this.done.push(this.doing[val]);
      this.doing.splice(val, 1);
    },
    deleteTodo(val) {
      this.done.splice(val, 1);
    }
  }
}
</script>

<style>
  .container {
    padding: 0 15px 0 15px;
    height: 100%;
  }

  html::-webkit-scrollbar{
    width: 0px;
    background: none;
  }

  #appTitle{
    margin-left: 20%;
    color: aliceblue;
    font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    text-transform: uppercase;
    position: fixed;
  }

  #fixedStuff{
    margin-top: -150px;
    position: fixed;
  }

  #allTodos{
    margin-top: 150px;
  }

  .todoCardOpen {
    height: 80px;
    width: 95%;
    margin: 0 auto 15px auto;
    background: rgba(10, 66, 219, 0.5);
    border-radius: 15px;
  }

  .todoCardOpen > h1 {
    color: rgba(255, 255, 255, 0.8);
    font-family: 'Courier New', Courier, monospace;
    font-size: 20px;
    padding-top: 25px;
    margin-left: 20px;
  }

  .todoCardDoing {
    height: 80px;
    width: 95%;
    margin: 0 auto 15px auto;
    background: rgba(255, 196, 0, 0.521);
    border-radius: 15px;
  }

  .todoCardDoing > h1 {
    color: rgba(255, 255, 255, 0.8);
    font-family: 'Courier New', Courier, monospace;
    font-size: 20px;
    padding-top: 25px;
    margin-left: 20px;
  }

  .todoCardDone {
    height: 80px;
    width: 95%;
    margin: 0 auto 15px auto;
    background: rgba(0, 255, 0, 0.466);
    border-radius: 15px;
  }

  .todoCardDone > h1 {
    color: rgba(255, 255, 255, 0.8);
    font-family: 'Courier New', Courier, monospace;
    font-size: 20px;
    padding-top: 25px;
    margin-left: 20px;
  }

  #todoInput {
    margin-top: 80px;
    width: 80%;
    margin-left: 5%;
    margin-bottom: 15px;
    height: 40px;
    background: none;
    border: none;
    font-size: 20px;
    border-bottom: 2px solid rgba(255, 255, 255, 0.4);
    position: fixed;
  }

  #todoInput:focus {
    outline: none;
    border-bottom: 2px solid greenyellow;
    caret-color: azure;
    color: aliceblue;
  }

  #startBtn {
    margin-left: 70%;
    display: block;
    margin-top: -30px;
    position: absolute;
    background: rgba(10, 66, 219, 0.9);
    color: white;
    border: none;
    background: grey;
    border-radius: 15px;
    box-shadow: white 20px;
  }

   #startBtn:focus{
     outline: none;
     color: rgba(255, 255, 255, 0.8);
   }

    #startBtn:hover{
      cursor: pointer;
      background: rgba(10, 66, 219, 0.5);
    }

    #endBtn {
    margin-left: 70%;
    display: block;
    margin-top: -30px;
    position: absolute;
    background: rgba(10, 66, 219, 0.9);
    color: white;
    border: none;
    background: grey;
    border-radius: 15px;
    box-shadow: white 20px;
  }

   #endBtn:focus{
     outline: none;
     color: rgba(255, 255, 255, 0.8);
   }

  #endBtn:hover{
    cursor: pointer;
    background: rgba(10, 66, 219, 0.5);
  }

  #deleteBtn {
    margin-left: 70%;
    display: block;
    margin-top: -30px;
    position: absolute;
    background: rgba(10, 66, 219, 0.9);
    color: white;
    border: none;
    background: grey;
    border-radius: 15px;
    box-shadow: white 20px;
  }

   #deleteBtn:focus{
     outline: none;
     color: rgba(255, 255, 255, 0.8);
   }

  #deleteBtn:hover{
    cursor: pointer;
    background: rgba(10, 66, 219, 0.5);
  }
</style>
