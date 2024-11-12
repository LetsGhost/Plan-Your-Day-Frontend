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
          @click="viewDetails(reminder)"
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
    viewDetails(reminder) {
      alert(`Details: ${reminder.description}`);
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

/* Card styling for desktop */
.reminder-card {
  padding: 1rem;
  margin: 1rem 0;
  border: 1px solid #444;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #333;
  color: #fff;
}

/* Card styling for mobile - show only title and checkbox */
@media (max-width: 768px) {
  #home {
    flex-direction: column;
    margin-left: 0;
  }

  .content {
    padding-top: 4rem; /* Adjust spacing for mobile */
  }

  .reminder-list .reminder-card {
    font-size: 0.9rem;
    padding: 0.6rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  /* Hide description on mobile and make the card clickable */
  .reminder-list .reminder-card .description {
    display: none;
  }

  .reminder-card {
    cursor: pointer;
  }
}
</style>
