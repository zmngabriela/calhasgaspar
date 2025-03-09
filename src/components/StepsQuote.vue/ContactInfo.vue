<script setup>
    const props = defineProps(['slideWidth', 'prevSlide', 'nextSlide', 'name', 'phone']);
    const emit = defineEmits(['update:name', 'update:phone'])
</script>

<template>
    <div class="slide flex flex-col items-center lg:items-start gap-4" :style="{ width: `${props.slideWidth}px` }">
        <h3 class="text-xl">Informações de contato</h3>
        <div class="flex flex-col gap-2 items-center">
            <div class="flex flex-col items-start gap-1">
                <label for="name" class="text-sm translate-x-3">Nome:</label>
                <input
                    type="text"
                    id="name"
                    :value="props.name"
                    placeholder="Digite seu nome"
                    class="w-[100%] px-4 py-1 border-2 rounded-4xl"
                    @input="emit('update:name', $event.target.value)"
                />
            </div>
            <div class="flex flex-col items-start gap-1">
                <label for="phone" class="text-sm translate-x-3">Telefone:</label>
                <input
                    type="tel"
                    id="phone"
                    :value="props.phone"
                    placeholder="Digite seu telefone"
                    class="w-[100%] px-4 py-1 border-2 rounded-4xl"
                    @input="emit('update:phone', $event.target.value)"
                />
            </div>
        </div>
        <div class="flex justify-center gap-5">
            <button
                type="button"
                @click.prevent="props.prevSlide"
                class="border-2 border-black/30 text-black/30 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
            >
                Voltar
            </button>
            <button
                type="button"
                @click.prevent="props.nextSlide"
                class="border-2 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
            >
                Avançar
            </button>
        </div>
    </div>
</template>