<template>
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        <Movie :movie="movie" />
      </li>
    </ul>
</template>

<script>
import Movie from './Movie.vue'
export default {
  // https://api.themoviedb.org/3/movie/550?api_key=ec5dc58dd49114aa47aebd1659fef849
  name: 'MoviesList',
  data() {
    return {
      movies: [],
    }
  },
  created: function() {
    this.fetchData()
  },
  methods: {
    fetchData: async function() {
      try {
        const res = await fetch(
          // 'https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=ec5dc58dd49114aa47aebd1659fef849'
           'https://herokutestnodecrashcourse.herokuapp.com/api/movies'
        )
        const movies = await res.json()
        this.movies = movies.results
      } catch (e) {
        console.log(e)
      }
    },
  },
  components: {
    Movie,
  },
}
</script>

<style scoped>
ul {
  display: grid;
  list-style: none;
  padding: 1rem;
  margin: 0;
  row-gap: 1rem;
  grid-template-columns: repeat(6,1fr)
}
</style>
