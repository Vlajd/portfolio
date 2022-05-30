<script>
	export let images;
	$: activeImage = 0;
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

<div class="slider rel">
    <figure>
	    <div class="bgw image" style='background-image: url("{images[activeImage].image_prev}")' alt={images[activeImage].alt}/>
        <figcaption>{images[activeImage].caption}</figcaption>
    </figure>
	<button class="arrow arrowLeft" on:click={() => changeImg(1)}>&lsaquo;</button>
	<button class="arrow arrowRight" on:click={() => changeImg(2)}>&rsaquo;</button>
</div>

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
	.bgw {
		background-image: url('{images[activeImage].image_prev}');
        min-height: 40vh;
	}
</style>