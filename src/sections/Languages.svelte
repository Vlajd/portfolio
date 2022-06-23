<script>
	export let lang;
	export let about_images;
</script>

<!-- Languages -->
<div class='infobox'>
	<figure class='infoboxData'>
		<div style='background-image: url("{about_images[5].image_prev}")' alt='{about_images[1].alt}' class='image'/>
		<div style='background-image: url("{about_images[6].image_prev}")' alt='{about_images[2].alt}' class='image'/>
	</figure>
	<div class='infoboxData'>
		<h4>{lang.Hobbies.elements[2].title}</h4>
		<br>
		<p>{@html lang.Hobbies.elements[2].text}</p>
		<br><br>
		<table>
			<tr>
				<th>Български ({lang.Hobbies.elements[2].langname[0]})</th>
				<th>{lang.Hobbies.elements[2].langlevel[0]}</th>
			</tr>
			<tr>
				<th>Deutsch ({lang.Hobbies.elements[2].langname[1]})</th>
				<th>{lang.Hobbies.elements[2].langlevel[1]}</th>
			</tr>
			<tr>
				<th>English ({lang.Hobbies.elements[2].langname[2]})</th>
				<th>{lang.Hobbies.elements[2].langlevel[1]}</th>
			</tr>
			<tr>
				<th>Letzeburgesch ({lang.Hobbies.elements[2].langname[3]})</th>
				<th>{lang.Hobbies.elements[2].langlevel[2]}</th>
			</tr>
			<tr>
				<th>日本語 ({lang.Hobbies.elements[2].langname[4]})</th>
				<th>{lang.Hobbies.elements[2].langlevel[3]}</th>
			</tr>
			<tr>
				<th>Français ({lang.Hobbies.elements[2].langname[5]})</th>
				<th>{lang.Hobbies.elements[2].langlevel[3]}</th>
			</tr>
		</table>
	</div>
</div>
