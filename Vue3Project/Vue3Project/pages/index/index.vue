<template>
	<view class="home pageBg">
		<pageHeaders ref="really"></pageHeaders>
		<view class="banner">
			<swiper indicator-dots="true" autoplay indicator-color="#c8c7cc"
				indicator-active-color="#fff" circular>
				<swiper-component v-for="(item, index) in imageSrc"
								  :key="index"
								  :image="item.image"></swiper-component>
			</swiper>
		</view>
		<view class="notice">
			<view class="left">
				<uni-icons type="sound-filled" size="20" color="#28b399"></uni-icons>
				<text class="text">公告</text>
			</view>
			<view class="center">
				<swiper vertical autoplay interval="1500" duration="300" circular>
					<swiper-item v-for="item in 4">文字内容</swiper-item>
				</swiper>
			</view>
			<view class="right">
				<uni-icons type="right" size="16" color="#28b399"></uni-icons>
			</view>
		</view>
		<view class="select">
			<common-title>
			<template #name>本地滑动</template>
			<template #custom>
				<view class="date">
					<uni-icons type="calendar" size="18" color="#28b399"></uni-icons>
				</view>
			</template>
			</common-title>

			<view class="content">
				<scroll-view scroll-x direction="horizontal">
					<view class="box" v-for="item in 8">
						<image src="../../common/images/1.jpg" mode="aspectFill"></image>
					</view>
				</scroll-view>
			</view>
			
			<view class="theme">
				<common-title>
					<template #name>本地列窗</template>
					<template #custom>
						<navigator url="../searchPage/searchPage" class="more">More+</navigator>
					</template>
				</common-title>
			</view>
		</view>
		<localList v-for="(item, index) in refs"
				   :key="index"
				   :title="item.title"
				   :content="item.content"
				   :author="item.author"
				   :date="item.date"
				   :image="item.image"
				   @click="navTo"></localList>
	</view>
</template>

<script setup>
import {ref, onMounted, defineProps} from 'vue';

const really = ref('');
//赋值对象传递到子组件
const refs = ref([]);

//此处使用本地数据
//要真实模拟请构建自己的后端api
const values = [
	{
		title : "今日财经",
		content : "内容1",
		author : "赵大",
		date : "2024-01-01",
		image : "../../common/images/1.jpg"
	},
	{
		title : "今日新闻",
		content : "内容2",
		author : "钱二",
		date : "2024-01-01",
		image : "../../common/images/2.jpg"
	},
	{
		title : "今日体育",
		content : "内容3",
		author : "张三",
		date : "2024-01-01",
		image : "../../common/images/3.jpg"
	},
	{
		title : "今日科技",
		content : "内容4",
		author : "李四",
		date : "2024-01-01",
		image : "../../common/images/4.jpg"
	},
	{
		title : "今日资讯",
		content : "内容5",
		author : "王五",
		date : "2024-01-01",
		image : "../../common/images/5.jpg"
	},
];
refs.value = values;

const navTo = ()=>{
	uni.navigateTo({
		//需要独立页面，不能选中TabBar中存在的页面
		//url空白的时候页面会报错因为没有Promise
		//可以使用reLaunch，但是尽量不要使用，因为会销毁所有页面栈
		url:""
	})
}

const imageSrc = ref([])

//此处使用本地数据
//要真实模拟请构建自己的后端api
let imageCount = [
	{
		image : "../../common/images/1.jpg"
	},
	{
		image : "../../common/images/2.jpg"
	},
	{
		image : "../../common/images/3.jpg"
	},
	{
		image : "../../common/images/4.jpg"
	},
]

imageSrc.value = imageCount;
console.log(imageSrc.value)
console.log(refs.value)

onMounted(()=>{
	console.log(really.value);
})
</script>

<style lang="scss" scoped>
.home{
	.banner{
		width: 750rpx;
		padding: 30rpx 0;
		swiper{
			width: 750rpx;
			height: 340rpx;
			swiper-item{
				width: 100%;
				height: 100%;
				padding: 0 30rpx;
				image{
					width: 100%;
					height: 100%;
					border-radius: 30rpx;
				}
			}
		}
	}
	.notice{
		width: 690rpx;
		height: 80rpx;
		line-height: 80rpx;
		background: #f9f9f9;
		margin: 0 auto;
		border-radius: 80rpx;
		display: flex;
		.left{
			width: 140rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			.text{
				color:#28b389;
				font-weight: 600;
				font-size: 30rpx;
			}
		}
		.center{
			flex : 1;
			swiper{
				height: 100%;
				swiper-item{
					height: 100%;
					font-size: 30rpx;
					color:#666;
					overflow: hidden;
					white-space: nowrap; //不换行
					text-overflow: ellipsis; //不超行
				}
			}
		}
		.right{
			width: 70rpx;
			display: flex;
			align-items: center;
			justify-content: center;
		}
	}
	
	.select{
		padding-top: 50rpx;
		margin-left: 30rpx;
		margin-top: 30rpx;
		.content{
			width: 720rpx;
			scroll-view{
				white-space: nowrap;
				.box{
					width: 200rpx;
					height: 430rpx;
					display: inline-block;
					margin-right: 15rpx;
					image{
						width: 100%;
						height: 100%;
						margin-right: 15rpx;
						padding-right: 15rpx;
						border-radius: 10rpx;
					}
				}
				.box:last-child{margin-right: 30rpx;}
			}
		}
	}
	
	.theme{
		padding-top: 50rpx;
		margin-right: 15rpx;
		.more{
			font-size: 32rpx;
			color:#ccc;
		}
		
		.content{
			margin-top: 30rpx;
			padding: 0 30rpx;
			display: grid;
			gap:15rpx;
			grid-template-columns: repeat(2, 1fr);
		}
	}
}
</style>
