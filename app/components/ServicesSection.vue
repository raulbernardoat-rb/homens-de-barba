<script setup lang="ts">
import { ref } from "vue";
import HaircutCard from "~/components/HaircutCard.vue";

const haircuts = [
  { image: "/images/cortes/corte-1.png", name: "Corte 1", price: "R$ 20" },
  { image: "/images/cortes/corte-2.png", name: "Corte 2", price: "R$ 20" },
  { image: "/images/cortes/corte-3.png", name: "Corte 3", price: "R$ 20" },
  { name: "Corte 4", price: "R$ 25" },
  { name: "Corte 5", price: "R$ 30" },
  { name: "Corte 6", price: "R$ 35" },
];

const track = ref<HTMLElement | null>(null);

function scrollByPage(direction: 1 | -1) {
  const el = track.value;
  if (!el) return;
  el.scrollBy({ left: direction * el.clientWidth * 0.9, behavior: "smooth" });
}
</script>

<template>
  <section id="servicos" class="bg-background">
    <div class="mx-auto max-w-7xl px-5 py-14 sm:px-6 lg:px-8 lg:py-24">
      <div class="mx-auto max-w-2xl text-center">
        <span class="text-sm font-semibold uppercase tracking-widest text-secondary">
          Serviços
        </span>
        <h2 class="mt-4 font-display text-3xl font-bold text-foreground sm:text-4xl">
          Escolha o seu
          <span class="bg-linear-to-r from-gold-300 to-gold-500 bg-clip-text text-transparent">
            estilo
          </span>
        </h2>
        <p class="mt-4 text-base text-muted sm:text-lg">
          Confira nossos cortes e valores.
        </p>
      </div>

      <div class="relative mt-10 lg:mt-14">
        <!-- Trilha rolável: arrastar no celular, setas no computador -->
        <div
          ref="track"
          class="flex snap-x snap-mandatory gap-4 overflow-x-auto scroll-smooth pb-2 [-ms-overflow-style:none] [scrollbar-width:none] sm:gap-6 [&::-webkit-scrollbar]:hidden"
        >
          <div
            v-for="haircut in haircuts"
            :key="haircut.name"
            class="w-[70%] shrink-0 snap-start sm:w-[calc(50%-0.75rem)] lg:w-[calc(33.333%-1rem)]"
          >
            <HaircutCard :image="haircut.image" :name="haircut.name" :price="haircut.price" />
          </div>
        </div>

        <!-- Setas nas pontas -->
        <button
          type="button"
          aria-label="Cortes anteriores"
          class="absolute left-2 top-[40%] flex size-11 -translate-y-1/2 items-center justify-center rounded-full bg-background/80 text-foreground shadow-lg backdrop-blur transition hover:bg-primary hover:text-primary-foreground focus-visible:outline-2 focus-visible:outline-ring lg:-left-5"
          @click="scrollByPage(-1)"
        >
          <svg class="size-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6" /></svg>
        </button>
        <button
          type="button"
          aria-label="Próximos cortes"
          class="absolute right-2 top-[40%] flex size-11 -translate-y-1/2 items-center justify-center rounded-full bg-background/80 text-foreground shadow-lg backdrop-blur transition hover:bg-primary hover:text-primary-foreground focus-visible:outline-2 focus-visible:outline-ring lg:-right-5"
          @click="scrollByPage(1)"
        >
          <svg class="size-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6" /></svg>
        </button>
      </div>
    </div>
  </section>
</template>
