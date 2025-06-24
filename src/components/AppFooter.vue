<template>
  <v-footer class="text-center d-flex flex-column ga-2 py-4">
    <div class="d-flex ga-3">
      <v-btn
        v-for="icon in icons"
        :key="icon"
        density="comfortable"
        :icon="icon"
        variant="text"
      />
    </div>
    <v-divider class="my-2" thickness="2" width="50" />
    <div class="text-caption font-weight-regular opacity-60">
      Copyright (C) xxyopen.com All rights reserved  小说精品屋版权所有
    </div>
    <v-divider />
    <div>
      {{ new Date().getFullYear() }} — <strong>小说精品屋</strong>
    </div>
  </v-footer>
</template>

<script setup lang="ts">
  const icons = [
    'mdi-facebook',
    'mdi-twitter',
    'mdi-linkedin',
    'mdi-instagram',
  ]
</script>
