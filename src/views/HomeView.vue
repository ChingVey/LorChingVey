<script setup lang="ts">
import { useDark, useToggle } from '@vueuse/core'
import { Ref, ref } from 'vue';
import { onClickOutside } from '@vueuse/core'

const isDark = useDark()
const toggleDark = useToggle(isDark)

const ModalOpen1 = ref(false)
const ModalOpen = ref(false)
const isModalOpen = ref(false)

const modal = ref(null)
onClickOutside(modal, () => (isModalOpen.value = false))
onClickOutside(modal, () => (ModalOpen.value = false))
onClickOutside(modal, () => (ModalOpen1.value = false))

</script>

<template>
  <main class="container max-w-full min-h-screen bg-black flex justify-center items-center lg:px-4 lg:pt-4">
    <div class="lg:w-[1500px] lg:h-[800px]">
      <div class="lg:block hidden bg-neutral-900 rounded-[45px] mb-6">
        <div class="flex justify-between items-center p-6">
          <h5 class="lg:text-xl lg:text-left lg:font-bold lg:text-white">Personal Portfolio</h5>
          <ul>
            <li class="text-white">
              <a class="p-4 hover:underline decoration-violet-800 underline-offset-4" href="#">Home</a>
              <a class="p-4 hover:underline decoration-violet-800 underline-offset-4" href="#2nd">About</a>
              <a class="p-4 hover:underline decoration-violet-800 underline-offset-4" href="#3rd">Skills</a>
              <a class="p-4 hover:underline decoration-violet-800 underline-offset-4" href="#4th">Contact</a>
            </li>
          </ul>
        </div>
      </div>


      <div
        class=" lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid-row-3 lg:grid lg:gap-2 lg:p-4 hidden">
        <div class="col-span-4 flex justify-around items-center p-8">
          <a class="transition duration-200 delay-110 hover:scale-95">
          <img class="xl:w-[560px] lg:w-[450px] object-cover bg-transparent" src="/Profile.png">
        </a>
          <div class="inlineblock">
            <p class="font-bold text-lg flex mb-4">Available for Work
              <span class="relative flex h-4 w-4 ml-2">
                <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-100"></span>
                <span class="relative inline-flex rounded-full h-4 w-4 bg-green-500"></span>
              </span>
            </p>
            <h5 class=" xl:text-6xl lg:text-5xl font-extrabold mb-8">DIGITAL PO AND BA</h5>
            <h1 class="xl:text-5xl lg:text-4xl font-bold"> Lor ChingVey</h1>
            <p class="font-bold text-lg pt-4">- Introduction</p>
            <p class="text-3xl font-semibold pt-4"> Digital Product Owner and Business Analyst<span class="block">based in Phnom Penh.</span>
            </p>
            <p class="text-md pt-4"><span class="text-4xl font-serif">"</span>Be kind at the end of the day only memories remaining<span class="text-4xl font-serif">"</span> </p>
            <div class="flex pt-8">
              <a href="#2nd"
                class="p-4 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100 mr-3">Get to
                Know me</a>
              <a @click="ModalOpen1 = true"
                class="cursor-pointer p-4 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100 mr-3">Preview CV</a>
                <a class="cursor-pointer p-4 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100" href="/LorChingVeyCV.pdf">Download CV</a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <teleport to="#modal">
      <transition name="modal">
        <div v-if="ModalOpen1" class="fixed left-0 top-0 w-[100vw] h-[100vh] object-cover flex bg-black/50 justify-center items-center">
          <div class="relative p-12 rounded-2xl" ref="modal">
            <img class="w-full h-screen cursor-pointer" src="/ImageCV.jpg">
          </div>
        </div>
      </transition>
    </teleport>

    <div class=" w-[1000px] h-[1000px] bg-neutral-900 text-white inlineblock lg:hidden">
      <div class="flex items-center justify-center text-center pt-6">
        <h5 class="text-7xl font-extrabold">DIGITAL</h5>
      </div>
      <div class="flex items-center justify-center text-center">
        <h5 class="text-sm font-extrabold">PRODUCT OWNER AND BUSINESS ANALYST</h5>
      </div>

      <div class="inlineblock pt-8">
        <div class="flex justify-center items-center">
          <img class="w-72 sm:w-80 md:w-96 object-cover bg-transparent" src="/Profile.png">
        </div>
        <p class="font-sans text-lg flex mt-4 text-center justify-center">Available for Work
              <span class="relative flex h-4 w-4 ml-2">
                <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-100"></span>
                <span class="relative inline-flex rounded-full h-4 w-4 bg-green-500"></span>
              </span>
            </p>
        <h1 class="text-5xl sm:text-4xl md:text-5xl font-bold text-center pt-7"> Lor ChingVey</h1>
        <p class="font-bold text-xl pt-2 text-center">- Introduction</p>
        <p class="text-md sm:text-xl md:text-2xl font-semibold pt-7 text-center">Digital Product Owner and Business Analyst
        </p>
        <p class="text-md sm:text-xl md:text-2xl font-semibold text-center">Based in Phnom Penh.</p>
        <p class="text-md text-center"><span class="text-4xl font-serif">"</span>Be kind at the end of the day only memories remaining<span class="text-4xl font-serif">"</span> </p>
        <div class="flex pt-8 justify-center">
          <a href="#2nd" class="p-3 border border-1 transition duration-100 delay-100 mr-6">Get to Know me</a>
          <a @click="ModalOpen = true"
            class="cursor-pointer py-3 px-6 border border-1 transition duration-100 delay-100">Preview CV</a>
        </div>
        <div class="text-center pt-6">
        <a class="py-3 px-24 border border-1 transition duration-100 delay-100" href="/LorChingVeyCV.pdf">Download CV</a>
      </div>
      </div>
    </div>
  </main>

  <teleport to="#modal">
    <transition name="modal">
      <div v-if="ModalOpen" class="fixed left-0 top-0 w-[100vw] h-[100vh] flex bg-black/50 justify-center items-center">
        <div class="relative p-12 rounded-2xl shadow-black/100" ref="modal">
          <img class="w-96" src="/ImageCV.jpg">
        </div>
      </div>
    </transition>
  </teleport>



  <main id="2nd" class="container max-w-full min-h-screen bg-black flex justify-center items-center lg:px-4">

    <div
      class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid lg:grid-rows-3 lg:gap-4 lg:p-4 hidden">
      <div class=" col-span-3">
        <div class="flex justify-between items-center">
          <h5 class="text-6xl text-left font-bold p-2">Hi, I'm Vey.</h5>
        </div>
        <div class="p-2">
          <p class="text-lg font-sans">I am a college student and a full time digital product owner.</p>
          <div class="flex items-center">
          <p class="text-2xl font-mono">I do project management, code and Design.<span class="text-6xl">👋🏻</span></p>
        </div>
        </div>
      </div>
      <div
        class=" bg-white text-left row-span-3 rounded-r-[40px] text-black p-4">
        <h1 class="text-4xl font-bold pt-8">EXPERIENCES</h1>

    <div class="flex justify-center">
      <a class="transition duration-200 delay-110 hover:scale-95">
      <img class="pt-8" src="/Skills.png">
    </a>
    </div>
      </div>
      <div class=" bg-white text-black col-span-1">
        <li class="list-none text-xl font-bold p-4">Personal Infomation</li>
        <div class="items-center p-4">
          <li class="text-sm list-none font-semibold">Gender: Male</li>
          <li class="text-sm list-none font-semibold">Nationality: Cambodian</li>
          <li class="text-sm list-none font-semibold">DOB: XX XX XXXX</li>
          <li class="text-sm list-none font-semibold">Place of Birth: Unknown</li>
        </div>
      </div>
      <div @click="isModalOpen = true"
        class=" bg-white col-span-2 text-black p-4 cursor-pointer transition duration-200 delay-175 hover:scale-105">
        <div class="flex justify-between">
          <li class="list-none text-xl font-bold">Personal Summary</li>
          <svg class=" bg-black rounded-full -rotate-45 w-8 h-8 lg:w-16 lg:h-16  md:w-12 md:h-12"
            xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
            style="fill: rgba(255, 255, 255, 1)">
            <path d="m11.293 17.293 1.414 1.414L19.414 12l-6.707-6.707-1.414 1.414L15.586 11H6v2h9.586z"></path>
          </svg>
        </div>
        <p class="text-sm pt-4">A Highly creative and multitalented project management and business analyst and highly skilled in socializing with stakeholder.
          <span class=" text-right font-bold">see more</span>
        </p>
      </div>

      <teleport to="#modal">
        <transition name="modal">
          <div v-if="isModalOpen"
            class="fixed left-0 top-0 w-[100vw] h-[100vh] flex bg-black/50 justify-center items-center">
            <div class="relative bg-white p-12 rounded-2xl shadow-black/100" ref="modal">
              <a href="">A Highly creative and multitalented project management and business analyst and highly skilled in socializing with stakeholder.
                <span class="block">I Passionated in collecting user requirementand translate it into user story and business flow.</span></a>
            </div>
          </div>
        </transition>
      </teleport>

      <div class=" bg-white text-center rounded-bl-[40px] col-span-2 text-black p-4">
        <li class="list-none text-xl font-bold">Project Management and Analyst Tools</li>
        <div class="flex items-center justify-center p-2 pt-7">
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://www.figma.com/">
              <img class="w-[40px]" src="/figma-svgrepo-com.svg">
              <p class="text-white">Figma</p>
            </a>
          </div>
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://xmind.app/">
              <img class="w-[40px] mr-2" src="/Xmind.svg">
              <p class="text-white">Xmind</p>
            </a>
          </div>
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://www.odoo.com/">
              <img class="w-[40px] mr-2" src="/Odoo.svg">
              <p class="text-white">Odoo</p>
            </a>
          </div>
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://en.wikipedia.org/wiki/JavaScript">
              <img class="w-[40px] mr-1" src="/js-svgrepo-com.svg">
              <p class="text-white">Javascript</p>
            </a>
          </div>
        </div>
        <div class="flex items-center justify-center p-2">
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://www.adobe.com/">
              <img class="w-[40px]" src="/adobe-illustrator-svgrepo-com.svg">
              <p class="text-white">Illutrator</p>
            </a>
          </div>
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://tailwindcss.com/">
              <img class="w-[40px]" src="/tailwindcss-icon-svgrepo-com.svg">
              <p class="text-white">Tailwindcss</p>
            </a>
          </div>
          <div
            class="bg-neutral-900 hover:bg-neutral-700 border-[2px] border-violet-800 flex items-center p-2 rounded-lg mx-2">
            <a class="flex items-center" href="https://vuejs.org/">
              <img class="w-[40px]" src="/vue-svgrepo-com.svg">
              <p class="text-white">Vue.js</p>
            </a>
          </div>
        </div>
      </div>
      <div class=" bg-white text-black col-span-1">
        <li class="list-none font-bold p-4 text-xl">Languages</li>
        <div class="items-center p-4">
          <li class="text-xs sm:text-sm font-semibold">Khmer (Native)</li>
          <li class="text-xs sm:text-sm font-semibold">English (Intermediate)</li>
        </div>
      </div>
    </div>


    <div class=" w-[1000px] h-[1000px] bg-neutral-900 text-white grid grid-cols-4 grid-rows-5 gap-4 p-4 lg:hidden">
      <div class=" rounded-[15px] col-span-4">
        <div class="text-center">
          <h5 class="text-4xl font-bold text-white">Hi, Im Vey.</h5>
          <p class="text-sm font-sans pt-2">I am a college student and a full time product owner</p>
          <p class="text-lg font-mono">I do project management, code and Design.<span class="text-3xl">👋🏻</span></p>
        </div>
        <div class="flex justify-center items-start pt-4">

         <!--<label class="relative inline-flex items-center cursor-pointer">
            <input type="checkbox" value="" class="sr-only peer">
            <div @click="toggleDark()" class="w-14 h-7 bg-gray-400  rounded-full peer peer-checked:after:translate-x-full after:content-[''] after:absolute after:top-0.5 after:left-[4px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-6 after:w-6 after:transition-all peer-checked:bg-sky-400 after:delay-125 after:duration-175">
            </div>
            <span class="ml-3 text-sm font-medium text-gray-300">Switch Mode</span>
          </label> -->

        </div>
      </div>
      <div
        class="bg-white rounded-[15px] text-center row-span-2 col-span-2 text-black p-4">
      <h1 class="text-2xl font-bold">EXPERINCES</h1>
    <div class="flex justify-center">
      <img class="w-32 sm:w-40 md:w-48 pt-4" src="/Skills.png">
    </div>
      </div>
      <div class="bg-white rounded-[15px] text-left col-span-2 text-black">
        <li class="list-none text-sm sm:text-xl font-bold p-4">Personal Infomation</li>
        <div class="items-center pl-4">
          <li class="text-xs sm:text-sm list-none font-semibold">Gender: Male</li>
          <li class="text-xs sm:text-sm list-none font-semibold">Nationality: Cambodian</li>
          <li class="text-xs sm:text-sm list-none font-semibold">DOB: XX XX XXXX</li>
          <li class="text-xs sm:text-sm list-none font-semibold">Place of Birth: Unknown</li>
        </div>
      </div>
      <div class="bg-white rounded-[15px] text-left col-span-2 text-black">
        <li class="list-none text-sm font-bold p-4 sm:text-xl">Languages</li>
        <li class="text-xs sm:text-sm font-semibold pl-4">Khmer (Native)</li>
        <li class="text-xs sm:text-sm font-semibold pl-4">English Intermediate</li>
      </div>

      <div @click="isModalOpen = true"
        class="cursor-pointer bg-white rounded-[15px] text-center col-span-4 text-black p-4 transition duration-200 delay-175 hover:scale-105">
        <div class=" flex justify-between items-center">
          <li class="list-none text-lg sm:text-xl md:text-2xl font-bold">Personal Summary</li>
          <svg class=" bg-black rounded-full -rotate-45 w-8 h-8 lg:w-16 lg:h-16  md:w-12 md:h-12"
            xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
            style="fill: rgba(255, 255, 255, 1)">
            <path d="m11.293 17.293 1.414 1.414L19.414 12l-6.707-6.707-1.414 1.414L15.586 11H6v2h9.586z"></path>
          </svg>
        </div>
        <p class="text-xs sm:text-md pt-4">A Highly creative and multitalented project management and business analyst and highly skilled in socializing with stakeholder.
