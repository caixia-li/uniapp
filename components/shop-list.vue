<template>
	<view>
		<block v-for="(item,index) in shopList">
			<view class="list-item" :key="index">
				<image :src="item.url" class="img"></image>
				<view class="message">
					<view class="name">{{item.name}}</view>
					<view class="rate">
						<view class="rate-left">
							<view class="iconfont iconstart-copy"></view>
							<view class="rating">{{item.rating}}</view>
						</view>
						<view class="count">{{item.business_info.recent_order_num_display}}</view>
					</view>
					<view class="price">
						<view class="fee">{{item.piecewise_agent_fee.description}}</view>
						<view class="nofee">{{item.piecewise_agent_fee.no_subsidy_fee}}</view>
					</view>
					<view class="comment">{{item.promotion_info}}</view>
					<view class="discount">
						<block v-for="(temp,index) in item.business_info.lemon_support_tags" :key="index">
							<view class="text" v-if="index<5">{{temp.text}}</view>
						</block>
					</view>
				</view>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		props: ['shopList']
	}
</script>

<style lang="scss">
	@import '../iconfont.css';

	@mixin layout {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.list-item {
		height: 250rpx;
		font-size: 28rpx;
		@include layout;

		.img {
			height: 200rpx !important;
			width: 200rpx !important;
			border-radius: 10rpx;
			border: 1rpx solid #C8C7CC;
		}

		.message {
			box-sizing: border-box;
			width: 500rpx;
			height: 250rpx;
			padding: 25rpx 8rpx;
			margin: 6rpx 0;
			border-bottom: 1rpx solid #C8C7CC;

			.name {
				font-size: 32rpx;
				font-weight: bolder;
			}

			.rate {
				@include layout;
				margin: 6rpx 0;
				width: 50%;

				.rate-left {
					@include layout;
					color: $uni-color-error;
				}

				.count {
					font-size: 24rpx;
					color: #999999;
				}
			}

			.price {
				display: flex;
				align-items: center;
				width: 80%;
				margin: 6rpx 0;
				color: #999999;
				font-size: 24rpx;

				.nofee {
					text-decoration: line-through;
					margin-left: 10rpx;
				}
			}

			.comment {
				overflow: hidden;
				white-space: nowrap;
				text-overflow: ellipsis;
				font-size: 22rpx;
				padding: 0 6rpx;
				margin: 6rpx 0rpx;
				background-color: rgba($color: #f0d070, $alpha: 0.3);
				color: #F0AD4E;
			}

			.discount {
				@include layout;
				font-size: 20rpx;
				padding: 0 6rpx;
				margin: 10rpx 0rpx;
				overflow: hidden;
				white-space: nowrap;

				.text {
					padding: 4rpx 8rpx;
					color: $uni-color-error;
					border: 1rpx solid $uni-color-error;
				}
			}
		}
	}
</style>
