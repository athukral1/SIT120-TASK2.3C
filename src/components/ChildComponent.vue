<template>
    <div class="child-component">
      <h2 class="child-title">{{ title }}</h2>
      <p class="child-content">{{ content }}</p>
      <button class="child-button" @click="handleClick">Click Me</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: String,
      content: String,
    },
    setup(props, { emit }) {
      const handleClick = () => {
        emit('customClick', 'Some data');
      };
  
      return {
        handleClick,
      };
    },
  };
  </script>
  
  <style scoped>
  .child-component {
    background-color: #ffffff;
    border: 1px solid #e0e0e0;
    border-radius: 5px;
    padding: 20px;
    margin: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease-in-out;
  }
  
  .child-title {
    font-size: 1.5rem;
    margin-bottom: 10px;
    color: #333;
  }
  
  .child-content {
    font-size: 1rem;
    color: #666;
    margin-bottom: 15px;
  }
  
  .child-button {
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    padding: 8px 16px;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out;
  }
  
  .child-button:hover {
    background-color: #0056b3;
  }
  </style>
  