<span class="block font-bold">see more</span></p>
      </div>

      <teleport to="#modal">
        <transition name="modal">
          <div v-if="isModalOpen"
            class="fixed left-0 top-0 w-[100vw] h-[100vh] flex bg-black/50 justify-center items-center overflow-hidden">
            <div class="relative bg-white p-12 rounded-2xl shadow-black/100" ref="modal">
              A Highly creative and multitalented project management and business analyst and highly skilled in socializing with stakeholder.<span class="block">I Passionated in collecting user requirementand translate it into user story and business flow.</span>

            </div>
          </div>
        </transition>
      </teleport>

      <div
        class="text-center col-span-4 text-white dark:border-black dark:text-white">
        <li class="list-none text-xl font-bold pt-3">Programming and Design Tools</li>
        <div class="flex items-center justify-center pt-4">
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://www.figma.com/">
              <img class="w-6" src="/figma-svgrepo-com.svg">
              <p class="text-white">Figma</p>
            </a>
          </div>
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://en.wikipedia.org/wiki/HTML"><img class="w-6"
                src="/Xmind.svg">
              <p class="text-white">Xmind</p>
            </a>
          </div>
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://en.wikipedia.org/wiki/CSS">
              <img class="w-6" src="/Odoo.svg">
              <p class="text-white">Odoo</p>
            </a>
          </div>
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://en.wikipedia.org/wiki/JavaScript">
              <img class="w-6" src="/js-svgrepo-com.svg">
              <p class="text-white">Javascript</p>
            </a>
          </div>
        </div>
        <div class="flex items-center justify-center p-1.5">
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center  p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://www.adobe.com/">
              <img class="w-6" src="/adobe-illustrator-svgrepo-com.svg">
              <p class="text-white">Illutrator</p>
            </a>
          </div>
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://tailwindcss.com/">
              <img class="w-6" src="/tailwindcss-icon-svgrepo-com.svg">
              <p class="text-white">Tailwindcss</p>
            </a>
          </div>
          <div class="bg-neutral-900 border-[1px] border-violet-800 flex items-center p-1.5 rounded-md sm:p-3 mx-1">
            <a class="flex items-center" href="https://vuejs.org/">
              <img class="w-6" src="/vue-svgrepo-com.svg">
              <p class="text-white">Vue.js</p>
            </a>
          </div>
        </div>
      </div>
    </div>

  </main>

