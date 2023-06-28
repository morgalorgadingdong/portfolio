<script>
    import { page } from '$app/stores';
    import { onMount } from 'svelte';
    import About from './About.svelte';
    import Projects from './Projects.svelte';
    import Resume from './Resume.svelte';


  

let projectsPage;
let aboutPage;
let resumePage;
let underline;
let body;
let height;
let documentBody;

let underlineWidth;
let underlineOffset;

let projectHeight;
let aboutHeight;
let resumeHeight;
let header;
let headerHeight;

let currentPage;

function updateHeight() {
    if (currentPage == 'projects') {
        projectHeight = projectsPage.offsetHeight;
        body.style.height = projectHeight + 'px';
        // let height = projectHeight + headerHeight;
        // documentBody.style.height = `calc(6rem + ${height}px`;

    } else if (currentPage == 'about') {
        aboutHeight = aboutPage.offsetHeight;
        body.style.height = aboutHeight + 'px';
        // let height = aboutHeight + headerHeight;
        // documentBody.style.height = `calc(6rem + ${height}px`;

    } else if (currentPage == 'resume') {
        resumeHeight = resumePage.offsetHeight;
        body.style.height = resumeHeight + 'px';
        // let height = resumeHeight + headerHeight;
        // documentBody.style.height = `calc(6rem + ${height}px`;

    } 
    setTimeout(() => {
                updateHeight()
            }
                , 500)
}


onMount(() => {
    projectsPage = document.getElementById("projects");
    aboutPage = document.getElementById("about");
    resumePage = document.getElementById("resume");
    underline = document.getElementById("underline");
    header = document.getElementById("header");

    underlineWidth = 90;
    underlineOffset = underlineWidth / 2;

    body = document.getElementById("body");
    documentBody = document.body;
    aboutPage.style.opacity = "0";
    resumePage.style.opacity = "0";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    projectHeight = projectsPage.offsetHeight;
    aboutHeight = aboutPage.offsetHeight;
    resumeHeight = resumePage.offsetHeight;
    headerHeight = header.offsetHeight;
    body.style.height = projectHeight + 'px';
    height = projectHeight + headerHeight;
    currentPage = 'projects';
    // documentBody.style.height = `calc(6rem + ${height}px`;
    console.log('Header Height:', headerHeight);
    console.log('Project Height:', projectHeight);
    console.log('Body Height:', documentBody.style.height);
    setTimeout(() => {
            updateHeight()
        }
            , 500)

});

function navigateToProjectsPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
    projectsPage.style.transform = "translateX(0)";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    underline.style.left = "50%";


    body.style.height = projectHeight + 'px';
    currentPage = 'projects';

    let height = projectHeight + headerHeight;
    // documentBody.style.height = `calc(6rem + ${height}px`;
    // console.log('Header Height:', headerHeight);
    // console.log('Project Height:', projectHeight);
    // console.log('Body Height:', documentBody.style.height);
    
}

function navigateToAboutPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
        projectsPage.style.transform = "translateX(100%)";
        aboutPage.style.transform = "translateX(0)";
        resumePage.style.transform = "translateX(200%)";
        
        if (window.screen.width < 1200) {
            underline.style.left = `calc(0.4rem + ${underlineOffset}px`;
        } else {
            underline.style.left = `calc(${underlineOffset}px - 11px)`;
        }

        // console.log(aboutPage)
        // height = aboutPage.offsetHeight;
        body.style.height = aboutHeight + 'px';
        currentPage = 'about';
        let height = aboutHeight + headerHeight;
        // documentBody.style.height = `calc(6rem + ${height}px`;
        // console.log('Header Height:', headerHeight);
        // console.log('About Height:', aboutHeight);
        // console.log('Body Height:', documentBody.style.height);
        // underline.style.transform = "translateX(-200%)";
}

function navigateToResumePage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
    projectsPage.style.transform = "translateX(-100%)";
    aboutPage.style.transform = "translateX(-200%)";
    resumePage.style.transform = "translateX(0)";
        

    if (window.screen.width < 1200) {
        underline.style.left = `calc(100% -  ${underlineOffset}px - 0.4rem)`;
        } else {
            underline.style.left = `calc(100% -  ${underlineOffset}px + 11px)`;
        }
    
        
        
        body.style.height = resumeHeight + 'px';
        currentPage = 'resume';
        let height = resumeHeight + headerHeight;
        // documentBody.style.height = `calc(6rem + ${height}px`;
        console.log('Header Height:', headerHeight);
        console.log('Resume Height:', resumeHeight);
        console.log('Body Height:', documentBody.style.height);
        
    
}
    // Header passes up current page
    
    function scrollToBottom() {
        window.scrollTo(0, document.body.offsetHeight);
    }

