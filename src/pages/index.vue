<template>
  <v-container class="py-4" fluid>
    <v-row class="mb-8">
      <v-col cols="12" md="10">
        <v-carousel height="300" hide-delimiter-background>
          <v-carousel-item v-for="(item, i) in carouselItems" :key="i" :src="item.src" />
        </v-carousel>
      </v-col>
      <v-col cols="12" md="2">
        <WeekRecommend :books="weekBooks" />
      </v-col>
    </v-row>

    <v-row class="mb-8">
      <v-col cols="12" md="10">
        <h2 class="text-h5 font-weight-bold mb-4">热门推荐</h2>
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
      <v-col cols="12" md="2">
        <ClickRank :books="clickBooks" />
      </v-col>
    </v-row>

    <v-row class="mb-8">
      <v-col cols="12" md="10">
        <h2 class="text-h5 font-weight-bold mb-4">精品推荐</h2>
        <v-row>
          <v-col
            v-for="book in goodBooks"
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
      <v-col cols="12" md="2">
        <NewBookRank :books="newBooks" />
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" md="10">
        <h2 class="text-h5 font-weight-bold mb-4">最新更新</h2>
        <v-table density="compact">
          <thead>
            <tr>
              <th class="text-left">书名</th>
              <th class="text-left">作者</th>
              <th class="text-left">时间</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in updateList" :key="item.id">
              <td>{{ item.name }}</td>
              <td>{{ item.author }}</td>
              <td>{{ item.time }}</td>
            </tr>
          </tbody>
        </v-table>
      </v-col>
      <v-col cols="12" md="2">
        <UpdateRank :books="updateRank" />
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

  const books: Book[] = [
    { id: 1, name: '范例小说一', author: '作者A', cover: '/images/smlcover.png', href: '#' },
    { id: 2, name: '范例小说二', author: '作者B', cover: '/images/smlcover.png', href: '#' },
    { id: 3, name: '范例小说三', author: '作者C', cover: '/images/smlcover.png', href: '#' },
    { id: 4, name: '范例小说四', author: '作者D', cover: '/images/smlcover.png', href: '#' },
  ]

  const weekBooks: Book[] = [
    { id: 5, name: '周推一', author: '作者E', cover: '/images/smlcover.png', href: '#' },
    { id: 6, name: '周推二', author: '作者F', cover: '/images/smlcover.png', href: '#' },
    { id: 7, name: '周推三', author: '作者G', cover: '/images/smlcover.png', href: '#' },
    { id: 8, name: '周推四', author: '作者H', cover: '/images/smlcover.png', href: '#' },
  ]

  const goodBooks: Book[] = [
    { id: 9, name: '精品一', author: '作者I', cover: '/images/smlcover.png', href: '#' },
    { id: 10, name: '精品二', author: '作者J', cover: '/images/smlcover.png', href: '#' },
    { id: 11, name: '精品三', author: '作者K', cover: '/images/smlcover.png', href: '#' },
    { id: 12, name: '精品四', author: '作者L', cover: '/images/smlcover.png', href: '#' },
  ]

  const clickBooks: Book[] = [
    { id: 13, name: '点击一', author: '作者M', cover: '/images/smlcover.png', href: '#' },
    { id: 14, name: '点击二', author: '作者N', cover: '/images/smlcover.png', href: '#' },
    { id: 15, name: '点击三', author: '作者O', cover: '/images/smlcover.png', href: '#' },
  ]

  const newBooks: Book[] = [
    { id: 16, name: '新书一', author: '作者P', cover: '/images/smlcover.png', href: '#' },
    { id: 17, name: '新书二', author: '作者Q', cover: '/images/smlcover.png', href: '#' },
    { id: 18, name: '新书三', author: '作者R', cover: '/images/smlcover.png', href: '#' },
  ]

  const updateList: Array<{ id: number, name: string, author: string, time: string }> = [
    { id: 19, name: '更新小说一', author: '作者S', time: '06-24' },
    { id: 20, name: '更新小说二', author: '作者T', time: '06-24' },
    { id: 21, name: '更新小说三', author: '作者U', time: '06-24' },
  ]

  const updateRank: Book[] = [
    { id: 22, name: '榜单一', author: '作者V', cover: '/images/smlcover.png', href: '#' },
    { id: 23, name: '榜单二', author: '作者W', cover: '/images/smlcover.png', href: '#' },
    { id: 24, name: '榜单三', author: '作者X', cover: '/images/smlcover.png', href: '#' },
  ]
</script>
