<template>
		<view class="item animated bounceInUp">
			<view class="item_header">
				<view class="item_header_left">
					<image :src="list.userImages" mode=""></image>
					<text>{{list.userName}}</text>
				</view>
				<view class="item_header_right" v-if="list.focus==='false'" @click="onFocus">
					<view class="icons" v-if="list.focus==true">
						<view class="iconfont icon-jia"></view>
						<text>关注</text>
					</view>
					<view class="iconfont icon-fork"></view>
				</view>
			</view>
			<view class="item_body">
				<text class="center">{{list.centent}}</text>
				<view class="images_vidoe">
					<image :src="list.titlepic" mode=""></image>
					<view class="iconfont icon-bofang" v-if="list.cententType==='video'"></view>
					<view class="palyNum" v-if="list.cententType==='video'">
						<text>{{list.playnum}} 次播放 {{list.long}}</text>
					</view>
				</view>
				<view class="models">
					<view class="models_left">
						<view class="flex_floor" :class="{'active':list.infonum.index===1}" @click="likes('zan')">
							<view class="iconfont icon-xiaolian padding"></view>
							<text class="padding ding">{{list.infonum.dingnum}}</text>
						</view>
						<view class="flex_floor" :class="{'active':list.infonum.index===2}" @click="likes('cai')">
							<view class="iconfont icon-shibaibiaoqing padding"></view>
							<text class="padding cai">{{list.infonum.cainum}}</text>
						</view>
					</view>
					<view class="models_right">
						<view class="flex_floor">
							<view class="iconfont icon-tubiaozhizuo- padding"></view>
							<text class="padding">{{list.comment}}</text>
						</view>
						<view class="flex_floor">
							<view class="iconfont icon-arrow- padding"></view>
							<text class="padding">{{list.shareNum}}</text>
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
				
			}
		},
		
		props:{
			list:{
				type:Object
			}
		},
		methods:{
			onFocus(){
				this.list.focus = true;
				uni.showToast({
					title:"关注成功"
				})
			},
			likes(type){
				switch(type){
					//1是操作过,2是没操作过
					case "zan":
						if(this.list.infonum.index == 1 ){
							return;
						}
						this.list.infonum.dingnum++;
						if(this.list.infonum.index==2){
							this.list.infonum.cainum--;
						}
						this.list.infonum.index = 1;
						break;
					
					case "cai":
						if(this.list.infonum.index ==2){
							return;
						}
						this.list.infonum.cainum++;
						if(this.list.infonum.index==1){
							this.list.infonum.dingnum--;
						}
						this.list.infonum.index = 2;
						break;
					
				}
			}
		}
	}
</script>

<style lang="less" scoped>
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
.active .ding,.active .cai{
	color: #FFB400;
}
.active .icon-xiaolian,.active .icon-shibaibiaoqing{
	color: #FFB400;
}
img{
	width: 100%;
}
</style>
