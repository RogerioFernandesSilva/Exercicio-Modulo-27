<script setup>
    const props = defineProps(['pegaNumero2'])
</script>
<template>
    <div class="grupo-input">
        <label for="num1">Segundo Número</label>
        <input type="number" id="num2" placeholder="Digite aqui o número" @keyup="props.pegaNumero2">
    </div>
</template>