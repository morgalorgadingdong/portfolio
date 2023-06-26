<script>
    import { slide } from "svelte/transition";
	let isOpen = false
	const toggle = () => isOpen = !isOpen
    export let item;
</script>


<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click={toggle} aria-expanded={isOpen} class="d-flex justify-content-between item flex-wrap">
    {#if item.company}

        <div class="d-flex justify-content-start">
            <img src="./img/arrow.svg" alt="arrow" class="arrow">
            <h3 class="text-start">{item.title}</h3>
        </div>
        <h3 class="text-end">{item.start} - {item.end}</h3>

        {#if isOpen}
        <ul transition:slide={{ duration: 500 }} class="col-12">
            <p>{item.description}</p>
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
        <ul transition:slide={{ duration: 500 }} class="col-12">
            <p>{item.description}</p>
        </ul>
    {/if}

    {/if}


</div>


<style>

h3 {
    margin-bottom: 0;
}


    .arrow {
        margin: 0 0.5rem;
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
    font-size: 1.2rem;
}

</style>