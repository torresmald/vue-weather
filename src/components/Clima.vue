<script setup>
import formatearClima from '../helpers/formatearClima.js'


const props = defineProps({
    clima: {
        type: Object,
        required: true
    }
});
</script>
<template >
    <div class="resultado">
        
        <h2>Clima de : {{ clima.name}} </h2>
        <p class="actual">
            {{ formatearClima(clima.main.temp) }} &deg;C
        </p>
        <div class="temperatura">
            <p>Min: {{ formatearClima(clima.main.temp_min) }} &deg;C</p>
            <p>Max: {{ formatearClima(clima.main.temp_max) }} &deg;C</p>
        </div>
    </div>
</template>

