<template>
	<view>
		<view class="me-header" style="width: 100%;height:100rpx;background-color: #8F8F94;">
			<navbar></navbar>
		</view>
		
		<view class="me-header" style="width: 100%;height:350rpx;background-color: pink;">
			
		</view>
	<view class="school-message-classify" style="width: 100%;height:100rpx;background-color: #e9e9ef;position: relative;">
		<view  style="width: 15%;height: 60rpx;border-radius: 10rpx; background-color: #b1b1b1;position: absolute;left: 1%;top: 50%;transform: translateY(-50%);">
			 最新
		</view>
		<view  style="width: 15%;height: 60rpx;border-radius: 10rpx; background-color: #b1b1b1;position: absolute;left: 17%;top: 50%;transform: translateY(-50%);">
			 最热
		</view>
		<view  style="width: 15%;height: 60rpx;border-radius: 10rpx; background-color: #b1b1b1;position: absolute;left: 34%;top: 50%;transform: translateY(-50%);">
			 最赞
		</view>
		<view @click="activityShowChange()" style="width: 80rpx;height: 80rpx;border-radius: 50%; background-color: #b1b1b1;position: absolute;right: 15rpx; top: 50%;transform: translateY(-50%);">
			 <image src="../../../static/bussiness-man.png" style=" width: 100%;height: 100%;" mode=""></image>
		</view>
	</view>
	<view class="school-newmessage" style="width: 100%;height:80rpx;background-color: pink;position: relative;"> 新消息
	  <view @click="showhismessage()" class="goNewMessage" style="width: 40%;height: 70%;border-radius: 10rpx; background-color: #b1b1b1;position: absolute;left: 50%;top: 50%;transform: translate(-50%,-50%);">
	  	 xx发布了新动态
	  </view>
	
	</view>
	
	<view class="newActivities" style="width: 100%;height: 100%;background-color: #e9e9ef;position: relative;">
		<view class="v-option" v-for="item in list" style="margin: 20rpx auto;height: 270rpx; border:2px solid #C0C0C0;" >
			
				{{item.title}}
						
		</view>
		
		
		
		<view v-show="show" class="hisMessage"style="width: 80%;height: 350rpx;position: absolute;top: 10rpx;left: 50%;transform: translateX(-50%);background-color: #159c0b;">
			<scroll-view scroll-y="true" style="height: 100%;width: 100vw;"
				      >
					<view class="v-option" v-for="item in friendslist" style="margin: 20rpx auto;height: 270rpx; border:2px solid #C0C0C0;" @click="readActivity(item.name)">
						
							
							<view  class="hisImg" style="width: 100rpx;height: 100rpx;border-radius: 50%;border: 1px #555555 solid;margin: 20rpx 0 0 20rpx;" >
								<image src="../../../static/head.png" style=" width: 100%;height: 100%;" mode=""></image>
								 {{item.name}}的动态
							</view>
							
						
						
						
					</view>
					
				</scroll-view>
			
			
		</view>
		<view v-show="activityShow" class="hisMessage"style="width: 80%;height: 350rpx;position: absolute;top: 10rpx;left: 50%;transform: translateX(-50%);background-color: #159c0b;">
			<view  class="hisImg" style="width: 100rpx;height: 100rpx;border-radius: 50%;border: 1px #555555 solid;margin: 20rpx 0 0 20rpx;">
				<image src="../../../static/bussiness-man.png" style=" width: 100%;height: 100%;" mode=""></image>
				 
			</view>
			xxx参加的新活动<br>
			......<br>
			......
			<view class="attendActivity" @click="goattend" style="width: 200rpx;height: 50rpx;border-radius: 50rpx;background-color: #7d8a05;position: absolute;top: 40rpx;left: 30%;">
				点击加入
			</view>
		</view>
	</view>
	
	<view :animation="animationData" @touchstart="touchStart" @touchend="touchEnd" class="hisNewActiviy" style="width: 80%;height: 0; position: fixed; bottom: 0; left: 50%;transform: translateX(-50%);background-color: #217f99;">
		
		<view class="big" style="width: 70rpx;height: 70rpx;float: left; ">
			<image @click.stop="gobig" src="../../../static/big.png" style="float: left;"  mode=""></image>
			
		</view>
		<view  class="back" style="width: 70rpx;height: 70rpx;float: right; ">
			
			<image @click.stop="back()" src="../../../static/back1.png" @click="" mode=""></image>
		</view>
		<view  class="hisImg" style="width: 100rpx;height: 100rpx;border-radius: 50%;border: 1px #555555 solid;margin: 90rpx 0 0 20rpx;">
			<image src="../../../static/bussiness-man.png" style=" width: 100%;height: 100%;" mode=""></image>
			<!-- <image src="../../../static/退出.png" style="float: right;" mode=""></image> -->
		</view>
	
		
		{{name}}
	</view>
	
	<view class="attendAct" v-show="activityFlag"  style="position: fixed;bottom: 0; width: 95%;height: 50%;left: 20rpx; background-color: #217f99;border-radius: 30rpx;">
		<view class="actTitle" style="width: 100%;height: 200rpx;background-color: #217f99;border-radius: 30rpx;">
			<text >##活动标题简介##</text>
			<view class="back" @click="goBack" style="width: 80rpx;height: 80rpx;position: absolute;right: 0rpx;top: 0rpx;">
				<image src="../../../static/back.png"  mode=""></image>
			</view>
		</view>
		<view class="actContent">
			##活动地点。。。##<br>
			##活动时间。。。##<br>
			##活动内容。。。##<br>
			##活动内容。。。####活动内容。。。##<br>
		</view>
		<view style="border-radius: 30rpx; float: left; width: 350rpx;height: 80rpx;position: absolute;bottom: 200rpx;background-color: #038d18;" >
			加入并分享给关注的人
		</view>
		<view style="border-radius: 30rpx; float: right;width: 300rpx;height: 80rpx; position: absolute;bottom: 200rpx;right: 0rpx;background-color: #038d18;" >
			加入并分享给好友
		</view>
	</view>
	 
	</view>
