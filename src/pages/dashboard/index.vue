<script setup lang="ts">
import { reactive } from 'vue';
import Sidebar from '~/components/organism/Sidebar.vue';
import Chart from 'primevue/chart';
import Card from '~/components/molecules/Card.vue';
import Chip from 'primevue/chip';
import CardIncome from '~/components/molecules/CardIncome.vue';
import AssetsCards from '~/components/molecules/AssetsCards.vue';

const investValue = [1000, 350, 150];
const totalValue = investValue.reduce((acc, val) => acc + val, 0);

const chartData = reactive({
    labels: ['Reserva de Emergência', 'Ações', 'Criptomoedas'],
    datasets: [
        {
            data: investValue,
            backgroundColor: ['#98FB98', '#FF8C00', '#FF3131'],
        }
    ]
});

const chartOptions = reactive({
    responsive: true,
    maintainAspectRatio: true,
    plugins: {
        legend: {
            position: 'bottom'
        },
        tooltip: {
            callbacks: {
                label: (tooltipItem: any) => {
                    let value = tooltipItem.raw;
                    return `R$ ${value.toLocaleString('pt-BR')}`;
                }
            }
        },
        datalabels: {
            color: '#fff',
            font: {
                weight: 'bold'
            },
            formatter: (value: number) => {
                const percentual = ((value / totalValue) * 100).toFixed(2);
                return ` R$ ${value.toLocaleString()} \n (${percentual}%)`;
            }
        }
    }
});

const stocks = [
    {
        stockName: 'Apple',
        stockQuantity: 10,
        stockPriceBuy: 100,
        stockPriceCurrent: 200,
        stockValuation: 15
    },
    {
        stockName: 'Microsoft',
        stockQuantity: 15,
        stockPriceBuy: 150,
        stockPriceCurrent: 250,
        stockValuation: 20
    },
    {
        stockName: 'Google',
        stockQuantity: 8,
        stockPriceBuy: 1200,
        stockPriceCurrent: 1500,
        stockValuation: 12.5
    },
    {
        stockName: 'Amazon',
        stockQuantity: 5,
        stockPriceBuy: 1700,
        stockPriceCurrent: 1900,
        stockValuation: 11.8
    },
    {
        stockName: 'Tesla',
        stockQuantity: 12,
        stockPriceBuy: 600,
        stockPriceCurrent: 900,
        stockValuation: 30
    },
    {
        stockName: 'Nvidia',
        stockQuantity: 20,
        stockPriceBuy: 500,
        stockPriceCurrent: 750,
        stockValuation: 25
    }
];


</script>

<template>
    <div class="container w-screen">
        <div class="container-sidebar flex bg-[#151530] w-screen">
            <Sidebar />
            <div class="w-full">
                <div class="navbarDashboard flex justify-between items-center w-full p-10">
                    <div class="welcome w-full">
                        <h1 class="text-3xl font-bold text-white">Seja Bem vindo, ${nameUser}</h1>
                    </div>
                    <div>
                        <nav>
                            <ul>
                                <Chip label="Amy Elsner"
                                    image="https://primefaces.org/cdn/primevue/images/avatar/amyelsner.png" />
                            </ul>

                        </nav>
                    </div>
                </div>

                <div class="container flex gap-20">

                    <div class="box w-[800px]">
                        <div class="cards flex gap-5">
                            <Card />
                            <CardIncome />
                        </div>

                        <div class="flex md:w-[25rem]">
                            <Chart type="pie" :data="chartData" :options="chartOptions"
                                class="w-full mt-10 ml-10 md:w-[25rem]" />
                        </div>

                    </div>

                    <div class="bg-[#1D1D41] rounded-[20px] py-4 px-7  w-full mr-10 text-white">
                        <div class="mb-4">
                            <h1 class="text-left font-bold text-4xl">Assets</h1>
                        </div>

                        <div v-for="stock in stocks" :key="stock.stockName"
                            class=" bg-[#3b3b81] w-full rounded-lg flex flex-col w-[300px] mb-2">
                            <AssetsCards :stock-option="stock.stockName" :stock-quantity-label="stock.stockQuantity"
                                :stock-price-label="stock.stockPriceCurrent"
                                :stock-percentage-label="stock.stockValuation" />
                        </div>


                    </div>

                </div>
            </div>
        </div>
    </div>
</template>

<style>
body {
    background-color: #151530 !important;
}

.p-chip {
    background-color: #6359E9 !important;
    color: white !important;
    width: 145px !important;
}

.p-chip-label {
    font-size: 16px !important;
    font-weight: 600;
}
</style>
