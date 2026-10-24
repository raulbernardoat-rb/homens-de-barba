<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from "vue";

const props = withDefaults(defineProps<{ delay?: number }>(), { delay: 0 });

const el = ref<HTMLElement | null>(null);
const state = ref<"idle" | "armed" | "in">("idle");
let observer: IntersectionObserver | null = null;

// No servidor o conteúdo fica visível. No cliente, só esconde o que está abaixo da tela
// e revela quando aparece (sem piscar o que já está à vista).
onMounted(() => {
  const node = el.value;
  if (!node) return;
  if (node.getBoundingClientRect().top < window.innerHeight * 0.92) return;

  state.value = "armed";
  observer = new IntersectionObserver(
    (entries) => {
      if (entries.some((entry) => entry.isIntersecting)) {
        state.value = "in";
        observer?.disconnect();
      }
    },
    { threshold: 0.12 }
  );
  observer.observe(node);
});

onBeforeUnmount(() => observer?.disconnect());
</script>

<template>
  <div
    ref="el"
    :class="{ 'reveal-armed': state === 'armed', 'reveal-in': state === 'in' }"
    :style="{ transitionDelay: `${props.delay}ms` }"
  >
    <slot />
  </div>
</template>