<!-- SKILLS and PROJECTS SECTION -->

<!-- Mind Up -->
<main id="3rd" class="container max-w-full lg:min-h-screen min-h-full lg:py-12 lg:px-4 bg-black flex justify-center items-center">

<div class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid lg:grid-rows-3 lg:gap-4 lg:p-4 hidden">
  <div class="rounded-[30px] col-span-1 row-span-3">
      <h5 class="lg:text-5xl xl:text-7xl text-left font-bold p-2">Mind Map</h5>
      <h1 class="text-md text-left font-san p-2 pb-10">A mind map is a diagram used to visually organize information into a hierarchy, showing relationships among pieces of the whole. It is often created around a single concept, drawn as an image in the center of a blank page, to which associated representations of ideas such as images, words and parts of words are added.</h1>
      <a class="cursor-pointer p-4 ml-2 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100" href="#buss">Keep Exploring</a>
  </div>
  <div class="rounded-[30px] col-span-3 row-span-3">
    <img class="lg:rounded-[30px] lg:w-[1500px] lg:h-[630px] p-2 items-center" src="/MobileApplicationUI.png" alt="">
    <h1 class="text-sm text-center font-san p-2">This is the mindmap that I've discussed with development team in order to build a SSO-Based System for the company project.</h1>
  </div>
