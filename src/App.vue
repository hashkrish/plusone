<script setup>

import { reactive } from "vue";
import Response from "./components/Response.vue";

let responses = reactive([
    {
        id: 0,
        responseText: "I do not understand this updating part",
        count: 1,
    },
    {
        id: 1,
        responseText: "How does x becomes 3?",
        count: 2,
    },
]);

const updateCount = (id, updateType) => {
    if (updateType === "inc") {
        responses[id].count++;
    }
    else if (updateType === "dec") {
        responses[id].count--;
    }
};

</script>

<template>
<header>
    <p class="h1 text-center">Plus One</p>
</header>

<main>
    <div class="container">
        <div class="d-flex justify-content-center flex-wrap">
            <Response v-for="response in responses"
                :responseText="response.responseText"
                :count="response.count"
                :id="response.id"
                :key="response.id"
                @update-count="updateCount"
            />
        </div>
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
