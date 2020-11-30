<template>
	<div class="kirby-wrap">
		<svg 
			id="kirby"
			class="kirby"
			viewBox="0 0 200 200"
		>
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
			<g id="legRight">
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
			<g id="armLeft">
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
			<g id="body">
				<circle 
					class="kirby-body" 
					cx="101.5" 
					cy="95.5" 
					r="57.5"
				/>
				<circle 
					class="kirby-stroke" 
					cx="100.5" 
					cy="91.5" 
					r="57.5"
				/>
			</g>
			<g id="armRight">
				<path 
					class="kirby-body" 
					d="M141,58.73A20.5,20.5,0,1,1,154.68,94.5"
				/>
				<path 
					class="kirby-stroke" 
					d="M136,58.73A20.5,20.5,0,1,1,149.68,94.5"
				/>
			</g>
			<g id="face">
				<path 
					id="eyeRight"
					class="kirby-eye" 
					d="M84,84.53c0,5.8-1.57,9.47-3.5,9.47S77,90.33,77,84.53,78.57,73,80.5,73,84,78.73,84,84.53Z"
				/>
				<path 
					id="eyeLeft"
					class="kirby-eye" 
					d="M68,84.53c0,5.8-1.57,9.47-3.5,9.47S61,90.33,61,84.53,62.57,73,64.5,73,68,78.73,68,84.53Z"
				/>
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
			<path 
				id="mouth" 
				class="kirby-stroke" 
				d="M77,98c0,1.93-2.12,3.5-4.5,3.5S68,99.93,68,98"
			/>
		</svg>
	</div>
</template>

<script>
export default {
	name: 'kirby'
}
</script>

<style lang="scss">
.kirby {
	display: inline-block;
	height: 12.5rem;
	width: 12.5rem;

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

	&-foot {
		fill: var(--secondary-color);
	}

	&-eye {
		fill: var(--black);
	}

	&-blush {
		stroke: var(--secondary-color);
	}

	&-blush-small {
		stroke-width: 2.5px;
	}
}
</style>