<template>
	<view>
		<view class="example-body">
			<uni-nav-bar :statusBar="true" left-icon="arrowleft" rightText="发布" @click-left="back" @click-right="submit">
			<view class="uni-flex u-text" @click="change">
				{{text}}<view class=""></view>
			</view>
			</uni-nav-bar>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '../../compument/uni-nav-bar/uni-nav-bar.vue'
	export default {
		data() {
			return {
				text:'所有人可见'
			}
		},
		components:{
			uniNavBar
		},
		methods: {
			back(){
				uni.navigateBack({
					delta:1
				})
			},
			submit(){
				console.log('发布')
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
.u-text{
	display: flex;
	margin: 0 auto;
}
</style>
