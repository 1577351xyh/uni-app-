<template>
	<view class="action">
		<!-- 自定义导航栏 -->
		
		<headers :arr="text" :activeindex="activeindex" @changeActive="tabclick"></headers>
		<!-- 公共列表 -->
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" 
			:style="{height:SwiperHeight+'px'}" 
			:current="activeindex"
			@change="onChange">
				<swiper-item>
						<scroll-view scroll-y class="list" @scrolltolower="loadings">
							<block v-for="(item,index) in objlist.list" :key="index">
								<list :item="item" :index="index"></list>
							</block>
							<loading :loading="objlist.loadtext"></loading>
						</scroll-view>
				</swiper-item>
				<swiper-item>
						<scroll-view scroll-y class="list">
							话题
						</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
	</view>
</template>

<script>
	import headers from '../../compument/nav-header/nva-header.vue'
	import list from '../../compument/action-list/action-lish.vue'
	import loading from '../../compument/loading-more/loading-more.vue'
	export default {
		data() {
			return {
				activeindex:0,
				tabIndex:0,
				SwiperHeight:'',
				text:[
					{text:'关注'},
					{text:'话题'}],
				objlist:{
					loadtext:'下拉加载更多',
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
					
			}
		},
		components:{
			headers,
			list,
			loading
		},
		onLoad() {
			uni.getSystemInfo({
				success:(res)=> {
					this.SwiperHeight = res.windowHeight;
				}
			})
		},
		methods: {
			tabclick(index){
				this.activeindex = index;
			},
			onChange(e){
				this.activeindex = e.detail.current;
			},
			loadings(){
				console.log(1)
				if(this.objlist.loadtext!=="下拉加载更多"){return};
				this.objlist.loadtext = "加载中...";
				setTimeout(()=>{
					let obj = {
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
					}
					// console.log(this.objlist.list)
					this.objlist.list.push(obj);
					this.objlist.loadtext = "下拉加载更多"
				},500)
		
			}
		},
		
	}
</script>

<style scoped lang="less">
	

</style>
