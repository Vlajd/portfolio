<script>
    export let val = 0;
    export let speed = 1;
    export let offset = {x: 0, y: 0};
    export let opacity = 100;
    export let rad = 50;
    export let vwpos = 0;
</script>

<svg
    style:transform='translate(calc({-rad + offset.x}em + {vwpos}vw), calc({-val * speed}px + {offset.y}em))'
    height='{rad * 2}em'
    width='{rad * 2}em'>
    <circle
        cx='{rad}em'
        cy='{rad}em'
        r='{rad}em'
        fill='var(--clr1)'
        fill-opacity='{opacity}%'
        />
</svg>

<style>
    svg {
        position: absolute;
        z-index: -1;
    }
    
    @media only screen and (max-width: 1280px) and (max-height: 2560px) {
        svg {
            visibility: hidden;
        }
    }
</style>
