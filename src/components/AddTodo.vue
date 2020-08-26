<template>
	<form @submit.prevent="addTodo">
		<input v-model="title" type="text">
		<button type="submit">addTodo</button>
	</form>
</template>

<script>
	export default {
		name: 'AddTodo',
		data(){
			return{
				title: ''
			}
		},
		methods: {
			addTodo: function () {
				if(this.title.trim()){
					const newTodo = {
						id: Date.now(),
						title: this.title,
						completed: false,
					}
					this.$emit('add-todo', newTodo);
					this.title = '';
				}
			}
		}
	}
</script>