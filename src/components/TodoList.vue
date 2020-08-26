<template>
	<ul class="todo-list">
		<TodoItem
		v-for="(todo, i ) of todos"
		v-bind:todo="todo"
		v-bind:index="i"
		v-on:remove="remove"
		/>
	</ul>
</template>

<script>
	import TodoItem from "./TodoItem";
	export default {
		name: 'TodoList',
		components:{
			TodoItem
		},
		props: ['todos'],
		methods:{
			remove: function (id) {
				this.$emit('remove', id);
			}
		}
	}
</script>
