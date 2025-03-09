<script setup>
    const currentYear = new Date().getFullYear()
</script>

<template>
    <footer class="w-full py-[116px] bg-radial from-detail/20 to-white">
        <div class="container justify-start xs:justify-evenly gap-10 flex-wrap">
            <div class="w-full xs:w-[185px]">
                <p class="font-bold">Gaspar</p>
                <p>R. Barra Velha, 122 - Santa Terezinha, Gaspar - SC, 89114-456, Brazil</p>
            </div>
            <div class="w-full xs:w-[185px]">
                <p class="font-bold">Navegantes</p>
                <p>R. Paraguai, 292 - Gravatá, Navegantes - SC, 88372-680, Brazil</p>
            </div>
            <div class="flex flex-col gap-2">
                <ul class="flex flex-col gap-2">
                    <li>
                        <a href="tel:+5547999797075" class="inline-flex align-center gap-2 bg-transparent">
                            <img
                                class="size-[15px]"
                                src="../assets/icons/telephone.png"
                                alt="Ícone de Telefone"
                            />
                            <p>+55 47 99979 7075</p>
                        </a>
                    </li>
                    <li class="w-full flex justify-start">
                        <a
                            :href="'https://wa.me/+5547999797075?text=' + encodeURIComponent('Oi, tudo bem? Quero solicitar um orçamento.')"
                            target="_blank"
                            class="inline-flex align-center gap-2 bg-transparent"
                        >
                            <img
                                class="size-[20px]"
                                src="../assets/icons/whatsapp.png"
                                alt="Ícone de Whatsapp"
                            />
                            <p>Whatsapp</p>
                        </a>
                    </li>
                    <li class="w-full flex justify-start">
                        <a 
                            href="mailto:calhas-gaspar@gmail.com" 
                            class="inline-flex align-center gap-2 bg-transparent"
                            target="_blank"
                        >
                            <img
                                class="size-[20px]"
                                src="../assets/icons/mail.png"
                                alt="Ícone de E-mail"
                            />
                            <p>E-mail</p>
                        </a>
                    </li>
                </ul>
            </div>
            <div class="flex flex-col gap-2 items-end">
                <h2 class="text-xl uppercase">Calinho Calhas</h2>
                <div class="flex gap-10 items-end">
                    <p class="italic translate-y-[5px]">&copy; {{ currentYear }}</p>
                    <ul class="flex gap-2">
                        <li>
                            <a 
                                href="https://www.facebook.com/calhasgaspar/" 
                                title="Nos acompanhe no Facebook" 
                                target="_blank"
                            >
                                <img src="../assets/icons/facebook.png" alt="Facebook logo" class="size-[25px]"/>
                            </a>
                        </li>
                        <li>
                            <a
                                href="https://maps.app.goo.gl/QfzEHLq1TdfHroG4A"
                                title="Nos acompanhe no Google Maps"
                                target="_blank"
                            >
                                <img src="../assets/icons/maps.png" alt="Youtube logo" class="size-[25px]"/>
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </footer>
</template>
