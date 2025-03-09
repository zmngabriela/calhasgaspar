<script setup>
    import { onMounted, onUnmounted, ref } from 'vue';

    const isScrolled = ref(false);

    const handleScroll = () => {
        isScrolled.value = window.scrollY > 200
    }

    const scrollToTop = () => {
        window.scrollTo({
            top: 0,
            behavior: 'smooth'
        })
    }

    onMounted(() => {
        window.addEventListener('scroll', handleScroll)
    })

    onUnmounted(() => {
        window.removeEventListener('scroll', handleScroll)
    })
</script>

<template>
    <nav
        class="sticky top-2 z-1 w-[300px] flex justify-center mx-auto rounded-4xl bg-transparent backdrop-blur py-5 transition-transform duration-[1000ms] ease-in-out"
        :class="{ 'translate-y-0': isScrolled, 'translate-y-[-100px]': !isScrolled }"
    >
        <ul class="inline-flex gap-10 list-none uppercase items-center">
            <li>
                <button 
                    type="button" 
                    class="bg-transparent flex cursor-pointer"
                    @click="scrollToTop"
                    >
                    <img src="../assets/icons/top.png" alt="" class="size-[16px]">
                </button>
            </li>
            <li class="hover:scale-[1.01]">
                <a href="#services" class="text-sm hover:scale-[1.01] bg-transparent">
                    Serviços
                </a>
            </li>
            <li class="hover:scale-[1.01]">
                <a href="#contact" class="text-sm hover:scale-[1.01] bg-transparent">
                    Fale conosco
                </a>
            </li>
        </ul>
    </nav>
</template>
