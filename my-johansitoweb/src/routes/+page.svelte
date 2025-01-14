<header class="fixed top-0 z-10 flex items-center justify-center w-full mx-auto mt-2" data-astro-cid-3ef6ksr2="">
     <nav class="flex px-3 text-sm font-medium rounded-full text-gray-600 dark:text-gray-200 justify-center items-center" data-astro-cid-3ef6ksr2=""> 
        <a class="relative block px-2 py-2 transition hover:text-blue-500 dark:hover:text-blue-500" aria-label="experiencia" href="/#experiencia" data-astro-cid-3ef6ksr2=""> Experiencia </a><a class="relative block px-2 py-2 transition hover:text-blue-500 dark:hover:text-blue-500" aria-label="proyectos" href="/#proyectos" data-astro-cid-3ef6ksr2=""> Proyectos </a><a class="relative block px-2 py-2 transition hover:text-blue-500 dark:hover:text-blue-500" aria-label="sobre-mi" href="/#sobre-mi" data-astro-cid-3ef6ksr2=""> Sobre mí </a><a class="relative block px-2 py-2 transition hover:text-blue-500 dark:hover:text-blue-500" aria-label="contacto" href="mailto:miduga@gmail.com" data-astro-cid-3ef6ksr2=""> Contacto </a> <div class="relative ml-1 mr-1" data-astro-cid-x3pjskd3=""> <button id="theme-toggle-btn" class="appearance-none border-none flex hover:scale-125 transition" data-astro-cid-x3pjskd3="" data-astro-transition-persist="astro-ko5uysgj-1"> <span class="sr-only" data-astro-cid-x3pjskd3="">Elige el tema</span> <svg id="light" class="theme-toggle-icon size-5 transition-all" data-astro-cid-x3pjskd3="" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round" style="scale: 0;"> <path stroke="none" d="M0 0h24v24H0z" fill="none"></path> <path d="M12 12m-4 0a4 4 0 1 0 8 0a4 4 0 1 0 -8 0"></path> <path d="M3 12h1m8 -9v1m8 8h1m-9 8v1m-6.4 -15.4l.7 .7m12.1 -.7l-.7 .7m0 11.4l.7 .7m-12.1 -.7l-.7 .7"></path> </svg> <svg id="dark" class="theme-toggle-icon absolute size-5 transition-all" data-astro-cid-x3pjskd3="" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round" style="scale: 1;"> <path stroke="none" d="M0 0h24v24H0z" fill="none"></path> <path d="M12 3c.132 0 .263 0 .393 0a7.5 7.5 0 0 0 7.92 12.446a9 9 0 1 1 -8.313 -12.454z"></path> </svg> <svg id="system" class="theme-toggle-icon absolute size-5 transition-all" data-astro-cid-x3pjskd3="" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round" style="scale: 0;"> <path stroke="none" d="M0 0h24v24H0z" fill="none"></path> <path d="M3 5a1 1 0 0 1 1 -1h16a1 1 0 0 1 1 1v10a1 1 0 0 1 -1 1h-16a1 1 0 0 1 -1 -1v-10z"></path> <path d="M7 20h10"></path> <path d="M9 16v4"></path> <path d="M15 16v4"></path> </svg> </button> <div id="themes-menu" class="absolute hidden scale-80 top-8 right-0 text-sm p-1 min-w-[8rem] rounded-md border border-gray-100 bg-white/90 dark:bg-gray-900/90 dark:border-gray-500/20 shadow-[0_3px_10px_rgb(0,0,0,0.2)] backdrop-blur-md" data-astro-cid-x3pjskd3="" data-astro-transition-persist="astro-d5hlxqxh-2"> <ul data-astro-cid-x3pjskd3=""> <li class="themes-menu-option px-2 py-1.5 cursor-default hover:bg-neutral-400/40 dark:hover:bg-gray-500/50 rounded-sm" data-astro-cid-x3pjskd3=""> Light </li><li class="themes-menu-option px-2 py-1.5 cursor-default hover:bg-neutral-400/40 dark:hover:bg-gray-500/50 rounded-sm" data-astro-cid-x3pjskd3=""> Dark </li><li class="themes-menu-option px-2 py-1.5 cursor-default hover:bg-neutral-400/40 dark:hover:bg-gray-500/50 rounded-sm" data-astro-cid-x3pjskd3=""> System </li> </ul> </div> </div>  <script data-astro-exec="">
  let remove = null
  const matchMedia = window.matchMedia("(prefers-color-scheme: dark)")
  const themesMenu = document.getElementById("themes-menu")

  const getThemePreference = () => {
    if (typeof localStorage !== "undefined") {
      return localStorage.getItem("theme") ?? "system"
    }

    return window.matchMedia("(prefers-color-scheme: dark)").matches
      ? "dark"
      : "light"
  }

  const updateIcon = (themePreference) => {
    document.querySelectorAll(".theme-toggle-icon").forEach((element) => {
      element.style.scale = element.id === themePreference ? "1" : "0"
    })
  }

  const updateTheme = () => {
    if (remove != null) {
      remove()
    }
    matchMedia.addEventListener("change", updateTheme)
    remove = () => {
      matchMedia.removeEventListener("change", updateTheme)
    }

    const themePreference = getThemePreference()
    const isDark =
      themePreference === "dark" ||
      (themePreference === "system" && matchMedia.matches)

    updateIcon(themePreference)
    document.documentElement.classList[isDark ? "add" : "remove"]("dark")
  }

  updateTheme()

  document.addEventListener("click", () => themesMenu.classList.remove("open"))

  document.getElementById("theme-toggle-btn").addEventListener("click", (e) => {
    e.stopPropagation()
    const isClosed = !themesMenu.classList.contains("open")
    themesMenu.classList[isClosed ? "add" : "remove"]("open")
  })

  document.querySelectorAll(".themes-menu-option").forEach((element) => {
    element.addEventListener("click", (e) => {
      localStorage.setItem("theme", e.target.innerText.toLowerCase().trim())
      updateTheme()
    })
  })

  document.addEventListener('astro:after-swap', () => {
    updateTheme();
    window.scrollTo({ left: 0, top: 0, behavior: 'instant' });
  })
