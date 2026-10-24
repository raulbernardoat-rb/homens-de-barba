<script setup lang="ts">
import { computed, ref } from "vue";
import ProductCard from "~/components/ProductCard.vue";

interface Product {
  name: string;
  price: string;
  image?: string;
}

interface ProductLine {
  id: string;
  name: string;
  products: Product[];
}

const lines: ProductLine[] = [
  {
    id: "fox",
    name: "Fox for Men",
    products: [
      { name: "Live In 240 ml", price: "R$ 40" },
      { name: "Shampoo Anticaspa", price: "R$ 35" },
      { name: "Hidratante Facial Pós-Barba 120 ml", price: "R$ 35" },
      { name: "Shampoo 4 em 1", price: "R$ 30" },
      { name: "Balm para Barba", price: "R$ 35" },
    ],
  },
  {
    id: "garden",
    name: "Garden for Men",
    products: [
      { name: "Pomada Modeladora Efeito Teia", price: "R$ 29,99" },
      { name: "Pomada Modeladora Efeito Neutro", price: "R$ 24,99" },
      { name: "Pomada Modeladora Efeito Cera de Abelha", price: "R$ 29,99" },
      { name: "Pomada Modeladora Névoa", price: "R$ 29,99" },
      { name: "Óleo Siliconado", price: "R$ 34,99" },
      { name: "Balm", price: "R$ 44,99" },
      { name: "Pomada Modeladora Efeito Mate", price: "R$ 34,99" },
      { name: "Pomada Modeladora Efeito Black", price: "R$ 29,99" },
    ],
  },
  {
    id: "minoxidil",
    name: "Minoxidil Kirkland",
    products: [{ name: "Minoxidil Kirkland", price: "R$ 99,99" }],
  },
  {
    id: "shampoo",
    name: "Shampoo Anticaspa",
    products: [{ name: "Shampoo Anticaspa", price: "R$ 20" }],
  },
  {
    id: "maquina",
    name: "Máquina de Corte",
    products: [{ name: "Máquina de Corte", price: "R$ 40" }],
  },
];

const selectedId = ref(lines[0]!.id);
const selectedLine = computed(() => lines.find((line) => line.id === selectedId.value)!);
</script>

<template>
  <section id="produtos" class="bg-surface">
    <div class="mx-auto max-w-7xl px-5 py-14 sm:px-6 lg:px-8 lg:py-24">
      <div class="mx-auto max-w-2xl text-center">
        <span class="text-sm font-semibold uppercase tracking-widest text-secondary">
          Produtos
        </span>
        <h2 class="mt-4 font-display text-3xl font-bold text-foreground sm:text-4xl">
          Cuide do seu
          <span class="bg-linear-to-r from-gold-300 to-gold-500 bg-clip-text text-transparent">
            visual em casa
          </span>
        </h2>
        <p class="mt-4 text-base text-muted sm:text-lg">
          Escolha uma linha para ver os produtos.
        </p>
      </div>

      <div class="mt-10 grid gap-6 lg:mt-14 lg:grid-cols-[18rem_1fr] lg:gap-10">
        <!-- Linhas: lista na lateral (computador) / faixa deslizável (celular) -->
        <div
          role="tablist"
          aria-label="Linhas de produtos"
          class="-mx-5 flex gap-3 overflow-x-auto px-5 pb-2 [-ms-overflow-style:none] [scrollbar-width:none] sm:-mx-6 sm:px-6 lg:mx-0 lg:flex-col lg:overflow-visible lg:px-0 lg:pb-0 [&::-webkit-scrollbar]:hidden"
        >
          <button
            v-for="line in lines"
            :key="line.id"
            type="button"
            role="tab"
            :aria-selected="line.id === selectedId"
            :class="[
              'shrink-0 rounded-lg border px-5 py-3 text-left text-sm font-semibold transition focus-visible:outline-2 focus-visible:outline-ring sm:text-base',
              line.id === selectedId
                ? 'border-primary bg-primary text-primary-foreground shadow-glow'
                : 'border-border bg-surface-raised text-foreground hover:border-primary hover:text-primary',
            ]"
            @click="selectedId = line.id"
          >
            {{ line.name }}
          </button>
        </div>

        <!-- Produtos da linha selecionada -->
        <div role="tabpanel">
          <h3 class="font-display text-xl font-semibold text-accent sm:text-2xl">
            {{ selectedLine.name }}
          </h3>
          <div class="mt-5 grid grid-cols-2 gap-4 sm:gap-6 xl:grid-cols-3">
            <ProductCard
              v-for="product in selectedLine.products"
              :key="product.name"
              :image="product.image"
              :name="product.name"
              :price="product.price"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
