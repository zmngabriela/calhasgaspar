<script setup>
    const props = defineProps(['slideWidth', 'returnSlide']);
</script>

<template>
    <div 
        class="slide flex flex-col gap-4 items-center lg:items-start" 
        :style="{ width: `${props.slideWidth}px` }"
    >
        <label class="text-xl">Obrigada!</label>
        <p class="sm:max-w-[300px]">Recebemos a sua solicitação de orçamento com sucesso. Em alguns minutos vamos entrar em contato com você.</p>
        <button
            type="button"
            @click.prevent="props.returnSlide"
            class="border-2 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
        >
            Voltar ao início
    </button>
    </div>
</template>