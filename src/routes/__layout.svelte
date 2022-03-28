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
		margin-block-start: var(--header-height);
		min-height: 300vh;
	}
</style>
