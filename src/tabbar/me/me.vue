<template>
	<view style="width: 100%;height: 100%;">
		
		<view style="width: 100%;height:40%;background-color: #8F8F94;position: relative;">
			<navbar></navbar>
			<view class="my-img">
				<image src="../../../static/head.png" style="width: 100%;height: 100%;" mode=""></image>
			</view>
		</view>
		<view style="border-radius: 10%; margin: 30rpx auto; width: 100;height: 12%;background-color: #4CD964;">
			</view>
		<view style="border-radius: 10%; margin: 30rpx auto; width: 100;height: 24%;background-color: #4CD964;">	
			
		</view>
		
	</view>
</template>


<script>
	import navbar from '../../../components/nav-bar.vue'
export default {
	components:{navbar},
	}
</script>

<style>
	page{
		width: 100%;height: 100%;
	}
	.my-img{
		height: 210rpx;
		width: 210rpx;
		border-radius: 50%;
		
		position: absolute;
		right: 50rpx;
		top: 30%;
	}
	
</style>
