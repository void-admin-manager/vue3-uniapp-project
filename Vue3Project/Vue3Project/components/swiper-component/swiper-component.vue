<template>
	<swiper-item>
		<image :src="image" mode="aspectFill"></image>
	</swiper-item>
</template>

<script setup>
defineProps({
	image:{
		type:String,
		default:"../../common/images/1.jpg"
	}
})
</script>

<style lang="scss">
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
</style>