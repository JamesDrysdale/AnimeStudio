<template lang="html">
    <form v-on:submit.prevent>
        <!-- Create drop down menu with selectable title -->
        <select v-on:change="handleSelect" v-model="selectedFilm">
            <option diasbled value="">Select a film...</option>
            <option v-for="film in films" :value="film"> {{ film.title }} </option>
        </select>
    </form>
  
</template>

<script>
import { eventBus } from '../main.js'
import FilmListItem from "@/components/FilmListItem"

export default {
    name: "film-list",
    data(){
        return {
            "selectedFilm": {},
        }
    },
    props: ["films"],
    components: {
        "film-list-item": FilmListItem
    },
    methods: {
        handleSelect(){
            this.search = ""
            eventBus.$emit('film-selected', this.selectedFilm)
        }
    }
}
</script>

<!--
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
-->

<style lang="css" scoped>


</style>