</div>

<div class="w-[1000px] h-[600px] bg-neutral-900 text-white justify-center items-center flex lg:hidden">
  <div class="rounded-[30px] p-4">
    <div class="inline-block justify-between items-center">
      <h5 class="text-4xl text-center font-bold p-2">Mind Map</h5>
      <h1 class="text-sm text-center font-san p-2">A mind map is a diagram used to visually organize information into a hierarchy, showing relationships among pieces of the whole. It is often created around a single concept, drawn as an image in the center of a blank page, to which associated representations of ideas such as images, words and parts of words are added.</h1>
    <img class="rounded-[30px] h-[350px] sm:w-[1000px] p-2 items-center bg-violet-800 mt-4" src="/MobileApplicationUI.png" alt="">
    </div>
  </div>
</div>

</main>

<!-- Mind Up -->

<!-- Business Flow -->

<main id="buss" class="container max-w-full lg:min-h-screen min-h-full lg:py-12 lg:px-4 bg-black flex justify-center items-center">

<div class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid lg:grid-rows-3 lg:gap-4 lg:p-4 hidden">
  <div class="rounded-[30px] col-span-1 row-span-3">
      <h5 class="lg:text-5xl xl:text-7xl text-left font-bold p-2">Business Flow</h5>
      <h1 class="text-md text-left font-san p-2 pb-10">A business process, business method, or business function is a collection of related, structured activities or tasks performed by people or equipment in which a specific sequence produces a service or product for a particular customer or customers.</h1>
      <a class="cursor-pointer p-4 ml-2 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100" href="#user">Keep Exploring</a>
  </div>
  <div class="rounded-[30px] col-span-3 row-span-3">
    <img class="lg:rounded-[30px] lg:w-[1500px] lg:h-[630px] p-2 items-center" src="/Businessflow.png" alt="">
    <h1 class="text-sm text-center font-san p-2">This is the Business Flow Process which I've drew for the development stakeholder, in order to offer them easier imagine on the requirement.</h1>
  </div>
