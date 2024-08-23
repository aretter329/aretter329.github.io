<template>
    <div class="articles-mentioned">
      <main>
        <section v-for="article in articles" :key="article.id" class="article">
          <a :href="article.link" target="_blank"> <blockquote>
            "{{ article.quote }}"
          </blockquote></a>
        </section>
      </main>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const articles = ref([
    {
      id: 1,
      quote: "ROCHESTER, NY - Swarthmore College women's track & field senior Adria Retter captured the National Championship in the discus throw to open the NCAA National Championships...",
      link: 'https://swarthmoreathletics.com/news/2023/5/25/womens-track-field-retter-crowned-national-champion-in-discus-throw.aspx'
    },
    {
      id: 2,
      quote: 'Retter Named PhillySIDA Co-Performer of the Year, Teszler Earns All-Area Nod',
      link: 'https://swarthmoreathletics.com/news/2023/6/16/womens-track-field-retter-named-phillysida-co-performer-of-the-year-teszler-earns-all-area-nod.aspx'
    }
    // Add more articles as needed
  ]);
  </script>
  
  <style scoped>
  .articles-mentioned {
    line-height: 1.6;
    margin: 0 auto;
    padding: 1rem;
    max-width: 900px;
  }
  
  header {
    text-align: center;
    margin-bottom: 2rem;
  }
  
  h1 {
    font-size: 2rem;
    margin: 0;
  }
  
  main {
    display: flex;
    flex-direction: column;
  }
  
  
  
  section {
    background-clip: border-box; 
    background: linear-gradient(35deg, var(--coral), var(--green)); /* Dark blue to medium blue gradient */
    -webkit-background-clip: text; /* WebKit-specific text background clipping */
    -webkit-text-fill-color: transparent; /* Make text transparent to show gradient */
  
    p {
      margin: 0;
    }
    font-style: italic;
    margin: 0;
  }
  
  a:hover{
    font-weight: bold;
  }
  
  </style>