<script setup>
import { ref, toRef, toRefs } from "vue";

const props = defineProps({
    responseText: {
        type: String,
        required: true,
    },
    count: {
        type: Number,
        default: 0,
    },
    include: {
        type: Boolean,
        default: null,
    },
    id: {
        type: String,
        default: "NoID",
    }
});

const emits = defineEmits([
    "incrementCount",
    "decrementCount"
]);

const selectedButtonClass = ref("round-btn btn btn-outline-success");
const countProp = toRef("");
function inverseSelection() {
    if (selectedButtonClass.value === "round-btn btn btn-outline-success") {
        selectedButtonClass.value = "round-btn btn btn-success";
        emits("updateCount", props.id, "inc");
    } else {
        selectedButtonClass.value = "round-btn btn btn-outline-success";
        emits("updateCount", props.id, "dec");
    }
};

</script>

<template>
<div class="card" style="width: 18rem">
    <div class="card-body">
        <p class="card-title"> {{ responseText }} </p>
        <div class="row justify-content-around">
            <span class="col"> {{ count }} <br/>people</span>
            <a role="button"
                data-bs-toggle="button"
                @click="inverseSelection"
                :class="selectedButtonClass"
            >
                +1
            </a>
        </div>
        <div class="row justify-content-around debug">
            <span class="col"> Id: {{ id }} </span>
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
    margin: 10px;
}

.debug {
    background-color: #ddd;
    margin-top: 10px;
    border-radius: 10px;
}
</style>
