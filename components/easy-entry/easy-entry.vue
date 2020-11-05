<template>
	<view class="easy_content" v-show="show">
		<view class="easy_input-box" v-show="show" :style="{bottom: bottomHeihgt, background: theme}">
				<textarea
					fixed
					auto-height="true"
					:focus="focused"
					:adjust-position="adjustPosition"
					:show-confirm-bar="showConfirmBar"
					cursor-spacing="0"
					class="easy_text"
					@focus="onFocus"
					@blur="onBlur"
					placeholder="输入评论..." placeholder-class="easy_input_null" v-model="commentText"></textarea>
				<view @click.stop="checkContent" class="easy_submit" :class="isEmptyComment ? 'easy-no-valid' : ''">发送</view>
		</view>
	</view>
</template>

<script>
	/**
	 * ===========================================
	 * 评论输入组件可悬浮在软键盘上端
	 * 
	 * author snoop 
	 * github https://github.com/zy0228
	 * ===========================================
	 * props: theme  背景颜色
	 * @end 点击发送时调用, 将当前输入框内容传递
	 * */

	const EASY_ENTRY = 'easy-entry'
	const EMIT_NAME = 'send'
	
	export default {
		name: EASY_ENTRY,
		props: {
			theme: {
				type: String,
				default: '#111'
			}
		},
		data() {
			return {
				commentText: '',
				show: false,
				focused: false,
				adjustPosition: false,
				showConfirmBar: false,
				bottomHeihgt: 0
			}
		},
		computed: {
			/**
			 *检查是否为空输入
			 * */
			isEmptyComment() {
				const formatText = this.commentText.replace(/\s/g, '')
				return formatText.length === 0
			}
		},
		methods: {
			onEntry() {
				this.commentText = ''
				this.show = !this.show
				// set timer fix bug
				setTimeout(() => {
					this.focused = !this.focused
				}, 100)
			},
			onFocus(e) {
				const { height } = e.detail
				this.bottomHeihgt = height + 'px'
			},
			onBlur(e) {
				this.focused = false
				this.show = false
			},
			checkContent() {
				if (this.isEmptyComment) return
				this.$emit(EMIT_NAME, this.commentText)
			}
		}
	}
</script>

<style scoped>
	.easy_content {
	    position: fixed;
	    top: 0;
	    left: 0;
	    right: 0;
	    bottom: 0;
	    z-index: 10000;
			background-color: rgba(0, 0, 0, 0.2);
	}
	
	.easy_input-box {
	    display: flex;
	    align-items: flex-end;
	    justify-content: space-between;
	    box-sizing: border-box;
	    position: absolute;
	    left: 0;
	    bottom: 0;
	    width: 100%;
	    padding: 20rpx 12rpx;
	    background: #111;
	}
	
	.easy_input-box .easy_text {
	    background: #F7F7F7;
	    border-radius: 8rpx;
	    width: 612rpx;
	    /* min-height: 70rpx; */
	    max-height: 120rpx;
	    border-width: 10rpx 20rpx;
	    border-style: solid;
	    border-color: #F7F7F7;
	    line-height: 40rpx;
	    font-family: PingFangSC-Regular;
	    font-size: 28rpx;
	    color: #333333;
	}
	
	.easy_input-box .easy_submit {
	    width: 138rpx;
	    font-family: PingFangSC-Regular;
	    font-size: 32rpx;
	    color: #1B9AF4;
	    text-align: center;
	    height: 64rpx;
	    line-height: 64rpx;
	}
	
	.easy_input_null {
	    margin-left: 12rpx;
	    font-family: PingFangSC-Regular;
	    font-size: 28rpx;
	    color: #939393;
	}
	
	.easy-no-valid {
		color: #939393!important;
	}
</style>
