<script>
    import Figure from './Figure.svelte';
    
    export let media = false;
    export let type = undefined;
	export let images = undefined;
	
    let is_figure = type == Figure;
    let elements;

    $: activeImage = 0;
	function changeImg(e) {
		let i = images.length;
		if (e == 1) {
			if (activeImage == 0)
                activeImage = i - 1;
			else
                activeImage -= 1;
		}
        else {
			if (i == activeImage + 1)
                activeImage = 0;
			else
                activeImage += 1;
		}
	}
</script>

{#if media}
    <div class="slider rel">
        {#if is_figure}
            <svelte:component this={type} image={images[activeImage]} section_tag='projects_figure'/>
        {/if}
    	<button class="arrow arrowLeft" on:click={() => changeImg(1)}>&lsaquo;</button>
    	<button class="arrow arrowRight" on:click={() => changeImg(2)}>&rsaquo;</button>
    </div>
{/if}
{#if !media}
    <span bind:this={elements}><slot/></span>
{/if}

<style>
	.arrow {
		background-color: transparent;
		color: rgba(255, 255, 255, 0.9);
		position: absolute;
		top: 0;
		width: 70px;
		height: 100%;
		font-size: 7rem;
		border: 0;
	}
	.arrowLeft { left: 0 }
	.arrowRight { right: 0 }
	button { cursor: pointer }
	.rel {
		position: relative
	}
</style>