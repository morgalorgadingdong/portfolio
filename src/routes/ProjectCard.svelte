<script>
    export let project;
    let imgSrc = `./img/projects/${project.id}. ${project.name}/${project.nickname}-banner.jpg`;
</script>

<img src= { imgSrc } alt=""/>
<div class="col-12 d-flex justify-content-between mt-2">
    <h4>{project.name}</h4>
    <h4>{project.date}</h4>
</div>


<style>
    img {
        width: 100%;
        object-fit: cover;
        object-position: center;
        aspect-ratio: 558 / 294;
        border-radius: 15px;
    }

    
</style>