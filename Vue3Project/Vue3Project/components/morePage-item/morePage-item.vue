<template>
	<view class="row">
		<uni-icons class="left" type="star-filled" size="20" color="#28b389"></uni-icons>
		<text class="text">{{ text }}</text>
		<uni-icons class="right" type="right" size="20" color="#28b389"></uni-icons>
	</view>
</template>

<script setup>
import {ref, defineExpose, defineProps} from'vue' 
defineProps({
	text:{
		type:String,
		required: true, 
	}
})
</script>

<style lang="scss" scoped>
.row{
	display: flex;
	align-items: center;
	justify-items: center;
	padding-top: 40rpx;
	padding-bottom: 40rpx;
	background: #fff;
	margin-bottom: 10rpx;
	.left{
		margin-right: 20rpx;
		margin-left: 20rpx;
	}
	.text{
		font-weight: 300;
	}
	.right{
		margin-left: auto;
		margin-right: 20rpx;
	}
}
</style>