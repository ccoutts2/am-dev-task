<script lang="ts">
	let { href, children, underline }: { href: string; children: any; underline?: boolean } =
		$props();
</script>

<a {href} data-is-hovered={underline} class="NavLink">
	{@render children()}
</a>

<style lang="scss">
	@use '../styles/partials/variables';

	.NavLink {
		color: variables.$color--brand--primary;
		position: relative;

		&[data-is-hovered]:after {
			background-color: variables.$color--brand--primary;
			bottom: 0;
			content: '';
			height: 2px;
			left: 0;
			position: absolute;
			transform-origin: bottom right;
			transform: scaleX(0);
			transition: transform 0.25s ease-out;
			width: 100%;
		}

		&[data-is-hovered]:hover:after {
			transform-origin: bottom left;
			transform: scaleX(1);
		}
	}
</style>
