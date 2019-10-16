<template>
	<view class="loading">{{loading}}</view>
</template>

<script>
	export default{
		props:{
			loading:String
		}
	}
</script>

<style lang="less" scoped>
	.loading{
		height: 100upx;
		color: #CCCCCC;
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
