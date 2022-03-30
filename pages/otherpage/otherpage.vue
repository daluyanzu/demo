<template>
	<view class="me-body" style="width: 100%;height: 100%;" >
		
		<view class="me-header" style="width: 100%;height:190rpx;background-color: #8F8F94;"><navbar></navbar></view>
		<view class="me-message" style="width: 100%;height:550rpx;position: relative;">
			<view class="me-img" style="width: 130rpx;height: 130rpx;border-radius: 50%;border: 1rpx solid #999999; position: absolute;top: 5%;left: 5%;">
				<image src="../../static/bussiness-man.png" mode=""></image>	
			</view>
			<view class="name">
					<text class="my-name">李石雪(他人)</text><br>
					<text class="my-school">清华/计算机/本科/3年经验</text>
					
					<view class="friend-options">
						<view class="both-friend" @click="friendslists()">
						<view class="me-myFriends" @click.stop="showFriend()" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image  src="../../static/Customer management.png" mode=""></image>
						</view>
						<view class="me-myFriends" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image  src="../../static/Customer management.png" mode=""></image>
						</view>
						<view class="me-myFriends" style="width: 25%;height: 90%;border-radius: 50%;border: 1rpx solid #333333;">
							<image  src="../../static/Customer management.png" mode=""></image>
						</view>
					</view>
					<view class="friendsnumber" style="width: 180rpx;height: 50rpx; position: absolute;top: 120rpx;left: 160rpx;">
							<text style="font-weight: 100;font-size: 25rpx;">117 friends</text>
							<view @click.stop="changeEye" class="img" style="width: 50rpx;height: 50rpx;float: right;">
								<image src="../../static/no_eye.png" style="width: 100%;height: 100%;" v-if="!eyeFlag" mode=""></image>
								<image src="../../static/eye.png" style="width: 100%;height: 100%;" v-if="eyeFlag" mode=""></image>
							</view>
						
							<!-- <image src="../../../static/no_eye.png" mode=""></image> -->
						</view>
					
					
					</view>
					
				</view>
				
				<view class="my-skill-pic" style="width: 330rpx;height: 250rpx;background-color: #38d1ff;position: absolute; bottom:40rpx ;right:5% ;">
					个人能力图
				</view>
			<view class="me-introduce" style="width: 100%; position: absolute;top: 210rpx;">
				<text>人大人科学研究所</text><br>
				<text>人大人科学研究所某路某楼</text><br>
				<text>中国，成都</text>
			</view>
			
			<button   style="width: 20%;height: 10%;position:absolute;bottom: 40rpx;left: 5%;">+关注</button>
			<button @click.stop="goChat()"  style="width: 20%;height: 10%;position:absolute;bottom: 40rpx;left: 28%;"  >私聊</button>
		</view>
		
		<view class="me-skill" style="width: 100%;height:100%;background-color: #3F536E;">
			<view @click="showskill()" :animation="animationData" class="me-skill-img" style="width: 90%;height:320rpx;background-color: #8F8F94;margin: 0 auto;">
				 作品展示
			</view>
			<view class="me-activity">
				<scroll-view scroll-y="true" style="height: 100%;width: 100vw;"
					      >
						<view class="v-option" v-for="item in list" style="margin: 20rpx auto;height: 270rpx; border:2px solid #C0C0C0;" >
							
								{{item.title}}
							
							
							
						</view>
						
					</scroll-view>
					 
				
			</view>
		</view>
		
		<view class="share-nine" v-show="shareFlag">
			<view class="share-things" v-for="item in shareList" @click.stop="goShareThing()">
				{{item.title}}
			</view>
			
		</view>
		
		<view class="myfriends" v-show="friendsFlag">
			
			<scroll-view scroll-y="true" style="height: 100%;width: 100%;"
				      ><view style="width: 60%;height: 10%;background-color:#aa9478;border-radius: 50rpx;margin-left: 50%;transform: translateX(-50%);">
				他的好友
			</view>
					<view class="v-option" v-for="item in friendslist" style="margin: 20rpx auto;height: 200rpx; border:2px solid #C0C0C0; position: relative;" >
						
						<view class="his-img" style="border-radius: 10%; margin: 40rpx 0 0 40rpx; width: 120rpx;height: 120rpx;background-color:#eb692d;">
							{{item.name}}
						</view>	
						<view class="his-message" style="border-radius: 50rpx;width: 200rpx;height: 50rpx;background-color:#3bb503;position: absolute;top: 40rpx;left: 400rpx;">
							关注他
						</view>
						<view  class="his-message" style="border-radius: 50rpx;width: 200rpx;height: 50rpx;background-color:#3bb503;position: absolute;top: 100rpx;left: 400rpx;">
							看他主页
						</view>
					
						
						
						
					</view>
					
				</scroll-view>
		</view>
		
		<view class="chatBox" v-if="chatFlag" style="width: 90%;height: 620rpx;background-color:white;position: fixed ;top: 380rpx;left: 30rpx;border:1rpx solid #333333;border-radius: 30rpx;">
			<view @click="changeChat" class="title" style="width: 100%;height: 10%;">
				<text style="font-weight: 1000;
			font-size: 50rpx;">私聊</text>
			</view>
			
			<chat></chat>
		</view>
		<tabbar></tabbar>
		
		
	</view>

	
