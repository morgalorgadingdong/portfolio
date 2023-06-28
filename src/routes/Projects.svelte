<script>
    import {projects} from './projects.js';
    import ProjectCard from './ProjectCard.svelte';
    import Footer from './Footer.svelte';
    console.log(projects)
</script>

<div class="col-12 d-flex justify-content-center flex-wrap px-0">
    <div id="project-container" class="col-12 col-xl-10 px-3 px-xl-0">
        {#each projects as project}
            <div class="item">
                <ProjectCard project={project}/>
            </div>   
        {/each}
    </div>
    <Footer />
</div>



<style>
    #project-container {
        display: grid;
        grid-template-columns: 1fr 1fr;
        justify-items: center;
        gap: 10vw 5vw;
    }

    @media (max-width: 576px) {
        #project-container {
            grid-template-columns: 1fr;
        }
    }
</style>


