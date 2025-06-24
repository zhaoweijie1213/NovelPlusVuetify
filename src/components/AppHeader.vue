<template>
  <v-app-bar color="primary" density="comfortable" elevate-on-scroll scroll-behavior="hide">
    <template #prepend>
      <v-app-bar-nav-icon @click="$emit('toggle-drawer')" />
    </template>
    <v-app-bar-title>
      <RouterLink class="d-flex text-white text-decoration-none" to="/">
        <span class="text-h6">{{ siteName }}</span>
      </RouterLink>
    </v-app-bar-title>
    <v-spacer />
    <v-text-field
      v-model="searchKey"
      class="mx-2"
      density="compact"
      hide-details
      label="搜索书名、作者"
      variant="solo-inverted"
    />
    <v-btn class="mr-2" icon="mdi-magnify" @click="doSearch" />
    <v-btn class="mr-2" icon @click="toggleTheme">
      <v-icon>{{ themeIcon }}</v-icon>
    </v-btn>
    <v-btn variant="text">登录</v-btn>
    <v-btn variant="text">注册</v-btn>
  </v-app-bar>
</template>

<script setup lang="ts">
  import { computed, ref } from 'vue'
  import { useRouter } from 'vue-router'
  import { useAppStore } from '@/stores/app'

  defineEmits(['toggle-drawer'])

  const searchKey = ref('')
  const router = useRouter()
  const siteName = '小说精品屋'

  function doSearch () {
    if (searchKey.value) {
      router.push(`/search?key=${encodeURIComponent(searchKey.value)}`)
    }
  }

  const appStore = useAppStore()
  const themeIcon = computed(() => appStore.theme === 'dark' ? 'mdi-white-balance-sunny' : 'mdi-weather-night')
  function toggleTheme () {
    appStore.toggleTheme()
  }
</script>
