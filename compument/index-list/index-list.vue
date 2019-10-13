<template>
		<view class="item">
			<view class="item_header">
				<view class="item_header_left">
					<image src="../../static/images/demo6.jpg" mode=""></image>
					<text>我是名称</text>
				</view>
				<view class="item_header_right">
					<view class="icons">
						<view class="iconfont icon-jia"></view>
						<text>关注</text>
					</view>
					<view class="iconfont icon-fork"></view>
				</view>
			</view>
			<view class="item_body">
				<text class="center">我是很长的文字文字</text>
				<view class="images_vidoe">
					<image src="../../static/images/banner1.jpg" mode=""></image>
					<view class="iconfont icon-bofang"></view>
					<view class="palyNum">
							<text>20w 次播放 2:47</text>
					</view>
				</view>
				<view class="models">
					<view class="models_left">
						<view class="flex_floor">
							<view class="iconfont icon-xiaolian padding"></view>
							<text class="padding">987</text>
						</view>
						<view class="flex_floor">
							<view class="iconfont icon-shibaibiaoqing padding"></view>
							<text class="padding">17</text>
						</view>
					</view>
					<view class="models_right">
						<view class="flex_floor">
							<view class="iconfont icon-tubiaozhizuo- padding"></view>
							<text class="padding">987</text>
						</view>
						<view class="flex_floor">
							<view class="iconfont icon-arrow- padding"></view>
							<text class="padding">17</text>
						</view>
					</view>
				</view>
			</view>
		</view>
</template>

<script>
	export default {
		data() {
			return {
				list:{
					userName:'',
					userImages:'',
					//关注状态
					focus:false,
					centent:'',
					cententType:'img', //img或者是video
					titlepic:'',//图片
					playnum:"",//播放次数
					long:'2:47',
					infonum:{
						index:0,
						//顶
						dingnum:11,
						//踩
						cainum:11
					},
					//分享次数
					shareNum:'',
					//评论次数
					comment:''
				}
			}
		},
		
	}
</script>

<style lang="less">
.item{
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	border-bottom: 2upx solid rgb(213, 213, 213);
	padding: 20upx;
	padding-bottom: 0;
	.item_header{
		height: 80upx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		.item_header_left{
			display: flex;
			align-items: center;
			image{
				width: 60upx;
				height: 60upx;
				border-radius: 50%;
				vertical-align: middle;
				margin-right: 10upx;
			}
			text{
				font-size: 16upx;
				color: #808080;
			}
		}
		.item_header_right{
			display: flex;
			align-content: center;
			.icons{
				display: flex;
				align-content: center;
				vertical-align: middle;
				margin-right: 15upx;
				padding:0 10upx;
				font-size: 24upx;
				background-color: rgb(244, 244, 244);
				text{
					margin: auto 0;
				}
			}
			.icon-fork{
				font-size: 24upx;
				margin: auto 0;
				color: rgb(213, 213, 213);
			}
		}
	}
	.item_body{
		margin-top: 25upx;
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
			.center{
				font-size: 36upx;
				margin-bottom: 30upx;
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
					border-radius: 30upx;
				}
			}
			.models{
				height: 120upx;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.models_right,.models_left{
					display: flex;
				}
				.flex_floor{
						display: flex;
				}
			}
	}
}
.padding{
	padding:0 10upx;
	color:rgb(213, 213, 213);
}
</style>
