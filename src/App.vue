<template>
  <div id="app">
    <!-- Navigation Links -->
    <router-link to="/">Home</router-link>
    <router-link to="/about">About</router-link>

    <!-- Include the DemoComponent -->
    <DemoComponent />

    <!-- Header -->
    <header class="header">
      <h1>Your Unique Vue App</h1>
      <p>Welcome to an Exceptional Experience</p>
    </header>

    <!-- Use router-view to display routed components -->
    <router-view></router-view>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';
import DemoComponent from './components/DemoComponent.vue';

// Function to run when the component is mounted
onMounted(() => {
  console.log('App.vue component has been mounted.');
});
</script>

<style scoped>
#app {
  font-family: 'Roboto', sans-serif;
  text-align: center;
  color: #333;
}

/* Header styling */
.header {
  padding: 20px;
  background-color: #007bff; /* Updated header background color */
  color: #fff; /* Updated header text color */
  border-bottom: 1px solid #ddd;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.header h1 {
  font-size: 2rem;
  margin-bottom: 10px;
}

.header p {
  font-size: 1.2rem;
  color: #f0f0f0;
}
</style>
