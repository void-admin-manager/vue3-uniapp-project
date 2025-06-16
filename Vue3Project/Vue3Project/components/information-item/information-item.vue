<template>
	<view class="information-item">
		<view class="left">
			<view class="left-top">
				<text class="title">{{ title }}</text>
				<text class="summary">{{ content }}</text>
			</view>
			<view class="left-bottom">
				<text class="author">作者：{{ author }}</text>
				<text class="time">发布时间：{{ date }}</text>
			</view>
		</view>
		<view class="right-image">
			<image :src="image" mode="aspectFill"></image>
		</view>
	</view>
</template>

<script setup>
// 接收父组件传递的数据
defineProps({
	title: {
		type: String,
		required: true, 
	},
	content: {
		type: String,
		default: '', 
	},
	author: {
		type: String,
		default: '未知作者',
	},
	date: {
		type: String,
		default: '未知日期',
	},
	image:{
		type: String,
		default:'',
	}
});
</script>

<style lang="scss">
.information-item {
	display: flex;
	justify-content: space-between;
	align-items: flex-start; 
	padding: 20rpx;
	border-bottom: 1rpx solid #eee;
	background-color: #fff;
	box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.1);
	border-radius: 10rpx;
	margin-bottom: 20rpx;

	.left {
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		margin-right: 20rpx;

		.left-top {
			width: 470rpx;
			.title {
				font-size: 32rpx;
				font-weight: bold;
				color: #333;
				display: -webkit-box; 
				white-space: nowrap;
				-webkit-box-orient: vertical;
				overflow: hidden;
				text-overflow: ellipsis;
				margin-bottom: 10rpx;
			}

			.summary {
				font-size: 28rpx;
				color: #666;
				line-height: 1.5;
				display: -webkit-box; 
				-webkit-line-clamp: 2; 
				-webkit-box-orient: vertical;
				overflow: hidden;
				text-overflow: ellipsis;
				margin-top: 10rpx; 
			}
		}

		.left-bottom {
			display: flex;
			align-items: center;
			margin-top: 10rpx;

			.author, .time {
				font-size: 24rpx;
				color: #999;
				margin-right: 20rpx;
			}
		}
	}

	.right-image {
		width: 200rpx;
		height: 150rpx;
		border-radius: 10rpx;
		overflow: hidden;
		flex-shrink: 0; // 防止图片被压缩

		image {
			width: 100%;
			height: 100%;
		}
	}
}
</style>