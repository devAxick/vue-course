

<template>
	<li class="todo-list__item" v-bind:class="{completed: todo.completed}">
		<span>
			<input type="checkbox" v-on:change="todo.completed = !todo.completed ">
			<b>{{index + 1}}</b>
			{{todo.title}}
		</span>
		<button v-on:click="removeTodo">&times;</button>
	</li>
</template>

<script>
	export default {
		name: 'TodoItem',
		props: {
			todo: {
				type: Object,
				required: true,
			},
			index: {
				required: true
			}
		},
		methods:{
			removeTodo: function () {
				this.$emit('remove', this.todo.id)
			}
		}
	}
</script>
