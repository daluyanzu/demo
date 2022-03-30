<template>
	<view>
		<!-- 顶部导航栏 -->
		<navbar :nav_btn="nav_btn"></navbar>

		<view class="topbar">
			<view class="menuBox">
				<button type="default" @click="declick()">播</button>
				<view class="pos" :animation="animationData">
					<view :class="[clicked===index?'active':'default']" 
					:id="index" 
					v-for="(item, index) in Status"
					@click="Click(index)">{{item}}</view>
				</view>
			</view>
		</view>
		<view style="padding-bottom: 200rpx;">
			<view v-show="(Status[clicked]==item.status)||(Status[clicked]=='全部')" 
			class="item" v-for="(item, index) in liveList">
				<!-- 头像 -->
				<image :src="item.img"></image>
				<view class="content">
					<!-- 标题 -->
					<view class="title">
						<view :class="[item.status==='未开始'?'notStart':'finished']">{{item.status}}</view>
						<!-- <view v-else class="finished">{{item.status}}</view> -->
						<text>{{item.title}}</text>
					</view>
					<!-- 直播时间 -->
					<text class="time">直播时间：{{item.time}}</text>
					<!-- 直播员 -->
					<text class="anchor">直播：{{item.anchor}}</text>
				</view>
			</view>
		</view>

		<!-- 底部导航栏 -->
		<tabbar :selected="selected"></tabbar>
	</view>
</template>

<script>
	import navbar from '../../components/nav-bar.vue'
	import tabbar from '../../custom-tab-bar/index'
	export default {
		components: {
			navbar,
			tabbar
		},
		data() {
			return {
				nav_btn: "live",
				selected: 0,
				liveList: [{
						img: '/static/image.png',
						title: "3.15职发沙龙-搭建高效团队",
						time: "03月15日 18:50-21:30",
						anchor: "孙老师",
						status: "未开始"
					},
					{
						img: '/static/image.png',
						title: "RDR青年电影人沙龙",
						time: "03月10日 19:00-21:00",
						anchor: "Jolin",
						status: "已结束"
					},
					{
						img: '/static/image.png',
						title: "RDR青年电影人沙龙",
						time: "03月10日 19:00-21:00",
						anchor: "Jolin",
						status: "已结束"
					},
					{
						img: '/static/image.png',
						title: "RDR青年电影人沙龙",
						time: "03月10日 19:00-21:00",
						anchor: "Jolin",
						status: "已结束"
					}
				],
				animationData: {},
				off: true,
				Status: ['全部', '直播中', '未开始', '已结束', '其他'],
				clicked: 0
			}
		},

		onLoad() {
			this.animation = uni.createAnimation()
		},
		onShow() {
			var animation = uni.createAnimation({
				duration: 500,
				trmingFunction: 'ease'
			})
			this.animation = animation
		},

		methods: {
			declick() {
				if (this.off) {
					//使用动画
					this.rotateAndScale()
				} else {
					this.norotateAndScale()
				}
				this.off = !this.off
			},
			//定义动画内容
			rotateAndScale() {
				var px = uni.upx2px(650)
				this.animation.rotate(0).translateX(px).step();
				//导出动画数据传递给data层
				this.animationData = this.animation.export();
			},
			//当!off的时候动画回到原始位置
			norotateAndScale() {
				this.animation.rotate(0).translateX(0).step();
				this.animationData = this.animation.export();
			},
			
			Click: function(e){
				this.clicked = e
			}

		}
	}
</script>

<style>
	page {
		background-color: #f1f1f1;
	}

	.topbar {
		width: 96%;
		height: 100rpx;
		border-radius: 20rpx;
		background-color: #FFFFFF;
		margin: 0 auto;
		margin-top: 20rpx;
		display: flex;
		align-items: center;
	}

	.item {
		flex: 1;
		/* height: 80px; */
		/* line-height: 100px; */
		padding: 0 10px;
		position: relative;
		background-color: #fff;
		display: flex;
		flex-direction: row;
		padding-top: 30rpx;
		padding-bottom: 30rpx;
		font-family: Microsoft YaHei;
		width: 90%;
		border-radius: 30rpx;
		margin: 20rpx auto;
	}

	.item image {
		width: 150rpx;
		height: 150rpx;
	}

	.content {
		display: flex;
		flex-direction: column;
		margin-left: 20rpx;
		padding-top: 15rpx;
		width: 80%;
	}

	.title {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.title text {
		font-weight: bold;
		font-size: 30rpx;
	}

	.notStart {
		width: 120rpx;
		height: 50rpx;
		background-color: #555555;
		border-radius: 20rpx;
		color: #FFFFFF;
		font-size: 20rpx;
		text-align: center;
		line-height: 50rpx;
		margin-right: 10rpx;
		border: #555555 2rpx solid;
	}

	.finished {
		width: 120rpx;
		height: 50rpx;
		background-color: #d7d7d7;
		border-radius: 20rpx;
		color: #FFFFFF;
		font-size: 20rpx;
		text-align: center;
		line-height: 50rpx;
		margin-right: 10rpx;
		border: #555555 2rpx solid;
	}

	.time {
		font-size: 28rpx;
		margin-top: 15rpx;
	}

	.anchor {
		color: #888888;
		font-size: 28rpx;
		margin-top: 30rpx;
	}

	.menuBox {
		width: 100%;
		height: 70rpx;
		z-index: 1;
		position: relative;
		/* 	right: -6rpx;
		bottom: 0rpx; */
		left: 6rpx;
		overflow: hidden;
		display: flex;
		align-items: center;
		border-radius: 50rpx;
		/* background-color: #red; */
	}

	.menuBox button {
		width: 70rpx;
		height: 70rpx;
		background: #fff;
		position: absolute;
		/* left: -4rpx; */
		/* bottom: -2rpx; */
		display: flex;
		font-size: 30rpx;
		justify-content: center;
		align-items: center;
		border-radius: 50rpx;
		border: #000000 4rpx solid;
	}

	.pos {
		width: 700rpx;
		height: 70rpx !important;
		position: absolute;
		left: -620rpx;
		/* bottom: -316rpx; */
		z-index: -1;
		display: flex;
		align-items: center;
		flex-direction: row;
		/* background-color: #d5d5d5; */
		border-radius: 54rpx;
		padding-left: 50rpx;
	}

	.default {
		background-color: #FFFFFF;
		font-size: 26rpx;
		width: 110rpx;
		height: 44rpx;
		border-radius: 18rpx;
		border: #034462 2rpx solid;
		line-height: 44rpx;
		align-items: center !important;
		text-align: center;
		margin-right: 10rpx;
	}

	.active {
		background-color: #034462;
		color: #FFFFFF;
		font-size: 26rpx;
		width: 110rpx;
		height: 44rpx;
		border-radius: 18rpx;
		border: #034462 2rpx solid;
		line-height: 44rpx;
		align-items: center !important;
		text-align: center;
		margin-right: 10rpx;
	}
</style>
