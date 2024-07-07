<template>
  <div>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Todoを追加" class="input input-bordered w-full mb-4" />
    <input v-model="searchKeyword" placeholder="キーワード検索" class="input input-bordered w-full mb-4" />
    <ul class="space-y-2">
      <TodoItem
        v-for="todo in filteredTodos"
        :key="todo.id"
        :todo="todo"
        @delete="showDeleteModal"
      />
    </ul>
    <DeleteModal
      :isOpen="isDeleteModalOpen"
      :todoToDelete="todoToDelete"
      @confirm="deleteTodo"
      @cancel="closeDeleteModal"
    />
  </div>
</template>

<script>
import { ref, computed } from 'vue'
import TodoItem from './TodoItem.vue'
import DeleteModal from './DeleteModal.vue'

export default {
  name: 'TodoList',
  components: {
    TodoItem,
    DeleteModal
  },
  setup() {
    const todos = ref([
      { id: 1, text: 'Todo1' },
      { id: 2, text: 'Todo2' },
      { id: 3, text: 'Todo3' }
    ])
    const newTodo = ref('')
    const searchKeyword = ref('')
    const isDeleteModalOpen = ref(false)
    const todoToDelete = ref(null)

    const filteredTodos = computed(() => {
      return todos.value.filter(todo => 
        todo.text.toLowerCase().includes(searchKeyword.value.toLowerCase())
      )
    })

    const addTodo = () => {
      if (newTodo.value.trim()) {
        todos.value.push({
          id: Date.now(),
          text: newTodo.value
        })
        newTodo.value = ''
      }
    }

    const showDeleteModal = (todo) => {
      todoToDelete.value = todo
      isDeleteModalOpen.value = true
    }

    const deleteTodo = () => {
      todos.value = todos.value.filter(todo => todo.id !== todoToDelete.value.id)
      closeDeleteModal()
    }

    const closeDeleteModal = () => {
      isDeleteModalOpen.value = false
      todoToDelete.value = null
    }

    return {
      todos,
      newTodo,
      searchKeyword,
      filteredTodos,
      addTodo,
      isDeleteModalOpen,
      todoToDelete,
      showDeleteModal,
      deleteTodo,
      closeDeleteModal
    }
  }
}
</script>