<template>
	<view>
		<view style="margin: 40upx;">
			<ayQrcode ref="qrcode" qrcode_id="qrcode" :modal="modal_qr" :url="url" @hideQrcode="hideQrcode" :height="300" :width="300" />
		</view>
		
		<view style="margin: 40upx;">
			<ayQrcode ref="qrcode2" qrcode_id="qrcode2" :modal="modal_qr" :url="url" @hideQrcode="hideQrcode" :height="300" :width="300" 
			themeColor="#33CCCC"/>
		</view>
		
		<view style="margin: 40upx;">
			<ayQrcode ref="qrcode3" qrcode_id="qrcode3" :modal="modal_qr" :url="url" @hideQrcode="hideQrcode" :height="300" :width="300"
			 themeColor="#dd524d" 
			 :is_themeImg="true"
			  themeImg="../../static/logo.png"
			  :h_w_img="40" 
			  />
		</view>
		
		<view style="margin: 40upx;">
			<ayQrcode ref="qrcode4" qrcode_id="qrcode4" :modal="modal_qr" :url="url" @hideQrcode="hideQrcode" :height="300" :width="300"
			 themeColor="#ddd890" 
			 :is_themeImg="true"
			  themeImg="https://cdn.pixabay.com/photo/2016/11/29/13/24/balloons-1869816__340.jpg"
			  :h_w_img="40" 
			  />
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
					_this.$refs.qrcode.crtQrCode()
					_this.$refs.qrcode2.crtQrCode()
					_this.$refs.qrcode3.crtQrCode()
					_this.$refs.qrcode4.crtQrCode()
				}, 100)
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
