<template>
  <view class="detail">
    <view>
      <button id="show-modal">Show Modal</button>
    </view>
  </view>
  <view class="detailArea">
    <view class="detailItem">
      <p class="detailTitle">{{ detailDate.title }}</p>
      <img :src="detailDate.image" class="detailImage" />
      <p  class="detail-contain">{{ detailDate.contain }}</p>
      <p @click="goback()" class="back">back</p>
    </view>
  </view>
</template>

<script setup>
import './detail.scss'
import { ref } from 'vue'
import { getCurrentInstance } from '@tarojs/taro';
import Taro from '@tarojs/taro'
console.log('setup run.');

const {router}  = getCurrentInstance()

const details = ref([
  {
    id: 1,
    title: '我们要面对的苦难和挫折不会因为我们遭遇够多而减少',
    image: require('../../static/images/image1.jpg'),
    contain: '我们要面对的苦难和挫折不会因为我们遭遇够多而减少，上天不会因为你的悲惨而悯怜你，它只会安排一道又一道难关来磨炼你的意志。'
  },
  {
    id: 2,
    title: '你可以靠透支身体',
    image: require('../../static/images/image2.jpg'),
    contain: '在某个年纪之前，你可以靠透支身体，小聪明和老天给你的运气一直取巧地活着。然而到了某个年纪之后，真正能让你走远的，都是自律，积极和勤奋'
  },
  {
    id: 3,
    title: '我们最终都要远行',
    image: require('../../static/images/image3.jpg'),
    contain: '我们最终都要远行，最终都要跟稚嫩的自己告别。也许路途有点艰辛，有点孤独，但熬过了痛苦，我们才能得以成长。'
  },
  {
    id: 4,
    title: '这就是所谓的人生',
    image: require('../../static/images/image4.jpg'),
    contain: '所有回不去的良辰美景，都是举世无双的好时光。感谢过去，珍惜现在，憧憬未来。哭给自己听，笑给别人看，这就是所谓的人生。'
  },
  {
    id: 5,
    title: '去做最好的自己',
    image: require('../../static/images/image5.jpg'),
    contain: '别人再好，也是别人。自己再不堪，也是自己，独一无二的自己。只要努力去做最好的自己，一生足矣。为自己的人生负责，为自己的梦想买单。'
  },
])

const detailDate = ref(details.value[router.params.index]) 

const showModal = ref(false)
function tapOpenModal() {
  showModal.value = true
}

function goback() {
  Taro.navigateBack()
}


</script>
