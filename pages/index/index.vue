<template>
	<view class="home">
		<!-- 一级菜单 -->
		<view class="navList">
			<view class="row" v-for="(item,index) in listNav" :key="index">
				{{item}}
			</view>
			<view class="nodata" v-if="!listArr.length">
				<image src="/static/icon/暂无数据.png"></image>
				<view class="text">暂无数据</view>	
			</view>
		</view>
		<!-- 二级菜单 -->
		<view class="content">
			<view class="row" v-for="item in listArr">
				<SecondMenu></SecondMenu>
			</view>
			<view class="nodata" v-if="!listArr.length">
				<image src="/static/icon/暂无数据.png"></image>
				<view class="text">暂无数据</view>	
			</view>
		</view>
		<!-- 加载数据 -->
		<view class="loadStyle" v-if="listArr.length">
			<view class="text" v-if="loading==1">数据加载中...</view>
			<view class="text" v-if="loading==2">没有更多了~~</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listNav:[],
				listArr:[1,2],
				loading:0
				
			
			}
		},
		onLoad() { 
			
		},
		methods: {
			getData(){
				wx.request({
					url:"",
					success:res=>{
						console.log(res)
						let obj =JSON.stringify(res.data)
						this.listNav=obj
					}
				})
			}
			
		
		}
	}
</script>

<style lang="scss" scoped>
.home{
	.navList{
		.row{
			padding: 15rpx 0;
			border-bottom: 1px dashed #efefef;
		}
		.nodata{
			padding-top: 50rpx;
			display: flex;
			justify-content: center;
			flex-direction: column;
			align-items: center;
			image{
				width: 400rpx;
				height: 400rpx;
			}
			.text{
				color: #999;
				font-size: 20rpx;
			}
	    }
	}
	.content{
		padding: 30rpx;
		padding-top: 130rpx;
		.row{
			padding: 15rpx 0;
			border-bottom: 2px dashed #003399;
		}
		.nodata{
			padding-top: 50rpx;
			display: flex;
			justify-content: center;
			flex-direction: column;
			align-items: center;
			image{
				width: 400rpx;
				height: 400rpx;
			}
			.text{
				color: #999;
				font-size: 20rpx;
			}
		}
	}
	.loadStyle{
		.text{
			font-size: 28rpx;
			color:#999;
			text-align: center;
			padding:20rpx 0;
		}
	}
}
</style>
