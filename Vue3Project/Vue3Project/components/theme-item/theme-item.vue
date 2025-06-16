<template>
	<view class="theme-item">
		<navigator url="" class="box">
			<image class="pic" :src="image" mode="aspectFill"></image>
			<view class="mask">{{ theme }}</view>
			<view class="tab">{{ update }}</view>
		</navigator>
	</view>
</template>

<script setup>
defineProps({
	image : {
		type:String,
		default: '../../common/images/4.jpg',
	},
	theme : {
		type:String,
		default:'默认主题'
	},
	update:{
		type:String,
		default:'最近更新'
	}
})
</script>

<style lang="scss" scoped>
.theme-item{
	.box{
		height: 340rpx;
		border-radius: 10rpx;
		overflow: hidden;
		position: relative;
		.pic{
			width: 100%;
			height: 100%;
		}
		.mask{
			width: 100%;
			height: 70rpx;
			position: absolute;
			bottom:0;
			left: 0;
			background: rgba(0, 0, 0, 0.2);
			color: #fff;
			display: flex;
			align-items: center;
			justify-content: center;
			backdrop-filter: blur(10rpx);
			font-weight: 200;
		}
		.tab{
			position: absolute;
			top:0;
			left: 0;
			background: rgba(250, 129, 90, 0.7);
			backdrop-filter: blur(20rpx);
			color:white;
			font-size: 22rpx;
			padding-left: 2rpx;
			padding-right: 2rpx;
		}
	}
}
</style>