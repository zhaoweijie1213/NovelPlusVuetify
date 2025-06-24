<template>
  <v-list density="compact" nav>
    <v-subheader>更新榜单</v-subheader>
    <v-list-item v-for="book in books" :key="book.id" :subtitle="book.author" :title="book.name">
      <template #prepend>
        <v-avatar :image="book.cover" size="40" />
      </template>
    </v-list-item>
  </v-list>
</template>

<script setup lang="ts">
  interface Book {
    id: number
    name: string
    author: string
    cover: string
    href: string
  }

  defineProps<{ books: Book[] }>()
</script>
