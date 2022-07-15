<template>
  <div class="todo-header">
    <input type="text" placeholder="Write down your todo, press Enter to add to the list below" @keyup.enter="addTodo"/>
  </div>
</template>

<script>
import {nanoid} from 'nanoid'
export default {
  name: "AddItem",
  props: ['upgive'],
  methods: {
    addTodo(e) {
      if (!e.target.value.trim()) return;
      const newTodo = {id: nanoid(), content: e.target.value, done:false};
      this.upgive(newTodo)
      e.target.value = ''
    }
  },
}
</script>

<style scoped>
  .todo-header input {
    width: 560px;
    height: 28px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 4px 7px;
  }

  .todo-header input:focus {
    outline: none;
    border-color: rgba(82, 168, 236, 0.8);
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
  }

</style>