</script> </nav> </header>
<section class="section py-16 md:py-36 scroll-m-20 w-full mx-auto container lg:max-w-4xl md:max-w-2xl">  <div class="max-w-xl"> <div class="flex gap-4 mb-4"> <img class="rounded-full shadow-lg size-16" src="https://avatars.githubusercontent.com/u/147890607?v=4" alt="johansitoweb"> <a href="johansitoweb" target="_blank" rel="noopener" class="flex items-center transition md:justify-center md:hover:scale-105"> <div class="flex items-center "> <span class="relative inline-flex overflow-hidden rounded-full p-[1px]"> <span class="absolute inset-[-1000%] animate-[spin_2s_linear_infinite] bg-[conic-gradient(from_90deg_at_50%_50%,#51E4B8_0%,#21554E_50%,#51E4B8_100%)]"></span> <div class="inline-flex items-center justify-center w-full px-3 py-1 text-sm text-green-800 bg-green-100 rounded-full cursor-pointer dark:bg-gray-800 dark:text-white/80 backdrop-blur-3xl whitespace-nowrap"> Disponible para trabajar </div> </span> </div> </a> </div> <h1 class="text-4xl font-bold tracking-tight text-gray-800 sm:text-5xl dark:text-white">
    Hey, Soy Johan Antonio
    </h1> <p class="mt-6 text-xl text-gray-800 dark:[&amp;>strong]:text-yellow-200 [&amp;>strong]:text-yellow-500 [&amp;>strong]:font-semibold dark:text-gray-300">
    +5 años de experiencia. <strong>Ingeniero de Software |Ruby Developer |Mobile Developer|DevOps</strong> de santo Domingo, Republica Dominicana . Especializado en el desarrollo de aplicaciones mobiles 
        únicas .
    </p> <nav class="flex flex-wrap gap-4 mt-8"> <a href="mailto:mancebojohan97@gmail.com" target="_blank" rel="noopener noreferrer" role="link" class="inline-flex items-center justify-center gap-2 px-4 py-1 text-gray-800 transition bg-gray-100 border border-gray-300 rounded-full dark:bg-gray-800 dark:border-gray-600 dark:text-white focus-visible:ring-yellow-500/80 text-md hover:bg-gray-900 hover:border-gray-700 hover:text-white dark:hover:bg-gray-100 dark:hover:border-gray-300 dark:hover:text-black group max-w-fit focus:outline-none focus-visible:outline-none focus-visible:ring focus-visible:ring-white focus-visible:ring-offset-2 active:bg-black">  <svg class="size-4" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M12 18h-7a2 2 0 0 1 -2 -2v-10a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v7.5"></path><path d="M3 6l9 6l9 -6"></path><path d="M15 18h6"></path><path d="M18 15l3 3l-3 3"></path></svg>
    Contáctame
     </a> <a href="" target="_blank" rel="noopener noreferrer" role="link" class="inline-flex items-center justify-center gap-2 px-4 py-1 text-gray-800 transition bg-gray-100 border border-gray-300 rounded-full dark:bg-gray-800 dark:border-gray-600 dark:text-white focus-visible:ring-yellow-500/80 text-md hover:bg-gray-900 hover:border-gray-700 hover:text-white dark:hover:bg-gray-100 dark:hover:border-gray-300 dark:hover:text-black group max-w-fit focus:outline-none focus-visible:outline-none focus-visible:ring focus-visible:ring-white focus-visible:ring-offset-2 active:bg-black">  <svg class="size-4" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M4 4m0 2a2 2 0 0 1 2 -2h12a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-12a2 2 0 0 1 -2 -2z"></path><path d="M8 11l0 5"></path><path d="M8 8l0 .01"></path><path d="M12 16l0 -5"></path><path d="M16 16v-3a2 2 0 0 0 -4 0"></path></svg>
    LinkedIn
     </a> </nav> </div>  </section>
     <section id="experiencia" data-section="experiencia" class="section undefined scroll-m-20 w-full mx-auto container lg:max-w-4xl md:max-w-2xl">  <h2 class="flex items-center mb-6 text-3xl font-semibold gap-x-3 text-black/80 dark:text-white undefined">  <svg class="size-8" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M3 7m0 2a2 2 0 0 1 2 -2h14a2 2 0 0 1 2 2v9a2 2 0 0 1 -2 2h-14a2 2 0 0 1 -2 -2z"></path><path d="M8 7v-2a2 2 0 0 1 2 -2h4a2 2 0 0 1 2 2v2"></path><path d="M12 12l0 .01"></path><path d="M3 13a20 20 0 0 0 18 0"></path></svg>
        Experiencia laboral
         </h2> <ol class="relative mt-16"> <li class=""> <div class="relative mx-12 pb-12 grid before:absolute before:left-[-35px] before:block before:h-full before:border-l-2 before:border-black/20 dark:before:border-white/15 before:content-[''] md:grid-cols-5 md:gap-10 md:space-x-4]"> <div class="relative pb-12 md:col-span-2"> <div class="sticky top-0"> <span class="text-yellow-400 -left-[42px] absolute rounded-full text-5xl">•</span> <h3 class="text-xl font-bold text-yellow-400">Creador de Contenido</h3> <h4 class="font-semibold text-xl text-gray-600 dark:text-white">Twitch</h4> <time class="p-0 m-0 text-sm text-gray-600/80 dark:text-white/80">Actualmente...</time> </div> </div> <div class="relative flex flex-col gap-2 pb-4 text-gray-600 dark:text-gray-300 md:col-span-3"> Divulgo sobre programación y desarrollo web en diferentes plataformas. Galardonado como mejor creador de contenido de habla no-inglesa en 2022 y mejor comunidad en 2023 por GitHub. <a href="https://twitch.tv/midudev" role="link" class="inline-flex items-center text-lg font-medium text-yellow-500 dark:text-yellow-200 dark:hover:text-yellow-300 hover:text-yellow-700"> 
        Saber más <svg xmlns="http://www.w3.org/2000/svg" class="w-5 icon icon-tabler icon-tabler-chevron-right" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">  <path stroke="none" d="M0 0h24v24H0z" fill="none"></path> <path d="M9 6l6 6l-6 6"></path>  </svg>  </a> </div> </div> </li><li class=""> <div class="relative mx-12 pb-12 grid before:absolute before:left-[-35px] before:block before:h-full before:border-l-2 before:border-black/20 dark:before:border-white/15 before:content-[''] md:grid-cols-5 md:gap-10 md:space-x-4]"> <div class="relative pb-12 md:col-span-2"> <div class="sticky top-0"> <span class="text-yellow-400 -left-[42px] absolute rounded-full text-5xl">•</span> <h3 class="text-xl font-bold text-yellow-400">Principal Frontend Engineer</h3> <h4 class="font-semibold text-xl text-gray-600 dark:text-white">Adevinta Spain</h4> <time class="p-0 m-0 text-sm text-gray-600/80 dark:text-white/80">Septiembre 2022</time> </div> </div> <div class="relative flex flex-col gap-2 pb-4 text-gray-600 dark:text-gray-300 md:col-span-3"> Responsable de la plataforma, componentes y utilidades para la creación y desarrollo de aplicaciones web. Mejora de un 30% en la entrega de software. Implantación de medidas de integración continua y despliegue con A/B testing en más de 15 equipos.  </div> </div> </li> </ol>  </section>
        <section id="proyectos" data-section="proyectos" class="section undefined scroll-m-20 w-full mx-auto container lg:max-w-4xl md:max-w-2xl">  <h2 class="flex items-center mb-6 text-3xl font-semibold gap-x-3 text-black/80 dark:text-white undefined">  <svg class="size-7" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M7 8l-4 4l4 4"></path><path d="M17 8l4 4l-4 4"></path><path d="M14 4l-4 16"></path></svg>
            Proyectos
             </h2> <div class="flex flex-col gap-y-16"> <article class="flex flex-col space-x-0 space-y-8 group md:flex-row md:space-x-8 md:space-y-0"> <div class="w-full md:w-1/2"> <div class="relative flex flex-col items-center col-span-6 row-span-5 gap-8 transition duration-500 ease-in-out transform shadow-xl overflow-clip rounded-xl sm:rounded-xl md:group-hover:-translate-y-1 md:group-hover:shadow-2xl lg:border lg:border-gray-800 lg:hover:border-gray-700 lg:hover:bg-gray-800/50"> <img alt="Recién llegado vs 5 años en Nueva Zelanda" class="object-cover object-top w-full h-56 transition duration-500 sm:h-full md:scale-110 md:group-hover:scale-105" loading="lazy" src="/projects/svgl.webp"> </div> </div> <div class="w-full md:w-1/2 md:max-w-lg"> <h3 class="text-2xl font-bold text-gray-800 dark:text-gray-100"> SVGL - A beautiful library with SVG logos </h3> <div class="flex flex-wrap mt-2"> <ul class="flex flex-row mb-2 gap-x-2"> <li> <span class="flex gap-x-2 rounded-full text-xs bg-black text-white py-1 px-2 "> <svg class="size-4" xmlns="http://www.w3.org/2000/svg" width="256" height="256" preserveAspectRatio="xMidYMid" viewBox="0 0 256 256"> <defs> <linearGradient id="c" x1="55.633%" x2="83.228%" y1="56.385%" y2="96.08%"> <stop offset="0%" stop-color="#FFF"></stop> <stop offset="100%" stop-color="#FFF" stop-opacity="0"></stop> </linearGradient> <linearGradient id="d" x1="50%" x2="49.953%" y1="0%" y2="73.438%"> <stop offset="0%" stop-color="#FFF"></stop> <stop offset="100%" stop-color="#FFF" stop-opacity="0"></stop> </linearGradient> <circle id="a" cx="128" cy="128" r="128"></circle> </defs> <mask id="b" fill="#fff"> <use xlink:href="#a"></use> </mask> <g mask="url(#b)"> <circle cx="128" cy="128" r="128"></circle> <path fill="url(#c)" d="M212.634 224.028 98.335 76.8H76.8v102.357h17.228V98.68L199.11 234.446a128.433 128.433 0 0 0 13.524-10.418Z"></path> <path fill="url(#d)" d="M163.556 76.8h17.067v102.4h-17.067z"></path> </g> </svg> Next.js </span> </li><li> <span class="flex gap-x-2 rounded-full text-xs bg-[#003159] text-white py-1 px-2 "> <svg class="size-4" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 54 33"><g clip-path="url(#a)"><path fill="#38bdf8" fill-rule="evenodd" d="M27 0c-7.2 0-11.7 3.6-13.5 10.8 2.7-3.6 5.85-4.95 9.45-4.05 2.054.513 3.522 2.004 5.147 3.653C30.744 13.09 33.808 16.2 40.5 16.2c7.2 0 11.7-3.6 13.5-10.8-2.7 3.6-5.85 4.95-9.45 4.05-2.054-.513-3.522-2.004-5.147-3.653C36.756 3.11 33.692 0 27 0zM13.5 16.2C6.3 16.2 1.8 19.8 0 27c2.7-3.6 5.85-4.95 9.45-4.05 2.054.514 3.522 2.004 5.147 3.653C17.244 29.29 20.308 32.4 27 32.4c7.2 0 11.7-3.6 13.5-10.8-2.7 3.6-5.85 4.95-9.45 4.05-2.054-.513-3.522-2.004-5.147-3.653C23.256 19.31 20.192 16.2 13.5 16.2z" clip-rule="evenodd"></path></g><defs><clipPath id="a"><path fill="#fff" d="M0 0h54v32.4H0z"></path></clipPath></defs></svg> Tailwind CSS </span> </li> </ul> <div class="mt-2 text-gray-700 dark:text-gray-400">Biblioteca de logos SVG de las marcas más populares. +10k visitas al mes. +2K svgs descargados. Creado desde cero con Next.js, React y Tailwind CSS.</div> <footer class="flex items-end justify-start mt-4 gap-x-4"> <a target="_blank" href="https://github.com/pheralb/svgl" role="link" class="inline-flex bg-gray-100 text-gray-800 border-gray-300 items-center justify-center gap-2 px-3 py-2 space-x-2 text-base transition dark:text-white dark:bg-gray-800 border dark:border-gray-600 focus-visible:ring-yellow-500/80 text-md hover:bg-gray-800 hover:border-gray-900 group max-w-fit rounded-xl hover:text-white focus:outline-none focus-visible:outline-none focus-visible:ring focus-visible:ring-white focus-visible:ring-offset-2 active:bg-black">  <svg class="size-6" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M9 19c-4.3 1.4 -4.3 -2.5 -6 -3m12 5v-3.5c0 -1 .1 -1.4 -.5 -2c2.8 -.3 5.5 -1.4 5.5 -6a4.6 4.6 0 0 0 -1.3 -3.2a4.2 4.2 0 0 0 -.1 -3.2s-1.1 -.3 -3.5 1.3a12.3 12.3 0 0 0 -6.2 0c-2.4 -1.6 -3.5 -1.3 -3.5 -1.3a4.2 4.2 0 0 0 -.1 3.2a4.6 4.6 0 0 0 -1.3 3.2c0 4.6 2.7 5.7 5.5 6c-.6 .6 -.6 1.2 -.5 2v3.5"></path></svg>
            Code
             </a> <a target="_blank" href="https://svgl.vercel.app/" role="link" class="inline-flex bg-gray-100 text-gray-800 border-gray-300 items-center justify-center gap-2 px-3 py-2 space-x-2 text-base transition dark:text-white dark:bg-gray-800 border dark:border-gray-600 focus-visible:ring-yellow-500/80 text-md hover:bg-gray-800 hover:border-gray-900 group max-w-fit rounded-xl hover:text-white focus:outline-none focus-visible:outline-none focus-visible:ring focus-visible:ring-white focus-visible:ring-offset-2 active:bg-black">  <svg class="size-4" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg>
            Preview
             </a> </footer> </div> </div> </article><article class="flex flex-col space-x-0 space-y-8 group md:flex-row md:space-x-8 md:space-y-0"> <div class="w-full md:w-1/2"> <div class="relative flex flex-col items-center col-span-6 row-span-5 gap-8 transition duration-500 ease-in-out transform shadow-xl overflow-clip rounded-xl sm:rounded-xl md:group-hover:-translate-y-1 md:group-hover:shadow-2xl lg:border lg:border-gray-800 lg:hover:border-gray-700 lg:hover:bg-gray-800/50"> <img alt="Recién llegado vs 5 años en Nueva Zelanda" class="object-cover object-top w-full h-56 transition duration-500 sm:h-full md:scale-110 md:group-hover:scale-105" loading="lazy" src="/projects/adventjs.webp"> </div> </div> <div class="w-full md:w-1/2 md:max-w-lg"> <h3 class="text-2xl font-bold text-gray-800 dark:text-gray-100"> AdventJS - Retos de programación con JavaScript y TypeScript </h3> <div class="flex flex-wrap mt-2"> <ul class="flex flex-row mb-2 gap-x-2"> <li> <span class="flex gap-x-2 rounded-full text-xs bg-black text-white py-1 px-2 "> <svg class="size-4" xmlns="http://www.w3.org/2000/svg" width="256" height="256" preserveAspectRatio="xMidYMid" viewBox="0 0 256 256"> <defs> <linearGradient id="c" x1="55.633%" x2="83.228%" y1="56.385%" y2="96.08%"> <stop offset="0%" stop-color="#FFF"></stop> <stop offset="100%" stop-color="#FFF" stop-opacity="0"></stop> </linearGradient> <linearGradient id="d" x1="50%" x2="49.953%" y1="0%" y2="73.438%"> <stop offset="0%" stop-color="#FFF"></stop> <stop offset="100%" stop-color="#FFF" stop-opacity="0"></stop> </linearGradient> <circle id="a" cx="128" cy="128" r="128"></circle> </defs> <mask id="b" fill="#fff"> <use xlink:href="#a"></use> </mask> <g mask="url(#b)"> <circle cx="128" cy="128" r="128"></circle> <path fill="url(#c)" d="M212.634 224.028 98.335 76.8H76.8v102.357h17.228V98.68L199.11 234.446a128.433 128.433 0 0 0 13.524-10.418Z"></path> <path fill="url(#d)" d="M163.556 76.8h17.067v102.4h-17.067z"></path> </g> </svg> Next.js </span> </li><li> <span class="flex gap-x-2 rounded-full text-xs bg-[#003159] text-white py-1 px-2 "> <svg class="size-4" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 54 33"><g clip-path="url(#a)"><path fill="#38bdf8" fill-rule="evenodd" d="M27 0c-7.2 0-11.7 3.6-13.5 10.8 2.7-3.6 5.85-4.95 9.45-4.05 2.054.513 3.522 2.004 5.147 3.653C30.744 13.09 33.808 16.2 40.5 16.2c7.2 0 11.7-3.6 13.5-10.8-2.7 3.6-5.85 4.95-9.45 4.05-2.054-.513-3.522-2.004-5.147-3.653C36.756 3.11 33.692 0 27 0zM13.5 16.2C6.3 16.2 1.8 19.8 0 27c2.7-3.6 5.85-4.95 9.45-4.05 2.054.514 3.522 2.004 5.147 3.653C17.244 29.29 20.308 32.4 27 32.4c7.2 0 11.7-3.6 13.5-10.8-2.7 3.6-5.85 4.95-9.45 4.05-2.054-.513-3.522-2.004-5.147-3.653C23.256 19.31 20.192 16.2 13.5 16.2z" clip-rule="evenodd"></path></g><defs><clipPath id="a"><path fill="#fff" d="M0 0h54v32.4H0z"></path></clipPath></defs></svg> Tailwind CSS </span> </li> </ul> <div class="mt-2 text-gray-700 dark:text-gray-400">Plataforma gratuita con retos de programación. Más de 1 millón de visitas en un mes. +50K retos completados. Creada desde cero con Next.js, React y Tailwind CSS.</div> <footer class="flex items-end justify-start mt-4 gap-x-4">  <a target="_blank" href="https://adventjs.dev" role="link" class="inline-flex bg-gray-100 text-gray-800 border-gray-300 items-center justify-center gap-2 px-3 py-2 space-x-2 text-base transition dark:text-white dark:bg-gray-800 border dark:border-gray-600 focus-visible:ring-yellow-500/80 text-md hover:bg-gray-800 hover:border-gray-900 group max-w-fit rounded-xl hover:text-white focus:outline-none focus-visible:outline-none focus-visible:ring focus-visible:ring-white focus-visible:ring-offset-2 active:bg-black">  <svg class="size-4" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg>
            Preview
             </a> </footer> </div> </div> </article> </div>  </section>
             <section id="sobre-mi" data-section="sobre-mi" class="section undefined scroll-m-20 w-full mx-auto container lg:max-w-4xl md:max-w-2xl">  <h2 class="flex items-center mb-6 text-3xl font-semibold gap-x-3 text-black/80 dark:text-white undefined">  <svg class="size-8" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M8 7a4 4 0 1 0 8 0a4 4 0 0 0 -8 0"></path><path d="M6 21v-2a4 4 0 0 1 4 -4h4"></path><path d="M15 19l2 2l4 -4"></path></svg>
                Sobre mí
                 </h2> <article class="flex flex-col items-center justify-center gap-8 text-gray-700 dark:text-gray-300 md:flex-row"> <div class="[&amp;>p]:mb-4 [&amp;>p>strong]:text-yellow-500 dark:[&amp;>p>strong]:text-yellow-100 [&amp;>p>strong]:font-normal [&amp;>p>strong]:font-mono text-pretty order-2 md:order-1"> <p>
                Me llamo Johan Mancebo pero mis amigos me llaman johansitoweb. Empecé en la
                      programación cuando tenía 12 años. Actualmente estoy <strong>trabajando como frelancer </strong>.
                </p> <p>
                Algunos de mis éxitos incluyen <strong>la creacion de un software para una veterinaria , Ferreteria , Tienda de productos del hogar
                        un videojuego 2D en Godot y GDscript entre otros</strong>. Actualmente imparcto clases de programacion
                </p> <p>
                Comparto contenido, <strong>en Discord y en you tube
                        sobre Desarrollo web , videojuegos , tensorflow y Desarrollo Movile </strong>. Mi objetivo es ayudar todos los jovones que quieren convertirse en programadores o Desarrolladores.
                </p> </div> <img width="200" height="200" src="https://avatars.githubusercontent.com/u/147890607?v=4" alt="johansitoweb" class="order-1 object-cover w-64 h-full p-1 md:order-2 rotate-3 lg:p-2 lg:w-64 aspect-square rounded-2xl bg-black/20 dark:bg-yellow-500/5 ring-1 ring-black/70 dark:ring-white/20 " style="object-position: 50% 50%"> </article> <!-- FRASES PROHIBIDAS EN VUESTRO PORTFOLIO
                
                <p>
                  Mi sueño es encontrar mi primer empleo en el mundo de la programación. Una empresa donde pueda seguir aprendiendo. ❌
                </p>
                
                <p>
                  ❌ Apasionado de la programación desde chekitito. Me encantan los ordenadores y crear páginas web buenas y rápidas con la última tecnología.
                </p>
                
                <p>
                  Trabajo bien en equipo. Siempre estoy aprendiendo cosas nuevas.
                </p>
                
                -------------------------------------
                
                --------------------------------------
                
                <p>
                  ¡Soy Leo! Estudié Derecho Empresarial y, tras años ejerciendo, me pasé al mundo de la Programación. Desde entonces disfruto creando experiencias web para los usuarios.
                </p>
                
                <p>
                  Entre mis éxitos destaco que durante el Grado Superior, ayudé a mis compañeros a aprender sobre TDD. Me encanta el testing, creo en su importancia, y me gusta compartir mi conocimiento sobre ello.
                </p>
                
                <p>
                  Cuento con experiencia desarrollando aplicaciones móviles, y he creado una iniciativa llamada X para mezclar mis dos pasiones: la programación y el derecho. Ayudando a la sociedad a acceso a una defensa justa.
                </p>
                
                ---------------------------------------
                
                <p>Me llamo Sara, tengo 25 años y soy de Santiago, Chile 🇨🇱. Terminé mis estudios como Desarrolladora Web. Me encanta enfocarme en la parte del rendimiento, para ofrecer la mejora experiencia al usuario.</p>
                
                <p>
                  Colaboro en la organización del MeetUp local BeerJS donde reunimos a desarrolladores de Santiago para compartir conocimiento y experiencias. El año 2023 hicimos un total de 25 charlas con más de 2000 asistentes.
                </p>
                
                <p>
                  Además de participar activamente en la comunidad, he participado en la Hackathon de Midudev quedando en 3er puesto con mi proyecto _Chatty_, donde usando IA podías interactuar con un PDF. ¡Échale un vistazo!
                </p>
                
                -->  </section>
                <div class="rounded-lg w-full max-w-screen-xl mx-auto md:flex md:items-center md:justify-between py-4"> <span class="text-sm sm:text-center text-zinc-800/90 dark:text-zinc-200/90">© 2024 <a href="https://midu.dev/" class="hover:underline">midudev</a>. Casi
                    todos los derechos reservados
              </span> <ul class="flex flex-wrap items-center mt-3 text-sm font-medium dark:text-white/90 sm:mt-0"> <li> <a href="/#sobre-mi" class="hover:underline me-4 md:me-6">Sobre mí</a> </li> <li> <a id="contacto" href="mailto:miduga@gmail.com" class="hover:underline">Contacto</a> </li> </ul> </div>


              <script src="https://cdn.tailwindcss.com"></script>

              <style>
                *,:before,:after {
    box-sizing: border-box;
    border-width: 0;
    border-style: solid;
    border-color: #e5e7eb
}

:before,:after {
    --tw-content: ""
}

html,:host {
    line-height: 1.5;
    -webkit-text-size-adjust: 100%;
    -moz-tab-size: 4;
    -o-tab-size: 4;
    tab-size: 4;
    font-family: ui-sans-serif,system-ui,sans-serif,"Apple Color Emoji","Segoe UI Emoji",Segoe UI Symbol,"Noto Color Emoji";
    font-feature-settings: normal;
    font-variation-settings: normal;
    -webkit-tap-highlight-color: transparent
}

body {
    margin: 0;
    line-height: inherit
}

hr {
    height: 0;
    color: inherit;
    border-top-width: 1px
}

abbr:where([title]) {
    -webkit-text-decoration: underline dotted;
    text-decoration: underline dotted
}

h1,h2,h3,h4,h5,h6 {
    font-size: inherit;
    font-weight: inherit
}

a {
    color: inherit;
    text-decoration: inherit
}

b,strong {
    font-weight: bolder
}

code,kbd,samp,pre {
    font-family: ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,Liberation Mono,Courier New,monospace;
    font-feature-settings: normal;
    font-variation-settings: normal;
    font-size: 1em
}

small {
    font-size: 80%
}

sub,sup {
    font-size: 75%;
    line-height: 0;
    position: relative;
    vertical-align: baseline
}

sub {
    bottom: -.25em
}

sup {
    top: -.5em
}

table {
    text-indent: 0;
    border-color: inherit;
    border-collapse: collapse
}

button,input,optgroup,select,textarea {
    font-family: inherit;
    font-feature-settings: inherit;
    font-variation-settings: inherit;
    font-size: 100%;
    font-weight: inherit;
    line-height: inherit;
    color: inherit;
    margin: 0;
    padding: 0
}

button,select {
    text-transform: none
}

button,[type=button],[type=reset],[type=submit] {
    -webkit-appearance: button;
    background-color: transparent;
    background-image: none
}

:-moz-focusring {
    outline: auto
}

:-moz-ui-invalid {
    box-shadow: none
}

progress {
    vertical-align: baseline
}

::-webkit-inner-spin-button,::-webkit-outer-spin-button {
    height: auto
}

[type=search] {
    -webkit-appearance: textfield;
    outline-offset: -2px
}

::-webkit-search-decoration {
    -webkit-appearance: none
}

::-webkit-file-upload-button {
    -webkit-appearance: button;
    font: inherit
}

summary {
    display: list-item
}

blockquote,dl,dd,h1,h2,h3,h4,h5,h6,hr,figure,p,pre {
    margin: 0
}

fieldset {
    margin: 0;
    padding: 0
}

legend {
    padding: 0
}

ol,ul,menu {
    list-style: none;
    margin: 0;
    padding: 0
}

dialog {
    padding: 0
}

textarea {
    resize: vertical
}

input::-moz-placeholder,textarea::-moz-placeholder {
    opacity: 1;
    color: #9ca3af
}

input::placeholder,textarea::placeholder {
    opacity: 1;
    color: #9ca3af
}

button,[role=button] {
    cursor: pointer
}

:disabled {
    cursor: default
}

img,svg,video,canvas,audio,iframe,embed,object {
    display: block;
    vertical-align: middle
}

img,video {
    max-width: 100%;
    height: auto
}

[hidden] {
    display: none
}

*,:before,:after {
    --tw-border-spacing-x: 0;
    --tw-border-spacing-y: 0;
    --tw-translate-x: 0;
    --tw-translate-y: 0;
    --tw-rotate: 0;
    --tw-skew-x: 0;
    --tw-skew-y: 0;
    --tw-scale-x: 1;
    --tw-scale-y: 1;
    --tw-pan-x: ;
    --tw-pan-y: ;
    --tw-pinch-zoom: ;
    --tw-scroll-snap-strictness: proximity;
    --tw-gradient-from-position: ;
    --tw-gradient-via-position: ;
    --tw-gradient-to-position: ;
    --tw-ordinal: ;
    --tw-slashed-zero: ;
    --tw-numeric-figure: ;
    --tw-numeric-spacing: ;
    --tw-numeric-fraction: ;
    --tw-ring-inset: ;
    --tw-ring-offset-width: 0px;
    --tw-ring-offset-color: #fff;
    --tw-ring-color: rgb(59 130 246 / .5);
    --tw-ring-offset-shadow: 0 0 #0000;
    --tw-ring-shadow: 0 0 #0000;
    --tw-shadow: 0 0 #0000;
    --tw-shadow-colored: 0 0 #0000;
    --tw-blur: ;
    --tw-brightness: ;
    --tw-contrast: ;
    --tw-grayscale: ;
    --tw-hue-rotate: ;
    --tw-invert: ;
    --tw-saturate: ;
    --tw-sepia: ;
    --tw-drop-shadow: ;
    --tw-backdrop-blur: ;
    --tw-backdrop-brightness: ;
    --tw-backdrop-contrast: ;
    --tw-backdrop-grayscale: ;
    --tw-backdrop-hue-rotate: ;
    --tw-backdrop-invert: ;
    --tw-backdrop-opacity: ;
    --tw-backdrop-saturate: ;
    --tw-backdrop-sepia:
}

::backdrop {
    --tw-border-spacing-x: 0;
    --tw-border-spacing-y: 0;
    --tw-translate-x: 0;
    --tw-translate-y: 0;
    --tw-rotate: 0;
    --tw-skew-x: 0;
    --tw-skew-y: 0;
    --tw-scale-x: 1;
    --tw-scale-y: 1;
    --tw-pan-x: ;
    --tw-pan-y: ;
    --tw-pinch-zoom: ;
    --tw-scroll-snap-strictness: proximity;
    --tw-gradient-from-position: ;
    --tw-gradient-via-position: ;
    --tw-gradient-to-position: ;
    --tw-ordinal: ;
    --tw-slashed-zero: ;
    --tw-numeric-figure: ;
    --tw-numeric-spacing: ;
    --tw-numeric-fraction: ;
    --tw-ring-inset: ;
    --tw-ring-offset-width: 0px;
    --tw-ring-offset-color: #fff;
    --tw-ring-color: rgb(59 130 246 / .5);
    --tw-ring-offset-shadow: 0 0 #0000;
    --tw-ring-shadow: 0 0 #0000;
    --tw-shadow: 0 0 #0000;
    --tw-shadow-colored: 0 0 #0000;
    --tw-blur: ;
    --tw-brightness: ;
    --tw-contrast: ;
    --tw-grayscale: ;
    --tw-hue-rotate: ;
    --tw-invert: ;
    --tw-saturate: ;
    --tw-sepia: ;
    --tw-drop-shadow: ;
    --tw-backdrop-blur: ;
    --tw-backdrop-brightness: ;
    --tw-backdrop-contrast: ;
    --tw-backdrop-grayscale: ;
    --tw-backdrop-hue-rotate: ;
    --tw-backdrop-invert: ;
    --tw-backdrop-opacity: ;
    --tw-backdrop-saturate: ;
    --tw-backdrop-sepia:
}

.container {
    width: 100%
}

@media (min-width: 640px) {
    .container {
        max-width:640px
    }
}

@media (min-width: 768px) {
    .container {
        max-width:768px
    }
}

@media (min-width: 1024px) {
    .container {
        max-width:1024px
    }
}

@media (min-width: 1280px) {
    .container {
        max-width:1280px
    }
}

@media (min-width: 1536px) {
    .container {
        max-width:1536px
    }
}

.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0,0,0,0);
    white-space: nowrap;
    border-width: 0
}

