<script lang="ts">
	import '$lib/styles/global.css';
	import NavBar from '$lib/components/NavBar.svelte';

	let { children } = $props();
</script>

<header>
	<NavBar />
</header>

{@render children()}
