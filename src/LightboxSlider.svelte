<script>
	export let images;
	$: activeImage = 0;
	let active;
	function showImg(e) {
		activeImage = e;
		active = 1;
	}
	function changeImg(e) {
		let i = images.length;
		if (e == 1) {
			if (activeImage == 0) activeImage = i - 1;
			else activeImage -= 1;
		} else {
			if (i == activeImage + 1) activeImage = 0;
			else activeImage += 1;
		}
	}
</script>

{#if images}

	{#if active}
		<div id="overlay" class="grid cell">
			<div id="overlayImage" class="rel">
                <figure>
				    <div class="bgw image" style='background-image: url("{images[activeImage].image_prev}")' alt={images[activeImage].alt}></div>
				    <figcaption>{images[activeImage].caption}</figcaption>
                </figure>
                <button class="abs arrow arrowLeft white noBor" on:click={() => changeImg(1)}>&lsaquo;</button>
				<button class="abs arrow arrowRight white noBor" on:click={() => changeImg(2)}>&rsaquo;</button>
				<button id="close" class="abs bold bgw" on:click={() => (active = '')}>X</button>
			</div>
		</div>
	{/if}

	<div id="img">
		<div id="bigImg">
            <figure>
			    <div class='image' style='background-image: url("{images[activeImage].image_prev}")' alt={images[activeImage].alt} on:click={() => showImg(0)}/>
                <figcaption>{images[activeImage].caption}</figcaption>
            </figure>
		</div>
		{#if images[1]}
			<div id="mini" class="grid">
				{#each images as item, i}
					{#if i > 0}
                        <figure>
						    <div  class='image' style='background-image: url("{item.image_prev}")' alt={item.alt} on:click={() => showImg(i)}/>
                            <figcaption>{images[activeImage].caption}</figcaption>
                        </figure>
					{/if}
				{/each}
			</div>
		{/if}
	</div>

{/if}

<style>
	#overlay {
		display: grid;
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		z-index: 1350;
		background-color: rgba(255,255,255,.8)
	}
	#overlay div,
	#overlay #close { border: 1px solid #999 }
	#overlay div {
		max-height: 95vh;
		padding: .5rem
	}
	#overlay button {
		z-index: 2000
	}
	#overlay #close {
		top: 1rem;
		right: 1rem;
		width: 32px;
		height: 32px;
		font-size: 1.2rem
	}
	#overlay .arrow {
		top: 0;
		width: 70px;
		height: 100%;
		font-size: 7rem
	}
	#overlay .arrowLeft { left: 0 }
	#overlay .arrowRight { right: 0 }
	button,
	.rel {
		position: relative
	}
	.abs {
		position: absolute
	}
	.bgw {
		background-color: #fff
	}
	.white {
		color: #fff
	}
	.noBor {
		background-color: transparent
	}
</style>