.fixed {
    position: fixed
}

.absolute {
    position: absolute
}

.relative {
    position: relative
}

.sticky {
    position: sticky
}

.inset-\[-1000\%\] {
    inset: -1000%
}

.-left-\[42px\] {
    left: -42px
}

.bottom-0 {
    bottom: 0
}

.right-0 {
    right: 0
}

.top-0 {
    top: 0
}

.top-8 {
    top: 2rem
}

.z-10 {
    z-index: 10
}

.z-\[-2\] {
    z-index: -2
}

.order-1 {
    order: 1
}

.order-2 {
    order: 2
}

.col-span-6 {
    grid-column: span 6 / span 6
}

.row-span-5 {
    grid-row: span 5 / span 5
}

.m-0 {
    margin: 0
}

.m-4 {
    margin: 1rem
}

.mx-12 {
    margin-left: 3rem;
    margin-right: 3rem
}

.mx-auto {
    margin-left: auto;
    margin-right: auto
}

.mb-10 {
    margin-bottom: 2.5rem
}

.mb-2 {
    margin-bottom: .5rem
}

.mb-4 {
    margin-bottom: 1rem
}

.mb-6 {
    margin-bottom: 1.5rem
}

.me-4 {
    margin-inline-end:1rem}

.ml-1 {
    margin-left: .25rem
}

