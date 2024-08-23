
<template>
    <div class="fancy-text">
      <h1 class="animated-text" ref="textElement">{{ text }}</h1>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  defineProps({
    text: String
  });
  
  </script>
  
  <style scoped>
  .fancy-text {
    display: flex;
    justify-content: center;
    align-items: center;
    color: var(--green);
    overflow: hidden;
  }
  
  .animated-text {
    font-size: 3.5rem;
    text-align: center;
    animation: fadeIn 2s ease-out, slideIn 2s ease-out;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  
  @keyframes slideIn {
    from { transform: translateY(-50px); }
    to { transform: translateY(0); }
  }
  </style>
  