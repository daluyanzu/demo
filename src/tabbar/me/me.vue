<template>
	<view class="me-body" style="width: 100%;height: 100%;" @click.stop="showFriendFlag()">
		<u-mask>
			<view class="warp" v-show="show" style="width: 50%;height: 30%;background-color: #007AFF;position: fixed;top: 50%;left: 50%;transform: translate(-50%,-50%); ">
				{{ show }}
			</view>
		</u-mask>
		<view class="me-header" style="width: 100%;height:60rpx;background-color: #8F8F94;"></view>
		<view class="me-img" style="width: 100%;height:180rpx;display: flex;justify-content: space-around;">
			<view style="width: 40%;height: 100%; border:2px solid #C0C0C0;">
				
			</view>
			<view style="width: 40%;height: 100%; border:2px solid #C0C0C0; ">
				
			</view>
			
		</view>
		<view class="me-message" style="width: 100%;height:220rpx;background-color: #4CD964;"></view>
		<view class="me-skill" style="width: 100%;height:100%rpx;background-color: #3F536E;">
			<view @click="showskill()" :animation="animationData" class="me-skill-img" style="width: 80%;height:220rpx;background-color: #8F8F94;margin: 0 auto;">
				
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
		<view class="me-friends" style="width: 10%;height:700rpx;background-color: #333333;position: fixed;top: 20%;right: 0; display: flex;flex-flow: column;">
			<view class="me-myFriends" @click.stop="showFriend()" style="width: 100%;height: 10%;background-color: pink;border-radius: 50%;border: 1rpx solid #333333;"></view>
			<view class="me-myFriends" style="width: 100%;height: 10%;background-color: pink;border-radius: 50%;border: 1rpx solid #333333;"></view>
		</view>
	</view>

	
</template>

<script>
export default {
	
	data() {
		return {
			flag:true,
			animationData: {},
			show: false,
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
		showFriendFlag(){
			if(this.show == true){
				this.show = false
			}
		},
		showFriend() {
			this.show = !this.show;
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
				animation.height(110).step()
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

</style>
