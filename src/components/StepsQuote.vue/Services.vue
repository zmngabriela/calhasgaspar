<script setup>
    const props = defineProps(['slideWidth', 'prevSlide', 'nextSlide', 'selectedServices']);
    const emit = defineEmits(['update:selectedServices'])

    const services = ['Calhas', 'Rufos', 'Canos', 'Outros'];

    const toggleService = (service) => {
        let updatedServices = [...props.selectedServices]
        if (updatedServices.includes(service)) {
            updatedServices = updatedServices.filter(item => item !== service)
        } else {
            updatedServices.push(service)
        }
        emit('update:selectedServices', updatedServices)
    }
</script>

<template>
    <div class="slide flex flex-col items-center lg:items-start" :style="{ width: `${props.slideWidth}px` }">
        <h3 class="text-xl">Qual serviço te interessa?</h3>
        <div class="grid grid-cols-2 md:grid-cols-4 justify-center gap-5 my-5">
            <div class="flex gap-2">
                <input
                    type="checkbox"
                    name="products"
                    :id="services[0]"
                    class="appearance-auto"
                    :checked="props.selectedServices.includes(services[0])"
                    @change="toggleService(services[0])"
                />
                <div class="flex flex-col items-center gap-2">
                    <img src="../../assets/icons/calha.png" class="size-[35px]" alt="" />
                    <label for="calhas">Calhas</label>
                </div>
            </div>
            <div class="flex gap-2">
                <input
                    type="checkbox"
                    name="products"
                    :id="services[1]"
                    class="appearance-auto"
                    :checked="props.selectedServices.includes(services[1])"
                    @change="toggleService(services[1])"
                />
                <div class="flex flex-col items-center gap-2">
                    <img src="../../assets/icons/rufo.png" class="size-[35px]" alt="" />
                    <label for="rufo">Rufos</label>
                </div>
            </div>
            <div class="flex gap-2">
                <input
                    type="checkbox"
                    name="products"
                    :id="services[2]"
                    class="appearance-auto"
                    :checked="props.selectedServices.includes(services[2])"
                    @change="toggleService(services[2])"
                />
                <div class="flex flex-col items-center gap-2">
                    <img src="../../assets/icons/cano.png" class="size-[35px]" alt="" />
                    <label for="canos">Canos</label>
                </div>
            </div>
            <div class="flex gap-2">
                <input
                    type="checkbox"
                    name="products"
                    :id="services[3]"
                    class="appearance-auto"
                    :checked="props.selectedServices.includes(services[3])"
                    @change="toggleService(services[3])"
                />
                <div class="flex flex-col items-center gap-2">
                    <img src="../../assets/icons/corrente.png" class="size-[35px]" alt="" />
                    <p>Outros</p>
                </div>
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