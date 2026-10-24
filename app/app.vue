<script setup lang="ts">
import SiteHeader from "~/components/SiteHeader.vue";
import SiteFooter from "~/components/SiteFooter.vue";

useHead({
  title: "Homens de Barba",
  htmlAttrs: { lang: "pt-BR" },
  link: [{ rel: "icon", type: "image/png", href: "/images/logo.png" }],
});
</script>

<template>
  <div class="min-h-screen bg-background text-foreground">
    <NuxtRouteAnnouncer />
    <SiteHeader />
    <NuxtPage />
    <SiteFooter />
  </div>
</template>
