<script setup>
import { computed, inject } from 'vue';
import BasketItem from './CarretItem.vue';

const carret = inject('carret');

const costTotal = computed(() =>
  carret.value.reduce((total, producte) => total + producte.preu, 0)
);

const handleBuidarCarret = () => {
  const confirmation = confirm('Estàs segur@ que vols buidar la cistella?');
  if (confirmation) {
    carret.value.length = 0;
  }
};
</script>

<template>
  <div class="basket">
    <header class="basket-header">
      <div class="basket-top">
        <h2 class="basket-title">
          Cistella <span class="basket-count">({{ carret.length }})</span>
        </h2>
        <button @click="handleBuidarCarret" class="icon-button">
          <img
            src="../assets/images/cart-cross.svg"
            alt="buidar cistella"
          />
        </button>
      </div>

      <ul class="basket-list">
        <BasketItem
          v-for="producte in carret"
          :key="producte.id"
          :producte="producte"
        />
      </ul>
    </header>

    <p class="basket-total">
      Total: <strong>{{ costTotal }}€</strong>
    </p>
  </div>
</template>
