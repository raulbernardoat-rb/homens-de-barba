<script setup lang="ts">
import BaseButton from "~/components/BaseButton.vue";
import ImageCarousel from "~/components/ImageCarousel.vue";

const heroImages = [
  { src: "/images/hero/hero-1.png", alt: "Barbeiro da Homens de Barba" },
  { src: "/images/hero/hero-2.png", alt: "Atendimento na Homens de Barba" },
  { src: "/images/hero/hero-3.png", alt: "Corte de cabelo na Homens de Barba" },
];
</script>

<template>
  <section class="relative isolate overflow-hidden bg-background">
    <!-- Degradê de fundo -->
    <div
      class="absolute inset-0 -z-10 bg-linear-to-br from-charcoal-950 via-charcoal-900 to-copper-900/60"
      aria-hidden="true"
    />
    <div
      class="absolute -left-32 -top-32 -z-10 size-[28rem] rounded-full bg-primary/20 blur-3xl"
      aria-hidden="true"
    />
    <div
      class="absolute -bottom-40 right-0 -z-10 size-[32rem] rounded-full bg-secondary/25 blur-3xl"
      aria-hidden="true"
    />

    <div class="mx-auto grid min-h-svh max-w-7xl items-center gap-8 px-5 py-10 sm:px-6 lg:grid-cols-2 lg:gap-12 lg:px-8">
      <!-- Texto de apresentação -->
      <div class="text-center lg:text-left">
        <span class="text-sm font-semibold uppercase tracking-widest text-secondary">
          Barbearia
        </span>
        <h1 class="mt-4 font-display text-4xl font-bold leading-tight sm:text-5xl text-foreground md:text-6xl">
          Estilo e tradição em
          <span class="bg-linear-to-r from-gold-300 to-gold-500 bg-clip-text text-transparent">
            cada corte
          </span>
        </h1>
        <p class="mx-auto mt-6 max-w-xl text-lg text-muted lg:mx-0">
          Na Homens de Barba, cuidamos do seu visual com técnica, atenção aos detalhes e
          um ambiente feito para você relaxar. Corte, barba e acabamento no seu melhor.
        </p>

        <div class="mt-10 flex flex-wrap justify-center gap-4 lg:justify-start">
          <BaseButton href="#agendar">Agendar horário</BaseButton>
          <BaseButton href="#servicos" variant="outline">Ver serviços</BaseButton>
        </div>
      </div>

      <!-- Carrossel de imagens -->
      <div class="relative">
        <ImageCarousel :images="heroImages" />
      </div>
    </div>
  </section>
</template>
