<template>
  <div class="card">
    <h3>{{ reminder.title }}</h3>
    <p>{{ reminder.description }}</p>
    <label>
      <input type="checkbox" v-model="reminder.done" />
      Done
    </label>
  </div>
</template>

<script>
export default {
  props: {
    reminder: Object,
  },
};
</script>

<style scoped>
.card {
  margin: 10px 0;
  border: 1px solid #3d3a4d;
}
h3 {
  color: #ffa07a;
}
</style>
