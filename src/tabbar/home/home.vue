<template>
	<view style="width: 100%;height: 100%;">
		<view class="home-header" style="width: 100%;height:60rpx;background-color: #8F8F94;"></view>
		<view class="home-video" style="width: 100;height: 100%;" @touchstart="touchStart" @touchend="touchEnd">
			
			
			
		</view>
		
	</view>
</template>

<script>
	import chat from '../../components/chat/chat/chat.vue'
	
	export default {
		components:{chat},
		data() {
			return {
				startX:0,
				
			}
		},
		
		
		methods: {
			 
				   touchStart(e){
						if (e.touches.length == 1) {
							//设置触摸起始点水平方向位置
							this.startX=e.touches[0].clientX;
						}
					},
					
					
					touchEnd(e){
						if (e.changedTouches.length == 1) {
							//手指移动结束后水平位置
							var endX = e.changedTouches[0].clientX;
							let diff = endX-this.startX;
							if(Math.abs(diff)>100){
								if(diff>0){
									console.log("左滑...");
									
								}else{
									uni.switchTab({
										url:"/src/tabbar/me/me",
										     
									})
									console.log("右滑...");
								}
							}
						}
					
					},
			
		}
	}
</script>

<style>
	page{
		width: 100%;height: 100%;
	}

</style>
