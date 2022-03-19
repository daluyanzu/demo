<template>
	<!--miniprogram/custom-tab-bar/index.wxml-->
	<view class="tab">123
		
	</view>	
</template>

<script>
</script>

<style>
	.tab-bar {
	  position: fixed;
	  bottom: 0;
	  left: 0;
	  right: 0;
	  height:55px;
	/*  background: black; */
	  display: flex;
	  padding-bottom: env(safe-area-inset-bottom);
	  z-index:-1;
	}
	
	.tab-bar-border {
	  background-color: rgba(0, 0, 0, 0.33);
	  position: absolute;
	  left: 0;
	  top: 0;
	  width: 100%;
	  height: 1px;
	  transform: scaleY(0.5);
	}
	
	.tab-bar-item {
	  flex: 1;
	  text-align: center;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  flex-direction: column;
	  font-size: 13px;
	}
	.tab-bar-item image {
	  width:36.23rpx;
	  height:48rpx;
	}
	
	/* .tab-bar-item-image-0 {
	  width:36.23rpx;
	  height:48rpx;
	} */
	
	/* .tab-bar-item-image-1 { 
	  width:100rpx;
	  height:48rpx !important;
	} */
	
	.tab-bar-item.big image{
		width: 61.59rpx;
		height: 61.59rpx;
	}
	.tab-bar-item cover-image {
	  width: 48.91rpx;
	  height: 48.91rpx;
	}
	
	.tab-bar-item cover-view {
	  font-size: 10px;
	}
	.tab-bar-item  {
		position: relative;
	}
	.tab-bar-item .btn-box .btn {
		opacity: 0;
		padding: 0;
		height: 50px;
		width: 100%;
		position: absolute;
		left: 0;
		top: 0;
	}
</style>
