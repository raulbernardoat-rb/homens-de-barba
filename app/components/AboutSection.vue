<script setup lang="ts">
import BaseButton from "~/components/BaseButton.vue";
</script>

<template>
  <section id="sobre" class="bg-white">
    <div class="mx-auto grid max-w-7xl items-center gap-8 px-5 py-14 sm:px-6 lg:grid-cols-2 lg:gap-12 lg:px-8 lg:py-24">
      <!-- Texto de apresentação -->
      <div class="text-center lg:text-left">
        <span class="text-sm font-semibold uppercase tracking-widest text-copper-600">
          Sobre nós
        </span>
        <h2 class="mt-4 font-display text-3xl font-bold leading-tight text-charcoal-900 sm:text-4xl">
          Mais que uma barbearia, um
          <span class="bg-linear-to-r from-gold-600 to-gold-400 bg-clip-text text-transparent">
            lugar para você
          </span>
        </h2>
        <p class="mx-auto mt-6 max-w-xl text-base text-charcoal-600 sm:text-lg lg:mx-0">
          A Homens de Barba nasceu para entregar um atendimento de verdade: com técnica,
          pontualidade e respeito ao seu estilo. Aqui você encontra um ambiente confortável,
          profissionais dedicados e o cuidado que seu visual merece.
        </p>
        <p class="mx-auto mt-4 max-w-xl text-base text-charcoal-600 sm:text-lg lg:mx-0">
          Cada corte e cada barba são feitos com atenção aos detalhes, para você sair
          daqui confiante e com a cara de quem se cuida.
        </p>

        <div class="mt-8 flex justify-center lg:justify-start">
          <BaseButton href="#agendar">Agendar horário</BaseButton>
        </div>
      </div>

      <!-- Imagem da barbearia -->
      <div class="relative">
        <img
          src="/images/barbearia-dentro.jpg"
          alt="Interior da barbearia Homens de Barba"
          loading="lazy"
          class="mx-auto aspect-4/3 w-full max-w-lg rounded-card border border-charcoal-200 object-cover shadow-xl shadow-charcoal-900/15 lg:max-w-none"
        />
      </div>
    </div>
  </section>
</template>
