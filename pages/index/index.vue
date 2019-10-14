<template>
	<view>
		<block v-for="(item,index) in listarr" :key="index">
			<list :list="item"></list>
		</block>
	</view>
</template>

<script>
	import list from '../../compument/index-list/index-list.vue'
	export default {
		data() {
			return {
				listarr:[{
					userName:'我是名字',
					userImages:'../../static/images/demo6.jpg',
					//关注状态
					focus:'false',
					centent:'我是很长的文字文字',
					cententType:'img', //img或者是video
					titlepic:'../../static/images/banner1.jpg',//图片
					playnum:"20w",//播放次数
					long:'2:47',
					infonum:{
						index:0,
						//顶
						dingnum:11,
						//踩
						cainum:11
					},
					//分享次数
					shareNum:'10',
					//评论次数
					comment:'100'
				},
				{
					userName:'我是名字',
					userImages:'../../static/images/demo6.jpg',
					//关注状态
					focus:'true',
					centent:'我是很长的文字文字',
					cententType:'video', //img或者是video
					titlepic:'../../static/images/banner1.jpg',//图片
					playnum:"20w",//播放次数
					long:'2:47',
					infonum:{
						index:0,
						//顶
						dingnum:11,
						//踩
						cainum:11
					},
					//分享次数
					shareNum:'10',
					//评论次数
					comment:'100'
				}],
			}
		},
		components:{
			list
		}
	}
</script>

<style>

</style>
