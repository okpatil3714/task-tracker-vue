<template>
  <div :class="{ dark: isDarkMode }" class="flex flex-col items-center px-8">
    <h2 class="text-3xl font-extrabold my-5">Add Task</h2>
    <form
      @submit.prevent="addTask"
      class="flex flex-col items-center w-full md:w-2/3 lg:w-1/2 xl:w-1/3 mx-auto"
    >
      <div class="flex flex-col mb-5 w-full">
        <label for="title" class="mb-2">Title:</label>
        <input
          v-model="title"
          type="text"
          required
          :class="{ 'text-white': isDarkMode, 'text-black': !isDarkMode }"
          class="border text-center border-black rounded-md p-2 h-12"
        />
      </div>
      <div class="flex flex-col mb-5 w-full">
        <label for="description" class="mb-2">Description:</label>
        <textarea
          v-model="description"
          required
          :class="{ 'text-white': isDarkMode, 'text-black': !isDarkMode }"
          class="border text-center border-black rounded-md"
        ></textarea>
      </div>
      <button
        type="submit"
        class="bg-blue-500 text-white rounded-md px-4 py-2 hover:bg-blue-700 transition duration-300 w-40"
      >
        Add Task
      </button>
    </form>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'AddTaskForm',
  setup(_, { emit }) {
    const title = ref('')
    const description = ref('')
    const isDarkMode = ref(false)

    const addTask = () => {
      if (title.value && description.value) {
        emit('addTask', {
          id: Date.now(),
          title: title.value,
          description: description.value
        })
        title.value = ''
        description.value = ''
      }
    }

    return { title, description, addTask, isDarkMode }
  }
}
</script>
