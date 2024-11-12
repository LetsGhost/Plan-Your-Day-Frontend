<template>
  <button @click="createReminder">+ Add Reminder</button>
</template>

<script>
export default {
  methods: {
    createReminder() {
      this.$emit('create');
    },
  },
};
</script>

<style scoped>
button {
  background-color: #5c5f6d;
  color: #f5f3f4;
  border-radius: 8px;
  font-size: 1rem;
  padding: 0.6em 1.2em;
  margin-top: 1rem; /* Add spacing from other elements */
}
</style>
