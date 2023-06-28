<template>
    <div>
     <Header/>
      <slot />
      <Footer />
    </div>
  </template>

<script setup>
import Footer from './Footer.vue';
import Header from './Header.vue';



const colorMode = useColorMode()
</script>

<style lang="postcss">
body {
  @apply min-h-screen bg-white dark:bg-gray-800 dark:text-gray-200;
}
</style>
