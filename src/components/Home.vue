<template>
  <div id="home">
    <Navbar />
    <div class="content">
      <CreateReminderButton @create="addReminder" />
      <div class="reminder-list">
        <ReminderCard
          v-for="(reminder, index) in reminders"
          :key="index"
          :reminder="reminder"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from '../components/Navbar.vue';
import ReminderCard from '../components/ReminderCard.vue';
import CreateReminderButton from '../components/CreateReminderButton.vue';

export default {
  name: 'Home',
  components: {
    Navbar,
    ReminderCard,
    CreateReminderButton,
  },
  data() {
    return {
      reminders: [
        { title: 'Grocery Shopping', description: 'Buy milk and bread', done: false },
        { title: 'Workout', description: '30 minutes cardio', done: false },
      ],
    };
  },
  methods: {
    addReminder() {
      const newReminder = { title: 'New Reminder', description: 'Details here', done: false };
      this.reminders.push(newReminder);
    },
  },
};
</script>

<style scoped>
#home {
  display: flex;
}

.content {
  flex-grow: 1;
  margin-left: 250px; /* Space for the left-side navbar */
  padding: 1rem;
}

.reminder-list {
  margin-top: 1rem;
}
</style>
