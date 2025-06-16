<template>
  <view class="search-container">
    <view class="search-box">
      <uni-icons class="search-icon" type="search" size="20" color="#aaaaaa"></uni-icons>
      <input 
        class="search-input" 
        type="text" 
        placeholder="请输入搜索内容"
        placeholder-class="placeholder-style"
        v-model="searchText"
        @confirm="addHistory"
      />
    </view>
    <view class="history">
      搜索历史:
      <view v-for="(item, index) in hisList" :key="index">{{ item }}</view>
    </view>
  </view>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const searchText = ref(''); 
const hisList = ref([]); 

onMounted(() => {
  const history = uni.getStorageSync('searchHistory');
  if (history) {
    hisList.value = history; 
  }
  console.log(history);
});

//本地存储，如果想要持久化或者从服务器获取记录请重写这一段
const addHistory = () => {
	uni.request({
		url:"",
	});
  if (searchText.value.trim()) { 
    const history = uni.getStorageSync('searchHistory') || []; 
    if (!history.includes(searchText.value)) { 
      history.unshift(searchText.value); 
      if (history.length > 10) { 
        history.pop(); 
      }
      uni.setStorageSync('searchHistory', history); 
      hisList.value = history; 
    }
    searchText.value = ''; 
  }
};
</script>

<style lang="scss" scoped>
.search-container {
  padding: 25rpx;
  background-color: #f8f8f8; 
}

.search-box {
  display: flex;
  align-items: center;
  background-color: #ffffff;
  border-radius: 18rpx;
  padding: 18rpx 22rpx;
  box-shadow: 0 2rpx 4rpx rgba(0,0,0,0.1);
}

.search-icon {
  margin-right: 18rpx;
}

.search-input {
  flex: 1;
  height: 42rpx;
  font-size: 24rpx;
  color: #333;
  border: none;
  outline: none;
  background-color: transparent;
}

.placeholder-style {
  color: #aaaaaa;
  font-size: 24rpx;
}

.history {
  margin-top: 16rpx;
  font-size: 26rpx;
  color: #aaa;
}
</style>