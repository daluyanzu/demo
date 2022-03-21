<template>
	<view class="me-body" style="width: 100%;height: 100%;" >
		<!-- <u-mask> -->
			<view  v-show="show" style="width: 50%;height: 30%;background-color: #007AFF;position: fixed;top: 50%;left: 50%;transform: translate(-50%,-50%); ">
				<view class="friend-img" style="position: relative;"></view>
				<!-- <button type="default" style="position: absolute;bottom: 0;left: 50%;
		transform: translateX(-50%);" @click.stop="letschat()">私聊</button> -->
		<view class="btn">
			<button type="default" @click.stop="letschat()">私聊</button>
		</view>
			</view>
			<view class="chat-view" v-show="showFlag">
				<Chat ></Chat>
			</view>
		<!-- </u-mask> -->
		<view class="me-header" style="width: 100%;height:100rpx;background-color: #8F8F94;"></view>
		<view class="me-message" style="width: 100%;height:550rpx;position: relative;">
			<view class="me-img" style="width: 130rpx;height: 130rpx;border-radius: 50%;border: 1rpx solid #999999; position: absolute;top: 5%;left: 5%;">
				<image src="../../../static/bussiness-man.png" mode=""></image>	
			</view>
			<view class="name">
					<text class="my-name">王建国</text><br>
					<text class="my-school">清华/计算机/本科/3年经验</text>
				</view>
				
				<view class="my-skill-pic" style="width: 300rpx;height: 150rpx;background-color: #38d1ff;position: absolute; bottom:40rpx ;right:5% ;">
					个人能力图
				</view>
			<view class="me-introduce" style="width: 100%; position: absolute;top: 115rpx;">
				<text>人大人科学研究所</text><br>
				<text>人大人科学研究所某路某楼</text><br>
				<text>中国，成都</text>
			</view>
			
			<button @click.stop="goShare()"  style="width: 25%;height: 15%;position:absolute;bottom: 40rpx;left: 5%;"  >发布</button>
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
		<view class="me-friends" style="width: 10%;height:300rpx;background-color: white;position: fixed;top: 15%;right: 5%; display: flex;flex-flow: column;justify-content: space-between; box-shadow: 2rpx 2rpx 10rpx;border:#C0C0C0 1rpx solid;">
			<view class="me-myFriends" @click.stop="showFriend()" style="width: 100%;height: 25%;border-radius: 50%;border: 1rpx solid #333333;">
				<image  src="../../../static/bussiness-man.png" mode=""></image>
			</view>
			<view class="me-myFriends" style="width: 100%;height: 25%;border-radius: 50%;border: 1rpx solid #333333;">
				<image  src="../../../static/bussiness-man.png" mode=""></image>
			</view>
			<view class="me-myFriends" style="width: 100%;height: 25%;border-radius: 50%;border: 1rpx solid #333333;">
				<image  src="../../../static/bussiness-man.png" mode=""></image>
			</view>
			
		</view>
		<view class="share-nine" v-show="shareFlag">
			<view class="share-things" v-for="item in shareList" @click.stop="goShareThing()">
				{{item.title}}
			</view>
			
		</view>
		
		
	</view>

	
</template>

<script>
	import Chat from '../../components/chat/chat/chat'
export default {
	components:{Chat},
	data() {
		return {
			shareFlag:false,
			flag:true,
			animationData: {},
			show: false,
			showFlag:false,
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
		
		goShare(){
			this.shareFlag = !this.shareFlag
			
			
			
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
		background-color: #38d1ff;
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
