<template>
	<view>
		我是搜索
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value:undefined
			}
		},
		//源生标题导航按钮取消点击事件
		onNavigationBarButtonTap(e) {
			console.log(e);
			if(e.index===0){
				//退回到上一级
				uni.navigateBack({
					delta:1
				})
			}
		},
		//源生搜索框change事件
		onNavigationBarSearchInputChanged(e){
			// this.value= e.text;
			console.log(e.tex)
		},		
		//监听点击搜素事件
		onNavigationBarSearchInputConfirmed(e){
			this.value = e.text;
		},
		methods: {
			
		}
	}
</script>

<style scoped>
	.uni-page-head .uni-page-head-hd {
	    display: none!important;
	}

</style>
