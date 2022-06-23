<script>
	export let lang;
	export let about_images;
</script>

<!-- Programming -->
<div class='infobox reverse'>
	<figure class='infoboxData'>
		<div style='background-image: url("{about_images[7].image_prev}")' alt='{about_images[1].alt}' class='image'/>
		<div style='background-image: url("{about_images[8].image_prev}")' alt='{about_images[2].alt}' class='image'/>
	</figure>
	<div class='infoboxData'>
		<h4>{lang.Hobbies.elements[3].title}</h4>
		<br>
		<p>{@html lang.Hobbies.elements[3].text}</p>
	</div>
</div>
