<template>
  <div class="login-container">
    <h1>Login</h1>
    <form @submit.prevent="handleLogin">
      <div class="input-group">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="email" required />
      </div>
      <div class="input-group">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="password" required />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const email = ref('')
const password = ref('')

const handleLogin = () => {
  // Handle login logic here
  console.log('Logging in with', email.value, password.value)
}
</script>

<style scoped>
.login-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 50vh;
  width: 50vh;

  color: #ecf0f1;
  padding: 0 20px;
}

h1 {
  margin-bottom: 2rem;
  color: #3498db;
}

.input-group {
  margin-bottom: 1.5rem;
  width: 100%;
  max-width: 400px;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  color: #3498db;
}

input {
  width: 100%;
  padding: 0.75rem;
  border: none;
  border-radius: 4px;
  background-color: #34495e;
  color: #ecf0f1;
}

button {
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
  background-color: #3498db;
  color: #ecf0f1;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #2980b9;
}
</style>