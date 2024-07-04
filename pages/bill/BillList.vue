<template>
	<view>
		<CustomNavBar left-text="返回" rightText="设置" title="单据列表" />
		<uni-swipe-action class="swipe_action" ref="swipeAction">
			<uni-swipe-action-item
				v-for="(item, index) in dataList"
				:right-options="options"
				:key="index"
			>
				<view class="content-box">
					<text class="content-text">{{ item.name+index }}</text>
				</view>
			</uni-swipe-action-item>
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
	onPullDownRefresh() {
		console.log('onPullDownRefresh...');
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