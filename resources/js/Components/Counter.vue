<script>
export default {
    data() {
        return {
            count: 0,
        }
    },
    methods: {
        increment() {
            this.count++
        },
        decrement() {
            this.count--
        }
    }
}
</script>

<template>
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
</template>
