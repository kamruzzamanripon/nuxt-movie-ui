<template>
    <div class="bg-gray-200 p-5 rounded-md dark:bg-black" >
            
            <div class="text-center mb-8 relative">
                <h1 class="text-2xl font-bold text-gray-700 mb-3 dark:text-white">Hello, I am here to help Make Movie</h1>
                <p class="dark:text-white">Please, write your idea below input box</p>
                <img src="/assets/pictures/robot-1.webp" alt="" class="rounded-full w-48 h-48 absolute -top-5 right-0 sm::hidden">
            </div>

            <div class="mx-10 px-10 py-16 bg-gray-400 dark:bg-black dark:border rounded-md">
            <div class="mb-6">
                <label for="message" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
                    Type your Movie Idea
                </label>
                <textarea id="message" rows="4"
                    class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    placeholder="Type Movie short description..." v-model="movieData.description"></textarea>
                <p v-if="!movieData.description && isSubmitted" class="text-red-500 mt-2">Movie Description is required.</p>
            </div>
            <div class="text-right">
                <button type="submit" class="bg-black text-white p-3 rounded-md dark:border" @click="submitForm">Make
                    Movie</button>
            </div>
            </div>

        </div>
</template>

<script setup>
import { Configuration, OpenAIApi } from 'openai';
import { ref } from 'vue';

const movieData = ref({
    title:"",
    category:"",
    description:""
})

const config = useRuntimeConfig();
const openAiApiKey = config.public.OPEN_AI_API_KEY
const configuration = new Configuration({
    apiKey: openAiApiKey
})
const openAi = new OpenAIApi(configuration);
const isSubmitted = ref(false);

function validateInputs() {
    const { title, category, description } = movieData.value;
    if (!title || !category || !description) {
        return false;
    }
    return true;
}

const submitForm = () => {
    isSubmitted.value = true;
    if (validateInputs()) {
        alert('form submit')
    }
};




</script>