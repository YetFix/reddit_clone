<script>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';

import PrimaryButton from '@/Components/PrimaryButton.vue';

import { Link } from '@inertiajs/inertia-vue3';


 
    export default{
      
            props: {
                communities: Object
            }
        }
 
    
  
    

</script>

<template>
   <Head title="All Community" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                All Communities
            </h2>
        </template>
       
        <div class="p-6 rounded-lg shadow-lg mx-auto mt-5 bg-white max-w-screen-md">
               
            <div class="overflow-x-auto relative shadow-md sm:rounded-lg">
                <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                    <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                        <tr>
                            <th scope="col" class="py-3 px-6">
                               Community name
                            </th>
                            <th scope="col" class="py-3 px-6">
                               Community Slug
                            </th>
                          
                            <th scope="col" class="py-3 px-6">
                                Action
                            </th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="c in communities" :key="c.id" class="bg-white border-b dark:bg-gray-900 dark:border-gray-700">
                            <th scope="row" class="py-4 px-6 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                               {{c.name}}
                            </th>
                           
                            <td class="py-4 px-6">
                               {{c.slug}}
                            </td>
                            <td class="py-4 px-6">
                                <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
                            </td>
                        </tr>
                      
                    </tbody>
                </table>
            </div>

        </div>
    </AuthenticatedLayout>
</template>


