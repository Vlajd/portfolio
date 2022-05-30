<script>
    import { onMount } from 'svelte';
    
    let project_image_source_name = [
        'TrainInRumania.jpg',
        'KissingPigeons.jpg',
        'GlasAndCheese.jpg',
        'Punktechaplin0.jpg',
        'Punktechaplin1.jpg',
        'BurningCastle.jpg'
    ]

    let Module;
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