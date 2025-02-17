<script setup lang="ts">
import { LayoutDashboard, Settings, LogOut } from 'lucide-vue-next';
import { useRoute } from 'vue-router';
import NavBar from '~/components/organism/NavBar.vue';

const route = useRoute();

</script>

<template>
    <aside
        class="pt-14 h-screen bg-[#27264E] rounded-tr-lg rounded-br-lg text-white flex flex-col justify-between items-start">
        <div class="max-w-[220px] w-full mx-auto">
            <nav>
                <ul class="flex flex-col justify-center gap-2">
                    <li>
                        <NuxtLink to="/dashboard" class="p-2 flex gap-2"
                            :class="{ 'font-bold rounded-md bg-[#6359E9]': route.path === '/dashboard' }">
                            <LayoutDashboard />

                        </NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/dashboard/settings" class="p-2 flex gap-2"
                            :class="{ 'font-bold rounded-md bg-[#6359E9]': route.path === '/dashboard/settings' }">
                            <Settings />
                        </NuxtLink>
                    </li>
                </ul>
            </nav>
        </div>

        <div class="max-w-[220px] w-full mx-auto mb-14 ">
            <NuxtLink to="/">
                <button
                    class="rounded-lg w-full items-center px-4 py-3 gap-3 bg-neutral-700 hover:bg-neutral-600 hover:cursor-pointer">
                    <LogOut />
                </button>
            </NuxtLink>
        </div>
    </aside>
</template>

<style scoped></style>