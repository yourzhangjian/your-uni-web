<template>
	<view>
		<CustomNavBar left-text="返回" rightText="设置" title="单据编辑" />
		<uni-section title="基本信息" type="line">
			<view class="uni-input">
				<label>标签名称</label>
				<input  placeholder-style="color:#F76260" placeholder="自动获得焦点" />
			</view>
		</uni-section>
		<uni-section title="分录信息" type="line">
		</uni-section>
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
			billInfo: {},
			entryInfo: [],
		}
	},
	methods: {
		
	}
}
</script>

<style scoped>
.uni-input label {
	display: inline-block;
	background-color: bisque;
}
.uni-input input {
	display: inline-block;
	background-color: aliceblue;
}
</style>