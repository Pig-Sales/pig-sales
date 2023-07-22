<template>
	<view>
		<view class="my-userinfo-container">

			<!-- 头像昵称区域 -->
			<view class="top-box" @click="loginIf">
				<image src="/static/icon/touxiang-initial.png" class="avatar"></image>
				<view class="info" v-if="tokenExist">
					<view class="nickname">南北nas</view>
					<view class="telephone">手机：13557054327</view>
				</view>
				<view class="info" v-else>
					<view class="nickname">点击登录</view>
					
				</view>

			</view>

		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				token: ""
			};
		},
		computed:{
			tokenExist(){
				return this.token!==""
			}
		},
		methods: {
			loginIf() {
				uni.showModal({
					title: '授权登录',
					content: '该功能需要授权登录！',
					cancelText:"暂不登录",
					confirmText:"授权登录",
					confirmColor: "#00aa00",
					bordercolor:"#c00000",
					success: function(res) {
						if (res.confirm) {
							console.log('授权登录');
						} else if (res.cancel) {
							console.log('暂不登录');
						}
					}
				});
			}
		}
	}
</script>

<style lang="scss">
	.my-userinfo-container {
		height: 100%;
		// background-color: #f4f4f4;

		.top-box {
			height: 250rpx;
			background-color: #c00000;
			display: flex;
			// flex-direction: column;
			align-items: center;
			// justify-content: space-around;

			.avatar {
				display: block;
				width: 90px;
				height: 90px;
				border-radius: 45px;
				margin-left: 60rpx;
				// border: 2px solid white;
				// box-shadow: 0 1px 5px black;
			}

			.info {
				display: flex;
				flex-direction: column;
				margin-bottom: 12rpx;
				margin-left: 12rpx;

				.nickname {
					text-align: left;
					color: white;
					font-size: 30px;
				}

				.telephone {
					color: white;
					font-size: 16px;
				}
			}
		}
	}
</style>