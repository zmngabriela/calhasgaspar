<script setup>
    import { ref, onMounted, onUnmounted } from 'vue';

    import Services from "./StepsQuote.vue/Services.vue";
    import Range from "./StepsQuote.vue/Range.vue";
    import ContactInfo from "./StepsQuote.vue/ContactInfo.vue";
    import Message from "./StepsQuote.vue/Message.vue";
    import Success from './StepsQuote.vue/Success.vue';

    const steps = ref(['service', 'quantity', 'contactInfo', 'message', 'success']);
    const currentSlide = ref(0);

    const selectedServices = ref([]);
    const metragem = ref({
        calhas: 0,
        rufos: 0,
        canos: 0
    });
    const name = ref('');
    const phone = ref('');
    const message = ref('');

    const slideWidth = ref(0);
    const formRef = ref(null);

    const updateSlideWidth = () => {
        if (formRef.value) {
            slideWidth.value = formRef.value.offsetWidth;
        }
    }

    onMounted(() => {
        updateSlideWidth();
        const resizeObserver = new ResizeObserver(updateSlideWidth);
        resizeObserver.observe(formRef.value)
        onUnmounted(() => {
            resizeObserver.disconnect()
        })
    })

    const nextSlide = () => {
        if (currentSlide.value < steps.value.length) {
            currentSlide.value++;
        }
    };

    const prevSlide = () => {
        currentSlide.value--;
    };

    const returnSlide = () => {
        currentSlide.value = 0;
        selectedServices.value = [];
        metragem.value = {
            calhas: 0,
            rufos: 0,
            canos: 0
        };
        name.value = '';
        phone.value = '';
        message.value = '';
    };

    const sendWhatsapp = () => {
        const myPhone = '+5547999797075';
        const services = selectedServices.value.length ? selectedServices.value.join(', ') : 'Nenhum serviço selecionado';
        const metragemText = Object.entries(metragem.value).map(([service, value]) => {
            if (value > 0) {
                return `${value} metros de ${service}.`
            }
        }).filter(Boolean).join('\n')
        const whatsappMessage = `Orçamento Calinho Calhas\n\nNome: ${name.value}\nTelefone: ${phone.value}\nServiços de interesse: ${services}.\nMetragem:\n${metragemText}\nMensagem: ${message.value}`;
        const url = `https://wa.me/${myPhone}?text=${encodeURIComponent(whatsappMessage)}`;
        window.open(url, "_blank");
    }
</script>

<template>
    <section class="h-[100vh] lg:h-[60vh] grid grid-cols-1 lg:grid-cols-[30%_70%] items-center gap-3" id="contact">
        <div class="h-full flex justify-center lg:justify-end items-end lg:items-center">
            <img
                src="../assets/icons/house-budget.png"
                class="size-[80px] lg:size-[160px] grayscale hover:grayscale-0"
                alt=""
            />
        </div>
        <form 
            ref="formRef"
            class="w-[80%] mx-auto h-full overflow-hidden"
            @submit.prevent="sendWhatsapp"
        >
            <div 
                class="h-full slider inline-flex flex-nowrap items-top lg:items-center text-center lg:text-start transition-transform duration-500"
                :style="{ transform: `translateX(-${currentSlide * slideWidth}px)` }"
            >
                <!-- STEP 0 -->
                <div class="slide flex flex-col gap-1 mx-auto items-center lg:items-start" :style="{ width: `${slideWidth}px` }">
                    <h3 class="text-xl">
                        Calhas, rufos e canos de alumínio, correntes e demais opções.
                    </h3>
                    <p>
                        Está precisando de um de nossos serviços e quer um atendimento personalizado?
                    </p>
                    <button
                        @click.prevent="nextSlide"
                        class="border-2 rounded-4xl py-2 px-3 mt-3 hover:bg-radial from-white to-detail/20 cursor-pointer"
                    >
                        Solicite um orçamento
                    </button>
                </div>
                <!-- STEP 1 -->
                <Services 
                    :slideWidth="slideWidth"
                    :prevSlide="prevSlide"
                    :nextSlide="nextSlide"
                    v-model:selectedServices="selectedServices"
                />
                <!-- STEP 2 -->
                <Range 
                    :slideWidth="slideWidth"
                    :prevSlide="prevSlide"
                    :nextSlide="nextSlide"
                    :selectedServices="selectedServices"
                    v-model:metragem="metragem"
                />
                <!-- STEP 3 -->
                <ContactInfo 
                    :slideWidth="slideWidth"
                    :prevSlide="prevSlide"
                    :nextSlide="nextSlide"
                    v-model:name="name"
                    v-model:phone="phone"
                />
                <!-- STEP 4 -->
                <Message 
                    :slideWidth="slideWidth"
                    :prevSlide="prevSlide"
                    :nextSlide="nextSlide"
                    v-model:message="message"
                    :sendWhatsapp="sendWhatsapp"
                />
                <Success 
                    :slideWidth="slideWidth"
                    :returnSlide="returnSlide"
                />
            </div>
        </form>
    </section>
</template>