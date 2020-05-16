<template lang="html">
  <div id="app">
    <h1>Anime Studio</h1>
    <div id="list-info" v-if="films.length">
      <film-list :films="films"></film-list>
    </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js"
import FilmList from "@/components/FilmList";

export default {
  name: "app",
  components: {
    "film-list": FilmList,
  },
  data() {
    return {
      films: [],
    };
  },
  methods: {
    getFilms: function() {
      fetch("https://ghibliapi.herokuapp.com/films")
      .then(res => res.json())
      .then(filmData => {
        this.films = filmData;
      })
    }
  },
  mounted() {
    this.getFilms();
  }

}
</script>

<style>

</style>