<template>
  <div v-if="isOpen" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div class="bg-base-100 p-6 rounded-lg shadow-xl max-w-sm w-full">
      <h2 class="text-lg font-bold mb-4">Todoを削除</h2>
      <p>{{ todoToDelete ? todoToDelete.text : '' }}を削除しますか？</p>
      <div class="flex justify-end mt-6">
        <button @click="$emit('cancel')" class="btn btn-ghost mr-2">キャンセル</button>
        <button @click="$emit('confirm')" class="btn btn-error">削除</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DeleteConfirmModal',
  props: {
    isOpen: {
      type: Boolean,
      required: true
    },
    todoToDelete: {
      type: Object,
      default: null
    }
  }
}
</script>

