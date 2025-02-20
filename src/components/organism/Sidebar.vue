<script setup lang="ts">
import { LayoutDashboard, Settings, LogOut } from 'lucide-vue-next';
import { useRoute } from 'vue-router';

const route = useRoute();
let sidebar: any;
let logout: any;

const initialWitdhDashboard = () => {
    sidebar = document.getElementById('sidebar');
    logout = document.getElementById('logout');
    logout?.classList.add('w-[130px]');
    sidebar?.classList.add('w-[180px]');
}

onMounted(() => {
    document.getElementById('sidebar');
    setTimeout(() => {
        initialWitdhDashboard();
        setTimeout(() => {
            sidebar?.classList.remove('w-[180px]');
            logout?.classList.remove('w-[130px]');
        }, 1500);
    }, 0);

})

</script>

<template>
    <aside id="sidebar"
        class="group mt-5 mb-5 pt-5 pb-5 ml-3 w-[60px] h-[95vh] bg-[#27264E] overflow-hidden rounded-lg text-white flex flex-col justify-between items-start transition-all backgroud duration-700 ease-in-out  hover:w-[180px]">
        <div class="max-w-[220px] w-full mx-auto">
            <nav>
                <ul class="flex flex-col pl-2 gap-2 items-start ">
                    <li class="w-[40px] h-[40px] flex items-center gap-3">
                        <NuxtLink to="/dashboard" class="p-2 flex gap-2"
                            :class="{ 'font-bold rounded-md bg-[#6359E9]': route.path === '/dashboard' }">
                            <LayoutDashboard />
                        </NuxtLink>
                        <p :class="{ 'font-bold': route.path === '/dashboard' }">Dashboard</p>
                    </li>
                    <li class="w-[40px] h-[40px] flex items-center gap-3">
                        <NuxtLink to="/dashboard/settings" class="p-2 flex gap-2"
                            :class="{ 'font-bold rounded-md bg-[#6359E9]': route.path === '/dashboard/settings' }">
                            <Settings />
                        </NuxtLink>
                        <p :class="{ 'font-bold': route.path === '/dashboard/settings' }">Settings</p>
                    </li>
                </ul>
            </nav>
        </div>

        <div class="flex ml-2 justify-items-start items-start">
            <NuxtLink to="/">
                <button id="logout"
                    class="w-[40px] h-[40px] flex rounded-lg justify-center items-center bg-neutral-700 group-hover:w-[130px] transition-all backgroud duration-700 ease-in-out hover:bg-neutral-600 hover:cursor-pointer">
                    <LogOut />
                </button>
            </NuxtLink>
        </div>
    </aside>
</template>

<style scoped></style>