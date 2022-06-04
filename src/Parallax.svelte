<script>
    export let val = 0;
    export let speed = 1;
    export let offset = {x: 0, y: 0};
    export let opacity = 100;
    export let rad = 50;
    export let vwpos = 0;
</script>

<svg
    style:transform='translate(calc({rad * -2 + offset.x}px + {vwpos}vw), {-val * speed + offset.y}px)'
    height='{rad * 2}'
    width='{rad * 2}'>
    <circle
        cx='{rad}'
        cy='{rad}'
        r='{rad}'
        fill='var(--clr1)'
        fill-opacity='{opacity}%'
        />
</svg>

<style>
    svg {
        position: absolute;
        z-index: -1;
    }
</style>
