<template>
	<div class="fullmodal-modal" :class="{'is-show': modalOpenState}">
		<div class="fullmodal-wrapper">
			<div class="fullmodal-container">
				<slot name="close">
					<div @click="closeModal" class="fullmodal-close" :class="{backActionClassName : enableBackAction }">
						<span></span>
					</div>
				</slot>
				<div class="fullmodal-box-wrapper display-flex">
					<div class="container">
						<slot name="container">
							<div class="example-box">
								<h4>FullModal Header</h4>
								<p>This is a short Description that may be fit to describe what you want or what you think.</p>
								<div class="example-box-actions">
									<a href="javascript:;" class="primary-btn btn-principal confirm-revoke-cnnct text-center">Primary Action</a>
									<a @click="$emit('close')" href="javascript:;" class="primary-btn btn-bordered dark text-center">Secondary Action</a>
								</div>
							</div>
						</slot>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	export default {
		props:{
			customClass:{
				default:'is-show'
			},
			open:{
				default:false
			}
		},
		data() {
			return {
				modalOpenState:false,
				enableBackAction:false,
				backActionClassName: 'fullmodal-back'
			}
		},
		methods:{
			closeModal() {
				this.$emit(this.enableBackAction ? 'back' : 'close');
				this.modalOpenState = false;
			}
		},
		mounted() {
			this.modalOpenState = this.open;
			this.$emit('mounted')
		}
	}
</script>
<style type="text/css">
	
