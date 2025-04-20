<script setup>
import Header from '~/components/Header/Header.vue';
import Navbar from '~/components/Header/Navbar.vue';

</script>

<template>
    <div>

        <Header></Header>
        <Main>
            <NuxtPage></NuxtPage>
        </Main>
        <AppAlert />
    </div>
</template>