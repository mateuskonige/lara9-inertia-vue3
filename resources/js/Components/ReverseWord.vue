<script>
export default {
    data() {
        return {
            word: '',
            reversedWord: '',
        }
    },
    methods: {
        reverse() {
            this.reversedWord = this.word.split("").reverse().join("")
        }
    }
}
</script>

<template>
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

    <hr class="mt-6" />
</template>
