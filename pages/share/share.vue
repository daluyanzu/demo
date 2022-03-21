<template>
	<view>
		<view class="shareHead">
			<view class="headimg" style="float: left;margin: 20rpx; width: 120rpx;height: 120rpx;border-radius: 50%;border: 1px black solid;">
				<image src="../../static/bussiness-man.png" style="width: 100%;height: 100%;" mode=""></image>
			</view>
		</view>
		<view class="headname" style="float: left;margin-top: 30rpx;">
		
			<text class="namefont" style="font-weight: 1000;
			font-size: 30rpx;">王建国</text>
			<!-- <picker >
				<view>123</view>
			</picker> -->
			<view @click="showskill()" class="mySelect" :animation="animationData" style="overflow: hidden;display: flex;flex-direction: column;justify-content:space-between;align-items: center;  margin-top: 10rpx; border-radius: 50rpx; width:150rpx ;height: 50rpx;background-color: pink;">
				<text >公开</text><br>
				<text >私有</text><br>
				
			</view>
			
			
			
		</view>
		<textarea value="" placeholder="请输入..." />
		
		
		
		<tabbar></tabbar>
	</view>
</template>

<script>
	import tabbar from '../../custom-tab-bar'
	
	export default {
		components:{
			tabbar
		},
		data() {
			return {
				flag:true,
				animationData: {},
				array:[{id:'1'},{id:'2'},{id:'3'}]
				 
			}
		},
		
		methods: {
			onload() {
				this.animation = uni.createAnimation();
				// 创建动画实例
			},
			showskill(){
				var animation = uni.createAnimation({
				 
				  duration: 700,
				  timingFunction: "ease",
				 
				})
				if(this.flag){
					
					animation.height(50).step()
					this.flag = !this.flag
				}else{
					animation.height(25).step()
					this.flag = !this.flag
				}
				
				
				
				
				this.animationData = animation.export()
				
				
			}
			 
		}
	}
</script>

<style>

</style>
