<script setup>
const props = defineProps({
  producte: Object
});
</script>

<template>
  <li class="basket-item">
    {{ props.producte.nom }} - {{ props.producte.preu }}€
  </li>
</template>
