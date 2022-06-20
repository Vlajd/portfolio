<script>
    import Burger from './Burger.svelte';
    import MediaQuery from './MediaQuery.svelte';
    import Slider from './Slider.svelte';
    import Figure from './Figure.svelte';
    import Parallax from './Parallax.svelte';
    import source from './data/source.json';
    
    export let lang = undefined;

    let project_images = new Array();
    for (let i = 0; i < source.projects.name.length; i++) {
        project_images.push({
            image: source.projects.full + source.projects.name[i],
            image_prev: source.projects.prev + source.projects.name[i],
            caption: lang.images.projects[i].caption,
            alt: lang.images.projects[i].alt,
            type: lang.images.projects[i].type
        });
    }
    let about_images = new Array();
    for (let i = 0; i < source.about.name.length; i++) {
        about_images.push({
            image: source.about.full + source.about.name[i],
            image_prev: source.about.prev + source.about.name[i],
            caption: lang.images.about[i].caption,
            alt: lang.images.about[i].alt,
            type: lang.images.about[i].type
        });
    }

    // Parallax Val, binded by a svelte window
    let parallax_val = 0;
</script>

<Burger text={lang.burger}/>
<svelte:window bind:scrollY={parallax_val}/>

<div>
<!-- Start -->
<section id='Start'>
    <Parallax val={parallax_val} speed={-0.75} offset={{x: 0, y: -7.5}} opacity={17.5} rad={7.5} vwpos={100}/>
    <div>
        <h1>{lang.Start.title.name}</h1>
        <h5>{lang.Start.title.sub}</h5>
    </div>
</section>

