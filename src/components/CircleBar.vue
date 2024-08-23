
<template>
    <div class="circle-bar">
      <div class="circle" v-for="n in 7" :key="n"></div> <!-- Creates 5 circles -->
    </div>
  </template>
  
  <script setup>
  </script>
  
  <style scoped>
  .circle-bar {
    display: flex;
    flex-direction: column;
    justify-content: center; /* Center circles vertically */
    align-items: center; /* Center circles horizontally */
    width: 80px; /* Width of the bar */
    position: fixed; /* Fix position to left side */
    top: 0;
    left: 0;
    bottom: 0;
    z-index: 1000; /* Ensure the bar is above other content */
  }
  
  .circle {
    width: 40px; /* Diameter of the circles */
    height: 40px; /* Diameter of the circles */
    background-color: #FF6F61; /* Accent color */
    border-radius: 50%; /* Makes the div a circle */
    margin: 30px 0; /* Space between circles */
  }
  @media (max-width: 950px) {
    .circle-bar{
      display: none;
    }
  }
  </style>
  