.mr-1 {
    margin-right: .25rem
}

.mt-16 {
    margin-top: 4rem
}

.mt-2 {
    margin-top: .5rem
}

.mt-3 {
    margin-top: .75rem
}

.mt-4 {
    margin-top: 1rem
}

.mt-6 {
    margin-top: 1.5rem
}

.mt-8 {
    margin-top: 2rem
}

.block {
    display: block
}

.inline {
    display: inline
}

.flex {
    display: flex
}

.inline-flex {
    display: inline-flex
}

.grid {
    display: grid
}

.hidden {
    display: none
}

.aspect-square {
    aspect-ratio: 1 / 1
}

.size-16 {
    width: 4rem;
    height: 4rem
}

.size-4 {
    width: 1rem;
    height: 1rem
}

.size-5 {
    width: 1.25rem;
    height: 1.25rem
}

.size-6 {
    width: 1.5rem;
    height: 1.5rem
}

.size-7 {
    width: 1.75rem;
    height: 1.75rem
}

.size-8 {
    width: 2rem;
    height: 2rem
}

.h-56 {
    height: 14rem
}

.h-full {
    height: 100%
}

.min-h-screen {
    min-height: 100vh
}

.w-5 {
    width: 1.25rem
}

.w-64 {
    width: 16rem
}

