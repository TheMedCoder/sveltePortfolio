<script>
  import { fade } from "svelte/transition";
  import { fly } from "svelte/transition";
  import { gsap } from "gsap";
  import { SplitText } from "gsap/SplitText";
  import Icon from "@iconify/svelte";
  import CVModal from "./CVModal.svelte";
  import AOS from "aos";
  import "aos/dist/aos.css";
  import { onMount } from "svelte";
  import { flip } from "svelte/animate";
  import { onDestroy } from "svelte";
  import "../app.css";

  // Get base path from import.meta.env
  const basePath = import.meta.env.BASE_URL;

  AOS.init();

  let skills = [
    { name: "HTML", icon: "devicon:html5" },
    { name: "CSS", icon: "devicon:css3" },
    { name: "TailwindCSS", icon: "logos:tailwindcss-icon" },
    { name: "JavaScript", icon: "logos:javascript" },
    { name: "Svelte", icon: "logos:svelte-icon" },
    { name: "Vue", icon: "logos:vue" },
    { name: "React", icon: "logos:react" },
    { name: "Git", icon: "logos:git-icon" },
    { name: "GitHub", icon: "logos:github-icon" },
    { name: "SQL", icon: "devicon:mysql" },
    { name: "C#", icon: "devicon:csharp" },
    { name: ".NET", icon: "devicon:dotnetcore" },
  ];

  let titleEl;
  let showCVModal = false;

  let interval;
  let visibleCount = 5;
  let windowWidth;

  // Update visible count based on width
  $: if (windowWidth) {
    if (windowWidth < 640) visibleCount = 5;
    else if (windowWidth < 1024) visibleCount = 7;
    else visibleCount = 8;
  }

  // Reactive slice for display
  $: visibleSkills = skills.slice(0, visibleCount);

  onMount(() => {
    const split = new SplitText(titleEl, { type: "chars" });

    gsap.from(split.chars, {
      opacity: 0,
      y: 10,
      stagger: 0.09,
      duration: 1,
      ease: "power3.out",
    });

    startRotation();
  });

  function startRotation() {
    interval = setInterval(() => {
      skills = [...skills.slice(1), skills[0]];
    }, 1500);
  }

  onDestroy(() => {
    if (interval) clearInterval(interval);
  });
</script>

<svelte:window bind:innerWidth={windowWidth} />

