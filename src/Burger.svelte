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
        <a href='#Start'>{text[0]}</a>
        <a href='#Projects'>{text[1]}</a>
        <a href='#About'>{text[2]}</a>
        <a href='#Contact'>{text[3]}</a>
    </div>
</nav>
<nav class:open id='ClosedBurger' class='burgerMenu' on:click={toggle_menu}>
    <svg
         width='150' height='75'
         viewBox='0 0 100 50' fill='none'
         stroke='var(--clr4)' stroke-width='6' stroke-linecap='round'>
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
    
    #OpenBurger {
        transform: translateY(-10em);
        transition: transform var(--transition-duration);
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
    }
    
    @media only screen and (max-width: 1280px) and (max-height: 2560px) {
        #OpenBurger {
            transform: translateY(-20em);
        }
    }
</style>
