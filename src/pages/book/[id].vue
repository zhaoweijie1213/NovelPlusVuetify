<template>
  <v-container class="py-4" fluid>
    <v-breadcrumbs class="mb-4" :items="breadcrumbs" />
    <v-row>
      <v-col cols="12" md="3">
        <v-img height="200" :src="book.cover" />
      </v-col>
      <v-col cols="12" md="9">
        <h1 class="text-h5 font-weight-bold mb-2">{{ book.title }}</h1>
        <div class="mb-2">作者：{{ book.author }}</div>
        <div>简介：{{ book.description }}</div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
  import { computed } from 'vue'
  import { useRoute } from 'vue-router'

  interface Book {
    id: string
    title: string
    author: string
    cover: string
    category: string
    description: string
  }

  const route = useRoute()
  // In a real app data would come from an API
  const book = computed<Book>(() => ({
    id: (route.params as any).id as string,
    title: '重生八零：我在长白山猎野味发家',
    author: '佚名',
    cover: '/images/smlcover.png',
    category: '都市言情',
    description: '这是一本示例小说的简介，用于演示详情页面。',
  }))

  const breadcrumbs = computed(() => [
    { title: '小说精品屋', disabled: false, to: '/' },
    { title: book.value.category, disabled: false, to: '/library' },
    { title: book.value.title, disabled: true },
  ])
</script>
