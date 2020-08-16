<template>
	<view>
		<view class="btn">
			<button type="primary" @click="createGroup()" :disabled='disabled'>
				创建群组
			</button>
		</view>
		<!-- 好友列表 -->
		<uni-indexed-list :options="list" :showSelect="true" @click="itemClick"></uni-indexed-list>
	</view>
</template>

<script>
	import userList from '../../commen/tim/user.js'
	import uniIndexedList from "@/components/uni-indexed-list/uni-indexed-list.vue"

	export default {
		name: 'createGroup',
		components: {
			uniIndexedList
		},
		data() {
			return {
				friendList: [],
				selectList: [],
				list: [{
						"letter": "A",
						"data": [{
								user: "阿克苏机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "阿拉山口机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "阿勒泰机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "阿里昆莎机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "安庆天柱山机场",
								userId: 1,
								userSign: '',
								img: ''
							}
						]
					},
					{
						"letter": "B",
						"data": [{
								user: "保山机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "包头机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "北海福成机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "北京南苑机场",
								userId: 1,
								userSign: '',
								img: ''
							},
							{
								user: "北京首都国际机场",
								userId: 1,
								userSign: '',
								img: ''
							}
						]
					},

					{
						"letter": "X",
						"data": [{
							user: "西安机场",
							userId: 11,
							userSign: '',
							img: ''
						}, ]
					}
				]
			}
		},
		computed:{
			disabled(){
				return this.selectList.length === 0
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
				console.log('createGroup',this.selectList)
				// let promise = this.tim.createGroup({
				// 	type: this.$TIM.TYPES.GRP_PUBLIC,
				// 	name: '阿萨德',
				// 	memberList: [{
				// 		userId: '3'
				// 	}, {
				// 		userId: '4'
				// 	}] // 如果填写了 memberList，则必须填写 userID
				// });
				// promise.then(function(imResponse) { // 创建成功
				// 	console.log('建群成功')
				// 	console.log(imResponse.data.group); // 创建的群的资料
				// }).catch(function(imError) {
				// 	console.warn('createGroup error:', imError); // 创建群组失败的相关信息
				// });
			},
			itemClick({
				item,
				select
			}) {
				console.log('item', item)
				console.log('select', select)
				this.selectList = select
			}
		},
		onShow() {
			if (this.isSDKReady) {
				console.log('SDKReady')
			} else {
				console.log('333333')
			}
		},
		onLoad(options) {
			let friendList = JSON.parse(decodeURIComponent(options.friendList)) || []
			this.friendList = friendList
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
