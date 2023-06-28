<template>
<div class="flex min-h-screen">
    <!-- Left Sidebar -->
    <LeftSideBar />
    <!-- /Left Sidebar -->

    <div class="w-full px-6 mt-10">
        <AiFormInput />
        <AiFormResult />
    </div>

    <!-- Right Sidebar -->
    <RightSideBar />
    <!-- /Right Sidebar -->
</div>
</template>

<script setup>
import AiFormInput from '@/components/make-movie/AiFormInput.vue';
import AiFormResult from '@/components/make-movie/AiFormResult.vue';
import LeftSideBar from '@/layouts/LefeSideBar.vue';
import RightSideBar from '@/layouts/RightSideBar.vue';
</script>
