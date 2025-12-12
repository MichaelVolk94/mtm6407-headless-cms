<script setup>

import { BASE_URL } from '~~/utils';
const route = useRoute()
const placeId = route.params.id;
const place = ref(null);

const { data } = await useFetch(`${BASE_URL}/api/places/${placeId}?populate=*`)
place.value = data.value.data;

</script>

<template>
    <section class="main-code">
    <img :src="`${BASE_URL}${place?.image?.url}`" width="800" />
    <h2>{{ place?.name }}</h2>
    <ul>
        <li v-for="rating in place.rating">
            ⭐
        </li>
    </ul>
    <p>{{ place?.content }}</p>
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
    display: inline-block;
}

img {
    max-width: 100%;
    margin: 0;
    padding: 0;
}
</style>