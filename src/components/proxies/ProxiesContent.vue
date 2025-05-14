<script setup lang="ts">
import { handlerProxySelect } from '@/store/proxies'
import { twoColumnProxyGroup } from '@/store/settings'
import ProxyNodeCard from './ProxyNodeCard.vue'
import ProxyNodeGrid from './ProxyNodeGrid.vue'

defineProps<{
  name: string
  now: string
  renderProxies: string[]
  showFullContent: boolean
}>()
</script>

<template>
  <ProxyNodeGrid>
    <ProxyNodeCard
      v-for="node in showFullContent
        ? renderProxies
        : renderProxies.slice(0, twoColumnProxyGroup ? 48 : 96)"
      :key="node"
      :name="node"
      :group-name="name"
      :active="node === now"
      @click.stop="handlerProxySelect(name, node)"
    />
  </ProxyNodeGrid>
</template>
