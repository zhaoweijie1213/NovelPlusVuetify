<template>
  <v-card class="pa-2" flat>
    <div v-for="(group, index) in groups" :key="index">
      <v-list density="compact">
        <v-list-item v-if="group[0]" class="text-center">
          <v-list-item-title class="font-weight-bold">
            <v-btn variant="text" @click="goBook(group[0].id)">{{ group[0].name }}</v-btn>
          </v-list-item-title>
        </v-list-item>
        <v-list-item
          v-for="book in group.slice(1)"
          :key="book.id"
          :title="book.name"
          @click="goBook(book.id)"
        />
      </v-list>
      <v-divider v-if="index < groups.length - 1" class="my-2" />
    </div>
  </v-card>
</template>

<script setup lang="ts">
  import { computed } from 'vue'
  import { useRouter } from 'vue-router'

  interface Book {
    id: number
    name: string
  }

  const props = defineProps<{ books: Book[] }>()
  const router = useRouter()

  const groups = computed(() => [props.books.slice(0, 3), props.books.slice(3, 5)])

  function goBook (id: number) {
    router.push(`/book/${id}`)
  }
</script>
