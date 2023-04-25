<template>
  <header class="text-center justify-center mx-auto px-3">
    <h1
      class="font-Lato font-bold uppercase mb-15  text-3xl tracking-widest py-7 text-Blue "
    >
      GET AHEAD
    </h1>
    <section class="flex flex-wrap items-stretch justify-stretch gap-15 mx-auto">
      <div
        class="basis-[400px] flex-shrink flex-grow flex flex-col items-center rounded p-15 border border-gray-300 cursor-pointer"
        v-for="item in appData.headerSectionOne"
        :key="item.id"
      >
        <img class="mb-10" :src="item.img" :alt="item.img" />
        <p class="text-2xl">{{ item.title }}</p>
        <p class="text-lg">{{ item.description }}</p>
      </div>
    </section>
  </header>
</template>

<script setup>
import appData from "@/assets/data";
</script>
