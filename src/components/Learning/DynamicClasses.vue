<script setup lang="ts">
import { ref } from 'vue'
const msg = ref('Fruits List')
const fruits = ref([
    { id: 1, name: 'Apple', checked: true },
    { id: 2, name: 'Banana', checked: true },
    { id: 3, name: 'Mango', checked: true },
    { id: 4, name: 'Orange', checked: false }
])
</script>

<template>
    <div class="container flex flex-wrap max-w-lg gap-5 py-5 mx-auto">
        <h1 class="w-full text-4xl font-bold shrink-0">{{ msg }}</h1>
        <ul class="w-full my-5 border divide-y divide-gray-200 rounded-xl">
            <li class="px-4 py-1 font-medium cursor-pointer"
                v-for="({ id, name }, index) in fruits"
                :key="id"
                :class="{ 'line-through text-red-500': fruits[index].checked, 'text-green-500': !fruits[index].checked }"
                @click="fruits[index].checked = !fruits[index].checked"
            >
                {{ index + 1 }}. {{ name }}
            </li>
        </ul>
    </div>

</template>