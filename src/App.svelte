<script>
    import { onMount } from 'svelte';
    let Module;
    onMount( async () => Module = (await import('./English.svelte')).default );
    
    // ## Language Selector
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

<style lang="css" global>
    /* ## Language Selector */
    #Lang {
        /* Transform */
        position: absolute;
        transform: translateY(28px);
        margin-left: 10vw;
        z-index: 100;
    }
    
    #Lang button {
        /* Font */
        font-family: var(--txt1);
        font-style: normal;
        font-weight: 400;
        font-size: 14pt;
        
        /* Button */
        background-color: transparent;
        border-color: transparent;
        cursor: pointer;
        
        /* Color */
        color: var(--clr4);
    }
    
    .underlined {
        text-decoration: underline;
    }
</style>

<!--
## Language Selector menu
Selects Language and hotswaps Module
DO NOT, AT ANY COST, TOUCH!!!
-->
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