<main class="mb-16 xl:mb-0 bg-gray-950 text-white mt-4">

  <div
    class="flex flex-col lg:flex-row items-center lg:items-start justify-between gap-12 lg:gap-24 px-6 md:px-12 lg:px-24 md:pt-20"
  >
    <!-- Left Content -->
    <div class="flex-1 space-y-8 pt-12">
      <div>
        <h1 class="text-4xl md:text-4xl lg:text-5xl xl:text-6xl font-bold mb-4">
          <div class="flex">
            <div transition:fly={{ x: -200, duration: 2000 }}>Welcome</div>
            <span class="text-sky-500 animate-bounce-once drop-shadow-blue-400 drop-shadow-sm">.</span>
          </div>
        </h1>
        <div class="flex items-center gap-4 mb-4 xl:mb-8 relative">
          <div
            class="hidden lg:block h-1 bg-sky-500 absolute left-0 -translate-x-full w-screen drop-shadow-blue-400 drop-shadow-sm"
          ></div>
          <div
            data-aos="fade-right"
            class="h-1 w-20 md:w-10 xl:w-20 bg-sky-500 relative drop-shadow-blue-400 drop-shadow-sm"
          ></div>
          <p class="text-2xl md:text-3xl text-gray-300">I'm Sajjad</p>
        </div>
        <h2 bind:this={titleEl} class="text-3xl md:text-4xl font-bold mb-8">
          Software Developer
        </h2>
      </div>

      <!-- Buttons -->
      <div class="  flex flex-wrap gap-4 mb-8 md:mb-0">
        <button 
        onclick={() =>
            document
              .getElementById("contact")
              ?.scrollIntoView({ behavior: "smooth" })}
        class="group relative overflow-hidden rounded p-[2px] focus:outline-none hover:scale-102 active:scale-98 focus:ring-slate-400 focus:ring-offset-2 focus:ring-offset-slate-50">
          <span class="absolute inset-[-1000%] animate-[spin_1.5s_linear_infinite] bg-[conic-gradient(from_90deg_at_50%_50%,#E2E8F0_0%,#4FA3E0_50%,#E2E8F0_100%)]"></span>
          <span class="inline-flex h-full w-full cursor-pointer items-center justify-center rounded bg-slate-950 px-8 py-3 font-bold text-white backdrop-blur-3xl transition-all group-hover:bg-slate-900">
           Get in Touch
          </span>
        </button>
        
          <!-- class=" px-8 py-4 bg-sky-500 hover:bg-sky-600 text-white font-semibold rounded transition-colors cursor-pointer drop-shadow-sm drop-shadow-blue-400" -->
        
        <button
          onclick={() => (showCVModal = true)}
          class=" px-8 py-4 border-2 border-sky-500 hover:bg-sky-500/10 text-white font-semibold rounded transition-colors cursor-pointer"
        >
          View CV
        </button>
      </div>
    </div>

    <!-- Right Content -->
    <div class="flex-1 flex justify-center lg:justify-end">
      <div class="relative overflow-visible">
        <div
          in:fade={{ duration: 500 }}
          class="absolute top-10 -left-12 hidden  md:w-24 md:h-24 xl:w-32 xl:h-32 border-2 border-sky-500/80 transform rotate-12 animate-spin overflow-hidden drop-shadow-blue-400 drop-shadow-md"
          style="animation-duration: 8s;"
        ></div>
        <div
          in:fade={{ duration: 500 }}
          class="absolute bottom-25 -right-8 hidden  md:w-24 md:h-24 xl:w-32 xl:h-32 border-2 border-sky-500/80 transform -rotate-12 animate-bounce overflow-hidden drop-shadow-blue-400 drop-shadow-md"
          style="animation-duration: 3.5s;"
        ></div>

        <div
          class="absolute inset-0 rounded-full blur-2xl opacity-10 z-0"
          style="
            background: conic-gradient(from 0deg, #38bdf8, #818cf8, #f472b6, #38bdf8);
            animation: spin 6s linear infinite;
          "
        ></div>

        <!-- circle background -->
        <div
          class="absolute -inset-5 lg:-inset-6 xl:-inset-6 bottom-1 w-72 h-72 md:w-82 md:h-82 xl:w-105 xl:h-105 rounded-full border-6 border-sky-500/80 drop-shadow-blue-400 drop-shadow-lg z-0 animate-[spin_2s_infinite_linear]"
        ></div>

        <!-- image in front -->
        <img
          src="./Sajjad_Ahmed.png"
          alt="Sajjad"
          class="relative w-64 h-auto md:w-72 xl:w-96 md:h-auto object-cover z-10 drop-shadow-xl/25 max-w-full"
        />
      </div>
    </div>
  </div>

  <!-- Skills Section -->
  <div class="xl:py-4 bg-slate-800 overflow-hidden">
    <div
      class="flex gap-4 justify-center items-center opacity-90 px-6 md:px-12 lg:px-24 h-16"
    >
      {#each visibleSkills as skill (skill.name)}
        <div
          animate:flip={{ duration: 300 }}
          in:fly={{ x: 50, duration: 300 }}
          out:fly={{ x: -50, duration: 300 }}
          class="flex items-center justify-center min-w-[60px] md:min-w-[80px]"
        >
          <span
            class="tracking-wide hover:text-sky-300 transition-colors cursor-default hover:scale-120"
            title={skill.name}
          >
            <Icon icon={skill.icon} class="w-7 h-7 md:w-8 md:h-8 xl:w-10 xl:h-10" />
          </span>
        </div>
      {/each}
    </div>

    <div class="relative xl:-bottom-4 w-full h-1 bg-blue-400/80 animate-[pulse_3s_infinite] drop-shadow-blue-400 drop-shadow-lg"></div>
  </div>

  <!-- CV Modal Component -->
  <CVModal
    bind:show={showCVModal}
    pdfPath="{basePath}Sajjad Ahmed Mohammed CV (1).pdf"
  />
</main>

<style>
  .animate-bounce-once {
    animation: bounce 0.75s ease-in-out 2;
  }

  @keyframes bounce {
    0%,
    100% {
      transform: translateY(0);
    }
    50% {
      transform: translateY(-25%);
    }
  }
</style>
