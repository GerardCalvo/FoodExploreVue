<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <img
    src="../assets/images/portada.jpg"
    alt="imatge portada"
    class="hero-image"
  />

  <main class="home-main">
    <div class="home-text">
      <h1 class="home-title">Benvinguts a CosmosFood</h1>
      <p>Descobreix plats d’arreu del món sense sortir de casa.</p>
    </div>

    <RouterLink to="/receptes" class="btn"> Explorar receptes </RouterLink>
  </main>
</template>
