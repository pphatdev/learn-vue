<script setup lang="ts">
import { ref } from 'vue'

const username = ref('')
const gender = ref('')
const email = ref('')

const genders = ref([
    { id: 1, name: 'Male' },
    { id: 2, name: 'Female' },
    { id: 3, name: 'Other' }
])

const checkbox = ref(false)
const checkboxes = ref([])
</script>

<template>
    <div class="container flex flex-wrap max-w-lg gap-5 py-5 mx-auto">
        <h1 class="w-full text-4xl font-bold shrink-0">User Input</h1>

        <div class="w-full border divide-y divide-gray-200 rounded-xl">
            <p class="w-full px-5 py-2">Your name is: {{ username }}</p>
            <p class="w-full px-5 py-2">Your gender is: {{gender}}</p>
            <p class="w-full px-5 py-2">Your email is: {{email}}</p>
        </div>


        <div class="flex w-full">
            <p class="w-full text-">Input your name</p>
            <input type="text" v-model="username" placeholder="Enter your name" class="w-full px-5 py-2 border rounded-xl focus:outline-none">
        </div>

        <div class="flex w-full">
            <p class="w-full">Select your gender </p>
            <select v-model="gender" class="w-full px-5 py-2 border rounded-xl focus:outline-none">
                <option selected value="" disabled> Select Gender </option>
                <option v-for="gen in genders" :key="gen.id" :value="gen.name">{{ gen.name }}</option>
            </select>
        </div>

        <div class="flex w-full">
            <p class="w-full text-">Input your email</p>
            <input type="text" v-model="email" placeholder="Enter your name" class="w-full px-5 py-2 border rounded-xl focus:outline-none">
        </div>

        <div class="w-full p-5 border rounded-xl">
            <h2 class="text-2xl font-bold">Checkbox</h2>
            <div class="flex gap-2 py-5">
                <input type="checkbox" v-model="checkbox" value="false" class="w-5 h-5">
            </div>
            <p>Checkbox value: {{ checkbox }}</p>

            <h2 class="mt-5 text-2xl font-bold">Checkboxes</h2>
            <div class="flex gap-2 py-5">
                <input type="checkbox" v-model="checkboxes" value="Banana" class="w-5 h-5">
                <input type="checkbox" v-model="checkboxes" value="Orange" class="w-5 h-5">
                <input type="checkbox" v-model="checkboxes" value="Apple" class="w-5 h-5">
            </div>
            <p>Checkbox value: {{ checkboxes }}</p>
        </div>
    </div>
</template>