<script>
    import { resume } from './resume.js';
    import ResumeItem from './ResumeItem.svelte';
</script>





<div id="" class="col-12 col-xl-10 px-0 d-flex justify-content-center flex-wrap">
    {#each resume as section}
        <div class="col-12 my-5">
            <h2>{section.section}</h2>
            {#each section.items as item}
                <ResumeItem item={item}/>
            {/each}
        </div>
    {/each}
</div>



<style>
    
</style>
