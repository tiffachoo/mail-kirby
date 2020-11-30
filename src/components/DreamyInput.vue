<template>
	<div class="dreamy-input">
		<input 
			:value="modelValue"
			class="dreamy-input-control"
			type="text"
			@input="$emit('update:modelValue', $event.target.value)"
		>
	</div>
</template>

<script>
export default {
	name: 'dreamy-input',
	props: {
		modelValue: String
	}
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
		width: 100%;
		height: 3.125rem;
		padding: 0 1rem;
		border: 0;
		background-color: var(--white);
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
}
</style>