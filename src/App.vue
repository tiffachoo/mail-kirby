<template>
	<main class="container">
		<div class="input-wrap">
			<svg 
				class="cloudy"
				viewBox="0 0 277 145"
			>
				<path 
					class="cloudy-poofs"
					d="M218,20c-0.74,0-1.47,0.03-2.2,0.06C204.99,7.77,189.16,0,171.5,0c-12.22,0-23.58,3.72-33,10.09 C129.08,3.72,117.72,0,105.5,0C87.84,0,72.01,7.77,61.2,20.06C60.47,20.03,59.74,20,59,20C26.42,20,0,46.42,0,79 c0,32.58,26.42,59,59,59c5.26,0,10.36-0.7,15.21-1.99C83.28,141.7,94,145,105.5,145c12.22,0,23.58-3.72,33-10.09 c9.42,6.37,20.78,10.09,33,10.09c11.5,0,22.22-3.3,31.29-8.99c4.85,1.29,9.95,1.99,15.21,1.99c32.58,0,59-26.42,59-59 C277,46.42,250.58,20,218,20z"
				/>
			</svg>
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
				const emailRegex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
				this.isValid = emailRegex.test(this.emailValue);
				this.isNotValid = !this.isValid;

				this.emailText = this.emailValue.length > 15 ?
					this.emailValue.slice(0, 15) + '...' :
					this.emailValue;
				this.emailValue = '';
				this.emailIsDisabled = true;
	
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
