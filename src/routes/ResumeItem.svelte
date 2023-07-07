<script>
    import { slide } from "svelte/transition";
	let isOpen = false
	const toggle = () => isOpen = !isOpen
    export let item;
    let imgSrc = `./img/resume/${item.nickname}.jpg`;
</script>


<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click={toggle} aria-expanded={isOpen} class="d-flex justify-content-between item flex-wrap py-5">
    {#if item.company}

        <div class="d-flex justify-content-start col-12 col-md-4 px-0">
            <img src="./img/arrow.svg" alt="arrow" class="arrow">
            <h3 class="text-start"><b>{item.title}</b> at {item.company}</h3>
        </div>
        
        {#if item.start == item.end}
         <h3 class="col-12 col-lg-auto text-end">{item.start}</h3>
         {:else}
         <h3 class="col-12 col-lg-auto text-end">{item.start} - {item.end}</h3>
        {/if}
        {#if isOpen}
        <ul transition:slide={{ duration: 500 }} class="col-12 pt-3 px-0 d-flex flex-wrap">
            {#if item.picture}
                <div class="col-12 col-lg-4 my-3 px-3">
                    <img src={imgSrc} alt="company logo" class="img-fluid">
                </div>
                <div class="col-12 col-md-8 my-md-3 px-3">
                {#each item.description as description}
                       
                    {#if description.bold}    
                        <p class="mb-0">
                            <b>{description.text}</b>
                        </p>
                    {:else}
                        <p class="mt-0">
                            {description.text}
                        </p>
                    {/if}
                    
                {/each}
                <div class="d-flex justify-content-start flex-wrap">
                    {#each item.skills as skill}
                        <span class="skill-tag">{skill}</span>
                    {/each}
                </div>
             </div>
            {:else}
            <div class="col-12 px-3">
            {#each item.description as description}
                
                {#if description.bold}    
                    <p class="mb-0">
                        <b>{description.text}</b>
                    </p>
                {:else}
                    <p class="mt-0">
                        {description.text}
                    </p>
                {/if}
                
            {/each}
                <div class="d-flex justify-content-start flex-wrap">
                    {#each item.skills as skill}
                        <span class="skill-tag">{skill}</span>
                    {/each}
                </div>
            </div>
            {/if}
        </ul>
        {/if}
    {:else if item.skill}
        <div class="d-flex justify-content-start">
            <img src="./img/arrow.svg" alt="arrow" class="arrow">
            <h3 class="text-start">{item.skill}</h3>
        </div>

        {#if isOpen}
        <ul transition:slide={{ duration: 500 }} class="col-12">
            <p>{item.description}</p>
            <div class="d-flex justify-content-start flex-wrap">
            {#each item.tools as tool}
                        <span class="skill-tag">{tool}</span>
            {/each}
        </div>
        </ul>
        {/if}
    {:else if item.school}
        <div class="d-flex">
            <div class="arrow-container">
                <img src="./img/arrow.svg" alt="arrow" class="arrow">
            </div>
            <h3 class="text-start">{item.school}<br>{item.degree}</h3>
        </div>
        <div>
            <h3 class="text-end">Graduated: {item.graduated}<br>GPA: {item.gpa}</h3>
        </div>    
        

        {#if isOpen}
        <ul transition:slide={{ duration: 500 }} class="col-12 pt-3 px-0 d-flex flex-wrap">
            {#if item.picture}
                <div class="col-12 col-lg-4 my-3 px-3">
                    <img src={imgSrc} alt="company logo" class="img-fluid">
                </div>
                <div class="col-12 col-md-8 my-md-3 px-3">
                {#each item.description as description}
                       
                    {#if description.bold}    
                        <p class="mb-0">
                            <b>{description.text}</b>
                        </p>
                    {:else}
                        <p class="mt-0">
                            {description.text}
                        </p>
                    {/if}
                    
                {/each}
             </div>
            {:else}
            <div class="col-12 px-3">
            {#each item.description as description}
                
                {#if description.bold}    
                    <p class="mb-0">
                        <b>{description.text}</b>
                    </p>
                {:else}
                    <p class="mt-0">
                        {description.text}
                    </p>
                {/if}
                
            {/each}
            </div>
            {/if}
        </ul>
    {/if}

    {/if}


</div>


<style>

    ul img {
        max-height: 200px;
        object-fit: cover;
        object-position: center;
        width: 100%;
    }

    .skill-tag {
        margin: 0.5rem 0.25rem;
        border: solid 1px var(--color-primary);
        border-radius: 5px;
        padding: 0.25rem;
    }

    b {
        color: var(--color-primary);
    }

    .item {
        padding: 1.5rem 0;
        border-bottom: 1px solid var(--color-primary);
    }

h3 {
    margin-bottom: 0;
}


    .arrow {
        margin: 0 0.5rem;
        max-width: 20px;
    }

    .arrow-container {
        display: flex;
        justify-content: center;
        align-items: center;
    }

a {
    text-decoration: none;
    color: var(--color-primary);
}

[aria-expanded=true] .arrow { transform: rotate(0.25turn);}

.arrow { transition: transform 0.25s ease-in;
}

.item:hover {
    cursor: pointer;
}

ul {
    padding-left: 2.3rem;
}

ul > p {
    font-size: 1rem;
    margin-top: 1rem;
}

</style>