<script>
    import { onMount } from 'svelte';

    let Module;

    function loadModule(index, path) {
        async () => {
            Module = (await import(path)).default;
        }
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

    onMount(async () => {
        Module = (await import('./English.svelte')).default;
    });
</script>
<div id='Lang'>
    <!-- svelte-ignore a11y-missing-attribute -->
    <button class='langSelect underlined' on:click={() => loadModule(0, './English.svelte')}>English</button>
    |
    <!-- svelte-ignore a11y-missing-attribute -->
    <button class='langSelect' on:click={() => loadModule(1, './German.svelte')}>Deutsch</button>
    |
    <!-- svelte-ignore a11y-missing-attribute -->
    <button class='langSelect' on:click={() => loadModule(2, './Bulgarian.svelte')}>Български</button>
</div>
<svelte:component this={Module}></svelte:component>