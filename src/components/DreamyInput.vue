<template>
	<div 
		:class="{ disabled }"
		class="dreamy-input"
	>
		<label 
			class="dreamy-input-label"
			for="dreamyInput"
		>Email</label>
		<input 
			id="dreamyInput"
			v-bind="$attrs"
			:aria-describedby="hasError ? 'dreamyInputErr' : null"
			:disabled="disabled"
			:value="modelValue"
			autocomplete="off"
			class="dreamy-input-control"
			type="email"
			@input="$emit('update:modelValue', $event.target.value)"
		>
		<transition name="fade">
			<span 
				v-if="hasError"
				id="dreamyInputErr"
				class="dreamy-input-error"
			>
				Please enter a valid email.
			</span>
		</transition>
		<button
			aria-label="Subscribe"
			class="dreamy-input-button"
			@click="$emit('click')"
		>
			<svg 
				class="dreamy-input-button-svg"
				viewBox="0 0 35 35"
			>
				<path 
					class="dreamy-input-button-star" 
					d="M29.36,23.14l4.63-5.32c2.08-2.39,0.77-6.08-2.39-6.7l-5.23-1.02c-0.23-0.05-0.44-0.19-0.56-0.39l-4.67-7.7 c-1.64-2.69-5.64-2.69-7.27,0l-4.67,7.7c-0.12,0.2-0.33,0.34-0.56,0.39L3.4,11.13c-3.16,0.62-4.47,4.31-2.39,6.7l4.63,5.32 c0.17,0.2,0.24,0.47,0.18,0.73L4.31,29.9c-0.83,3.32,2.61,6.12,5.82,4.74l7.03-3.03c0.22-0.09,0.47-0.09,0.68,0l7.03,3.03 c3.21,1.38,6.65-1.42,5.82-4.74l-1.51-6.04C29.12,23.61,29.18,23.34,29.36,23.14z"
				/>
			</svg>
		</button>
	</div>
</template>

<script>
export default {
	name: 'dreamy-input',
	inheritAttrs: false,
	props: {
		disabled: Boolean,
		hasError: Boolean,
		modelValue: String
	},
	emits: ['click', 'update:modelValue']
}
</script>

<style lang="scss">
.dreamy-input {
	--offset-top: 0.1875rem;
	--offset-left: -0.125rem;
	--control-height: 3.125rem;

	position: relative;

	&::after {
		content: '';
		position: absolute;
		top: var(--offset-top);
		left: var(--offset-left);
		height: 100%;
		width: 100%;
		border: 3px solid var(--black);
		pointer-events: none;
		transition: border 0.5s ease-in-out;
	}

	&::after,
	&-control {
		border-radius: var(--control-height);
	}

	&-control {
		width: 15.625rem;
		height: var(--control-height);
		padding: 0 calc(1rem + var(--control-height)) 0 1rem;
		border: 0;
		background-color: var(--primary-color);
		font-family: $primary-font;
		font-size: 1.25rem;
		color: var(--black);
		caret-color: var(--secondary-color);
		transition: background-color 0.5s ease-in-out;

		&:focus {
			outline: none;
		}

		&:disabled {
			background-color: var(--primary-color-tint);
		}
	}

	&:focus-within {
		&::after {
			border-color: var(--secondary-color);
		}
	}

	&-label,
	&-error {
		position: absolute;
		left: 1rem;
		font-size: 0.75rem;
		letter-spacing: 0.05em;
	}

	&-label {
		top: -0.75rem;
		color: var(--black);
	}

	&-error {
		bottom: -1.5rem;
		color: var(--secondary-color);
	}

	&-button {
		display: grid;
		place-items: center;
		position: absolute;
		top: calc(var(--offset-top) + 3px);
		right: 0;
		height: var(--control-height);
		width: var(--control-height);
		padding: 0;
		border: 0;
		background-color: transparent;
		color: var(--white);
		cursor: pointer;
		transition: 0.4s ease-in-out;

		&-star {
			fill: currentColor;
			stroke: var(--star-stroke, transparent);
			stroke-width: 3px;
		}

		&-svg {
			width: 40%;
			overflow: visible;
		}

		&:focus {
			outline: none;
			color: var(--secondary-color);
		}

		&:hover {
			--star-stroke: var(--black);
			transform: scale(1.2);
			color: var(--accent-color);
		}
	}

	&.disabled {
		&::after {
			border-color: var(--primary-color);
		}

		.dreamy-input-button {
			color: var(--primary-color);
		}
	}
}
</style>