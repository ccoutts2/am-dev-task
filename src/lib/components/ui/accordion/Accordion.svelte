<script lang="ts">
	import type { AccordionData } from '../../../fixtures/accordionData';
	import AccordionItem from './AccordionItem.svelte';

	// Pass accordionData and name as props into this component
	let { accordionData, name }: { accordionData: AccordionData[]; name?: string } = $props();
</script>

<!-- Best case not using aria role - better to use semantics -->
<div class="Accordion">
	{#each accordionData as { title, content }}
		<AccordionItem {title} {content} {name} />
	{/each}
</div>

<style lang="scss">
	@use '../../../styles/partials/mixins';

	.Accordion {
		@include mixins.flex($direction: column, $gap: 0.25rem);
	}
</style>
