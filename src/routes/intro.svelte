<script lang="ts">
	import { tools } from '$lib';
	import { linear } from 'svelte/easing';
	import { fly } from 'svelte/transition';

	export let tool = tools[0];
</script>

<div class="relative w-full min-h-[16px]">
	{#key tool.name}
		<div
			class="flex gap-1 w-full absolute justify-center"
			in:fly={{ y: 20, easing: linear }}
			out:fly={{ y: -20, easing: linear }}
		>
			<img src={tool.iconSrc} alt="" width="16" height="16" />
			<span class="capitalize text-sm font-mono" style="color:{tool.brandColor}"> {tool.name}</span>
		</div>
	{/key}
</div>
