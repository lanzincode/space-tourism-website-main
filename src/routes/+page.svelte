<section class="home container">
	<div class="home__content">
		<header class="home__header">
			<p class="home__subtitle">SO, YOU WANT TO TRAVEL TO</p>
			<h1 class="home__title">SPACE</h1>
		</header>
		<p class="home__description">
			Let’s face it; if you want to go to space, you might as well genuinely go to outer space and
			not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly
			out of this world experience!
		</p>
	</div>
	<div class="home__cta">
		<a href="/destination" class="home__explore">EXPLORE</a>
	</div>
</section>

<style>
	.home {

		display: grid;
		grid-template-columns: repeat(2, 1fr);
		align-items: center;
		justify-content: center;
		gap: var(--space-4xl);
		@media (width <= 768px) {
			grid-template-columns: 1fr;
			text-align: center;
		}
	}

	.home__subtitle {
		font-size: var(--fs-l);
		font-family: var(--ff-2);

		@media (width <= 600px) {
			font-size: var(--fs-xl);
		}
	}
	.home__title {
		font-size: var(--fs-4xl);
	}

	.home__description {
		text-wrap: balance;
	}

	.home__cta {
		display: grid;
		place-items: center;
	}

	.home__explore {
		position: relative;
		font-size: var(--fs-l);
		font-family: var(--ff-1);
		z-index: 1;
		aspect-ratio: 1;
		padding: var(--space-l);
		color: var(--color-primary-900);
		background-color: var(--white);
		border-radius: var(--radius-full);

		display: inline-grid;
		place-items: center;

		@media (width <= 768px) {
			padding: var(--space-xl);
		}
	}

	.home__explore::after {
		content: '';
		position: absolute;
		z-index: -1;
		width: 100%;
		height: 100%;
		opacity: 0.3;
		background: var(--white);
		border-radius: var(--radius-full);
		transition: transform var(--duration-slow) ease-in-out;
	}

	.home__explore:hover::after,
	.home__explore:focus::after {
		transform: scale(1.5);
	}
</style>
