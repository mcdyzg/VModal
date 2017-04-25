VModal
==========

vue模态框组件

## Run Demo


```
1. npm install
2. npm start
```
@onShow='this.show'	
		@onHide='this.hide'	
	  	@onClose='showModal = !showModal'
	  	modalStyle=''
	  	overlayStyle=''
	  	:msg='msg'
	  	:overlayClose='true'
	  	:show='showModal' >

## Usage


```
<template>
  <div id="app">
	<VModal
		@onShow='this.show'	
		@onHide='this.hide'	
	  	@onClose='showModal = !showModal'
	  	modalStyle=''
	  	overlayStyle=''
	  	:msg='msg'
	  	:overlayClose='true'
	  	:show='showModal' >
	</VModal>
	<VModal
	  	@onClose='showModal2 = !showModal2'
	  	modalStyle=''
	  	overlayStyle=''
	  	:overlayClose='true'
	  	:show='showModal2' >
	  	<div>自定义模态框内容</div>
	</VModal>
	<button @click='showModal = !showModal'>点击显示modal1</button>
	<button @click='showModal2 = !showModal2'>点击显示modal2</button>
  </div>
</template>

<script>
import VModal from '../components/VModal'

export default {
  name: 'app',
  components: {
	VModal
  },
  data(){
	return {
		showModal:false,
		showModal2:false,
		msg:'出错啦'
	}
  },
  methods:{
  	show(){
  		console.log('show')
  	},
  	hide(){
  		console.log('hide')
  	}
  },
  computed:{
  },
}
</script>
```

## API

* modalStyle: 模态框的style
* overlayStyle:遮罩层的style
* msg:弹框中将显示的错误信息
* overlayClose:点击遮罩层是否关闭弹框，默认false
* show:弹框显示状态
* onClose:自定义事件，当弹框内部点击关闭时将调用此方法
* onHide:自定义事件，弹框隐藏时执行此事件
* onShow:自定义事件，弹框显示时执行此事件
