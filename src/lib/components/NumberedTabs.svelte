<script>
	let { items, activeIndex, onChange } = $props();
</script>

<nav class="numberedTabs" aria-label="Technology">
	{#each items as _, index}
		<button
			aria-current={index === activeIndex ? 'true' : undefined}
			class:active={index === activeIndex}
			onclick={() => onChange(index)}
		>
			{index + 1}
		</button>
	{/each}
</nav>

<style>
	.numberedTabs {
		margin-inline-end: var(--space-m);

		display: flex;
		flex-direction: column;
		justify-content: space-evenly;

		@media (width <= 768px) {
			margin-inline-end: 0;
			margin-block: var(--space-s);
			justify-content: center;
			flex-direction: row;
			gap: var(--space-m);
		}
	}

	button {
		font-family: var(--ff-1);
		width: var(--space-2xl);
		height: var(--space-2xl);
		border-radius: 50%;
		border: 1px solid var(--white);
		background: none;
		cursor: pointer;

		display: inline-grid;
		place-items: center;
	}

	button.active {
		background: var(--white);
		color: var(--color-primary-900);
	}
</style>
