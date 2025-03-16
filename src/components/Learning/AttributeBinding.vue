<script setup lang="ts">
import { ref } from 'vue'
const inputValue = ref('')

</script>


<template>

    <div class="container max-w-lg mx-auto">
        <h1 class="text-4xl font-bold">HTML Attribute v-bind</h1>

        <input type="text" v-model="inputValue" class="w-full px-3 py-2 my-5 border border-gray-300 rounded-xl" placeholder="Enter a value">

        <div class="flex gap-4">
            <button :disabled="inputValue.length <= 5" class="px-3 py-2 text-white bg-blue-500 rounded-xl disabled:bg-gray-500">Submit</button>
            <button :disabled="inputValue === ''" class="px-3 py-2 text-white bg-red-500 rounded-xl disabled:bg-gray-500">Cancel</button>
        </div>
        <p class="mt-4">
            If the input value is less than or equal to 5 characters, the Submit button will be disabled. If the input value is empty, the Cancel button will be disabled.
        </p>
    </div>

</template>