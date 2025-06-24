<template>
  <v-row class="book-carousel" no-gutters>
    <!-- 左侧大图：垂直轮播 -->
    <v-col class="flex-grow-1">
      <v-carousel
        v-model="current"
        cycle
        direction="vertical"
        :height="height"
        hide-delimiters
        :interval="4000"
        :show-arrows="false"
        vertical-delimiters="right"
      >
        <v-carousel-item
          v-for="(item, idx) in items"
          :key="item.id"
        >
          <!-- 包一层，用于给当前页加边框 -->
          <div :class="['slide-wrapper', { 'active-slide': idx === current }]">
            <v-img cover :height="height" :src="item.cover" />
          </div>
        </v-carousel-item>
      </v-carousel>
    </v-col>

    <!-- 右侧缩略图列（34 px 宽，2:3 比例）-->
    <v-col
      class="thumb-col d-flex flex-column align-center ps-3"
      cols="auto"
      :style="{ height: height + 'px' }"
    >
      <v-responsive
        v-for="(item, idx) in items"
        :key="item.id"
        aspect-ratio="2/3"
        class="my-1 thumb"
        :class="{ 'active-thumb': idx === current }"
        style="width: 34px"
        @mouseover="current = idx"
      >
        <v-img cover :src="item.cover" />
      </v-responsive>
    </v-col>
  </v-row>
</template>

<script setup lang="ts">
  import type { Book } from '@/types/novel'
  import { ref } from 'vue'

  const props = defineProps<{ items: Book[], height?: number }>()
  const height = props.height ?? 380
  const current = ref(0) // 纯 number，避免类型不一致
</script>

<style scoped>
/* -------- 大图高亮边框 -------- */
.slide-wrapper {
  width: 100%;
  height: 100%;
}
.active-slide {
  border: 2px solid var(--v-theme-primary);
  border-radius: 4px;
  box-sizing: border-box;
}

/* -------- 缩略图列 -------- */
.thumb-col { min-width: 0 !important; }

/* 缩略图样式（已去掉 hover 放大/透明）*/
.thumb {
  border-radius: 4px;
  cursor: pointer;
  box-sizing: border-box;
}

/* 当前缩略图边框高亮 */
.active-thumb {
  border: 2px solid var(--v-theme-primary);
}

/* 轮播容器防止溢出 */
.book-carousel { overflow: hidden; }
</style>
