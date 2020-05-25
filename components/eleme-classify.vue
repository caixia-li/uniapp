<template>
	<view>
		<swiper :indicator-dots="true" :interval="3000" :duration="1000" class="classify-swiper">
			<swiper-item>
				<view class="classify-box">
					<block v-for="(item,index) in classifyList[0]" :key="item.activity_id">
						<view class="classify" v-if="index<15">
							<image :src="item.url" mode="widthFix"></image>
							<view class="name">{{item.name}}</view>
						</view>
					</block>
				</view>
			</swiper-item>
			<swiper-item>
				<view class="classify-box">
					<block v-for="(item,index) in classifyList[0]" :key="item.activity_id">
						<view class="classify" v-if="index>=16">
							<image :src="item.url" mode="widthFix"></image>
							<view class="name">{{item.name}}</view>
						</view>
					</block>
					<block v-for="(item,index) in classifyList[1]">
						<view class="classify" :key="item.activity_id">
							<image :src="item.url" mode="widthFix"></image>
							<view class="name">{{item.name}}</view>
						</view>
					</block>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		props: ['classifyList']
	}
</script>

<style lang="scss">
	.classify-swiper {
		height: 620rpx !important;

		.classify-box {
			display: flex;
			justify-content: flex-start;
			flex-wrap: wrap;

			.classify {
				width: 130rpx;
				height: 190rpx;
				margin: 0rpx 6rpx;

				image {
					width: 130rpx;
				}

				.name {
					font-size: 30rpx;
					text-align: center;
				}
			}
		}
	}
</style>
