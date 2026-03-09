<script setup>
import { onMounted, ref } from 'vue'

const heroVideo = ref(null)

onMounted(() => {
    if (heroVideo.value) {
        heroVideo.value.play().catch(() => {
        })
    }
})
</script>

<template>
    <section class="relative w-[100vw] h-[100vh] overflow-hidden">
        <video
            ref="heroVideo"
            class="absolute inset-0 h-full w-full object-cover"
            autoplay
            muted
            loop
            playsinline
            webkit-playsinline
            preload="auto"
        >
            <source src="/calha.mp4" type="video/mp4">
            Seu navegador não suporta vídeo em HTML5.
        </video>

        <div class="absolute inset-0 bg-black/35"></div>

        <div class="container relative z-10 h-full items-center">
            <div class="max-w-[100%] sm:max-w-[70%] flex flex-col justify-start md:justify-center mt-[10vh] md:mt-0 items-start gap-8 text-white">
                <div class="flex flex-wrap items-start gap-3">
                    <p class="py-1 px-4 rounded-4xl text-base bg-black/30 text-white">Mais de 35 anos de experiência</p>
                    <p class="py-1 px-4 rounded-4xl text-base bg-black/30 text-white">Gaspar</p>
                    <p class="py-1 px-4 rounded-4xl text-base bg-black/30 text-white">Brusque</p>
                    <p class="py-1 px-4 rounded-4xl text-base bg-black/30 text-white">Navegantes</p>
                </div>
                <h2 class="text-4xl md:text-5xl lg:text-6xl">Calhas e rufos de alumínio com qualidade garantida.</h2>
                <a
                    href="#contact"
                    class="p-3 text-base border-2 border-white text-white hover:scale-[1.01] hover:bg-zinc-600/50 cursor-pointer bg-black/30 transition-colors"
                >
                    Solicite um orçamento
                </a>
            </div>
        </div>
    </section>
</template>
