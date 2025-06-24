<template>
  <v-list density="compact" nav>
    <v-subheader>
      <h2>本周强推</h2>
    </v-subheader>
    <v-list-item
      v-for="book in books"
      :key="book.id"
      :subtitle="book.author"
      :title="book.name"
      :to="`/book/${book.id}`"
    >
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
