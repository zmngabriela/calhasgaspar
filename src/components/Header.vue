<template>
  <header class="absolute top-0 left-0 z-40 w-full py-7 text-white">
    <div class="flex items-center justify-between container">
      <h1 class="text-xl uppercase">Calinho Calhas</h1>
      <nav class="hidden sm:flex">
        <ul class="inline-flex gap-10 list-none uppercase">
          <li class="hover:scale-[1.01]">
            <a href="#services" class="text-sm hover:scale-[1.01]">Serviços</a>
          </li>
          <li class="hover:scale-[1.01]">
            <a href="#contact" class="text-sm hover:scale-[1.01]">Fale conosco</a>
          </li>
        </ul>
      </nav>
      <div class="inline-flex items-center justify-center gap-5">
        <div>
          <a
            href="tel:+5547999797075"
            class="flex items-center justify-center gap-2 text-sm cursor-pointer"
          >
            <p class="hidden md:block hover:scale-[1.01] cursor-pointer">+55 47 99979 7075</p>
          </a>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped>
header,
header * {
  background-color: transparent !important;
}
</style>
