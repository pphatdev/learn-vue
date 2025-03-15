<script setup lang="ts">
import { ref } from 'vue'
const msg = ref('Fruits List')
const fruits = ref(['Apple', 'Banana', 'Mango', 'Orange'])
const fruitArrObj = ref([
    { id: 1, name: 'Apple', color: 'Red' },
    { id: 2, name: 'Banana', color: 'Yellow' },
    { id: 3, name: 'Mango', color: 'Green' },
    { id: 4, name: 'Orange', color: 'Orange' }
])
</script>

<template>
    <div class="container flex flex-wrap max-w-4xl gap-5 py-5 mx-auto">
        <h1 class="w-full text-4xl font-bold shrink-0">{{ msg }}</h1>
        <ul class="w-1/4 my-5 border divide-y divide-gray-200 rounded-xl">
            <!--
                The v-for directive is used to render a list of items based on an array. 
                The v-for directive requires a special syntax in the form of item in items, 
                where items is the source data array and item is an alias for the array element being iterated on.

                The :key attribute is required when using v-for to render a list of elements.
                The key attribute is used to identify each node in the list, so that Vue can identify which nodes have changed,
                added, or removed. This helps Vue to optimize the rendering of the list.

                {{ fruit }} is used to render the value of the current item in the list.
            -->
            <li class="px-4 py-1" v-for="fruit in fruits" :key="fruit">{{ fruit }}</li>
        </ul>

        <ul class="w-1/4 my-5 border divide-y divide-gray-200 rounded-xl">
            <!-- fruits.forEach( fruit => {} ) -->
            <li class="px-4 py-1" v-for="fruit in fruitArrObj" :key="fruit.id"> {{ fruit.name }} </li>
        </ul>

        <ul class="w-1/4 my-5 border divide-y divide-gray-200 rounded-xl">
            <!-- fruits.forEach( (fruit, index) => {} ) -->
            <li class="px-4 py-1" v-for="(fruit, index) in fruits" :key="index">{{ index + 1 }}. {{ fruit }}</li>
        </ul>

        <ul class="w-1/4 my-5 border divide-y divide-gray-200 rounded-xl">
            <!-- fruitArrObj.forEach( ({id, name}, index) => {} ) -->
            <li class="px-4 py-1" v-for="({ id, name }, index) in fruitArrObj" :key="id"> {{ index + 1 }}. {{ name }} {{ id }}</li>
        </ul>
    </div>

</template>