.w-full {
    width: 100%
}

.min-w-\[8rem\] {
    min-width: 8rem
}

.max-w-fit {
    max-width: -moz-fit-content;
    max-width: fit-content
}

.max-w-screen-xl {
    max-width: 1280px
}

.max-w-xl {
    max-width: 36rem
}

.rotate-3 {
    --tw-rotate: 3deg;
    transform: translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))
}

.transform {
    transform: translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))
}

@keyframes spin {
    to {
        transform: rotate(360deg)
    }
}

.animate-\[spin_2s_linear_infinite\] {
    animation: spin 2s linear infinite
}

.cursor-default {
    cursor: default
}

.cursor-pointer {
    cursor: pointer
}

.scroll-m-20 {
    scroll-margin: 5rem
}

.appearance-none {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none
}

.flex-row {
    flex-direction: row
}

.flex-col {
    flex-direction: column
}

.flex-wrap {
    flex-wrap: wrap
}

.items-end {
    align-items: flex-end
}

.items-center {
    align-items: center
}

.justify-start {
    justify-content: flex-start
}

.justify-center {
    justify-content: center
}

.gap-2 {
    gap: .5rem
}

.gap-4 {
    gap: 1rem
}

.gap-8 {
    gap: 2rem
}

.gap-x-2 {
    -moz-column-gap: .5rem;
    column-gap: .5rem
}

.gap-x-3 {
    -moz-column-gap: .75rem;
    column-gap: .75rem
}

.gap-x-4 {
    -moz-column-gap: 1rem;
    column-gap: 1rem
}

.gap-y-10 {
    row-gap: 2.5rem
}

.gap-y-16 {
    row-gap: 4rem
}

.space-x-0>:not([hidden])~:not([hidden]) {
    --tw-space-x-reverse: 0;
    margin-right: calc(0px * var(--tw-space-x-reverse));
    margin-left: calc(0px * calc(1 - var(--tw-space-x-reverse)))
}

.space-x-2>:not([hidden])~:not([hidden]) {
    --tw-space-x-reverse: 0;
    margin-right: calc(.5rem * var(--tw-space-x-reverse));
    margin-left: calc(.5rem * calc(1 - var(--tw-space-x-reverse)))
}

.space-y-24>:not([hidden])~:not([hidden]) {
    --tw-space-y-reverse: 0;
    margin-top: calc(6rem * calc(1 - var(--tw-space-y-reverse)));
    margin-bottom: calc(6rem * var(--tw-space-y-reverse))
}

.space-y-8>:not([hidden])~:not([hidden]) {
    --tw-space-y-reverse: 0;
    margin-top: calc(2rem * calc(1 - var(--tw-space-y-reverse)));
    margin-bottom: calc(2rem * var(--tw-space-y-reverse))
}

.overflow-hidden {
    overflow: hidden
}

.overflow-clip {
    overflow: clip
}

.whitespace-nowrap {
    white-space: nowrap
}

.text-pretty {
    text-wrap: pretty
}

.rounded-2xl {
    border-radius: 1rem
}

.rounded-full {
    border-radius: 9999px
}

.rounded-lg {
    border-radius: .5rem
}

.rounded-md {
    border-radius: .375rem
}

.rounded-sm {
    border-radius: .125rem
}

.rounded-xl {
    border-radius: .75rem
}

.border {
    border-width: 1px
}

.border-none {
    border-style: none
}

.border-gray-100 {
    --tw-border-opacity: 1;
    border-color: rgb(243 244 246 / var(--tw-border-opacity))
}

.border-gray-300 {
    --tw-border-opacity: 1;
    border-color: rgb(209 213 219 / var(--tw-border-opacity))
}

.bg-\[\#003159\] {
    --tw-bg-opacity: 1;
    background-color: rgb(0 49 89 / var(--tw-bg-opacity))
}

.bg-black {
    --tw-bg-opacity: 1;
    background-color: rgb(0 0 0 / var(--tw-bg-opacity))
}

.bg-black\/20 {
    background-color: #0003
}

.bg-gray-100 {
    --tw-bg-opacity: 1;
    background-color: rgb(243 244 246 / var(--tw-bg-opacity))
}

.bg-gray-50 {
    --tw-bg-opacity: 1;
    background-color: rgb(249 250 251 / var(--tw-bg-opacity))
}

.bg-green-100 {
    --tw-bg-opacity: 1;
    background-color: rgb(220 252 231 / var(--tw-bg-opacity))
}

.bg-white\/90 {
    background-color: #ffffffe6
}

