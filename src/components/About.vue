<script>
    document.addEventListener('DOMContentLoaded', () => {
        const scrollers = document.querySelectorAll('.scroller');

        if (!window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
            addAnimation();
        }

        function addAnimation() {
            scrollers.forEach(scroller => {
                scroller.setAttribute('data-animated', true);

                const scrollerInner = scroller.querySelector('.scroller__inner')
                const scrollerContent = Array.from(scrollerInner.children)

                for (let i = 0; i < 2; i++) {
                    scrollerContent.forEach(item => {
                        const duplicatedItem = item.cloneNode(true)
                        duplicatedItem.setAttribute('aria-hidden', true)
                        scrollerInner.appendChild(duplicatedItem)
                    })
                }
            })
        }
    })
</script>

<template>
    <section 
        class="h-[160vh] md:h-[100vh] lg:h-[80vh] flex flex-col text-center justify-center items-center gap-2"
        id="services"
    >
        <h2 class="w-[80%] text-xl">
            Cuidamos do trabalho pesado, seja para sua casa, empresa ou estabelecimento, <br> para que você tenha sempre <span class="italic">segurança e tranquilidade.</span>
        </h2>
        <div class="relative scroller w-full overflow-hidden">
            <ul
                class="flex justify-center align-center gap-[.5rem] my-16 scroller__inner"
            >
                <li class="w-[240px] overflow-hidden">
                    <img src="../assets/images/calha.jpg" alt="" class="w-full grayscale hover:scale-101" />
                </li>
                <li class="w-[240px] overflow-hidden">
                    <img src="../assets/images/casa-calha.jpg" alt="" class="w-full grayscale hover:scale-101" />
                </li>
                <li class="w-[240px] overflow-hidden">
                    <img src="../assets/images/rufo.jpg" alt="" class="w-full grayscale hover:scale-101" />
                </li>
                <li class="w-[240px] overflow-hidden">
                    <img src="../assets/images/casa2.jpeg" alt="" class="w-full grayscale hover:scale-101" />
                </li>
                <li class="w-[240px] overflow-hidden">
                    <img src="../assets/images/rufo3.jpg" alt="" class="w-full grayscale hover:scale-101" />
                </li>
                <li class="w-[240px] overflow-hidden">
                    <img src="../assets/images/casa.jpg" alt="" class="w-full grayscale hover:scale-101" />
                </li>
            </ul>
        </div>
        <div class="w-[80%] grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 text-start">
            <div class="flex flex-col gap-2">
                <img src="../assets/icons/calha.png" alt="" class="size-[35px]">
                <p class="font-extralight"><strong>Calhas de alumínio</strong> de qualidade, para diferenetes tipos telhados e construções.</p>
            </div>
            <div class="flex flex-col gap-2">
                <img src="../assets/icons/rufo.png" alt="" class="size-[35px]">
                <p class="font-extralight"><strong>Rufos de alumínio</strong> que vedam e protegem contra a infiltração de água.</p>
            </div>
            <div class="flex flex-col gap-2">
                <img src="../assets/icons/cano.png" alt="" class="size-[35px]">
                <p class="font-extralight"><strong>Canos de alumínio ou pvc</strong>, desembocando a água e mantendo a estética.</p>
            </div>
            <div class="flex flex-col gap-2">
                <img src="../assets/icons/corrente.png" alt="" class="size-[35px]">
                <p class="font-extralight"><strong>Correntes e demais acessórios</strong> mediante solicitação, pensados pra sua necessidade.</p>
            </div>
        </div>
    </section>
</template>


<style scoped>
    .scroller[data-animated='true'] {
        overflow: hidden;
    }

    .scroller[data-animated='true'] .scroller__inner {
        width: max-content;
        flex-wrap: nowrap;
        animation: scroll 50s linear infinite;
    }

    @media (max-width: 768px) {
        .scroller[data-animated='true'] .scroller__inner {
            animation: scroll 80s linear infinite;
        }
    }

    .scroller__inner li {
        flex: 0 0 auto;
    }

    @keyframes scroll {
        to {
            transform: translateX(calc(-100% + 3rem));
        }
    }
</style>