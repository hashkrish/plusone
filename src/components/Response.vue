<script setup>
defineProps({
    responseText: {
        type: String,
        required: true,
    },
    count: {
        default: 0,
        type: Number,
    },
});
</script>

<template>
<div class="card" style="width: 18rem">
    <div class="card-body">
        <p class="card-title"> {{ responseText }} </p>
        <div class="row justify-content-around">
            <span class="col">{{ count }} <br/>people</span>
            <a href="#" 
               class="round-btn btn btn-primary col"
            >+1</a>
        </div>
    </div>
</div>
</template>

<style scoped>
.round-btn {
    border-radius: 40px;
    min-height: 40px;
    min-width: 40px;
    max-height: 50px;
    max-width: 50px;
    padding-top: 10px;
}

.card {
    padding: 10px;
    border-radius: 40px;
}
</style>
