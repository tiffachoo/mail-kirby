<template>
	<div class="kirby-wrap">
		<svg 
			id="kirby"
			class="kirby"
			viewBox="0 0 200 200"
		>
			<defs>
				<path
					ref="bodySwallow"
					d="M104.29,88c33.94,0,59.29,17.2,59.29,32.58,0,8.34-1.28,14.4-7.69,18.83-7.63,5.27-22.25,7.83-44.7,7.83-2.19,0-4.49,0-6.84-.07-26.18-.55-42.32-3.11-50.8-8.07-7.15-4.19-8.55-10-8.55-18.52C45,105.2,70.36,88,104.29,88m0-3C69.89,85,42,102.59,42,120.58s6,28.42,62.29,29.59q3.58.08,6.9.07c49.89,0,55.39-12.43,55.39-29.66,0-18-27.89-35.58-62.29-35.58Z"
				/>
				<path 
					id="star"
					class="kirby-star" 
					d="M119.43,124.74l4.63-5.32a4.08,4.08,0,0,0-2.39-6.7l-5.23-1a.9.9,0,0,1-.56-.39l-4.67-7.69a4.28,4.28,0,0,0-7.27,0l-4.68,7.69a.85.85,0,0,1-.56.39l-5.23,1a4.09,4.09,0,0,0-2.39,6.7l4.63,5.32a.77.77,0,0,1,.18.72l-1.51,6a4.19,4.19,0,0,0,5.82,4.73l7-3a.89.89,0,0,1,.68,0l7,3a4.19,4.19,0,0,0,5.82-4.73l-1.51-6A.82.82,0,0,1,119.43,124.74Z"
				/>
			</defs>
			<transition-group @enter="animateStar">
				<use 
					v-for="index in starIsVisible"
					:key="`star${index}`"
					href="#star" 
				/>
			</transition-group>
			<g id="legLeft">
				<ellipse 
					class="kirby-foot" 
					cx="90" 
					cy="141.5" 
					rx="23" 
					ry="26"
				/>
				<ellipse 
					class="kirby-stroke" 
					cx="85" 
					cy="141.5" 
					rx="23" 
					ry="26"
				/>
			</g>
			<g 
				id="legRight"
				ref="legRight"
			>
				<ellipse 
					class="kirby-foot" 
					cx="138" 
					cy="134.5" 
					rx="23" 
					ry="26"
				/>
				<ellipse 
					class="kirby-stroke" 
					cx="138" 
					cy="129.5" 
					rx="23" 
					ry="26"
				/>
			</g>
			<g 
				id="armLeft"
				ref="armLeft"
			>
				<circle 
					id="armLeft-2" 
					class="kirby-body" 
					cx="51.5" 
					cy="76" 
					r="20.5"
				/>
				<circle 
					class="kirby-stroke" 
					cx="50.5" 
					cy="82" 
					r="20.5"
				/>
			</g>
			<g 
				id="body"
				ref="body"
			>
				<circle 
					ref="bodyFill"
					class="kirby-body" 
					cx="101.5" 
					cy="95.5" 
					r="57.5"
				/>
				<circle 
					ref="bodyStroke"
					class="kirby-stroke" 
					cx="100.5" 
					cy="91.5" 
					r="57.5"
				/>
			</g>
			<g 
				id="armRight"
				ref="armRight"
			>
				<path 
					class="kirby-body" 
					d="M141,58.73A20.5,20.5,0,1,1,154.68,94.5"
				/>
				<path 
					class="kirby-stroke" 
					d="M136,58.73A20.5,20.5,0,1,1,149.68,94.5"
				/>
			</g>
			<g 
				id="face"
				ref="face"
			>
				<path 
					id="eyeRight"
					ref="eyeRight"
					class="kirby-eye" 
					d="M84,84.53c0,5.8-1.57,9.47-3.5,9.47S77,90.33,77,84.53,78.57,73,80.5,73,84,78.73,84,84.53Z"
				/>
				<path 
					id="eyeLeft"
					ref="eyeLeft"
					class="kirby-eye" 
					d="M68,84.53c0,5.8-1.57,9.47-3.5,9.47S61,90.33,61,84.53,62.57,73,64.5,73,68,78.73,68,84.53Z"
				/>
				<path 
					id="eyeRightClosed" 
					ref="eyeRightClosed" 
					class="kirby-stroke" 
					d="M80.69,125.12c.37-1.41,1.89-3.8,4-6.35a22.84,22.84,0,0,1,5.61-5.14"
				/>
				<path 
					id="eyeLeftClosed" 
					ref="eyeLeftClosed" 
					class="kirby-stroke" 
					d="M55.05,113.61c1.33.61,3.42,2.52,5.56,5.07a23.08,23.08,0,0,1,4.09,6.42"
				/>
				<g ref="cheeks">
					<path 
						id="cheekRight" 
						class="kirby-blush kirby-stroke" 
						d="M93,92.94A22.41,22.41,0,0,1,101.66,89l1.09,5.41s2.74-2.94,8.66-3.93"
					/>
					<path 
						id="cheekLeft" 
						class="kirby-blush kirby-blush-small kirby-stroke" 
						d="M47,92.94A11,11,0,0,1,51.19,89l.52,5.41a8,8,0,0,1,4.19-3.93"
					/>
				</g>
			</g>
			<path 
				id="mouth" 
				ref="mouth"
				class="kirby-stroke" 
				d="M77,98c0,1.93-2.12,3.5-4.5,3.5S68,99.93,68,98"
			/>
			<g 
				id="mouthOpen"
				ref="mouthOpen"
				class="kirby-mouth-open"
			>
				<path class="kirby-stroke kirby-mouth-open-inner" d="M94,105.69c0,14.36-11,23.31-22,23.31s-18-9-18-23.31S61,77,72,77,94,91.33,94,105.69Z"/>
				<path class="kirby-stroke kirby-mouth-open-tongue" d="M72,129a22,22,0,0,0,18.91-11.18C90,109.51,82.8,101.07,74,101.07c-9.39,0-17,9.6-17,18.41,0,.11,0,.21,0,.32A16.16,16.16,0,0,0,72,129Z"/>
			</g>
			<g 
				id="mouthFull"
				ref="mouthFull"
				class="kirby-mouth-full"
			>
				<path 
					class="kirby-stroke" 
					d="M68.45,101.5a6.42,6.42,0,0,1,4-1,7.1,7.1,0,0,1,4,1"
				/>
				<path 
					class="kirby-stroke kirby-mouth-cheek" 
					d="M78.07,106.19a5.17,5.17,0,0,1-1.2-4.75,5.63,5.63,0,0,1,2.76-4.11"
				/>
				<path 
					class="kirby-stroke kirby-mouth-cheek" 
					d="M67,99a4,4,0,0,1,1.5,2.76,4.31,4.31,0,0,1-.46,3.15"
				/>
			</g>
			<path 
				id="mouthFrown" 
				ref="mouthFrown" 
				class="kirby-stroke" 
				d="M70,133.5a2.2,2.2,0,0,1,2-1,2.4,2.4,0,0,1,2,1"
			/>
		</svg>
	</div>
