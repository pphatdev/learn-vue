<script setup lang="ts">
import { ref, computed } from 'vue'
const newItem = ref('')
const countLength = computed(() => newItem.value.length)
</script>

<template>
    <div class="container max-w-lg mx-auto">
        <h1 class="text-4xl font-bold">HTML Attribute v-bind</h1>

        <input type="text" v-model="newItem" class="w-full px-3 py-2 my-5 border border-gray-300 rounded-xl" placeholder="Enter a value">

        <p class="mt-4"> {{ countLength }} / unlimited </p>
    </div>

</template>