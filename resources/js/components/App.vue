<template>
    <div class="flex flex-col min-h-screen">
        <Header class="w-full" />
        <LoadingOverlay v-if="loading" />
        <div class="flex flex-1 justify-center items-center p-4">
            <router-view></router-view>
            <!-- Tu neskôr pridáme Filter, Pagination -->
        </div>
        <Footer class="w-full" />
    </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './Header.vue';
import Footer from './Footer.vue';
import LoadingOverlay from './LoadingOverlay.vue';
import { useRouter } from 'vue-router';

const loading = ref(false);
const router = useRouter();

router.beforeEach((to, from, next) => {
    loading.value = true;
    next();
});
router.afterEach(() => {
    loading.value = false;
});
</script>

<style scoped></style>