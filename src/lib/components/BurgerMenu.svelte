<script lang="ts">
	import { sineInOut } from 'svelte/easing';
	import NavLink from './NavLink.svelte';
	import Button from './ui/Button.svelte';
	import { fade } from 'svelte/transition';
</script>

<menu class="BurgerMenu" transition:fade={{ duration: 500, delay: 250, easing: sineInOut }}>
	<li>
		<NavLink href="/" underline>Home</NavLink>
	</li>
	<li>
		<NavLink href="/" underline>Services</NavLink>
	</li>
	<li>
		<NavLink href="/" underline>About</NavLink>
	</li>
	<li>
		<NavLink href="/" underline>Resources</NavLink>
	</li>
	<li>
		<Button>
			<span>Call To Action</span>
			<span>
				<svg
					aria-hidden="true"
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M8 12H16M16 12L12 16M16 12L12 8M5 3H19C20.1046 3 21 3.89543 21 5V19C21 20.1046 20.1046 21 19 21H5C3.89543 21 3 20.1046 3 19V5C3 3.89543 3.89543 3 5 3Z"
						stroke="currentColor"
						stroke-width="2"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg>
			</span>
		</Button>
	</li>
</menu>

<style lang="scss">
	@use '../styles/partials/variables';
	@use '../styles/partials/mixins';

	.BurgerMenu {
		@include mixins.flex($direction: column, $justify: center, $align: center, $gap: 2rem);
		font-size: variables.$font-size--6;
		inset: 0;
		list-style: none;
		position: fixed;
		backdrop-filter: blur(32px);
	}
</style>
