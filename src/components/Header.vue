<script setup>
import { RouterLink, useRoute } from 'vue-router';

const route = useRoute();
</script>

<template>
  <header class="app-header">
    <RouterLink to="/" class="app-logo">
      <p class="app-title">CosmosFood</p>
    </RouterLink>

    <nav class="main-nav">
      <RouterLink
        to="/"
        class="nav-link"
        :class="{ 'nav-link--active': route.path === '/' }"
      >
        Inici
      </RouterLink>
      <RouterLink
        to="/receptes"
        class="nav-link"
        :class="{ 'nav-link--active': route.path.startsWith('/receptes') }"
      >
        Receptes
      </RouterLink>
      <RouterLink
        to="/gadgets"
        class="nav-link"
        :class="{ 'nav-link--active': route.path === '/gadgets' }"
      >
        Gadgets
      </RouterLink>
    </nav>
  </header>
</template>
