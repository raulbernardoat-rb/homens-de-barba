<script setup lang="ts">
import { ref } from "vue";

const props = defineProps<{
  images: { src: string; alt: string }[];
}>();

const current = ref(0);

function go(index: number) {
  const total = props.images.length;
  current.value = (index + total) % total;
}

let touchStartX = 0;

function onTouchStart(event: TouchEvent) {
  touchStartX = event.touches[0]?.clientX ?? 0;
}

function onTouchEnd(event: TouchEvent) {
  const deltaX = (event.changedTouches[0]?.clientX ?? 0) - touchStartX;
  if (Math.abs(deltaX) > 40) go(current.value + (deltaX < 0 ? 1 : -1));
}
</script>

<template>
  <div @touchstart.passive="onTouchStart" @touchend.passive="onTouchEnd" class="relative mx-auto aspect-5/6 touch-pan-y w-full max-w-lg overflow-hidden lg:h-[84vh] lg:max-h-[780px] lg:w-auto rounded-card border border-border bg-surface shadow-glow">
    <!-- Slides: todos com o mesmo tamanho, a imagem preenche o quadro -->
    <div
      class="flex h-full transition-transform duration-500 ease-out"
      :style="{ transform: `translateX(-${current * 100}%)` }"
    >
      <img
        v-for="image in props.images"
        :key="image.src"
        :src="image.src"
        :alt="image.alt"
        class="h-full w-full shrink-0 object-cover"
      />
    </div>

    <!-- Setas -->
    <button
      type="button"
      aria-label="Imagem anterior"
      class="absolute left-3 top-1/2 flex size-11 -translate-y-1/2 items-center justify-center rounded-full bg-background/70 text-foreground backdrop-blur transition hover:bg-primary hover:text-primary-foreground focus-visible:outline-2 focus-visible:outline-ring"
      @click="go(current - 1)"
    >
      <svg class="size-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6" /></svg>
    </button>
    <button
      type="button"
      aria-label="Próxima imagem"
      class="absolute right-3 top-1/2 flex size-11 -translate-y-1/2 items-center justify-center rounded-full bg-background/70 text-foreground backdrop-blur transition hover:bg-primary hover:text-primary-foreground focus-visible:outline-2 focus-visible:outline-ring"
      @click="go(current + 1)"
    >
      <svg class="size-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6" /></svg>
    </button>

    <!-- Indicadores -->
    <div class="absolute bottom-4 left-1/2 flex -translate-x-1/2 gap-2">
      <button
        v-for="(image, index) in props.images"
        :key="image.src"
        type="button"
        :aria-label="`Ir para imagem ${index + 1}`"
        :class="[
          'h-2 rounded-full p-0 transition-all before:absolute before:-inset-3 relative',
          index === current ? 'w-6 bg-primary' : 'w-2 bg-foreground/50 hover:bg-foreground/80',
        ]"
        @click="go(index)"
      />
    </div>
  </div>
</template>
