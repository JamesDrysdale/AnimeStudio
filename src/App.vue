<template lang="html">
  <div id="app">
    <header>
      <h1>Ghibli Studio</h1>
      <h2>Film Explorer</h2>
    
      <div id="list-info" v-if="films.length">
        <film-list :films="films"></film-list>
      </div>
    </header>
      <div>
        <film-detail />
      </div>
  </div>
</template>

<script>
import { eventBus } from "@/main.js"
import FilmList from "@/components/FilmList";
import FilmDetail from "@/components/FilmDetail";

export default {
  name: "app",
  components: {
    "film-list": FilmList,
    "film-detail": FilmDetail,
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

<style lang="css" scoped>

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');

header {
  background-color: #109CEB;
  color: white;
  padding: 20px;
  text-align: center;
  font-family: 'Roboto', sans-serif;
}

</style>