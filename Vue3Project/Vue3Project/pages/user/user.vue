<template>
	<view class="userLayout pageBg">
		<view class="userInfo">
			<view class="avatar">
				<image src="../../common/images/2.jpg" mode="aspectFill"></image>
			</view>
			<view class="userName">
				用户
			</view>
			<view class="address"></view>
		</view>
		<view class="section">
			<view class="list">
				<view class="list">
					<view class="row">
						<view class="left">
							<uni-icons type="download-filled" size="16" color="#28b389"></uni-icons>
							<view class="text">
								我的缓存
							</view>
						</view>
						<view class="right">
							<view class="text">
								
							</view>
							<uni-icons type="right" size="16" color="#28b389"></uni-icons>
						</view>
					</view>
					<view class="row">
						<view class="left">
							<uni-icons type="star-filled" size="16" color="#28b389"></uni-icons>
							<view class="text">
								我的收藏
							</view>
						</view>
						<view class="right">
							<view class="text">
								
							</view>
							<uni-icons type="right" size="16" color="#28b389"></uni-icons>
						</view>
					</view>
					<view class="row">
						<view class="left">
							<uni-icons type="phone-filled" size="16" color="#28b389"></uni-icons>
							<view class="text">
								联系客服
							</view>
						</view>
						<view class="right">
							<view class="text">
								
							</view>
							<uni-icons type="right" size="16" color="#28b389"></uni-icons>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="section">
			<view class="list">
				<view class="row">
					<view class="left">
						<uni-icons type="loop" size="16" color="#28b389"></uni-icons>
						<view class="text">
							版本更新
						</view>
					</view>
					<view class="right">
						<view class="text">
							
						</view>
						<uni-icons type="right" size="16" color="#28b389"></uni-icons>
					</view>
				</view>
				<view class="row">
					<view class="left">
						<uni-icons type="flag-filled" size="16" color="#28b389"></uni-icons>
						<view class="text">
							常见问题
						</view>
					</view>
					<view class="right">
						<view class="text">
							
						</view>
						<uni-icons type="right" size="16" color="#28b389"></uni-icons>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>

</script>

<style lang="scss">
.userLayout{
	display: flex;
	align-items: center;
	justify-content: center;
	flex-direction: column;
	text-align: center;
	padding: 50rpx 0;
	.avatar{
		width: 150rpx;
		height: 150rpx;
		border-radius: 50%;
		overflow: hidden;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-left: 00rpx;
		image{
			width: 100%;
			height: 100%;
		}
	}
	.userName{
		margin-top: 20rpx;
		color:#333;
	}
	.address{
		color:#aaa;
	}
	
	.section{
		width: 690rpx;
		margin: 50rpx 30rpx;
		border: 1px solid #eee;
		border-radius: 10rpx;
		box-shadow: 0 0 30rpx rgba(0,0,0,0.05);
		.list{
			background: white;
			.row{
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding: 0 30rpx;
				height: 100rpx;
				border: 1rpx solid #eee;
				&:last-child{border-bottom: 0;}
				.left{
					display: flex;
					align-items: center;
					justify-content: center;
					.text{
						padding-left: 20rpx;
						color:#666
					}
				}
				.right{
					display: flex;
					align-items: center;
					justify-content: center;
					.text{
						padding-right: 20rpx;
						color: #666;
					}
				}
			}
		}
	}
}
</style>
