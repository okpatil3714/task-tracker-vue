<template>
  <div v-if="task" :class="{ dark: isDarkMode }" class="flex flex-col items-center">
    <h2 class="text-2xl font-extrabold my-5">Edit Task</h2>
    <form
      @submit.prevent="updateTask"
      class="flex flex-col items-center w-full md:w-2/3 lg:w-1/2 xl:w-1/3 mx-auto"
    >
      <div class="flex flex-col mb-5 w-full">
        <label for="title" class="mb-2">Title:</label>
        <input
          v-model="editedTask.title"
          type="text"
          required
          :class="{ 'text-white': isDarkMode, 'text-black': !isDarkMode }"
          class="border text-center border-black rounded-md p-2 h-12"
        />
      </div>
      <div class="flex flex-col mb-5 w-full">
        <label for="description" class="mb-2">Description:</label>
        <textarea
          v-model="editedTask.description"
          required
          :class="{ 'text-white': isDarkMode, 'text-black': !isDarkMode }"
          class="border text-center border-black rounded-md"
        ></textarea>
      </div>
      <button
        type="submit"
        class="bg-blue-500 text-white rounded-md px-4 py-2 hover:bg-blue-700 transition duration-300 w-40 mb-5"
      >
        Update Task
      </button>
      <button
        @click="$emit('cancelEdit')"
        class="bg-blue-500 text-white rounded-md px-4 py-2 hover:bg-blue-700 transition duration-300 w-40"
      >
        Cancel
      </button>
    </form>
  </div>
</template>

<script>
import { ref, watch } from 'vue'

export default {
  name: 'EditTaskForm',

  props: {
    task: Object
  },
  setup(props, { emit }) {
    const editedTask = ref({})
    const isDarkMode = ref(false)

    watch(
      () => props.task,
      (newTask) => {
        editedTask.value = { ...newTask }
      },
      { immediate: true }
    )

    const updateTask = () => {
      console.log('Update Method is called')
      if (editedTask.value.title && editedTask.value.description) {
        emit('updateTask', editedTask.value)
      }
    }

    return { editedTask, updateTask, isDarkMode }
  }
}
</script>
