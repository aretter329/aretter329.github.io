<script setup>
</script>

<template>
  <nav class="navbar">
    <div class="navbar-container">
      <ul class="navbar-menu">
        <li>
          <router-link to="/" exact-active-class="active" class="menu-item">
            Home
          </router-link>
        </li>
        <li>
          <router-link to="/projects" exact-active-class="active" class="menu-item">
            Projects
          </router-link>
        </li>
        <li>
          <router-link to="/throwing" exact-active-class="active" class="menu-item">
            Throwing
          </router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0; 
  left: 0;
  width: 100%;
  backdrop-filter: blur(10px); 
  z-index: 1000; 
  display: flex;
  justify-content: center; 
  padding: 0 20px; 
  
  box-sizing: border-box;
}

.navbar-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 20px; 
  height: 60px; 
}

.navbar-menu {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
  flex-wrap: wrap;
}

.navbar-menu li {
  margin-left: 20px; 
  padding-top: 10px;
}

.navbar-menu a {
  color: white;
  text-decoration: none;
  transition: color 0.3s;
}

.menu-item {
  height: 35px; 
  font-size: 30px;
  transition: background-color 0.3s ease;
  padding: 5px; 
  border-radius: 4px;
}

.menu-item:hover {
  background-color: var(--coral);
}

.menu-item.router-link-active {
  background-color: var(--coral); /* Highlight active link */
  color: white; /* Ensure text color is visible */
}
</style>