<template>
	<view>
		<view class="vip-box">
			<view class="vip-left">
				<view class="iconfont iconhuangguan"></view>
				<view class="discount">加入会员每月领取20元红包</view>
			</view>
			<view class="vip-right">
				<view class="">立即开通</view>
				<view class="iconfont iconleft"></view>
			</view>
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
	@import "../iconfont.css";

	.vip-box {
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 26rpx;
		padding: 10rpx;
		background-image: linear-gradient(#ffeeb0, #ffd07d);
		border-radius: 20rpx;
		color: #a56e00;

		.vip-left {
			@extend .vip-box;

			.iconhuangguan {
				color: #d89000;
				font-size: 50rpx;
			}
		}

		.vip-right {
			@extend .vip-box;

			.iconleft {
				font-size: 30rpx;
				vertical-align: bottom;
			}
		}
	}
</style>
