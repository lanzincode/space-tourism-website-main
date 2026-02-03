<script>
	import { page } from '$app/stores';

	let openMenu = $state(false);

	const links = [
		{ href: '/', label: 'HOME', number: '00' },
		{ href: '/destination', label: 'DESTINATON', number: '01' },
		{ href: '/crew', label: 'CREW', number: '02' },
		{ href: '/technology', label: 'TECHNOLOGY', number: '03' }
	];

	let pathname = $derived($page.url.pathname);

	function toggleMenu() {
		openMenu = !openMenu;
	}

	function closeMenu() {
		openMenu = false;
	}
</script>

<header class="header">
	<div class="header__logo">
		<img src="./src/lib/assets/shared/logo.svg" alt="Space Tourism logo" />
	</div>

	<span class="header__line" aria-hidden="true"></span>
	<button
		class="header__toggle"
		aria-controls="primary-navigation"
		aria-expanded={openMenu}
		onclick={toggleMenu}
	>
		<span class="sr-only">Toggle navigation</span>
		<img
			src={openMenu
				? 'src/lib/assets/shared/icon-close.svg'
				: 'src/lib/assets/shared/icon-hamburger.svg'}
			alt=""
			aria-hidden="true"
		/>
	</button>
	<button aria-hidden="true" class="overlay" onclick={closeMenu} data-open={openMenu}></button>
	<nav class="header__nav" aria-label="Primary navigation" data-open={openMenu}>
		<ul class="header__list">
			{#each links as link}
				<li>
					<a
						href={link.href}
						class:active={pathname === link.href}
						onclick={closeMenu}
						aria-current={pathname === link.href ? 'page' : undefined}
					>
						<span aria-hidden="true">{link.number}</span>
						{link.label}
					</a>
				</li>
			{/each}
		</ul>
	</nav>
</header>

<style>
	.header {
		display: grid;
		grid-template-columns: auto 1fr auto;
		align-items: center;
		padding-block-start: var(--space-xl);
		font-family: var(--ff-2);
		color: var(--white);

		@media (width <= 768px) {
			padding: 0;
		}

		@media (width <= 600px) {
			padding-block-start: var(--space-m);
			grid-template-columns: 1fr auto;
		}
	}
	.header__logo {
		margin-inline: var(--space-l);
	}
	.header__logo img {
		width: var(--space-2xl);
	}

	.header__toggle {
		display: none;
		background: none;
		border: none;
		z-index: 1000;
		margin-inline: var(--space-l);

		@media (width <= 600px) {
			display: block;
		}
	}

	.overlay {
		display: none;
	}

	.overlay[data-open='true'] {
		display: block;
		position: fixed;
		width: 100%;
		height: 100%;
		top: 0;
		left: 0;
		z-index: 9;
	}

	.header__toggle img {
		width: var(--space-xl);
	}

	.header__line {
		height: 2px;
		margin-inline-end: -12px;
		background-color: hsl(0 0% 100% / 0.25);
		z-index: 1;
		@media (width <= 768px) {
			display: none;
		}
	}

	.header__nav {
		background: hsl(0 0% 100% / 0.05);
		backdrop-filter: blur(1.5rem);
		padding-inline-start: var(--space-6xl);
		padding-inline-end: var(--space-3xl);
		padding-block: var(--space-l);
		@media (width <= 768px) {
			padding-inline-end: var(--space-l);
		}

		@media (width <= 600px) {
			z-index: var(--z-header);
			position: fixed;
			inset: 0 0 0 30%;
			transform: translateX(100%);
			transition: transform 250ms ease-in-out;
			padding-block-start: var(--space-6xl);
			padding-inline-start: var(--space-xl);
			padding-inline-end: 0;
		}
	}

	.header__nav[data-open='true'] {
		transform: translateX(0);
	}

	.header__list {
		display: flex;
		gap: var(--space-m);
		align-items: center;
		justify-content: space-evenly;
		list-style: none;
		margin: 0;
		@media (width <= 768px) {
			gap: 0;
		}

		@media (width <= 600px) {
			flex-direction: column;
			align-items: flex-start;
			gap: var(--space-2xl);
		}
	}

	.header__list a {
		position: relative;
		letter-spacing: 2px;
		padding-block: var(--space-l);
		@media (width <= 600px) {
			width: 100%;
			font-size: var(--fs-l);
			display: inline-block;
			padding-block: 0;
		}
	}

	.header__list a::after {
		content: '';
		position: absolute;
		bottom: 0;
		height: 3px;
		background: var(--white);
		transform: scaleX(0);
		transform-origin: center;
		transition: all 200ms ease;

		@media (width > 600px) {
			inset-inline: 0;
		}

		@media (width <= 600px) {
			transform-origin: right;
			right: 0;
			height: 100%;
			width: 3px;
			inset-block: 0;
		}
	}

	.header__list li {
		@media (width <= 600px) {
			width: 100%;
		}
	}

	.header__list a span {
		font-weight: 700;
	}

	.header__list a:hover:not(.active)::after,
	.header__list a:focus-visible::after {
		transform: scaleX(1);
		opacity: 0.3;
	}
	.header__list a.active::after {
		transform: scaleX(1);
	}
</style>