.bg-\[conic-gradient\(from_90deg_at_50\%_50\%\,\#51E4B8_0\%\,\#21554E_50\%\,\#51E4B8_100\%\)\] {
    background-image: conic-gradient(from 90deg at 50% 50%,#51e4b8,#21554e,#51e4b8)
}

.bg-\[radial-gradient\(ellipse_80\%_80\%_at_50\%_-20\%\,rgba\(217\,216\,255\,0\.5\)\,rgba\(255\,255\,255\,0\.9\)\)\] {
    background-image: radial-gradient(ellipse 80% 80% at 50% -20%,#d9d8ff80,#ffffffe6)
}

.object-cover {
    -o-object-fit: cover;
    object-fit: cover
}

.object-top {
    -o-object-position: top;
    object-position: top
}

.p-0 {
    padding: 0
}

.p-1 {
    padding: .25rem
}

.p-\[1px\] {
    padding: 1px
}

.px-2 {
    padding-left: .5rem;
    padding-right: .5rem
}

.px-3 {
    padding-left: .75rem;
    padding-right: .75rem
}

.px-4 {
    padding-left: 1rem;
    padding-right: 1rem
}

.py-1 {
    padding-top: .25rem;
    padding-bottom: .25rem
}

.py-1\.5 {
    padding-top: .375rem;
    padding-bottom: .375rem
}

.py-16 {
    padding-top: 4rem;
    padding-bottom: 4rem
}

.py-2 {
    padding-top: .5rem;
    padding-bottom: .5rem
}

.py-4 {
    padding-top: 1rem;
    padding-bottom: 1rem
}

.py-44 {
    padding-top: 11rem;
    padding-bottom: 11rem
}

.pb-12 {
    padding-bottom: 3rem
}

.pb-32 {
    padding-bottom: 8rem
}

.pb-4 {
    padding-bottom: 1rem
}

.text-2xl {
    font-size: 1.5rem;
    line-height: 2rem
}

.text-3xl {
    font-size: 1.875rem;
    line-height: 2.25rem
}

.text-4xl {
    font-size: 2.25rem;
    line-height: 2.5rem
}

.text-5xl {
    font-size: 3rem;
    line-height: 1
}

.text-base {
    font-size: 1rem;
    line-height: 1.5rem
}

.text-lg {
    font-size: 1.125rem;
    line-height: 1.75rem
}

.text-sm {
    font-size: .875rem;
    line-height: 1.25rem
}

.text-xl {
    font-size: 1.25rem;
    line-height: 1.75rem
}

.text-xs {
    font-size: .75rem;
    line-height: 1rem
}

.font-bold {
    font-weight: 700
}

.font-medium {
    font-weight: 500
}

.font-semibold {
    font-weight: 600
}

.italic {
    font-style: italic
}

.tracking-tight {
    letter-spacing: -.025em
}

.text-black {
    --tw-text-opacity: 1;
    color: rgb(0 0 0 / var(--tw-text-opacity))
}

.text-black\/80 {
    color: #000c
}

.text-blue-500 {
    --tw-text-opacity: 1;
    color: rgb(59 130 246 / var(--tw-text-opacity))
}

.text-gray-600 {
    --tw-text-opacity: 1;
    color: rgb(75 85 99 / var(--tw-text-opacity))
}

.text-gray-600\/80 {
    color: #4b5563cc
}

.text-gray-700 {
    --tw-text-opacity: 1;
    color: rgb(55 65 81 / var(--tw-text-opacity))
}

.text-gray-800 {
    --tw-text-opacity: 1;
    color: rgb(31 41 55 / var(--tw-text-opacity))
}

.text-green-800 {
    --tw-text-opacity: 1;
    color: rgb(22 101 52 / var(--tw-text-opacity))
}

.text-white {
    --tw-text-opacity: 1;
    color: rgb(255 255 255 / var(--tw-text-opacity))
}

.text-yellow-400 {
    --tw-text-opacity: 1;
    color: rgb(250 204 21 / var(--tw-text-opacity))
}

.text-yellow-500 {
    --tw-text-opacity: 1;
    color: rgb(234 179 8 / var(--tw-text-opacity))
}

.text-zinc-800\/90 {
    color: #27272ae6
}

.opacity-80 {
    opacity: .8
}

.shadow-\[0_3px_10px_rgb\(0\,0\,0\,0\.2\)\] {
    --tw-shadow: 0 3px 10px rgb(0,0,0,.2);
    --tw-shadow-colored: 0 3px 10px var(--tw-shadow-color);
    box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000),var(--tw-ring-shadow, 0 0 #0000),var(--tw-shadow)
}

.shadow-lg {
    --tw-shadow: 0 10px 15px -3px rgb(0 0 0 / .1), 0 4px 6px -4px rgb(0 0 0 / .1);
    --tw-shadow-colored: 0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);
    box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000),var(--tw-ring-shadow, 0 0 #0000),var(--tw-shadow)
}

.shadow-xl {
    --tw-shadow: 0 20px 25px -5px rgb(0 0 0 / .1), 0 8px 10px -6px rgb(0 0 0 / .1);
    --tw-shadow-colored: 0 20px 25px -5px var(--tw-shadow-color), 0 8px 10px -6px var(--tw-shadow-color);
    box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000),var(--tw-ring-shadow, 0 0 #0000),var(--tw-shadow)
}

.ring-1 {
    --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
    --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(1px + var(--tw-ring-offset-width)) var(--tw-ring-color);
    box-shadow: var(--tw-ring-offset-shadow),var(--tw-ring-shadow),var(--tw-shadow, 0 0 #0000)
}

.ring-black\/70 {
    --tw-ring-color: rgb(0 0 0 / .7)
}

.blur {
    --tw-blur: blur(8px);
    filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow)
}

.backdrop-blur {
    --tw-backdrop-blur: blur(8px);
    -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
    backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)
}

.backdrop-blur-3xl {
    --tw-backdrop-blur: blur(64px);
    -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
    backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)
}

.backdrop-blur-md {
    --tw-backdrop-blur: blur(12px);
    -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
    backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)
}

.backdrop-filter {
    -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
    backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)
}

.transition {
    transition-property: color,background-color,border-color,text-decoration-color,fill,stroke,opacity,box-shadow,transform,filter,-webkit-backdrop-filter;
    transition-property: color,background-color,border-color,text-decoration-color,fill,stroke,opacity,box-shadow,transform,filter,backdrop-filter;
    transition-property: color,background-color,border-color,text-decoration-color,fill,stroke,opacity,box-shadow,transform,filter,backdrop-filter,-webkit-backdrop-filter;
    transition-timing-function: cubic-bezier(.4,0,.2,1);
    transition-duration: .15s
}

.transition-all {
    transition-property: all;
    transition-timing-function: cubic-bezier(.4,0,.2,1);
    transition-duration: .15s
}

.duration-500 {
    transition-duration: .5s
}

.ease-in-out {
    transition-timing-function: cubic-bezier(.4,0,.2,1)
}

.before\:absolute:before {
    content: var(--tw-content);
    position: absolute
}

.before\:left-\[-35px\]:before {
    content: var(--tw-content);
    left: -35px
}

.before\:block:before {
    content: var(--tw-content);
    display: block
}

.before\:h-full:before {
    content: var(--tw-content);
    height: 100%
}

.before\:border-l-2:before {
    content: var(--tw-content);
    border-left-width: 2px
}

.before\:border-black\/20:before {
    content: var(--tw-content);
    border-color: #0003
}

