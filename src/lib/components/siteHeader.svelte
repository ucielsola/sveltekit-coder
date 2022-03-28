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
		display: flex;
		align-items: center;
		justify-content: start;
		width: 100%;
		height: var(--header-height);
		padding-inline: 1rem;
        background-color: var(--darker-base-color);
		border-bottom: 1px solid var(--text-color);
		box-shadow: var(--shadow);
	}
    h1 {
        font-size: 2rem;
        font-weight: 700;
    }
</style>
