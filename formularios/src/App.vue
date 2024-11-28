<script>
import Formulario from './components/Formulario.vue';
import Tarjeta from './components/Tarjeta.vue';
export default {
  data() {
    return {
      datos: {} // Inicializa un objeto vacío para almacenar los datos de la tarjeta
    };
  },
  components:{
    Formulario,
    Tarjeta
  },
  methods: { //actualiza los datos
    actualizarDatos(datos) {
      // console.log('Datos recibidos en App.vue:', datos);
      this.datos = { ...datos };  // Asigna los datos al objeto 'datos'
    }
  }
};
</script>

<template>
  <div class="form">
    <Formulario @datos-actualizados="actualizarDatos"/> <!-- Escucha el evento 'datos-actualizados' y llama al método actualizarDatos -->
    <Tarjeta :datos="datos" /> <!-- Pasa los datos al componente Tarjeta -->
  </div>
</template>
<style scoped>
  .form{
    display: flex;
    gap: 15px;
  }
</style>