<template lang="html">
    <div class="film-list" v-if="films.length">
        <film-list-item
            v-for="(film, index) in films"
            :film="film"
            :key="index"
        >
        </film-list-item>
    </div>
  
</template>

<script>
import FilmListItem from "@/components/FilmListItem"

export default {
    name: "film-list",
    props: ["films"],
    components: {
        "film-list-item": FilmListItem
    }
}
</script>

<style>

</style>