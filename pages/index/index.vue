<template>
	<view>
		<view class="padding">单独使用MyRadio</view>
		<xhy-radio :checked="singleRadioCheck" label="单独radio" value="single" color="#ff55ff"></xhy-radio>
		<view class="padding">RadioGroup</view>
		<xhy-radio-group @change="setRadioSelect">
			<xhy-radio :checked="radioSelect=='radio1'" label="radio1" value="radio1" color="#ff55ff"></xhy-radio>
			<xhy-radio :checked="radioSelect=='radio2'" label="radio2" value="radio2" color="#ff55ff"></xhy-radio>
		</xhy-radio-group>
	</view>
</template>

<script>
	import XhyRadioGroup from '@/components/xhy-radio/xhy-radio-group';
	import XhyRadio from '@/components/xhy-radio/xhy-radio';
	export default {
		components:{
			XhyRadioGroup,
			XhyRadio
		},
		data() {
			return {
				singleRadioCheck:false,
				radioSelect:'radio1'
			}
		},
		onLoad() {

		},
		methods: {
			setRadioSelect(e){
				console.log(e);
			}
		}
	}
</script>

<style>
	.padding{
		padding:5upx 30upx;
		border-left: 10upx solid #3F536E;
		margin:15upx 30upx;
	}
</style>
