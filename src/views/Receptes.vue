<script setup>
import { inject } from 'vue';
import { RouterLink } from 'vue-router';

const receptes = inject('receptes');
</script>

<template>
  <main class="recipes-page">
    <h1 class="recipes-heading">Receptes</h1>

    <ul class="recipes-grid">
      <li
        v-for="recepta in receptes"
        :key="recepta.id"
        class="recipe-card"
      >
        <img
          :src="recepta.img"
          alt="img recepta"
          class="recipe-card__img"
        />

        <div class="recipe-card__body">
          <div>
            <h2 class="recipe-card__title">{{ recepta.nom }}</h2>
            <p class="recipe-card__description">
              {{ recepta.descripcio }}
            </p>
          </div>

          <RouterLink
            :to="`/receptes/${recepta.id}`"
            class="btn"
          >
            Veure detall
          </RouterLink>
        </div>
      </li>
    </ul>
  </main>
</template>
