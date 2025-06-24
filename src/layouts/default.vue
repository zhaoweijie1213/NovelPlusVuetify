<template>
  <AppHeader @toggle-drawer="drawer = !drawer" />
  <v-navigation-drawer
    v-model="drawer"
    app
    :permanent="!mobile"
    temporary
  >
    <v-list nav>
      <v-list-item prepend-icon="mdi-home" title="首页" to="/" />
      <v-list-item prepend-icon="mdi-book-open-page-variant" title="书库" to="/library" />
      <v-list-item prepend-icon="mdi-format-list-numbered" title="排行榜" to="/rank" />
      <v-list-item prepend-icon="mdi-account" title="作家专区" to="/author" />
    </v-list>
  </v-navigation-drawer>
  <v-main>
    <v-container fluid>
      <v-row justify="center">
        <v-col cols="12" md="10">
          <v-sheet class="pa-4" color="white" rounded="lg">
            <router-view />
          </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
  <AppFooter />
</template>

<script lang="ts" setup>
  import { ref } from 'vue'
  import { useDisplay } from 'vuetify'

  const drawer = ref(false)
  const { mobile } = useDisplay()
</script>
