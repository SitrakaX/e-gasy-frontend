<script setup>
import Navbar from '~/components/Header/Navbar.vue';

</script>

<template>
    <div>

        <Navbar/>
        <Main>
            <NuxtPage></NuxtPage>
        </Main>
        <AppAlert />
    </div>
</template>