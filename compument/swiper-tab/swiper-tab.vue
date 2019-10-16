<template>
	<view>
		<scroll-view scroll-x show-scrollbar="false" class="uni-swiper-tab">
			<block v-for="(tab,index) in tabBars" :key="index">
				<view class="swiper-tab-list" :class="{'active':tabIndex==index}" @click="tabclick(index)">
					{{tab.name}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
			
		</scroll-view>
	</view>
</template>

<script>
	export default{
		props:{
			tabBars:Array,
			tabIndex:Number
		},
		created() {
			console.log(this.tabBars)
		},
		methods:{
			tabclick(index){
				this.$emit("tabclick",index)
			}
		},
		
	}
</script>

<style lang="less">
	.active{
		color:#FFB400;
	}
	.active .swiper-tab-line{
		border-bottom: 6upx solid #FFB400;
		width: 60upx;
		margin: 0 auto;
	}
</style>
