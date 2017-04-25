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

