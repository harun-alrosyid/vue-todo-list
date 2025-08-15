<script setup>
import { computed, ref } from 'vue'

const emit = defineEmits(['addTask']) // definisikan event
const todoInput = ref('')
const res = computed({
  get() {
    return todoInput.value
  },
  set(value) {
    todoInput.value = value
  },
})
function handleAddTask() {
  emit('addTask', { item: res.value, completed: false })
  todoInput.value = ''
}
</script>

<template>
  <div class="flex gap-4 mb-6">
    <input
      class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-base ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium file:text-foreground placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 md:text-sm flex-1 font-mono b"
      type="text"
      placeholder="Add a task"
      v-model.trim="res"
    />
    <button
      @click="handleAddTask"
      :disabled="!res"
      class="inline-flex items-center justify-center gap-2 py-2 px-4 whitespace-nowrap rounded-md text-sm font-medium bg-amber-50 text-black disabled:cursor-not-allowed disabled:opacity-50"
    >
      +
    </button>
  </div>
</template>
