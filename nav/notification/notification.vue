<template>
	<view>
		<!-- 顶部导航栏 -->
		<navbar :nav_btn="nav_btn"></navbar>

		<uni-collapse ref="collapse">
			<!-- 系统通知 -->
			<uni-collapse-item>
				<template v-slot:title>
					<view class="message-item">
						<view class="point">
							<view class="red-point" v-if="sysHavenew"></view>
						</view>
						<!-- 头像 -->
						<image src="../../static/image.png" class="img"></image>
						<view class="content" style="width: 60%;">
							<!-- 名字 -->
							<text class="title">系统通知</text>
							<!-- 通知消息 -->
							<text class="notification">还有{{sysList.length}}条通知</text>
						</view>
						<!-- 通知时间 -->
						<view class="time">
							<text>{{sysList[0].time}}</text>
						</view>
					</view>
				</template>
				<!-- 展开 -->
				<uni-swipe-action>
					<uni-swipe-action-item v-for="(item,index) in sysList" :rightOptions="options"
						@click="sys_swipeClick($event, index)">
						<view class="message-item">
							<!-- 通知类型 -->
							<view class="Type">
								<image :src="item.type" mode="aspectFit" class="type"></image>
							</view> <!-- 头像 -->
							<image :src="item.img" class="img"></image>
							<!-- 通知内容 -->
							<view class="content" style="width: 45%;">{{item.content}}</view>
							<!-- 通知时间 -->
							<view class="time">
								<text>{{item.time}}</text>
							</view>
						</view>
					</uni-swipe-action-item>
				</uni-swipe-action>
			</uni-collapse-item>
			<!-- 好友动态 -->
			<uni-collapse-item>
				<template v-slot:title>
					<view class="message-item">
						<view class="point">
							<view class="red-point" v-if="friHavenew"></view>
						</view>
						<!-- 头像 -->
						<image src="../../static/image.png" class="img"></image>
						<view class="content" style="width: 60%;">
							<!-- 名字 -->
							<text class="title">好友动态</text>
							<!-- 通知消息 -->
							<text class="notification">还有{{friList.length}}条通知</text>
						</view>
						<!-- 通知时间 -->
						<view class="time">
							<text>{{sysList[0].time}}</text>
						</view>
					</view>
				</template>
				<!-- 展开 -->
				<uni-swipe-action>
					<uni-swipe-action-item v-for="(item,index) in friList" :rightOptions="options"
						@click="fri_swipeClick($event, index)">
						<view class="message-item">
							<!-- 通知类型 -->
							<view class="Type">
								<image :src="item.type" mode="aspectFit" class="type"></image>
							</view> <!-- 头像 -->
							<image :src="item.img" class="img"></image>
							<!-- 通知内容 -->
							<view class="content" style="width: 45%;">{{item.content}}</view>
							<!-- 通知时间 -->
							<view class="time">
								<text>{{item.time}}</text>
							</view>
						</view>
					</uni-swipe-action-item>
				</uni-swipe-action>
			</uni-collapse-item>
		</uni-collapse>

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
				sysHavenew: true,
				friHavenew: true,
				nav_btn: "notification",
				selected: 0,
				// 系统通知内容
				sysList: [{
						img: '/static/image.png',
						content: '王建国关注了你',
						time: '4小时前',
						type: '/static/smile.png'
					},
					{
						img: '/static/image.png',
						content: '汪东城关注了你',
						time: '6小时前',
						type: '/static/smile.png'
					}
				],
				// 好友动态内容
				friList: [{
					img: '/static/image.png',
					content: '王建国分享了一个职业发布',
					time: '4小时前',
					type: '/static/file.png'
				}],
				// 左滑选项
				options: [{
						text: '收藏',
						style: {
							backgroundColor: '#3686ee'
						}
					},
					{
						text: '转发',
						style: {
							backgroundColor: '#f19c46',
						}
					},
					{
						text: '删除',
						style: {
							backgroundColor: '#f75855',
						}
					},
				],
			}
		},
		methods: {
			sys_swipeClick: function(e, index) {
				let {
					content
				} = e
				// console.log(content)
				if (content.text === "删除") {
					this.sysList.splice(index, 1)
					if(!this.sysList.length){  ////判断系统通知内容是否为空，如果为空则取消红点显示
						this.sysHavenew = false
					}
				} else {
					uni.showToast({
						title: `点击了${content.text}按钮`,
						icon: 'none'
					})
				}
				this.$nextTick(() => {  //这个方法作用是当数据被修改后使用这个方法会回调获取更新后的dom再渲染出来
					this.$refs.collapse.resize()
				})
			},
			fri_swipeClick: function(e, index) {
				let {
					content
				} = e
				// console.log(content)
				if (content.text === "删除") {
					this.friList.splice(index, 1)
					if(!this.friList.length){  //判断好友动态内容是否为空，如果为空则取消红点显示
						this.friHavenew = false
					}
				} else {
					uni.showToast({
						title: `点击了${content.text}按钮`,
						icon: 'none'
					})
				}
				this.$nextTick(() => {
					this.$refs.collapse.resize()
				})
			}
		}
	}
</script>

<style>
	.message-item {
		flex: 1;
		/* height: 80px; */
		/* line-height: 100px; */
		padding: 0 20rpx;
		position: relative;
		background-color: #fff;
		/* border-bottom: #e3e3e3 2rpx solid; */
		display: flex;
		flex-direction: row;
		padding-top: 30rpx;
		padding-bottom: 30rpx;
		font-family: Microsoft YaHei;
	}

	.img {
		width: 120rpx;
		height: 120rpx;
	}

	.content {
		display: flex;
		flex-direction: column;
		margin-left: 20rpx;
		padding-top: 15rpx;
	}

	.time {
		font-size: 26rpx;
		color: #858585;
		font-weight: 500;
		margin-top: 15rpx;
		text-align: right;
	}

	.title {
		font-weight: bold;
	}

	.notification {
		font-size: 20rpx;
		color: #bababa;
		margin-top: 24rpx;
	}

	.point {
		align-items: center !important;
		display: flex !important;
		margin-right: 10rpx;
		width: 20rpx;
	}

	.red-point {
		background-color: #dc0020;
		width: 20rpx;
		height: 20rpx;
		border-radius: 20rpx;
	}

	.type {
		width: 40rpx;
		height: 40rpx;
	}

	.Type {
		align-items: center !important;
		display: flex !important;
		margin-left: 58rpx;
		margin-right: 10rpx;
	}
</style>
