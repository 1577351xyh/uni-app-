<template>
	<view class="action">
		<!-- 自定义导航栏 -->

			<uni-nav-bar :statusBar="true" class="navbar">
				<block slot="left" class="headericon">
					<view class="left-icon iconfont icon-qiandao"></view>
				</block>
				<view class="center-text">
					<view class="text_box">
						<text>关注</text>
						<text>话题</text>
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
	export default {
		data() {
			return {
				
			}
		},
		components:{
			uniNavBar
		},
		methods: {
			
		},
		created() {
			console.log(uniNavBar)
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
			width: 100%;
			height: 100%;
			display: flex;
			align-content: center;
			justify-content: center;
			.text_box{
				display: flex;
				align-items: center;
				justify-content: space-between;
				width: 130upx;
				view{
					flex: 1;
				}
			}
		}
	}
	
</style>
