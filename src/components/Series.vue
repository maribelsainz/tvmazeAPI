<template>
  <div>
    <div class="row">
      <div
        v-for="(serie, index) in informacion"
        :key="index"
        class="col-12 col-sm-12 col-md-6 col-lg-3 col-xl-3 d-flex"
      >
        <div class="card my-2">
          <img :src="serie.image.medium" class="card-img-top" alt="serie" />
          <div class="card-body">
            <h5 class="card-title">{{ serie.name | mayusculas }}</h5>
            <p
              class="card-text"
              v-html="$options.filters.recorte(serie.summary)"
            ></p>
            <!-- Button trigger modal -->
            <button
              type="button"
              class="btn btn-primary"
              data-toggle="modal"
              data-target="#staticBackdrop"
            >
              Ver más
            </button>
          </div>
        </div>
      </div>
    </div>
    <modal></modal>
  </div>
</template>

<script>
import Modal from "./Modal.vue";
export default {
  name: "Series",
  components: {
    Modal,
  },
  props: {
    informacion: {
      type: Array,
      required: true,
    },
  },
  filters: {
    mayusculas(valor) {
      return valor.toUpperCase();
    },
    recorte(texto) {
      return texto.substring(0, 100) + "...";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
