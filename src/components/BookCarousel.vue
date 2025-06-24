<template>
  <v-row class="book-carousel" no-gutters>
    <v-col class="flex-grow-1">
      <v-window v-model="current" class="h-100">
        <v-window-item v-for="(item, index) in items" :key="item.id" :value="index">
          <v-img cover :height="height" :src="item.cover" />
        </v-window-item>
      </v-window>
    </v-col>
    <v-col class="d-flex flex-column align-center" :style="{ height: height + 'px', width: '70px' }">
      <v-img
        v-for="(item, index) in items"
        :key="item.id"
        class="my-1 cursor-pointer"
        :class="{ 'active-thumb': index === current }"
        cover
        :height="thumbHeight"
        :src="item.cover"
        @click="current = index"
      />
    </v-col>
  </v-row>
</template>

<script setup lang="ts">
  import { computed, onBeforeUnmount, onMounted, ref } from 'vue'

  interface Book {
    id: number
    cover: string
  }

  const props = defineProps<{ items: Book[], height?: number }>()
  const current = ref(0)
  const interval = ref<number>()
  const height = props.height ?? 300
  const thumbHeight = computed(() => `${height / props.items.length}px`)

  onMounted(() => {
    interval.value = window.setInterval(() => {
      current.value = (current.value + 1) % props.items.length
    }, 3000)
  })

  onBeforeUnmount(() => {
    clearInterval(interval.value)
  })
</script>

<style scoped>
.active-thumb {
  border: 2px solid var(--v-theme-primary);
}
.book-carousel {
  overflow: hidden;
}
</style>
