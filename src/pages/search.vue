<template>
  <v-container class="py-4" fluid>
    <h1 class="text-h5 font-weight-bold mb-4">搜索结果</h1>
    <v-alert class="mb-4" type="info">搜索功能仅为示例</v-alert>
    <v-row>
      <v-col
        v-for="n in 5"
        :key="n"
        cols="12"
        lg="3"
        md="4"
        sm="6"
      >
        <v-card rounded="lg" :to="`/book/${n}`">
          <v-img height="200" src="/images/smlcover.png" />
          <v-card-title>搜索结果 {{ n }}</v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
//
</script>
