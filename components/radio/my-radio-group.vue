<template>
	<view class="left_right">
		<slot />
	</view>
</template>

<script>
	export default{
		name:'MyRadioGroup',
		provide(){
			return {
				radioGroup:this
			}
		},
		data(){
			return {
				select:''
			}
		},
		watch:{
			select(newVal){
				this.$emit('change',newVal);
				this.$children.forEach(item=>{
					if(item.value!==''){
						item.setRadioStatus(newVal==item.value);	
					}else{
						item.setRadioStatus(newVal==item.label);
					}
				});
			}
		},
		methods:{
			setSelect(value){
				this.select = value;
			}
		}
	}
</script>

<style>
</style>
