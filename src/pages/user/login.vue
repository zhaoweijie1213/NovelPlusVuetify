<template>
  <v-container class="py-4" fluid>
    <v-row justify="center">
      <v-col cols="12" lg="4" md="6" sm="8">
        <h1 class="text-h5 font-weight-bold mb-4 text-center">用户登录</h1>
        <v-text-field label="账号" prepend-icon="mdi-account" />
        <v-text-field label="密码" prepend-icon="mdi-lock" type="password" />
        <v-btn block class="mt-2" color="primary">登录</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
//
</script>
