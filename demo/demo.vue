<template>
	<view ref="pic1">
		<view id="1" @click="pick(1)" v-show="flag1" :animation="animationData" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: pink;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			IT
		</view>
		<view id="2"  @click="pick(2)" v-show="flag2" :animation="animationData1" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #007AFF;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			金融
		</view>
		<view  id="3"  @click="pick(3)" v-show="flag3" :animation="animationData2" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #ff8f33;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			管理
		</view>
		<view  id="4"  @click="pick1(4)" v-show="flag4" :animation="animationData3" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #ff2ad8;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			前端
		</view>
		<view  id="5"  @click="pick1(5)" v-show="flag5" :animation="animationData4" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #5cff2a;position: fixed;bottom:-100rpx;left: 50%;transform: translateX(-50%);">
			后端
		</view>
		<view  id="6"  @click="pick1(6)" v-show="flag6" :animation="animationData5" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #10fbff;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			测试
		</view>
		<view  id="7"  @click="pick2(7)" v-show="flag7" :animation="animationData6" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #8175ff;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			java
		</view>
		<view  id="8"  @click="pick2(8)" v-show="flag8" :animation="animationData7" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #7effec;position: fixed;bottom:-100rpx;left: 50%;transform: translateX(-50%);">
			c++
		</view>
		<view  id="9"  @click="pick2(9)" v-show="flag9" :animation="animationData8" style="width: 100rpx;height: 100rpx;border-radius: 50%;background-color: #ffc3a4;position: fixed;bottom: -100rpx;left: 50%;transform: translateX(-50%);">
			python
		</view>
	</view>
</template>

