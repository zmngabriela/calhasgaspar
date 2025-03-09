<script setup>
    import { ref } from 'vue';

    const props = defineProps(['slideWidth', 'prevSlide', 'nextSlide', 'selectedServices', 'metragem']);
    const emit = defineEmits(['update:metragem'])

    const metragemCalhas = ref(30)
    const metragemRufos = ref(30)
    const metragemCanos = ref(30)

    const updateMetragem = (service, value) => {
        if (service === 'Calhas') metragemCalhas.value = Number(value)
        if (service === 'Rufos') metragemRufos.value = Number(value)
        if (service === 'Canos') metragemCanos.value = Number(value)
        emit('update:metragem', {...props.metragem, [service]: Number(value)})
    }
</script>

<template>
    <div 
        v-if="selectedServices.includes('Calhas') || selectedServices.includes('Rufos') || selectedServices.includes('Canos')" 
        class="slide flex flex-col gap-4" 
        :style="{ width: `${slideWidth}px` }"
    >
        <h3 class="text-xl">Qual a metragem?</h3>
        <div class="flex flex-col gap-5">
            <div v-if="selectedServices.includes('Calhas')">
                <div class="flex gap-[100px]">
                    <p class="w-[100px]">Calhas</p>
                    <p>
                        <span>{{ metragemCalhas }}</span> metros
                    </p>
                </div>
                <input
                    type="range"
                    min="0"
                    max="250"
                    :value="metragemCalhas"
                    step="1"
                    @input="(e) => updateMetragem('Calhas', e.target.value)"
                    class="w-[50%] appearance-none mb-5 [&::-webkit-slider-runnable-track]:bg-black [&::-webkit-slider-runnable-track]:h-[2px] [&::-moz-range-track]:bg-black [&::-moz-range-track]:h-[2px]"
                />
            </div>
            <div v-if="selectedServices.includes('Rufos')">
                <div class="flex gap-[100px]">
                    <p class="w-[100px]">Rufos</p>
                    <p>
                        <span>{{ metragemRufos }}</span> metros
                    </p>
                </div>
                <input
                    type="range"
                    min="0"
                    max="250"
                    :value="metragemRufos"
                    step="1"
                    @input="(e) => updateMetragem('Rufos', e.target.value)"
                    class="w-[50%] appearance-none mb-5 [&::-webkit-slider-runnable-track]:bg-black [&::-webkit-slider-runnable-track]:h-[2px] [&::-moz-range-track]:bg-black [&::-moz-range-track]:h-[2px]"
                />
            </div>
            <div v-if="selectedServices.includes('Canos')">
                <div class="flex gap-[100px]">
                    <p class="w-[100px]">Canos</p>
                    <p>
                        <span>{{ metragemCanos }}</span> metros
                    </p>
                </div>
                <input
                    type="range"
                    min="0"
                    max="250"
                    :value="metragemCanos"
                    step="1"
                    @input="(e) => updateMetragem('Canos', e.target.value)"
                    class="w-[50%] appearance-none mb-5 [&::-webkit-slider-runnable-track]:bg-black [&::-webkit-slider-runnable-track]:h-[2px] [&::-moz-range-track]:bg-black [&::-moz-range-track]:h-[2px]"
                />
            </div>
            <p>* Medida aproximada</p>
        </div>
        <div class="flex gap-5">
            <button
                @click.prevent="prevSlide"
                class="border-2 border-black/30 text-black/30 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
            >
                Voltar
            </button>
            <button
                @click.prevent="nextSlide"
                class="border-2 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
            >
                Avançar
            </button>
        </div>
    </div>
</template>