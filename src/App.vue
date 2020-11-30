<template>
	<div class="container">
		<dreamy-input 
			v-model="emailValue" 
			@keydown.enter="submitMail"
		/>
		<kirby />
	</div>
</template>

<script>
import DreamyInput from './components/DreamyInput.vue'
import Kirby from './components/Kirby.vue'

export default {
	name: 'App',
	components: {
		Kirby,
		DreamyInput
	},
	data() {
		return {
			emailValue: ''
		}
	},
	methods: {
		submitMail() {
			console.log(this.emailValue);
		}
	}
}
</script>

<style lang="scss">
@import '@/styles/styles';
</style>
