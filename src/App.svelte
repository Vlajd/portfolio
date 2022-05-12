<script>
    import { onMount } from 'svelte';
    let Module;
    onMount( async () => Module = (await import('./English.svelte')).default );
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
<div id='Lang'>
    <!-- svelte-ignore a11y-missing-attribute -->
    <button class='langSelect underlined' on:click={ () => {
        selectLang(0);
        let fn = async () => Module = (await import('./English.svelte')).default;
        fn();
    }}>English</button>
    |
    <!-- svelte-ignore a11y-missing-attribute -->
    <button class='langSelect' on:click={ () => {
        selectLang(1);
        let fn = async () => Module = (await import('./German.svelte')).default;
        fn();
    }}>Deutsch</button>
    |
    <!-- svelte-ignore a11y-missing-attribute -->
    <button class='langSelect' on:click={ () => {
        selectLang(2);
        let fn = async () => Module = (await import('./Bulgarian.svelte')).default;
        fn();
    }}>Български</button>
</div>
<svelte:component this={Module}></svelte:component>