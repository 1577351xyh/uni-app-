<template>
	<view>
		<!-- tab -->
		<view>
			<scroll-view scroll-x show-scrollbar="false" class="uni-swiper-tab">
				<block v-for="(tab,index) in tabBars" :key="index">
					<view class="swiper-tab-list" :class="{'active':tabIndex==index}" @click="tabclick(index)">
						{{tab.name}}
						<view class="swiper-tab-line">
							
						</view>
					</view>
				</block>
				
			</scroll-view>
		</view>
		<!-- item内容 -->
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
				tabBars:[
					{name:'关注',id:0},
				    {name:'推荐',id:1},
				    {name:'体育',id:2},
					{name:'热点',id:3},
					{name:'财经',id:4},
					{name:'娱乐',id:5},
				],
				tabIndex:0
			}
		},
		methods:{
			tabclick(index){
				this.tabIndex = index;
			}
		},
		components:{
			list
		}
	}
</script>

<style lang="less">
.active{
	color:#FFB400;
	
}
.active .swiper-tab-line{
	border-bottom: 6upx solid #FFB400;
	width: 60upx;
	margin: 0 auto;
}
</style>
