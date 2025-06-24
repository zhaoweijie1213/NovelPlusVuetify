<template>
  <v-container class="py-4" fluid>
    <h1 class="text-h5 font-weight-bold mb-4">排行榜</h1>
    <v-table class="elevation-1" density="comfortable">
      <thead>
        <tr>
          <th class="text-left">排名</th>
          <th class="text-left">书名</th>
          <th class="text-left">作者</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="n in 10" :key="n">
          <td>{{ n }}</td>
          <td>范例小说 {{ n }}</td>
          <td>作者 {{ n }}</td>
        </tr>
      </tbody>
    </v-table>
  </v-container>
</template>

<script setup lang="ts">
//
</script>
