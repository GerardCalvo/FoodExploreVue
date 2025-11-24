<script setup>
import { inject } from 'vue';
import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
const router = useRouter();

const receptaId = parseInt(route.params.id);

const receptes = inject('receptes');
const recepta = receptes.value.find(r => r.id === receptaId);

// si no troba recepta redirigeixo
if (!recepta) {
  router.push({ name: 'NoTrobat' });
}
</script>

<template>
  <main v-if="recepta" class="detail-layout">
    <img
      class="detail-image"
      :src="recepta.img"
      alt="foto recepta"
    />

    <div class="detail-content">
      <header>
        <h1 class="detail-title">{{ recepta.nom }}</h1>
        <p>{{ recepta.descripcio }}</p>
      </header>

      <section>
        <p class="subsection-title">Ingredients</p>
        <ul class="detail-list">
          <li
            v-for="(ingredient, i) in recepta.ingredients"
            :key="i"
          >
            {{ ingredient }}
          </li>
        </ul>
      </section>

      <section>
        <p class="subsection-title">Pas a pas</p>
        <ol class="detail-list">
          <li v-for="(pas, i) in recepta.passos" :key="i">
            {{ pas }}
          </li>
        </ol>
      </section>

      <div class="rating-row">
        <p class="subsection-title">Valoració</p>
        <div class="rating-stars">
          <span
            v-for="i in recepta.puntuacio"
            :key="`full-${i}`"
          >
            <img
              src="../assets/images/estrella.svg"
              alt="estrella"
            />
          </span>
          <span
            v-for="i in 5 - recepta.puntuacio"
            :key="`empty-${i}`"
          >
            <img
              src="../assets/images/estrella-buida.svg"
              alt="estrella buida"
            />
          </span>
        </div>
      </div>
    </div>
  </main>
</template>
