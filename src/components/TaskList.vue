<template>
  <div class="flex flex-col items-center">
    <div
      v-for="task in tasks"
      :key="task.id"
      class="task border px-4 md:px-8 py-4 md:py-6 rounded-md my-4 md:w-1/2 xl:w-1/3 mx-auto dark:bg-gray-800 dark:border-white border-black"
    >
      <div class="flex flex-col mb-3 items-center">
        <h3 class="mb-2">{{ task.title }}</h3>
        <p>{{ task.description }}</p>
      </div>
      <div class="mb-2">
        <button
          @click="$emit('editTask', task)"
          class="border border-black rounded-md px-4 py-2 mr-2 bg-blue-500 text-white hover:bg-blue-700 transition duration-300"
        >
          Edit
        </button>
        <button
          @click="$emit('deleteTask', task)"
          class="border border-black rounded-md px-4 py-2 bg-blue-500 text-white hover:bg-blue-700 transition duration-300"
        >
          Delete
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { defineProps } from 'vue'

export default {
  name: 'TaskList',
  props: {
    tasks: Array,
    darkMode: Boolean // receiving darkMode as a prop
  },
  setup(props) {
    return defineProps(props)
  }
}
</script>
