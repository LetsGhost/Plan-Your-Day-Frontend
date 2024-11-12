<template>
  <div class="navbar">
    <div class="categories">
      <h3>Categories</h3>
      <ul>
        <li v-for="category in categories" :key="category">{{ category }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      categories: ['Today', 'Tomorrow', 'Misc'],
    };
  },
};
</script>

<style scoped>
.navbar {
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  width: 250px;
  background: #2b2c37;
}

.categories {
  margin-top: 50px;
  padding: 10px;
  color: #e5e0f0;
}
</style>
