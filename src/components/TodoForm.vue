<template>
  <div class="mb-4">
    <input
      v-model="newTodo"
      @keyup.enter="submitTodo"
      type="text"
      placeholder="Todoを追加"
      class="input input-bordered w-full"
    />
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup(props, { emit }) {
    const newTodo = ref('');

    const submitTodo = () => {
      if (newTodo.value.trim() !== '') {
        emit('add-todo', newTodo.value);
        newTodo.value = '';
      }
    };

    return {
      newTodo,
      submitTodo,
    };
  },
};
</script>
