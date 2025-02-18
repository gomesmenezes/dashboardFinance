<script setup lang="ts">
import { reactive } from 'vue';
import Sidebar from '~/components/organism/Sidebar.vue';
import Chart from 'primevue/chart';
import Card from '~/components/molecules/Card.vue';
import Chip from 'primevue/chip';

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

                <Card />

                <Chart type="pie" :data="chartData" :options="chartOptions" class="w-full mt-10 ml-10 md:w-[25rem]" />
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
