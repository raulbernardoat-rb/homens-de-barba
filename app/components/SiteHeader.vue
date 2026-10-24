<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from "vue";
import BaseButton from "~/components/BaseButton.vue";

const links = [
  { label: "Sobre", href: "#sobre" },
  { label: "Serviços", href: "#servicos" },
  { label: "Produtos", href: "#produtos" },
  { label: "Contato", href: "#contato" },
];

const scrolled = ref(false);
const open = ref(false);

function onScroll() {
  scrolled.value = window.scrollY > 24;
}

onMounted(() => {
  onScroll();
  window.addEventListener("scroll", onScroll, { passive: true });
});
onBeforeUnmount(() => window.removeEventListener("scroll", onScroll));
</script>

<template>
  <header
    :class="[
      'fixed inset-x-0 top-0 z-50 transition-all duration-300',
      scrolled || open
        ? 'border-b border-border/60 bg-background/80 backdrop-blur-xl'
        : 'border-b border-transparent bg-transparent',
    ]"
  >
    <div class="mx-auto flex h-16 max-w-7xl items-center justify-between px-5 sm:px-6 lg:px-8">
      <!-- Marca -->
      <a href="#inicio" class="flex items-center gap-3" @click="open = false">
        <img src="/images/logo.png" alt="Logo Homens de Barba" width="150" height="150" class="size-10 rounded-full" />
        <span class="font-display text-lg font-bold tracking-wide text-foreground">
          Homens de Barba
        </span>
      </a>

      <!-- Navegação (computador) -->
      <nav class="hidden items-center gap-8 md:flex" aria-label="Principal">
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="text-sm font-medium text-muted transition hover:text-primary"
        >
          {{ link.label }}
        </a>
        <BaseButton href="#contato" class="px-5! py-2! text-sm">Agendar</BaseButton>
      </nav>

      <!-- Botão do menu (celular) -->
      <button
        type="button"
        class="flex size-11 items-center justify-center rounded-lg text-foreground md:hidden"
        :aria-expanded="open"
        aria-label="Abrir menu"
        @click="open = !open"
      >
        <svg class="size-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
          <path v-if="!open" d="M4 7h16M4 12h16M4 17h16" />
          <path v-else d="M6 6l12 12M18 6 6 18" />
        </svg>
      </button>
    </div>

    <!-- Menu (celular) -->
    <nav v-if="open" class="border-t border-border/60 px-5 pb-6 pt-2 md:hidden" aria-label="Menu móvel">
      <a
        v-for="link in links"
        :key="link.href"
        :href="link.href"
        class="block border-b border-border/40 py-4 text-lg font-medium text-foreground"
        @click="open = false"
      >
        {{ link.label }}
      </a>
      <BaseButton href="#contato" class="mt-5 block w-full text-center" @click="open = false">
        Agendar horário
      </BaseButton>
    </nav>
  </header>
</template>
