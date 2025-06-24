<template>
  <v-app-bar color="primary" density="comfortable" elevate-on-scroll scroll-behavior="hide">
    <v-app-bar-nav-icon class="d-lg-none" @click="$emit('toggle-drawer')" />
    <v-toolbar-title class="text-h6">
      <RouterLink class="text-white text-decoration-none" to="/">{{ siteName }}</RouterLink>
    </v-toolbar-title>
    <v-toolbar-items class="hidden-sm-and-down">
      <RouterLink to="/">
        <v-btn class="text-white" variant="text">首页</v-btn>
      </RouterLink>
      <RouterLink to="/library">
        <v-btn class="text-white" variant="text">书库</v-btn>
      </RouterLink>
      <RouterLink to="/rank">
        <v-btn class="text-white" variant="text">排行榜</v-btn>
      </RouterLink>
      <RouterLink to="/author">
        <v-btn class="text-white" variant="text">作家专区</v-btn>
      </RouterLink>
    </v-toolbar-items>
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
