<script setup lang="ts">
    import { ref, reactive } from 'vue'
    const msg = ref('Hello, Vue 3!')
    const obj = reactive({ count: 0 })
</script>

<template>
    <div class="container max-w-lg mx-auto">
        <h1 class="text-4xl font-bold">Reactivity</h1>

        <p>{{ msg }}</p>
        <p>{{ obj.count }}</p>

        <button @click="msg = 'Hello, Vue 3! ' + obj.count++" class="px-3 py-2 mt-5 text-white bg-blue-500 rounded-xl">Increment</button>
    </div>
</template>