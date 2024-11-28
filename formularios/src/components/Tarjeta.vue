<script>
import imgchip from '../assets/chip.png';
import imgvisa from '../assets/visa.png';

export default {
    // Propiedades que el componente puede recibir
    props: {
        datos: {
        type: Object,
        //Devolver el objeto por defecto
        default() {
            return {
            titulo: '',
            chip: '',
            numero: '',
            fechaExpiracion: '',
            propietario: '',
            tipoSRC: ''
            };
        },
        },
    },
    methods: {
        // Función para obtener la imagen del chip desde el formulario. No se debe eliminar la barra diagonal (/), ya que eso provoca que no funcione correctamente.
        getChipImage(chipName) {
            try {
                return new URL(`../assets/${chipName}`, import.meta.url).href;
            } catch (e) {
                return ''; 
            }
        },
        //funcion para imagen de visa
        getTipoSRCImage(tipoSRC) {
            try {
                return new URL(`../assets/${tipoSRC}`, import.meta.url).href;
            } catch (e) {
                return '';
            }
        }
    }
};
</script>

<template>
    <div class="carnet">
        <h3>{{ datos.titulo || '' }}</h3>
        <img width="40" :src="getChipImage(datos.chip)" alt="" />
        <div>
            <h2>{{ datos.numero || '' }}</h2>
            <span>Fecha Exp: <b>{{ datos.fechaExpiracion || '' }}</b></span>
        </div>
        <footer>
            <span>{{ datos.propietario || '' }}</span>
            <img :src="getTipoSRCImage(datos.tipoSRC)" width="60" />
        </footer>
    </div>
</template>

<style scoped>
.carnet {
    width: 400px;
    height: 230px;
    background: #1c1a1e;
    color: white;
    border-radius: 20px;
    padding: 20px;
    box-shadow: 0px 0px 10px 2px black;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
footer {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    font-weight: bold;
    font-size: 18px;
    text-transform: uppercase;
    font-style: italic;
}
</style>