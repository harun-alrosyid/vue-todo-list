<script setup>
defineProps({
  tasks: {
    type: Array,
  },
})
</script>

<template>
  <div>
    <ul class="flex flex-col gap-4 h-[40vh] overflow-y-auto">
      <li
        class="w-full grid grid-cols-[auto_1fr_auto] gap-4 border-dashed rounded-lg border-amber-50 border-2 p-4"
        v-for="(task, index) in tasks"
        :key="index"
      >
        <input
          class="w-min-[calc(100% - 40px)]"
          type="checkbox"
          :checked="task.completed"
          @click="$emit('completeTask', index)"
        />
        <p v-if="!task.completed" class="flex items-center text-ellipsis overflow-hidden">
          {{ task.item }}
        </p>
        <p v-else class="flex line-through items-center text-ellipsis overflow-hidden">
          {{ task.item }}
        </p>
        <button
          @click="$emit('removeTask', index)"
          class="bg-red-400 hover:bg-red-600 text-white font-bold py-2 px-4 rounded items-end"
        >
          x
        </button>
      </li>
    </ul>
  </div>
</template>
