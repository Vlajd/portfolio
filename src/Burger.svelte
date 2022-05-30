<nav id='OpenBurger' class='hidden burgerMenu'>
    <a href='#Start'>{text[0]}</a>
    <a href='#Projects'>{text[1]}</a>
    <a href='#About'>{text[2]}</a>
    <a href='#Contact'>{text[3]}</a>
</nav>
<nav id='ClosedBurger' class='burgerMenu' on:click={()=>toggle_menu()}>
    <svg width="72.5" height="48.5" viewBox="0 0 72.5 48.5">
        <g id="Burgermenu_Closed" transform="translate(-1805.75 -25.75)">
          <line id="Burgermenu_3" x1="64" transform="translate(1810 30)" fill="none" stroke-linecap="round" stroke-width="7"/>
          <line id="Burgermenu_2" x1="64" transform="translate(1810 50)" fill="none" stroke-linecap="round" stroke-width="7"/>
          <line id="Burgermenu_1" x1="46" transform="translate(1828 70)" fill="none" stroke-linecap="round" stroke-width="7"/>
        </g>
    </svg>  
</nav>

<script>
    export let text;
    let is_open = false;
    let menus = document.getElementsByClassName('burgerMenu');
    function toggle_menu() {
        is_open = !is_open;
        for (let i = 0; i < menus.length; i++) {
            menus[i].classList.toggle('hidden');
        }
    }
    function close_menu() { if (is_open) toggle_menu() }
    document.addEventListener('click', close_menu, true);
    document.addEventListener('scroll', close_menu, true);
</script>
