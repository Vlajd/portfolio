<script>
    export let text;
    let open = false;
    let toggle_menu = () => {
        open = !open;
    };
    let close_menu = () => {
        if (open)
            open = false;
    }
    document.addEventListener('click', close_menu, true);
    document.addEventListener('scroll', close_menu, true);
</script>
 
<nav class:open>
    <div id='OpenBurger' class='burgerMenu'>
        <a class='burgerLink' href='#Start'>{text[0]}</a>
        <a class='burgerLink' href='#Projects'>{text[1]}</a>
        <a class='burgerLink' href='#About'>{text[2]}</a>
        <a class='burgerLink' href='#Contact'>{text[3]}</a>
    </div>
</nav>
<nav class:open id='ClosedBurger' class='burgerMenu' on:click={toggle_menu}>
    <svg
         width='150' height='75'
         viewBox='0 0 100 50' fill='none'
         stroke='var(--clr4)' stroke-linecap='round'>
        <path class='topBurger' d='M90,6 l-50,0'/> 
        <path class='midBurger' d='M90,22 l-50,0'/> 
        <path class='botBurger' d='M90,38 l-35,0'/> 
    </svg>
</nav>

<style>
    :root {
        --transition-duration: 200ms;
    }

    svg {
        transition: transform var(--transition-duration) cubic-bezier(1,0,.35,1), stroke var(--transition-duration);
    }

    .open svg {
        stroke: transparent;
        transform: translateX(10em);
    }
    
    .burgerLink {
        transform: translateY(-10em);
        transition: transform var(--transition-duration) cubic-bezier(.75,0,.4,1);
    }

    .open .burgerLink {
        transform: translateY(0);
    }

    .open .midBurger {
        transform: translateY(-16px);
        transition: transform var(--transition-duration) cubic-bezier(0,0.75,0,1);
    }

    .open .botBurger {
        transform: translateY(-32px);
        transition: transform var(--transition-duration) cubic-bezier(0,0.75,0,1);
    }

    .open #OpenBurger {
        transform: translateY(0);
        stroke-width: 3;
    }
    
    nav {
        /* Display */
        display: flex;
        flex-direction: row;
        gap: 5em;

        /* Transform */
        position: fixed;
        top: 1em;
        right: 2em;
        
        z-index: 200;
    }

    a {
        /* Font */
        font-family: var(--txt1);
        color: var(--clr0);
        font-size: var(--p);

        cursor: pointer;
    }

    a::before {
        content: '';
        position: absolute;
        transform: translateY(1.25em);
        border-radius: 50px;
        height: 3px;
        width: 0;
        background-color: var(--clr1);
        transition: width var(--anim0) ease;
    }

    a:hover::before {
        width: 100%;
    }
    
    #OpenBurger {
        /* Transform */
        padding: 1em 7.5em;
        transform: translateY(-10em);
        transition: transform var(--transition-duration);

        /* Border */
        border-radius: 5em;
        border-style: solid;
        border-width: 3px;
        border-color: var(--clr3);
        background-color: var(--clr2);

        /* Display */
        display: flex;
        flex-direction: row;
        gap: 5em;

        /* Transform */
        position: fixed;
        top: 1em;
        right: 2em;

        z-index: 2
    }

    #ClosedBurger {
        /* SVG */
        stroke: var(--clr3);

        stroke-width: 3;

        cursor: pointer;

        transition: stroke-width var(--anim0) ease;
    }
    
    #ClosedBurger:hover {
        stroke-width: 5;
    }

    @media only screen and (max-width: 1280px) and (max-height: 2560px) {
        #OpenBurger {
            transform: translateY(-20em);

            /* Transform */
            padding: 1em;
            right: 1;
        
            /* Border */
            border-radius: 3em;
        
            /* Display */
            gap: 1em;
            flex-direction: column;
        }

        nav {
            /* Display */
            gap: 1em;
            flex-direction: column;
            
            /* Transform */
            right: 1;
        }
        
        nav a {
            /* Font */
            font-size: calc(var(--pm) + 4pt);
            text-align: center;
        }
            
        #ClosedBurger {
            transform: scale(0.75) translate(4em, -1.5em);
        }
    }
</style>
