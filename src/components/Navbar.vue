<template>
  <div>
    <!-- Toggle button only visible on mobile -->
    <button class="menu-toggle" @click="toggleNavbar">☰</button>
    <!-- Navbar with conditional classes for mobile and desktop -->
    <div class="navbar" :class="{ open: isOpen || !isMobile }">
      <button v-if="isMobile" class="close-btn" @click="toggleNavbar">✕</button>
      <div class="categories">
        <h3>Categories</h3>
        <ul>
          <li v-for="category in categories" :key="category">{{ category }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      categories: ['Today', 'Tomorrow', 'Misc'],
      isMobile: window.innerWidth <= 768,
    };
  },
  methods: {
    toggleNavbar() {
      this.isOpen = !this.isOpen;
    },
    checkScreenSize() {
      this.isMobile = window.innerWidth <= 768;
      if (!this.isMobile) this.isOpen = false; // Always closed on desktop
    },
  },
  mounted() {
    window.addEventListener('resize', this.checkScreenSize);
    this.checkScreenSize(); // Initial check
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.checkScreenSize);
  },
};
</script>

<style scoped>
.menu-toggle {
  display: none;
  position: absolute;
  top: 1rem;
  left: 1rem;
  font-size: 1.5rem;
  background: none;
  border: none;
  color: #ffffff;
  z-index: 2;
}

.navbar {
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  width: 250px; /* Fixed width on desktop */
  background-size: 50px;
  background: #2b2c37;
  display: flex;
  flex-direction: column;
  padding: 1rem;
  transform: translateX(0);
}

.navbar.open {
  width: 100vw;
  height: 100vh;
}

.categories {
  margin-top: 50px;
  padding: 10px;
  color: #e5e0f0;
}

.close-btn {
  display: none;
  align-self: flex-end;
  background: none;
  border: none;
  color: #ffffff;
  font-size: 1.5rem;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: block;
  }

  .navbar {
    width: 100vw;
    height: 100vh;
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }

  .navbar.open {
    transform: translateX(0);
  }

  .close-btn {
    display: block;
    margin: 1rem;
    position: absolute;
    right: 1rem;
    top: 1rem;
  }
}
</style>
