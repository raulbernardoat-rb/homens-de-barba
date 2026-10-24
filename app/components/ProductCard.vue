<script setup lang="ts">
defineProps<{
  image?: string;
  name: string;
  price: string;
}>();
</script>

<template>
  <article class="overflow-hidden rounded-card border border-border bg-surface-raised">
    <div class="aspect-square overflow-hidden">
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
        class="flex h-full w-full items-center justify-center bg-linear-to-br from-charcoal-800 to-copper-900/60 text-sm text-subtle"
      >
        Sem imagem
      </div>
    </div>
    <div class="flex items-center justify-between gap-3 p-4">
      <h3 class="text-base font-semibold text-foreground">{{ name }}</h3>
      <span class="shrink-0 font-bold text-primary">{{ price }}</span>
    </div>
  </article>
</template>
