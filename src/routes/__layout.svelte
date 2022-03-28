<script>
	import SiteFooter from '$lib/components/siteFooter.svelte';
	import SiteHeader from '$lib/components/siteHeader.svelte';
</script>

<SiteHeader />
<main>
	<slot />
</main>
<SiteFooter />

<style>
	main {
		margin-block-start: calc(var(--header-height) + 1.5rem);
		padding-block-end: 3rem;
		padding-inline: 0.75rem;
	}

	@media screen and (min-width: 64rem) {
		main {
			padding-inline: 1.5rem;
		}
	}
</style>
