<template>
	<view class="SecondMenu">
		<view class="box">
			<text class="title">988你好</text>
		</view>
	</view>
</template>

<script>
	export default {
		name:"SecondMenu",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
.SecondMenu{
	width: 750rpx;
	.box{
		display: flex;
		width: 100%;
		flex: 1;
		background-color: #3399FF;
		.title{
			background-color: #3366CC;
			width: 70%;
			font-size: 35rpx;
			color: white;
		}
	}
}

</style>