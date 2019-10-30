<template>
	<view>
		<topic-iofo :item="topicInfo"></topic-iofo>
	</view>
</template>

<script>
	import topicIofo from '../../compument/topic/topic-info.vue'
	export default {
		data() {
			return {
				topicInfo:{
					titlepic:'../../static/images/userpic/8.jpg',
					desc:'我是描述',
					title:'我是标题',
					totalnum:20,
					totaynum:20
				}
			}
		},
		components:{
			topicIofo
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
