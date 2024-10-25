<script setup>
    // Receber o objeto display como propriedade
    const props = defineProps({
        display: Object
    })
</script>

<template>
    <div class="p-4 mt-5 bg-dark bg-opacity-10 rounded-5">

        <!-- Exibir a expressão matemática com v-html -->
        <h2 class="text-center" v-html="display.expr"></h2>

        <!-- Exibir o resultado ou erro condicionalmente -->
        <h2 class="text-center"
            :style="{ color: display.result === 'Erro. Impossível dividir por zero!' ? 'red' : 'black' }">
            <span v-if="display.result !== 'Erro. Impossível dividir por zero!'">=</span> {{ display.result }}
        </h2>

    </div>
</template>