<script>
    export let project;
    let imgSrc = `./img/projects/${project.id}. ${project.name}/${project.nickname}-banner.jpg`;
</script>
<a href="{project.url}" target="_blank" rel="">
    <div class="img-container mb-3">
        <img src= { imgSrc } alt=""/>
        <div class="badge-container px-3 px-md-5">
            <div class="col-12">
                <h4 class="col-12">Skills</h4>
                {#each project.skills as skill}
                    <span class="badge text-light m-2">{skill}</span>
                {/each}
            </div>
            <div class="col-12">
            <h4 class="col-12">Stack</h4>
            {#each project.tags as tag}
                <span class="badge text-light m-2">{tag}</span>
            {/each}
        </div>
        </div>
    </div>
        <div class="col-12 d-flex justify-content-between mt-2">
        <h4>{project.name}</h4>
        <h4>{project.date}</h4>
    </div>
</a>


<style>
    * {
        --animation-duration: 0.5s;
    }

    .badge-container {
        position: absolute;
        top: 0;
        left: 0;
        z-index: 1;
        width: 100%;
        height: 100%;
        display: flex;
        flex-wrap: wrap;
        justify-content: start;
        align-items: center;
        transition: all ease-in-out var(--animation-duration);
        opacity: 0;
    }   

    .badge-container h4 {
        font-weight: 400;
        font-size: 1.2rem;
        margin-bottom: .5rem;
        color: white !important;
        border-bottom: solid 1px white;
    }

    .badge {
        font-size: 0.8rem;
        border-radius: 0.25rem;
        
        transition: all var(--animation-duration) ease-in-out;
        border: solid 1px white;
    }

    

    /* :global(.badge:nth-child(1)) {
        animation: fadeIn 0.5s ease-in-out 0.5s forwards;
    } */

    .img-container {
        width: 100%;
        aspect-ratio: 558 / 294;
        border-radius: 2.107526882% / 4%;
        /* box-shadow: 0px 5px 10px 0px rgba(0,0,0,0.5); */
        overflow: hidden;
        position: relative;
        box-shadow: 0px 5px 10px 0px rgba(0,0,0,0.75);
        transition: all var(--animation-duration) ease-in-out;
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
        transition: all var(--animation-duration) ease-in-out;

    }

    /* .img-container::after {
        content: '';
        position: absolute;
        left: 0;
        z-index: -1;
        width: 100%;
        height: 100%;
        border-radius: 15px;
        box-shadow: 0px 10px 20px 0px rgba(0,0,0,0.75);
        opacity: 0;
        transition: opacity var(--animation-duration) ease-in-out;
    }

    .img-container:hover::after {
        opacity: 1;
    } */

    

    a {
        text-decoration: none;
        color: var(--color-primary);
    }


   

    /* a:hover img {
        box-shadow: 3px 3px 15px 0px rgba(0,0,0,0.75);
    } */


    h4 {
        font-weight: 400;
    }


    @media (pointer: fine), (hover: hover) {
        a:hover .img-container {
            box-shadow: 0px 10px 20px 0px rgba(0,0,0,0.75);
        }
        a:hover img {
            transform: scale(1.05);
        }
        a:hover {
            cursor: pointer;
        }
    }



    @media (min-width: 992px) {
        a:hover .badge-container {
            background-color: rgba(0,0,0,0.5);
            opacity: 1;
            transition: all var(--animation-duration) ease-in-out;
        }

        a:hover .badge {
            transition: all var(--animation-duration) ease-in-out;
        }
    }

</style>