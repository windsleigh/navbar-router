<script setup lang="ts">
import { ref } from 'vue';

const navLinksActive = ref(false);

function toggleNavLinks() {
  navLinksActive.value = !navLinksActive.value;
}
</script>

<template>
  <header>
    <div class="wrapper">
      <nav class="nav">
        <RouterLink to="/" class="siteTitle">Home</RouterLink>
        <div class="navLinks" :class="{ active: navLinksActive }">
          <ul>
            <li class="block"><RouterLink to="/">Home</RouterLink></li>
            <li class="block"><RouterLink to="/about">About</RouterLink></li>
            <li class="block"><RouterLink to="/contact">Contact</RouterLink></li>
          </ul>
        </div>
        <div class="toggleButton" @click="toggleNavLinks">
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
        </div>
      </nav>
    </div>
  </header>
  <RouterView />
</template>
<style>
/* Your Given CSS Here */
nav {
  background-color: #333;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
  padding: 0 1rem;
}

.siteTitle {
  font-size: 2rem;
  margin: 0.5rem;
  text-decoration: none;
  color: inherit;
}

.navLinks ul {
  padding: 0;
  margin: 0;
  list-style: none;
  display: flex;
  gap: 1rem;
}

.navLinks a {
  color: inherit;
  font-size: 1.5rem;
  text-decoration: none;
  height: 100%;
  display: block;
  align-items: center;
  padding: 1rem;
}

.navLinks a:hover {
  background-color: rgb(117, 121, 121);
}

.toggleButton {
  position: absolute;
  top: 1.2rem;
  right: 1rem;
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 21px;
}

.toggleButton .bar {
  height: 3px;
  width: 100%;
  background-color: white;
  border-radius: 10px;
}

@media (max-width: 1024px) {
  .toggleButton {
    display: flex;
  }
  .navLinks {
    display: none;
    width: 100%;
  }
  .nav {
    flex-direction: column;
    align-items: flex-start;
  }
  .navLinks ul {
    width: 100%;
    flex-direction: column;
  }
  .navLinks li {
    text-align: center;
  }
  .navLinks li {
    padding: 0.5rem 1rem;
  }
  .navLinks.active {
    display: flex;
  }
}
</style>
