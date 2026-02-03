<script>
	let { items, activeIndex, onChange } = $props();
</script>

<nav class="dots" aria-label="Crew">
	{#each items as _, index}
		<button
			aria-current={index === activeIndex ? 'true' : undefined}
			class:active={index === activeIndex}
			onclick={() => onChange(index)}
		>
			●
		</button>
	{/each}
</nav>

<style>
	button {
		font-size: 1.5rem;
		background: none;
		border: none;
		cursor: pointer;
		opacity: 0.5;
		margin-right: 1rem;
		transition: 200ms ease;
	}

	button.active {
		opacity: 1;
	}

	button:hover,
	button:focus-visible {
		opacity: 0.8;
	}
</style>
