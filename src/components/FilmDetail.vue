<template lang="html">
    <div v-if="film" id="filmDetail">
        <div id="detailWrapper">
            <h2>{{film.title}}</h2>
            <p>{{film.description}} </p>
            <div id="flexWrapper">
                <div id="left">
                    <h3>Film Facts</h3>
                    <p><span class="fact">Locations</span>: </p>
                    <p><span class="fact">  </span>: </p>
                </div>
                <div id="right">
                    <h3>Production Details</h3>
                    <p><span class="fact">Director</span>: {{film.director}}</p>
                    <p><span class="fact">Producer</span>: {{film.producer}}</p>
                    <p><span class="fact">Release date </span>: {{film.release_date}}</p>
                    <p><span class="fact">Tomatometer score</span>: {{film.rt_score}}</p>
            </div>
        </div>
        </div>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'film-detail',
    data(){
        return {
            film: null 
        }
    },
    mounted(){
        eventBus.$on('film-selected', (film) => {
            this.film = film
        })
    }
}
</script>

<style lang="css" scoped>

/* Creates two columns */
#flexWrapper {
    display: flex;
    justify-content: space-around;
}


#left, #right {
    width: 40%;
    border: 1px solid grey;
    padding: 10px;
}

.fact {
    font-weight: bold;
}

div {
    font-family: Arial, Helvetica, sans-serif;
}

#film-detail {
    margin: 10px;
}

</style>