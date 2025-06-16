<template>
	<view class="morePage">
		<morePage-item  v-for="(item, index) in items"
						:key="index"
						:text="item"
						></morePage-item>
	</view>
</template>

<script setup>
import { nextTick, onMounted } from 'vue';
import { ref } from 'vue';

const items = ref(["文档", "API接口", "数据查询", '数据字典', '帮助']);
	
const setItem = (item) =>{
	
}

onMounted(()=>{
	
})

</script>

<style lang="scss" scoped>
.morePage{
	width: 100vw;
	height: 85vh;
	background: #eee;
}
</style>