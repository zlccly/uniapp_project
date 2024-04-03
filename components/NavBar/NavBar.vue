<template>
	<view class="nav-bar">
		<view class="nav-bar-top">
			<!-- 上边距 -->
			<view :style="{paddingTop: statusHeight +'rpx'}"></view>
			<view class="nav-bar-content" :style="{marginRight:marginRight+'rpx'}" @click="goSearchPage">
				<uni-icons class="nav-bar-search-icon" type="search"></uni-icons>
				<view class="nav-bar-search-text">输入文章标题进行搜索</view>
			</view>
		</view>
		<!-- 底部垫片 -->
		<view :style="{height: 80+statusHeight+'rpx'}"></view>
	</view>
</template>

<script>
	export default {
		name: "NavBar", // 便于devtools进行查找
		data() {
			return {
				statusHeight: 20,
				marginRight: 0
			};
		},
		created() {
			// 获取初始化状态栏高度
			this.initStatusBarHeight()

		},
		methods: {
			initStatusBarHeight() {
				const systemInfo = uni.getSystemInfoSync()
				console.log(systemInfo, "jjhhk");
				this.statusHeight = systemInfo.statusHeight ? systemInfo.statusBarHeight * 2 : this.statusHeight
				// #ifdef MP-WEIXIN
				const menuButtonInfo = uni.getMenuButtonBoundingClientRect()
				this.marginRight = menuButtonInfo.width * 2
				this.statusHeight = menuButtonInfo.top * 2
				console.log(menuButtonInfo);
				// #endif
			},
			goSearchPage() {
				uni.navigateTo({
					url: "/pages/search/search"
				})
			}
		}
	}
</script>

<style lang="scss">
	@import "./css/NavBar.scss";
</style>