<template>
    <div class="px-6 pt-10 sm:px-6 lg:px-40">
        <div class="sm:flex sm:items-center">
            <div class="sm:flex-auto">
                <h1 class="text-base font-semibold leading-6 text-gray-900">
                    All your sites
                </h1>
                <p class="mt-2 text-sm text-gray-700">
                    A list of all the users in your account including their
                    name, title, email, and role.
                </p>
            </div>
            <div class="mt-4 sm:mt-0 sm:ml-16 sm:flex-none">
               
                    <button
                        @click="CreateSite"
                        class="block rounded-md bg-indigo-600 py-2 px-3 text-center text-sm"
                    >
                        Add Site
                    </button>
             
            </div>
        </div>

        <div class="mt-8 flow-root">
            <div class="-my-2 -mx-4 overflow-x-auto sm:mx-6 lg:-mx-8">
                <div
                    class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8"
                >
                    <table class="min-w-full divide-y divide-gray-300">
                        <thead>
                            <tr>
                                <th
                                    scope="col"
                                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                                >
                                    Name
                                </th>
                                <th
                                    scope="col"
                                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                                >
                                    URL
                                </th>
                                <th
                                    scope="col"
                                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                                >
                                    Status
                                </th>
                                <th
                                    scope="col"
                                    class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                                >
                                    Role
                                </th>
                                <th
                                    scope="col"
                                    class="relative py-3.5 pl-3 pr-4 sm:pr-0"
                                >
                                    <span class="sr-only">Edit</span>
                                </th>
                            </tr>
                        </thead>

                        <tbody class="divide-y divide-gray-200">
                            <tr
                                v-for="monitors in monitors.data"
                                :key="monitors.id"
                            >
                                <td
                                    class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                                >
                                    {{ monitors.site_name }}
                                </td>
                                <td
                                    class="whitespace-nowrap py-4 px-3 text-sm text-gray-500"
                                >
                                    {{ monitors.site_url }}
                                </td>
                                <td
                                    class="whitespace-nowrap py-4 px-3 text-sm text-gray-500"
                                >
                                    {{ monitors.status }}
                                </td>
                                <td
                                    class="whitespace-nowrap py-4 px-3 text-sm text-gray-500"
                                >
                                    {{ monitors.role }}
                                </td>
                                <td
                                    class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm front-medium sm:pr-0"
                                >
                                    <a
                                        href="#"
                                        class="text-indigo-600 hover:text-indigo-900"
                                        >Edit
                                        <span class="sr-only"
                                            >, {{ monitors.name }}</span
                                        >
                                    </a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
    <Paginate 
    :next="monitors.next_page_url" 
    :prev="monitors.prev_page_url"
    :last="monitors.last_page"
    :total="monitors.total"
    :currentPage="monitors.current_page"
    />
</template>

<script setup>
import { router } from "@inertiajs/vue3";
import Paginate from "@/components/Paginate.vue"
defineProps(["monitors"]);

function CreateSite() {
    console.log('Button clicked');
    router.visit('/site/create');
};
</script>
