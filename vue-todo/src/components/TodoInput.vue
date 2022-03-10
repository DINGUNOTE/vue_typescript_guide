<template>
  <div>
    <label for="todo-input">오늘 할 일 : </label>
    <input id="todo-input" type="text" :value="item" @input="handleInput" />
    <button @click="addTodo" type="button">추가</button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  // props: ['item'],
  props: {
    item: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleInput(event: any) {
      console.log(event);
      this.$emit('input', event.target.value);
    },
    addTodo() {
      this.$emit('add');
    },
  },
});
</script>

<style scoped>
div {
  display: flex;
  align-items: center;
}
</style>
