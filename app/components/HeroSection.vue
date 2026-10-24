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
  <section id="inicio" class="relative isolate overflow-hidden bg-background">
    <!-- Degradê de fundo -->
    <div
      class="absolute inset-0 -z-10 bg-linear-to-br from-charcoal-950 via-charcoal-900 to-copper-900/70"
      aria-hidden="true"
    />
    <div
      class="absolute -left-32 -top-32 -z-10 size-[28rem] rounded-full bg-primary/25 blur-3xl"
      aria-hidden="true"
    />
    <div
      class="absolute -bottom-40 right-0 -z-10 size-[32rem] rounded-full bg-secondary/30 blur-3xl"
      aria-hidden="true"
    />
    <!-- Textura de pontos -->
    <div
      class="absolute inset-0 -z-10 opacity-[0.07] [background-image:radial-gradient(var(--color-gold-200)_1px,transparent_1px)] [background-size:28px_28px] [mask-image:radial-gradient(ellipse_at_center,black_30%,transparent_75%)]"
      aria-hidden="true"
    />

    <div class="mx-auto grid min-h-svh max-w-7xl items-center gap-10 px-5 pb-12 pt-28 sm:px-6 lg:grid-cols-2 lg:gap-12 lg:px-8 lg:pt-24">
      <!-- Texto de apresentação -->
      <div class="animate-fade-up text-center lg:text-left">
        <!-- Logo + nome da barbearia -->
        <div class="flex items-center justify-center gap-4 lg:justify-start">
          <img
            src="/images/logo.png"
            alt="Logo Homens de Barba"
            width="150"
            height="150"
            class="size-20 rounded-full shadow-glow-copper ring-2 ring-primary/40 sm:size-24"
          />
          <div class="text-left">
            <p class="bg-linear-to-r from-gold-200 via-gold-400 to-copper-400 bg-clip-text font-display text-3xl font-bold leading-none text-transparent sm:text-4xl">
              Homens de Barba
            </p>
            <p class="mt-2 text-xs font-semibold uppercase tracking-[0.3em] text-secondary sm:text-sm">
              Barbearia
            </p>
          </div>
        </div>
        <h1 class="mt-8 font-display text-4xl font-bold leading-tight text-foreground sm:text-5xl md:text-6xl">
          Estilo e tradição em
          <span class="bg-linear-to-r from-gold-200 via-gold-400 to-copper-400 bg-clip-text text-transparent">
            cada corte
          </span>
        </h1>
        <p class="mx-auto mt-6 max-w-xl text-lg text-muted lg:mx-0">
          Na Homens de Barba, cuidamos do seu visual com técnica, atenção aos detalhes e
          um ambiente feito para você relaxar. Corte, barba e acabamento no seu melhor.
        </p>

        <div class="mt-10 flex flex-wrap justify-center gap-4 lg:justify-start">
          <BaseButton href="#contato">Agendar horário</BaseButton>
          <BaseButton href="#servicos" variant="outline">Ver serviços</BaseButton>
        </div>
      </div>

      <!-- Carrossel de imagens com anéis (como na logo) -->
      <div class="relative flex justify-center py-6">
        <div
          class="absolute left-1/2 top-1/2 -z-10 aspect-square h-[108%] -translate-x-1/2 -translate-y-1/2 rounded-full border-2 border-secondary/50"
          aria-hidden="true"
        />
        <div
          class="absolute left-1/2 top-1/2 -z-10 aspect-square h-[120%] -translate-x-1/2 -translate-y-1/2 animate-spin-slow rounded-full border border-dashed border-primary/50"
          aria-hidden="true"
        />
        <div class="absolute -inset-2 -z-10 rounded-[1.1rem] bg-linear-to-br from-gold-300/60 via-transparent to-copper-500/60 blur-xl" aria-hidden="true" />
        <ImageCarousel :images="heroImages" />
      </div>
    </div>
  </section>
</template>
