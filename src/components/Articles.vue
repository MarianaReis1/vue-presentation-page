<template>
  <section class="max-w-5xl mx-auto my-20 px-3">
    <div
      v-for="article in appData.articles"
      :key="article.id"
      class="item max-w-xl mx-auto my-8 py-5"
      ref="items"
    >
      <p
        class="opacity-100 text-Sky font-bold font-lato text-xs tracking-wider text-left uppercase"
      >
        {{ article.sectionName }}
      </p>
      <h1 class="text-Blue my-5 opacity-100 font-bold text-5xl leading-10">
        {{ article.title }}
      </h1>
      <p class="text-Graphite font-bold text-lg">{{ article.description }}</p>
    </div>
  </section>
</template>

<script setup>
import appData from "@/assets/data";
import { onMounted, ref } from "vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

const items = ref([]);

onMounted(() => {
  // const items = document.querySelectorAll(".item");

  items.value.forEach((item, index) => {
    // if (screenWidth <= 1280) {
      // if (index === 0) {
      //   gsap.set(item, { opacity: 1, y: 0 });
      // } else {
      //   gsap.set(item, { opacity: 0, y: 50 });
      // }
      // gsap.set(item, { autoAlpha: 0 })

      ScrollTrigger.create({
        markers: true,
        trigger: item,
        start: "center center",
        end: "center",
        pin: true,
        pinSpacing: true,
        scrub: true,
        animation: gsap.fromTo(item, { autoAlpha: 0 },{ autoAlpha: 1 })
        // onEnter: () => {
        //   gsap.to(item, { opacity: 1, y: 0 });
        //   if (index > 0) {
        //     gsap.to(items[index - 1], { opacity: 0, y: -50 });
        //   }
        //   if (index < items.length - 1) {
        //     gsap.to(items[index + 1], {
        //       opacity: 1,
        //       y: 0,
        //       ease: "power2.out",
        //       duration: 0.5,
        //     });
        //   }
        // },
        // onLeaveBack: () => {
        //   if (index > 0) {
        //     gsap.to(items[index - 1], {
        //       opacity: 1,
        //       y: 0,
        //       ease: "power2.out",
        //       duration: 0.5,
        //     });
        //   }
        //   if (index < items.length - 1) {
        //     gsap.to(items[index + 1], { opacity: 0, y: 50 });
        //   }
        //   gsap.to(item, { opacity: 0, y: -50 });
        // },
      });
    // } else {
    //   gsap.set(item, { opacity: 1, y: 0 });
    // }
  });
});
</script>
