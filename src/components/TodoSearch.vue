<template>
  <div class="mb-4">
    <input
      v-model="keyword"
      type="text"
      placeholder="キーワード検索"
      class="input input-bordered w-full"
    />
  </div>
</template>

<script>
export default {
  props: ['modelValue'],
  emits: ['update:modelValue'],
  computed: {
    keyword: {
      get() {
        return this.modelValue;
      },
      set(value) {
        this.$emit('update:modelValue', value);
      },
    },
  },
};
</script>
