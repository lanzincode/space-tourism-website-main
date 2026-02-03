<script>
	import data from '$lib/data/data.json';
	import Dots from '$lib/components/Dots.svelte';

	let activeIndex = $state(0);
</script>

<section class="crew container">
	<div class="crew__header">
		<h1><span aria-hidden="true">02</span>MEET YOUR CREW</h1>
	</div>
	<div class="crew__content">
		<div class="crew__info">
			<article class="crew__details">
				<h2>{data.crew[activeIndex].role}</h2>
				<h3>{data.crew[activeIndex].name}</h3>
				<p>{data.crew[activeIndex].bio}</p>
			</article>
			<Dots items={data.crew} {activeIndex} onChange={(index) => (activeIndex = index)} />
		</div>
		<div class="crew__image">
			<picture>
				<source srcset={data.crew[activeIndex].images.webp} type="image/webp" />
				<img
					src={data.crew[activeIndex].images.png}
					alt={`Crew ${data.crew[activeIndex].name}`}
					loading="lazy"
				/>
			</picture>
		</div>
	</div>
</section>

<style>
	.crew__content {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: var(--space-m);

		@media (width <= 768px) {
			grid-template-columns: 1fr;
			text-align: center;
		}
	}

	.crew__info {
		display: flex;
		flex-direction: column;
		gap: var(--space-m);
		justify-content: space-evenly;
	}

	.crew__header {
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

	.crew__details {
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

		p {
			text-wrap: balance;
		}
	}

	.crew__image {
		overflow: hidden;
		height: 435px;
		width: 100%;
		max-width: 20rem;
		display: block;
		margin-inline: auto;
	}

	.crew__image img {
		mask-image: linear-gradient(to bottom, var(--color-primary-900) 80%, transparent 100%);
	}
</style>
