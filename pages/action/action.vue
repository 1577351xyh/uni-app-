<template>
	<view class="action">
		<!-- 自定义导航栏 -->
			<uni-nav-bar :statusBar="true" class="navbar">
				<block slot="left" class="headericon">
					<view class="left-icon iconfont icon-qiandao"></view>
				</block>
				<view class="center-text">
					<view class="text_box" :class="{'active':index===activeindex}" v-for="(item,index) in text" :key="index" @click="tabclick(index)">
						<text class="text_title">{{item.text}}</text>
						<view class="activeicons"></view>
					</view>
				</view>
				<block slot="right">
					<view class="right-icon iconfont icon-bi"></view>
				</block>
			</uni-nav-bar>
		
		<!-- 公共列表 -->
		<view class="list_center flex">
			<view class="list_center_left">
				<image src="../../static/images/userpic/8.jpg" mode=""></image>
			</view>
			<view class="list_center_right">
				<view class="name flex">
					<view class="flex name_item">
						<view class="text_color">我是名称</view>
						<view class="jieshao">
							<view class="iconfont icon-xingbienan1" style="font-size: 24upx;">25岁</view>
						</view>
					</view>
					<view class="flex center name_item">
						<view class="flex guanzhu">
							<view class="iconfont icon-jia" style="font-size: 24upx;">关注</view>
						</view>
						<view class="iconfont icon-fork"></view>
					</view>
				</view>
				<view class="text floor1">
					我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
				</view>
				<view class="images_vidoe">
					<!-- <image src="../../static/images/1.jpg" mode=""></image>
					<view class="iconfont icon-bofang"></view>
					<view class="palyNum">
						<text>2次播放 3:33</text>
					</view> -->
					<!-- 分享 -->
					<view class="share flex">
						<image src="../../static/images/demo7.jpg" mode=""></image>
						<text class="text">我是分享的文字我是分享的文字我是分享的文字我是分享的文字我是分享的文字</text>
					</view>
				</view>
				<!-- 分享 -->
				<view class="floor2 flex">
					<view class="flex">
						<view class="text_color margin">深圳</view>
						<view class="text_color margin">龙岗</view>
					</view>
					<view class="flex">
						<view class="">
							<view class="iconfont icon-arrow- text_color margin">36</view>
						</view>
						<view class="">
							<view class="iconfont icon-tubiaozhizuo- text_color margin">36</view>
						</view>
						<view class="">
							<view class="iconfont icon-thumbup text_color margin">55</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '../../compument/uni-nav-bar/uni-nav-bar.vue'
	export default {
		data() {
			return {
				activeindex:0,
				text:[
					{text:'关注'},
					{text:'话题'}
					]
			}
		},
		components:{
			uniNavBar
		},
		methods: {
			tabclick(index){
				this.activeindex = index;
			}
		},
		created() {
			console.log(uniNavBar)
		}
	}
</script>

<style scoped lang="less">
	.share{
		padding: 10upx;
		background-color: #CCCCCC;
		justify-content: flex-start;
		image{
			width: 160upx!important;
			margin: auto 0;
			height: 120upx;
			margin-right: 20upx;
		}
		.text{
			width: 70%;
		}
		
	}
	.margin{
		margin: 0 5upx;
	}
	.text_color{
		color: #3333;
	}
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
	.text_title span{
		color: #333333;
	}
	.list_center{
		width: 100%;
		padding: 0 20upx;
		padding-top: 20upx;
		.list_center_left{
			width: 15%;
			image{
				width: 100upx;
				height: 100upx;
				border-radius: 50%;
			}
		}
		.list_center_right{
			width: 79%;
			padding-right: 40upx;
			.jieshao,.guanzhu{
				border-radius: 20upx;
				background-color: rgb(68, 179, 255);
				padding: 0 10upx;
				color: #FFFFFF;
				height: 40upx;
				align-items: center;
				margin-left: 10upx;
				display: flex;
				font-size: 24upx;
			}
			.guanzhu{
				background-color: rgb(244, 244, 244);
				border-radius: 5upx;
				margin-right: 20upx;
				color: #000000;
			}
			.icon-fork{
				color: #000000;
			}
			.name_item{
				display: flex;
				align-items: center;
			}
			.floor1{
				font-size: 32upx;
				padding-right: 60upx;
				margin-bottom: 26upx;
			}
			.images_vidoe{
				position: relative;
				.icon-bofang{
					position: absolute;
					top: 50%;
					left: 50%;
					transform: translate(-50%,-50%);
					font-size: 140upx;
					color: #fff;
				}
				.palyNum{
					position: absolute;
					right: 20upx;
					padding: 10upx 15upx;
					bottom: 15upx;
					font-size: 24upx;
					border-radius: 60upx;
					color: #fff;
					background-color: rgba(0,0,0,.6);
				}
				image{
					width: 100%;
					border-radius: 30upx;
				}
			}
		}
	}
</style>
