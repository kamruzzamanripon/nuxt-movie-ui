<template>
<section class="mt-9 bg-blue-400 dark:bg-black p-5 rounded-md">
    <div class="flex items-center justify-between">
        <span class="font-semibold text-gray-700 text-base dark:text-white">Category wise movie</span>
        <div class="flex items-center space-x-2 fill-gray-500">
            <svg class="h-7 w-7 rounded-full border p-1 hover:border-red-600 hover:fill-red-600 dark:fill-white dark:hover:fill-red-600" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path d="M13.293 6.293L7.58 12l5.7 5.7 1.41-1.42 -4.3-4.3 4.29-4.293Z"></path>
            </svg>
            <svg class="h-7 w-7 rounded-full border p-1 hover:border-red-600 hover:fill-red-600 dark:fill-white dark:hover:fill-red-600" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
                <path d="M10.7 17.707l5.7-5.71 -5.71-5.707L9.27 7.7l4.29 4.293 -4.3 4.29Z"></path>
            </svg>
        </div>
    </div>

    <div class="mt-4 grid grid-cols-2 gap-y-5 sm:grid-cols-3 gap-x-5 ">
        <div class="flex flex-col rounded-xl overflow-hidden aspect-square border dark:border-zinc-600" v-for="n in 3" :key="n">
            <img src="https://upload.wikimedia.org/wikipedia/en/1/14/Tenet_movie_poster.jpg" class=" h-4/5 object-cover w-full  " alt="">
            <div class="w-full h-1/5 bg-white dark:bg-zinc-800 dark:text-white px-3 flex items-center justify-between border-t-2 border-t-red-600">
                <span class="capitalize  font-medium truncate">Tenet</span>
                <div class="flex space-x-2 items-center text-xs">
                    <IconImdbLogo />
                    <span>7.4</span>
                </div>
            </div>
        </div>
    </div>
</section>
</template>

<script setup>
import IconImdbLogo from '../Icon/ImdbLogo.vue';
</script>
