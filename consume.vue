<!DOCTYPE html>
<html>
<head>
  <title>Vue API Example</title>
  <!-- Load Vue.js and Axios from CDNs -->
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
</head>
<body>
  <div id="app">
    <h1>User List</h1>

    <!-- Display a loading message while data is being fetched -->
    <p v-if="loading">Loading...</p>

    <!-- Display the list of users if data is available -->
    <ul v-if="!loading">
      <li v-for="user in users" :key="user.id">
        {{ user.name }} ({{ user.email }})
      </li>
    </ul>
  </div>

  <script>
    new Vue({
      el: '#app',
      data: {
        users: [],    // Array to store user data
        loading: true // Flag to show loading message
      },
      mounted() {
        // Fetch user data from an API using Axios
        axios.get('https://jsonplaceholder.typicode.com/users')
          .then(response => {
            // Set the user data and hide the loading message
            this.users = response.data;
            this.loading = false;
          })
          .catch(error => {
            console.error('Error fetching data:', error);
            this.loading = false;
          });
      }
    });
  </script>
</body>
</html>

