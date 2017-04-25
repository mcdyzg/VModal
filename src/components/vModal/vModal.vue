

<template>
	<transition name='fade'>
	<div v-if='show' >
		<div @click='this.overlayClick' class="vljh-modal-overlay" :style='overlayStyle'></div>
		<div class="vljh-modal" :style='modalStyle' >
			<slot>
			    <div style="text-align:center;padding:20px 10px;" >
					<svg class="icon" style="margin: 15px 0;" viewBox="0 0 1024 1024"  width="3rem" height="3rem"><path d="M516.461 20.457c-274.346 0-496.742 222.394-496.742 496.742s222.394 496.742 496.742 496.742 496.742-222.394 496.742-496.742-222.394-496.742-496.742-496.742zM516.461 964.278c-246.527 0-447.079-200.547-447.079-447.079s200.547-447.079 447.079-447.079 447.079 200.547 447.079 447.079-200.547 447.079-447.079 447.079z" fill="#ff5600" ></path><path d="M741.978 291.67c-12.099-12.117-31.79-12.117-43.905 0l-181.633 181.633-181.633-181.633c-12.102-12.117-31.795-12.117-43.905 0-12.117 12.102-12.117 31.79 0 43.905l181.633 181.633-181.633 181.633c-12.117 12.102-12.117 31.79 0 43.905 6.032 6.061 13.984 9.073 21.942 9.073 7.926 0 15.886-3.03 21.942-9.073l181.633-181.633 181.633 181.633c6.061 6.061 14.002 9.073 21.942 9.073s15.886-3.03 21.942-9.073c12.117-12.102 12.117-31.79 0-43.905l-181.669-181.633 181.633-181.633c12.117-12.102 12.117-31.79 0-43.905z" fill="#ff5600" ></path></svg>
					<div class="error-text">{{msg}}</div>
					<div v-if='showCloseBtn === undefined ? true:showCloseBtn' @click='this.innerClose' class="error-btn">关闭</div>
				</div>
			</slot>
		</div>
	</div>
	</transition>
</template>

<script>
import Vue from 'vue'

export default {
	name: 'vModal',
	props:[
		// 模态框的样式
		'modalStyle',
		// 遮罩层的样式
		'overlayStyle',
		// 是否显示
		'show',
		// 错误信息
		'msg',
		// 是否显示关闭按钮
		'showCloseBtn',
		// 遮罩点击是否隐藏
		'overlayClose'
	],
	data () {
		return {
		}
	},
	mounted(){
		this.show && this.$emit('onShow')
	},
	updated(){
		this.show ? this.$emit('onShow'):this.$emit('onHide')
	},
	methods: {
		innerClose(){
			this.$emit('onClose')
		},
		overlayClick(){
			if(this.overlayClose){
				this.$emit('onClose')
			}
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fade-enter-active, .fade-leave-active {
  	transition: all 0.5s;
}
.fade-enter,.fade-leave-active{
	opacity: 0;
}

.vljh-modal-overlay{
	position: fixed;
	top:0;
	left:0;
	right:0;
	bottom:0;
	z-index: 998;
	opacity: 0.5;
	background: #333;
}
.vljh-modal{
	position: fixed;
	top:50%;
	left:50%;
    width: 80%;
    min-width: 200px;
    max-width: 800px;
    border-radius: 3px;
	color:#333;
	background: #fff;
	z-index: 999;
	transform: translate(-50%,-50%);
	
	
}
.error-text{
	padding:1rem;
	font-size:1.0rem;
}
.error-btn{
	width:5rem;
	text-align:center;
	color:#fff;
	background:#ff7600;
	padding:0.8rem 0;
	margin:0 auto;
	border-radius:5px;
}
</style>
