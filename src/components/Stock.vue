<template>
    <tr>
      <td>{{ juego.codigo }}</td>
      <td>{{ juego.nombre }}</td>
      <td>{{ juego.stock }}</td>
      <td>${{ juego.precio }}</td>
      <td>
        <button @click="aumentarStock">+</button>
        <button @click="disminuirStock" :disabled="juego.stock === 0">-</button>
      </td>
    </tr>
  </template>
  
  <script>
  export default {
    name: "Stock",
    props: {
      juego: {
        type: Object,
        required: true,
      },
    },
    methods: {
      aumentarStock() {
        this.$emit("aumentar-stock", this.juego.codigo);
      },
      disminuirStock() {
        this.$emit("disminuir-stock", this.juego.codigo);
      },
    },
  };
  </script>
  
  <style scoped>
  button {
    padding: 5px 10px;
    margin: 0 5px;
    cursor: pointer;
  }
  button:disabled {
    cursor: not-allowed;
    background-color: #ccc;
  }
  </style>
  
  
