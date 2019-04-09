<template>
	<view class="content">
		<view class="title">{{dataInfo.title}}</view>
		<view class="art-content">
			<rich-text class="htmlText" :nodes="dataInfo.content"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				dataInfo:null,
			};
		},
		onLoad:function(e){
			console.log(e)
			uni.showLoading({
				title: '加载中...',
				mask: true
			});
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+e.id,
				method: 'GET',
				data: {},
				success: res => {
					this.dataInfo=res.data;
				},
				fail: () => {},
				complete: () => {
					uni.hideLoading();
				}
			});
		}
	}
</script>

<style>
	.title{
		font-size: 40upx;
		line-height: 1.2;
	}
</style>
