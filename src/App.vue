<template>
	<div class="container">
		<div class="input-wrap">
			<div 
				v-if="emailText"
				class="input-text"
			>
				<span 
					v-for="(letter, index) in emailText" 
					:key="index"
					class="input-text-letter"
				>{{ letter }}</span>
			</div>
			<dreamy-input 
				v-model="emailValue" 
				:disabled="emailIsDisabled"
				@keydown.enter="submitMail"
			/>
		</div>
		<kirby />
	</div>
</template>

<script>
import { gsap } from "gsap";
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
			emailValue: '',
			emailIsDisabled: false,
			emailText: ''
		}
	},
	methods: {
		submitMail() {
			this.emailText = this.emailValue;
			this.emailValue = '';
			this.emailIsDisabled = true;

			this.$nextTick(this.animateText);
		},
		animateText() {
			const tl = gsap.timeline({ delay: 1 });
			tl
				.to('.input-text-letter', {
					y: 3,
					duration: 0.05
				})
				.to('.input-text-letter', {
					y: -5,
					duration: 0.05
				})
				.to('.input-text-letter', {
					y: 3,
					duration: 0.1
				})
				.to('.input-text-letter', {
					y: -5,
					duration: 0.1
				})
				.to('.input-text-letter', {
					y: 0,
					duration: 0.1
				})
				.to('.input-text-letter', {
					x: 300,
					duration: 0.5,
					ease: 'expo.in',
					stagger: {
						amount: 0.3,
						from: 'end'
					}
				});
		}
	}
}
</script>

<style lang="scss">
@import '@/styles/styles';
</style>
