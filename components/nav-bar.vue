<template>
	<view>
		<uni-nav-bar shadow="true" :fixed="true" :statusBar="true" leftWidth="1200rpx" backgroundColor="#555555">
			<view class="left" slot="left">
				<!-- 热榜 -->
				<button size="mini" :class="[nav_btn==='hotlist'?'btn-active':'btn-default']" @click="navTo('hotlist')">热榜</button>
				<!-- 直播 -->
				<button size="mini" :class="[nav_btn==='live'?'btn-active':'btn-default']" @click="navTo('live')">直播</button>
				<!-- 公益招聘 -->
				<button size="mini" :class="[nav_btn==='recruit'?'btn-active':'btn-default']" style="width: 125rpx;" @click="navTo('recruit')">公益招聘</button>
				<!-- 消息提醒UI -->
				<uni-badge :offset="[3,3]" absolute="rightTop" :text="num" type="error" size="small">
					<uni-icons type="notification-filled" size="25" :color="[nav_btn==='notification'?'#0ca0d9':'#898989']" style="margin-left: -4rpx;" @click="navTo('notification')"></uni-icons>
				</uni-badge>
				<!-- 搜索框 -->
				<view class="search" @click="navTo('search')">
					<view class="wrap"></view>
					<view class="wrap">搜索框</view>
					<view class="wrap" style="text-align: right;">
						<uni-icons type="search" size="20" color="#c1c1c1"></uni-icons>
					</view>
				</view>
			</view>
		</uni-nav-bar>
	</view>
</template>

<script>
	export default {
		props:{
			nav_btn: {
				type:String,
				default:""
			}
		},
		name: "nav-bar",
		data() {
			return {
				// customStyle:{
				// 	width: "32rpx",
				// 	height: "32rpx",
				// 	alignItems:"center",
				// 	position: "fixed",
				// 	left: "47%",
				// 	top: "4%"
				// },
				num: 1
			};
		},
		onLoad() {
			
		},
		methods:{
			navTo:function(name){
				uni.redirectTo({
					url: '/nav/' + name + '/' + name,
					success(res) {
						console.log(res)
					},
					fail(err) {
						console.log(err)
					}
				});
			}
		}
	}
</script>

<style>
	.left {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.btn-default {
		height: 60rpx;
		width: 80rpx;
		line-height: 60rpx!important;
		border: 1rpx solid #000000;
		font-size: 17rpx !important;
		margin-right: 10rpx;
		border-radius: 14rpx;
	}
	.btn-active {
		height: 60rpx;
		width: 80rpx;
		line-height: 60rpx!important;
		border: 1rpx solid #000000;
		font-size: 17rpx !important;
		margin-right: 10rpx;
		border-radius: 14rpx;
		background-color: #0ca0d9;
		color: #FFFFFF;
		font-weight: bold;
	}
	
	.search{
		font-size: 17rpx !important;
		width: 150rpx;
		height: 50rpx;
		line-height: 50rpx;
		border-radius: 15rpx;
		background-color: #FFFFFF;
		display: flex;
		align-items: center;
		margin-left: 20rpx;
		/* justify-content: space-between; */
	}
	.wrap{
		height: 50rpx;
		line-height: 50rpx;
		flex:1;
	}
	
</style>
