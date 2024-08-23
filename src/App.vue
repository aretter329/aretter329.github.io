<script setup>
import NavBar from './components/NavBar.vue';
import CircleBar from './components/CircleBar.vue'; 

const beforeEnter = (el) => {
  el.style.opacity = 0;
};

const enter = (el, done) => {
  el.offsetHeight; // trigger reflow
  el.style.transition = 'opacity 1s ease';
  el.style.opacity = 1;
  done();
};

const leave = (el, done) => {
  el.style.transition = 'opacity 1s ease';
  el.style.opacity = 0;
  done();
};
</script>

<template>
  <div id="app">
    <NavBar />
    <router-view v-slot="{ Component }">
      <transition name="page" @before-enter="beforeEnter" @enter="enter" @leave="leave">
        <component :is="Component" />
      </transition>
    </router-view>
    <CircleBar />
  </div>
</template>

<style>
#app {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--white);
  margin-top: 60px;
  font-size: 20px;
}

body {
  background-color: var(--gray);
}



</style>