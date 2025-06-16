<template>
	<view class="classLayout pageBg">
		<view class="classify">
			<theme-item v-for="(item, index) in listItem"
						:key="index"
						:image="item.image"
						:theme="item.theme"
						:update="item.update"></theme-item>
		</view>
	</view>
</template>

<script setup>
import {ref} from 'vue';
//触底操作
import {onReachBottom} from '@dcloudio/uni-app'
//初始化
const listItem = ref([]);

//变量数据
let container = [
	{
		image : "../../common/images/1.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/2.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/3.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/4.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/5.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/1.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/2.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/3.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/4.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/5.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/1.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/2.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/3.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/4.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
	{
		image : "../../common/images/5.jpg",
		theme : "动漫人物",
		update : "1天前"
	},
]

//赋值
listItem.value = container;

const newData = {
	image : "../../common/images/5.jpg",
	theme : "动漫人物",
	update : "1天前"
}

onReachBottom(()=>{
	//以下代码会使进程卡死，慎用
	// let i = 0;
	// for(i; i < container.length; i++){
	// 	newList.push(container[i]);
	// }
	// console.log(newList)
	
	//使用以下代码代替
	//涉及网络传输时可将newData封装成接收接口, i < data.length
	//本地暂时用本地数据代替
	for(let i = 0; i < 6; i++){
		listItem.value.push(newData);
	}
	
	// 或
	// listItem.value.push(newData, newData, newData)
})
</script>

<style>
.classify{
	padding: 30rpx;
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 15rpx;
}       
</style>
