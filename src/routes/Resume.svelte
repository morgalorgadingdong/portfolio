<script>
    import { resume } from './resume.js';
    import ResumeItem from './ResumeItem.svelte';
    import Footer from './Footer.svelte';
</script>




<div class="col-12 d-flex flex-wrap px-0 justify-content-center">
<div id="" class="col-12 col-xl-10 px-3 px-xl-0 d-flex justify-content-center flex-wrap">
    {#each resume as section}
        <div class="col-12 mb-5 pb-5">
            <h2 class="pb-3"><b>{section.section}</b></h2>
            {#each section.items as item}
                <ResumeItem item={item}/>
            {/each}
        </div>
    {/each}
</div>
<Footer />
</div>



<style>
    h2 {
        border-bottom: 1px solid var(--color-primary);
    }
</style>
