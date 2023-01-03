<script setup>
import { reactive } from "vue";
import Response from "./components/Response.vue";
import AddResponse from "./components/AddResponse.vue";

let id = 0;

let responses = reactive([
    {
        id: id++,
        responseText: "I do not understand this updating part",
        count: 1,
    },
    {
        id: id++,
        responseText: "How does x becomes 3?",
        count: 2,
    },
]);

const updateCount = (id, updateType) => {
    if (updateType === "inc") {
        responses[id].count++;
    } else if (updateType === "dec") {
        responses[id].count--;
    }
};

const newResponse = (data) => {
    responses.push({ ...data, id: id++, count: 1 });
};
</script>

<template>
    <header>
        <p class="h1 text-center">Plus One</p>
    </header>

    <main>
        <div class="container">
            <div class="d-flex justify-content-center flex-wrap">
                <Response
                    v-for="response in responses"
                    :responseText="response.responseText"
                    :count="response.count"
                    :id="response.id"
                    :key="response.id"
                    @update-count="updateCount"
                />
            </div>
            <div class="d-flex justify-content-center">
                <AddResponse @new-response="newResponse" />
            </div>
        </div>
    </main>
</template>

<style scoped>
header {
    line-height: 1.5;
}

/* @media (min-width: 1024px) { */
/*     header { */
/*         display: flex; */
/*         place-items: center; */
/*         padding-right: calc(var(--section-gap) / 2); */
/*     } */
/*  */
/*     header .wrapper { */
/*         display: flex; */
/*         place-items: flex-start; */
/*         flex-wrap: wrap; */
/*     } */
/* } */
</style>
