<template>
	<view>
		<view class="classify">
			<view class="box" :class="chooseClassify==1?'box-active':''" @click="onChooseClassify(1)">推荐</view>
			<view class="box" :class="chooseClassify==2?'box-active':''" @click="onChooseClassify(2)">果蔬超市</view>
			<view class="box" :class="chooseClassify==3?'box-active':''" @click="onChooseClassify(3)">到店自取</view>
		</view>
		<view class="order">
			<view class="order-left">
				<view class="comprehensive" :class="chooseOrder==1?'order-active':''" @click="onChooseOrder(1)">
					<view class="text">综合排序</view>
					<view class="iconfont iconarrow-down"></view>
				</view>
				<view class="distance" :class="chooseOrder==2?'order-active':''" @click="onChooseOrder(2)">
					<view class="text">距离</view>
				</view>
				<view class="sales" :class="chooseOrder==3?'order-active':''" @click="onChooseOrder(3)">
					<view class="text">销量</view>
				</view>
			</view>
			<view class="order-right">
				<view class="text">筛选</view>
				<view class="iconfont iconshaixuan"></view>
			</view>
		</view>
		<view class="discount">
			<view class="dicount-item">津贴优惠</view>
			<view class="dicount-item">会员领红包</view>
			<view class="dicount-item">满减优惠</view>
			<view class="dicount-item">品质联盟</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				chooseClassify: 1,
				chooseOrder: 1
			};
		},
		methods: {
			onChooseClassify(data) {
				this.chooseClassify = data
			},
			onChooseOrder(data) {
				this.chooseOrder = data
			}
		}
	}
</script>

<style lang="scss">
	@import "../iconfont.css";

	@mixin layout {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.classify {
		width: 500rpx;
		@include layout;

		.box {
			padding: 10rpx 0rpx;
			font-size: 34rpx;
		}

		.box-active {
			color: $uni-color-primary;
			font-weight: bolder;
			border-bottom: 6rpx solid $uni-color-primary;
		}
	}

	.order {
		@include layout;
		font-size: 30rpx;
		margin: 20rpx 0px;

		.order-left {
			@include layout;
			width: 450rpx;

			.comprehensive {
				@include layout;
			}

			.order-active {
				color: $uni-color-primary;
			}
		}

		.order-right {
			@include layout;
		}

		.iconfont {
			font-size: 30rpx;
		}
	}

	.discount {
		@include layout;
		font-size: 30rpx;

		.dicount-item {
			padding: 20rpx;
			background-color: #e8e8e8;
			border-radius: 10rpx;
		}
	}
</style>
