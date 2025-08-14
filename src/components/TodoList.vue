<script setup>
import { reactive } from 'vue'
import EmptyTask from '../components/TodoLists/_components/EmptyTask.vue'
import InputTask from './TodoLists/_components/InputTask.vue'
import ListTasks from './TodoLists/_components/ListTasks.vue'

const tasks = reactive([])

const addTask = (task) => {
  tasks.push(task)
}
const removeTask = (index) => {
  tasks.value = tasks.splice(index, 1)
}

const completeTask = (index) => {
  tasks.value = tasks.map((task, i) => {
    if (i === index) {
      task.completed = !task.completed
    }
    return task
  })
}
</script>
<template>
  <div
    class="flex flex-col gap-4 items-center justify-center m-20 border-dashed rounded-lg border-amber-50 border-2 p-10 relative bg-gray-800"
  >
    <h1 class="text-4xl font-sans font-extrabold">VUE TODOLIST</h1>
    <p>A Simple task management • Vue prototype</p>
    <div class="w-full">
      <h2 class="text-2xl font-sans font-bold">TODO LIST</h2>
      <p>
        {{ tasks.length }} total * {{ tasks.filter((task) => task.completed).length }} completed
      </p>

      <div class="w-[95%] mx-auto p-10 h-[50vh]">
        <InputTask @addTask="addTask" />

        <EmptyTask v-if="tasks.length === 0" />

        <ListTasks v-else :tasks="tasks" @removeTask="removeTask" @completeTask="completeTask" />
      </div>
    </div>
  </div>
</template>
