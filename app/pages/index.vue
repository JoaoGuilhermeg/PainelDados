<script setup lang="ts">
import { ref, computed } from 'vue'

definePageMeta({
  layout: 'default'
})

// 1. Termo de busca (reativo)
const busca = ref('')

// 2. Seus cards originais
const cards = ref([
  {
    title: 'Total de relatórios',
    description: 'Relatórios disponíveis para o seu perfil',
    icon: 'i-lucide-file-check',
  },
  {
    title: 'Favoritos',
    description: 'Relatórios marcados',
    icon: 'i-lucide-star',
  },
  {
    title: 'Recentes',
    description: 'Relatórios acessados nos ultimos 7 dias',
    icon: 'i-lucide-clock-10',
  }
])

// 3. Lógica de pesquisa dinâmica
const cardsFiltrados = computed(() => {
  if (!busca.value) return cards.value
  
  const termo = busca.value.toLowerCase().trim()
  return cards.value.filter(card => 
    card.title.toLowerCase().includes(termo) || 
    card.description.toLowerCase().includes(termo)
  )
})
</script>

<template>
  <UDashboardPanel grow>
    <UDashboardNavbar>
      <template #left>
         <div class="w-full max-w-2xl px-4">
            <UInput
              v-model="busca"
              icon="i-lucide-search"
              placeholder="Pesquisar relatórios"
              size="xl"
              class="shadow-sm"
            />
          </div>
        <UDashboardNavbarToggle />
  
      </template>
    </UDashboardNavbar>

    <UDashboardPanel class="p-4">
      <UContainer class="max-w-none p-0 flex flex-col">
        <h1 class="text-xl md:text-2xl font-bold ml-2">Painel</h1>
        <UPageGrid class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 md:gap-8">
          <UPageCard 
            v-for="(card, index) in cardsFiltrados" 
            :key="index" 
            v-bind="card" 
          />
        </UPageGrid>

        <div v-if="cardsFiltrados.length === 0" class="text-center py-20">
          <p class="text-gray-500">Nenhum resultado para "{{ busca }}"</p>
        </div>

      </UContainer>
    </UDashboardPanel>
  </UDashboardPanel>
</template>