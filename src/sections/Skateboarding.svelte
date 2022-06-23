<script>
	export let lang;
	export let about_images;
</script>

<!-- Skateboarding -->
<div class='infobox'>
    <figure class='infoboxData'>
        <div style='background-image: url("{about_images[1].image_prev}")' alt='{about_images[1].alt}' class='image'/>
        <div style='background-image: url("{about_images[2].image_prev}")' alt='{about_images[2].alt}' class='image'/>
    </figure>
    <div class='infoboxData'>
        <h4>{lang.Hobbies.elements[0].title}</h4>
        <br>
        <p>{@html lang.Hobbies.elements[0].text}</p>
    </div>
</div>

<style src='./hobbies.css'></style>
