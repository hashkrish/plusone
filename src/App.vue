<script setup>
    import Response from './components/Response.vue'
</script>

<template>
    <header>
        <p class="h1 text-center">Plus One</p>
    </header>

    <main>
        <div class="container">
            <Response responseText="Hi" />
        </div>
    </main>
</template>

<style scoped>
    header {
        line-height: 1.5;
    }

    .logo {
        display: block;
        margin: 0 auto 2rem;
    }

    @media (min-width: 1024px) {
        header {
            display: flex;
            place-items: center;
            padding-right: calc(var(--section-gap) / 2);
        }

        .logo {
            margin: 0 2rem 0 0;
        }

        header .wrapper {
            display: flex;
            place-items: flex-start;
            flex-wrap: wrap;
        }
    }
</style>
