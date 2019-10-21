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
		
	</view>
</template>

<script>
	
	import uniNavBar from '../../compument/uni-nav-bar/uni-nav-bar.vue'
	import uploadImages from '../../compument/upload-images/lupload-images.vue'
	export default {
		data() {
			return {
				text:'所有人可见',
				textarea:'',
				listimages:[]
			}
		},
		components:{
			uniNavBar,
			uploadImages
		},
		methods: {
			uploads(arr){
				this.listimages = arr;
				console.log(this.listimages)
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

<style scoped>
	.uni-navbar__content{
		box-shadow: none;
	}
	.u-text{
		display: flex;
		margin: 0 auto;
	}

		
</style>
