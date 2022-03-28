<script>
	import { page } from '$app/stores';
	export let href;
	export let title;
	export let text;
</script>

<a {href} {title} class:active={$page.url.pathname === href}>{text}</a>

<style>
	a {
		text-decoration: none;
		font-weight: 600;
		color: var(--text-color);
        transition: all 0.2s ease-in-out;
	}

	a:hover {
		color: var(--highlight-color);
	}

	a.active {
		text-decoration: underline;
		color: var(--highlight-color);
	}
</style>
