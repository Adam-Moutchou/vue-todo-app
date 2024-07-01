<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <header>
        <div class="header__content">
            <img src="../assets/logo.png" alt="">
            <ul class="header__content-routes">
                <RouterLink to="/">Home</RouterLink>
                <RouterLink to="/about">About</RouterLink>
            </ul>
        </div>
    </header>
</template>

<style scoped>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    header {
        background-color: #fed9bc;
        padding: 10px;
    }

    .header__content {
        display: flex;
        align-items: center;
        justify-content: space-around;
    }

    .header__content img {
        width: 10rem;
        aspect-ratio: 2/1;
        object-fit: cover;
        filter: drop-shadow(0 10px 20px rgb(0, 0, 0,0.5));
    }

    .header__content-routes a {
        margin: 10px;
        text-decoration: none;
        font-size: 20px;
        padding: 10px 20px 10px 20px;
        color: #000;
        border-radius: 5px;
        transition: all .3s ease-out;
    }

    .header__content-routes a:hover {
        transition: all .1s ease-in;
        background-color: #000;
        color: var(--secondary-color);
    }

</style>