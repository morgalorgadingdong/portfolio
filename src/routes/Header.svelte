<script>
	import { page } from '$app/stores';
	import logo from '$lib/img/logo.png';

    

    export let currentPage

    function changePage(page) {
        currentPage = page
        console.log(page)
    }
</script>


<header class="col-12 d-flex justify-content-center flex-wrap">
    <h1 class="col-12 text-center">Morgan Folz</h1>
    <ul class="col-12 d-flex justify-content-between">
        <li on:click={() => changePage('about')}>About</li>
        <li on:click={() => changePage('projects')}>Projects</li>
        <li on:click={() => changePage('resume')}>Resume</li>
    </ul>
</header>

<style>
    li {
        list-style: none;
    }
</style>