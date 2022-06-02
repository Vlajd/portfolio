<script>
    export let image;
    export let section_tag = undefined;

    let figcaption_length = image.caption.length;
</script>

<figure 
    href="{image.image}"
    data-img="{image.image}"
    data-thumb="{image.image_prev}"
    data-alt="{image.caption}"
    data-height="2000"
    data-width="3000"
    class='{section_tag}'
>
    <div style='background-image: url("{image.image_prev}")'
    alt='{image.alt}' class='image'/>
    <figcaption style='--figcaption-length: {figcaption_length}ch'>{image.caption}</figcaption>
</figure>    

<style>
    figure {
        /* Display */
        display: flex;
        flex-direction: column;
        flex-wrap: nowrap;
        position: block;
        flex-basis: 300px;
        flex-grow: 1;
        flex-shrink: 3;

        /* Transform */
        min-width: 29%;
        height: 330px;

        overflow: hidden;
    }

    div {
        /* Display */
        display: block;

        /* Transform */
        width: auto;
        height: 100%;
    
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

    figcaption {
        /* Font */
        font-family: var(--txt1);
        font-weight: 400;
        font-size: 18pt;
        text-align: start;
        max-width: 20ch;

        /* Transform */
        position: absolute;
        width: 100%;
        z-index: 100;
        transform: translate(0, 330px);

        transition: transform var(--anim0) ease;
    }
    
    figure:hover div {
        filter: brightness(.66) saturate(.5);

        border-bottom-left-radius: 15px;
        border-bottom-right-radius: 15px;
    }

    figure:hover figcaption {
        transform: translate(calc(var(--figcaption-length) / 2 + 2em), 165px) scale(1.2);
        
    }
</style>