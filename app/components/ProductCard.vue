<script setup lang="ts">
defineProps<{
  image?: string;
  name: string;
  price: string;
}>();
</script>

<template>
  <article class="overflow-hidden rounded-card border border-charcoal-200 bg-white shadow-sm transition duration-300 hover:-translate-y-1 hover:border-gold-400 hover:shadow-xl hover:shadow-gold-500/20">
    <div class="aspect-square overflow-hidden bg-charcoal-950">
      <img
        v-if="image"
        :src="image"
        :alt="name"
        loading="lazy"
        class="h-full w-full object-cover"
      />
      <!-- Provisório: produto sem imagem -->
      <div
        v-else
        class="flex h-full w-full items-center justify-center bg-linear-to-br from-charcoal-950 to-charcoal-900 text-sm text-charcoal-400"
      >
        Sem imagem
      </div>
    </div>
    <div class="flex items-center justify-between gap-3 p-4">
      <h3 class="text-base font-semibold text-charcoal-900">{{ name }}</h3>
      <span class="shrink-0 rounded-full bg-gold-100 px-2.5 py-0.5 text-sm font-bold text-gold-800">{{ price }}</span>
    </div>
  </article>
</template>
