<template>
  <v-container class="py-4" fluid>
    <h1 class="text-h5 font-weight-bold mb-4">书库</h1>
    <v-row>
      <v-col
        v-for="n in 8"
        :key="n"
        cols="12"
        lg="3"
        md="4"
        sm="6"
      >
        <v-card rounded="lg" :to="`/book/${n}`">
          <v-img height="200" src="/images/smlcover.png" />
          <v-card-title>示例书籍 {{ n }}</v-card-title>
          <v-card-subtitle>作者 {{ n }}</v-card-subtitle>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
//
</script>
