<script setup>
useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/chart-column-big.png' }
  ],
  htmlAttrs: {
    lang: 'pt-br'
  }
})

const title = 'Portal de Dados'
const description = 'Portal de Dados para acesso aos Dashboard'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
})
</script>

<template>
  <UApp>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>

  </UApp>
</template>
