<script setup lang="ts">
const words = ["Corte", "Barba", "Acabamento", "Estilo", "Tradição", "Cuidado"];
</script>

<template>
  <div
    class="relative overflow-hidden border-y border-gold-300/30 bg-linear-to-r from-gold-500 via-copper-500 to-gold-500 py-4"
    aria-hidden="true"
  >
    <div class="flex w-max animate-marquee">
      <!-- Duas cópias para o loop ficar contínuo -->
      <div v-for="copy in 2" :key="copy" class="flex shrink-0 items-center">
        <template v-for="word in words" :key="word + copy">
          <span class="px-6 font-display text-lg font-bold uppercase tracking-[0.25em] text-charcoal-950 sm:px-8 sm:text-xl">
            {{ word }}
          </span>
          <span class="text-charcoal-950/60">✦</span>
        </template>
      </div>
    </div>
  </div>
</template>
