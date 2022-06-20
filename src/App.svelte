<script>
    import 'bigger-picture/dist/bigger-picture.css';
    import BiggerPicture from 'bigger-picture/src/bigger-picture.js';
    import Site from './Site.svelte';
    import english from './data/english.json';
    import german from './data/german.json';
    import bulgarian from './data/bulgarian.json';
    import { onMount } from 'svelte';

    const bind_json_querries = () => {
        document.getElementById('AboutInnerHtmlQuerry').innerHTML = lang.About;
        document.getElementById('HobbiesInnerHtmlQuerry').innerHTML = lang.Hobbies.intro;
        let hobbies = document.getElementsByClassName('hobbiesElementsInnerHtmlQuerry');
        for (let i = 0; i < hobbies.length; i++) {
            hobbies[i].innerHTML = lang.Hobbies.elements[i].text;
        }
        document.getElementById('ContactFigureInnerHtmlQuerry').innerHTML = lang.Contact.name;
    };

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

    // █░░ ▄▀█ █▄░█ █▀▀ █░█ ▄▀█ █▀▀ █▀▀   █▀ █▀▀ █░░ █▀▀ █▀▀ ▀█▀ █▀█ █▀█
    // █▄▄ █▀█ █░▀█ █▄█ █▄█ █▀█ █▄█ ██▄   ▄█ ██▄ █▄▄ ██▄ █▄▄ ░█░ █▄█ █▀▄
    // Visually changes the selected language 
    let lang = english;
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
        setTimeout(bind_json_querries);
    }
    onMount(bind_json_querries);
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
        lang = english;
    }}>English</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(1);
        lang = german; 
    }}>Deutsch</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(2);
        lang = bulgarian;
    }}>Български</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(3);
        lang = bulgarian;
    }}>日本語</button>
</div>

<!-- Current Language Module -->
<svelte:component this={Site} lang={lang}/>

<style>
    /* ## Language Selector */
    #Lang {
        /* Transform */
        position: absolute;
        transform: translateY(2em);
        margin-left: 10vw;
        z-index: 100;
    }

    #Lang button {
        /* Font */
        font-family: var(--txt1);
        font-style: normal;
        font-size: 14pt;
        text-align: start;
        
        /* Button */
        background-color: transparent;
        border-color: transparent;
        cursor: pointer;
        
        /* Color */
        color: var(--clr4);
        
        /* Transform */
        min-width: 10ch;
    }

    .underlined {
        font-weight: 700;
    }

    /* ## Mobile */
    @media only screen and (max-width: 1280px) and (max-height: 2560px) {
        #Lang {
            /* Transform */
            transform: translate(-5vw, 1em);
        }

        #Lang button {
            /* Font */
            font-size: 12pt;
        }
    }
</style>