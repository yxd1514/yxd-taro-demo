<template>
  <view class="index">
    <view>
      <button id="show-modal" @tap="tapOpenModal">Show Modal</button>
      <teleport to="#teleportId" v-if="showModal">
        <modal :show="showModal" @close="showModal = false">
          <template #header>
            <view>custom header</view>
          </template>
        </modal>
      </teleport>
    </view>
  </view>
  <view id="teleportId" class="teleportId"></view>
  <view class="listArea">
    <view v-for="(feed, index) in feeds" :key="feed.id" class="feedItem">
      <view>
        <p class="feedTitle" @click="jump(index)">{{ feed.title }}</p>
      </view>
      <img :src="feed.image" class="feedImage" />
    </view>
  </view>
</template>

<script setup>
import './index.scss'
import Modal from './Modal.vue'
import { ref } from 'vue'
import Taro from '@tarojs/taro'
console.log('setup run.');

const showModal = ref(false)
const feeds = ref([
  {
    id: 1,
    title: '我们要面对的苦难和挫折不会因为我们遭遇够多而减少',
    image: require('../../static/images/image1.jpg'),
  },
  {
    id: 2,
    title: '你可以靠透支身体',
    image: require('../../static/images/image2.jpg'),
  },
  {
    id: 3,
    title: '我们最终都要远行',
    image: require('../../static/images/image3.jpg'),
  },
  {
    id: 4,
    title: '这就是所谓的人生',
    image: require('../../static/images/image4.jpg'),
  },
  {
    id: 5,
    title: '去做最好的自己',
    image: require('../../static/images/image5.jpg'),
  },
])
function tapOpenModal() {
  showModal.value = true
}

function jump(index) {
  // 跳转到目的页面，打开新页面
  Taro.navigateTo({
    url: '/pages/detail/detail?index='+ index,
  })
}


</script>
