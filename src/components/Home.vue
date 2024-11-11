<template>
  <div class="home-container">
    <nav class="navbar">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Reminders</a></li>
        <!-- Add more options here -->
      </ul>
    </nav>
    <main class="main-content">
      <div class="reminder-cards">
        <!-- Display reminder cards here -->
        <div class="card" v-for="reminder in reminders" :key="reminder.id">
          <h2>{{ reminder.title }}</h2>
          <p>{{ reminder.description }}</p>
        </div>
      </div>
      <button class="add-reminder-button" @click="createReminder">Add Reminder</button>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const reminders = ref([
  { id: 1, title: 'Reminder 1', description: 'Description for reminder 1' },
  { id: 2, title: 'Reminder 2', description: 'Description for reminder 2' },
  // Add more reminders here
])

const createReminder = () => {
  // Logic to create a new reminder
  console.log('Create new reminder')
}
</script>

<style scoped>
.home-container {
  display: flex;
  height: 100vh;
  background-color: #f4f4f9;
}

.navbar {
  width: 250px;
  background-color: #2c3e50;
  padding: 1rem;
  color: #ecf0f1;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.navbar ul {
  list-style: none;
  padding: 0;
  width: 100%;
}

.navbar li {
  width: 100%;
  margin-bottom: 1rem;
}

.navbar a {
  color: #ecf0f1;
  text-decoration: none;
  display: block;
  padding: 0.75rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.navbar a:hover {
  background-color: #34495e;
}

.main-content {
  flex: 1;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow-y: auto;
}

.reminder-cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}

.card {
  background-color: #ffffff;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  width: 200px;
  transition: transform 0.3s;
}

.card:hover {
  transform: translateY(-5px);
}

.add-reminder-button {
  margin-top: 2rem;
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 4px;
  background-color: #3498db;
  color: #ecf0f1;
  cursor: pointer;
  transition: background-color 0.3s;
}

.add-reminder-button:hover {
  background-color: #2980b9;
}
</style>