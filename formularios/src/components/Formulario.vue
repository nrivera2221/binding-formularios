<script>
    export default {
        name: "Formulario",
            // Función de datos que devuelve un objeto que representa el estado del componente
            data(){
                return{
                    formulario: {
                        titulo: '',
                        chip: '',
                        numero: '',
                        fechaExpiracion: '',
                        propietario: '',
                        tipoSRC: ''
                    }
                }
            },
            methods: {
                // Función de datos que devuelve un objeto que representa el estado del componente
                emitData() {
                    console.log(this.formulario);
                    this.$emit('datos-actualizados', { ...this.formulario }); // Emitir todo el objeto 'formulario'
                }
            }
};
</script>
<template>
    <form @submit.prevent="submitForm">
        <div>
            <label>Título de la tarjeta: </label>
            <input v-model="formulario.titulo"  @input="emitData" />
        </div>
        <div>
            <label>Chip SRC: </label>
            <input v-model="formulario.chip"  @input="emitData"/>
        </div>
        <div>
            <label>Número: </label>
            <input v-model="formulario.numero" @input="emitData"  />
        </div>
        <div>
            <label>Fecha de expiración: </label>
            <input v-model="formulario.fechaExpiracion" @input="emitData" />
        </div>
        <div>
            <label>Propietario: </label>
            <input v-model="formulario.propietario" @input="emitData" />
        </div>
        <div>
            <label>Tipo de tarjeta SRC: </label>
            <input v-model="formulario.tipoSRC" @input="emitData" />
        </div>
    </form>

</template>
<style scoped>
    form {
        padding: 18px;
        border-radius: 20px;
        border: ridge 1px;
        box-shadow: 1px 1px 1px 1px gray;
        font-weight: bold;
        display: flex;
        flex-direction: column;
        gap: 15px;
        justify-content: center;
    }
    form div {
        display: grid;
        grid-template-columns: 100px 200px;
        align-items: center;
        gap: 5px;
    }

    form div label {
        text-align: right;
    }
</style>