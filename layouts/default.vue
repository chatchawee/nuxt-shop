<template>
    <div>
        <nav class="navbar navbar-expand-lg bg-light">
            <div class="container-fluid">
                <!-- <a class="navbar-brand" href="#">Home</a> -->
                <NuxtLink to="/" class="navbar-brand">Home</NuxtLink>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="#">menu1</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">menu2</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">menu3</a>
                    </li>
                </ul>
                </div>
            </div>
        </nav>
        <div class="container mt-3">
            <!-- Content here -->
            <slot/>
        </div>
 
    </div>
</template>

<style scoped>
    body {
        font-family: 'Roboto', sans-serif; 
    }
</style>