.before\:content-\[\'\'\]:before{--tw-content: "";content:var(--tw-content)}.hover\:scale-125:hover{--tw-scale-x: 1.25;--tw-scale-y: 1.25;transform:translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.hover\:border-gray-700:hover{--tw-border-opacity: 1;border-color:rgb(55 65 81 / var(--tw-border-opacity))}.hover\:border-gray-900:hover{--tw-border-opacity: 1;border-color:rgb(17 24 39 / var(--tw-border-opacity))}.hover\:bg-gray-800:hover{--tw-bg-opacity: 1;background-color:rgb(31 41 55 / var(--tw-bg-opacity))}.hover\:bg-gray-900:hover{--tw-bg-opacity: 1;background-color:rgb(17 24 39 / var(--tw-bg-opacity))}.hover\:bg-neutral-400\/40:hover{background-color:#a3a3a366}.hover\:text-blue-500:hover{--tw-text-opacity: 1;color:rgb(59 130 246 / var(--tw-text-opacity))}.hover\:text-white:hover{--tw-text-opacity: 1;color:rgb(255 255 255 / var(--tw-text-opacity))}.hover\:text-yellow-700:hover{--tw-text-opacity: 1;color:rgb(161 98 7 / var(--tw-text-opacity))}.hover\:underline:hover{text-decoration-line:underline}.focus\:outline-none:focus{outline:2px solid transparent;outline-offset:2px}.focus-visible\:outline-none:focus-visible{outline:2px solid transparent;outline-offset:2px}.focus-visible\:ring:focus-visible{--tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);--tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(3px + var(--tw-ring-offset-width)) var(--tw-ring-color);box-shadow:var(--tw-ring-offset-shadow),var(--tw-ring-shadow),var(--tw-shadow, 0 0 #0000)}.focus-visible\:ring-white:focus-visible{--tw-ring-opacity: 1;--tw-ring-color: rgb(255 255 255 / var(--tw-ring-opacity))}.focus-visible\:ring-yellow-500\/80:focus-visible{--tw-ring-color: rgb(234 179 8 / .8)}.focus-visible\:ring-offset-2:focus-visible{--tw-ring-offset-width: 2px}.active\:bg-black:active{--tw-bg-opacity: 1;background-color:rgb(0 0 0 / var(--tw-bg-opacity))}:is(.dark .dark\:border-gray-500\/20){border-color:#6b728033}:is(.dark .dark\:border-gray-600){--tw-border-opacity: 1;border-color:rgb(75 85 99 / var(--tw-border-opacity))}:is(.dark .dark\:bg-gray-800){--tw-bg-opacity: 1;background-color:rgb(31 41 55 / var(--tw-bg-opacity))}:is(.dark .dark\:bg-gray-800\/0){background-color:#1f293700}:is(.dark .dark\:bg-gray-800\/90){background-color:#1f2937e6}:is(.dark .dark\:bg-gray-900\/90){background-color:#111827e6}:is(.dark .dark\:bg-gray-950){--tw-bg-opacity: 1;background-color:rgb(3 7 18 / var(--tw-bg-opacity))}:is(.dark .dark\:bg-yellow-500\/5){background-color:#eab3080d}:is(.dark .dark\:bg-\[radial-gradient\(ellipse_80\%_80\%_at_50\%_-20\%\,rgba\(120\,119\,198\,0\.3\)\,rgba\(255\,255\,255\,0\)\)\]){background-image:radial-gradient(ellipse 80% 80% at 50% -20%,#7877c64d,#fff0)}:is(.dark .dark\:text-gray-100){--tw-text-opacity: 1;color:rgb(243 244 246 / var(--tw-text-opacity))}:is(.dark .dark\:text-gray-200){--tw-text-opacity: 1;color:rgb(229 231 235 / var(--tw-text-opacity))}:is(.dark .dark\:text-gray-300){--tw-text-opacity: 1;color:rgb(209 213 219 / var(--tw-text-opacity))}:is(.dark .dark\:text-gray-400){--tw-text-opacity: 1;color:rgb(156 163 175 / var(--tw-text-opacity))}:is(.dark .dark\:text-white){--tw-text-opacity: 1;color:rgb(255 255 255 / var(--tw-text-opacity))}:is(.dark .dark\:text-white\/80){color:#fffc}:is(.dark .dark\:text-white\/90){color:#ffffffe6}:is(.dark .dark\:text-yellow-200){--tw-text-opacity: 1;color:rgb(254 240 138 / var(--tw-text-opacity))}:is(.dark .dark\:text-zinc-200\/90){color:#e4e4e7e6}:is(.dark .dark\:ring-white\/20){--tw-ring-color: rgb(255 255 255 / .2)}:is(.dark .dark\:before\:border-white\/15):before{content:var(--tw-content);border-color:#ffffff26}:is(.dark .dark\:hover\:border-gray-300:hover){--tw-border-opacity: 1;border-color:rgb(209 213 219 / var(--tw-border-opacity))}:is(.dark .dark\:hover\:bg-gray-100:hover){--tw-bg-opacity: 1;background-color:rgb(243 244 246 / var(--tw-bg-opacity))}:is(.dark .dark\:hover\:bg-gray-500\/50:hover){background-color:#6b728080}:is(.dark .dark\:hover\:text-black:hover){--tw-text-opacity: 1;color:rgb(0 0 0 / var(--tw-text-opacity))}:is(.dark .dark\:hover\:text-blue-500:hover){--tw-text-opacity: 1;color:rgb(59 130 246 / var(--tw-text-opacity))}:is(.dark .dark\:hover\:text-yellow-300:hover){--tw-text-opacity: 1;color:rgb(253 224 71 / var(--tw-text-opacity))}@media (min-width: 375px){.min-\[375px\]\:pl-4{padding-left:1rem}}@media (min-width: 640px){.sm\:mt-0{margin-top:0}.sm\:h-full{height:100%}.sm\:rounded-xl{border-radius:.75rem}.sm\:text-center{text-align:center}.sm\:text-5xl{font-size:3rem;line-height:1}}@media (min-width: 768px){.md\:order-1{order:1}.md\:order-2{order:2}.md\:col-span-2{grid-column:span 2 / span 2}.md\:col-span-3{grid-column:span 3 / span 3}.md\:me-6{margin-inline-end:1.5rem}.md\:flex{display:flex}.md\:size-6{width:1.5rem;height:1.5rem}.md\:w-1\/2{width:50%}.md\:max-w-2xl{max-width:42rem}.md\:max-w-lg{max-width:32rem}.md\:scale-110{--tw-scale-x: 1.1;--tw-scale-y: 1.1;transform:translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.md\:grid-cols-5{grid-template-columns:repeat(5,minmax(0,1fr))}.md\:flex-row{flex-direction:row}.md\:items-center{align-items:center}.md\:justify-center{justify-content:center}.md\:justify-between{justify-content:space-between}.md\:gap-10{gap:2.5rem}.md\:space-x-4>:not([hidden])~:not([hidden]){--tw-space-x-reverse: 0;margin-right:calc(1rem * var(--tw-space-x-reverse));margin-left:calc(1rem * calc(1 - var(--tw-space-x-reverse)))}.md\:space-x-8>:not([hidden])~:not([hidden]){--tw-space-x-reverse: 0;margin-right:calc(2rem * var(--tw-space-x-reverse));margin-left:calc(2rem * calc(1 - var(--tw-space-x-reverse)))}.md\:space-y-0>:not([hidden])~:not([hidden]){--tw-space-y-reverse: 0;margin-top:calc(0px * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0px * var(--tw-space-y-reverse))}.md\:py-36{padding-top:9rem;padding-bottom:9rem}.md\:pl-0{padding-left:0}.md\:hover\:scale-105:hover{--tw-scale-x: 1.05;--tw-scale-y: 1.05;transform:translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.group:hover .md\:group-hover\:-translate-y-1{--tw-translate-y: -.25rem;transform:translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.group:hover .md\:group-hover\:scale-105{--tw-scale-x: 1.05;--tw-scale-y: 1.05;transform:translate(var(--tw-translate-x),var(--tw-translate-y)) rotate(var(--tw-rotate)) skew(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.group:hover .md\:group-hover\:shadow-2xl{--tw-shadow: 0 25px 50px -12px rgb(0 0 0 / .25);--tw-shadow-colored: 0 25px 50px -12px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000),var(--tw-ring-shadow, 0 0 #0000),var(--tw-shadow)}}@media (min-width: 1024px){.lg\:w-64{width:16rem}.lg\:max-w-4xl{max-width:56rem}.lg\:border{border-width:1px}.lg\:border-gray-800{--tw-border-opacity: 1;border-color:rgb(31 41 55 / var(--tw-border-opacity))}.lg\:p-2{padding:.5rem}.lg\:hover\:border-gray-700:hover{--tw-border-opacity: 1;border-color:rgb(55 65 81 / var(--tw-border-opacity))}.lg\:hover\:bg-gray-800\/50:hover{background-color:#1f293780}}.\[\&\>p\>strong\]\:font-mono>p>strong{font-family:ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,Liberation Mono,Courier New,monospace}.\[\&\>p\>strong\]\:font-normal>p>strong{font-weight:400}.\[\&\>p\>strong\]\:text-yellow-500>p>strong{--tw-text-opacity: 1;color:rgb(234 179 8 / var(--tw-text-opacity))}:is(.dark .dark\:\[\&\>p\>strong\]\:text-yellow-100>p>strong){--tw-text-opacity: 1;color:rgb(254 249 195 / var(--tw-text-opacity))}.\[\&\>p\]\:mb-4>p{margin-bottom:1rem}.\[\&\>strong\]\:font-semibold>strong{font-weight:600}.\[\&\>strong\]\:text-yellow-500>strong{--tw-text-opacity: 1;color:rgb(234 179 8 / var(--tw-text-opacity))}:is(.dark .dark\:\[\&\>strong\]\:text-yellow-200>strong){--tw-text-opacity: 1;color:rgb(254 240 138 / var(--tw-text-opacity))}@font-face{font-family:Onest Variable;font-style:normal;font-display:swap;font-weight:100 900;src:url(data:font/woff2;base64,d09GMgABAAAAAAikABQAAAAADtAAAAg5AAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGhYbchwuP0hWQVJ8P01WQVI5BmA/U1RBVIEeAFQvbBEICoUMhA8LFAAwh0IBNgIkAyIEIAWFUgdlDAcb2wxRlHLSTCh+JpgqYzdCr74T1zFPDeljyGrzJCL6Ev8bD9Fava+qe3dnZu8TYRBRRkWdCpCOBCJhosglnmB+fp3vJiXGXwdGMZ0w+x/Y23aEczWThqTNJjW8hoicA6eO+L2oNF/ezlXBg1dQQRzciijV+BogZE/7tcrgVbTzMA0JUqWU99sevg1ROdGGhMSFRKWb7SFuSTKXaTxVNWQt4oUcFJHOcfztJwpMAFIIRQh0NtqvHHs8KUI6P+tvSN/b5hfSKnw6zG65Tv9ChClClRyg2f98xwIbLRcSTENItK/y7DZks80Z85XYtScLsB4BBMzQ5NT5aRoDQxMCxwrgEGzCUswXcBgPy0u/KUjEj8dZL+8xCYRYL+RHPgJHGlBAYzk7X91NAC4lYvTFq/YZItQ8JiYNyMczEzglmDgu1/Q3SpwjpG9/5vIC/Bw1r5Xb/z+gvhdTgCchp+WnWK4VQiMwW4vF8oEb7iaRmGmpjfY6Hm/ryUZAFNcCJqz6KmAQm1FsM4YxSb4nqBzFrxDW5IVDW2FYV5a3j8tjnBRK62xFBAHVkQeb0EjVUf6R9ZPlR/sezvNj9/qP+uF9dI9LzgYCrRaYLoXZWs0pm8EZxCQ77hUZhcT6FV8RA2IzMRTLGAF+NW/IC0G0J7xEdJTlxFjxoUL0/aaBFszEGK/jFyzG7F5mT1IWnnHsWpvysG5qN+1wWpWlEOTvCAqefEo+5tL51Awhm+QUTVlERij/2khmFpfNUZyMy/x19vPLJrLuFplzx4usvfiU5KSTNIIESAZJlaZL54BDLvXTolW7jhUlJ/boC/E2r3f/Moob9BwOt8yhsOIIrtl/m5t99aQHt+HKgxdkzrN7h8C8dqcLAS6VAL90JZjP3SJzTpxR+eXdp/kZJDV/9vP0A9iRc2B1S3WtovRJKXDM5d+dLucPWGFtJ7XKf9ECUF5473zeWztTPhmeMfwzT+THZrn43gebYz+Ly4j7DK7BeYtz/ATjbP0UrSo0VKWdQlZPNILyuPOOrrzlFcOlNGm4EXnAcb13l5ZPqkirmIRFXF68UPyyzswtb57BMO9zpvqxgWzQWM13JJT/5quUqb9+N6Nh6tSOJoPqVZyvLvSLP3Mzfr46ThMUMFrzXleofju3ZtTU2d/N6J+a8eNqre9Ys8nQNXROVvqPh8arIOjd1Lm5784FyJyaORJT9o9bDbagAgEBgAUWp8J+DvKlj0YDAHAA1FLZhqB9MSDAZyx2MCgAAIoBSH/cwTAOtiHgAtyMd1LgIpgR5MADgEgHB0PtL8JXmANmCnjwAAQDAPCM643XbH/Jy4eCA0rFAidCoKxMZ+EbmeGpDnp4Wl6NP4wWzYgoOt29C97eFosOGB2T/TEihQ2lyAD6jUZW4GX1RkxSvw0AQQzLPKvWaCRJ7e2gQn93n2MnKH3SxbB9XY8L27r63Lw7muvs0CpasL5edGIUoKurqNUHo9GVVyj6ukn0TWcU3IwWxt5enzUiJGQ4/Av/4mcZI+A6nIIrmPY1r3NJz5eTnTp68KCff/osZyKu8/lbkAIHRTMREKOj620IIr55I2rfFEJhodTOsoKKhIC1HVKh5fCRjpnqEKaDff2CkNJSF21lc5Wn23BmQp4/aZERuv9Fkb29pbGLaOul4kqwimZAER0OJwWgiC4uostcoNNp6P7+9tb2dsOwbVqjsxDr8bIhHYh5eR/5/J4C2w3favObEyLixKgQT55MnjR2SJS/m0o5dcrIBMgXLRgaKmKMAnzyRHRRwMOHz2t7eqDQNC0DLKt9/vDQ8Q9mu0ju4N01cpYl7gzTG487EvR6nYYGWUdtpcrFTcP0dbU006zlj5+0tXaeb221Vxaaayqvs9r6tO62GqmKckCPKBrabbX2ZlalkiSdzuHoVeu8g8KMMjQoMNBLw/5llDEcoVutaZawTE+lkjdYKwtfkIvnL1+/rmjqLkhm5H22UtNUZLX2n3GkwyZQSx0y1jMsqvBlWZOMkbsFJ2DXYeOnxMYO+x2LBg4YBDcVILBOrVJJ3MA4P0oNJjEZsR9ZlYebWh0R0d3t6enRIT08ud/EPHnzZkk7JdN3orubKI27TreIF+qp1VpD4NAZmWiZNS0lJczZCfBRBq/iAUDmJlQ4LDK6rY12w682zyCiaG1ekRS+8L0Gs+Bh8mhsp6BXoaqRyh0WpZ+fHLGboqhuRMbNzyJTNBaXepvU0FRe6u2jI6aopoZqCo1eJIzeeytbaixwCQRH/bPf7lSH/taU8jN8v2bNXPhpaUjp0/5/OF5XPsJQguCbLMePSjxuOhHIusnFZvcLOidWuVQq//pvp6nRf9enIdDmURIuFdDJKVnJTN+HFrXFE5FfUejiXEpT43gqttdcqhb6lwYO+oSGFnoxcqq97k4UacL1VDQup2q2k2mgc+SQ4c5ljBR8dlNjutXUaiymzkzd1cc6HO3t4ORlymXSHYxgb+dgsODi48GCwllYKYnEcTd3pop9olh0Zzq/FBfQHK2MrTK0bJvrHie6B5WJuioWP7yDs99Bd1NzhhkS4+vCYKo428WNdfjFOpnL0dcuhH0hO2y1fU59iBtcmXDzm2GVKN7qgKPbhUMvU84EOSpN7pkWeIL2gThy9mLbMUzl0S9BM7LTdqd0h+WXaOwFOhi9M+mwJ9brVHoU68Ll4BN1jqy/iAx4NN9Zjn3zNbBPCvdwUKo6nH5lzR07qi1IlGX/up0O2GK1ryOjRI1BDGM0POrqv72wCN93+6O++5iYzDPWzeb2o+Pbq66xzMvvzzCvpefZtX3vW9H/90t1Hg==) format("woff2-variations");unicode-range:U+0460-052F,U+1C80-1C88,U+20B4,U+2DE0-2DFF,U+A640-A69F,U+FE2E-FE2F}@font-face{font-family:Onest Variable;font-style:normal;font-display:swap;font-weight:100 900;src:url(/_astro/onest-cyrillic-wght-normal.okE7jKFK.woff2) format("woff2-variations");unicode-range:U+0301,U+0400-045F,U+0490-0491,U+04B0-04B1,U+2116}@font-face{font-family:Onest Variable;font-style:normal;font-display:swap;font-weight:100 900;src:url(/_astro/onest-latin-ext-wght-normal.NATBPiDw.woff2) format("woff2-variations");unicode-range:U+0100-02AF,U+0304,U+0308,U+0329,U+1E00-1E9F,U+1EF2-1EFF,U+2020,U+20A0-20AB,U+20AD-20CF,U+2113,U+2C60-2C7F,U+A720-A7FF}@font-face{font-family:Onest Variable;font-style:normal;font-display:swap;font-weight:100 900;src:url(/_astro/onest-latin-wght-normal.ycwkluYs.woff2) format("woff2-variations");unicode-range:U+0000-00FF,U+0131,U+0152-0153,U+02BB-02BC,U+02C6,U+02DA,U+02DC,U+0304,U+0308,U+0329,U+2000-206F,U+2074,U+20AC,U+2122,U+2191,U+2193,U+2212,U+2215,U+FEFF,U+FFFD}#themes-menu[data-astro-cid-x3pjskd3].open{display:inline;animation:scale-up-center .15s cubic-bezier(.25,.46,.45,.94) both}@keyframes scale-up-center{0%{transform:scale(.8);opacity:0}to{transform:scale(1);opacity:1}}@keyframes astroFadeInOut{0%{opacity:1}to{opacity:0}}@keyframes astroFadeIn{0%{opacity:0}}@keyframes astroFadeOut{to{opacity:0}}@keyframes astroSlideFromRight{0%{transform:translate(100%)}}@keyframes astroSlideFromLeft{0%{transform:translate(-100%)}}@keyframes astroSlideToRight{to{transform:translate(100%)}}@keyframes astroSlideToLeft{to{transform:translate(-100%)}}@media (prefers-reduced-motion){::view-transition-group(*),::view-transition-old(*),::view-transition-new(*){animation:none!important}[data-astro-transition-scope]{animation:none!important}}nav[data-astro-cid-3ef6ksr2]{animation:nav-shadown 1s linear both;animation-timeline:scroll();animation-range:0 100px;background-color:#ffffff80}:is(.dark nav)[data-astro-cid-3ef6ksr2]{background-color:#1f2937e6}@keyframes nav-shadown{0% {background-color: rgb(255 255 255 / 0);} :is(.dark 0%) {background-color: rgb(31 41 55 / 0);} to { --tw-shadow: 0 10px 15px -3px rgb(0 0 0 / .1), 0 4px 6px -4px rgb(0 0 0 / .1); --tw-shadow-colored: 0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color); box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow); --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color); --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(1px + var(--tw-ring-offset-width)) var(--tw-ring-color); box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000); --tw-ring-color: rgb(255 255 255 / .1); --tw-backdrop-blur: blur(8px); -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia); backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia); }}.astro-route-announcer{position:absolute;left:0;top:0;clip:rect(0 0 0 0);-webkit-clip-path:inset(50%);clip-path:inset(50%);overflow:hidden;white-space:nowrap;width:1px;height:1px}:root{color-scheme:light dark}html{font-family:Onest Variable,system-ui,sans-serif;scroll-behavior:smooth}body{color:#111111e6;display:flex;flex-direction:column;min-height:100vh;overscroll-behavior:none}@media (prefers-reduced-motion: reduce){html{scroll-behavior:auto}}@media (prefers-color-scheme: dark){body{color:#ffffffe6}}#header-nav{animation:blur linear both .5s;animation-timeline:scroll();animation-range:0 500px}@keyframes blur{to{-webkit-backdrop-filter:blur(20px);backdrop-filter:blur(20px);border-width:1px;border-color:#000;padding:.25rem .75rem;display:flex;flex-direction:row;align-items:center;background-color:#e5e5e5;border-radius:9999px}}@media (prefers-color-scheme: dark){@keyframes blur{0%{border:0px}to{box-shadow:0 5px 50px -5px #0000001a,0 0 0 1px #0000004d;background:#0000004d;-webkit-backdrop-filter:blur(20px);backdrop-filter:blur(20px);border-width:1px;border-color:#000;padding:.25rem .75rem;display:flex;flex-direction:row;align-items:center;background-color:#0000004d;border-radius:9999px}}}
              </style>