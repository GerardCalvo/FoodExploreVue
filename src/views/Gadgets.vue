<script setup>
import { inject } from 'vue';
import GadgetCard from '@/components/ProducteItem.vue';
import BasketPanel from '@/components/Carret.vue';

const productes = inject('productes');
const carret = inject('carret');

const handleAddProducte = producte => {
  carret.value.push(producte);
};
</script>

<template>
  <main>
    <h1 class="section-title">Zona tech</h1>

    <div class="shop-layout">
      <section class="shop-products">
        <h2 class="subsection-title">Catàleg</h2>
        <ul class="gadget-list">
          <GadgetCard
            v-for="producte in productes"
            :key="producte.id"
            :producte="producte"
            @add-product="handleAddProducte"
          />
        </ul>
      </section>

      <aside class="shop-basket">
        <BasketPanel />
      </aside>
    </div>
  </main>
</template>
