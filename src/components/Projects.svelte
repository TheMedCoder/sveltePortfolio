<script>
  import AOS from "aos";
  import "aos/dist/aos.css";
  AOS.init();

  const projects = [
    {
      name: "Portfolio Website",
      description:
        "A personal portfolio website built with Svelte and Tailwind CSS to showcase my projects and skills.",
      technologies: ["Svelte", "Tailwind CSS", "JavaScript"],
    },
    {
      name: "Web-based OCR Service",
      description:
      "A web-based OCR service for extracting text from images and PDFs, built with Svelte, Tailwind CSS, Laravel, PDF.js, and other tools.",
      technologies: ["Svelte", "Tailwind CSS", "Laravel", "PDF.js", "Olama AI"],
    },
    {
      name: "Healthcare Patient Management System",
      description:
        "A full-stack healthcare platform for managing patient appointments, medical tests, doctor schedules, patient history, and electronic health records.",
      technologies: ["SvelteKit", "C#", ".NET", "PostgreSQL"],
    },
    {
      name: "Calculator App",
      description:
        "A calculator built with HTML, Vue.js, and Tailwind CSS featuring basic arithmetic operations and a clean interface.",
      technologies: ["HTML", "Vue.js", "Tailwind CSS"],
    },
    {
      name: "Cinema Booking CLI System",
      description:
        "A command-line cinema booking system with seat selection, ticket management, and booking confirmation features.",
      technologies: ["C#", ".NET", "Console"],
    },
    {
      name: "A Google-Forms Like Web Application",
      description:
        "A Google-Forms-like web application for creating, distributing, and analyzing surveys, built with Svelte, C#, and Tailwind CSS.",
      technologies: [
        "C#",
        ".NET Framework",
        "SQlite",
        "Svelte",
        "Tailwind CSS",
      ],
    },
  ];
</script>

<div class="w-full px-6 md:px-12 lg:px-24 pb-6" id="projects">
  <h1 class="text-center text-6xl font-bold text-white mb-12">Projects</h1>

  <div class="flex flex-col items-center mb-12 animate-pulse">
    <div class="w-3 h-3 bg-sky-400 rounded-full"></div>
    <div class="w-1 h-24 bg-sky-400"></div>
    <div class="w-3 h-3 bg-sky-400 rounded-full"></div>
  </div>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-12 lg:my-24">
    {#each projects as project}
      <div
        class="border-rotate rounded-lg p-6 transition-all duration-300 hover:scale-102 active:scale-98"
        data-aos="fade-up"
      >
        <h3 class="text-2xl font-semibold text-white mb-4">{project.name}</h3>
        <p class="text-slate-400 mb-6">{project.description}</p>
        <div class="flex flex-wrap gap-4">
          {#each project.technologies as tech}
            <span
              class="text-sm bg-slate-700 text-slate-300 px-3 py-1 rounded-full"
              >{tech}</span
            >
          {/each}
        </div>
      </div>
    {/each}
  </div>

  <div class="flex flex-col items-center mt-12 animate-pulse">
    <div class="w-3 h-3 bg-sky-400 rounded-full"></div>
    <div class="w-1 h-24 bg-sky-400"></div>
    <div class="w-3 h-3 bg-sky-400 rounded-full"></div>
  </div>
</div>

<style>
  @property --border-angle {
    syntax: "<angle>";
    inherits: true;
    initial-value: 0deg;
  }

  @keyframes rotate-border {
    to {
      --border-angle: 360deg;
    }
  }

  .border-rotate {
    --border-angle: 0deg;
    animation: rotate-border 5s linear infinite;
    background:
      linear-gradient(oklch(13% 0.028 261.692), oklch(13% 0.028 261.692)) padding-box,
      conic-gradient(
          from var(--border-angle),
          transparent 0%,
          transparent 60%,
          oklch(74.6% 0.16 232.661) 90%,
          oklch(50% 0.134 242.749) 70%,
          transparent 90%,
          transparent 100%
        )
        border-box;
    border: 2px solid transparent;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  }

  .border-rotate:hover {
    box-shadow: 
      0 0 10px oklch(74.6% 0.16 232.661),
      0 0 10px oklch(50% 0.134 242.749),
      0 4px 6px -1px rgba(0, 0, 0, 0.1);
    transform: translateY(-4px);
    animation: rotate-border 3s linear infinite;
  }
</style>