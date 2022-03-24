<template>
	
	<view class="hot-body" >
		<navbar :nav_btn="nav_btn"></navbar>
	<tabbar :selected="selected"></tabbar>
		 
			<view class="hot-item" v-for="item in list" @click="readActivity(item.content)">
			<view class="hot-item-img">
				封面
				
			</view>
			<view class="hot-item-content">
				{{item.content}}<br>
				内容。。。。。
				<view class="hot-item-content-img" style="width: 200rpx;height: 100rpx;background-color: #38D1FF;margin-left: 250rpx;">
					图片
				</view>
			</view>
			
		</view>
		
		<view :animation="animationData" @touchstart.stop="touchStart" @touchend.stop="touchEnd" class="hisNewActiviy" style="width: 90%;height: 0; position: fixed; bottom: 0; left: 50%;transform: translateX(-50%);background-color: #217f99;border-radius: 30rpx;">
			<view class="hot-title" style="margin-left: 50rpx;">
				
				<text style="font-weight: 1000;
			font-size: 50rpx;">#此处{{content}}标题。。。#</text><br>
				<text>#此处概要。。。。#</text>
			</view>
			
				<view  class="hisImg" style="width: 120rpx;height: 120rpx;border-radius: 50%;border: 1px #555555 solid;margin: 20rpx 0 0 20rpx;">
				<image src="../../static/bussiness-man.png" style=" width: 100%;height: 100%;" mode=""></image>	
			</view>
			
			
			<view class="hotcontent" style="margin-left: 60rpx;">
				<text>##此处详细内容.....##</text><br>
				<text>##此处详细内容.....##</text>
			</view>
			
		</view>
		
		<tabbar></tabbar>
		
	</view>
</template>

<script>
	import tabbar from '../../custom-tab-bar'
	import navbar from '../../components/nav-bar.vue'
	
	
	
		
	export default {
		components:{
			tabbar,navbar
		},
		data() {
			return {
				nav_btn: "hotlist",
				selected: 0,
				content:'',
				startY:0,
				animationData: {},
				list:[
					{
						id:'001',
					content:'热榜第一条'
					
					},
					{
						id:'002',
					content:'热榜第二条'
					
					},
					{
						id:'003',
					content:'热榜第三条'
					
					},
					{
						id:'004',
					content:'热榜第四条'
					
					},
					{
						id:'005',
					content:'热榜第五条'
					
					},
					{
						id:'006',
					content:'热榜第六条'
					
					},
					{
						id:'007',
					content:'热榜第七条'
					
					}
					
				],
				
			}
		},
		methods: {
			onUnload() {
				this.animationData = {};
				// 页面关闭后清空数据
			},
			onload() {
				this.animation = uni.createAnimation();
				// 创建动画实例
			},
			readActivity(val){
				this.content = val
				var animation = uni.createAnimation({
				 
				  duration: 700,
				  timingFunction: "ease",
				 
				})
				
					
					animation.height(600).step()
					
				
				
				
				
				
				this.animationData = animation.export()
				
				
			},
			
			touchStart(e){
									if (e.touches.length == 1) {
										//设置触摸起始点水平方向位置
										this.startY=e.touches[0].clientY;
									}
								},
								
								
								touchEnd(e){
									if (e.changedTouches.length == 1) {
										//手指移动结束后水平位置
										var endY = e.changedTouches[0].clientY;
										let diff = endY-this.startY;
										if(Math.abs(diff)>100){
											if(diff>0){
												console.log("下滑...");
												var animation = uni.createAnimation({
												 
												  duration: 700,
												  timingFunction: "ease",
												 
												})
												animation.height(0).step()
												this.flag = !this.flag
												this.animationData = animation.export()
												
												if(this.show){
													this.show = false
												}
												
											}else{
												
												console.log("上滑...");
											}
										}
									}
								
								},
			
		}
	}
</script>

<style>
	.hot-item{
		width: 95%;
		height: 250rpx;
		background-color: #f4f4f4;
		border-radius: 20rpx;
		display: flex;
		margin:10rpx auto ;
	}
	.hot-body{
		width: 100%;
		height: 100%;
		background-color: #e2e2e2;
		display: flex;
		justify-content: center;
		flex-direction: column;
		
	}
	.hot-item-img{
		width: 20%;
		height: 80%;
		background-color: #e2e2e2;
		margin: 20rpx 0 0 40rpx  ;
		border-radius: 40rpx;
	}
	.hot-item-content{
		width: 65%;
		height: 80%;
		background-color: #e2e2e2;
		margin: 25rpx 0 0 30rpx;
	}
	

</style>
