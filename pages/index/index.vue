<template>
	<view class="content">
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in news" :key="index" @tap="showDetail" :data-newsid="item.post_id">
				<view class="uni-media-list">
					<image class="uni-media-list-logo" :src="item.author_avatar"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top">{{item.title}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">{{item.updated_at}}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				news:[]
			};
		},
		onLoad:function(){
			uni.showLoading({
				title: '正在加载...',
				mask: false
			})
			uni.request({
				method:'GET',
				url:'https://unidemo.dcloud.net.cn/api/news',
				data:{},
				success: res =>{
					console.log(res);
					this.news = res.data;
					uni.hideLoading();
				},
				fail: ()=>{},
				complete: () => {
					
				}
				
			});
		},
		methods: {
			showDetail(e) { 
				console.log(e);
				var newsid = e.currentTarget.dataset.newsid;
				uni.navigateTo({
					url: '../info/info?newsid='+newsid,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
	}
</script>

<style>
	.uni-media-list-body{
		height: auto;
	}
</style>
