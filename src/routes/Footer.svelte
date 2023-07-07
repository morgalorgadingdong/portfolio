<script>
    let email = 'morganfolz@gmail.com'
    let phone = '(503) 949 8766'
    let location = 'Bend, Oregon'
    let linkedin = 'https://www.linkedin.com/in/morgan-folz-6753aa99/'
    let github = 'https://github.com/morgalorgadingdong'
    let instagram = 'https://www.instagram.com/morgalorgadingdong/'
</script>

<footer id="footer" class="col-12 mt-5">
    <div class="col-12 d-flex justify-content-center justify-content-md-between flex-wrap my-5">
        <div class="col-10 col-md-3 d-flex justify-content-center px-5 mx-md-0 order-md-2">
            <img src="./img/signature.png"/>
        </div>
        <div class="col-12 col-md-4 order-md-1 d-flex justify-content-center flex-wrap align-content-center align-items-start my-3">
            <!-- <h3 class col-12 text-end="mb-3">Contact</h3> -->
            <p class="mb-0 col-12 text-center text-md-end"><a href="mailto:{email}">{email}</a></p>
            <p class="mb-0 col-12 text-center text-md-end"><a href="tel:{phone}">{phone}</a></p>
            <p class="mb-0 col-12 text-center text-md-end">{location}</p>
        </div>
        

        <div class="col-12 col-md-4 d-flex  justify-content-center justify-content-md-start order-md-3 align-items-center">
            <!-- <h3 class="mb-3">Social</h3> -->
            <a class="mx-3" href="{linkedin}" target="_blank" rel="no-referrer"><i class="fa-brands fa-linkedin"></i></a>
            <a class="mx-3" href="{github}" target="_blank" rel="no-referrer"><i class="fa-brands fa-square-github"></i></a>
            <a class="mx-3" href="{instagram}" target="_blank" rel="no-referrer"><i class="fa-brands fa-square-instagram"></i></a>
        </div>
    </div>
    
</footer>


<style>
    i {
        font-size: 2rem;
    }
    
    footer {
        /* background-color: var(--color-background); */
    }

    img {
        width: 100%;
        object-fit: contain;
        max-width: 200px;
    }

    a {
        color: var(--color-primary);
        text-decoration: none;
    }

</style>