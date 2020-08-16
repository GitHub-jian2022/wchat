<template>
	<view>
		<view class="btn" style="margin-bottom: 40rpx;">
			<button type="default" @click="createGroup()">
				创建群组
			</button>
		</view>
		<!-- 好友列表 -->
		<view class="user-box">

			<view class="list-box" v-if="friendList.length > 0">
				<view class="user-item-box" v-for="(item,index) in friendList" :key="index" @click="checkUserToRoom(item)">
					<view class="user-img">
						<image :src="item.img" alt=""></image>
					</view>
					<view class="user-name">
						{{item.user}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import userList from '../../commen/tim/user.js'
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"

	export default {
		name: 'contact',
		components: {
			uniNavBar
		},
		data() {
			return {
				friendList: [],
			}
		},
		methods: {
			//选择用户聊天
			checkUserToRoom(toUserInfo) {
				this.$store.commit('createConversationActive', toUserInfo.userId)
				uni.navigateTo({
					url: '/pages/tim/room'
				})
			},
			createGroup() {
				uni.navigateTo({
					url: '/pages/tim/createGroup?friendList='+encodeURIComponent(JSON.stringify(this.friendList))
				})
			},
			onShow() {
				if (this.isSDKReady) {
					console.log('SDKReady')
				} else {
					console.log('333333')
				}
			},
			onLoad() {
				let userInfo = JSON.parse(uni.getStorageSync('userInfo'))
				this.friendList = []
				userList.forEach(item => {
					if (item.userId != userInfo.userId) {
						// console.log(item)
						this.friendList.push(item)
					}
				})

			}
		}
	}
</script>

<style scoped lange="scss">
	.list-box {
		width: 94%;
		margin: 40rpx auto;
	}

	.user-box {
		width: auto;
		height: 80rpx;
		padding: 0 20rpx;
	}

	.user-item-box {
		padding: 20rpx 0;
		width: auto;
		height: 70rpx;
		line-height: 70rpx;
		cursor: pointer;
		border-bottom: 1px solid #eee;
	}

	.user-img {
		float: left;
		width: 70rpx;
		height: 70rpx;
		border-radius: 50%;
		overflow: hidden;
	}

	.user-img image {
		width: 70rpx;
		height: 70rpx;
		border-radius: 50%;
	}

	.user-name {
		float: left;
		margin-left: 20rpx;
		width: 250rpx;
		height: 70rpx;
		line-height: 70rpx;
		color: #666;
		font-weight: 500;
	}
</style>
