<script>
	import NavLink from './navLink.svelte';
</script>

<nav>
	<NavLink href="/" title="Inicio" text="Inicio" />
	<NavLink href="/tutorial" title="Tutorial" text="Tutorial" />
	<NavLink href="/acerca-de" title="Sobre mí" text="Sobre mí" />
</nav>

<style>
	nav {
		display: flex;
		align-items: center;
		justify-content: space-evenly;
		width: clamp(320px, 10rem, 50vw);
	}
</style>
