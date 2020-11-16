<template>
	<view>
		<view class="padding">单独使用MyRadio</view>
		<my-radio :checked="singleRadioCheck" label="单独radio" value="single" color="#ff55ff"></my-radio>
		<view class="padding">RadioGroup</view>
		<my-radio-group @change="setRadioSelect">
			<my-radio :checked="radioSelect=='radio1'" label="radio1" value="radio1" color="#ff55ff"></my-radio>
			<my-radio :checked="radioSelect=='radio2'" label="radio2" value="radio2" color="#ff55ff"></my-radio>
		</my-radio-group>
	</view>
</template>

<script>
	import MyRadioGroup from '@/components/radio/my-radio-group';
	import MyRadio from '@/components/radio/my-radio';
	export default {
		components:{
			MyRadioGroup,
			MyRadio
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
