<script>
	export let lang;
	export let about_images;
</script>

<!-- Music -->
<div class='infobox reverse'>
	<figure class='infoboxData'>
		<iframe width='200%'
				src='https://www.youtube-nocookie.com/embed/aT5iVxysewA?controls=0'
				title='"Fight Of The Spirits", played by Boris Kostadinov'
				frameborder='0'
				allowfullscreen
				style='border-radius:1em'/>
	</figure>
	<div class='infoboxData'>
		<h4>{lang.Hobbies.elements[1].title}</h4>
		<br>
		<p>{@html lang.Hobbies.elements[1].text}
			<a href='../vlajdsheetmusic' target='_blank'><strong>vlajdsheetmusic.com</strong></a>
		</p>
	</div>
</div>
