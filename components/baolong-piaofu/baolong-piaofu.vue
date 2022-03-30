<template>
	<view class="baolong-float-box">
		<view v-if="is_show" v-for="(item,index) in float.density" :key="index" :style="'left:'+pfmark[index].left+'%;animationDelay:'+pfmark[index].animationDelay+'ms;animationDuration:'+pfmark[index].animationDuration+'ms;width:'+pfmark[index].width+'upx'" >
			<image  :src="float.img"  mode="widthFix"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			float: {
				type: Object,
				default(){
					return {show:false,img:"/static/piaofu/1.png",density:20}
				}
			}
		},
		data() {
			return {
				is_show: false,
				param:{
					delay: [400, 10000],
					left: [5, 95],
					duration: [1000, 20000],
					width: [10, 50]
				},
				pfmark:[]
			}
		},
		watch: {
			// 数据
			list: function (newVal, oldVal) {
				this.waterFall();
			}
		},
		// #ifdef H5
		mounted() {
		    if(this.float.show) this.piaofuFall();
		},
		// #endif
		// #ifndef H5
		onReady() {
			if(this.float.show) this.piaofuFall();
		},
		// #endif
		methods: {
			piaofuFall() {
				uni.createSelectorQuery().selectAll('.baolong-flow-box').boundingClientRect().exec(res => {
					let item = res[0],delay,left,duration,width;										
					for (let i = 0; i < this.float.density; i++) {						
						 delay = Math.floor(this.param.delay[0] + Math.random() * (this.param.delay[1] - this.param.delay[0])) + Math.floor(200 + Math.random() * (200 - 50));
						 left = Math.floor(this.param.left[0] + Math.random() * (this.param.left[1] - this.param.left[0]));
						 duration = Math.floor(this.param.duration[0] + Math.random() * (this.param.duration[1] - this.param.duration[0])) + Math.floor(1000 + Math.random() * (1000 - 200));
						 width = Math.floor(this.param.width[0] + Math.random() * (this.param.width[1] - this.param.width[0] ));
						this.pfmark.push({
							left:left,
							animationDelay:delay,
							animationDuration:duration,
							width:width,
							fontSize:width,
						});
					}
					this.is_show = true;
				});
			}
		}
	}
</script>

<style scoped>
	/*漂浮物*/
        .baolong-float-box{
            position: fixed;
            left:0;
			right: 0;
            top:0;
			bottom: 0;
            z-index: 9999999999;
            overflow: hidden;
            pointer-events: none;
        }
        .baolong-float-box view {
             position: fixed;
            top: -20%;
            list-style: none;
            display: block;
            width: 20upx;
            animation: downFloat 10s infinite;
            -webkit-transition-timing-function: linear;
            transition-timing-function: linear;
            z-index: 10;
        }
        .baolong-float-box view image {
            width: 100%;
        }
        @keyframes downFloat {
            0% {
                top: -20%;

            }
            100% {
                top: 110%;
            }
        }
        @keyframes upFloat {
            0% {

            }
            100% {

            }
        }
</style>