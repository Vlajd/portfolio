<script>
	import Figure from './Figure.svelte';

	export let type = undefined;
	export let media = true;
	export let items;

	export let lang = undefined;
	export let about_images = undefined;

	$: active_item = 0;
	function changeImg(e) {
		let i = items.length;
		if (e == 1) {
			if (active_item == 0) active_item = i - 1;
			else active_item -= 1;
		} else {
			if (i == active_item + 1) active_item = 0;
			else active_item += 1;
		}
	}
</script>

{#if media}
	<div class='slider rel'>
		{#if type == Figure}
			<svelte:component this={type} image={items[active_item]}/>
			<button style='top:0;left:0' class='arrow arrowLeft' on:click={() => changeImg(1)}>&lsaquo;</button>
			<button style='top:0;right:0' class='arrow arrowRight' on:click={() => changeImg(2)}>&rsaquo;</button>
		{/if}
		{#if type == undefined}
			<svelte:component this={items[active_item]} lang={lang} about_images={about_images}/>
			<button style='bottom:0;left:0'  class='arrow arrowLeft' on:click={() => changeImg(1)}>&lsaquo;</button>
			<button style='bottom:0;right:0' class='arrow arrowRight' on:click={() => changeImg(2)}>&rsaquo;</button>
		{/if}
	</div>
{/if}

<style>
	.arrow {
		background-color: transparent;
		color: rgba(250, 250, 250, 0.9);
		position: absolute;
		width: 70px;
		height: 100%;
		font-size: 7rem;
		border: 0;
		text-shadow: 0 0 6px black;
	}
	button { cursor: pointer }
	.rel {
		position: relative
	}
</style>
