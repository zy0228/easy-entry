# easy-entry (小程序版uniapp)
*输入组件，应用场景：评论等，（可悬浮在软键盘上方* 
### Basic example
```
<template>
	<view class="content">
		<view class="text-area">
			<button @click="onEntry">评论</button>
		</view>
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
```
---
### Motivation
*从评价业务中分离出来的单独小模块 '评价输入功能'，我觉得这就是你想找的*
___
### Options:
| props            | type    | require | explain                               |
| ---------------- | ------- | ------- | ------------------------------------- |
| theme    				 |str 		 | false   | 输入框背景颜色													 |
| @send            |function | false   | 发送事件 携带输入内容   								 |
---
### Notice
+ 不需要啥具体配置直接引入即可
---
### finally
同样的如果你可以，也鼓励你可以在我的基础上自己魔改~
另外这是我另外一个作品, 同样的好用快捷强大
[easy-tabBar](https://ext.dcloud.net.cn/plugin?id=2221)。
[easy-select](https://ext.dcloud.net.cn/plugin?id=2511)
最后，如果喜欢的话去 [github](https://github.com/zy0228/easy-entry) 点个赞吧

有疑问加wx: QJZY123
