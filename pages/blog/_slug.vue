<template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <img :src="article.img" :alt="article.alt" class="udh">
    <p class="lastUpdate"><small>Article last updated: {{formatDate(article.updatedAt)}}</small></p>
    <hr>

    <!-- fuck sake sir my ears lol im calling my brotherr coz hes no answering my maw
        lol he's shagging lmao
    -->

    <!-- Table of contents -->
    <nav>
        <ul>
            <li v-for="link of article.toc" :key="link.id">
                <NuxtLink :to="`#${link.id}`">{{ link.text }}</NuxtLink>
            </li>
        </ul>
    </nav>

    <!-- Parses main body of markdown document -->
    <nuxt-content :document="article" />
  </article>
</template>

<script>
export default {
    async asyncData({ $content, params }) {
        const article = await $content('articles', params.slug).fetch()
        return {article}
    },

    methods: {
        formatDate(date) {
            const options = { year: 'numeric', month: 'long', day: 'numeric'}
            return new Date(date).toLocaleDateString('en', options)
        }
    }
}
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;700&display=swap');

    body {
        background-color: rgb(33, 35, 43);
        color: #fff;
    }

    article {
        font-family: 'Poppins', sans-serif;
        width: 50%;
        margin-left: auto;
        margin-right: auto;
    }

    .nuxt-content h2 {
        font-weight: bold;
        font-size: 28px;
    }

    .nuxt-content h3 {
        font-weight: bold;
        font-size: 22px;
    }

    .nuxt-content p {
        margin-bottom: 20px;
    }

    video {
        width: 40vh;
        height: 25vh;
    }

    article img {
        width: 30vw;
    }

    article p.lastUpdate {
        float: right;
        margin-top: 30vh;
    }

    nav {
        width: 100%;
        height: auto;
        background-color: rgb(31, 32, 36);
        padding: 1px;
        border-bottom-left-radius: 10px;
        border-bottom-right-radius: 10px;
        margin-bottom: 30px;
    }

    nav ul {
        display: flex;
        justify-content: space-around;
    }

    nav ul li {
        list-style-type: none;
        margin-right: 2px;
        height: auto;
    }

    nav ul li a {
        text-decoration: none;
        color: #dadada;
        transition: 0.3s ease-in-out all;
    }

    nav ul li a:hover {
        color: rgb(89, 89, 214);
        text-decoration: underline;
    }
</style>

<!-- CEASE AND DESIST FUCKING MORON -->
<!-- CEASE AND DESIST FUCKING MORON -->
<!-- CEASE AND DESIST FUCKING MORON -->
<!-- CEASE AND DESIST FUCKING MORON -->