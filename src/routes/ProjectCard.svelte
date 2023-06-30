<script>
    export let project;
    let imgSrc = `./img/projects/${project.id}. ${project.name}/${project.nickname}-banner.jpg`;
</script>
<a href="{project.url}" target="_blank" rel="">
    <div class="img-container mb-3">
        <img src= { imgSrc } alt=""/>
    </div>
        <div class="col-12 d-flex justify-content-between mt-2">
        <h4>{project.name}</h4>
        <h4>{project.date}</h4>
    </div>
</a>


<style>
    .img-container {
        width: 100%;
        aspect-ratio: 558 / 294;
        border-radius: 2.107526882% / 4%;
        /* box-shadow: 0px 5px 10px 0px rgba(0,0,0,0.5); */
        overflow: hidden;
        position: relative;
        box-shadow: 0px 5px 10px 0px rgba(0,0,0,0.75);
        transition: all 0.3s ease-in-out;
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
        transition: all 0.3s ease-in-out;

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
        transition: opacity 0.3s ease-in-out;
    }

    .img-container:hover::after {
        opacity: 1;
    } */

    a:hover .img-container {
        box-shadow: 0px 10px 20px 0px rgba(0,0,0,0.75);
    }
    a:hover img {
        transform: scale(1.05);
    }

    a {
        text-decoration: none;
        color: var(--color-primary);
    }


    a:hover {
        cursor: pointer;
    }

    /* a:hover img {
        box-shadow: 3px 3px 15px 0px rgba(0,0,0,0.75);
    } */


    h4 {
        font-weight: 400;
    }
    
</style>