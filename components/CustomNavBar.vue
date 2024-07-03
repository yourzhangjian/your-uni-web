<template>
	<view class="custom_navbar">
		<view style="height:36px;"></view>
		<uni-nav-bar :left-text="leftText" :right-text="rightText" :title="title" :color="color" :background-color="backgroundColor" @clickLeft="clickLeft" @clickRight="clickRight" />
	</view>
</template>

<script>
export default {
	name:"CustomNavBar",
	props: {
		leftText: {
			type: String,
			default: ''
		},
		rightText: {
			type: String,
			default: ''
		},
		title: {
			type: String,
			default: ''
		},
		color: {
			type: String,
			default: '#f1f1f1'
		},
		backgroundColor: {
			type: String,
			default: '#0088ff'
		}
	},
	data() {
		return {
			
		};
	},
	methods: {
		clickLeft() {
			alert(1)
		},
		clickRight() {
			alert(2)
		}
	},
}
</script>

<style scoped>
.custom_navbar {
	
}
</style>