</template>

<script>
import { gsap } from 'gsap';

export default {
	name: 'kirby',
	props: {
		swallow: Boolean,
		inhale: Boolean
	},
	data() {
		return {
			starIsVisible: 0
		};
	},
	watch: {
		swallow() {
			if (this.swallow) {
				this.animateInhale();

				// temp un-disable 
				setTimeout(() => {
					this.$emit('animationdone');
				}, 5000)
			}
		}
	},
	mounted() {
		gsap.set(this.$refs.mouthOpen, {
			transformOrigin: '17px 26px',
			scale: 0
		});

		gsap.set(this.$refs.mouthFull, {
			transformOrigin: 'center center',
			scale: 0
		});

		gsap.set(this.$refs.mouthFrown, {
			transformOrigin: 'center center',
			scaleY: 0
		});

		gsap.set(this.$refs.eyeLeft, {
			transformOrigin: 'center 17px'
		});

		gsap.set(this.$refs.eyeRight, {
			transformOrigin: 'center 17px'
		});

		gsap.set(this.$refs.eyeLeftClosed, {
			transformOrigin: 'center bottom',
			scaleY: 0
		});

		gsap.set(this.$refs.eyeRightClosed, {
			transformOrigin: 'center bottom',
			scaleY: 0
		});

		gsap.set(this.$refs.face, {
			transformOrigin: '25px bottom'
		});

		gsap.set(this.$refs.armLeft, {
			transformOrigin: '70px 42px'
		});

		gsap.set(this.$refs.armRight, {
			transformOrigin: '-35px 44px'
		});

		gsap.set(this.$refs.legRight, {
			transformOrigin: '-13px -6px'
		});

		gsap.set(this.$refs.body, {
			transformOrigin: 'left bottom'
		});
		
		gsap.set(this.$refs.bodyStroke, {
			transformOrigin: 'center bottom'
		});
		
		gsap.set(this.$refs.bodyFill, {
			transformOrigin: 'center bottom'
		});
	},
	methods: {
		animateInhale() {
			const delay = 0.1;
			const tlMouth = gsap.timeline();
			tlMouth
				.to(this.$refs.mouth, {
					duration: delay,
					scale: 0
				})
				.to(this.$refs.mouthOpen, {
					duration: 0.5,
					scale: 1
				});

			gsap.to(this.$refs.face, {
				delay,
				duration: 0.5,
				rotation: 5,
				y: -20
			});

			gsap.to(this.$refs.armLeft, {
				delay,
				duration: 0.7,
				rotation: 80
			});

			gsap.to(this.$refs.armRight, {
				delay,
				duration: 0.7,
				rotation: -15
			});

			gsap.to(this.$refs.legRight, {
				delay: delay + 1,
				duration: 1,
				rotation: -15,
				onComplete: this.animatePuffed
			});
		},
		animatePuffed() {
			const tlMouth = gsap.timeline();
			tlMouth
				.to(this.$refs.mouthOpen, {
					duration: 0.5,
					scale: 0
				})
				.to(this.$refs.mouthFull, {
					duration: 0.3,
					scale: 1
				});

			gsap.to(this.$refs.face, {
				duration: 0.5,
				rotate: 0,
				y: 0
			});

			gsap.to(this.$refs.body, {
				duration: 1.5,
				ease: 'elastic',
				scale: 1.1
			});

			gsap.to(this.$refs.armRight, {
				duration: 1.5,
				ease: 'elastic',
				rotation: 0,
				x: 10,
				onComplete: this.animateSwallow
			});

			gsap.to(this.$refs.armLeft, {
				duration: 0.3,
				rotate: 0
			});

			gsap.to(this.$refs.legRight, {
				duration: 0.6,
				rotation: 0,
				y: 10
			});
		},
		animateSwallow() {
			const tlEyes = gsap.timeline();
			const tlMouth = gsap.timeline();
			const dur = {
				// delay: -0.2,
				duration: 0.8,
				ease: 'elastic'
			};

			tlEyes
				.to([this.$refs.eyeLeft, this.$refs.eyeRight], {
					duration: 0.1,
					scaleY: 0
				})
				.to([this.$refs.eyeLeftClosed, this.$refs.eyeRightClosed], {
					duration: 0.2,
					scaleY: 1
				});

			tlMouth
				.to(this.$refs.mouthFull, {
					duration: 0.1,
					scaleY: 0,
					y: 35
				})
				.to(this.$refs.mouthFrown, {
					duration: 0.1,
					scaleY: 1,
					onComplete: () => { 
						this.starIsVisible = 2;
					}
				});

			gsap.to(this.$refs.cheeks, {
				...dur,
				y: 40
			});

			gsap.to([this.$refs.bodyStroke, this.$refs.bodyFill], {
				...dur,
				// morphSVG: this.$refs.bodySwallow,
				scaleY: 0.57,
				onComplete: this.animatePowerUp
			});

			gsap.to(this.$refs.body, {
				...dur,
				scale: 1
			});

			gsap.to(this.$refs.armLeft, {
				...dur,
				rotation: 70,
				y: 50
			});

			gsap.to(this.$refs.armRight, {
				...dur,
				rotation: -50,
				x: 0,
				y: 50
			});
		},
		animatePowerUp() {
			this.animateReset();
		},
		animateReset() {
			const tlEyes = gsap.timeline();
			const tlMouth = gsap.timeline();
			const dur = {
				delay: 0.2,
				duration: 1,
				ease: 'elastic',
			};

			tlEyes
				.to([this.$refs.eyeLeftClosed, this.$refs.eyeRightClosed], {
					delay: 0.2,
					duration: 0.1,
					scaleY: 0
				})
				.to([this.$refs.eyeLeft, this.$refs.eyeRight], {
					duration: 0.3,
					scaleY: 1
				});

			tlMouth
				.to(this.$refs.mouthFrown, {
					delay: 0.2,
					duration: 0.1,
					scaleY: 0,
					y: -35
				})
				.to(this.$refs.mouth, {
					duration: 0.1,
					scale: 1
				});

			gsap.to(this.$refs.cheeks, {
				...dur,
				y: 0
			});
			
			gsap.to([this.$refs.bodyStroke, this.$refs.bodyFill], {
				...dur,
				scaleY: 1
			});

			gsap.to(this.$refs.armLeft, {
				...dur,
				rotation: 0,
				y: 0
			});

			gsap.to(this.$refs.armRight, {
				...dur,
				rotation: 0,
				y: 0
			});

			gsap.to(this.$refs.legRight, {
				y: 0
			});
		},
		animateStar(el, done) {
			const tl = gsap.timeline({ onComplete: done });

			gsap.set(el, {
				scale: 0,
				transformOrigin: 'center center'
			});

			tl
				.to(el, {
					delay: 'random(0, 0.5)',
					duration: 0.6,
					rotation: 500,
					scale: 1,
					x: 'random(-120, 120)',
					y: 'random(-120, -50)'
				})
				.to(el, {
					duration: 1,
					ease: 'elastic',
					opacity: 0,
					scale: 2
				});
		}
	}
}
</script>

<style lang="scss">
.kirby {
	display: inline-block;
	height: 12.5rem;
	width: 12.5rem;
	overflow: visible;

	&-stroke {
		stroke: var(--black);
		stroke-width: 3px;
		stroke-miterlimit: 10;
		stroke-linecap: round;
		stroke-linejoin: round;
		fill: none;
	}

	&-body {
		fill: var(--primary-color);
	}

	&-mouth-open-tongue,
	&-foot {
		fill: var(--secondary-color);
	}

	&-mouth-open-inner,
	&-eye {
		fill: var(--black);
	}

	// &-mouth,
	// &-mouth-open {
	// 	transform-origin: 72.5px 101.5px !important;
	// }

	&-blush {
		stroke: var(--secondary-color);
	}

	&-blush-small {
		stroke-width: 2.5px;
	}

	// &-arm {
		// transform-origin: 101px 98px !important;
	// }

	// &-face {
		// transform-origin: 80px 83px !important;
	// }

	&-star {
		fill: var(--accent-color);
	}
}
</style>