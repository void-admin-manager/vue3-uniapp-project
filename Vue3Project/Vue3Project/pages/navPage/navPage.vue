<template>
  <view class="container">
    <view class="nav-bar">
      <view 
        v-for="(item, index) in navItems" 
        :key="index"
        class="nav-item"
        :class="{ active: activeIndex === index }"
        @click="switchPage(index)"
      >
	  {{ item.title }}
      </view>
    </view>
 
    <view class="content-container">
        <component :is="activeComponent" />
    </view>

    <view class="uni-tabbar-placeholder" />
  </view>
</template>

<script setup>
import { ref, shallowRef, defineAsyncComponent } from 'vue';

// 异步加载组件
const PageA = defineAsyncComponent(() => import('../classify/classify.vue'));
const PageB = defineAsyncComponent(() => import('../information/information.vue'));
const PageC = defineAsyncComponent(() => import('../classList/classList.vue'));

const navItems = [
  { title: '壁纸', component: PageA },
  { title: '资讯', component: PageB },
  { title: '更多', component: PageC }
];

const activeIndex = ref(0);
//默认准备
const activeComponent = shallowRef(navItems[0].component);

function switchPage(index) {
  activeIndex.value = index;
  activeComponent.value = navItems[index].component;
}
</script>

<style scoped>
.container {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.nav-bar {
  height: 44px;
  display: flex;
  background: #fff;
  border-bottom: 1px solid #eee;
}

.nav-item {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  color: #666;
}

.nav-item.active {
  color: #007AFF;
  font-weight: bold;
  position: relative;
}

.nav-item.active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 2px;
  background: #007AFF;
}

.content-container {
  flex: 1;
  overflow: hidden;
}

.uni-tabbar-placeholder {
  height: 50px;
}
</style>