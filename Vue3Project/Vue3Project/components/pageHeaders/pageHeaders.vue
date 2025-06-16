<template>
	<view class="headres">
		<view class="head-content">
			<view class="head-text" @click="toExercises">
				首页
			</view>
			<view class="search-box">
				<uni-icons class="search-icon" type="search" size="20" color="#aaaaaa"></uni-icons>
				<input
				  class="search-input" 
				  type="text" 
				  placeholder="请输入搜索内容"
				  placeholder-class="placeholder-style"
				  @click="toSearch"
				/>
			</view>
			<uni-icons class="person-filled" 
					   type="person-filled" 
					   size="20" 
					   color="#aaaaaa"></uni-icons>
		</view>
	</view>
</template>

<script setup>
	import {ref} from "vue";
	
	const toSearch = ()=> {
		uni.navigateTo({
			url:"/pages/searchPage/searchPage",
		})
	}
	
	const toExercises = () => {
		uni.navigateTo({
			url:"../../pages/ExercisesPage/ExercisesPage",
		})
	}
</script>

<style lang="scss">
	.headres{
		padding-top: 20rpx;
		padding-left: 30rpx;
		color:#111;
		font-weight: 200;
		.head-text{
			margin-right: 30rpx;
		}
		.head-content{
			display: flex;
		}
		.search-box{
			display: flex;
			background: white;
			margin-left: 20rpx;
			border-radius: 20rpx;
			.search-icon{
				padding-left: 5rpx;
				padding-right: 5rpx;
			}
			.search-input{
				width: 450rpx;
			}
		}
		.person-filled{
			display: flex;
			margin-left: auto;
			margin-right: 30rpx;
		}
	}
</style>