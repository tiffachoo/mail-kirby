<template>
	<main class="container">
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
				:has-error="isNotValid"
				@keydown.enter="submitMail"
			/>
		</div>
		<kirby 
			:swallow="isValid"
			:spit="isNotValid"
			@animationdone="reset"
		/>
	</main>
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
			isValid: false,
			isNotValid: false
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
				this.isNotValid = !this.isValid;
	
				this.$nextTick(this.animateText);
			}
		},
		animateText() {
			const tlJiggle = gsap.timeline({ 
				delay: 1, 
				defaults: {
					duration: 0.1
				}
			});
			
			tlJiggle
				.to('.input-text-letter', {
					y: 'random(-6, 4)'
				})
				.to('.input-text-letter', {
					y: 'random(-6, 4)'
				})
				.to('.input-text-letter', {
					y: 'random(-6, 4)'
				})
				.to('.input-text-letter', {
					y: 'random(-6, 4)'
				})
				.to('.input-text-letter', {
					y: 0,
					duration: 0.1
				})
				.to('.input-text-letter', {
					delay: 0,
					duration: 0.5,
					ease: 'expo.in',
					x: 300,
					stagger: {
						amount: 0.3,
						from: 'end'
					}
				});
		},
		reset() {
			this.emailIsDisabled = false;
			this.isValid = false;
			this.isNotValid = false;
			this.emailText = '';
		}
	}
}
</script>

<style lang="scss">
@import '@/styles/styles';
</style>
