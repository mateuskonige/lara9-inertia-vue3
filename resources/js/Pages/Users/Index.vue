<script setup>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import BreezeButton from '@/Components/Button.vue';
import { Head } from '@inertiajs/inertia-vue3';
import { Link } from '@inertiajs/inertia-vue3';
import Modal from '@/Components/Modal.vue';
import Table from '@/Components/Table.vue';
</script>

<script>
export default {
    props: {
        users: Object,
    },

    data() {
        return {
            openModal: false,
        }
    }
}
</script>

<template>
    <Modal :open="openModal" @closed="openModal = false" />

    <Head title="Users" />

    <BreezeAuthenticatedLayout>
        <template #header>
            <div class="flex items-center justify-between">
                <h2 class="font-semibold text-xl text-gray-800 leading-tight">Users</h2>

                <BreezeButton type="button" @click="openModal = !openModal">Adicionar</BreezeButton>
            </div>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200 text-center">
                        <Table :users="users" />
                    </div>
                </div>
            </div>
        </div>
    </BreezeAuthenticatedLayout>
</template>
