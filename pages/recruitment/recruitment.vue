<template>
	<view>
		<view class="head-img" style="width: 100%;height: 300rpx;background-color: #808080;"></view>
		<view class="body-box" style="width: 100%;height: 100%;background-color: #C0C0C0;">
			<view class="body-head" style="width: 100%;height: 100rpx;background-color: #C0C0C0;">
				<view style="width: 15%;height: 60%;border-radius: 10rpx;float: left;margin-right: 20rpx;margin-top: 15rpx;background-color: #3F536E;">所有</view>
				<view style="width: 15%;height: 60%;border-radius: 10rpx;float: left;margin-right: 20rpx;margin-top: 15rpx;background-color: #3F536E;">已投递</view>
				<view style="width: 15%;height: 60%;border-radius: 10rpx;float: left;margin-right: 20rpx;margin-top: 15rpx;background-color: #3F536E;">未投递</view>
				<view style="width: 10%;height: 60%;border-radius: 10rpx;float: right;margin-right: 20rpx;margin-top: 15rpx;background-color: #3F536E;">位置</view>
				<view style="width: 10%;height: 60%;border-radius: 10rpx;float: right;margin-right: 20rpx;margin-top: 15rpx;background-color: #3F536E;">筛选</view>
			</view>
			<view class="recommend" style="width: 90%;height: 250rpx;margin: 30rpx auto;background-color: white;border-radius: 10rpx;">
				<view class="recommend-title">名企选择</view>

				<view class="recommend-img" style="width: 100rpx;height: 100rpx;border-radius: 50%; float: left;margin-right: 20rpx;margin-top: 30rpx;border: 1rpx #333333 solid ;">
					<image src="../../static/bussiness-man.png" style="width: 100%;height: 100%;" mode=""></image>
				</view>
				<view class="recommend-img" style="width: 100rpx;height: 100rpx;border-radius: 50%;float: left;margin-right: 20rpx;margin-top: 30rpx; border: 1rpx #333333 solid ;">
					<image src="../../static/bussiness-man.png" style="width: 100%;height: 100%;" mode=""></image>
				</view>
				<view class="recommend-img" style="width: 100rpx;height: 100rpx;border-radius: 50%;float: left;margin-right: 20rpx;margin-top: 30rpx;border: 1rpx #333333 solid ;">
					<image src="../../static/bussiness-man.png" style="width: 100%;height: 100%;" mode=""></image>
				</view>
				<view class="recommend-img" style="width: 100rpx;height: 100rpx;border-radius: 50%;float: left;margin-right: 20rpx;margin-top: 30rpx;border: 1rpx #333333 solid ;">
					<image src="../../static/bussiness-man.png" style="width: 100%;height: 100%;" mode=""></image>
				</view>
				<view class="recommend-img" style="width: 100rpx;height: 100rpx;border-radius: 50%;float: left;margin-right: 20rpx;margin-top: 30rpx;border: 1rpx #333333 solid ;">
					<image src="../../static/bussiness-man.png" style="width: 100%;height: 100%;" mode=""></image>
				</view>
			</view>
			<view class="jobForyuo" style="width: 90%;height: 100%;margin:10rpx auto;border-radius: 10rpx;" >
				<view class="jobHeader" style="width: 100%;height: 100rpx;background-color: white;">
					<text style="float: left;">职位推荐</text>
					<view class="jobAllChoose">
						<label style="float: left;">
							<checkbox :value="true" /><text>多选</text>
						</label>
					</view>
				</view>
				<view
				v-for="item in shareList"
				class="recommendToyuo"
				style="width: 100%;height: 300rpx; background-color: white;  position: relative;">
				xx公司{{ item.title }}
				<view class="img" style="height: 130rpx;width: 130rpx;border: 1rpx solid #333333;border-radius: 50%; margin: 30rpx 0 0 30rpx; ">
					<image src="../../static/Customer%20management.png" style="width: 100%;height: 100%;" mode=""></image>
				</view>

				<view class="toAttend" style="width: 130rpx; height: 70rpx;background-color: #3F536E;position: absolute; right: 50rpx; top: 50%;transform: translateY(-50%);">
					直接投递
				</view>
			</view>
			</view>
			
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			shareList: [
				{
					id: 1,
					title: '财务'
				},
				{
					id: 2,
					title: '经理'
				},
				{
					id: 3,
					title: '会计'
				},
				{
					id: 4,
					title: '文员'
				},
				{
					id: 5,
					title: '前台'
				}
			]
		};
	},
	methods: {}
};
</script>

<style></style>
