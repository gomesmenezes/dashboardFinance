<script setup lang="ts">

const stockProps = defineProps({
    stockOption: String,
    stockQuantityLabel: Number,
    stockPriceLabel: Number,
    stockPercentageLabel: Number
})

</script>

<template>
    <div class="w-full flex gap-3 items-center justify-between px-3 py-2">
        <div class="flex gap-3 items-center">
            <div class="logo">
                <div class="bg-[#6359E9] rounded-full w-[40px] h-[40px] "></div>
            </div>
            <div class="labels">
                <p>{{ stockProps.stockOption }}</p>
                <p>Quantity: {{ stockProps.stockQuantityLabel }}</p>
            </div>
        </div>

        <div class="valuation">
            <p>R$ {{ stockProps.stockPriceLabel }}</p>
            <p class="bg-[##02b1593d] flex justify-center rounded-full">{{
                stockProps.stockPercentageLabel }}%
            </p>
        </div>
    </div>
</template>

<style scoped></style>