</script>

<div on:click={() => scrollToBottom()} id="contact" class="d-flex">
    <p class="px-3">contact</p>
    <i class="fa-regular fa-message"></i>
</div>

<header id="header" class="col-12 col-xl-10 d-flex justify-content-center flex-wrap mb-5">
    <div id="headline-container" class="col-12 px-3 px-xl-0 d-flex justify-content-start flex-wrap">
        <h1 class="text-start">Morgan Folz</h1>
        <ul class="d-flex flex-wrap justify-content-start align-content-center align-items-start">
            <li class="col-12">designer</li>
            <li class="col-12">developer</li>
            <li class="col-12">problem solver</li>
        </ul>
    </div>
    
    <ul class="col-12 px-3 px-xl-0 mt-3">
        <a on:click={() => navigateToAboutPage()} class="text-center left nav-item"><li><h2>About</h2></li></a>
        <a on:click={() => navigateToProjectsPage()} class="text-center centered nav-item"><li><h2>Projects</h2></li></a>
        <a on:click={() => navigateToResumePage()} class="text-center right nav-item"><li ><h2>Resume</h2></li></a>
    </ul>
    <div id="underline-container" class="col-12 d-flex justify-content-center">
        <div id="underline" class=""></div>
    </div>
</header>
<div id="body" class="mt-5">
    <div id="about" class="page d-flex justify-content-center flex-wrap">
        <About />
    </div>
    <div id="projects" class="page d-flex justify-content-center flex-wrap">
        <Projects />
    </div>
    <div id="resume" class="page d-flex justify-content-center flex-wrap">
            <Resume />
    </div>
</div>

<style>
    i {
        font-size: 1.5rem;
    }

    #contact > p {
        transform: translateX(2rem);
        opacity: 0;
        transition: all 0.3s ease-in-out;
    }

    #contact {
        position: absolute;
        top: 2rem;
        right: 2rem;
    }

    #contact:hover {
        cursor: pointer;
    }

    #contact:hover p {
        transform: translateX(0);
        opacity: 1;
        transition: all 0.3s ease-in-out;
    }

    .tagline {
        font-style: italic;
        font-size: 2.3rem;
        /* margin: 1rem auto 5rem auto; */
        text-transform: lowercase;
        /* font-weight: 300; */
        color: var(--color-primary);
    }
    li > h2 {
        font-size: 1.2rem;
        

    }
    
    #headline-container {
        padding-top: 5rem;
        padding-bottom: 3rem; 
    }

    #headline-container > ul {
        row-gap: 0rem;
        border-left: solid 2px var(--color-primary);
        padding-left: 1rem
    }

    #headline-container > ul > li {
        font-size: 1.5rem;
        font-weight: 300;
        line-height: 1.5rem;
        text-transform: lowercase;
        color: var(--color-primary);
        
        font-style: italic;
    }

    header h1 {
        font-size: 5rem;
        line-height: 5rem;
        font-weight: 700;
        color: var(--color-primary);
        height: fit-content;
        /* padding-bottom: 0.5rem;
        border-bottom: solid 2px var(--color-primary); */
        text-transform: uppercase;
        padding-right: 1rem;
    }


    ul {
        display: grid;
        grid-template-columns: 1fr auto 1fr;
        grid-gap: 1rem;
    }

    ul > .left {
        justify-self: start;
    }

    ul > .right {
        justify-self: end;
    }

    ul > .centered {
        justify-self: center;
    }

    a {
        text-decoration: none;
        color: var(--color-primary);
    }
    #underline-container {
        
        padding: 0;
        position: relative;

    }
    #underline {
        height: 3px;
        width: 90px;
        border-bottom: solid 3px var(--color-primary);
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        transition: all 0.5s ease;
    }
    


    #projects, #about, #resume {
        width: 100vw;
        width: 100svw;
        min-height: 100vh;
        min-height: 100svh;
        position: absolute;
        top: 0;
        left: 0;
        transition: transform 0.5s ease;
    }

    #about, #resume {
        opacity: 0;
    }

    li {
        list-style: none;
    }

    .nav-item:hover {
        cursor: pointer;
    }



</style>
