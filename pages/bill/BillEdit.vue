<template>
	<view>
		<CustomNavBar left-text="返回" rightText="设置" title="单据编辑" />
		<uni-section title="提示消息" type="line">
			<view class="example-body box">
				<button class="button popup-success" @click="showToast()"><text
						class="button-text success-text">showToast</text></button>
				<button class="button popup-error" @click="showPopup()"><text
						class="button-text error-text">showPopup</text></button>
				<button class="button popup-warn" @click="showMessage()"><text
						class="button-text warn-text">showMessage</text></button>
				<button class="button popup-info" @click="showDialog()"><text
						class="button-text info-text">showDialog</text></button>
			</view>
		</uni-section>
				
		<!-- 普通弹窗 -->
		<uni-popup ref="popup" background-color="#fff" @change="change">
			<view style="width: 300px;">
				<text class="text">popup 内容</text>
			</view>
		</uni-popup>
		<!-- 提示信息弹窗 -->
		<uni-popup ref="message" type="message">
			<uni-popup-message :type="msgType" :message="messageText" :duration="2000"></uni-popup-message>
		</uni-popup>
		<!-- 提示窗示例 -->
		<uni-popup ref="alertDialog" type="dialog">
			<uni-popup-dialog :type="msgType" cancelText="关闭" confirmText="同意" title="通知" content="欢迎使用 uni-popup!" @confirm="dialogConfirm" @close="dialogClose"></uni-popup-dialog>
		</uni-popup>
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
			msgType: '',
			messageText: ''
		}
	},
	methods: {
		showToast() {
			uni.showToast({
				title: '标题',
				icon: 'none',
				duration: 2000
			});
		},
		showPopup() {
			this.$refs.popup.open('right')
		},
		showMessage() {
			this.msgType = 'success'
			this.messageText = '这是一个消息提示'
			this.$refs.message.open()
		},
		showDialog() {
			this.$refs.alertDialog.open()
		},
	}
}
</script>

<style scoped>
</style>