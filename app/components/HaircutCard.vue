<script setup lang="ts">
defineProps<{
  image?: string;
  name: string;
  price: string;
}>();
</script>

<template>
  <!-- Borda em degradê aparece ao passar o mouse -->
  <article
    class="group rounded-card bg-linear-to-br from-border to-border p-px transition duration-300 hover:-translate-y-1 hover:from-gold-300 hover:to-copper-500 hover:shadow-glow-copper"
  >
    <div class="overflow-hidden rounded-[calc(var(--radius-card)-1px)] bg-surface">
      <div class="relative aspect-4/5 overflow-hidden">
        <img
          v-if="image"
          :src="image"
          :alt="name"
          loading="lazy"
          draggable="false"
          class="h-full w-full object-cover transition duration-700 group-hover:scale-110"
        />
        <!-- Provisório: card sem imagem -->
        <div
          v-else
          class="flex h-full w-full items-center justify-center bg-linear-to-br from-charcoal-800 to-copper-900/60 text-sm text-subtle"
        >
          Sem imagem
        </div>
        <!-- Sombra inferior para dar destaque ao preço -->
        <div class="absolute inset-x-0 bottom-0 h-1/3 bg-linear-to-t from-charcoal-950/80 to-transparent" aria-hidden="true" />
        <span
          class="absolute bottom-3 right-3 rounded-full bg-linear-to-r from-gold-300 to-gold-500 px-3 py-1 text-sm font-bold text-charcoal-950 shadow-lg"
        >
          {{ price }}
        </span>
      </div>
      <div class="p-4 sm:p-5">
        <h3 class="font-display text-lg font-semibold text-foreground">{{ name }}</h3>
      </div>
    </div>
  </article>
</template>
