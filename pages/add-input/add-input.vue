<template>
	<view>
		<view class="example-body">
			<uni-nav-bar :statusBar="true" left-icon="arrowleft" rightText="发布" @click-left="back" @click-right="submit">
			<view class="uni-flex u-text" @click="change">
				{{text}}<view class="iconfont icon-down" style="margin-left: 10upx;vertical-align: middle;"></view>
			</view>
			</uni-nav-bar>
		</view>
		<!-- 文本域 -->
		<view class="uni-textarea">
			<textarea v-model="textarea" placeholder="说点什么把" />
		</view>
		<!-- 上传多图 -->
		<uploadImages @upload="uploads"></uploadImages>
		<!-- 弹出公告 -->
		<view class="bgc" v-show="bgc">
			<view class="center">
				<text class="text">我是弹出层</text>
				<button type="primary" @click="bgc=false">关闭</button>
			</view>
		</view>
	</view>
</template>

<script>
	
	import uniNavBar from '../../compument/uni-nav-bar/uni-nav-bar.vue'
	import uploadImages from '../../compument/upload-images/lupload-images.vue'
	export default {
		data() {
			return {
				bgc:true,
				text:'所有人可见',
				textarea:'',
				listimages:[],
				isget:false,
			}
		},
		components:{
			uniNavBar,
			uploadImages
		},
		onBackPress() {
			if(this.listimages.length==0 && !this.textarea){
				return;
			}
			if(!this.isget){
				console.log(1)
				this.modal();
				return true;
			}
		},
		methods: {
			modal(){
				console.log(222)
				uni.showModal({
					content:'是否要保存为草稿',
					cancelText:'不保存',
					confirmText:'保存',
					success: (res) => {
						if(res.confirm){
							//存入本地缓存
							console.log('保存')
							this.isget = true;
							uni.navigateBack({
								delta:1
							})
						}else{
							console.log('不保存')
							this.isget = true;
							uni.navigateBack({
								delta:1
							})
						}
						
					}
				})
			},
			uploads(arr){
				this.listimages = arr;
			},
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			change(){
				uni.showActionSheet({
					itemList:['所有人可见','仅自己可见'],
					success:(res)=>{
						console.log(res);
						if(res.tapIndex==0){
							this.text="所有人可见";
						}else{
							this.text = "仅自己可见";
						}
					}
				})
			}
			
		}
	}
</script>

<style scoped lang="less">
	.uni-navbar__content{
		box-shadow: none;
	}
	.u-text{
		display: flex;
		margin: 0 auto;
	}
	.bgc{
		width: 100%;
		height: 100vh;
		background-color: rgba(0,0,0,.7);
		position: absolute;
		z-index: 10;
		top: 0;
		left: 0;
		.center{
			position: absolute;
			width: 70%;
			height: 50vh;
			top: 50%;
			left: 50%;
			transform: translate(-50%,-50%);
			padding: 20upx;
			background-color: #FFFFFF;
			border-radius: 20upx;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			button{
				width: 90%;
			}
		}
	}
		
</style>
