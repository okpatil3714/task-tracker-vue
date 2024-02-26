<template>
  <div id="app" :class="{ dark: darkMode }" class="font-serif text-center bg-gray-100 min-h-screen">
    <div class="container mx-auto py-8">
      <TaskList :tasks="tasks" :darkMode="darkMode" @editTask="editTask" @deleteTask="deleteTask" />
      <AddTaskForm @addTask="addTask" />
      <EditTaskForm :task="editedTask" @updateTask="updateTask" @cancelEdit="cancelEdit" />
      <button @click="toggleDarkMode" class="bg-gray-800 text-white rounded-md px-4 py-2 mt-5">
        {{ darkMode ? 'Light Mode' : 'Dark Mode' }}
      </button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import TaskList from '@/components/TaskList.vue'
import AddTaskForm from '@/components/AddTaskForm.vue'
import EditTaskForm from '@/components/EditTaskForm.vue'

export default {
  name: 'App',
  components: {
    TaskList,
    AddTaskForm,
    EditTaskForm
  },
  setup() {
    const tasks = ref([])
    const editedTask = ref(null)
    const darkMode = ref(false)

    const addTask = (task) => {
      tasks.value.push(task)
    }

    const editTask = (task) => {
      editedTask.value = task
    }

    const toggleDarkMode = () => {
      darkMode.value = !darkMode.value
    }

    const updateTask = (updatedTask) => {
      const index = tasks.value.findIndex((t) => t.id === updatedTask.id)
      if (index !== -1) {
        tasks.value[index] = { ...updatedTask }
      }
      editedTask.value = null
    }

    const deleteTask = (task) => {
      const confirmed = window.confirm('Are you sure you want to delete?')
      if (confirmed) {
        tasks.value = tasks.value.filter((t) => t.id !== task.id)
        editedTask.value = null
      }
    }

    const cancelEdit = () => {
      editedTask.value = null
    }

    return {
      tasks,
      editedTask,
      darkMode,
      toggleDarkMode,
      addTask,
      editTask,
      updateTask,
      deleteTask,
      cancelEdit
    }
  }
}
</script>
