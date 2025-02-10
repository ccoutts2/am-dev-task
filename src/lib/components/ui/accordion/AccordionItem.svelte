<script lang="ts">
	import { slide } from 'svelte/transition';

	//  Pass title & content from accordionData, and name as props
	let { title, content, name }: { title: string; content: string; name?: string } = $props();

	// Provide special properties to the details element, for animating
	let details: HTMLDetailsElement | undefined = $state();

	// No accordion items have been toggled
	let toggled = $state(false);

	// Toggle Accordion items state
	const toggleAccordion = (event: Event) => {
		// Prevent default toggling behaviour for purposes of managing animation
		event.preventDefault();

		// Targetting open property of details element
		// Details will never be null - use of non-null assertion operator
		if (!details?.open) {
			details!.open = true;
			toggled = true;
		} else {
			toggled = false;
			details!.open = false;
		}
	};
</script>

<details {name} class="AccordionItem" bind:open={toggled} bind:this={details}>
	<summary class="AccordionItem__Header" onclick={toggleAccordion}>
		<span class="AccordionItem__Title">
			{title}
		</span>
		<span class="AccordionItem__Icon">
			<svg
				aria-hidden="true"
				width="20"
				height="20"
				viewBox="0 0 20 20"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M6 10H14M10 6V14M3 1H17C18.1046 1 19 1.89543 19 3V17C19 18.1046 18.1046 19 17 19H3C1.89543 19 1 18.1046 1 17V3C1 1.89543 1.89543 1 3 1Z"
					stroke="white"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
		</span>
	</summary>
	{#if toggled}
		<p class="AccordionItem__Content" transition:slide={{ duration: 500 }}>
			{content}
		</p>
	{/if}
</details>

<style lang="scss">
	@use '../../../styles/partials/mixins';
	@use '../../../styles/partials/variables';

	.AccordionItem {
		@include mixins.flex($direction: column);

		&[open] {
			block-size: auto;
		}

		svg {
			display: flex;
		}

		&__Header {
			@include mixins.flex($justify: space-between, $align: center);
			border-bottom: 1px solid variables.$color--line-divider;
			cursor: pointer;
			// Hide marker on Firefox
			list-style-type: none;
			margin-inline: -0.5rem;
			padding-block: 0.5rem;
			padding-inline: 0.5rem;
			transition: background-color 0.2s ease-out;
			position: relative;

			// Hide marker on Chrome & future proof
			&::-webkit-details-marker,
			&::marker {
				display: none;
			}

			&::before {
				content: '';
				display: block;
				inset: 0 -0.5rem;
				position: absolute;
			}

			&:hover::before {
				background-color: variables.$color--accordion-hover;
			}
		}

		&__Title {
			font-weight: 500;
			margin: 0;
			padding-block: 0.25rem;
			z-index: 10;
		}

		&__Icon {
			z-index: 10;
		}

		&__Content {
			padding-block: 0.5rem;
		}
	}
</style>
