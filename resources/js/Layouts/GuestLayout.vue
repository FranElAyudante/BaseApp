<template>
    <div class="d-flex flex-column min-vh-100">
        <!-- Header-->
         <header>
            <Header/>
         </header>


        <!-- Main-->
        <main class="flex-grow-1" >
            <slot />
        </main>

        <!-- Footer -->
        <Footer/>

    </div>
</template>

<script setup>
import { Link } from '@inertiajs/vue3';
import Header from '@/Components/Header/header.vue';
import Footer from '@/Components/Footer/footer.vue';

</script>

