<script setup lang="ts">
defineProps<{
  image?: string;
  name: string;
  price: string;
}>();
</script>

<template>
  <article
    class="group overflow-hidden rounded-card border border-border bg-surface transition hover:border-primary hover:shadow-glow"
  >
    <div class="aspect-4/5 overflow-hidden">
      <img
        v-if="image"
        :src="image"
        :alt="name"
        loading="lazy"
        draggable="false"
        class="h-full w-full object-cover transition duration-500 group-hover:scale-105"
      />
      <!-- Provisório: card sem imagem -->
      <div
        v-else
        class="flex h-full w-full items-center justify-center bg-linear-to-br from-charcoal-800 to-copper-900/60 text-sm text-subtle"
      >
        Sem imagem
      </div>
    </div>
    <div class="flex items-center justify-between gap-3 p-4 sm:p-5">
      <h3 class="font-display text-lg font-semibold text-foreground">{{ name }}</h3>
      <span class="shrink-0 text-lg font-bold text-primary">{{ price }}</span>
    </div>
  </article>
</template>
