<template>
  <div class="min-h-screen bg-base-200 flex items-center justify-center">
    <div class="container mx-auto p-4 max-w-md">
      <div class="bg-base-100 shadow-xl rounded-lg p-6">
        <h1 class="text-2xl font-bold mb-4 text-center">Todo List</h1>
        <TodoList />
      </div>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
name: 'App',
components: {
  TodoList
}
}
</script>