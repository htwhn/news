<template>
<view>
		<view class="title">
			{{newsDetail.title}}
		</view>
		<rich-text :nodes="Strings">
			
		</rich-text>
		
	
</view>
</template>

<script>
export default {
	data() {
		return {
			newsDetail:'',
			Strings:'',
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
				this.newsDetail = res.data;
				this.Strings = res.data.content;
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
.title{
	font-weight: bold;
}
rich-text{
	margin: 3upx;
}
</style>
