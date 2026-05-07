<script setup lang="ts">
import { ref } from 'vue'


definePageMeta
({
  layout: 'default'
})
const cards = ref([
  {
    title: 'Total de relatórios',
    description: 'Relatórios disponíveis para o seu perfil',
    icon:'i-lucide-file-check',
    to:'/total'
  },
  {
    title: 'Favoritos',
    description: 'Relatórios marcados',
    icon:'i-lucide-star',
    to:'/favoritos'
  },
  {
    title: 'Recentes',
    description: 'Relatórios acessados nos ultimos 7 dias',
    icon:'i-lucide-clock-10',
    to:'/recentes'
  }
])
</script>

<template>
  <UDashboardPanel>
    <UContainer>
    <template #header>   
      <UDashboardNavbar />
   </template>
  </UContainer>
   <template>
     <UContainer class="py-10">
    <div class="mb-8">
      <h2 class="text-3xl font-bold text-gray-900 dark:text-white">
        Painel
      </h2>
    </div>
    <UPageGrid class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
      <UPageCard v-for="(card, index) in cards" :key="index" v-bind="card" />
    </UPageGrid>
  </UContainer>
  <UContainer class="py-2">
    <div class=" flex mb-12">
    </div>
  </UContainer>
</template>
  </UDashboardPanel>
</template>
