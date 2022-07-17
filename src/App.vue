<template lang="pug">
v-app(style="width: 100%; height: 100%; background-image: url('https://www.pcclean.io/wp-content/uploads/2021/11/1064255544315822962.jpg'); background-position: center; background-size: 100% 100%; background-repeat: no-repeat;")
  v-app-bar(color="#31D4D0")
    v-app-bar-title(style="color: #3A46D6;font-size: 1.7rem; font-weight: bolder;") 哥吉拉番茄鐘
    v-spacer
    v-btn(icon to='/')
      v-icon(style="color: black;") mdi-timer
    v-btn(icon to='/list')
      v-icon(style="color: black;") mdi-format-list-bulleted
    v-btn(icon to='/settings')
      v-icon(style="color: black;") mdi-cog
    v-btn(icon v-if="notify" @click="toggleNotify")
      v-icon(style="color: black;") mdi-bell
    v-btn(icon v-else @click="toggleNotify")
      v-icon(style="color: gray;") mdi-bell-off
  v-main
    v-container
      router-view(v-slot="{ Component }")
        keep-alive(include="HomeView")
          component(:is="Component")
</template>

<script setup>
import { storeToRefs } from 'pinia'
import { useListStore } from '@/stores/list'
const list = useListStore()
const { notify } = storeToRefs(list)
const { toggleNotify } = list
</script>
