<script lang="ts">
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	let tools = ['React', 'Vue', 'Svelte'];
	let i = 0;

	onMount(() => {
		const interval = setInterval(() => {
			i += 1;
			i %= tools.length;
		}, 2000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<p>
	I use {#key i}
		<span in:fly={{ y: 20 }}>{tools[i]}</span>
	{/key}
</p>

<style>
	p {
		font-family: monospace;
		padding-block: 0.5rem;
	}

	span {
		display: inline-block;
	}
</style>
