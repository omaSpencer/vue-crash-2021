<template>
  <header>
    <h1>{{ title }}</h1>
		<Button 
			v-show="isHomePage"
      @btn-click="$emit('toggle-add-task')" 
      :text="showAddTask ? 'Close' : 'Add task'" 
      :color="showAddTask ? 'red' : 'green'" />
  </header>
</template>

<script>
import Button from './Button';

export default {
	name: 'Header',
	props: {
		title: {
			type: String,
			default: 'Task Tracker'
		},
    showAddTask: Boolean
	},
	components: {
		Button
	},
	computed: {
		isHomePage() {
			if (this.$route.path === '/') {
				return true
			} else {
				return false
			}
		}
	},
  emits: ['toggle-add-task']
}
</script>

<style scoped>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 20px;
	}
</style>