<script setup lang="ts">

import { ref } from 'vue'

const list = ref([
    { id: 1, name: 'Apple', color: 'Red' },
    { id: 2, name: 'Banana', color: 'Yellow' },
    { id: 3, name: 'Mango', color: 'Green' },
    { id: 4, name: 'Orange', color: 'Orange' }
])

const name = ref('')

const addFruit = () => {
    list.value.push({
        id: list.value.length + 1,
        name: name.value,
        color: 'Random'
    })

    name.value = '' // Clear the input field
}

</script>

<template>
    <div class="container flex flex-col max-w-lg gap-4 py-5 mx-auto">
        <h1 class="text-4xl font-bold">User Events Handling</h1>

        <input type="text" v-model="name" v-on:keyup.enter="addFruit" placeholder="Enter your name" class="w-full px-5 py-2 border rounded-xl focus:outline-none">

        <div class="p-5 border rounded-xl">
            <h2>Using @</h2>
            <div class="flex items-center w-full gap-3">
                <button @click="addFruit" class="flex-shrink-0 px-5 py-2 text-white bg-blue-500 rounded-xl">Add Fruit</button>
            </div>
        </div>

        <div class="p-5 border rounded-xl">
            <h2>Using v-on (function)</h2>
            <div class="flex items-center w-full gap-3">
                <button v-on:click="addFruit" class="flex-shrink-0 px-5 py-2 text-white bg-blue-500 rounded-xl">Add Fruit</button>
            </div>
        </div>

        <div class="p-5 border rounded-xl">
            <h2>Using v-on (In line)</h2>
            <div class="flex items-center w-full gap-3">
                <button v-on:click="list.push(
                    { id: list.length + 1, name: name, color: 'Random' }
                )" class="flex-shrink-0 px-5 py-2 text-white bg-blue-500 rounded-xl">Add Fruit</button>
            </div>
        </div>

        <ul class="border divide-y divide-gray-200 rounded-xl">
            <li v-for="({ id, name, color }) in list" :key="id" class="px-4 py-2">
                <p>{{ name }} - {{ color }}</p>
            </li>
        </ul>

        <form v-on:submit.prevent="addFruit" class="flex flex-col gap-4 p-5 border rounded-xl">
            <h1 class="font-bold">Using Form Control</h1>
            <input type="text" v-model="name" placeholder="Enter your name" class="w-full px-5 py-2 border rounded-xl focus:outline-none">
            <button class="flex-shrink-0 px-5 py-2 text-white bg-blue-500 rounded-xl">Add Fruit</button>
        </form>
    </div>


</template>