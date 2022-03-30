<template>
	<view>
		<view
			@click="choose"
			class="floatView"
			:style="styleCss"
			:class="fixPosition == 'left' ? 'floatView-left' : 'floatView-right'"
		>
			<slot name="showTextHead"></slot>
			<slot><view style="display: inline-block;">{{ floatShow }}</view></slot>
			<slot name="showTextFoot"></slot>
		</view>
	</view>
</template>

<script>
export default {
	name: 'floatAni',
	/**
	 * @property {Array} floatList 浮动内容
	 * @property {Number} showIndex 浮动开始元素下标，默认0
	 * @property {String} fixPosition 浮动定位位置，left/right,默认left
	 * @property {Number} fixMargin 浮动 left/right 边距，单位px
	 * @property {Number} animation 动画及数据循环总时长，单位s
	 * @property {String} bgColor 浮动内容颜色
	 * @property {Number} beginMargin 浮动开始位置距离屏幕顶部的距离，单位 px
	 * @property {Number} endMargin 浮动结束位置距离屏幕顶部的距离，单位 px
	 * @property {Number} beginOpacity 浮动开始时元素透明度
	 * @property {Number} endOpacity 浮动结束时元素透明度
	 * @property {String} textColor 浮动内容文字颜色
	 * @property {Number} textSize 浮动内容文字大小，单位 px
	 */
	props: {
		floatList: {
			type: Array,
			required: true,
		},
		showIndex: {
			type: Number,
			default: 0,
		},
		fixPosition: {
			type: String,
			default: 'left',
		},
		fixMargin: {
			type: Number,
			default: 10,
		},
		animation: {
			type: Number,
			default: 10,
		},
		bgColor: {
			type: String,
			default: '#d70130',
		},
		beginMargin: {
			type: Number,
			default: 400,
		},
		endMargin: {
			type: Number,
			default: 20,
		},
		beginOpacity: {
			type: Number,
			default: 0.4,
		},
		endOpacity: {
			type: Number,
			default: 0.9,
		},
		textColor: {
			type: String,
			default: '#ffffff',
		},
		textSize: {
			type: Number,
			default: 12,
		},
	},
	model: {
		prop: 'floatList',
		event: 'change',
	},
	data() {
		return {
			floatShow: '',
			floatIndex: this.showIndex,
			styleCss: {
				'--backgroud-color': this.bgColor,
				'--text-color': this.textColor,
				'--text-size': this.textSize + 'px',
				'--fix-postion': this.fixPosition,
				'--fix-margin': this.fixMargin + 'px',
				'--animation-time': this.animation + 's',
				'--start-margin': this.beginMargin + 'px',
				'--stop-margin': this.endMargin + 'px',
				'--begin-opacity': this.beginOpacity,
				'--end-opacity': this.endOpacity,
			},
		};
	},
	mounted() {
		this.showFloat();
	},
	methods: {
		choose() {
			this.$emit('choose', this.floatIndex);
		},
		showFloat() {
			this.floatShow = this.floatList[this.floatIndex];
			setInterval(() => {
				this.floatIndex++;
				if (this.floatIndex == this.floatList.length) {
					this.floatIndex = 0;
				}
				this.floatShow = this.floatList[this.floatIndex];
			}, this.animation * 1000 + 200);
		},
	},
};
</script>

<style lang="scss" scoped>
.floatView {
	color: var(--text-color);
	font-size: var(--text-size);
	padding: 2px 10px;
	border-radius: 500px;
	animation: floatView_animation var(--animation-time) linear 0ms infinite;
	&:hover {
		animation-play-state: paused;
	}
}
.floatView-left {
	position: fixed;
	left: var(--fix-margin);
}
.floatView-right {
	position: fixed;
	right: var(--fix-margin);
}
@keyframes floatView_animation {
	0% {
		background-color: var(--backgroud-color);
		position: fixed;
		top: var(--start-margin);
		opacity: var(--begin-opacity);
	}
	90% {
		background-color: var(--backgroud-color);
		position: fixed;
		top: var(--stop-margin);
		opacity: var(--end-opacity);
	}
	100% {
		background-color: var(--backgroud-color);
		position: fixed;
		top: var(--stop-margin);
		opacity: var(--end-opacity);
	}
}
</style>
