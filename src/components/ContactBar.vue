<script setup>
</script>

<template>
  <div class="container">
    <div class="contact-bar" id="contact">
      <div class="contact-logos">
        <a href="https://www.linkedin.com/in/adria-retter" target="_blank" aria-label="LinkedIn">
          <i class="fa fa-linkedin"></i>
        </a>
        <a href="https://github.com/aretter329" target="_blank" aria-label="GitHub">
          <i class="fa fa-github"></i>
        </a>
        <a href="https://www.instagram.com/aretter29/" target="_blank" aria-label="Instagram">
          <i class="fa fa-instagram"></i>
        </a>
        <a href="mailto:aretter329@gmail.com?subject=Me&body=Hello!" aria-label="Email">
          <i class="fa fa-envelope"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Contact Bar Styles */
.contact-bar {
  max-width: 900px;
  position: fixed;
  bottom: 0;
  width: 100%;
  color: white;
  text-align: center;
  padding: 10px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--gray);
}

.container{
  display: flex; 
  flex-direction: column; 
  align-items: center;
  
}

.contact-header {
  font-size: 1.2rem;
  margin-bottom: 10px;
}

.contact-logos {
  display: flex;
  justify-content: center;
  gap: 15px; /* Spacing between icons */
}

.contact-logos a {
  color: var(--blue);
  font-size: 1.5rem; /* Icon size */
  transition: color 0.3s; /* Smooth color transition */
}

.contact-logos a:hover {
  color: var(--coral); /* Change color on hover (Tomato) */
}

.contact-logos .fa {
  font-size: 2rem; /* Font size for icons */
}
</style>