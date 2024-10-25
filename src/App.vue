<script setup>
import { computed, ref } from 'vue';
import Header from './components/Header.vue';
import Display from './components/Display.vue';
import Form from './components/Form.vue';

// Variáveis reativas
const numA = ref(0);
const numB = ref(0);
const operation = ref('+');

// Cálculo do resultado
const display = computed(() => {
    const a = numA.value;
    const b = numB.value;
    const op = operation.value;
    const erroDivZero = op === '/' && b == 0;

    const resultado = erroDivZero ? 'Erro. Impossível dividir por zero!' : eval(`${a} ${op} ${b}`);
    
    return {
        expr: `<span style="opacity: 0.5;">${a}</span> <span style="opacity: 0.5;">${op}</span> <span style="${erroDivZero ? 'color: red;' : 'opacity: 0.5;'}">${b}</span>`,
        result: resultado
    };
})

</script>

<template>
    <div class="container d-flex flex-column justify-content-center min-vh-100" style="font-family: 'Orbitron', sans-serif;">
        <Header />
        <Display :display="display" />
        <Form v-model:numA="numA" v-model:numB="numB" v-model:operation="operation" />
    </div>
</template>

<style scoped>
/* Fonte Orbitron */
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap');
</style>