</template>

<script>
	import tabbar from '../../custom-tab-bar'
	import chat from '../../components/chat.vue'
	import navbar from '../../components/nav-bar.vue'
export default {
	
	components:{
		tabbar,chat,navbar
	},
	data() {
		return {
			eyeFlag:true,
			chatFlag:false,
			friendsFlag:false,
			shareFlag:false,
			flag:true,
			animationData: {},
			show: false,
			showFlag:false,
			friendslist:[{
						id: 1,
						name: '王建国'
					},
					{
						id: 2,
						name: '王国'
					},
					{
						id: 3,
						name: '王键'
					},
					{
						id: 4,
						name: '建国'
					},
				
			],
			shareList:[
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
					},
					{
						id: 7,
						title: '校友'
					},
					{
						id: 8,
						title: '活动'
					},
					{
						id: 9,
						title: '干货'
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
		changeEye(){
			this.eyeFlag = !this.eyeFlag
		},
		// friendslist(){
		// 	this.friendsFlag = !this.friendsFlag
		// },
		goChat() {
			this.chatFlag = true
			
		},
		changeChat(){
			this.chatFlag=false
		},
		
		goShare(){
			this.shareFlag = !this.shareFlag
			
			
			
		},
		friendslists(){
			this.friendsFlag = !this.friendsFlag
		},
			
		goShareThing(){
			
			uni.navigateTo({
				url:'../../../pages/share/share'
			})
			
			if(this.shareFlag){
				this.shareFlag = false
			}
			
		},
		
		// showFriendFlag(){
		// 	if(this.show == true){
		// 		this.show = false
		// 	}
		// },
		letschat(){
				this.showFlag=true
				if(this.show == true){
					this.show = false
				}
				console.log(345345)
			
		},
		showFriend() {
			this.show = !this.show;
			if(this.showFlag == true)
			{
				this.showFlag = false
			}
			uni.setTabBarBadge({ //显示数字
			  index: 2,//tabbar下标
			  text: '1'//数字
			})
			uni.showTabBarRedDot({
				index: 1,
				text: '5'})
			
		
		},
		onUnload() {
			this.animationData = {};
			// 页面关闭后清空数据
		},
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
				
				animation.height(300).step()
				this.flag = !this.flag
			}else{
				animation.height(130).step()
				this.flag = !this.flag
			}
			
			
			
			
			this.animationData = animation.export()
			
			
		},
		
		onShareTimeline(res){
		    console.log(res)
		    return {
		      title: '测试小程序分享至朋友圈',
		      
		      imageUrl:'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1594374964481&di=3ceba827e91e126012c43de3887a58c7&imgtype=0&src=http%3A%2F%2Fdmimg.5054399.com%2Fallimg%2Fpkm%2Fpk%2F13.jpg'
		    }
		
		  },
		  onShareAppMessage: function(ops) {
		    return {
		      title: "分享卡片",
		      
		
		      }
		     
		  }
		}
		
};
</script>

<style>
	.myfriends{
		width: 85%;
		height: 45%;
		background-color: #466fce;
		position: fixed;
		top: 25%;
		left: 50%;
		transform: translateX(-50%);
			
		
	},
	.friend-options{
		width: 350rpx;
		height: 50rpx;
		
		display: flex;
		justify-content: space-between;
	}
	.both-friend{
		width: 150rpx;
		height: 50rpx;
		background-color: #4CD964;
		margin-top: 20rpx;
		
		display: flex;
		
		justify-content: space-between;
		 border:#C0C0C0 1rpx solid;
		 border-radius: 50rpx;
		
	}
	.recommend-friend{
		width: 150rpx;
		height: 50rpx;
		background-color: #4CD964;
		margin-top: 20rpx;
		display: flex;
		border-radius: 50rpx;
		justify-content: space-between;
		
	}
	
	
	.share-nine{
		width: 80%;
		height: 50%;
		background-color: pink;
		position: fixed;
		top: 35%;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		display: -webkit-flex;
		            justify-content: space-between;
		            flex-direction: row;
		            flex-wrap: wrap;
		
		}
		
.share-things{
	width: 30%;
	height: 30%;
	display: flex;
	justify-content: center;
	align-items: center;
	border: #555555 1rpx solid;
	border-radius: 10%;
	
}

	.name{
		position: absolute;
		left: 190rpx;
		top: 8%;
		
		width: 100%;
		
	}
	.my-name{
			font-weight: 1000;
			font-size: 30rpx;
		}
		.my-school{
			font-weight:100;
			font-size: 20rpx;
		}
		.frident-list{
			font-weight: 1000;
			font-size: 25rpx;
			
		}
	.me-introduce>text{
		font-size: 20rpx;
		margin-left: 3%;
		width: 100%;
	}
	button{
		font-size: 100%;
		line-height: 1.5;
		
	}
	image{
		width: 100%;
		height: 100%;
	}
	.friend-img{
		width: 50%;
		height: 50%;
		position: absolute;
		left: 50%;
		transform: translateX(-50%);
		border-radius: 50%;
		background-color: pink;
	}
	.chat-view{
		width: 80%;height: 400rpx;background-color: pink;float: left;position: fixed;top: 30%;left: 50%;transform: translate(-50%,-50%);
		
	}
	

</style>
