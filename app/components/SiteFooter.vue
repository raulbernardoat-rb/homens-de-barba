<script setup lang="ts">
const year = new Date().getFullYear();
</script>

<template>
  <footer class="border-t border-border/60 bg-charcoal-950">
    <div class="mx-auto flex max-w-7xl flex-col items-center gap-6 px-5 py-10 text-center sm:px-6 md:flex-row md:justify-between md:text-left lg:px-8">
      <div class="flex flex-col items-center gap-3 md:flex-row md:gap-4">
        <img src="/images/logo.png" alt="Logo Homens de Barba" width="150" height="150" loading="lazy" class="size-16 rounded-full" />
        <div>
        <p class="bg-linear-to-r from-gold-300 to-copper-400 bg-clip-text font-display text-xl font-bold text-transparent">
          Homens de Barba
        </p>
        <p class="mt-1 text-sm text-subtle">Corte, barba e estilo com tradição.</p>
        </div>
      </div>

      <nav class="flex flex-wrap justify-center gap-x-6 gap-y-2 text-sm text-muted" aria-label="Rodapé">
        <a href="#sobre" class="transition hover:text-primary">Sobre</a>
        <a href="#servicos" class="transition hover:text-primary">Serviços</a>
        <a href="#produtos" class="transition hover:text-primary">Produtos</a>
        <a href="#contato" class="transition hover:text-primary">Contato</a>
        <a href="https://instagram.com/homensdebarba_" target="_blank" rel="noopener" class="transition hover:text-primary">
          Instagram
        </a>
      </nav>

      <p class="text-xs text-subtle">© {{ year }} Homens de Barba. Todos os direitos reservados.</p>
    </div>
  </footer>
</template>
