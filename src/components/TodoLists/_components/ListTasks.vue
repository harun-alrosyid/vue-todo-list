<script setup>
defineProps({
  tasks: {
    type: Array,
  },
})
</script>

<template>
  <div
    class="w-full flex items-center justify-center border-dashed rounded-lg border-amber-50 border-2 p-4"
  >
    <div>
      <ul class="flex flex-col gap-4">
        <li v-for="task in tasks" :key="task.id">
          {{ task }}
        </li>
      </ul>
    </div>
  </div>
</template>
