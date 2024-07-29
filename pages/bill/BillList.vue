<template>
	<view>
		<CustomNavBar left-text="返回" rightText="设置" title="单据列表" />
		<uni-swipe-action class="swipe_action" ref="swipeAction">
			<view v-for="(item, index) in dataList" :key="index">
				<uni-section title="个人信息" type="line" @click="toEdit()"></uni-section>
				<uni-swipe-action-item :right-options="options">
					<view class="content-box">
						<text class="content-text">{{ item.name+index }}</text>
					</view>
				</uni-swipe-action-item>
			</view>
		</uni-swipe-action>
	</view>
</template>

<script>
import CustomNavBar from '@/components/CustomNavBar.vue'
export default {
	components: {
		CustomNavBar
	},
	data() {
		return {
			dataList: [],
			options: [{
					text: '取消',
					style: {
						backgroundColor: '#007aff'
					}
				},
				{
					text: '确认',
					style: {
						backgroundColor: '#F56C6C'
					}
				}
			],
		}
	},
	onLoad() {
		 const systemInfo = uni.getSystemInfoSync()
		 console.log(systemInfo);
		 console.log(systemInfo.appVersion);
	},
	onPullDownRefresh() {
		console.log('onPullDownRefresh...');
		uni.showToast({
			title: '下拉刷新中...',
			icon: 'none',
			duration: 2000
		});
	},
	created() {
		for (let i = 0; i < 30; i++) {
			this.dataList.push({
				id: i,
				number: '2024070415321'+i,
				bizDate: '2004-07-05',
				name: '单据名称',
				remark: '这是一个备注'
			})
		}
	},
	methods: {
		toEdit() {
			uni.navigateTo({
				url: '/pages/bill/BillEdit'
			});
		}
	}
}
</script>

<style scoped>
::v-deep .uni-swipe_box {
	background-color: white;
	height: 80px;
	margin: 5px 0;
}
</style>