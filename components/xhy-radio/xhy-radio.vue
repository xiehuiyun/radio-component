<template>
	<label class="radio-div" @tap="selfClick">
		<text class="iconfont radio" 
			:class="{'icon-radio':isCheck,'icon-RadioButton':!isCheck}"
			:style="'color:'+color+';font-size:'+size+'px;'">
		</text>
		<text>{{label}}</text>
	</label>
</template>

<script>
	export default {
		name: "XhyRadio",
		/**
		 * 显示的名称 对应的数值  是否选中
		 */
		props: {
			size: {
				type: [Number,String],
				default: 25
			},
			color: {
				type: String,
				default: '#00FF00'
			},
			label: {
				type: String,
				default: ''
			},
			checked: {
				type: Boolean,
				default: false
			},
			value: {
				type: [String, Boolean],
				default: ''
			}
		},
		inject: ['xhyRadioGroup'],
		data() {
			return {
				isCheck: false
			}
		},
		created() {
			this.isCheck = this.checked;
		},
		methods: {
			/**
			 * 当前点击，向上级传递数据
			 */
			selfClick() {
				if (!this.isCheck) {
					this.isCheck = !this.isCheck;
					if (this.xhyRadioGroup) {
						this.xhyRadioGroup.setSelect(this.value !== '' ? this.value : this.label);
					}
					this.$emit('itemClick');
				}
			},
			setRadioStatus(status) {
				this.isCheck = status;
			}
		}
	}
</script>

<style scoped>
	@import url("/static/xhy-radio/xhy-iconfont.css");

	.radio-div {
		min-width: 230upx;
		margin-right: 10upx;
		display: inline-flex;
		justify-content: flex-start;
		align-items: center;
	}
</style>
