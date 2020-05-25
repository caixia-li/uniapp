<template>
	<view>
		<view class="head-box">
			<view class="head-left">
				<view class="iconfont iconlocation"></view>
				<view class="local">
					<text>{{location.address}}+{{location.address_detail}}</text>
				</view>
				<view class="iconfont iconarrow-down"></view>
			</view>
			<view class="head-right">
				<view class="iconfont iconsaoma"></view>
				<view class="iconfont iconxiaoxi"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		props: {
			location: {
				type: Object
			}
		}
	}
</script>

<style lang="scss">
	@import '../iconfont.css';

	.head-box {
		width: 100%;
		padding: 20rpx 0;
		display: flex;
		justify-content: space-between;

		.head-left {
			display: flex;

			.local {
				font-size: 30rpx;
				padding: 0 10rpx;
			}

			.iconlocation {
				color: #007AFF;
			}

			.iconarrow-down {
				font-size: 30rpx;
				line-height: 40rpx;
			}
		}

		.head-right {
			display: flex;

			.iconsaoma {
				font-size: 50rpx;
			}

			.iconxiaoxi {
				font-size: 38rpx;
				margin-top: 8rpx;
			}
		}

	}
</style>
