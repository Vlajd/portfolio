<script>
    import Burger from './Burger.svelte';
</script>

<Burger text={['Start', 'Projects', 'About', 'Contact']}/>

<div>
<!-- Start -->
<section id='Start'>
    <div>
        <h1>Boris Kostadinov</h1>
        <h5>Multimedia</h5>
    </div>
</section>

<main id='Content'>
    <!-- Projects -->
    <section id='Projects'>
        <h1>Projects</h1>
        <div id='Gallery'>
            <!-- Train In Rumania -->
            <figure>
                <div style='background-image: url("./img/TrainInRumania.jpg")' alt='A Train driving through the nature of Rumania.' class='image'></div>
                <figcaption>Train in Rumania</figcaption>
            </figure>
            <!-- Kissing Pigeons -->
            <figure>
                <div style='background-image: url("./img/KissingPigeons.jpg")' alt='Two Pigeons enjoying their time together on a roof.' class='image'></div>
                <figcaption>Kissing Pigeons</figcaption>
            </figure>
            <!-- Bell and Cheese -->
            <figure>
                <div style='background-image: url("./img/GlasAndCheese.jpg")' src='./img/GlasAndCheese.jpg' alt='Glass bell with cheddar in the background.' class='image'></div>
                <figcaption>Bell and Cheese</figcaption>
            </figure>
            <!-- Pointchaplin N°1 -->
            <figure>
                <div style='background-image: url("./img/Punktechaplin0.jpg")' alt='Chaplin Illustration.' class='image'></div>
                <figcaption>Point Chaplin N°1</figcaption>
            </figure>
            <!-- Pointchaplin N°2 -->
            <figure>
                <div style='background-image: url("./img/Punktechaplin1.jpg")' alt='Chaplin Illustration.' class='image'></div>
                <figcaption>Point Chaplin N°2</figcaption>
            </figure>
            <!-- Burning Castle -->
            <figure>
                <div style='background-image: url("./img/BurningCastle.jpg")' alt='Photoshop of imaginary burning Castle.' class='image'></div>
                <figcaption>Burning Castle</figcaption>
            </figure>
        </div>
    </section>
    
    <!-- About -->
    <section id='About'>
        <h1>About</h1>
        <!-- Introduction -->
        <div class='infobox'>
            <div class='infoboxData'>
                <p>
                    <strong>Hi</strong>, my name is <strong>Boris</strong>, and I am currently a student at "<strong>die Graphische</strong>" in Vienna.
                    <br><br>
                    My area of interest is very wide. From <strong>music-arrangements</strong>, to <strong>photography</strong>, <strong>vector- and 3D-art</strong>, to programming powerful applications in <strong>Rust</strong> and/or <strong>C++</strong>. As said, my area of interest is very wide.
                    <br><br>
                    As for my skills, you should check out <a href='#Projects'><strong>my projects</strong></a> to make a unique image for yourself. Just telling you what I'm able to do will <strong>not</strong> justify my actual skills to a <strong>desired extend</strong>.
                    <br><br>
                    If you're interested in finding out more about me, you can take a look at my <strong>CV</strong> or <a href='#Contact'><strong>contact me</strong></a>.
                </p>
            </div>
            <figure class='infoboxData'>
                <div style='background-image: url("./img/FamilienFoto.jpg")' class='image'></div>
            </figure>
        </div>
    
        <!-- Hobbies -->
        <div id='Hobbies'>
            <div>
                <h2>Hobbies</h2>
                <br><br>
                <p>Hobbies are something that can <strong>shape someone’s life</strong> very drastically. As for me, I've mixed my something into one big dish that I try to keep in balance. It has been fun so far...</p>
            </div>
            <!-- Skateboarding -->
            <div class='infobox'>
                <figure class='infoboxData'>
                    <div style='background-color: black' class='image'></div>
                    <div style='background-color: black' class='image'></div>
                </figure>
                <div class='infoboxData'>
                    <h4>Skateboarding</h4>
                    <br>
                    <p>
                        I've been skateboarding since ~2018. It's very frustrating and expensive, but fortunately, it's also very rewarding.
                        <br><br>
                        Skateboarding is not a sport in the traditional sense. It allows for <strong>creativity</strong>, because no one's telling you what to do or how you should do it. For me, it pushed my own creativity to <strong>another level</strong>.
                        <br><br>
                        If you've been to Vienna's Danube Island, you may recognize the location in both pictures. It's my favorite place to hang out, skate, and chill.
                    </p>
                </div>
            </div>
    
            <!-- Music -->
            <div class='infobox reverse'>
                <figure class='infoboxData'>
                    <div style='background-color: black' class='image'></div>
                    <div style='background-color: black' class='image'></div>
                </figure>
                <div class='infoboxData'>
                    <h4>Music</h4>
                    <br>
                    <p>
                        Music's also one of my favourite things to do. I've been obsessed with it since I was <strong>7 years old!</strong>
                        <br><br>
                        I'm mostly playing piano and percussion. From Frederic Chopin to modern Jazz, I enjoy pretty much any genre.
                        <br><br>
                        I am also writing sheet-music for (mostly) piano. If you're intereted, check out my website:
                        <br><br>
                        <!-- svelte-ignore a11y-missing-attribute -->
                        <a><strong>vlajdsheetmusic.com</strong></a>
                    </p>
                </div>
            </div>
    
            <!-- Languages -->
            <div class='infobox'>
                <figure class='infoboxData'>
                    <div style='background-color: black' class='image'></div>
                    <div style='background-color: black' class='image'></div>
                </figure>
                <div class='infoboxData'>
                    <h4>Languages</h4>
                    <br>
                    <p>
                        There are tons of languages out there in the wild, and millions of dialects to those as well. Because I grew up in Luxembourg, I got to get a taste of a pack of languages at a very young age.
                        <br><br>
                        The languages I currently speak are:
                    </p>
                    <br><br>
                    <table>
                        <tr>
                            <th>Български (Bulgarian)</th>
                            <th>Native</th>
                        </tr>
                        <tr>
                            <th>Deutsch (German)</th>
                            <th>Fluent</th>
                        </tr>
                        <tr>
                            <th>English (English)</th>
                            <th>Fluent</th>
                        </tr>
                        <tr>
                            <th>Letzeburgesch (Luxembourgish)</th>
                            <th>Moderate</th>
                        </tr>
                        <tr>
                            <th>日本語 (Japanese)</th>
                            <th>Beginner</th>
                        </tr>
                        <tr>
                            <th>Français (French)</th>
                            <th>Beginner</th>
                        </tr>
                    </table>
                </div>
            </div>
        
            <!-- Programming -->
            <div class='infobox reverse'>
                <figure class='infoboxData'>
                    <div style='background-color: black' class='image'></div>
                    <div style='background-color: black' class='image'></div>
                </figure>
                <div class='infoboxData'>
                    <h4>Programming</h4>
                    <br>
                    <p>
                        As you’ve already read in my basic introduction, I have not too little knowledge in the art of programming. I've started my programming-journey back in 2014, and I'm looking forward to my future projects every single day!
                        <br><br>
                        If you're interested to see the source code of some of my projects, check out my GitHub account: <a href='https://github.com/Vlajd' target='_blank'><strong>github.com/Vlajd</strong></a>
                        <br><br>
                        Also, check out the open-source game engine I'm developing in Rust: <a href='https://github.com/slackers123/engine' target='_blank'><strong>github.com/slackers123/engine</strong></a>
                    </p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Contact -->
    <section id='Contact'>
        <h1>Contact</h1>
        <div class='infobox'>
            <div id='ContactData' class='infoboxData'>
                <a href='mailto: boris.kostadinov@graphische.net'><h2>Boris.Kostadinov@Graphische.net</h2></a>
                <p>I am always open to inquiries or questions, so do not hesitate to contact me!</p>
                <div id='ContactMedia'>
                    <!-- E-Mail -->
                    <a href='mailto: boris.kostadinov@graphische.net'><div class='contactMediaIcon'><svg width="65.402" height="52.321" viewBox="0 0 66 52.321"><path d="M61.862,6H9.54a6.531,6.531,0,0,0-6.507,6.54L3,51.781a6.559,6.559,0,0,0,6.54,6.54H61.862a6.559,6.559,0,0,0,6.54-6.54V12.54A6.559,6.559,0,0,0,61.862,6Zm0,13.08L35.7,35.431,9.54,19.08V12.54L35.7,28.891,61.862,12.54Z" transform="translate(-2.5 -6)"/></svg></div></a>
                    <!-- Github -->
                    <a href='https://github.com/Vlajd' target='_blank'><div class='contactMediaIcon'><svg width="68.674" height="68.674" viewBox="0 0 68.674 68.674"><path d="M36.587,2.25C17.625,2.25,2.25,18.024,2.25,37.461a35.143,35.143,0,0,0,23.484,33.4,2.691,2.691,0,0,0,.583.061,1.661,1.661,0,0,0,1.763-1.748c0-.843-.031-3.05-.046-5.994a15.7,15.7,0,0,1-3.464.414c-6.607,0-8.109-5.135-8.109-5.135-1.564-4.062-3.817-5.151-3.817-5.151-2.989-2.1-.015-2.161.215-2.161h.015c3.449.307,5.258,3.648,5.258,3.648,1.717,3,4.016,3.848,6.07,3.848a9.65,9.65,0,0,0,3.924-.92A7.607,7.607,0,0,1,30.3,53.02c-7.618-.889-15.636-3.909-15.636-17.4a13.781,13.781,0,0,1,3.526-9.443,12.961,12.961,0,0,1,.337-9.32,2.858,2.858,0,0,1,.766-.077c1.242,0,4.047.475,8.676,3.694a31.917,31.917,0,0,1,17.2,0c4.629-3.219,7.435-3.694,8.676-3.694a2.858,2.858,0,0,1,.766.077,12.961,12.961,0,0,1,.337,9.32,13.838,13.838,0,0,1,3.526,9.443c0,13.52-8.032,16.494-15.682,17.368,1.226,1.088,2.33,3.234,2.33,6.515,0,4.706-.046,8.508-.046,9.657a1.653,1.653,0,0,0,1.748,1.763,2.966,2.966,0,0,0,.613-.061,35.137,35.137,0,0,0,23.484-33.4C70.924,18.024,55.549,2.25,36.587,2.25Z" transform="translate(-2.25 -2.25)"/></svg></div></a>
                    <!-- Youtube -->
                    <a href='https://www.youtube.com/channel/UCbI6zfXhfQ7pFb8ezgJwLkw' target='_blank'><div class='contactMediaIcon'><svg width="65.653" height="46.162" viewBox="0 0 65.653 46.162"><path d="M65.331,11.723a8.249,8.249,0,0,0-5.8-5.842C54.407,4.5,33.876,4.5,33.876,4.5s-20.53,0-25.65,1.381a8.25,8.25,0,0,0-5.8,5.842c-1.372,5.153-1.372,15.9-1.372,15.9s0,10.752,1.372,15.9a8.126,8.126,0,0,0,5.8,5.749c5.12,1.381,25.65,1.381,25.65,1.381s20.53,0,25.65-1.381a8.126,8.126,0,0,0,5.8-5.749c1.372-5.153,1.372-15.9,1.372-15.9s0-10.752-1.372-15.9ZM27.162,37.389V17.866l17.159,9.762L27.162,37.389Z" transform="translate(-1.05 -4.5)"/></svg></div></a>
                    <!-- Instagram -->
                    <a href='https://www.instagram.com/vlajd_/' target='_blank'><div class='contactMediaIcon'><svg width="61.46" height="61.46" viewBox="0 0 61.46 61.46"><g transform="translate(-4.5 -4.5)"><path d="M48.034,9.622a12.842,12.842,0,0,1,12.8,12.8V48.034a12.842,12.842,0,0,1-12.8,12.8H22.426a12.842,12.842,0,0,1-12.8-12.8V22.426a12.842,12.842,0,0,1,12.8-12.8H48.034m0-5.122H22.426A17.979,17.979,0,0,0,4.5,22.426V48.034A17.979,17.979,0,0,0,22.426,65.96H48.034A17.979,17.979,0,0,0,65.96,48.034V22.426A17.979,17.979,0,0,0,48.034,4.5Z"/><path d="M27.466,16.682a3.841,3.841,0,1,1,3.841-3.841A3.832,3.832,0,0,1,27.466,16.682Z" transform="translate(24.409 5.743)"/><path d="M26.615,16.372A10.243,10.243,0,1,1,16.372,26.615,10.253,10.253,0,0,1,26.615,16.372m0-5.122A15.365,15.365,0,1,0,41.98,26.615,15.369,15.369,0,0,0,26.615,11.25Z" transform="translate(8.615 8.615)"/></g></svg></div></a>
                </div>
            </div>
            <figure>
                <div style='background-color: black' class='image'></div>
                <figcaption><strong>Boris Krassimirov Kostadinov<br>Vienna, Austria</strong></figcaption>
            </figure>
        </div>
    </section>
</main>

<!-- End Footer -->
<footer>
    ⒸBoris Kostadinov 2022
</footer>

</div>