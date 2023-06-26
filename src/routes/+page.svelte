<script>
    import { page } from '$app/stores';
    import { onMount } from 'svelte';
    import About from './About.svelte';
    import Projects from './Projects.svelte';
    import Resume from './Resume.svelte';
    import currentPage from './Header.svelte';
    

let projectsPage;
let aboutPage;
let resumePage;
let underline;
let body;
let height;

let underlineWidth;
let underlineOffset;
let underlineLeft;
let underlineRight;

onMount(() => {
    projectsPage = document.getElementById("projects");
    aboutPage = document.getElementById("about");
    resumePage = document.getElementById("resume");
    underline = document.getElementById("underline");
    
    underlineWidth = 90;
    underlineOffset = underlineWidth / 2;

    body = document.getElementById("body");
    aboutPage.style.opacity = "0";
    resumePage.style.opacity = "0";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    
    height = projectsPage.scrollHeight;
    body.style.height = height + 'px';
    console.log(height);
    
});

function navigateToProjectsPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
    projectsPage.style.transform = "translateX(0)";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    underline.style.left = "50%";

    height = projectsPage.scrollHeight;
    body.style.height = height + 'px';
    console.log(projectsPage);
    
}

function navigateToAboutPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
        projectsPage.style.transform = "translateX(100%)";
        aboutPage.style.transform = "translateX(0)";
        resumePage.style.transform = "translateX(200%)";
        underline.style.left = underlineOffset + 'px';
        console.log(underline.style.left)

        height = aboutPage.scrollHeight;
        body.style.height = height + 'px';
        console.log(height);
        // underline.style.transform = "translateX(-200%)";

        
    
    
}

function navigateToResumePage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
    projectsPage.style.transform = "translateX(-100%)";
    aboutPage.style.transform = "translateX(-200%)";
    resumePage.style.transform = "translateX(0)";
        
    underline.style.left = `calc(100% -  ${underlineOffset}px`;
        
        height = projectsPage.scrollHeight;
        body.style.height = height + 'px';
        
    
}
    // Header passes up current page
    

</script>

<header class="col-12 col-xl-8 d-flex justify-content-center flex-wrap mb-5">
    <h1 class="col-12 text-center">Portfolio</h1>
    <ul class="col-12 px-0">
        <a on:click={() => navigateToAboutPage()} class="text-center left"><li><h2>About</h2></li></a>
        <a on:click={() => navigateToProjectsPage()} class="text-center centered"><li><h2>Projects</h2></li></a>
        <a on:click={() => navigateToResumePage()} class="text-center right"><li ><h2>Resume</h2></li></a>
    </ul>
    <div id="underline-container" class="col-12 d-flex justify-content-center">
        <div id="underline" class=""></div>
    </div>
</header>
<div id="body" class="">
    <div id="about" class="page d-flex justify-content-center">
        <About />
    </div>
    <div id="projects" class="page d-flex justify-content-center">
        <Projects />
    </div>
    <div id="resume" class="page d-flex justify-content-center">
            <Resume />
    </div>
</div>

<style>
    li > h2 {
        font-size: 1.2rem;

    }
    
    header h1 {
        font-size: 3rem;
        font-weight: 700;
        color: var(--color-primary);
        margin: 5rem auto;
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

    li:hover {
        cursor: pointer;
    }

</style>
