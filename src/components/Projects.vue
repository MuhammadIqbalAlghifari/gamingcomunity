<template>
    <section class="lg:p-10 md:p-14 p-8 max-w-screen-2xl mx-auto w-full">
        <div class="flex flex-col w-full gap-y-5 justify-center items-center">
            <div ref="tittle" class="flex flex-col w-full md:gap-y-3 gap-y-1.5 justify-center items-center">
                <h1 class="text-white lg:text-3xl md:text-xl text-base mx-auto tracking-wide text-center leading-loose max-w-2xl font-semibold">Our Recent Projects</h1>
                <h1 class="text-white md:text-sm text-xs mx-auto tracking-wide text-center leading-loose max-w-lg font-light">Lorem Ipsum is simply dummy text of the printing and typersetting industry.</h1>
            </div>
            <div ref="imageOne" class="flex flex-wrap-reverse w-auto xl:justify-between justify-center gap-10 items-center">
                <img src="/gamehall-aesthetic.png" class="w-full md:w-auto h-full object-cover rounded-lg"/>
                <img src="/gaming-on-pc.png" class="w-full md:w-auto h-full object-cover rounded-lg"/>
                <img src="/buld-pc.png" class="w-full md:w-auto h-full object-cover rounded-lg"/>
            </div>
            <div ref="imageTwo" class="flex flex-wrap w-auto xl:justify-between justify-center gap-10 items-center">
                <img src="/play-projects.png" class="w-full md:w-auto h-full object-cover rounded-lg"/>
                <img src="/gamehall-project.png" class="w-full md:w-auto h-full object-cover rounded-lg"/>
                <img src="/gamehall-night.png" class="w-full md:w-auto h-full object-cover rounded-lg"/>
            </div>
            <button class="bg-[#1c1c1c] text-white rounded-md px-4 py-2 xl:text-base md:text-sm text-xs my-10 uppercase tracking-wide">see all</button>
        </div>
    </section>
</template>

<script setup>

import { ref, onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);
const tittle = ref(null)
const imageOne = ref(null)
const imageTwo = ref(null)

const animateOnScroll = (element, { opacity, x, y }) => {
  gsap.fromTo(element, { opacity, x, y }, {
      opacity: 1,
      x: 0,
      y: 0,
      duration: 1,
      stagger: 0.3,
      delay: 0.2,
      ease: 'power3.out',
      scrollTrigger: {
        trigger: element,
        start: 'top bottom',
        end: 'center center',
      },
    }
  );
};

onMounted(() => {
  tittle.value.childNodes.forEach(card => {
    animateOnScroll(card, { opacity: 0, y: 50 });
  });
  imageOne.value.childNodes.forEach(card => {
    animateOnScroll(card, { opacity: 0, y: 50 });
  });
  imageTwo.value.childNodes.forEach(card => {
    animateOnScroll(card, { opacity: 0, y: 50 });
  });
});

</script>