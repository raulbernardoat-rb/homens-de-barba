<script setup lang="ts">
type Variant = 'primary' | 'secondary' | 'outline'

const props = withDefaults(
  defineProps<{
    href?: string
    variant?: Variant
  }>(),
  { href: '#', variant: 'primary' }
)

const variants: Record<Variant, string> = {
  primary:
    'bg-linear-to-r from-gold-300 via-gold-400 to-gold-500 text-primary-foreground shadow-glow hover:-translate-y-0.5 hover:shadow-glow-copper hover:brightness-110 active:translate-y-0',
  secondary:
    'bg-secondary text-secondary-foreground hover:bg-secondary-hover active:bg-secondary-active',
  outline:
    'border border-border text-foreground hover:border-primary hover:text-primary'
}
</script>

<template>
  <a
    :href="props.href"
    :class="[
      'inline-block rounded-lg px-8 py-3 font-semibold transition duration-300 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-ring',
      variants[props.variant]
    ]"
  >
    <slot />
  </a>
</template>
