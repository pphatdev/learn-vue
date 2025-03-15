<script setup lang="ts">
    import {ref} from 'vue'
    const msg = ref('Hello Vite + Vue')
</script>

<template>
    <h1>{{ msg }}</h1>
    <h1>{{ msg.toLocaleUpperCase() }}</h1>
    <h1>{{ msg.toLocaleLowerCase()}}</h1>
</template>