<script setup lang="ts">
import BaseButton from "~/components/BaseButton.vue";
import RevealOnScroll from "~/components/RevealOnScroll.vue";

const highlights = [
  "Ambiente confortável",
  "Profissionais dedicados",
  "Atenção aos detalhes",
];
</script>

<template>
  <section id="sobre" class="relative isolate overflow-hidden bg-white">
    <!-- Brilhos suaves de fundo -->
    <div class="absolute -right-24 top-0 -z-10 size-96 rounded-full bg-gold-200/50 blur-3xl" aria-hidden="true" />
    <div class="absolute -left-24 bottom-0 -z-10 size-96 rounded-full bg-copper-100/70 blur-3xl" aria-hidden="true" />

    <div class="mx-auto grid max-w-7xl items-center gap-12 px-5 py-16 sm:px-6 lg:grid-cols-2 lg:gap-16 lg:px-8 lg:py-28">
      <!-- Texto de apresentação -->
      <RevealOnScroll class="text-center lg:text-left">
        <span class="text-sm font-semibold uppercase tracking-widest text-copper-600">
          Sobre nós
        </span>
        <h2 class="mt-4 font-display text-3xl font-bold leading-tight text-charcoal-900 sm:text-4xl">
          Mais que uma barbearia, um
          <span class="bg-linear-to-r from-gold-600 via-gold-500 to-copper-500 bg-clip-text text-transparent">
            lugar para você
          </span>
        </h2>
        <div class="mx-auto mt-5 h-1 w-20 rounded-full bg-linear-to-r from-gold-400 to-copper-500 lg:mx-0" />
        <p class="mx-auto mt-6 max-w-xl text-base text-charcoal-600 sm:text-lg lg:mx-0">
          A Homens de Barba nasceu para entregar um atendimento de verdade: com técnica,
          pontualidade e respeito ao seu estilo. Aqui você encontra um ambiente confortável,
          profissionais dedicados e o cuidado que seu visual merece.
        </p>
        <p class="mx-auto mt-4 max-w-xl text-base text-charcoal-600 sm:text-lg lg:mx-0">
          Cada corte e cada barba são feitos com atenção aos detalhes, para você sair
          daqui confiante e com a cara de quem se cuida.
        </p>

        <ul class="mt-6 flex flex-wrap justify-center gap-3 lg:justify-start">
          <li
            v-for="item in highlights"
            :key="item"
            class="flex items-center gap-2 rounded-full border border-gold-300 bg-gold-50 px-4 py-2 text-sm font-medium text-gold-800"
          >
            <svg class="size-4 text-copper-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="m5 12 5 5L20 7" /></svg>
            {{ item }}
          </li>
        </ul>

        <div class="mt-8 flex justify-center lg:justify-start">
          <BaseButton href="#contato">Agendar horário</BaseButton>
        </div>
      </RevealOnScroll>

      <!-- Imagem da barbearia com moldura em degradê -->
      <RevealOnScroll :delay="150" class="relative">
        <div class="relative mx-auto max-w-lg lg:max-w-none">
          <div class="absolute -bottom-4 -right-4 size-full rounded-card bg-linear-to-br from-gold-400 to-copper-500 sm:-bottom-5 sm:-right-5" aria-hidden="true" />
          <div class="absolute -left-3 -top-3 size-24 rounded-tl-card border-l-4 border-t-4 border-gold-400" aria-hidden="true" />
          <img
            src="/images/barbearia-dentro.jpg"
            alt="Interior da barbearia Homens de Barba"
            loading="lazy"
            class="relative aspect-4/3 w-full rounded-card object-cover shadow-2xl shadow-charcoal-900/25"
          />
        </div>
      </RevealOnScroll>
    </div>
  </section>
</template>
