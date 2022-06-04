<script>
    export let image;
    export let section_tag = undefined;

    let hover = false;
</script>

<figure 
    href="{image.image}"
    data-img="{image.image}"
    data-thumb="{image.image_prev}"
    data-alt="{image.caption}"
    data-height="2000"
    data-width="3000"
    class='{section_tag}'
    class:hover
    on:mouseenter={()=>hover=true}
    on:mouseleave={()=>hover=false}>
    <div
        style='background-image: url("{image.image_prev}")'
        alt='{image.alt}'
        class='image'/>
    <span>{image.type}</span>
    <figcaption>{image.caption}</figcaption>
</figure>    

<style>
    figure {
        /* Display */
        position: relative;
        flex-basis: 300px;
        flex-grow: 1;
        flex-shrink: 3;

        /* Transform */
        min-width: 29%;
        height: 330px;

        cursor: pointer;
    }

    div {
        /* Display */
        display: block;

        /* Transform */
        position: relative;
        width: auto;
        height: 100%;
        z-index: 0;
    
        /* Background */
        background-position: center;
        background-size: cover;

        /* Border */
        border-top-left-radius: 15px;
        border-top-right-radius: 15px;
        border-bottom-left-radius: 3px;
        border-bottom-right-radius: 3px;

        transition: border-radius var(--anim0) ease,
                    filter var(--anim0) ease;
    }

    span {
        /* Font */
        font-family: var(--txt3);
        font-weight: 400;
        font-size: 18pt;
        max-width: 20ch;
        text-align: center;
        color: transparent;

        /* Transform */
        position: absolute;
        bottom: 40%;
        left: 50%;
        transform: translateX(-50%);
    }

    figcaption {
        /* Font */
        font-family: var(--txt1);
        font-weight: 400;
        font-size: 18pt;
        text-align: start;
        max-width: 20ch;
        color: var(--clr4);

        /* Transform */
        position: absolute;
        bottom: 0;
        left: 0;
        transform: translateY(1.35em);
        z-index: 100;
        
        transition: transform var(--anim0) ease,
                    color var(--anim0) ease,
                    bottom var(--anim0) ease,
                    left var(--anim0) ease;

        cursor: pointer;
    }

    figcaption::before {
        content: '';
        position: absolute;
        width: 0;
        height: 2px;
        bottom: -0.1em;
        border-radius: 30px;
        background-color: var(--clr0);
        transition-delay: var(--anim0);
        transition-duration: 200ms;
        transition-timing-function: ease;
        transition-property: width;
    }

    @media (hover: hover) {
        .hover span {
            color: var(--clr1);
            transition-delay: calc(var(--anim0) * 0.3);
            transition-duration: calc(var(--anim0) * 5);
            transition-timing-function: ease;
            transition-property: color;
        }

        .hover div {
            filter: brightness(0.5) saturate(.5);
            border-radius: 25px;
        }

        .hover figcaption {
            color: var(--clr0);
            transform: translate(-50%, 0);
            bottom: 50%;
            left: 50%;
        }

        .hover figcaption::before {
            width: 100%;
        }
    }
</style>