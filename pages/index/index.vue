<template>
	<view class="content">
		<view class="text-area">
			<button @click="onEntry">评论</button>
		</view>
		<view>e.g.请用手机调试效果明显</view>
		<view>作者snoop</view>
		<view>发送了：{{comment}}</view>
		<easy-entry ref="easyEntry" @send="send" theme="#111"></easy-entry>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				comment: ''
			}
		},
		methods: {
			onEntry() {
				this.$refs.easyEntry.onEntry()
			},
			send(comment) {
				this.comment = comment
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}
</style>
