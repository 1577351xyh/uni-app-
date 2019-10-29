<template>
	<view class="action">
		<uni-nav-bar :statusBar="true" class="navbar">
			<block slot="left" class="headericon">
				<view class="left-icon iconfont icon-qiandao"></view>
			</block>
			<view class="center-text">
				<view class="text_box" :class="{'active':index===activeindex}" v-for="(item,index) in arr" :key="index" @click="tabclick(index)">
					<text class="text_title">{{item.text}}</text>
					<view class="activeicons"></view>
				</view>
			</view>
			<block slot="right">
				<view class="right-icon iconfont icon-bi"></view>
			</block>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from '../../compument/uni-nav-bar/uni-nav-bar.vue'
	export default{
		props:{
			activeindex:{
				type:Number,
			},
			arr:{
				type:Array,
			}
		},
		components:{
			uniNavBar
		},
		methods:{
			tabclick(index){
				this.$emit('changeActive',index)
			}
		}
	}
</script>

<style scoped lang="less">
	
	.uni-navbar__header-btns{
		width: 25upx;
	}
	.action{
		.navbar{
			display: flex;
			justify-content: space-between;
		}
		.right-icon{
			margin-right: 10%;
			font-size: 36upx;
			color: #FFB400;
		}
		.left-icon{
			margin-left: 10%;
			font-size: 44upx;
			color: #FFB400;
		}
		.center-text{
			margin: 0 auto;
			width: 120upx;
			height: 100%;
			display: flex;
			align-content: center;
			justify-content: space-between;
			.text_box{
				display: flex;
				align-items: center;
				justify-content: center;
				position: relative;
				view{
					flex: 1;
				}
			}
		}
	}
	.active .text_title span{
		color: #000;
	}
	.active .activeicons{
		position: absolute;
		bottom:-6upx;
		left: 50%;
		transform: translateX(-50%);
		width: 110%;
		height: 7upx;
		background-color:#FFB400;
	}
	
</style>
