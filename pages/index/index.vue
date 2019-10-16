<template>
	<view>
		<!-- tab -->
		<tabHeader :tabBars="tabBars" :tabIndex="tabIndex" @tabclick="tabclick"></tabHeader>
		<view class="uni-tab-bar">
			<swiper class="swiper-box" 
			:style="{height:SwiperHeight+'px'}" 
			:current="tabIndex"
			@change="onChange">
				<swiper-item v-for="(item,index) in newslist" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loading(index)">
						<block v-for="(items,index) in item.list" :key="index">
							<list :list="items"></list>
						</block>
						<loading :loading="item.loading"></loading>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
		
	</view>
</template>

<script>
	import list from '../../compument/index-list/index-list.vue';
	import tabHeader from '../../compument/swiper-tab/swiper-tab.vue'
	import loading from'../../compument/loading-more/loading-more.vue'
	export default {
		data() {
			return {
				SwiperHeight:500,
				tabBars:[
					{name:'关注',id:0},
				    {name:'推荐',id:1},
				    {name:'体育',id:2},
					{name:'热点',id:3},
					{name:'财经',id:4},
					{name:'娱乐',id:5},
				],
				newslist:[
					{	
						loading:'下拉加载更多',
					    list:[{
					    	userName:'我是名字',
					    	userImages:'../../static/images/demo6.jpg',
					    	//关注状态
					    	focus:false,
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
					    	focus:true,
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
					},
					{
						loading:'下拉加载更多',
						list:[{
							userName:'我是名字',
							userImages:'../../static/images/demo6.jpg',
							//关注状态
							focus:false,
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
						}]
					}
				],
				tabIndex:0
			}
		},
		methods:{
			tabclick(index){
				this.tabIndex  = index;
			},
			onChange(e){
				this.tabIndex = e.detail.current;
			},
			loading(index){
				if(this.newslist[index].loading!=="下拉加载更多"){return};
				this.newslist[index].loading = "加载中...";
				setTimeout(()=>{
					let obj = {
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
					}
					this.newslist[index].list.push(obj);
					this.newslist[index].loading = "下拉加载更多"
				},500)
				
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success:(res)=> {
					this.SwiperHeight = res.windowHeight;
				}
			})
		},
		components:{
			list,
			tabHeader,
			loading
		}
	}
</script>

<style lang="less">
	

</style>
