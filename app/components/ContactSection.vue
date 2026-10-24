<script setup lang="ts">
import RevealOnScroll from "~/components/RevealOnScroll.vue";

// Dados de contato da barbearia
const info = {
  name: "Homens de Barba",
  phone: "(83) 99938-6200",
  phoneLink: "tel:+5583999386200",
  address: "Tv. Castelo Branco, Tavares - PB, 58753-000",
  hours: "Segunda a sábado, das 9h às 19h",
  instagram: "@homensdebarba_",
  instagramLink: "https://instagram.com/homensdebarba_",
};

const mapUrl = `https://www.google.com/maps?q=${encodeURIComponent(info.address)}&output=embed`;
const mapLink = `https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(info.address)}`;

const items = [
  {
    label: "Telefone",
    value: info.phone,
    href: info.phoneLink,
    icon: "M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.13.96.36 1.9.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.91.34 1.85.57 2.81.7A2 2 0 0 1 22 16.92z",
  },
  {
    label: "Endereço",
    value: info.address,
    icon: "M20 10c0 6-8 12-8 12S4 16 4 10a8 8 0 0 1 16 0zM12 13a3 3 0 1 0 0-6 3 3 0 0 0 0 6z",
  },
  {
    label: "Horário de atendimento",
    value: info.hours,
    icon: "M12 22a10 10 0 1 0 0-20 10 10 0 0 0 0 20zM12 6v6l4 2",
  },
  {
    label: "Instagram",
    value: info.instagram,
    href: info.instagramLink,
    icon: "M7 2h10a5 5 0 0 1 5 5v10a5 5 0 0 1-5 5H7a5 5 0 0 1-5-5V7a5 5 0 0 1 5-5zM16 11.37a4 4 0 1 1-7.914 1.173A4 4 0 0 1 16 11.37zM17.5 6.5h.01",
  },
];
</script>

<template>
  <section id="contato" class="relative isolate overflow-hidden bg-background">
    <div class="absolute inset-0 -z-10 bg-linear-to-br from-charcoal-950 via-charcoal-900 to-copper-900/60" aria-hidden="true" />
    <div class="absolute -left-24 top-10 -z-10 size-96 rounded-full bg-primary/15 blur-3xl" aria-hidden="true" />
    <div class="absolute -bottom-32 right-0 -z-10 size-[28rem] rounded-full bg-secondary/25 blur-3xl" aria-hidden="true" />
    <div class="mx-auto grid max-w-7xl items-center gap-8 px-5 py-16 sm:px-6 lg:grid-cols-2 lg:gap-12 lg:px-8 lg:py-28">
      <!-- Informações de contato -->
      <RevealOnScroll class="text-center lg:text-left">
        <span class="text-sm font-semibold uppercase tracking-widest text-secondary">
          Contato
        </span>
        <h2 class="mt-4 font-display text-3xl font-bold leading-tight text-foreground sm:text-4xl">
          {{ info.name }}
        </h2>
        <p class="mx-auto mt-4 max-w-xl text-base text-muted sm:text-lg lg:mx-0">
          Venha nos visitar ou fale com a gente para agendar o seu horário.
        </p>

        <ul class="mt-8 space-y-5 text-left">
          <li v-for="item in items" :key="item.label" class="flex items-start gap-4">
            <span class="flex size-11 shrink-0 items-center justify-center rounded-full border border-border bg-surface text-primary">
              <svg class="size-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
                <path :d="item.icon" />
              </svg>
            </span>
            <div>
              <p class="text-sm text-subtle">{{ item.label }}</p>
              <a v-if="item.href" :href="item.href" class="text-base font-semibold text-foreground transition hover:text-primary sm:text-lg">
                {{ item.value }}
              </a>
              <p v-else class="text-base font-semibold text-foreground sm:text-lg">{{ item.value }}</p>
            </div>
          </li>
        </ul>
      </RevealOnScroll>

      <!-- Mapa -->
      <RevealOnScroll :delay="150" class="relative">
        <div class="mx-auto aspect-4/3 w-full max-w-lg overflow-hidden rounded-card border border-primary/30 bg-surface shadow-glow-copper lg:max-w-none">
          <iframe
            :src="mapUrl"
            title="Localização da Homens de Barba no mapa"
            class="h-full w-full border-0"
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
            allowfullscreen
          />
        </div>
        <a
          :href="mapLink"
          target="_blank"
          rel="noopener"
          class="mt-3 block text-center text-sm font-semibold text-primary transition hover:text-primary-hover lg:text-left"
        >
          Abrir no Google Maps
        </a>
      </RevealOnScroll>
    </div>
  </section>
</template>
