<script setup lang="ts">
import { ref } from 'vue'

type Fruit = {
    id: number
    name?: string
}

const fruits = ref<Fruit[]>([])
const newFruit = ref('')
const addFruit = () => {
    if (newFruit.value.trim() !== '') {
        fruits.value.push({
            id: fruits.value.length + 1,
            name: newFruit.value
        })
        newFruit.value = ''
    }
}

const editing = ref(false)
const reset = () => {
    newFruit.value = ''
    editing.value = false
}

</script>

<template>

    <form @submit.prevent="addFruit" class="container flex flex-wrap max-w-4xl gap-5 px-10 py-5 mx-auto">
        <h1 class="w-full text-4xl font-bold shrink-0">Fruits List</h1>
        <div class="flex items-center justify-between w-full gap-4">
            <input type="text" v-model="newFruit" @keyup.prevent="editing = newFruit != '' ? true : false" placeholder="Enter a fruit name" class="w-1/2 px-3 py-2 my-5 border border-gray-300 rounded-xl">
            <button type="reset" v-if="editing" @click="reset" class="w-1/2 px-3 py-2 text-white bg-red-500 rounded-xl">Cancel</button>
        </div>
    </form>

    <div class="container flex flex-wrap max-w-4xl gap-5 px-10 py-5 mx-auto">

        <ul class="w-full border border-gray-300 divide-y divide-border rounded-xl">
            <li v-for="({id, name}) in fruits" :key="id" class="px-4 py-2">
                {{ id }}. {{ name }}
            </li>

            <li v-if="fruits.length === 0" class="px-4 py-1 text-center">
                No fruits available
            </li>
        </ul>

    </div>

</template>