.fullmodal-modal {
  position: fixed;
  height: 100vh;
  width: 100vw;
  overflow: auto;
  z-index: 999;
  right: 0;
  left: auto;
  top: 0;
  -webkit-box-align: center;
  -webkit-align-items: center;
      -ms-flex-align: center;
          align-items: center;
  -webkit-align-self: center;
      -ms-flex-item-align: center;
          align-self: center;
  display: -ms-flexbox;
  display: -webkit-box;
  display: -webkit-flex;
  display: flex;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease-in-out;
  -webkit-transition: all 0.3s ease-in-out;
  -ms-transition: all 0.3s ease-in-out;
  background: rgba(0, 0, 0, 0.5);
}
.fullmodal-modal.is-show {
  opacity: 1;
  visibility: visible;
}
.fullmodal-modal.is-show .close-fullmode {
  opacity: 1;
  visibility: visible;
  top: 15px;
}
.fullmodal-container {
  overflow: auto;
  width: 100%;
  min-height: 100%;
  padding: 50px 0 30px;
}
.fullmodal-wrapper {
  width: 100%;
  margin: auto;
  background: #fff;
  overflow: hidden;
  position: relative;
  display: block;
  height: 100%;
  min-height: 100vh;
  overflow: auto;
}
.fullmodal-close {
  position: relative;
  z-index: 10;
  padding: 0;
  border: none;
  cursor: pointer;
  opacity: 0.5;
  text-transform: uppercase;
  height: 40px;
  width: 40px;
  text-align: center;
  font-size: 12px;
  overflow: hidden;
  line-height: 1;
  margin: 0 auto 30px;
  background-color: #e0e0e0;
  border-radius: 100%;
  -webkit-border-radius: 100%;
  -ms-border-radius: 100%;
  transition: all 0.3s ease-in-out;
  -webkit-transition: all 0.3s ease-in-out;
  -ms-transition: all 0.3s ease-in-out;
}
.fullmodal-close.fullmodal-back span {
  background-image: url(img/arrowup-white.svg);
  background-position: 13px center;
}
.fullmodal-close.fullmodal-back span:before,
.fullmodal-close.fullmodal-back span:after {
  display: none;
}
.fullmodal-close:hover {
  opacity: 1;
}
.fullmodal-close:hover:not(.fullmodal-back) span {
  transform: rotate(90deg);
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
}
.fullmodal-close:hover.fullmodal-back span {
  transform: translateY(-5px);
  -webkit-transform: translateY(-5px);
  -moz-transform: translateY(-5px);
  -ms-transform: translateY(-5px);
}
.fullmodal-close span {
  width: 100%;
  height: 100%;
  display: block;
  margin: auto;
  transition: transform 0.3s cubic-bezier(0.24, 0.51, 0.18, 0.99);
  -webkit-transition: -webkit-transform 0.3s cubic-bezier(0.24, 0.51, 0.18, 0.99);
  -ms-transition: transform 0.3s cubic-bezier(0.24, 0.51, 0.18, 0.99);
  position: relative;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-repeat: no-repeat;
}
.fullmodal-close span:before,
.fullmodal-close span:after {
  position: absolute;
  content: "";
  left: 19px;
  top: 13px;
  border-radius: 2px;
  -webkit-border-radius: 2px;
  -ms-border-radius: 2px;
  background-color: #333;
  height: 14px;
  width: 2px;
}
.fullmodal-close span:before {
  transform: rotate(45deg);
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
}
.fullmodal-close span:after {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
  -ms-transform: rotate(-45deg);
}
.duedate-picker .input-icon-addon {
  background-color: #eef2f5;
}
.duedate-picker .input-icon-addon i {
  right: 11px;
}
.duedate-picker .input-icon-addon svg {
  fill-opacity: 1;
}
.step-wizard {
  width: 100%;
}
.step-wizard.active {
  display: block;
}
.move-top {
  animation: center_to_top 0.5s backwards;
  -webkit-animation: center_to_top 0.5s backwards;
  -ms-animation: center_to_top 0.5s backwards;
}
.move-center {
  animation: top_to_center 0.5s backwards;
  -webkit-animation: top_to_center 0.5s backwards;
  -ms-animation: top_to_center 0.5s backwards;
}
@-webkit-keyframes center_to_top {
  0% {
    opacity: 1;
    transform: translateY(0);
    -webkit-transform: translateY(0);
    -moz-transform: translateY(0);
    -ms-transform: translateY(0);
  }
  100% {
    opacity: 0;
    transform: translateY(200px);
    -webkit-transform: translateY(200px);
    -moz-transform: translateY(200px);
    -ms-transform: translateY(200px);
  }
}
@keyframes center_to_top {
  0% {
    opacity: 1;
    transform: translateY(0);
    -webkit-transform: translateY(0);
    -moz-transform: translateY(0);
    -ms-transform: translateY(0);
  }
  100% {
    opacity: 0;
    transform: translateY(200px);
    -webkit-transform: translateY(200px);
    -moz-transform: translateY(200px);
    -ms-transform: translateY(200px);
  }
}
.fullmodal-box-wrapper {
  position: relative;
  width: 100%;
  min-height: calc(100vh - 190px);
}
.example-box {
  margin: auto;
  text-align: center;
}
.example-box h4 {
  color: #454553;
  font-family: "Nunito", sans-serif;
  font-size: 30px;
  line-height: 30px;
  font-weight: 300;
  max-width: 415px;
  margin: 0 auto 20px;
  text-align: center;
}
.example-box p {
  color: #454553;
  font-size: 16px;
  line-height: 24px;
  max-width: 415px;
  margin: auto;
  text-align: center;
}
.example-box .connection-circles {
  text-align: center;
  position: relative;
  margin-bottom: 36px;
}
.example-box .connection-circles .circles {
  display: inline-block;
  height: 200px;
  position: relative;
}
.example-box .connection-circles .cnnct-logo {
  height: 60px;
}
.example-box-actions {
  margin-top: 40px;
}
.example-box-actions .kontent-btn + .kontent-btn {
  margin-left: 10px;
}
.example-box-actions .cancel-btn {
  width: 120px;
}
.internal-check-label {
  display: inline-block;
  margin-right: 30px !important;
}
.primary-btn {
  color: #fff;
  position: relative;
  overflow: hidden;
  z-index: 1;
  font-family: "Nunito", sans-serif;
  font-weight: 500;
  font-size: 16px;
  padding: 13px 20px 13px;
  height: 48px;
  transition: all 0.2s ease-out;
  -webkit-transition: all 0.2s ease-out;
  -ms-transition: all 0.2s ease-out;
  min-width: 120px;
  line-height: 1.5;
  letter-spacing: .3px;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-border-radius: 2px;
  -ms-border-radius: 2px;
  display: inline-block;
  vertical-align: middle;
  -ms-touch-action: manipulation;
  touch-action: manipulation;
  cursor: pointer;
  text-align: center;
  background-image: none;
  white-space: nowrap;
  -webkit-user-select: none;
     -moz-user-select: none;
      -ms-user-select: none;
          user-select: none;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -ms-user-select: none;
  text-transform: capitalize;
}
.primary-btn:focus {
  color: #fff;
}
.primary-btn i[class*="spinner"] {
  position: relative;
  vertical-align: middle;
  height: 19px;
  width: 14px;
  line-height: 1;
  text-align: center;
}
.primary-btn:active {
  box-shadow: none;
  -webkit-box-shadow: none;
  -ms-box-shadow: none;
}
.primary-btn:hover:not(.disabled) {
  color: #fff;
}
.primary-btn.btn-principal {
  background-color: #c63e3e;
}
.primary-btn.btn-principal:hover,
.primary-btn.btn-principal.active {
  	color: #c63e3e;
	background-color: #ffffff;
	border: 1px solid #c63e3e;
}
.primary-btn.btn-bordered {
  background-color: #ffffff;
  color: #939cae;
  border: 1px solid #c9cdd6;
  height: 48px;
}
.primary-btn.btn-bordered:focus {
  color: #939cae;
}

.primary-btn.dark:hover,
.primary-btn.dark:focus {
  color: #333;
  border-color: #333;
}

</style>