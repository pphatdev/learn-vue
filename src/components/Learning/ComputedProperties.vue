<script setup lang="ts">
    import type { Fruit } from '@/types/fruit'
    import { ref, computed } from 'vue'
    const newItem = ref('')
    const countLength = computed(() => newItem.value.length)
    const fruits = ref<Fruit[]>([])

    const addFruit = () => {
        if (newItem.value.trim() !== '') {
            fruits.value.push({
                id: fruits.value.length + 1,
                name: newItem.value
            })
            newItem.value = ''
        }
    }

    const reverseFruits = computed(() => [...fruits.value].reverse())

</script>

<template>
    <div class="container max-w-lg mx-auto">
        <h1 class="text-4xl font-bold">HTML Attribute v-bind</h1>

        <input type="text" v-model="newItem" class="w-full px-3 py-2 my-5 border border-gray-300 rounded-xl" placeholder="Enter a value">

        <div class="flex gap-4">
            <button :disabled="newItem.length <= 3" @click="addFruit" class="px-3 py-2 text-white bg-blue-500 rounded-xl disabled:bg-gray-500">Submit</button>
            <button :disabled="newItem === ''" class="px-3 py-2 text-white bg-red-500 rounded-xl disabled:bg-gray-500">Cancel</button>
        </div>

        <p class="mt-4"> {{ countLength }} / unlimited </p>

        <ul class="mt-5 divide-gray-200 rounded-xl" :class="{ 'border divide-y': fruits.length > 0 }">
            <li v-for="(fruit, index) in reverseFruits" :key="fruit.id" class="px-4 py-2">
                {{ index + 1 }}. {{ fruit.name }}
            </li>
        </ul>
    </div>

</template>