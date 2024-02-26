# Vue Project

- This is a simple Vue project for managing tasks with dark mode functionality. It includes a Task List, Add Task Form, and Edit Task Form components.

# Table of Contents

- Getting Started
- Project Structure
- How to Use
- Additional Information

# Getting Started

- git clone "https://github.com/okpatil3714/task-tracker-vue.git"
- Install Dependencies
  - npm install
- Run the development server:
  - Copy code
  - npm run dev

# Project Structure

- src/App.vue: Main application component.
- src/components/TaskList.vue: Component for displaying a list of tasks.
- src/components/AddTaskForm.vue: Component for adding new tasks.
- src/components/EditTaskForm.vue: Component for editing existing tasks.
- src/main.js: Entry point for the application.
- src/main.css: Styles for the application.

# How to Use

- Tasks are displayed in the TaskList component.
- Click the "Add Task" button to open the AddTaskForm and add new tasks.
- Click the "Edit" button next to a task to open the EditTaskForm and modify the task.
- Toggle between light mode and dark mode using the "Dark Mode" button.

# Additional Information

- The project uses Vue 3 and Tailwind CSS.
- Dark mode is implemented using conditional class binding in the main App.vue component.
- Task data is managed using Vue ref to make it reactive.
