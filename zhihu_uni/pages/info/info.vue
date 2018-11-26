<template>
	<view class="content">
		<view class="title">{{title}}</view>
		<rich-text class="richText" :nodes="strings"></rich-text>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				title:'',
				strings:''
			}
		},
		onLoad:function(e){
			uni.request({
				url: 'http://news-at.zhihu.com/api/4/news/' + e.id,
				method: 'GET',
				data: {},
				success: res => {
					console.log(res.data.body);
					this.title = res.data.title;
					this.strings = res.data.body.replace("type=“text/javascript”",'type="text/javascript"');
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>
.content{padding: 10px %2; width: 96%; flex-wrap: wrap;}
.title{line-height: 2em;font-weight: 700;font-size: 20px;}
</style>
