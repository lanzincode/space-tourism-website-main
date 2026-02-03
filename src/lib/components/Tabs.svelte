<script>
	let { items, activeIndex, onChange } = $props();
</script>

<nav class="tabs" aria-label="Destinations">
	{#each items as item, index}
		<button
			aria-current={activeIndex === index ? 'true' : undefined}
			class:active={index === activeIndex}
			onclick={() => onChange(index)}
		>
			{item.name}
		</button>
	{/each}
</nav>

<style>
	.tabs {
		display: flex;
		gap: var(--space-m);
		font-family: var(--ff-2);
		font-size: var(--fs-m);
		margin-bottom: var(--space-m);
	}

	.tabs button {
		position: relative;
		text-transform: uppercase;
	}

	.tabs button::after {
		content: '';
		position: absolute;
		bottom: 0;
		inset-inline: 0;
		height: 3px;
		background: var(--white);
		transform: scaleX(0);
		transform-origin: center;
		transition: all 200ms ease;
	}

	.tabs button:focus-visible::after,
	.tabs button:hover:not(.active)::after {
		transform: scaleX(1);
		opacity: 0.3;
	}

	.tabs button.active::after {
		transform: scaleX(1);
	}
</style>
