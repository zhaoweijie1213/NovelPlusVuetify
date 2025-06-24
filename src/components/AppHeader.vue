<template>
  <v-app-bar color="primary" density="comfortable" elevate-on-scroll scroll-behavior="hide">
    <v-app-bar-nav-icon class="d-md-none" @click="$emit('toggle-drawer')" />
    <RouterLink class="d-flex align-center text-white text-decoration-none mr-4" to="/">
      <v-img class="mr-2" height="32" src="/src/assets/logo.png" />
      <span class="text-h6">{{ siteName }}</span>
    </RouterLink>
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
    <RouterLink to="/user/login">
      <v-btn variant="text">登录</v-btn>
    </RouterLink>
    <RouterLink to="/user/register">
      <v-btn variant="text">注册</v-btn>
    </RouterLink>
  </v-app-bar>
  <v-toolbar class="d-none d-md-flex" color="primary" density="comfortable">
    <RouterLink class="text-white mx-2" to="/">首页</RouterLink>
    <RouterLink class="text-white mx-2" to="/library">全部作品</RouterLink>
    <RouterLink class="text-white mx-2" to="/rank">排行榜</RouterLink>
    <RouterLink class="text-white mx-2" to="/author">作家专区</RouterLink>
  </v-toolbar>
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
