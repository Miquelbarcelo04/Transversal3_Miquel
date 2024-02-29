<template>
  <body>
    <Header />
    <div class="home">
      <h1>galaxia films</h1>
      <h2>Pel·licula del dia</h2>
      <div class="movie-list">
        <div v-if="dailyMovie" class="movie-card">
          <img :src="dailyMovie.poster" alt="Pòster de la pel·lícula" />
          <h2>{{ dailyMovie.title }}</h2>
          <p>{{ dailyMovie.genre }}</p>
          <button @click="bookTicket(dailyMovie.id)">Reserva Entrada</button>
        </div>
      </div>
    </div>
  </body>
</template>
  
<script>
export default {
  data() {
    return {
      movies: [
        {
          id: 1,
          title: "John Wick 4",
          genre: "Acció",
          poster: "/JohnWick4.jpg",
        },
        // Añade más películas aquí si lo deseas
      ],
      today: new Date().getDay(), // Obtiene el día de la semana actual
    };
  },
  computed: {
    dailyMovie() {
      // Retorna una película basada en el día de la semana
      return this.movies[this.today % this.movies.length];
    },
  },
  methods: {
    bookTicket(movieId) {
      // Redirecciona a la página de cine al reservar una entrada
      this.$router.push({ name: 'cine' }); // Asegúrate de tener configurado el enrutamiento en tu aplicación Vue
    },
  },
};
</script>
  
<style scoped>
body {
  margin: 0;
  /* Elimina los márgenes predeterminados del body */
  padding: 0;
  /* Elimina el padding predeterminado del body */
  height: 100vh;
  /* Hace que el body ocupe el 100% del alto de la ventana */
  overflow: hidden;
  /* Evita el desplazamiento vertical */
}

.home {
  text-align: center;
  padding: 20px;
  background-color: #1a1a1d;
  color: #c5c6c7;
  height: 100%;
}

h1 {
  font-variant: small-caps;
  font-size: 3rem;
  font-family: 'Your Epic Font', sans-serif;
}

.movie-list {
  display: flex;
  justify-content: center;
}

.movie-card {
  margin: 20px;
  padding: 20px;
  border: 1px solid #4b5d67;
  /* Borde sutil */
  border-radius: 15px;
  /* Bordes más redondeados */
  width: 300px;
  /* Ancho mayor para mejor visualización */
  background-color: #0b0c10;
  /* Fondo oscuro para la tarjeta */
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
  /* Sombra más pronunciada para profundidad */
  transition: transform 0.3s ease;
  /* Suave transformación al pasar el mouse */
}

.movie-card:hover {
  transform: translateY(-5px);
  /* Ligero movimiento hacia arriba al pasar el mouse */
}

.movie-card img {
  width: 100%;
  height: auto;
  border-radius: 15px;
  margin-bottom: 15px;
  /* Espacio después del póster */
}

.movie-card h2,
.movie-card p {
  margin: 10px 0;
}

.movie-card button {
  display: block;
  width: 100%;
  padding: 10px 0;
  background-color: #66fcf1;
  /* Color distintivo para el botón */
  color: #0b0c10;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  /* Transición suave al cambiar el color */
}

.movie-card button:hover {
  background-color: #45a29e;
  /* Color más oscuro al pasar el mouse */
}

/* Estilos para el botón de login/registro */
.login-button {
  position: absolute;
  top: 20px;
  right: 20px;
  padding: 10px 20px;
  background-color: #66fcf1;
  color: #0b0c10;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.login-button:hover {
  background-color: #45a29e;
}</style>
  
  