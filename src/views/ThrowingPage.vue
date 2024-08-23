
<script setup> 
import TrackArticles from '@/components/TrackArticles.vue';
import PictureFrame from '@/components/PictureFrame.vue';
import BigEast from '@/assets/bigeast.webp';
import CentennialChamp from '@/assets/centennial.jpeg';
import NationalChamp from '@/assets/nationals.webp';
</script> 

<template>
<div class="gallery-container">
   <div class="full-page">
      <a id='swat-page' href="https://swarthmoreathletics.com/sports/womens-track-and-field/roster/adria-retter/11142" target="_blank">
        Swarthmore Bio
      </a>
      
      <a id='nova-page' href="https://villanova.com/sports/womens-track-and-field/roster/adria-retter/14142" target="_blank">
      Villanova Bio
      </a>

      <a id='nova-page' href="https://villanova.com/sports/womens-track-and-field/roster/adria-retter/14142" target="_blank">
      Results
      </a>
    </div>

    <div class="gallery">

      <PictureFrame 
          :href="CentennialChamp"
          caption="Centennial Conference Shot Put & Weight Throw Champion"
          class='photo'
      />
      <PictureFrame
        :href="NationalChamp"
        caption="NCAA DIII Discus Champion"
        class='photo'
      />
      <PictureFrame
        :href="BigEast"
        caption="Big East Discus Champion"
        class='photo'
      />
    </div>

   <TrackArticles></TrackArticles>
  </div>
</template>

<style scoped>
.gallery{
  display: flex;
  flex-wrap: wrap;
  gap: 1rem; 
  justify-content: center; 
  max-width: 900px;
  align-items: center;
}
.logo {
  height: 30px; 
  width: 30px; 
  margin-right: 8px; 
  object-fit: cover;
}

.gallery-container {
  display: flex;
  justify-content: center; 
  align-items: center; 
  flex-direction: column;
}

a {
  display: inline-flex; 
  align-items: center; 
  text-decoration: none; 
  font-size: 24px;
  color: var(--blue);
  transition: color 0.3s ease, background-color 0.3s ease;
  padding-left: 10px;
  padding-right: 10px;
}

a:hover {
  color: var(--coral);
  font-weight: bold;
}

.full-page{
  padding-top: 40px;
  max-width: 600px;
  width: 100%;
  padding-bottom: 40px;
  display: flex; 
  flex-wrap: wrap;
  justify-content: space-between;
}
.photo{
  max-width: 30%;
}

</style> 
