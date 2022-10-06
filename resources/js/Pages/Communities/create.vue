<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Link, useForm } from '@inertiajs/inertia-vue3';

const form = useForm({
    name: '',
    description: '',
    slug: '',
    terms: false,
});
const submit = () => {
    form.post(route('communities.store'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
   <Head title="Create Community" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Create Community
            </h2>
        </template>

        <div class="block p-6 rounded-lg shadow-lg mx-auto mt-5 bg-white max-w-sm">
               <form @submit.prevent="submit">
            <div>
                <InputLabel for="name" value="Name" />
                <TextInput id="name" type="text" class="mt-1 block w-full" v-model="form.name" required autofocus autocomplete="name" />
                <InputError class="mt-2" :message="form.errors.name" />
            </div>
            <div>
                <InputLabel for="slug" value="Slug" />
                <TextInput id="slug" type="text" class="mt-1 block w-full" v-model="form.slug" required  autocomplete="slug" />
                <InputError class="mt-2" :message="form.errors.slug" />
            </div>
             <div>
                <InputLabel for="description" value="Description" />
                <TextInput id="description" type="text" class="mt-1 block w-full" v-model="form.description" required  autocomplete="description" />
                <InputError class="mt-2" :message="form.errors.description" />
            </div>
           


            <div class="flex items-center justify-end mt-4">
               

                <PrimaryButton class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                   Create
                </PrimaryButton>
            </div>
        </form>
        </div>
    </AuthenticatedLayout>
</template>


