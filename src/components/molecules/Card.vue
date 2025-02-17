<script setup>
import { MoveDownLeft } from 'lucide-vue-next';
const investValue = [1000, 350, 150];
const totalValue = investValue.reduce((acc, val) => acc + val, 0);

</script>

<template>
    <div
        class="container max-w-[300px] w-[300px] max-h-[100px] h-[100px] ml-10 bg-[#1D1D41] rounded-[20px] py-4 px-7 flex items-center">
        <div class="content h-[54px] gap-4 flex">
            <div class="icon flex items-center">
                <div class="container-icon bg-[#827be6] h-[45px] w-[45px] flex items-center justify-center rounded-lg">
                    <MoveDownLeft color="white" />
                </div>
            </div>
            <div class="text-label text-white flex flex-col items-start justify-center">
                <p>Total Income</p>
                <p class="font-bold">R$ {{ totalValue }}</p>
            </div>
            <div class="porcentag rounded-lg h-[30px] w-[54px] bg-[#02b1593d] flex items-center justify-center mt-auto">
                <p class="font-light text-[#02B15A] flex items-center justify-center">+0%</p>
            </div>
        </div>
    </div>
</template>

<style scoped></style>