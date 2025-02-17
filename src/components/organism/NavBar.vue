<script setup lang="ts">
import Chip from 'primevue/chip';
</script>

<template>
    <header class="w-screen h-[70px] bg-[#6359E9] flex items-center justify-between px-[30px]">
        <div class="logo text-white text-3xl text-center font-semibold">
            MyFinance
        </div>
        <nav>
            <ul>
                <Chip label="Amy Elsner" image="https://primefaces.org/cdn/primevue/images/avatar/amyelsner.png" />
            </ul>

        </nav>
    </header>
</template>

<style scoped>
.p-chip {
    background-color: #3b3b3b !important;
    color: white !important;
}
</style>