<main id='Content'>
    <!-- Projects -->
    <section id='Projects'>
        <Parallax val={parallax_val} speed={0.3} offset={{x: -15, y: -15}} opacity={40} rad={25} vwpos={0}/>
        <h1>{lang.burger[1]}</h1>
        <MediaQuery query = '(min-width: 1280px)' let:matches>
            {#if matches}
            <div id='Gallery'>
                {#each project_images as image}
                    <svelte:component this={Figure} image={image} section_tag='projects_figure'/>   
                {/each}
            </div>
            {/if}
            {#if !matches}
            <div id='Gallery'>
                <Slider images={project_images}/>
            </div>
            {/if}
        </MediaQuery>
        <Parallax val={parallax_val} speed={0.2} offset={{x: -10, y: 50}} opacity={25} rad={20} vwpos={100}/>
    </section>
    
    <!-- About -->
    <section id='About'>
        <Parallax val={parallax_val} speed={0.3} offset={{x: -15, y: 15}} opacity={40} rad={25} vwpos={0}/>
        <h1>{lang.burger[2]}</h1>
        <!-- Introduction -->
        <div class='infobox'>
            <div class='infoboxData'>
                <p id='AboutInnerHtmlQuerry'></p>
            </div>
            <figure class='infoboxData'>
                <div style='background-image: url("{about_images[0].image_prev}")' class='image' alt='{about_images[0].alt}'/>
            </figure>
        </div>
        <Parallax val={parallax_val} speed={0.2} offset={{x: -10, y: 75}} opacity={25} rad={20} vwpos={100}/>
        
        <!-- Hobbies -->
        <div id='Hobbies'>
            <div>
                <Parallax val={parallax_val} speed={0.2} offset={{x: -15, y: 25}} opacity={25} rad={20} vwpos={0}/>
                <h2>{lang.Hobbies.title}</h2>
                <br><br>
                <p id='HobbiesInnerHtmlQuerry'></p>
            </div>
            <!-- Skateboarding -->
            <div class='infobox'>
                <figure class='infoboxData'>
                    <div style='background-image: url("{about_images[1].image_prev}")' alt='{about_images[1].alt}' class='image'/>
                    <div style='background-image: url("{about_images[2].image_prev}")' alt='{about_images[2].alt}' class='image'/>
                </figure>
                <div class='infoboxData'>
                    <h4>{lang.Hobbies.elements[0].title}</h4>
                    <br>
                    <p class='hobbiesElementsInnerHtmlQuerry'></p>
                </div>
            </div>
            
            <!-- Music -->
            <div class='infobox reverse'>
                <figure class='infoboxData'>
                    <div style='background-image: url("{about_images[3].image_prev}")' alt='{about_images[1].alt}' class='image'/>
                    <div style='background-image: url("{about_images[4].image_prev}")' alt='{about_images[2].alt}' class='image'/>
                </figure>
                <div class='infoboxData'>
                    <h4>{lang.Hobbies.elements[1].title}</h4>
                    <br>
                    <p class='hobbiesElementsInnerHtmlQuerry'></p>
                </div>
            </div>
            
            <!-- Languages -->
            <div class='infobox'>
                <figure class='infoboxData'>
                    <div style='background-image: url("{about_images[5].image_prev}")' alt='{about_images[1].alt}' class='image'/>
                    <div style='background-image: url("{about_images[6].image_prev}")' alt='{about_images[2].alt}' class='image'/>
                </figure>
                <div class='infoboxData'>
                    <h4>{lang.Hobbies.elements[2].title}</h4>
                    <br>
                    <p class='hobbiesElementsInnerHtmlQuerry'></p>
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
            <Parallax val={parallax_val} speed={0.2} offset={{x: -10, y: 185}} opacity={25} rad={20} vwpos={100}/>
            
            <!-- Programming -->
            <div class='infobox reverse'>
                <figure class='infoboxData'>
                    <div style='background-image: url("{about_images[7].image_prev}")' alt='{about_images[1].alt}' class='image'/>
                    <div style='background-image: url("{about_images[8].image_prev}")' alt='{about_images[2].alt}' class='image'/>
                </figure>
                <div class='infoboxData'>
                    <h4>{lang.Hobbies.elements[3].title}</h4>
                    <br>
                    <p class='hobbiesElementsInnerHtmlQuerry'></p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Contact -->
    <section id='Contact'>
        <Parallax val={parallax_val} speed={0.3} offset={{x: -15, y: 95}} opacity={40} rad={25} vwpos={0}/>
        <h1>{lang.Contact.title}</h1>
        <div class='infobox'>
            <div id='ContactData' class='infoboxData'>
                <a href='mailto: boris.kostadinov@graphische.net'><h2>Boris.Kostadinov@Graphische.net</h2></a>
                <p>{lang.Contact.intro}</p>
                <MediaQuery query = '(min-width: 1280px)' let:matches>
                    {#if matches}
                        <div id='ContactMedia'>
                            <!-- E-Mail -->
                            <a href='mailto: boris.kostadinov@graphische.net'><div class='contactMediaIcon'><svg width="65.402" height="52.321" viewBox="0 0 66 52.321"><path d="M61.862,6H9.54a6.531,6.531,0,0,0-6.507,6.54L3,51.781a6.559,6.559,0,0,0,6.54,6.54H61.862a6.559,6.559,0,0,0,6.54-6.54V12.54A6.559,6.559,0,0,0,61.862,6Zm0,13.08L35.7,35.431,9.54,19.08V12.54L35.7,28.891,61.862,12.54Z" transform="translate(-2.5 -6)"/></svg></div></a>
                            <!-- Github -->
                            <a href='https://github.com/Vlajd' target='_blank'><div class='contactMediaIcon'><svg width="68.674" height="68.674" viewBox="0 0 68.674 68.674"><path d="M36.587,2.25C17.625,2.25,2.25,18.024,2.25,37.461a35.143,35.143,0,0,0,23.484,33.4,2.691,2.691,0,0,0,.583.061,1.661,1.661,0,0,0,1.763-1.748c0-.843-.031-3.05-.046-5.994a15.7,15.7,0,0,1-3.464.414c-6.607,0-8.109-5.135-8.109-5.135-1.564-4.062-3.817-5.151-3.817-5.151-2.989-2.1-.015-2.161.215-2.161h.015c3.449.307,5.258,3.648,5.258,3.648,1.717,3,4.016,3.848,6.07,3.848a9.65,9.65,0,0,0,3.924-.92A7.607,7.607,0,0,1,30.3,53.02c-7.618-.889-15.636-3.909-15.636-17.4a13.781,13.781,0,0,1,3.526-9.443,12.961,12.961,0,0,1,.337-9.32,2.858,2.858,0,0,1,.766-.077c1.242,0,4.047.475,8.676,3.694a31.917,31.917,0,0,1,17.2,0c4.629-3.219,7.435-3.694,8.676-3.694a2.858,2.858,0,0,1,.766.077,12.961,12.961,0,0,1,.337,9.32,13.838,13.838,0,0,1,3.526,9.443c0,13.52-8.032,16.494-15.682,17.368,1.226,1.088,2.33,3.234,2.33,6.515,0,4.706-.046,8.508-.046,9.657a1.653,1.653,0,0,0,1.748,1.763,2.966,2.966,0,0,0,.613-.061,35.137,35.137,0,0,0,23.484-33.4C70.924,18.024,55.549,2.25,36.587,2.25Z" transform="translate(-2.25 -2.25)"/></svg></div></a>
                            <!-- Youtube -->
                            <a href='https://www.youtube.com/channel/UCbI6zfXhfQ7pFb8ezgJwLkw' target='_blank'><div class='contactMediaIcon'><svg width="65.653" height="46.162" viewBox="0 0 65.653 46.162"><path d="M65.331,11.723a8.249,8.249,0,0,0-5.8-5.842C54.407,4.5,33.876,4.5,33.876,4.5s-20.53,0-25.65,1.381a8.25,8.25,0,0,0-5.8,5.842c-1.372,5.153-1.372,15.9-1.372,15.9s0,10.752,1.372,15.9a8.126,8.126,0,0,0,5.8,5.749c5.12,1.381,25.65,1.381,25.65,1.381s20.53,0,25.65-1.381a8.126,8.126,0,0,0,5.8-5.749c1.372-5.153,1.372-15.9,1.372-15.9s0-10.752-1.372-15.9ZM27.162,37.389V17.866l17.159,9.762L27.162,37.389Z" transform="translate(-1.05 -4.5)"/></svg></div></a>
                            <!-- Instagram -->
                            <a href='https://www.instagram.com/vlajd_/' target='_blank'><div class='contactMediaIcon'><svg width="61.46" height="61.46" viewBox="0 0 61.46 61.46"><g transform="translate(-4.5 -4.5)"><path d="M48.034,9.622a12.842,12.842,0,0,1,12.8,12.8V48.034a12.842,12.842,0,0,1-12.8,12.8H22.426a12.842,12.842,0,0,1-12.8-12.8V22.426a12.842,12.842,0,0,1,12.8-12.8H48.034m0-5.122H22.426A17.979,17.979,0,0,0,4.5,22.426V48.034A17.979,17.979,0,0,0,22.426,65.96H48.034A17.979,17.979,0,0,0,65.96,48.034V22.426A17.979,17.979,0,0,0,48.034,4.5Z"/><path d="M27.466,16.682a3.841,3.841,0,1,1,3.841-3.841A3.832,3.832,0,0,1,27.466,16.682Z" transform="translate(24.409 5.743)"/><path d="M26.615,16.372A10.243,10.243,0,1,1,16.372,26.615,10.253,10.253,0,0,1,26.615,16.372m0-5.122A15.365,15.365,0,1,0,41.98,26.615,15.369,15.369,0,0,0,26.615,11.25Z" transform="translate(8.615 8.615)"/></g></svg></div></a>
                        </div>
                    {/if}
                </MediaQuery>
            </div>
            <figure>
                <MediaQuery query = '(max-width: 1280px)' let:matches>
                    {#if matches}
                        <div id='ContactMedia'>
                            <div class='contactMediaVPadding'>
                                <!-- E-Mail -->
                                <a href='mailto: boris.kostadinov@graphische.net'><div class='contactMediaIcon'><svg width="65.402" height="52.321" viewBox="0 0 66 52.321"><path d="M61.862,6H9.54a6.531,6.531,0,0,0-6.507,6.54L3,51.781a6.559,6.559,0,0,0,6.54,6.54H61.862a6.559,6.559,0,0,0,6.54-6.54V12.54A6.559,6.559,0,0,0,61.862,6Zm0,13.08L35.7,35.431,9.54,19.08V12.54L35.7,28.891,61.862,12.54Z" transform="translate(-2.5 -6)"/></svg></div></a>
                                <!-- Github -->
                                <a href='https://github.com/Vlajd' target='_blank'><div class='contactMediaIcon'><svg width="68.674" height="68.674" viewBox="0 0 68.674 68.674"><path d="M36.587,2.25C17.625,2.25,2.25,18.024,2.25,37.461a35.143,35.143,0,0,0,23.484,33.4,2.691,2.691,0,0,0,.583.061,1.661,1.661,0,0,0,1.763-1.748c0-.843-.031-3.05-.046-5.994a15.7,15.7,0,0,1-3.464.414c-6.607,0-8.109-5.135-8.109-5.135-1.564-4.062-3.817-5.151-3.817-5.151-2.989-2.1-.015-2.161.215-2.161h.015c3.449.307,5.258,3.648,5.258,3.648,1.717,3,4.016,3.848,6.07,3.848a9.65,9.65,0,0,0,3.924-.92A7.607,7.607,0,0,1,30.3,53.02c-7.618-.889-15.636-3.909-15.636-17.4a13.781,13.781,0,0,1,3.526-9.443,12.961,12.961,0,0,1,.337-9.32,2.858,2.858,0,0,1,.766-.077c1.242,0,4.047.475,8.676,3.694a31.917,31.917,0,0,1,17.2,0c4.629-3.219,7.435-3.694,8.676-3.694a2.858,2.858,0,0,1,.766.077,12.961,12.961,0,0,1,.337,9.32,13.838,13.838,0,0,1,3.526,9.443c0,13.52-8.032,16.494-15.682,17.368,1.226,1.088,2.33,3.234,2.33,6.515,0,4.706-.046,8.508-.046,9.657a1.653,1.653,0,0,0,1.748,1.763,2.966,2.966,0,0,0,.613-.061,35.137,35.137,0,0,0,23.484-33.4C70.924,18.024,55.549,2.25,36.587,2.25Z" transform="translate(-2.25 -2.25)"/></svg></div></a>
                            </div>
                            <div class='contactMediaVPadding'>
                                <!-- Youtube -->
                                <a href='https://www.youtube.com/channel/UCbI6zfXhfQ7pFb8ezgJwLkw' target='_blank'><div class='contactMediaIcon'><svg width="65.653" height="46.162" viewBox="0 0 65.653 46.162"><path d="M65.331,11.723a8.249,8.249,0,0,0-5.8-5.842C54.407,4.5,33.876,4.5,33.876,4.5s-20.53,0-25.65,1.381a8.25,8.25,0,0,0-5.8,5.842c-1.372,5.153-1.372,15.9-1.372,15.9s0,10.752,1.372,15.9a8.126,8.126,0,0,0,5.8,5.749c5.12,1.381,25.65,1.381,25.65,1.381s20.53,0,25.65-1.381a8.126,8.126,0,0,0,5.8-5.749c1.372-5.153,1.372-15.9,1.372-15.9s0-10.752-1.372-15.9ZM27.162,37.389V17.866l17.159,9.762L27.162,37.389Z" transform="translate(-1.05 -4.5)"/></svg></div></a>
                                <!-- Instagram -->
                                <a href='https://www.instagram.com/vlajd_/' target='_blank'><div class='contactMediaIcon'><svg width="61.46" height="61.46" viewBox="0 0 61.46 61.46"><g transform="translate(-4.5 -4.5)"><path d="M48.034,9.622a12.842,12.842,0,0,1,12.8,12.8V48.034a12.842,12.842,0,0,1-12.8,12.8H22.426a12.842,12.842,0,0,1-12.8-12.8V22.426a12.842,12.842,0,0,1,12.8-12.8H48.034m0-5.122H22.426A17.979,17.979,0,0,0,4.5,22.426V48.034A17.979,17.979,0,0,0,22.426,65.96H48.034A17.979,17.979,0,0,0,65.96,48.034V22.426A17.979,17.979,0,0,0,48.034,4.5Z"/><path d="M27.466,16.682a3.841,3.841,0,1,1,3.841-3.841A3.832,3.832,0,0,1,27.466,16.682Z" transform="translate(24.409 5.743)"/><path d="M26.615,16.372A10.243,10.243,0,1,1,16.372,26.615,10.253,10.253,0,0,1,26.615,16.372m0-5.122A15.365,15.365,0,1,0,41.98,26.615,15.369,15.369,0,0,0,26.615,11.25Z" transform="translate(8.615 8.615)"/></g></svg></div></a>
                            </div>
                            <div style='background-color: black' class='image'/>
                        </div>
                    {/if}
                    {#if !matches}
                        <div style='background-color: black' class='image'/>
                        <figcaption id='ContactFigureInnerHtmlQuerry'></figcaption>
                    {/if}    
                </MediaQuery>
            </figure>
        </div>
    </section>
</main>

<!-- End Footer -->
<footer>{lang.name}</footer>

</div>

<style>
    #Content {
        /* Transform */
        padding: 0 10vw;

        /* Display */
        display: flex;
        flex-direction: column;
        gap: 20em;
    }

    /* ## Start */
    #Start {
        /* Transform */
        min-width: 100%;
        min-height: 100vh;
    }

    #Start div {
        /* Display */
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        
        /* Transform */
        min-width: 100%;
        min-height: 100vh;
    }
    
    /* ## Projects */
    #Projects {
        /* Display */
        display: flex;
        flex-direction: column;
        gap: 10em;

        /* Transform */
        min-width: 100%;
        min-height: 100vh;
    }

    #Gallery {
        /* Display */
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        gap: 5em;
        row-gap: 7.5em;
    }
    
    /* ## About */
    #About {
        /* Display */
        display: flex;
        flex-direction: column;
        gap: 15em;

        /* Transform */
        width: 100%;
        min-height: 100vh;
    }

    #About p {
        max-width: 68ch;
    }

    #About .infobox {
        /* Display */
        display: flex;
        justify-content: space-around;
        gap: 5em;
        min-height: 50vh;
    }

    #About .infobox figure {
        /* Display*/
        display: flex;
        justify-content: space-between;
        gap: 2.5em; 
        flex-wrap: nowrap;

        /* Transform */
        min-width: 640px;
    }

    #About .infobox a {
        /* Font */
        color: var(--clr4);
        text-decoration: underline;
        text-decoration-thickness: 1.5px;
        cursor: pointer;

        transition: text-decoration-color var(--anim0) linear;
    }

    #About .infobox a:hover {
        text-decoration-color: transparent;
    }

    #About .infobox .infoboxData {
        /* Transform */
        width: 50%;
        height: auto;
    }

    #Hobbies {
        /* Display*/
        display: flex;
        flex-direction: column;
        gap: 10em;
    }

    .reverse {
        /* Display */
        flex-direction: row-reverse;
    }
    
    /* Contact */
    #Contact {
        /* Display */
        display: flex;
        flex-direction: column;
        gap: 6em;
    }

    #Contact .infobox {
        /* Display */
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        gap: 5em;

        /* Transform */
        width: 100%;
        min-height: 30vh;
        padding: 5em;
        padding-bottom: 3em;

        /* Border */
        border-style: solid;
        border-radius: 111px;
        
        background-color: rgba(232, 232, 219, 0.65);
    }

    #ContactData {
        /* Transform */
        gap: 3.5em;
    }

    #ContactData a {
        /* Font */
        color: var(--clr4);
        text-decoration: underline;
        text-decoration-thickness: 1.5px;

        transition: text-decoration-color var(--anim0) linear;
    }

    #ContactData a:hover {
        /* Font */
        text-decoration-color: transparent;
    }

    #Contact .infobox .infoboxData {
        /* Display */
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    #Contact .infobox .infoboxData p {
        /* Transform*/
        text-align: center;
        max-width: 34ch;
    }

    #Contact figure .image {
        /* Transform */
        height: 20em;
        
        /* Border */
        border-bottom-left-radius: 3px;
        border-bottom-right-radius: 3px;
    }

    #Contact figcaption {
        /* Font*/
        font-family: var(--txt1);
        font-style: normal;
        font-weight: 500;
        font-size: 16pt;
        line-height: 28pt;
    }

    /* SocialMedia */
    #ContactMedia {
        /* Display */
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        flex-wrap: nowrap;
        gap: 2em;
    }

    .contactMediaIcon {
        /* Disply */
        display: flex;
        justify-content: center;
        align-items: center;

        /* Transform*/
        width: 6em;
        height: 6em;
        padding: 15px;

        /* Background */
        background-color: var(--clr1);
        
        /* Border */
        border-radius: 30px;
        
        overflow: hidden;

        transition: transform var(--anim0) ease;
    }

    .contactMediaIcon:hover {
        /* Transform */
        transform: scale(1.15);
    }

    .contactMediaIcon path {
        /* Path */
        fill: var(--clr0);
    }

    /* ## Mobile */
    @media only screen and (max-width: 1280px) and (max-height: 2560px) {
        #Content {
            /* Transform */
            padding: 0 8vw;
            width: 100vw;
        
            /* Display */
            gap: 20em;

            overflow-x: hidden;
        }

        #Start div {
            /* Transform */
            padding-bottom: 10vh;
        }

        #Gallery {
            /* Display */
            display: block;
        }

        #About {
            /* Display */
            gap: 5em;
        }

        #About .infobox {
            /* Display */
            flex-direction: column;
        }
        
        #Hobbies .infobox {
            /* Display */
            flex-direction: column-reverse;
        }

        #About .infobox .infoboxData {
            /* Transform */
            min-width: 100%;
            min-height: 640px;
        }

        #About .infobox .infoboxData .image {
            /* Transform */
            min-height: 540px;
        }
        
        .reverse {
            /* Display */
            flex-direction: row;
        }
        
        #Contact h2 {
            /* Font */
            font-size: 14pt;
            font-weight: 700;
        }

        #Contact .infobox {
            /* Border */
            border-style: none;
            padding: 0;

            /* Display */
            gap: 1em;
        }

        #Contact .infoboxData:first-child {
            /* Display */
            gap: 2em;
        }
        
        #Contact figure {
            /* Display */
            gap: 1em;
            flex-direction: row;
            flex-wrap: wrap;

            /* Transform */
            transform: scale(0.9);
        }
        
        #Contact figure .image {        
            /* Border */
            border-radius: 20px;
            
            /* Transform*/
            width: 50%;
            min-width: 200px;
            max-width: 30vw;
            margin-left: 1em;

            /* Display */
            flex-shrink: 2;
        }
        
        #Contact figcaption {
            visibility: hidden;
        }
        
        #ContactMedia {
            /* Display */
            flex-wrap: nowrap;
            flex-direction: row;
            gap: 0;
        }

        #ContactMedia a {
            /* Transform */
            transform: scale(0.8);
        }

        .contactMediaIcon {
            /* Display */
            flex-grow: 2;
            flex-shrink: 2;
            flex-basis: 50%;

            /* Transform */
            padding: 0;
        }
        
        .contactMediaVPadding {
            display: flex;
            flex-direction: column;
            justify-content: space-around;
        }
    }
</style>