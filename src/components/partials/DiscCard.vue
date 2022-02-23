<template>
    <div class="col text-center disc-card p-3">
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
        background-color: #2e3a46;

        h1 {
            color: white;
            text-transform: uppercase;
            font-size: 25px;
            font-weight: bold;
        }

        h2 {
            color: #808080;
            font-size: 20px;
            font-weight: bold;
        }
    }
</style>