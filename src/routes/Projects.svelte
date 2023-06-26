<script>
    import {projects} from './projects.js';
    import ProjectCard from './ProjectCard.svelte';
    console.log(projects)
</script>

<div id="" class="col-12 col-xl-10 container">
    {#each projects as project}
        <div class="item">
            <ProjectCard project={project}/>
        </div>   
    {/each}
</div>



<style>
    .container {
        display: grid;
        grid-template-columns: 1fr 1fr;
        justify-items: center;
        gap: 10vw 5vw;
    }

    @media (max-width: 576px) {
        .container {
            grid-template-columns: 1fr;
        }
    }
</style>


