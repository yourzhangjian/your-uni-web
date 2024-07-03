<template>
	<view class="container">
		<CustomNavBar left-text="返回" rightText="设置" title="门户首页" />
		<uni-notice-bar style="margin-bottom: 0px;" showClose showIcon scrollable single text="[多行] 这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏"></uni-notice-bar>
		<uni-swiper-dot :info="info" :current="current" field="content" mode="default">
			<swiper style="padding: 5px;" @change="change">
				<swiper-item v-for="(item ,index) in info" :key="index">
					<image style="border-radius: 5px;width: 100%;height: 150px;" :src="item"></image>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<uni-section title="销售管理" type="line">
			业务信息
		</uni-section>
		<uni-section title="个人信息" type="line">
			个人信息
		</uni-section>
		<!-- 升级中心 -->
		<UpgradeCenter />
	</view>
</template>

<script>
import UpgradeCenter from '@/components/UpgradeCenter.vue'
import CustomNavBar from '@/components/CustomNavBar.vue'
export default {
	components: {
		UpgradeCenter,CustomNavBar
	},
	data() {
		return {
			info: [
				'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				'https://cdn.uviewui.com/uview/swiper/swiper2.png',
				'https://cdn.uviewui.com/uview/swiper/swiper3.png'
			],
			current: 0,
			statusBarHeight: 0
		}
	},
	onLoad() {
		const systemInfo = uni.getSystemInfoSync();
		console.log(systemInfo);
		this.statusBarHeight = systemInfo.platform === 'android'? 30 : (systemInfo.platform === 'ios'?20:0)
	},
	methods: {
		change(e) {
			this.current = e.detail.current;
		}
	}
}
</script>

<style>
</style>
