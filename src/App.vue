<template>
  <div class="app">
    <h1>Tienda 32 Bits</h1>
    <h3>Lista de Juegos</h3>
    <table border="1" cellspacing="0" cellpadding="10">
      <thead>
        <tr>
          <th>Código</th>
          <th>Nombre</th>
          <th>Stock</th>
          <th>Precio</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <Stock
          v-for="juego in stock"
          :key="juego.codigo"
          :juego="juego"
          @aumentar-stock="aumentarStock"
          @disminuir-stock="disminuirStock"
        />
      </tbody>
    </table>
  </div>
</template>

<script>
import { mapState, mapActions } from "vuex";
import Stock from "./components/Stock.vue";

export default {
  name: "App",
  components: {
    Stock,
  },
  computed: {
    ...mapState(["stock"]),
  },
  methods: {
    ...mapActions(["incrementStock", "decrementStock"]),
    aumentarStock(codigo) {
      this.incrementStock(codigo);
    },
    disminuirStock(codigo) {
      this.decrementStock(codigo);
    },
  },
};
</script>

<style>
table {
  width: 100%;
  text-align: center;
}
</style>

