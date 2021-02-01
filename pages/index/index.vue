<template>
	<view>
		<view style="margin-top: 26upx;margin: 40upx;">
			<ayQrcode ref="qrcode" :modal="modal_qr" :url="url" @hideQrcode="hideQrcode" />
		</view>
	</view>
</template>

<script>
	import ayQrcode from "@/components/ay-qrcode/ay-qrcode.vue"
	export default {
		components: {
			ayQrcode,

		},
		data() {
			return {
				//二维码相关参数
				modal_qr: false,
				url: 'https://pixabay.com/images/search/?order=ec', // 要生成的二维码值
				
			}
		},

		onLoad() {
			let that = this;
			that.showQrcode();//一加载生成二维码
		},
		methods: {
			// 展示二维码
			showQrcode() {
				let _this = this;
				this.modal_qr = true;
				// uni.showLoading()
				setTimeout(function() {
					// uni.hideLoading()
					_this.$refs.qrcode.couponQrCode()
				}, 50)
			},

			//传入组件的方法
			hideQrcode() {
				this.modal_qr = false;
			},
		}

	}
</script>

<style lang="scss">
</style>
