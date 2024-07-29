<template>
	<view class="container">
		<CustomNavBar rightText="设置" title="门户首页" />
		<uni-notice-bar style="margin-bottom: 0px;" showClose showIcon scrollable single text="[多行] 这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏"></uni-notice-bar>
		<uni-swiper-dot :info="info" :current="current" field="content" mode="default">
			<swiper style="padding: 5px;" @change="change">
				<swiper-item v-for="(item ,index) in info" :key="index">
					<image style="border-radius: 5px;width: 100%;height: 150px;" :src="item"></image>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<uni-section title="销售管理" type="line">
			业务信息 版本号：{{appVersion}}
		</uni-section>
		<uni-section title="个人信息" type="line">
			<uni-grid :column="5">
				<uni-grid-item v-for="item in 5" @click="toView">
					<image style="border-radius: 5px;width: 55px;height: 55px;padding: 15px;" :src="info[0]"></image>
					<text class="text">文本{{item}}</text>
				</uni-grid-item>
			</uni-grid>
		</uni-section>
		<uni-section title="个人信息" type="line">
			个人信息
		</uni-section>
		<uni-section title="个人信息" type="line">
			个人信息
		</uni-section>
		<uni-section title="个人信息" type="line">
			个人信息
		</uni-section>
		<uni-section v-for="item in 30" title="个人信息" type="line">
			个人信息 {{item}}
		</uni-section>
		<!-- 升级中心 -->
		<UpgradeCenter update="isUpdate" />
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
			statusBarHeight: 0,
			appVersion: null,
			isUpdate: false
		}
	},
	onLoad() {
		const systemInfo = uni.getSystemInfoSync();
		this.appVersion = systemInfo.appVersion
	},
	onPullDownRefresh() {
		console.log('onPullDownRefresh...');
		uni.showToast({
			title: '下拉刷新中...',
			icon: 'none',
			duration: 2000
		});
		this.isUpdate = true
	},
	methods: {
		change(e) {
			this.current = e.detail.current;
		},
		toView() {
			uni.navigateTo({
				url: '/pages/bill/BillList'
			});
		}
	}
}
</script>

<style scoped>
::v-deep .uni-grid-item__box{
	border: 0px;
	text-align: center;
}
</style>
