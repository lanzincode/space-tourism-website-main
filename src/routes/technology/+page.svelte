<script>
	import data from '$lib/data/data.json';
	import NumberedTabs from '$lib/components/NumberedTabs.svelte';

	let activeIndex = $state(0);
</script>

<section class="technology">
	<div class="technology__header">
		<h1><span aria-hidden="true">03</span>SPACE LAUNCH 101</h1>
	</div>
	<div class="technology__content">
		<div class="technology__info">
			<NumberedTabs
				items={data.technology}
				{activeIndex}
				onChange={(index) => (activeIndex = index)}
			/>
			<article class="technology__details">
				<h2>THE TERMINOLOGY...</h2>
				<h3>{data.technology[activeIndex].name}</h3>
				<p>{data.technology[activeIndex].description}</p>
			</article>
		</div>
		<div class="technology__image">
			<picture>
				<source
					srcset={data.technology[activeIndex].images.landscape}
					type="image/jpeg"
					media="(max-width: 768px)"
				/>
				<img
					src={data.technology[activeIndex].images.portrait}
					alt={`Photo of the ${data.technology[activeIndex].name}`}
				/>
			</picture>
		</div>
	</div>
</section>

<style>
	.technology {
		padding-inline-start: 10%;

		@media (width <= 768px) {
			padding-inline-start: 0%;
		}
	}

	.technology__content {
		text-wrap: balance;

		display: grid;
		grid-template-columns: 1fr auto;
		align-items: center;

		@media (width <= 768px) {
			grid-template-columns: 1fr;
			text-align: center;
		}
	}

	.technology__info {
		display: grid;
		grid-template-columns: auto 1fr;

		@media (width <= 768px) {
			grid-template-columns: 1fr;
		}
	}

	.technology__header {
		font-size: var(--fs-l);
		margin-block: var(--space-s);

		h1 {
			font-family: var(--ff-2);
		}

		span {
			font-family: var(--ff-3);
			font-weight: var(--fw-bold);
			opacity: 0.5;
			margin-inline-end: var(--space-m);
		}

		@media (width <= 768px) {
			padding-inline: 0;
			text-align: center;
		}
	}

	.technology__details {
		h2 {
			text-transform: uppercase;
			color: var(--color-primary-200);
			font-size: var(--fs-l);
		}

		h3 {
			margin-block-end: var(--space-m);
			text-transform: uppercase;
			font-size: var(--fs-2xl);
		}
	}

	.technology__image {
		margin-inline: auto;

		@media (width <= 768px) {
			order: -1;
		}
	}

	.technology__image img {
		height: 440px;

		@media (width <= 768px) {
			height: auto;
		}
	}
</style>
