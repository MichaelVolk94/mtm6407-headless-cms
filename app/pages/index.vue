<script setup>

    import { ALL_PLACES_URL, BASE_URL } from '../../utils/index.js';

    const places = ref([]);

    const { data } = await useFetch(ALL_PLACES_URL);
    places.value = data.value.data;

</script>

<template>
    <section class="main-code">
    <h1>Michael Volk's Recommendations of Places</h1>
    <h2>Welcome to my reviewing website! Where I review certain places that I visited and why I recommend them.</h2>
    <ul>
        <li v-for="place in places">
            <NuxtLink :to="place.documentId">
                <img :src="`${BASE_URL}${place?.image?.url}`" width="350" />
                {{ place?.name }}
            </NuxtLink>
        </li>
    </ul>
    <footer>&#169; Michael Volk's Recommendations of Places 2025</footer>
    </section>
</template>

<style scoped>
.main-code {
    text-align: center;
    font-family: Verdana, Tahoma, sans-serif;
    background-color: lightblue;
}
li {
    display: flex;
    text-align: center;
}

h1 {
    font-size: 35px;
}

h2 {
    font-size: 15px;
}

</style>