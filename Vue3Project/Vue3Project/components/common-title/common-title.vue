<template>
	<view class="common-title">
		<view class="name">
			<slot name="name"></slot>
		</view>
		<view class="custom">
			<slot name="custom"></slot>
		</view>
	</view>
</template>

<script setup>
	import {ref, defineExpose} from'vue' 
	const count = ref(6);
	defineExpose({
		count,
	})
</script>

<style lang="scss">
.common-title{
	display: flex;
	justify-content: space-between;
	align-items: center;
	box-sizing: border-box;
	margin-right: 20rpx;
	margin-bottom: 20rpx;
	.name{
		font-size: 40rpx;
	}
}
</style>