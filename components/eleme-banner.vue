<template>
	<view>
		<swiper :autoplay="true" :interval="3000" :duration="1000" class="banner">
			<block v-for="item in bannerList" :key="item.id">
				<swiper-item>
					<image :src="item.url" mode="widthFix"></image>
				</swiper-item>
			</block>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		props: ['bannerList']
	}
</script>

<style>
	.banner {
		width: 100%;
		height: 176rpx !important;
	}

	image {
		width: 100%;
		height: 176rpx;
	}
</style>
