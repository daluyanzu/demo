<template>
	<view class="tab-bar">
			<view v-for="(item,index) in list" :key="index" class="tab-bar-item" @click="switchTab(item, index)">
				<image class="tab_img" :src="selected === index ? item.selectedIconPath : item.iconPath"></image>
				<view class="tab_text" :style="{color: selected === index ? selectedColor : color}">{{item.text}}</view>
			</view>
		</view>

</template>

<script>
	export default {
	
				data() {
					return {
						color: "#02330a",
						selectedColor: "#02330a",
						list: [{
						    pagePath: "/src/tabbar/home/home",
						    iconPath: "/static/bussiness-man.png",
						    selectedIconPath: "/static/bussiness-man.png",
						    text: "主页"
						},
						{
						    pagePath: "/src/tabbar/message/message",
						    iconPath: "/static/bussiness-man.png",
						    selectedIconPath: "/static/bussiness-man.png",
						    text: "信息"
						},
						{
						    pagePath: "/src/tabbar/school/school",
						    iconPath: "/static/bussiness-man.png",
						selectedIconPath: "/static/bussiness-man.png",
						    text: "校友圈"
						},
						{
						    pagePath: "/src/tabbar/myPage/myPage",
						    iconPath: "/static/bussiness-man.png",
						    selectedIconPath: "/static/bussiness-man.png",
						text: "个人主页"
						},
						
						{
						    pagePath: "/src/tabbar/me/me",
						    iconPath: "/static/bussiness-man.png",
						    selectedIconPath: "/static/bussiness-man.png",
						    text: "我的"
						}
						]
					}
				},
				methods: {
					switchTab(item, index) {
						console.log("item", item)
						console.log("index", index)
						let url = item.pagePath;
		                
						
						uni.switchTab({
							url
						})
		 
					}
				}

	}
	
</script>

<style lang="scss">
	.tab-bar {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		height: 100rpx;
		background: #C0C0C0;
		display: flex;
		justify-content: center;
		align-items: center;
		padding-bottom: env(safe-area-inset-bottom); // 适配iphoneX的底部
 
		.tab-bar-item {
			flex: 1;
			text-align: center;
			display: flex;
			justify-content: center;
			align-items: center;
			flex-direction: column;
			border: 1rpx solid black ;
             border-radius: 10%;
			.tab_img {
				width: 40rpx;
				height: 41rpx;
			}
 
			.tab_text {
				font-size: 25rpx;
				margin-top: 9rpx;
			}
		}
	}
</style>
