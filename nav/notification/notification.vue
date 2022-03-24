<template>
	<view>
		<navbar :nav_btn="nav_btn"></navbar>
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
				nav_btn: "notification",
				selected: 0				
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
