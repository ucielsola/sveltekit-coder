<script>
	import SiteNavigation from './siteNavigation.svelte';
</script>

<header>
	<h1>Uciel Sola - Tutorial SvelteKit</h1>
	<SiteNavigation />
</header>

<style>
	header {
		position: fixed;
		top: 0;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		align-items: center;
		justify-content: start;
		width: calc(100% - 3rem);
		margin: 1rem 0;
		height: var(--header-height);
		padding-inline: 1rem;
		background-color: var(--base-color-200);
		border-radius: 1rem;
		box-shadow: var(--shadow);
	}
	h1 {
		display: none;
	}

	@media screen and (min-width: 64rem) {
		h1 {
			display: inline;
			font-size: 2rem;
			font-weight: 700;
		}
	}
</style>
