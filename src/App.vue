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
		<kirby 
			:swallow="isValid"
			:spit="!isValid"
			@animationdone="reset"
		/>
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
			emailText: '',
			isValid: false
		}
	},
	methods: {
		submitMail() {
			if (this.emailValue) {
				this.emailText = this.emailValue;
				this.emailValue = '';
				this.emailIsDisabled = true;
	
				const emailRegex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
				this.isValid = emailRegex.test(this.emailText);
	
				this.$nextTick(this.animateText);
			}
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
		},
		reset() {
			this.emailIsDisabled = false;
			this.isValid = false;
			this.emailText = '';
		}
	}
}
</script>

<style lang="scss">
@import '@/styles/styles';
</style>
