<template>
	<label class="left_center radio-div" @tap="selfClick">
		<text class="iconfont radio" :style="'color:'+color+';'" :class="{'icon-radio':isCheck,'icon-RadioButton':!isCheck}"></text>
		<text>{{label}}</text>
	</label>
</template>

<script>
	export default {
		name: "MyRadio",
		/**
		 * 显示的名称 对应的数值  是否选中
		 */
		props: {
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
		inject: ['radioGroup'],
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
					this.radioGroup.setSelect(this.value !== '' ? this.value : this.label);
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
	@import url("/static/iconfont.css");

	.radio {
		width: 48upx;
		height: 48upx;
		margin-right: 10upx;
	}

	.radio-div {
		min-width: 230upx;
		margin-right: 10upx;
	}
</style>
