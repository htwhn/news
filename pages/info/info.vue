<template>
<view class="content">
		<view class="title" v-text="newsDetail.title"> <!-- 不要使用差值表达式，网络原因 -->
		</view>
		<view class="art-content">
			<rich-text :nodes="Strings" >
				
			</rich-text>
		</view>
		
		
	
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
		uni.showLoading({
			title: '正在加载...',
			mask: false
		});
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
				uni.hideLoading();
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
	font-size: 40upx;
}
.content{
	padding: 10upx;
}

</style>
