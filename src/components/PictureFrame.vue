<template>
    <div class="image-card">
      <img :src="href" :alt="caption" class="image" />
      <p class="caption">{{ caption }}</p>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  defineProps({
    href: {
      type: String
    },
    caption: {
      type: String
    },
  });
  </script>
  
  <style scoped>
  .image-card {
    margin: 0 auto;
    text-align: center;
  }
  
  .image {
    width: 100%;
    height: auto;
    display: block;
    border-radius: 8px; 
    object-fit: cover; 
  }
  
  .caption {
    margin-top: 0.5rem;
    font-size: 1rem;
  }

  </style>