<script>
	import data from '$lib/data/data.json';
	import Tabs from '$lib/components/Tabs.svelte';

	let activeIndex = $state(0);
</script>

<section class="destination container">
	<div class="destination__header">
		<h1><span aria-hidden="true">01</span>PICK YOUR DESTINATION</h1>
	</div>
	<div class="destination__content">
		<div class="destination__image">
			<picture>
				<source srcset={data.destinations[activeIndex].images.webp} type="image/webp" />
				<img
					src={data.destinations[activeIndex].images.png}
					alt={`${data.destinations[activeIndex].name} image`}
					loading="lazy"
				/>
			</picture>
		</div>
		<div class="destination__info">
			<Tabs items={data.destinations} {activeIndex} onChange={(index) => (activeIndex = index)} />
			<article class="destination__details">
				<h2>{data.destinations[activeIndex].name}</h2>
				<p>{data.destinations[activeIndex].description}</p>
				<div class="destination__meta">
					<div>
						<h3>AVG. DISTANCE</h3>
						<p>{data.destinations[activeIndex].distance}</p>
					</div>
					<div>
						<h3>EST. TRAVEL TIME</h3>
						<p>{data.destinations[activeIndex].travel}</p>
					</div>
				</div>
			</article>
		</div>
	</div>
</section>

<style>

	.destination__content {
		display: grid;
		grid-template-columns: repeat(2, 1fr);

		@media (width <= 768px) {
			padding-block: 0;
			grid-template-columns: 1fr;
			text-align: center;
		}
	}

	.destination__image {
		margin: 0 auto;

		img {
			max-width: 80%;
			margin: 0 auto;
			padding-block: var(--space-m);
		}
	}

	.destination__header {
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

	.destination__info {
		display: grid;

		@media (width <= 768px) {
			justify-items: center;
		}
	}

	.destination__details {
		h2 {
			font-size: var(--fs-3xl);
			text-transform: uppercase;
		}
	}
	.destination__details > p {
		text-wrap: balance;
		padding-block-end: var(--space-m);
		border-bottom: 2px solid hsl(255 100 100 / 0.3);
		padding-inline-end: var(--space-s);

		@media (width <= 600px) {
			padding-inline-end: 0;
		}
	}

	.destination__meta {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		padding-block-start: var(--space-m);

		h3 {
			font-family: var(--ff-2);
			color: var(--color-primary-200);
		}

		p {
			font-family: var(--ff-1);
			font-size: var(--fs-l);
			color: var(--white);
			text-transform: uppercase;
		}
	}
</style>
