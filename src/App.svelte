<script>
    import 'bigger-picture/dist/bigger-picture.css';
    import BiggerPicture from 'bigger-picture/src/bigger-picture.js';
    import { onMount } from 'svelte';
    
    let project_image_source_name = [
        'TrainInRumania.jpg',
        'KissingPigeons.jpg',
        'GlasAndCheese.jpg',
        'Punktechaplin0.jpg',
        'Punktechaplin1.jpg',
        'BurningCastle.jpg'
    ];


    let bp = BiggerPicture({
	    target: document.body,
    });
    let projects_figures = undefined;
    function open_gallery(e) {
    	e.preventDefault()
    	bp.open({
    		items: projects_figures,
    		el: e.currentTarget,
    	})
    }
    function set_project_lightbox() {
        projects_figures = document.querySelectorAll('.projects_figure');
        for (let i = 0; i < projects_figures.length; i++) {
            projects_figures.item(i).addEventListener('click', open_gallery);
        }
    }
    window.addEventListener('load', set_project_lightbox);
    window.addEventListener('resize', () => {
        setTimeout(set_project_lightbox, 500);
    });

    let Module = undefined;
    onMount( async () => Module = (await import('./english/English.svelte')).default );
    // █░░ ▄▀█ █▄░█ █▀▀ █░█ ▄▀█ █▀▀ █▀▀   █▀ █▀▀ █░░ █▀▀ █▀▀ ▀█▀ █▀█ █▀█
    // █▄▄ █▀█ █░▀█ █▄█ █▄█ █▀█ █▄█ ██▄   ▄█ ██▄ █▄▄ ██▄ █▄▄ ░█░ █▄█ █▀▄
    // Visually changes the selected language 
    function selectLang(index) {
        let elements = document.getElementsByClassName('langSelect');
        for (let i = 0; i < elements.length; i++) {
            if (i == index) {
                elements[i].classList.add('underlined');
            }
            else {
                elements[i].classList.remove('underlined');
            }
        }
    }
</script>

<!--
█░░ ▄▀█ █▄░█ █▀▀ █░█ ▄▀█ █▀▀ █▀▀   █▀ █▀▀ █░░ █▀▀ █▀▀ ▀█▀ █▀█ █▀█
█▄▄ █▀█ █░▀█ █▄█ █▄█ █▀█ █▄█ ██▄   ▄█ ██▄ █▄▄ ██▄ █▄▄ ░█░ █▄█ █▀▄
Selects Language and hotswaps Module
DO NOT, AT ANY COST, TOUCH!!!
-->
<div id='Lang'>
    <button class='langSelect underlined' on:click={ () => {
        selectLang(0);
        let fn = async () => Module = (await import('./english/English.svelte')).default;
        fn();
        setTimeout(set_project_lightbox, 500);
    }}>English</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(1);
        let fn = async () => Module = (await import('./german/German.svelte')).default;
        fn();
    }}>Deutsch</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(2);
        let fn = async () => Module = (await import('./bulgarian/Bulgarian.svelte')).default;
        fn();
    }}>Български</button>
</div>

<!-- Current Language Module -->
<svelte:component this={Module} project_image_source_name={project_image_source_name}></svelte:component>
