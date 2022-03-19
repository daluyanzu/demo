<template>
	<view style="width: 90%;height: 600rpx;background-color: pink;">
		<scroll-view scroll-y="true" style="height: 300rpx;">
			<view style="border:1rpx solid #8F8F94;width: 100%;" v-for="item in myList" :key="item.time">
				<text v-if="item.id == 'Sam'" style="float: right;clear:both;">{{ item.id }}&nbspsay:\n&nbsp&nbsp{{ item.msg }}</text>
				<text v-if="item.id !== 'Sam'" style="float: left;clear:both;">{{ item.id }}&nbspsay:\n&nbsp&nbsp{{ item.msg }}</text>
			</view>
		</scroll-view>
		<view style="height: 300rpx;background-color: white;"><textarea value="" @confirm="send1" placeholder="" @input="onInput" /></view>
	</view>
</template>

<script>
let timer;
export default {
	data() {
		return {
			myList: [
				{
					id: 'li',
					time: '202101011231',
					msg: 'hello'
				},
				{
					id: 'li',
					time: '202101031231',
					msg: 'hello'
				},
				{
					id: 'Sam',
					time: '202101041231',
					msg: 'hello'
				},
				{
					id: 'Sam',
					time: '202101021231',
					msg: 'hello'
				},
				{
					id: 'Sam',
					time: '2021010213231',
					msg: 'hello'
				},
				{
					id: 'Sam',
					time: '2021010212311',
					msg: 'hello'
				},
				{
					id: 'li',
					time: '202101101231',
					msg: 'bye'
				},
				{
					id: 'Sam',
					time: '202101051231',
					msg: 'bye'
				}
			]
		};
	},
	methods: {
		onInput(e) {
			clearTimeout(timer);

			timer = setTimeout(() => {
				console.log(e.detail.value);
			}, 500);
		},
		send1(e) {
			console.log(e);
		}
	}
};
</script>

<style></style>
