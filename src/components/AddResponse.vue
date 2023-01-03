<script setup>
import { ref } from "vue";

const emits = defineEmits(["newResponse"]);
const isNewResponse = ref(false);
const responseText = ref(null);
const sendResponse = () => {
    emits("newResponse", {
        responseText: responseText.value.value,
    });
    isNewResponse.value = false;
};
</script>

<template>
    <span v-if="isNewResponse">
        <div class="card" style="width: 18rem">
            <div class="card-body">
                <div class="row justify-content-around">
                    <form @submit.prevent="sendResponse">
                        <input
                            ref="responseText"
                            row="3"
                            class="form-control rounded"
                            placeholder="Enter your text"
                        />
                        <div class="row justify-content-end">
                            <button
                                type="submit"
                                class="col-2 p-2 mx-2 mt-2 btn btn-success round-btn"
                            >
                                +
                            </button>
                            <button
                                class="col-2 p-2 mx-2 mt-2 me-3 btn btn-danger round-btn"
                                @click="isNewResponse = false"
                            >
                                x
                            </button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </span>
    <span v-else>
        <button
            v-if="!isNewResponse"
            class="col-2 px-5 mx-2 mt-2 btn btn-outline-success rounded-pill"
            @click="isNewResponse = true"
        >
            +
        </button>
    </span>
</template>

<style scoped>
.round-btn {
    border-radius: 40px;
    min-height: 40px;
    min-width: 40px;
    max-height: 50px;
    max-width: 50px;
    padding-top: 10px;
    margin: 10px;
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
