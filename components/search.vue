<template>
	<view>
		<view class="search">
			<input type="text" value="" placeholder-class="iconfont iconsousuo" placeholder="请输入内容 " placeholder-style="text-align:center;" class="ipt"/>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	.search{
		width: 100%;
		height: 80rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #e2e2e2;
		border-radius: 80rpx;
		.ipt{
			padding: 0 30rpx;
			width: 100%;
		    text-align: center;
		}
	}
	
</style>
