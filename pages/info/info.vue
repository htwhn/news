<template>
	<view>
		<view class="uni-list">
			
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// newsDetail:{}
			}
		},
		onLoad:function(e){
			var newsid = e.newsid;
			console.log(newsid);
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+newsid,
				method: 'GET',
				data: {},
				success: res => {
					console.log(res);
					// this.newsDetail = res;
				},
				fail: () => {},
				complete: () => {}
			});
			
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
