<template>
    <div class="col disc-card">
        <img class="img-thumbnail" :src="disc.poster">
        <h1>{{disc.title}}</h1>
        <h2>{{disc.author}}</h2>
        <h2>{{disc.year}}</h2>
    </div>
</template>

<script>
export default {
    name: "DiscCard",
    props: {
        "disc": Object,
    }
}
</script>

<style scoped lang="scss">
    .disc-card {
        border: 1px solid black;
    }
</style>