</div>

<div class=" w-[1000px] h-[600px] bg-neutral-900 text-white justify-center items-center flex lg:hidden">
  <div class=" rounded-[30px] p-4">
    <div class="inline-block justify-center items-center">
      <h5 class="text-4xl text-center font-bold p-2">Business Flow</h5>
      <h1 class="text-sm text-center font-san p-2">A business process, business method, or business function is a collection of related, structured activities or tasks performed by people or equipment in which a specific sequence produces a service or product for a particular customer or customers.</h1>
    <img class="rounded-[30px] h-[350px] sm:w-[1000px] p-2 items-center bg-violet-800 mt-4" src="/Businessflow.png" alt="">
    </div>
  </div>
</div>

</main>

<!-- Business Flow -->

<!-- User Story -->

<main id="user" class="container max-w-full lg:min-h-screen min-h-full lg:py-12 lg:px-4 bg-black flex justify-center items-center">

<div class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid lg:grid-rows-3 lg:gap-4 lg:p-4 hidden">
  <div class="rounded-[30px] col-span-1 row-span-3">
      <h5 class="lg:text-5xl xl:text-7xl text-left font-bold p-2">User Story</h5>
      <h1 class="text-md text-left font-san p-2 pb-10">In software development and product management, a user story is an informal, natural language description of features of a software system. They are written from the perspective of an end user or user of a system, and may be recorded on index cards, Post-it notes, or digitally in specific management software.</h1>
      <a class="cursor-pointer p-4 ml-2 border border-1 hover:bg-white hover:text-black transition duration-100 delay-100" href="#4th">Keep Exploring</a>
  </div>
  <div class="rounded-[30px] col-span-3 row-span-3">
    <img class="lg:rounded-[30px] lg:w-[1500px] lg:h-[630px] p-2 items-center" src="/Userstory.png" alt="">
    <h1 class="text-sm text-center font-san p-2">This is a User Story and was built up for the purpose of describe the stakeholder requirment vision and detail every inches of information.</h1>
  </div>
