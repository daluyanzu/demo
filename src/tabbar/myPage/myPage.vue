<template>
	<view class="me-body" style="width: 100%;height: 100%;">
		<!-- <u-mask> -->
		<!-- <view  v-show="show" style="width: 50%;height: 30%;background-color: #007AFF;position: fixed;top: 50%;left: 50%;transform: translate(-50%,-50%); ">
				<view class="friend-img" style="position: relative;"></view> -->
		<!-- <button type="default" style="position: absolute;bottom: 0;left: 50%;
		transform: translateX(-50%);" @click.stop="letschat()">私聊</button> -->
		<!-- <view class="btn">
			<button type="default" @click.stop="letschat()">私聊</button>
		</view>
			</view>
			<view class="chat-view" v-show="showFlag">
				<Chat ></Chat>
			</view> -->
		<!-- </u-mask> -->
		<view class="me-header" style="width: 100%;height:190rpx;background-color: #8F8F94;"><navbar></navbar></view>
		<view class="me-message" style="width: 100%;height:550rpx;position: relative;">
			<view class="me-img" style="width: 130rpx;height: 130rpx;border-radius: 50%;border: 1rpx solid #999999; position: absolute;top: 5%;left: 5%;">
				<image src="../../../static/head.png" mode=""></image>
			</view>
			<view class="name">
				<text class="my-name">王建国(自己)</text>
				<br />
				<text class="my-school">清华/计算机/本科/3年经验</text>

				<view class="friend-options">
					<view class="both-friend" @click="friendslists()">
						<view class="me-myFriends" @click.stop="showFriend()" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image src="../../../static/bussiness-man.png" mode=""></image>
						</view>
						<view class="me-myFriends" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image src="../../../static/bussiness-man.png" mode=""></image>
						</view>
						<view class="me-myFriends" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image src="../../../static/bussiness-man.png" mode=""></image>
						</view>
						<view class="me-myFriends" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image src="../../../static/bussiness-man.png" mode=""></image>
						</view>
						<view class="me-myFriends" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image src="../../../static/bussiness-man.png" mode=""></image>
						</view>
					</view>
					<view class="friendsnumber" style="width: 180rpx;height: 50rpx; position: absolute;top: 120rpx;left: 160rpx;">
						<text style="font-weight: 100;font-size: 25rpx;">117 friends</text>
						<view @click.stop="changeEye" class="img" style="width: 50rpx;height: 50rpx;float: right;">
							<image src="../../../static/no_eye.png" style="width: 100%;height: 100%;" v-if="!eyeFlag" mode=""></image>
							<image src="../../../static/eye.png" style="width: 100%;height: 100%;" v-if="eyeFlag" mode=""></image>
						</view>

						<!-- <image src="../../../static/no_eye.png" mode=""></image> -->
					</view>
				</view>
			</view>

			<view class="my-skill-pic" style="width: 330rpx;height: 250rpx;background-color: #38d1ff;position: absolute; bottom:40rpx ;right:5% ;">个人能力图</view>
			<view class="me-introduce" style="width: 100%; position: absolute;top: 210rpx;">
				<text>人大人科学研究所</text>
				<br />
				<text>人大人科学研究所某路某楼</text>
				<br />
				<text>中国，成都</text>
			</view>
		</view>
		<view class="share-nine">
			<view class="share-things" v-for="item in shareList" @click.stop="goShareThing()">{{ item.title }}</view>
		</view>

		<view @click="showskill()" :animation="animationData" class="me-skill-img" style="width: 90%;height:260rpx;background-color: #8F8F94;margin: 0 auto;">作品展示</view>
		<view class="me-activity">
			<scroll-view scroll-y="true" style="height: 100%;width: 100vw;">
				<view class="v-option" v-for="item in list" style="margin: 20rpx auto;height: 270rpx; border:2px solid #C0C0C0;">{{ item.title }}</view>
			</scroll-view>
		</view>

		<view class="myfriends" v-show="friendsFlag">
			<scroll-view scroll-y="true" style="height: 100%;width: 50%;float: left;">
				<view class="his-message" style="border-radius: 50rpx;width: 250rpx;height: 50rpx;background-color:#3bb503;position: absolute;top: 30rpx;left: 80rpx;">
					我的好友
				</view>
				<view class="v-option" v-for="item in friendslist" style="margin: 20rpx auto;height: 200rpx; border:2px solid #C0C0C0; position: relative;">
					<view @click="goTohisPage()" class="his-img" style="border-radius: 50%; margin: 60rpx 0 0 20rpx; width: 120rpx;height: 120rpx;background-color:#eb692d;">
						{{ item.name }}
					</view>

					<view class="his-friends" style="width: 380rpx;height: 80rpx;position: absolute;top: 110rpx;left: 200rpx; display: flex;justify-content: space-between;">
						<view @click="goTohisPage" style="width: 40%;height: 100%;background-color:#aa9478;border-radius: 10%;">查看主页</view>
					</view>
				</view>
			</scroll-view>
			<scroll-view scroll-y="true" style="height: 100%;width: 50%;float: right;">
				<view class="his-message" style="border-radius: 50rpx;width: 250rpx;height: 50rpx;background-color:#3bb503;position: absolute;top: 30rpx;left: 80rpx;">
					推荐好友
				</view>
				<view class="v-option" v-for="item in friendslist" style="margin: 20rpx auto;height: 200rpx; border:2px solid #C0C0C0; position: relative;">
					<view class="his-img" style="border-radius: 50%; margin: 60rpx 0 0 20rpx; width: 120rpx;height: 120rpx;background-color:#eb692d;">{{ item.name }}</view>

					<view class="his-friends" style="width: 380rpx;height: 80rpx;position: absolute;top: 110rpx;left: 200rpx; display: flex;justify-content: space-between;">
						<view @click="goTohisPage" style="width: 40%;height: 100%;background-color:#aa9478;border-radius: 10%;">查看主页</view>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
