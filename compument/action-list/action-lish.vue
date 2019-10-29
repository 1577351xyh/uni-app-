<template>
	<view class="list_center flex">
		<view class="list_center_left">
			<image :src="item.userpic" mode=""></image>
		</view>
		<view class="list_center_right">
			<view class="name flex">
				<view class="flex name_item">
					<view class="text_color">{{item.username}}</view>
					<view class="jieshao">
						<view class="iconfont icon-xingbienan1" style="font-size: 24upx;">{{item.age}}岁</view>
					</view>
				</view>
				<view class="flex center name_item">
					<view class="flex guanzhu" v-show="!isguanzhu"
						@click="toguanzhu">
						<view class="iconfont icon-jia" 
						style="font-size: 24upx;">关注</view>
					</view>
					<view class="iconfont icon-fork"></view>
				</view>
			</view>
			<view class="text floor1">
				{{item.title}}
			</view>
			
			<view class="images_vidoe">
				<image v-if="item.titlepic && !item.share" :src="item.titlepic" mode=""></image>
				
				<template v-if="item.video">
					<view class="iconfont icon-bofang"></view>
					<view class="palyNum">
						<text>2次播放 3:33</text>
					</view>
				</template>
				
				<template v-if="item.share">
				<!-- 分享 -->
				<view class="share flex">
					<image src="../../static/images/demo7.jpg" mode=""></image>
					<text class="text">我是分享的文字我是分享的文字我是分享的文字我是分享的文字我是分享的文字</text>
				</view>
				</template>
			</view>
			<!-- 分享列表 -->
			<template v-if="item.share">
			<view class="floor2 flex">
				<view class="flex">
					<block v-for="(items,index) in item.share" :key="index">
						<view class="text_color margin">{{items.title}}</view>
					</block>
				</view>
			</view>
			</template>
				<view class="flex">
					<view class="">
						<view class="iconfont icon-arrow- text_color margin">{{item.conmentnum}}</view>
					</view>
					<view class="">
						<view class="iconfont icon-tubiaozhizuo- text_color margin">{{item.goodnum}}</view>
					</view>
					<view class="">
						<view class="iconfont icon-thumbup text_color margin">{{item.sharenum}}</view>
					</view>
				</view>
			
		
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number
		},
		data(){
			return{
				isguanzhu:false
			}
		},
		methods:{
			toguanzhu(){
				this.isguanzhu=true;
				uni.showModal({
					title:"关注成功"
				})
			}
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
