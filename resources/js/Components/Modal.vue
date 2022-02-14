<template>
    <TransitionRoot as="template" :show="open">
        <Dialog as="div" class="fixed z-10 inset-0 overflow-y-auto" @close="open = false">
            <div
                class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0"
            >
                <TransitionChild
                    as="template"
                    enter="ease-out duration-300"
                    enter-from="opacity-0"
                    enter-to="opacity-100"
                    leave="ease-in duration-200"
                    leave-from="opacity-100"
                    leave-to="opacity-0"
                >
                    <DialogOverlay
                        class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
                    />
                </TransitionChild>

                <!-- This element is to trick the browser into centering the modal contents. -->
                <span
                    class="hidden sm:inline-block sm:align-middle sm:h-screen"
                    aria-hidden="true"
                >&#8203;</span>
                <TransitionChild
                    as="template"
                    enter="ease-out duration-300"
                    enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                    enter-to="opacity-100 translate-y-0 sm:scale-100"
                    leave="ease-in duration-200"
                    leave-from="opacity-100 translate-y-0 sm:scale-100"
                    leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
                >
                    <div
                        class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
                    >
                        <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                            <div class="mt-3 text-center sm:mt-0 sm:text-left">
                                <DialogTitle
                                    as="h3"
                                    class="text-lg leading-6 font-medium text-gray-900"
                                >Add new user</DialogTitle>
                                <div class="mt-2">
                                    <form @submit.prevent="submit">
                                        <div>
                                            <BreezeLabel for="name" value="Name" />
                                            <BreezeInput
                                                id="name"
                                                type="text"
                                                class="mt-1 block w-full"
                                                v-model="form.name"
                                                required
                                                autofocus
                                                autocomplete="name"
                                            />
                                        </div>

                                        <div class="mt-4">
                                            <BreezeLabel for="email" value="Email" />
                                            <BreezeInput
                                                id="email"
                                                type="email"
                                                class="mt-1 block w-full"
                                                v-model="form.email"
                                                required
                                                autocomplete="username"
                                            />
                                        </div>

                                        <div class="mt-4">
                                            <BreezeLabel for="password" value="Password" />
                                            <BreezeInput
                                                id="password"
                                                type="password"
                                                class="mt-1 block w-full"
                                                v-model="form.password"
                                                required
                                                autocomplete="new-password"
                                            />
                                        </div>

                                        <div class="mt-4">
                                            <BreezeLabel
                                                for="password_confirmation"
                                                value="Confirm Password"
                                            />
                                            <BreezeInput
                                                id="password_confirmation"
                                                type="password"
                                                class="mt-1 block w-full"
                                                v-model="form.password_confirmation"
                                                required
                                                autocomplete="new-password"
                                            />
                                        </div>
                                    </form>
                                </div>
                            </div>
                        </div>
                        <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                            <button
                                :disabled="form.processing"
                                type="button"
                                class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-green-600 text-base font-medium text-white hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 sm:ml-3 sm:w-auto sm:text-sm"
                                @click="saveUser"
                            >Save</button>
                            <button
                                type="button"
                                class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
                                @click="open = false"
                                ref="cancelButtonRef"
                            >Cancel</button>
                        </div>
                    </div>
                </TransitionChild>
            </div>
        </Dialog>
    </TransitionRoot>
</template>

<script setup>
import { useForm } from "@inertiajs/inertia-vue3";

const form = useForm({
    name: "",
    email: "",
    password: "",
    password_confirmation: "",
    terms: false,
});
</script>

<script>
import { ref } from "vue";
import {
    Dialog,
    DialogOverlay,
    DialogTitle,
    TransitionChild,
    TransitionRoot,
} from "@headlessui/vue";
import { ExclamationIcon } from "@heroicons/vue/outline";
import BreezeButton from "@/Components/Button.vue";
import BreezeInput from "@/Components/Input.vue";
import BreezeLabel from "@/Components/Label.vue";

export default {
    components: {
        Dialog,
        DialogOverlay,
        DialogTitle,
        TransitionChild,
        TransitionRoot,
        ExclamationIcon,
    },

    props: {
        open: Boolean,
    },

    watch: {
        open() {
            if (!this.open) {
                this.$emit("closed");
            }
        },
    },

    methods: {
        saveUser() {
            this.form.post(route("users.store"), {
                onFinish: () => console.log(this.form),
            });
            this.$emit("closed");
        },
    },
};
</script>