import Chat from '../../components/chat/chat/chat';
import navbar from '../../../components/nav-bar.vue';
export default {
	components: { Chat, navbar },
	data() {
		return {
			eyeFlag: true,
			friendsFlag: false,

			flag: true,
			animationData: {},
			show: false,
			showFlag: false,
			friendslist: [
				{
					id: 1,
					name: '李石雪'
				},
				{
					id: 2,
					name: '李石'
				},
				{
					id: 3,
					name: '李雪'
				},
				{
					id: 4,
					name: '石雪'
				}
			],
			shareList: [
				{
					id: 1,
					title: '留言板'
				},
				{
					id: 2,
					title: '图片'
				},
				{
					id: 3,
					title: '视频'
				},
				{
					id: 4,
					title: '项目'
				},
				{
					id: 5,
					title: '找工作'
				},
				{
					id: 6,
					title: '职场'
				}
			],

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
		};
	},
	methods: {
		changeEye() {
			this.eyeFlag = !this.eyeFlag;
		},
		// friendslist(){
		// 	this.friendsFlag = !this.friendsFlag
		// },
		goTohisPage() {
			uni.navigateTo({
				url: '../../../pages/otherpage/otherpage'
			}),
				(this.friendsFlag = false);
		},

		goShare() {
			this.shareFlag = !this.shareFlag;
		},
		friendslists() {
			this.friendsFlag = !this.friendsFlag;
		},

		goShareThing() {
			uni.navigateTo({
				url: '../../../pages/share/share'
			});

			if (this.shareFlag) {
				this.shareFlag = false;
			}
		},

		// showFriendFlag(){
		// 	if(this.show == true){
		// 		this.show = false
		// 	}
		// },
		letschat() {
			this.showFlag = true;
			if (this.show == true) {
				this.show = false;
			}
			console.log(345345);
		},
		showFriend() {
			this.show = !this.show;
			if (this.showFlag == true) {
				this.showFlag = false;
			}
			uni.setTabBarBadge({
				//显示数字
				index: 2, //tabbar下标
				text: '1' //数字
			});
			uni.showTabBarRedDot({
				index: 1,
				text: '5'
			});
		},
		onUnload() {
			this.animationData = {};
			// 页面关闭后清空数据
		},
		onload() {
			this.animation = uni.createAnimation();
			// 创建动画实例
		},
		showskill() {
			var animation = uni.createAnimation({
				duration: 700,
				timingFunction: 'ease'
			});
			if (this.flag) {
				animation.height(300).step();
				this.flag = !this.flag;
			} else {
				animation.height(130).step();
				this.flag = !this.flag;
			}

			this.animationData = animation.export();
		},

		onShareTimeline(res) {
			console.log(res);
			return {
				title: '快来围观大牛',

				imageUrl: '../../../static/my.jpg'
			};
		},
		onShareAppMessage: function(ops) {
			return {
				title: '分享卡片'
			};
		}
	}
};
</script>

<style>
.myfriends {
	width: 98%;
	height: 35%;
	background-color: #466fce;
	position: fixed;
	top: 25%;
	left: 50%;
	transform: translateX(-50%);
}
,
.friend-options {
	width: 350rpx;
	height: 50rpx;

	display: flex;
	justify-content: space-between;
}
.both-friend {
	width: 150rpx;
	height: 50rpx;

	margin-top: 20rpx;

	display: flex;

	justify-content: space-between;
	border: #c0c0c0 1rpx solid;
	border-radius: 50rpx;
}
.recommend-friend {
	width: 150rpx;
	height: 50rpx;
	background-color: #4cd964;
	margin-top: 20rpx;
	display: flex;
	border-radius: 50rpx;
	justify-content: space-between;
}

.share-nine {
	width: 100%;
	height: 200rpx;
	background-color: #9e7233;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-around;
}

.share-things {
	width: 30%;
	height: 40%;
	display: flex;
	justify-content: center;
	align-items: center;
	border: #555555 1rpx solid;
	border-radius: 30rpx;
}

.name {
	position: absolute;
	left: 190rpx;
	top: 8%;

	width: 100%;
}
.my-name {
	font-weight: 1000;
	font-size: 30rpx;
}
.my-school {
	font-weight: 100;
	font-size: 20rpx;
}
.frident-list {
	font-weight: 1000;
	font-size: 25rpx;
}
.me-introduce > text {
	font-size: 20rpx;
	margin-left: 3%;
	width: 100%;
}
button {
	font-size: 100%;
	line-height: 1.5;
}
image {
	width: 100%;
	height: 100%;
}
.friend-img {
	width: 50%;
	height: 50%;
	position: absolute;
	left: 50%;
	transform: translateX(-50%);
	border-radius: 50%;
	background-color: pink;
}
.chat-view {
	width: 80%;
	height: 400rpx;
	background-color: pink;
	float: left;
	position: fixed;
	top: 30%;
	left: 50%;
	transform: translate(-50%, -50%);
}
</style>
