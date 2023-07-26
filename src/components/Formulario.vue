<script setup>
import { reactive, ref } from 'vue';
import Alerta from './Alerta.vue';


const emit = defineEmits(['obtener-clima'])
const paises = [
    { codigo: 'US', nombre: 'Estados Unidos' },
    { codigo: 'MX', nombre: 'México' },
    { codigo: 'AR', nombre: 'Argentina' },
    { codigo: 'CO', nombre: 'Colombia' },
    { codigo: 'CR', nombre: 'Costa Rica' },
    { codigo: 'ES', nombre: 'España' },
    { codigo: 'PE', nombre: 'Perú' }
];
const busqueda = reactive({
    pais: '',
    ciudad: ''
});
const error = ref('');
const validarFormulario = () => {
    if(Object.values(busqueda).includes('')){
        error.value = 'Todos los campos son Obligatorios'
    }else{
        error.value = ''
        emit('obtener-clima', busqueda)
    }
};
</script>
<template>
    <form class="formulario" @submit.prevent="validarFormulario">
        <div class="campo">
            <label for="ciudad">Ciudad</label>
            <input type="text" id="ciudad" placeholder="Ciudad" v-model="busqueda.ciudad">
        </div>
        <div class="campo">
            <label for="pais">Pais</label>
            <select id="pais" v-model="busqueda.pais">
                <option value="">-- Seleccione Pais --</option>
                <option :value="pais.codigo" v-for="pais in paises">{{ pais.nombre }}</option>
            </select>
        </div>
        <input type="submit" value="Consultar">
    </form>
    <Alerta v-if="error"> {{ error }}</Alerta>
</template>

