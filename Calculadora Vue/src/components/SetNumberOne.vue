<script setup>
    const props = defineProps(['pegaNumero1'])
</script>
<template>
    <div class="grupo-input">
        <label for="num1">Primeiro Número</label>
        <input type="number" id="num1" placeholder="Digite aqui o número" @keyup="props.pegaNumero1">
    </div>
</template>