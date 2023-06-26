<script>
    import { page } from '$app/stores';
    import { onMount } from 'svelte';

    import About from './About.svelte';
    import Projects from './Projects.svelte';
    import Resume from './Resume.svelte';
    import currentPage from './Header.svelte';

    console.log(currentPage)

let projectsPage;
let aboutPage;
let resumePage;
let underline;

onMount(() => {
    projectsPage = document.getElementById("projects");
    aboutPage = document.getElementById("about");
    resumePage = document.getElementById("resume");
    underline = document.getElementById("underline");
    aboutPage.style.opacity = "0";
    resumePage.style.opacity = "0";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    
});

function navigateToProjectsPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
    projectsPage.style.transform = "translateX(0)";
    aboutPage.style.transform = "translateX(-100%)";
    resumePage.style.transform = "translateX(100%)";
    underline.style.left = "50%";

    
    
}

function navigateToAboutPage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
        projectsPage.style.transform = "translateX(100%)";
        aboutPage.style.transform = "translateX(0)";
        resumePage.style.transform = "translateX(200%)";
        underline.style.left = "3%";
        // underline.style.transform = "translateX(-200%)";

        
    
    
}

function navigateToResumePage() {
    aboutPage.style.opacity = "1";
    resumePage.style.opacity = "1";
        projectsPage.style.transform = "translateX(-100%)";
        aboutPage.style.transform = "translateX(-200%)";
        resumePage.style.transform = "translateX(0)";
        underline.style.left = "97%";
        // underline.style.transform = "translateX(200%)";

        
    
}
    // Header passes up current page
    

</script>
<header class="col-12 d-flex justify-content-center flex-wrap">
    <h1 class="col-12 text-center">TEST</h1>
    <ul class="col-12 ">
        <li on:click={() => navigateToAboutPage()} class="text-center left">About</li>
        <li on:click={() => navigateToProjectsPage()} class="text-center centered">Projects</li>
        <li on:click={() => navigateToResumePage()} class="text-center right">Resume</li>
    </ul>
    <div id="underline-container" class="col-12 d-flex justify-content-center mx-5">
        <div id="underline" class="col-3 col-xl-2"></div>
    </div>
</header>
<div id="body" class="">
    <div id="about" class="page d-flex justify-content-center">
        <h2>
            About
        </h2>
    </div>
    <div id="projects" class="page d-flex justify-content-center">
        <h2>
            Projects
        </h2>
    </div>
    <div id="resume" class="page d-flex justify-content-center">
        <h2>
            Resume
        </h2>
    </div>
</div>

<style>
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
    #underline-container {
        
        padding: 0;
        position: relative;

    }
    #underline {
        height: 3px;
        border-bottom: solid 3px var(--color-primary);
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        transition: all 0.5s ease;
        max-width: 100px !important;
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
