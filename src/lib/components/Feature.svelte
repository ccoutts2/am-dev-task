<script lang="ts">
	import Accordion from './ui/accordion/Accordion.svelte';
	import Button from './ui/Button.svelte';

	import { accordionData } from '../fixtures/accordionData';
</script>

<div class="Feature">
	<div class="Feature__Layout">
		<section class="Feature__Information">
			<div class="Text">
				<h2 class="Text__Header">Modern & verstaile HubSpot theme</h2>
				<p class="Text__Paragraph">
					Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt
					ut labore et.
				</p>

				<Button variant="secondary">
					<span>Call to action</span>
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
			</div>

			<Accordion {accordionData} name="accordion" />
		</section>

		<div class="Feature__ImageContainer">
			<!-- Exported images as jpg and compressed for better loading -->
			<img
				srcset="
						images/am-image-low.jpg 576w, 
						images/am-image-medium.jpg 768w, 
						images/am-image-high.jpg 1200w"
				sizes="(max-width: 36rem) 576px, 
						(max-width: 48rem) 768px, 
						1200px"
				src="images/am-image-high.jpg"
				alt="A woman sitting on a modern chair in a brightly lit apartment room, wearing casual clothes, while working on a MacBook."
			/>
		</div>
	</div>
</div>

<style lang="scss">
	@use '../styles/partials/breakpoints';
	@use '../styles/partials/mixins';
	@use '../styles/partials/variables';

	.Feature {
		background: variables.$color--brand--primary;
		min-height: 50vh;

		&__Layout {
			@include mixins.flex($direction: column-reverse, $align: stretch, $gap: 2rem);
			@include mixins.max-content(variables.$content--max-width--lg);
			margin: 0 auto;
			padding-block: 3rem;

			@include breakpoints.tablet {
				@include mixins.flex($direction: row-reverse, $justify: space-between, $gap: 3rem);
				padding: 5.75rem 4rem;
			}

			@include breakpoints.desktop {
				gap: 7.74rem;
			}
		}

		&__Information {
			@include mixins.flex($direction: column, $justify: space-between, $gap: 2rem);
			padding-inline: 1rem;

			@include breakpoints.tablet {
				gap: 3rem;
			}

			@include breakpoints.desktop {
				gap: 8.5rem;
			}

			flex: 1;
		}

		&__ImageContainer {
			aspect-ratio: 1.4;
			flex: 1.4;

			img {
				height: 100%;
				object-fit: cover;
				width: 100%;
			}
		}
	}

	.Text {
		@include mixins.flex($direction: column, $gap: 2rem);

		&__Header {
			max-width: 25.25rem;
			font-size: clamp(variables.$font-size--6, 10vw, variables.$font-size--7);
			font-weight: 400;
		}

		&__Paragraph {
			line-height: 1.5rem;
			max-width: 25.875rem;
		}
	}
</style>
