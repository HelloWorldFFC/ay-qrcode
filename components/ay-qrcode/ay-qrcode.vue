<template>
	<view :class="modal?'show':'hide'">
		<canvas class="canvas" style="width: 550rpx;height: 550rpx;" canvas-id="couponQrcode"></canvas>
	</view>
</template>

<script>
	const qrCode = require('./weapp-qrcode.js')
	export default {
		data() {
			return {
				show: true
			}
		},
		props: {
			modal: {
				type: Boolean,
				default: false
			},
			url: {
				type: String,
				default: ''
			}
		},
		methods: {
			// 展示二维码
			// showQrcode(){
			// this.modal=true;
			// let ID=uni.getStorageSync('userInfo').id;
			// let url="https://www.ttlwl.cn/appDownload.html?shareUserId="+ID;
			// this.couponQrCode(url);
			// },
			hideQrcode() {
				// this.modal=false;
				this.$emit("hideQrcode")
			},
			// 二维码生成工具
			couponQrCode() {
				let _this = this;
				new qrCode('couponQrcode', {
					text: this.url,
					width: 260,
					height: 260,
					colorDark: "#333333",
					colorLight: "#FFFFFF",
					correctLevel: qrCode.CorrectLevel.H
				})
			}
		},
		mounted() {}
	}
</script>

<style scoped lang="scss">
	.qrcode-box {
		position: fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		height: 100vh;
		width: 100vw;
		background-color: rgba(59, 59, 59, 0.6);
		// opacity: 0.8;
		text-align: center;
		display: flex;
		align-items: center;
		display: none;

		.qrcode-item {
			flex: 1;
			position: relative;
			text-align: center;

			.item-box {
				width: 90%;
				margin: auto;
				display: inline-block;
				margin-top: 30%;
				padding-bottom: 30rpx;

				// animation: show 0.7s;
				.title {
					font-size: 46rpx;
					text-align: center;
					margin-bottom: 24rpx;
				}

				.canvas {
					margin: auto;
					display: inline-block;
					margin: auto;
				}

				background-color: #FFFFFF;
			}

		}
	}

	.opacity {
		opacity: 0;
		display: block;
	}

	.show {
		display: block;
		animation: fade 0.7s;
		// -moz-animation: fade 0.5s; /* Firefox */
		// -webkit-animation: fade 0.5s; /* Safari 和 Chrome */
		// -o-animation: fade 0.5s;
	}

	.hide {
		animation: hide 0.7s;
	}

	@keyframes fade {
		from {
			opacity: 0.8;
		}

		to {
			opacity: 1;
		}
	}

	@keyframes hide {
		from {
			opacity: 1;
		}

		to {
			opacity: 0;
		}
	}
</style>