<script>
	
	export default {
		components:{
			
		},
		data() {
			return {
				flag1:true,
				flag2:true,
				flag3:true,flag4:true,flag5:true,flag6:true,
					flag7:true,flag8:true,flag9:true,			
				animationData: {},
				animationData1: {},
				animationData2: {},
				animationData3:{},
				animationData4:{},
				animationData5:{},
				animationData6:{},
				animationData7:{},
				animationData8:{},
			}
		},
		
		methods: {
		
			onUnload() {
				this.animationData = {};
				this.animationData1 = {};
				this.animationData2 = {};
				this.animationData3 = {};
				this.animationData4 = {};
				this.animationData5 = {};
				this.animationData6 = {},
				this.animationData7 = {},
				this.animationData8 = {}
				// 页面关闭后清空数据
			},
			onload() {
				this.animation = uni.createAnimation();
				// 创建动画实例
			
				
				
			},
			
			pick(id){
				
				var animation = uni.createAnimation({
					
					timingFunction: 'linear'
				});
				if(id==1){
					animation.translateX(-140).translateY(-700).scale(1.6).step({duration: 1000});
					this.animationData = animation.export();
					this.flag2=false;
					this.flag3=false;
				}else if(id ==2 ){
					animation.translateX(-140).translateY(-700).scale(1.6).step({duration: 1000});
					this.animationData1 = animation.export();
					this.flag1=false;
					this.flag3=false;
				}else if(id == 3){
					animation.translateX(-140).translateY(-700).scale(1.6).step({duration: 1000});
					this.animationData2 = animation.export();
					this.flag2=false;
					this.flag1=false;
				}
				animation.translateX(120).translateY(-130).scale(1.1).step({duration: 1500,}).translateX(-120).translateY(-230).scale(1.2).step({duration:1500}).translateX(-90).translateY(-330).scale(1.3).step({duration:1500}).translateX(100).translateY(-440).scale(1.6).step({duration:1500}); //.translateX(-150).translateY(-600).scale(1.5).step({duration:2500})Math.random() * (max - min) + min
				this.animationData3 = animation.export();
				
				
				animation.translateX(-120).translateY(-100).scale(1.1).step({duration: 1500,}).translateX(0).translateY(-190).scale(1.2).step({duration:1500}).translateX(-100).translateY(-250).scale(1.3).step({duration:1500}).translateX(20).translateY(-370).scale(1.6).step({duration:1500}); //.translateX(100).translateY(-600).scale(1.5).step({duration:2500});Math.random() * (max - min) + min
				this.animationData4 = animation.export();
				
				animation.translateX(80).translateY(-130).scale(1.1).step({duration: 2500,}).translateX(100).translateY(-250).scale(1.2).step({duration:2500}).translateX(-50).translateY(-350).scale(1.3).step({duration:2500}).translateX(-150).translateY(-450).scale(1.6).step({duration:1500}); //.translateX(-25).translateY(-600).scale(1.5).step({duration:2500}Math.random() * (max - min) + min
				this.animationData5 = animation.export();
				
				
			},
			pick1(id){
				var animation = uni.createAnimation({
					
					timingFunction: 'linear'
				});
				if(id ==4){
					animation.translateX(-140).translateY(-610).scale(1.7).step({duration: 1000});
					this.animationData3 = animation.export();
					this.flag5=false;
					this.flag6=false;
				}else if(id ==5){
					animation.translateX(-140).translateY(-610).scale(1.7).step({duration: 1000});
					this.animationData4 = animation.export();
					this.flag4=false;
					this.flag6=false;
				}else if(id ==6){
					animation.translateX(-140).translateY(-610).scale(1.7).step({duration: 1000});
					
					console.log(id)
					this.animationData5 = animation.export();
					this.flag5=false;
					this.flag4=false;
				}
				animation.translateX(120).translateY(-130).scale(1.1).step({duration: 1500,}).translateX(-120).translateY(-230).scale(1.2).step({duration:1500}).translateX(-90).translateY(-330).scale(1.3).step({duration:1500}).translateX(100).translateY(-440).scale(1.6).step({duration:1500}); //.translateX(-150).translateY(-600).scale(1.5).step({duration:2500})Math.random() * (max - min) + min
				this.animationData6 = animation.export();
				
				
				animation.translateX(-120).translateY(-100).scale(1.1).step({duration: 1500,}).translateX(0).translateY(-190).scale(1.2).step({duration:1500}).translateX(-100).translateY(-250).scale(1.3).step({duration:1500}).translateX(20).translateY(-370).scale(1.6).step({duration:1500}); //.translateX(100).translateY(-600).scale(1.5).step({duration:2500});Math.random() * (max - min) + min
				this.animationData7 = animation.export();
				
				animation.translateX(80).translateY(-130).scale(1.1).step({duration: 2500,}).translateX(100).translateY(-250).scale(1.2).step({duration:2500}).translateX(-50).translateY(-350).scale(1.3).step({duration:2500}).translateX(-150).translateY(-450).scale(1.6).step({duration:1500}); //.translateX(-25).translateY(-600).scale(1.5).step({duration:2500}Math.random() * (max - min) + min
				this.animationData8 = animation.export();
				
				
			},
			pick2(id){
				var animation = uni.createAnimation({
					
					timingFunction: 'linear'
				});
				if(id ==7){
					animation.translateX(-140).translateY(-520).scale(1.7).step({duration: 1000});
					this.animationData6 = animation.export();
					this.flag8=false;
					this.flag9=false;
				}else if(id ==8){
					animation.translateX(-140).translateY(-520).scale(1.7).step({duration: 1000});
					this.animationData7 = animation.export();
					this.flag7=false;
					this.flag9=false;
				}else if(id ==9){
					animation.translateX(-140).translateY(-520).scale(1.7).step({duration: 1000});
					
					console.log(id)
					this.animationData8 = animation.export();
					this.flag7=false;
					this.flag8=false;
				}
				
				
			},
			
			
			
			move() {
				
				// createAnimation(animationData3,110,-120,130,-240,-100,-240,110,-440);
				
			 	
				
				var animation = uni.createAnimation({
					
					timingFunction: 'linear'
				});
	
				animation.translateX(120).translateY(-160).scale(1.1).step({duration: 1500,}).translateX(-120).translateY(-250).scale(1.2).step({duration:1500}).translateX(-90).translateY(-350).scale(1.3).step({duration:1500}).translateX(100).translateY(-480).scale(1.6).step({duration:1500}); //.translateX(-150).translateY(-600).scale(1.5).step({duration:2500})Math.random() * (max - min) + min
				this.animationData = animation.export();
				
				
				animation.translateX(-120).translateY(-130).scale(1.1).step({duration: 1500,}).translateX(0).translateY(-220).scale(1.2).step({duration:1500}).translateX(-100).translateY(-280).scale(1.3).step({duration:1500}).translateX(20).translateY(-400).scale(1.6).step({duration:1500}); //.translateX(100).translateY(-600).scale(1.5).step({duration:2500});Math.random() * (max - min) + min
				this.animationData1 = animation.export();
				
				animation.translateX(80).translateY(-120).scale(1.1).step({duration: 1500,}).translateX(100).translateY(-280).scale(1.2).step({duration:1500}).translateX(-50).translateY(-370).scale(1.3).step({duration:1500}).translateX(-150).translateY(-500).scale(1.6).step({duration:1500}); //.translateX(-25).translateY(-600).scale(1.5).step({duration:2500}Math.random() * (max - min) + min
				this.animationData2 = animation.export();
				
				
				
				
			
				
			},
			
			
			
			
		},
		mounted() {
			this.move()
		},
		
	}
</script>

<style>

</style>
