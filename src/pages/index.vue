<script setup lang="ts">
import { ref } from 'vue';
import { Form } from '@primevue/forms';
import { useToast } from 'primevue/usetoast';
import InputText from 'primevue/inputtext';
import Password from 'primevue/password';
import Button from 'primevue/button';
import Toast from 'primevue/toast';
import { FormField } from '@primevue/forms';

const toast = useToast();

const initialValues = ref({
    username: '',
    password: ''
});

const onFormSubmit = (data: any) => {
    toast.add({ severity: 'success', summary: 'Success', detail: 'Form submitted!', life: 3000 });
    console.log('Form Data:', data);
};


const goToDashboard = () => {
    setTimeout(() => {
        window.location.href = '/dashboard';
    }, 1500)
}
</script>

<template>
    <div class="max-w-[900px] mx-auto mt-[60px] rounded-xl flex flex-col justify-center items-center">
        <div class="content flex flex-col justify-center items-center gap-10">
            <div class="text-center text-4xl mb-[25px] font-bold text-amber-200">
                <span class="text-zinc-600">CASH</span>VIP
            </div>

            <div class="card flex justify-center">
                <Toast />

                <Form @click="" @submit="onFormSubmit" :initial-values="initialValues"
                    class="flex flex-col gap-4 w-full sm:w-60">
                    <div class="flex flex-col gap-1">
                        <FormField name="username" v-slot="{ props, error }">
                            <InputText v-bind="props" class="!bg-[#cdcdcd] !text-white !border-none" type="text"
                                placeholder="Nome de Usuário" fluid />
                        </FormField>
                    </div>

                    <div class="flex flex-col gap-1">
                        <FormField name="password" v-slot="{ props, error }">
                            <Password v-bind="props" placeholder="Senha" :feedback="false" toggleMask fluid />
                        </FormField>
                    </div>

                    <Button @click="goToDashboard" type="submit" severity="secondary" label="Entrar" />
                </Form>
            </div>
        </div>
    </div>
</template>

<style scoped>
:deep(.p-password .p-inputtext) {
    background-color: #cdcdcd !important;
    color: white !important;
    border: none !important;
}
</style>
