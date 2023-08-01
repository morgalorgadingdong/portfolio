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

let introOverlay
let loaderLine
let loaderLineMask

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
                scrollFunction()
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
    // console.log('Header Height:', headerHeight);
    // console.log('Project Height:', projectHeight);
    // console.log('Body Height:', documentBody.style.height);
    
    introOverlay = document.getElementById("intro-overlay");
    loaderLine = document.getElementById("loader-line");
    loaderLineMask = document.getElementById("loader-line-mask");


    setTimeout(() => {
        // loaderLine.style.height = 0
        // loaderLine.style.width = 0
        // loaderLineMask.style.height = 0
        loaderLineMask.style.width = 0
        setTimeout(() => {
        introOverlay.style.opacity = "0";
        introOverlay.style.zIndex = "-1";
            }, 700);
    }, 500);

    

    setTimeout(() => {
            updateHeight()
        }
            , 250)

});

function navigateToProjectsPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
    projectsPage.style.transform = "translateX(0)";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    underline.style.left = "50%";
    underline.style.width = '90px';


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
    underline.style.width = '60px';    

        if (window.screen.width < 1200) {
            underline.style.left = `calc(0.4rem + ${underlineOffset}px - 5px)`;
        } else {
            underline.style.left = `calc(${underlineOffset}px - 11px - 4px)`;
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
    underline.style.width = '70px';

    if (window.screen.width < 1200) {
        underline.style.left = `calc(100% -  ${underlineOffset}px - 0.4rem)`;
        } else {
            underline.style.left = `calc(100% -  ${underlineOffset}px + 11px - 1px)`;
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
    function revealPage() {

    }


    function scrollToBottom() {
        window.scrollTo(0, document.body.offsetHeight);
    }

    function scrollToTop() {
        window.scrollTo(0, 0);
        // document.getElementById("scrollToTop").style.opacity = 0;
    }

    function scrollFunction() {
        if (document.body.scrollTop > 20 || document.documentElement.scrollTop > 20) {
            document.getElementById("scrollToTop").style.opacity = 1;
        } else {
            document.getElementById("scrollToTop").style.opacity = 0;
        }
        updateHeight(() => {
                scrollFunction()
            }
                , 250)
    }

    // create a loading bar
    // function createLoadingBar() {
    //     let loadingBar = document.createElement("div");
    //     loadingBar.id = "loading-bar";
    //     loadingBar.style.width = "0%";
    //     loadingBar.style.height = "100%";
    //     loadingBar.style.backgroundColor = "black";
    //     loadingBar.style.position = "absolute";
    //     loadingBar.style.top = "0";
    //     loadingBar.style.left = "0";
    //     loadingBar.style.zIndex = "1000";
    //     loadingBar.style.transition = "width 0.5s ease-in-out";
    //     document.body.appendChild(loadingBar);
    // }


</script>

<div id="intro-overlay">
    <!-- Create a loading bar -->
    <!-- <div class="loader-circle"></div> -->
    <div id="loader-line-mask">
      <div id="loader-line"></div>
    </div>

    <!-- <h2>Morgan Folz</h2> -->
</div>

<div on:click={() => scrollToBottom()} id="contact" class="d-flex">
    <p class="px-3">contact</p>
    <i class="fa-regular fa-message"></i>
</div>

<div id="scrollToTop" on:click={() => scrollToTop()} >
    <i class="fa-solid fa-angle-up"></i>
</div>

<header id="header" class="col-12 col-xl-10 d-flex justify-content-center flex-wrap mb-5">
    <div id="headline-container" class="col-12 px-3 px-xl-0 d-flex justify-content-start justify-content-md-center flex-wrap">
        <h1 class="text-start">Morgan Folz</h1>
        <!-- <ul class="d-flex flex-wrap justify-content-start align-content-center align-items-start"> -->
        <ul class="d-flex flex-wrap flex-column justify-content-center">
            <li class="col-12 mb-1 d-block d-md-none">full stack engineer</li>
            <li class="col-12 mb-1 d-none d-md-block">full<br> stack<br> engineer</li>
            <!-- <li class="col-12 mb-1"></li> -->
            <!-- <li class="col-12 ">r</li> -->
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
    #loader-circle {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 120px;
  height: 120px;
  border-radius: 50%;
  box-shadow: inset 0 0 0 1px rgba(255,255,255,.1);
  margin-left: -60px;
  margin-top: -60px;
  /* // .animation(fade 1.2s infinite ease-in-out); */
}

#loader-line-mask {
  position: absolute;
  left: 50%;
  top: 50%;
  width: 60px;
  height: 120px;
  margin-left: -60px;
  margin-top: -60px;
  overflow: hidden;
  transform-origin: 60px 60px;
  
  animation: rotate 1.2s infinite linear;
  transition: all 0.25s ease-in-out;
}

/* -webkit-mask-image: -webkit-linear-gradient(top, rgba(0,0,0,1), rgba(0,0,0,0)); */

#loader-line {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    box-shadow: inset 0 0 0 1px rgba(255,255,255,.5);
    transition: all 0.25s ease-in-out;
  }

  @keyframes rotate { 0% { transform: rotate(0deg);} 100% { transform: rotate(360deg);}}

#intro-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: var(--color-primary);
    z-index: 100;
    opacity: 1;
    transition: all 0.5s ease-in-out;
}



    #scrollToTop {
        position: fixed;
        bottom: 2rem;
        right: 2rem;
        font-size: 2rem;
        color: var(--color-primary);
        opacity: 0;
        transition: all 0.3s ease-in-out;
        z-index: 10;
    }

    #scrollToTop:hover {
        cursor: pointer;
    }

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
        color: var(--color-primary);
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
        padding-left: 1rem;
        width: fit-content;
    }

    #headline-container > ul > li {
        font-size: 1.5rem;
        font-weight: 300;
        line-height: 1.5rem;
        text-transform: lowercase;
        color: var(--color-primary);
        
        font-style: italic;
    }

    header h1, #intro-overlay h2 {
        font-size: 5rem;
        line-height: 5rem;
        font-weight: 700;
        
        height: fit-content;
        /* padding-bottom: 0.5rem;
        border-bottom: solid 2px var(--color-primary); */
        text-transform: uppercase;
        padding-right: 1rem;
    }

    #intro-overlay h2 {
        color: var(--color-background);
        z-index: 101;
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


    @media (max-width: 375px) {
        header h1 {
            font-size: calc(100vw / 75 * 16);
            line-height: calc(100vw / 75 * 16);
        }
    }

</style>
