<template>
  <li>
    <span class="item" :class="todoItemClass" @click="toggleItem"
      >🎈{{ todoItem.title }}</span
    >
    <button type="button" @click="removeItem">삭제</button>
  </li>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue';
import { Todo } from '../App.vue';

export default Vue.extend({
  props: {
    todoItem: Object as PropType<Todo>,
    index: Number,
  },
  computed: {
    todoItemClass(): string | null {
      return this.todoItem.done ? 'complete' : null;
    },
  },
  methods: {
    toggleItem() {
      this.$emit('toggle', this.todoItem, this.index);
    },
    removeItem() {
      this.$emit('remove', this.index);
    },
  },
});
</script>

<style scoped>
li {
  display: flex;
  align-items: center;
  text-align: left;
}
li + li {
  margin-top: 1rem;
}
.item {
  cursor: pointer;
}
.item + button {
  margin-left: 1rem;
}
.complete {
  text-decoration: line-through;
}
button {
  padding: 0;
  width: 4rem;
  font-family: 'RIDIBatang', sans-serif;
  color: #fff;
  border: none;
  background: #ad8b73;
}
</style>
