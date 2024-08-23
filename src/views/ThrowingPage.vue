
<script setup> 
import TrackArticles from '@/components/TrackArticles.vue';
import PictureFrame from '@/components/PictureFrame.vue';
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
          href="https://pbs.twimg.com/media/FMpAb2UXIAENYm_?format=jpg&name=4096x4096"
          caption="Centennial Conference Shot Put & Weight Throw Champion"
          class='photo'
      />
      <PictureFrame
        href="https://swarthmoreathletics.com/images/2023/5/25/adria_championship.png?width=1534&quality=80&format=jpg"
        caption="NCAA DIII Discus Champion"
        class='photo'
      />
      <PictureFrame
        href="https://images.sidearmdev.com/convert?url=https%3A%2F%2Fdxbhsrqyrr690.cloudfront.net%2Fsidearm.nextgen.sites%2Fvillanova.com%2Fimages%2F2024%2F5%2F21%2F2024-05-11BigEastT_FDay3_2299.jpg&type=webp"
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
  font-size: 20px;
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
