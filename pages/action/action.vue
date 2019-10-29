<template>
	<view class="action">
		<!-- 自定义导航栏 -->
		
		<headers :arr="text" :activeindex="activeindex" @changeActive="tabclick"></headers>
		<!-- 公共列表 -->
		<block v-for="(item,index) in list" :key="index">
			<list :item="item" :index="index"></list>
		</block>
		
		
	</view>
</template>

<script>
	import headers from '../../compument/nav-header/nva-header.vue'
	import list from '../../compument/action-list/action-lish.vue'
	export default {
		data() {
			return {
				activeindex:0,
				text:[
					{text:'关注'},
					{text:'话题'}],
					list:[
						{
							//文字
							userpic:'../../static/images/userpic/8.jpg',
							username:'我是名称',
							sex:0, //0男 1女
							age:25,
							isguanzhu:false,
							title:'我是标题',
							video:false,
							//封面图
							share:false,
							path:['深圳','龙岗'],
							conmentnum:30,
							goodnum:20,
							sharenum:20
						},
						{
							//视频
							userpic:'../../static/images/userpic/8.jpg',
							username:'我是名称',
							sex:0, //0男 1女
							age:25,
							isguanzhu:false,
							title:'我是标题',
							//封面图
							titlepic:'../../static/images/1.jpg',
							share:false,
							video:{
								num:30,
								longtime:'3:20'
							},
							path:['深圳','龙岗'],
							conmentnum:30,
							goodnum:20,
							sharenum:20
						},
						{
							//分享
							userpic:'../../static/images/userpic/8.jpg',
							username:'我是名称',
							sex:0, //0男 1女
							age:25,
							isguanzhu:false,
							title:'我是标题',
							//封面图
							titlepic:'../../static/images/1.jpg',
							share:{
								title:'我是分享标题',
								titlepic:'../../static/images/demo7.jpg'
							},
							video:false,
							path:['深圳','龙岗'],
							conmentnum:30,
							goodnum:20,
							sharenum:20
						}
					]
			}
		},
		components:{
			headers,
			list
		},
		methods: {
			tabclick(index){
				this.activeindex = index;
			}
		},
		
	}
</script>

<style scoped lang="less">
	

</style>
