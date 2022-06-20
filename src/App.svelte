<script>
    import 'bigger-picture/dist/bigger-picture.css';
    import BiggerPicture from 'bigger-picture/src/bigger-picture.js';
    import Site from './Site.svelte';
    import english from './data/english.json';
    import german from './data/german.json';
    import bulgarian from './data/bulgarian.json';
    import { onMount } from 'svelte';
    import source from './data/source.json';

    let lang = english;
    let project_images = undefined;
    let about_images = undefined;
    let contact_images = undefined;

    let cookies = document.cookie
        .split(';')
        .map(cookie => cookie.split('='))
        .reduce((accumulator, [key, value]) =>
            ({ ...accumulator, [key.trim()]: decodeURIComponent(value) }),
        {}
    );
    let cookie_date = new Date;
    cookie_date.setFullYear(cookie_date.getFullYear() + 1);

    const bind_image_querries = () => {
        
        project_images = new Array();
        about_images = new Array();
        contact_images = new Array();

        // Images
        for (let i = 0; i < source.projects.name.length; i++) {
            project_images.push({
                image: source.projects.full + source.projects.name[i],
                image_prev: source.projects.prev + source.projects.name[i],
                caption: lang.images.projects[i].caption,
                alt: lang.images.projects[i].alt,
                type: lang.images.projects[i].type
            });
        }
        for (let i = 0; i < source.about.name.length; i++) {
            about_images.push({
                image: source.about.full + source.about.name[i],
                image_prev: source.about.prev + source.about.name[i],
                caption: lang.images.about[i].caption,
                alt: lang.images.about[i].alt,
                type: lang.images.about[i].type
            });
        }
        for (let i = 0; i < source.contact.name.length; i++) {
            contact_images.push({
                image: source.contact.full + source.contact.name[i],
                image_prev: source.contact.prev + source.contact.name[i]
            });
        }
    }

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
    const selectLang = async (index) => {
        switch (index) {
            case 0:
                lang = english;
                break;
            case 1:
                lang = german; 
                break;
            case 2:
                lang = bulgarian;
                break;
            case 3:
                lang = bulgarian;
                break;
        }
        document.cookie = 'lang=' + index + ';AC-C=ac-c;expires=' + cookie_date.toUTCString() + ';path=/;SameSite=Strict';

        let elements = document.getElementsByClassName('langSelect');
        for (let i = 0; i < elements.length; i++) {
            if (i == index) {
                elements[i].classList.add('underlined');
            }
            else {
                elements[i].classList.remove('underlined');
            }
        }
        setTimeout(bind_image_querries, 100);
    }
        
    bind_image_querries();
    
    onMount( () => {
        if (cookies.lang != undefined) {
            console.log("Test");
            selectLang(parseInt(cookies.lang));
        }
        else {
            selectLang(0);
        }
    });
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
    }}>English</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(1);
    }}>Deutsch</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(2);
    }}>Български</button>
    <hr>
    <button class='langSelect' on:click={ () => {
        selectLang(3);
    }}>日本語</button>
</div>

<!-- Current Language Module -->
<svelte:component this={Site} lang={lang} project_images={project_images} about_images={about_images} contact_images={contact_images}/>

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