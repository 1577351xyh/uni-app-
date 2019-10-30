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
							<!-- input -->
							<view class="search-input">
								<input class="uni-input" placeholder-class="icon iconfont icon-sousuo topic-search" placeholder="搜索话题" disabled @tap="openSearch"/>
							</view>
							<!-- 轮播图 -->
							<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" :style="SwiperHeight">
								<block v-for="(item,index) in topic.swiper" :key="index">
									<swiper-item :style="SwiperHeight">
										<image :src="item.src" mode="widthFix" lazy-load :style="SwiperHeight"></image>
									</swiper-item>
								</block>
							</swiper>
							
							<!-- 热门分类 -->
							<topic-nav :nav="topic.nav"></topic-nav>
							<!-- 最近更新 -->
							<view class="topic-new">
								<view>最近更新</view>
								<block v-for="(item,index) in topic.list" :key="index">
									<topic-list :item="item" :index="index"></topic-list>
								</block>
							</view>
							
							
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
	import topicNav from '../../compument/news/topic-nav.vue'
	import topicList from '../../compument/news/topic-list.vue'
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
				},
				topic:{
					//轮播图
					swiper:[
						{src:'../../static/images/userpic/8.jpg'},
						{src:'../../static/images/userpic/8.jpg'},
						{src:'../../static/images/userpic/8.jpg'}
					],
					// 
					nav:[
						{name:'最新'},
						{name:'游戏'},
						{name:'打卡'},
						{name:'喜爱'},
						{name:'故事'},
						],
					list:[
						{
							titlepic:'../../static/images/userpic/8.jpg',
							title:'标题',
							desc:'我是秒速',
							totalnum:50,
							todaynum:20
						},
						{
							titlepic:'../../static/images/userpic/8.jpg',
							title:'标题',
							desc:'我是秒速',
							totalnum:50,
							todaynum:20
						},
						{
							titlepic:'../../static/images/userpic/8.jpg',
							title:'标题',
							desc:'我是秒速',
							totalnum:50,
							todaynum:20
						}
					]
				}
					
			}
		},
		components:{
			headers,
			list,
			loading,
			topicNav,
			topicList
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
	.search-input{
		padding: 20upx;
	}
	.search-input>input{
		background: #F4F4F4;
		border-radius:10upx;
	}
	.topic-search{
		display: flex;
		justify-content: center;
		font-size: 27upx;
	}
	
	.topic-swiper{
		padding:0 20upx 20upx 20upx;
	}
	.topic-swiper image{
		width: 100%;
		border-radius:10upx;
	}
	
	.topic-new{
		padding: 20upx;
	}
	.topic-new>view:first-child{
		padding-bottom: 5upx;
		font-size: 32upx;
	}

</style>
