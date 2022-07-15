<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <AddItem :upgive="upgive"/>
        <TodoList :todos="todos" @deleteItem="(e) => removeItem(e)"/>
        <ManageAll :todos="todos" @checkall='checkAll' @clearCompleted='clearCompleted'/>
      </div>
    </div>
  </div>
</template>

<script>
import AddItem from './components/AddItem.vue'
import TodoList from './components/TodoList.vue'
import ManageAll from './components/ManageAll.vue'

export default {
  name: "App",
  data() {
    return {
      todos: [
        {id: '001', content: 'Coding', done: false},
        {id: '002', content: 'Eating', done: true},
        {id: '003', content: 'Sleeping', done: true},
      ]
    }
  },
  methods: {
    upgive(x) {
      this.todos.unshift(x)
    },
    checkAll(check) {
      this.todos.forEach(element => {
        element.done = !check;
      })
    },
    removeItem(e) {
      this.todos = this.todos.filter(element => element.id !== e);
    },
    clearCompleted() {
      this.todos.forEach(element => {
        if (element.done)
          this.removeItem(element.id);
      });
    }
  },  
  components: {
    AddItem,
    TodoList,
    ManageAll
  }
}
</script>

<style>
  body {
    background: #fff;
  }
  .btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0, 1px, 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }
  .btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
    font-size: large;
  }
  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }
  .btn:focus {
    outline: none;
  }
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>