</div>

<div class=" w-[1000px] h-[600px] bg-neutral-900 text-white items-center justify-center flex lg:hidden">
  <div class=" rounded-[30px] p-4">
    <div class="inline-block justify-between items-center">
      <h5 class="text-4xl text-center font-bold p-2">User Story</h5>
      <h1 class="text-sm text-center font-san p-2">In software development and product management, a user story is an informal, natural language description of features of a software system. They are written from the perspective of an end user or user of a system, and may be recorded on index cards, Post-it notes, or digitally in specific management software.</h1>
    <img class="rounded-[30px] h-[350px] sm:w-[1000px] p-2 items-center bg-violet-800 mt-4" src="/Userstory.png" alt="">
    </div>
  </div>
</div>

</main>

<!-- User Story -->

<!-- SKILLS and PROJECTS SECTION -->

  <main id="4th" class="container max-w-full min-h-screen bg-black flex justify-center items-center lg:px-4">

    <div
      class="lg:w-[1500px] lg:h-[800px] lg:bg-neutral-900 lg:text-white lg:rounded-[45px] lg:grid-cols-4 lg:grid lg:grid-rows-3 lg:gap-4 lg:p-4 hidden">
      <div class=" rounded-[30px] col-span-4">
        <div class="flex justify-center items-center">
          <h5 class="text-7xl text-center font-bold p-2">Contact</h5>
        </div>
        <h1 class="text-xl text-center font-san pt-6 pl-2 ">I am glad you reach this contact information section, I hope we can get in touch with one another.</h1>
      </div>

      <a href="https://github.com/ChingVey"
        class=" bg-violet-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/LorChingVeylogo.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Github</li>
      </a>

      <a href="tel:066849166"
        class=" bg-green-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/IncomingCallIcon.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Phone</li>
      </a>


      <a href="https://www.linkedin.com/in/lor-chingvey-126letsdoit29/"
        class=" bg-sky-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/LinkedInlogo.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Linkedin</li>
      </a>

      <a href="https://t.me/Lor_JingVey"
        class=" bg-rose-300 rounded-[30px] text-center transition duration-200 delay-175 hover:scale-105 cursor-pointer">
        <div class="flex justify-between items-center p-3">
          <img class="w-12" src="/telegram-svgrepo-com.svg">
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
        <li class="list-none text-left pl-4 font-bold text-black">Telegram</li>
      </a>

      <div class=" text-center col-span-4 pt-12">
        <h1 class="text-xl text-white">All Rights Reserved.</h1>
        <p class="text-6xl pt-10 font-bold">THANK YOU !</p>
      </div>

    </div>


    <div class=" w-[1000px] h-[1000px] bg-neutral-900 text-white grid grid-cols-2 gap-4 p-4 lg:hidden">
      <div class=" rounded-[15px] col-span-2">
        <div class="flex justify-center items-center">
          <h5
            class="text-7xl text-white font-bold mt-8 pl-6">
            Contact</h5>
        </div>

        <h1 class="text-md text-center font-san pt-6 pl-2 ">I am glad you reach this contact information section, I hope we can get in touch with one another.</h1>
      </div>

      <a href="https://github.com/ChingVey"
        class="bg-violet-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-center p-3">
          <div class="flex items-center">
          <img class="w-12" src="/LorChingVeylogo.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Github</li>
        </div>
        <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
      </a>

      <a href="tel:0889998500"
        class="bg-green-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-center p-3">
          <div class="flex items-center">
          <img class="w-12" src="/IncomingCallIcon.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Phone</li>
        </div>
        <img class="w-12 animate-pulse" src="/Arrow.svg">
      </div>
      </a>

      <a href="https://www.linkedin.com/in/lor-chingvey-126letsdoit29/"
        class="bg-sky-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-cente p-2">
          <div class="flex items-center">
            <img class="w-12" src="/LinkedInlogo.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Linkedin</li>
          </div>
          <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
      </a>

      <a href="https://t.me/Lor_JingVey"
        class="bg-rose-300 rounded-[15px] text-center col-span-4 transition duration-200 delay-175 hover:scale-105 cursor-pointer v-motion">
        <div class="flex justify-between items-center p-3">
          <div class="flex items-center">
          <img class="w-12" src="/telegram-svgrepo-com.svg">
          <li class="list-none text-left pl-4 font-bold text-black">Telegram</li>
        </div>
        <img class="w-12 animate-pulse" src="/Arrow.svg">
        </div>
      </a>

      <div class=" text-center col-span-4 pt-12">
        <h1 class="text-xl text-white">All Rights Reserved.</h1>
        <p>Please View on large screen for a better a portfolio experience.</p>
      </div>
    </div>

  </main>
</template>

<style>
.modal-enter-active,
.modal-leave-active {
  transition: all 0.25s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(1.1);
}</style>