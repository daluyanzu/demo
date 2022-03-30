<template>
	<view>
		<navbar></navbar>
		<uni-swipe-action>
			<uni-swipe-action-item v-for="(item,index) in chatList" :key="item.id" :rightOptions="options"
				@click="swipeClick($event, index)">
				<view class="message-item">
					<!-- 头像 -->
					<image :src="item.img" mode="aspectFit"></image>
					<view class="content">
						<!-- 名字 -->
						<text class="name">{{item.name}}</text>
						<!-- 学历 -->
						<text class="subject">{{item.subject}}</text>
						<!-- 最后一条消息 -->
						<text class="lastMsg">{{item.lastMessage}}</text>
					</view>
					<!-- 最后对话时间 -->
					<view class="time">
						<text>{{item.lastTime}}</text>
					</view>
				</view>
			</uni-swipe-action-item>
		</uni-swipe-action>
	</view>
</template>

<script>
	import navbar from '../../../components/nav-bar.vue'
	export default {
		components:{navbar},
		data() {
			return {
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
				// 聊天对象数据
				chatList: [{
						id: 0,
						name: "王建国",
						subject: "学历/专业",
						lastMessage: "您好，我是RDR的张老师",
						lastTime: "2小时前",
						img: "/static/默认头像.png"
					},
					{
						id: 0,
						name: "王建国",
						subject: "学历/专业",
						lastMessage: "您好，我是RDR的张老师",
						lastTime: "2小时前",
						img: "/static/默认头像.png"
					},
					{
						id: 0,
						name: "王建国",
						subject: "学历/专业",
						lastMessage: "您好，我是RDR的张老师",
						lastTime: "2小时前",
						img: "/static/默认头像.png"
					}
				]
			}
		},
		methods: {
			swipeClick: function(e, index){
				let {content} = e
				// console.log(content)
				if(content.text === "删除"){
					this.chatList.splice(index, 1)
				}else{
					uni.showToast({
						title: `点击了${content.text}按钮`,
						icon: 'none'
					})
				}
			}
		}
	}
</script>

<style>
	page{
		background-color: #f9f9f9;
	}
	
	.message-item {
		flex: 1;
		/* height: 80px; */
		/* line-height: 100px; */
		padding: 0 15px;
		position: relative;
		background-color: #fff;
		border-bottom: #e3e3e3 2rpx solid;
		display: flex;
		flex-direction: row;
		padding-top:30rpx;
		padding-bottom:30rpx;
		font-family: Microsoft YaHei;
	}
	.message-item image{
		width: 100rpx;
		height: 100rpx;
	}
	
	.content-text {
		font-size: 15px;
	}
	
	.content{
		display: flex;
		flex-direction: column;
		margin-left: 15rpx;
		padding-top: 15rpx;
		width: 70%;
	}
	.name{
		font-size: 32rpx;
		font-weight: bold;
	}
	.subject{
		font-size: 24rpx;
		font-weight: bold;
		margin-top: 6rpx;
	}
	.lastMsg{
		font-size: 28rpx;
		color: #858585;
		font-weight:500;
		margin-top: 20rpx;
	}
	.time{
		font-size: 26rpx;
		color: #858585;
		font-weight: 500;
		margin-top: 15rpx;
		text-align: right;
	}
</style>
