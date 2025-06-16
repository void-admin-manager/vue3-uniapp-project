<template>
	<view>
		<information-item 
			v-for="(item, index) in newsList" 
			:key="index"
			:title="item.title"
			:content="item.content"
			:author="item.author"
			:date="item.date"
			:image="item.image"
			@click="openPage">
		</information-item>
	</view>
</template>

<script setup>
import { ref } from 'vue'

const newsList = ref([])

//对应的是原生的promise对象
uni.request({
	//此处请使用自己构建的后端server，如果没有的话promise会返回一个错误对象
	url: "http://localhost:8080/news",
	method:"GET",
	timeout:5000,
	success: async (res) => {
		if (res.statusCode === 200) {		
			try {
				// 确认res并确认格式正确
				if (res.data && Array.isArray(res.data.title)) {
					// 使用map检测每一个元素并写入newsList
					newsList.value = res.data.title.map((title, index) => ({
						title: title,
						content: res.data.content[index],
						author: res.data.author[index],
						date: res.data.date[index],
						image: res.data.image[index]
					}))
				} else {
					console.error('返回数据格式不正确:', res.data)
				}
			} catch (error) {
				console.error('数据解析失败:', error)
			}
		} else {
			console.error('请求失败，状态码:', res.statusCode)
		}
	},
	fail: (err) => {
		console.error('请求失败:', err)
	}
})

setTimeout(()=>{
	uni.request({
		url: "http://localhost:8080/news1",
		method:"GET",
		timeout:5000,
		success: async (res) => {
			if (res.statusCode === 200) {
				console.log(newsList.value)
				try {
					// 确认res并确认格式正确
					if (res.data && Array.isArray(res.data.title)) {
						// 使用map检测每一个元素并写入newsList
						const newdata = res.data.title.map((title, index) => ({
							title: title,
							content: res.data.content[index],
							author: res.data.author[index],
							date: res.data.date[index],
							image: res.data.image[index]
						}))
						newsList.value = newsList.value.concat(newdata);
						//newsList.value.push(...newData);
					} else {
						console.error('返回数据格式不正确:', res.data)
					}
				} catch (error) {
					console.error('数据解析失败:', error)
				}
			} else {
				console.error('请求失败，状态码:', res.statusCode)
			}
		},
		fail: (err) => {
			console.error('请求失败:', err)
		}
	})
}, 2000);

const openPage = ()=> {
	
}
</script>