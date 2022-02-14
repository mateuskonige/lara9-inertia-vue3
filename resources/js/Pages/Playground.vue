<script setup>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import { Head } from '@inertiajs/inertia-vue3';
import { Link } from '@inertiajs/inertia-vue3';

</script>
<script>

export default {
    data() {
        return {
            count: 0,
            word: '',
            reversedWord: '',
        }
    },
    methods: {
        increment() {
            this.count++
        },
        decrement() {
            this.count--
        },
        reverse() {
            this.reversedWord = this.word.split("").reverse().join("")
        }
    }
}
</script>

<template>
    <Head title="Playground" />

    <BreezeAuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Playground</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200 text-center">
                        <h3 class="text-2xl text-left">Playground</h3>
                        <hr />
                        <h4 class="text-xl my-6">Counter</h4>

                        <button
                            @click="increment"
                            class="px-6 py-2 bg-green-600 text-white font-bold rounded-full hover:bg-green-500 transition ease-in-out"
                        >+</button>
                        <h3 class="text-2xl my-6">{{ count }}</h3>
                        <button
                            @click="decrement"
                            class="px-6 py-2 bg-red-600 text-white font-bold rounded-full hover:bg-red-500 transition ease-in-out"
                        >-</button>
                        <hr class="mt-6" />
                        <h4 class="text-xl my-6">Reverse Word</h4>
                        <input
                            type="text"
                            v-model="word"
                            class="w-full sm:w-96 bg-gray-100 outline-none border-0 rounded-full sm:rounded-r-none"
                        />
                        <button
                            @click="reverse"
                            class="px-6 py-2 bg-green-600 text-white font-bold rounded-full sm:rounded-l-none hover:bg-green-500 transition ease-in-out"
                        >Reverse!</button>

                        <p class="my-4">
                            <b>Reversed:</b>
                            {{ reversedWord }}
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </BreezeAuthenticatedLayout>
</template>
