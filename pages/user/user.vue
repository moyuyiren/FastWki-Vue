<template>
	<view class="user">
		<view class="top">
			<!-- 登录模块 -->
			<view class="login" v-if="Userinfo.token==''">
				<Login></Login>
			</view>
			<!-- 用户信息显示 -->
			<view class="userinfo" v-if="!Userinfo.token==''">
				<!-- <image :src="Userinfo.userimage" mode=""></image> -->
				<image src="/static/icon/暂无数据.png" mode=""></image>
			</view>
			<view class="text">
				<text>{{Userinfo.username}}</text>
			</view>
		</view>
		<!-- 用户历史查询 -->
		<view class="content">
			<view class="item" v-for="item in listArr">
				<newsbox :item="item"  @click.native="clickDetail(item)"></newsbox>				
			</view>			
		</view>
		<view class="noContent" v-if="!listArr.length">
			<div class="text">暂无浏览记录</div>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// Userinfo:{
				// 	username:"摸鱼呓人不睡觉",
				// 	userimage:"https://lmg.jj20.com/up/allimg/1114/040221103339/210402103339-8-1200.jpg",
				// 	token:"11"
				// },
				Userinfo:{
					username:"",
					userimage:"",
					token:""
				},
				listArr:[]
			};
		},
		onLoad() {
			//this.getHistory();
		},
		methods:{
			getHistory(){
				let historyArr=uni.getStorageSync("historyArr") || [];
				this.listArr=historyArr;
			},
			
			
		}
	}
</script>

<style lang="scss" scoped>
.user{
	.top{
		background: #f8f8f8;
		padding:50rpx 0;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		.userinfo{
			image{
				width: 120rpx;
				height: 120rpx;
			}
		}
		.text{
			font-size: 32rpx;
			color:#666;
			padding-top:0rpx;
		}
	}
	.content{
		padding:30rpx;
		padding-top:30rpx;
		.item{
			padding:20rpx 0;
			border-bottom:1rpx #e2e2e2 dotted;
		}
	}
	.noContent{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		image{
			width: 500rpx;
		}
		.text{
			font-size: 30rpx;
			color:#888;
		}
	}
}
	

</style>
