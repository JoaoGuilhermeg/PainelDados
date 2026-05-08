<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const items: NavigationMenuItem[][] = [
    [
    {
    label: 'Painel de Dados',
    icon:'i-lucide-layout-list',
    active:true
    },
],
[{
    label: 'Gestão de Relatórios',
    icon: 'i-lucide-chart-column-big'
}],
[
    {
    label: 'Personalização',
    icon:'i-lucide-settings'
}],
]
</script>

<template>  
<UDashboardGroup>
   <UDashboardSidebar collapsible resizable :ui="{ footer: 'border-r border-default'}">
        <template #header = "{ collapsed }">
            <Logo v-if="!collapsed" class="h-2 w-auto shrink-0" />
            <UIcon v-else name="i-lucide-chart-column-big" class="size-5 text-primary nx-auto" />
        </template>
            
        <template #default = "{collapsed}">
            <div class="h-screen overflow-hidden">
            <UNavigationMenu
            :collapsed="collapsed"
            :items="items[0]"
            orientation="vertical"
            />

            <UNavigationMenu
            :collapsed="collapsed"
            :items="items[1]"
            orientation="vertical"
            class="mt-auto"
            />

            <UNavigationMenu
            :collapsed="collapsed"
            :items="items[2]"
            orientation="vertical"
            class="flex-col mt-auto"
            />
            </div>
        </template>
    </UDashboardSidebar>
<UDashboardPanel>
    <slot/>
</UDashboardPanel>
</UDashboardGroup>
</template>
    
  