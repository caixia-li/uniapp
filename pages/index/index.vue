<template>
	<view class="content">
		<eleme-head :location="location"></eleme-head>
		<search></search>
		<view class="banner">
			<eleme-banner :bannerList="bannerList "></eleme-banner>
		</view>
		<view class="classify" v-if="flag">
			<classify-list :classifyList="classifyList"></classify-list>
		</view>
		<view class="vip">
			<vip></vip>
		</view>
		<view class="shopping">
			<shop-menu></shop-menu>
			<shopList :shopList="shopList"></shopList>
		</view>
	</view>
</template>

<script>
	import elemeHead from "../../components/head.vue"
	import search from '../../components/search.vue'
	import elemeBanner from '../../components/eleme-banner.vue'
	import classifyList from '../../components/eleme-classify.vue'
	import vip from '../../components/vip.vue'
	import shopMenu from '../../components/shop-menu.vue'
	import shopList from '../../components/shop-list.vue'
	export default {
		components: {
			elemeHead,
			search,
			elemeBanner,
			classifyList,
			vip,
			shopMenu,
			shopList
		},
		data() {
			return {
				location: {},
				bannerList: [],
				classifyList: [],
				flag: false,
				shopList: []
			}
		},
		onLoad() {
			this.init();
		},
		onShow() {
			this.init()
		},
		methods: {
			request(url) {
				return new Promise((reslove, reject) => {
					uni.request({
						url: url,
						method: "GET",
						data: {},
						success: (res) => {
							reslove(res.data)
						}
					})
				})
			},
			imgEdit(list) {
				let newList = []
				list.forEach(item => {
					let oldValue = item.image_hash;
					const first = "https://fuss10.elemecdn.com/";
					const second = oldValue.slice(0, 1);
					const third = oldValue.slice(1, 3);
					const forth = oldValue.slice(3);
					if (oldValue.match(/png/)) {
						const fifth =
							".png?imageMogr/thumbnail/!90x90r/gravity/Center/crop/90x90/";
						item.url = `${first}${second}/${third}/${forth}${fifth}`
					} else {
						const fifth =
							".jpeg?imageMogr/thumbnail/!90x90r/gravity/Center/crop/90x90/";
						item.url = `${first}${second}/${third}/${forth}${fifth}`
					}
					newList.push({
						...item
					})
				})
				return newList;
			},
			merchant(list) {
				let newList = []
				list.forEach(item => {
					let oldValue = item.restaurant.image_path;
					const first = "https://fuss10.elemecdn.com/";
					const second = oldValue.slice(0, 1);
					const third = oldValue.slice(1, 3);
					const forth = oldValue.slice(3);
					if (oldValue.match(/png/)) {
						const fifth =
							".png?imageMogr/thumbnail/!90x90r/gravity/Center/crop/90x90/";
						item.restaurant.url = `${first}${second}/${third}/${forth}${fifth}`
					} else {
						const fifth =
							".jpeg?imageMogr/thumbnail/!90x90r/gravity/Center/crop/90x90/";
						item.restaurant.url = `${first}${second}/${third}/${forth}${fifth}`
					}
					newList.push({
						url: item.restaurant.url,
						name: item.restaurant.name,
						business_info: JSON.parse(item.restaurant.business_info),
						rating: item.restaurant.rating,
						promotion_info: item.restaurant.promotion_info,
						authentic_id: item.restaurant.authentic_id,
						piecewise_agent_fee: item.restaurant.piecewise_agent_fee
					})
				})
				return newList;
			},
			init() {
				this.request(`http://192.168.137.1:3000/restapi/member/v2/users/14547420/location`).then(res => {
					this.location = res.addresses[0]
				});
				this.request(`http://192.168.137.1:3000/restapi/shopping/v2/banners`).then(res => {
					this.bannerList = this.imgEdit(res)
				});
				this.request(`http://192.168.137.1:3000/restapi/shopping/v2/entries`).then(res => {
					this.classifyList[0] = this.imgEdit(res[0].entries)
					this.classifyList[1] = this.imgEdit(res[1].entries)
					this.flag = true
				});
				this.request(`http://192.168.137.1:3000/restapi/shopping/v3/restaurants`).then(res => {
					this.shopList = this.merchant(res.items);
				})
			}
		}
	}
</script>

<style lang="scss">
	page {
		box-sizing: border-box;
		padding: 0rpx 20rpx;

		.banner {
			width: 100%;
			margin: 40rpx 0;
		}

		.shopping {
			margin-top: 40rpx;
		}
	}
</style>
