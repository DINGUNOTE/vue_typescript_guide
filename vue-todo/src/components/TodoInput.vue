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
    handleInput(event: InputEvent) {
      // console.log(event);
      // if (!event.target) {
      //   return;
      // }
      const eventTarget = event.target as HTMLInputElement;
      this.$emit('input', eventTarget.value);
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
  height: 3rem;
  align-items: center;
  justify-content: center;
}
input {
  margin-left: 0.5rem;
  height: 100%;
  border: 1px solid #ad8b73;
  border-right: none;
}
button {
  padding: 0;
  width: 5rem;
  height: 100%;
  font-family: 'RIDIBatang', sans-serif;
  color: #fff;
  border: none;
  background: #ad8b73;
}
</style>
