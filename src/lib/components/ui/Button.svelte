<script lang="ts">
	// Button Props created as interface for cleanliness of code, rather than inline

	interface ButtonProps {
		variant?: 'primary' | 'secondary' | 'tertiary';
		onClick?: () => void;
		children: any;
	}

	// Variant for Modifier class, onClick and children props passed
	let { variant = 'primary', onClick, children }: ButtonProps = $props();
</script>

<button onclick={onClick} class="Button Button--{variant}">
	{@render children()}
</button>

<style lang="scss">
	@use '../../styles/partials/breakpoints';
	@use '../../styles/partials/mixins';
	@use '../../styles/partials/variables';

	.Button {
		@include mixins.flex($direction: row-reverse, $align: center, $gap: 0.5rem);
		border: none;
		border-radius: 4px;
		cursor: pointer;
		font-size: variables.$font-size--2;
		padding: 0.375rem 0.75rem;
		transition:
			background-color 0.3s ease-in-out,
			color 0.3s ease-in-out;
		width: 100%;

		@include breakpoints.mobile {
			max-width: 10.563rem;
		}

		/* Primary Button */
		&--primary {
			background-color: variables.$button--primary-background-color;
			color: variables.$button--primary-text-color;

			&:hover {
				background-color: variables.$button--primary--hover-background-color;
				border: 2px solid variables.$button--primary-border-color;
				color: variables.$button--primary--hover-text-color;
			}
		}

		/* Secondary Button */
		&--secondary {
			background-color: variables.$button--secondary-background-color;
			color: variables.$button--secondary-text-color;

			&:hover {
				background-color: variables.$button--secondary--hover-background-color;
				border: 2px solid variables.$button--secondary-border-color;
				color: variables.$button--secondary--hover-text-color;
			}
		}

		/* Tertiary Button */
		&--tertiary {
			background-color: variables.$button--tertiary-background-color;
			border: 2px solid variables.$button--tertiary-border-color;
			color: variables.$button--tertiary-text-color;

			&:hover {
				background-color: variables.$button--tertiary--hover-background-color;
				color: variables.$button--tertiary--hover-text-color;
			}
		}
	}
</style>
