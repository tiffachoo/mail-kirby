<template>
	<div class="dreamy-input">
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
	emits: ['update:modelValue']
}
</script>

<style lang="scss">
.dreamy-input {
	position: relative;

	&::after {
		content: '';
		position: absolute;
		top: 3px;
		left: -2px;
		height: 100%;
		width: 100%;
		border: 3px solid var(--black);
		pointer-events: none;
		transition: border 0.4s ease-in-out;
	}

	&::after,
	&-control {
		border-radius: 3.125rem;
	}

	&-control {
		width: 12.5rem;
		height: 3.125rem;
		padding: 0 1rem;
		border: 0;
		background-color: var(--primary-color);
		font-family: $primary-font;
		font-size: 1.25rem;
		color: var(--black);
		caret-color: var(--secondary-color);

		&:focus {
			outline: none;
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
}
</style>