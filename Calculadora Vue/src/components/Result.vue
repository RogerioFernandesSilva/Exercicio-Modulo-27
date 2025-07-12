<script setup>
    const props = defineProps(['results'])
</script>

<template>
    <h2>Resultado</h2>
    <span :class="{ 'erro': typeof props.results === 'string' }"> {{ props.results }}</span>
</template>