<template>
  <v-container class="py-4" fluid>
    <v-row>
      <v-col class="mb-4 mb-md-0" cols="12" md="3">
        <v-list density="compact" nav>
          <v-subheader>小说分类</v-subheader>
          <v-list-item v-for="item in categories" :key="item" :title="item" />
        </v-list>
      </v-col>
      <v-col cols="12" md="9">
        <v-carousel height="300" hide-delimiter-background>
          <v-carousel-item v-for="(item, i) in carouselItems" :key="i" :src="item.src" />
        </v-carousel>

        <h2 class="text-h5 font-weight-bold mt-8 mb-4">热门推荐</h2>
        <v-row>
          <v-col
            v-for="book in books"
            :key="book.id"
            cols="12"
            lg="3"
            md="4"
            sm="6"
          >
            <v-card :href="book.href" rounded="lg" :subtitle="book.author" :title="book.name">
              <v-img height="200" :src="book.cover" />
            </v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
  interface Book {
    id: number
    name: string
    author: string
    cover: string
    href: string
  }

  const carouselItems = [
    { src: '/images/smlcover.png' },
    { src: '/images/smlcover.png' },
    { src: '/images/smlcover.png' },
  ]

  const categories = [
    '玄幻奇幻',
    '武侠仙侠',
    '都市言情',
    '历史军事',
    '网游竞技',
    '科幻灵异',
    '女生频道',
  ]

  const books: Book[] = [
    { id: 1, name: '范例小说一', author: '作者A', cover: '/images/smlcover.png', href: '#' },
    { id: 2, name: '范例小说二', author: '作者B', cover: '/images/smlcover.png', href: '#' },
    { id: 3, name: '范例小说三', author: '作者C', cover: '/images/smlcover.png', href: '#' },
    { id: 4, name: '范例小说四', author: '作者D', cover: '/images/smlcover.png', href: '#' },
  ]
</script>
