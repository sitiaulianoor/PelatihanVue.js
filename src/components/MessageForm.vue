<template>
	<div class="form">
		<input v-model="msg" />
		<button @click="addMessage">Add</button>
		<br />
		<ul>

				//fungsi if nama reza masih muncul di listMessage tapi tidak ditampilkan
			<li v-for="(message, id) in listMessage" v-bind:key="id" v-if="message != 'reza'">{{message}}</li>
		</ul>
		<label>{{msg}}</label>
	</div>
</template>

<script>

	export default{
	name : 'MessageForm',
	data(){
		return{
			listMessage: [],
			msg:"",
		}
	},

	methods: {
		addMessage(){
			//if (this.msg !="reza"){} // untuk menghilangkan nama reza dari listMessage
			this.listMessage.push(this.msg);
			this.msg = "";
		}
	}
}
</script>


