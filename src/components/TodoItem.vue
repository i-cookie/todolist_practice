<template>
  <li>
      <label>
        <input type="checkbox" :checked='tag.done' @change='complete'/>
        <span :class="{completed : tag.done}">{{tag.content}}</span>
      </label>
      <button class="btn btn-danger" @click="deleteItem">delete</button>
    </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['tag'],
  emits: ['completeTask', 'deleteItem'],
  methods: {
    complete() {
      this.$emit('completeTask', !this.tag.done);
    },
    deleteItem() {
      this.$emit('deleteItem', this.tag.id);
    }
  }
}
</script>

<style scoped>
  .completed {
    text-decoration: line-through;
  }

  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    float: right;
    display: none;
    margin-top: 3px;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }

  li:hover {
    background-color: #ddd;
  }

  li:hover button {
    display: block;
  }
</style>