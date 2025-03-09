<script setup>
    const props = defineProps(['slideWidth', 'nextSlide', 'prevSlide', 'sendWhatsapp', 'message']);
    const emit = defineEmits(['update:message'])

    const handleSubmit = () => {
        props.sendWhatsapp()
        props.nextSlide()
    }
</script>

<template>
    <div 
        class="slide flex flex-col gap-4 items-center lg:items-start" 
        :style="{ width: `${props.slideWidth}px` }"
    >
        <label for="message" class="text-xl">Deixe uma mensagem:</label>
        <textarea
            id="message"
            :value="props.message"
            placeholder="Escreva aqui"
            class="w-[100%] lg:w-auto h-[160px] px-5 py-4 border-2 rounded-4xl resize-none"
            @input="emit('update:message', $event.target.value)"
        ></textarea>
        <div class="flex gap-5">
            <button
                type="button"
                @click.prevent="props.prevSlide"
                class="border-2 border-black/30 text-black/30 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
            >
                Voltar
            </button>
            <button
                type="button"
                @click.prevent="handleSubmit"
                class="border-2 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
            >
                Enviar
            </button>
        </div>
    </div>
</template>