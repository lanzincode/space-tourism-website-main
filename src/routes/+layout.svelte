<script>
	import Header from '$lib/components/Header.svelte';
	import { page } from '$app/stores';

	import '$lib/styles/tokens.css';
	import '$lib/styles/base.css';
	import '$lib/styles/layout.css';

	let pathname = $derived($page.url.pathname);
</script>

<svelte:head>
	<link rel="icon" href="/assets/favicon-32x32.png" />
</svelte:head>

<div class="page" data-route={pathname}>
	<Header />
	<main class="layout">
		<slot />
	</main>
</div>
