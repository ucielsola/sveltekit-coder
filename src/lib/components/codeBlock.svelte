<script>
	export let text;
</script>

<pre>
    <code>
        {text}
    </code>
</pre>

<style>
	pre {
		display: grid;
		margin-block: 0.5rem;
	}
	code {
		display: block;
		background: var(--base-color-200);
		white-space: pre;
		-webkit-overflow-scrolling: touch;
		overflow-x: auto;
		max-width: 100%;
		min-width: 100px;
		padding: 0;
		font-family: monospace;
		border-radius: 1rem;
		box-shadow: var(--shadow);
	}
</style>
