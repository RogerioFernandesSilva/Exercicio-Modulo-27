<script setup>
    const props = defineProps(['showOperation', 'operation'])
</script>
<template>
    <div class="set-operacao">
        <select @change="props.showOperation" :value="props.operation">
            <option value="-">Subtração</option>
            <option value="+">Adição</option>
            <option value="x">Mutiplicação</option>
            <option value="/">Divisão</option>
        </select>
        <div class="view-operacao">
            Operação selecionada: {{ props.operation }}
        </div>
    </div>
</template>