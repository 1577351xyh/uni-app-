<script>
	
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import './common/animation.css';
	@import './common/font.css';
	 @import './common/uni.css';
	 @import './common/common.css';
	 .flex{
		 display: flex;
		 justify-content: space-between;
	 }
</style>
