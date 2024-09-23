<template>
  <v-container>
    <!-- Mostramos el título de la película seleccionada -->
    <div v-if="selectedMovie">
      <h3>Pelicula: {{ selectedMovie }}</h3>
    </div>

    <v-table>
      <thead>
        <tr>
          <th>Título</th>
          <th>Calificación</th>
          <th>IMDB</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(movie, index) in movies" :key="index">
          <!-- Agregamos @click al título de la película -->
          <td @click="selectMovie(movie.movie)" style="cursor: pointer;">
            {{ movie.movie }}
          </td>
          <td>{{ movie.rating }}</td>
          <td><a :href="movie.imdb_url" target="_blank">{{ movie.imdb_url }}</a></td>
        </tr>
      </tbody>
    </v-table>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      movies: [], // Almacena los datos de las películas
      selectedMovie: '', // Almacena el nombre de la película seleccionada
    };
  },
  mounted() {
    this.fetchMovies();
  },
  methods: {
    async fetchMovies() {
      try {
        const response = await fetch('https://dummyapi.online/api/movies');
        if (response.ok) {
          const data = await response.json();
          console.log(data); // Verificar la estructura
          this.movies = data; // Como el JSON es un array de objetos, lo asignamos directamente
        } else {
          console.error('Error al obtener los datos de la API:', response.statusText);
        }
      } catch (error) {
        console.error('Error al realizar la solicitud:', error);
      }
    },
    selectMovie(movieTitle) {
      this.selectedMovie = movieTitle;
    },
  },
};
</script>
