<!DOCTYPE html>
<html>
<head>
  <title>Vue Todo List</title>
  <!-- Load Vue.js from a CDN -->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
</head>
<body>
  <div id="app">
    <h1>Todo List</h1>
    
    <!-- Input field to add new tasks -->
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task">
    <button @click="addTask">Add</button>
    
    <!-- Display the list of tasks -->
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>

  <script>
    new Vue({
      el: '#app',
      data: {
        newTask: '', // Input field value for new task
        tasks: [],   // Array to store tasks
      },
      methods: {
        // Function to add a new task
        addTask() {
          if (this.newTask.trim() !== '') {
            this.tasks.push(this.newTask);
            this.newTask = '';
          }
        },
        // Function to remove a task by index
        removeTask(index) {
          this.tasks.splice(index, 1);
        },
      },
    });
  </script>
</body>
</html>

