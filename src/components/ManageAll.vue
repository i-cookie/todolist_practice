<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" :checked="allChecked" @change="checkAll(allChecked)"/>
    </label>
    <span>
      {{countDone}} / {{todos.length}} completed.
    </span>
    <button class="'btn btn-danger" @click="clearCompleted">clear completed items</button>
  </div>
</template>

<script>
export default {
  name: "ManageAll",
  props: ['todos'],
  emits: ['checkall', 'clearCompleted'],
  data() {
    return {
      
    }
  },
  methods: {
    checkAll(check) {
      this.$emit("checkall", check);
    },
    clearCompleted() {
      this.$emit("clearCompleted");
    }
  },
  computed: {
    countDone() {
      let temp = 0;
      this.todos.forEach(element => {
        if (element.done) temp++;
      });
      return temp;
    },
    allChecked() {
      return this.countDone === this.todos.length;
    }
  }
}
</script>

<style scoped>
  .todo-footer {
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
  }

  .todo-footer label {
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
  }

  .todo-footer label input {
    position: relative;
    top: -1px;
    vertical-align: middle;
    margin-right: 5px;
  }

  .todo-footer button {
    float: right;
    margin-top: 5px;
  }
</style>