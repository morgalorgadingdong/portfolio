<script>


    import Footer from './Footer.svelte';

</script>

<div class="col-12 d-flex flex-wrap px-0 justify-content-center">
    <div id="" class="col-12 col-xl-10 d-flex justify-content-center">
        <div class="col-12 col-md-8 px-3 px-md-0 d-flex justify-content-start flex-wrap align-content-start">
            <img src="./img/introduction-text.png" alt="Hello, my name is Morgan" class="col-10 col-sm-8 my-3">
            <!-- <h3 class="mb-5 mt-0 mt-md-5 col-12 text-center">Hello, my name is Morgan</h3> -->
            <p class="mb-5">I am a small business owner, designer and developer based in Bend, Oregon. Utlizing a broad range of skills developed over a diverse career, I help small businesses and entrepenuers take their brand's to the next level through thoughtful, tailor made websites and web applications.</p>
            <img src="./img/about-mobile.png" alt="" class="d-block d-sm-none about-pic mobile">
            <img src="./img/about-desktop.png" alt="" class="d-none d-sm-block about-pic desktop">
            
        </div>
    
    </div>
<Footer />
</div>

<style>
    .about-pic {
        width: 100%;
        object-position: center;
        object-fit: contain;
    }

    .about-pic.mobile {
        aspect-ratio: 523 / 806;
    }

    .about-pic.desktop {
        aspect-ratio: 1035 / 537;
    }

    img.col-10 {
        aspect-ratio: 781 / 135;
        object-fit: contain;
        
        /* border-bottom: solid 2px var(--color-primary); */
    }

    h3 {
        font-style: italic;
    }

    p {
        height: fit-content;
    }
</style>