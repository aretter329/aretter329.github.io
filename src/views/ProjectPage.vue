<template>
  <div class = "gallery-container">
  <div class="gallery">

      <a href='https://codepen.io/aretter29/pens/public' target="_blank">
          <PictureFrame
          :href="codePenImage"
          caption="CodePen Portfolio"
          />
      </a>

      <a :href="pdfUrl" target="_blank">
          <PictureFrame
          :href="golImage"
          caption="GoL Simulator"
          />
      </a>

      <router-link to="projects/game">
        <PictureFrame
          :href="dragonImage"
          caption="Simple RPG"
        />
      </router-link>
      
      <!-- Optional: Display the HTML content in a hidden element -->
      <div v-if="showHtmlContent" v-html="htmlContent" class="html-content"></div>
  </div>
  </div>

</template>

<script setup>
import PictureFrame from '@/components/PictureFrame.vue';
import { ref } from 'vue';
import codePenImage from '@/assets/codepen.png';
import golImage from '@/assets/gol.png';
import dragonImage from '@/assets/dragongame.png';

const pdfUrl = new URL('@/assets/retter_srcomp.pdf', import.meta.url).href;
const htmlContent = ref('');
const showHtmlContent = ref(false);

async function loadHtmlContent() {
try {
  const htmlFile = new URL('@/assets/dragon.html', import.meta.url).href;
  const response = await fetch(htmlFile);
  htmlContent.value = await response.text();
  showHtmlContent.value = true;
} catch (error) {
  console.error('Error loading HTML file:', error);
}
}
</script>

<style scoped> 

.gallery{
padding-top: 100px;
display: flex;
flex-wrap: wrap;
gap: 1rem; 
justify-content: space-between; 
max-width: 900px;
align-items: center;
}

.gallery-container {
display: flex;
justify-content: center; 
align-items: center; 
flex-direction: column;
}
.html-content {
display: none; 
}

a{
  max-width: 25%;
  text-decoration: none; 
  color: var(--white);
}

a:hover{
transform: translateY(-5px); /* Optional: Slight lift effect */
}
</style> 