<template>
    <div class="bg-gray-200 p-5 rounded-md dark:bg-black">
        <!-- ... -->
        <div class="sm-56 lg:mx-72 px-10 py-16 bg-gray-400 dark:bg-black dark:border">
            <div class="mb-6">
                <label for="large-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Movie
                    Title</label>
                <input type="text" id="large-input"
                    class="block w-full p-4 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 sm:text-md focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    placeholder="Type your Movie Title..." v-model="movieData.title">
                <p v-if="!movieData.title && isSubmitted" class="text-red-500 mt-2">Movie Title is required.</p>
            </div>
            <div class="mb-6">
                <label for="base-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Movie
                    Category</label>
                <input type="text" id="base-input"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    placeholder="Type your Movie category Name..." v-model="movieData.category">
                <p v-if="!movieData.category && isSubmitted" class="text-red-500 mt-2">Movie Category is required.</p>
            </div>
            <div class="mb-6">
                <label for="message" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Movie Short
                    Description</label>
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

const submitForm = () => {
    isSubmitted.value = true;
    if (validateInputs()) {
        fetchBotReply();
    }
};

function validateInputs() {
    const { title, category, description } = movieData.value;
    if (!title || !category || !description) {
        return false;
    }
    return true;
}

async function fetchBotReply() {
    console.log('movieDat', movieData.value)
    // const response = await openAi.createCompletion({
    //     model: 'text-davinci-003',
    //     prompt: `Generate a short message to enthusiastically say an outline sounds interesting and that you need minutes to think about it.
    //     ###
    //     outline: Two dogs fall in love and move to Hawaii to learn to surf.
    //     message: I'll need tho think about that. But your iea is amazing! I love the bit about Hawaii~
    //     ###
    //     outline:A plane crashes in the jungle and the passengers have to walk 1000km to safety.
    //     message: I'll spend a few moments considering that. But I love your idea!! A disaster movie in the jungle!
    //     ###
    //     outline: A group of corrupt lawyers try to send an innocent woman to jail.
    //     message: Wow that is awesome! Corrupt lawyers, huh? Give me a few moments to think!
    //     ###
    //     outline: A thief running from bank
    //     message: 
    //     `,
    //     max_tokens:60
    // })

    // console.log('ai result', response.data.choices[0].text.trim())
}

// ...
</script>