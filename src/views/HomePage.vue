<template>
  <div class="container">
    <AnimatedText text="Hi, I'm Adria." />
    
    <div  id="main" class="fade-in-content">
      <div class="about" id="about"> 
        <div id="bio">
          <p>I'm a Masters student studying software engineering at Villanova University. 
              In May 2023, I graduated from Swarthmore College with Bachelors degrees in mathematics 
              and computer science. </p>

          <p>In addition to my studies, I throw discus, shot put, and hammer for Villanova. 
              During my time at Swarthmore, I was a 2x All-American and the 2023 NCAA National Champion in the discus.</p>
        </div>
      </div>
    
  <ContactBar/>
    </div>
  </div>
</template>

<script setup>
import AnimatedText from '@/components/AnimatedText.vue';
import ContactBar from '@/components/ContactBar.vue';

</script>

<style scoped>
#main {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  box-sizing: border-box;
}
.container{
  padding-top: 100px;
  display: flex; 
  flex-direction: column;
  align-items: center;
}

.fade-in-content {
  color: white;
  max-width: 900px;
  opacity: 0; /* Start as invisible */
  animation: fadeIn 3s ease-out forwards; /* Apply animation */
  animation-delay: .5s; /* Delay animation start by 1 second */
}

/* Keyframe animation for fading in */
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

</style>