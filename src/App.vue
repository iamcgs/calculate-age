<template>
  <div class="container">
    <CalculateAge />
    <div class="description">
      <p>
        La idea es usar la calculadora para controlar que sean correctas las
        edades que figuran en las diferentes Actas que se van a presentar para
        realizar el trámite de la Ciudadanía Italiana. Me pareció una forma más
        fácil y rápida de realizar el control. <br />
        Espero que les sirva!
      </p>
    </div>
    <footer>
      <p>
        Desarrollado por
        <a href="https://github.com/iamcgs" target="_blank">CGS</a>
      </p>
    </footer>
  </div>
</template>

<script>
import CalculateAge from './components/CalculateAge.vue';

export default {
  name: 'App',
  components: {
    CalculateAge,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
}

.container {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.description {
  width: 650px;
  font-size: 0.85rem;
  color: rgb(102, 101, 101);
  background: #fcfcfc;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0px 0px 4px 1px rgba(217, 219, 218, 0.72);
  line-height: 1.6;
}

footer {
  color: rgb(102, 101, 101);
  font-size: 0.85rem;
  font-style: italic;
  margin: 15px auto;
}

footer a {
  color: #40916c;
  text-decoration: none;
}

@media screen and (max-width: 768px) {
  .description {
    width: 450px;
  }
}

@media screen and (max-width: 475px) {
  .description {
    width: 350px;
  }
}
</style>
