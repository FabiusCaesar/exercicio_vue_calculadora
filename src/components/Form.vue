<script setup>
    // Receber as variáveis reativas como props
    const props = defineProps({
        numA: Number,
        numB: Number,
        operation: String
    })
</script>

<template>
    <form>
        <div class="row p-3 mx-0 mt-4 bg-dark bg-opacity-50 rounded-5 justify-content-center">
            <div class="col-md-2 align-self-center">
                <!-- Emite evento de atualização ao alterar o valor -->
                <input :value="numA" @input="$emit('update:numA', $event.target.value)" class="form-control my-3 d-flex justify-content-center" type="number" placeholder="0" name="num-a">
                <label for="num-a" class="h5 text-center my-3 d-flex justify-content-center"
                    style=" font-weight: 700">Informe um número</label>
            </div>
            <div class="col-md-1 mx-5">
                <label for="seletor-operacao" class="h5 text-center my-3 d-flex justify-content-center"
                    style=" font-weight: 700">Selecione uma operação:</label>
                <!-- Emite evento de atualização para operação -->
                <select :value="operation" @change="$emit('update:operation', $event.target.value)" class="form-control my-3 text-center" name="seletor-operacao" id="seletor-operacao">
                    <option value="+">+</option>
                    <option value="-">-</option>
                    <option value="*">x</option>
                    <option value="/">/</option>
                </select>
            </div>
            <div class="col-md-2 align-self-center">
                <!-- Emite evento de atualização ao alterar o valor -->
                <input :value="numB" @input="$emit('update:numB', $event.target.value)" class="form-control my-3 d-flex justify-content-center" type="number" placeholder="0" name="num-b">
                <label for="num-b" class="h5 text-center my-3 d-flex justify-content-center"
                    style=" font-weight: 700">Informe um número</label>
            </div>
        </div>
    </form>
</template>