</template>

<script>
	import navbar from '../../../components/nav-bar.vue'
	export default {
		components:{navbar},
		data() {
			return {
				activityFlag:false,
				name:'xxx',
				startY:0,
				flag:true,
				animationData: {},
				show:false,
				activityShow:false,
				friendslist:[{
							id: 1,
							name: '王建国'
						},
						{
							id: 2,
							name: '王国'
						},
						{
							id: 3,
							name: '王键'
						},
						{
							id: 4,
							name: '建国'
						},],
				list: [
					{
						id: 1,
						title: '第一项'
					},
					{
						id: 2,
						title: '第二项'
					},
					{
						id: 3,
						title: '第三项'
					},
					{
						id: 4,
						title: '第四项'
					},
					{
						id: 5,
						title: '第五项'
					},
					{
						id: 6,
						title: '第六项'
					},
					{
						id: 7,
						title: '第七项'
					},
					{
						id: 8,
						title: '第八项'
					}
				]
			}
		},
		methods: {
			goattend(){
				this.activityFlag = true
				this.activityShow = false
			},
			goBack(){
				this.activityFlag = false
				
			},
			
			showhismessage(){
				this.show = !this.show
			},
			activityShowChange()
			{
				this.activityShow = !this.activityShow
			},
			onUnload() {
			this.animationData = {};
			// 页面关闭后清空数据
		},
		onload() {
			this.animation = uni.createAnimation();
			// 创建动画实例
		},
		readActivity(val){
			
			this.name = val
			// this.$nextTick();
		
			
			var animation = uni.createAnimation({
			 
			  duration: 700,
			  timingFunction: "ease",
			 
			})
			if(this.flag){
				
				animation.height(550).step()
				this.flag = !this.flag
			}
			
			
			
			
			this.animationData = animation.export()
			
			
		},
		gobig(){
			var animation = uni.createAnimation({
			 
			  duration: 700,
			  timingFunction: "ease",
			 
			})
			
				
				animation.height(710).width(370).step()
				
				
				
				
			
			
			
			
			
			this.animationData = animation.export()
			
		},
		back(){
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
	image{
		height: 100%;
		width: 100%;
	}

</style>
