<script>
	import { tools } from '$lib';
	import { onMount } from 'svelte';
	import Intro from './intro.svelte';
	import { fade } from 'svelte/transition';

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

	$: tool = tools[i];
</script>

<div class="relative z-0 h-screen flex flex-col items-center justify-center bg-pink-200">
	<div class="bg-white/80 w-1/2 max-w-xs shadow-sm rounded-lg backdrop-blur-3xl px-3 pt-3 pb-4">
		<div class="flex flex-col items-center justify-center">
			<h1 class="text-3xl">👨‍💻</h1>
			<span class="text-xs text-zinc-600 my-3">Frontend Developer</span>
			<Intro {tool} />
		</div>
	</div>
	{#key tool.iconSrc}
		<div
			class="absolute inset-0 -z-10"
			style:background="radial-gradient({tool.brandColor}, white)"
			transition:fade
		/>
		<img
			src={tool.iconSrc}
			alt=""
			class="object-contain blur-lg absolute -z-10 w-3/4 h-auto max-w-2xl"
			transition:fade
		/>
	{/key}
</div>
