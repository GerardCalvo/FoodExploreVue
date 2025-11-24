<script setup>
import { defineEmits } from 'vue';

const props = defineProps({
  producte: Object
});

const emit = defineEmits(['add-product']);

const onAfegirProducte = producte => {
  alert("'" + producte.nom + "' afegit a la cistella!");
  emit('add-product', props.producte);
};
</script>

<template>
  <li class="gadget-card">
    <div class="gadget-main">
      <h3 class="gadget-name">{{ props.producte.nom }}</h3>
      <p class="gadget-price">{{ props.producte.preu }}€</p>
    </div>

    <button @click="onAfegirProducte(producte)" class="btn">
      Afegir a la cistella
    </button>
  </li>
</template>
