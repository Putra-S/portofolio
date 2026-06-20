<template>
    <section id="hero" class="relative min-h-[90vh] flex items-center justify-center pt-24 pb-20 px-6 lg:px-20 overflow-hidden">
        <div class="absolute inset-0 -z-10 overflow-hidden bg-gray-50 dark:bg-gray-900">
            <div class="absolute top-0 right-0 w-[800px] h-[800px] rounded-full blur-3xl opacity-30 dark:opacity-10 animate-pulse-slow" style="background: radial-gradient(circle, rgb(238, 239, 175) 0%, rgb(195, 227, 250) 100%)"></div>
            <div class="absolute bottom-0 left-0 w-[600px] h-[600px] bg-primary/20 rounded-full blur-3xl opacity-20"></div>
        </div>

        <div class="container mx-auto flex flex-col-reverse md:flex-row items-center justify-between z-10">
            <div class="md:w-1/2 text-center md:text-left mt-12 md:mt-0">
                <div class="inline-block px-4 py-1.5 mb-6 rounded-full bg-blue-100 text-primary dark:bg-primary/20 dark:text-blue-300 font-medium text-sm animate-fade-up" style="animation-delay: 0.1s">🚀 Siap untuk Freelance & Kolaborasi</div>

                <h1 class="text-5xl lg:text-7xl font-bold text-gray-900 dark:text-white leading-tight mb-6 animate-fade-up" style="animation-delay: 0.2s">
                    Halo, Saya <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-blue-600">Ma'ruf Putra</span> <span class="animate-wave inline-block">👋</span>
                    <br />
                    <span class="text-3xl lg:text-5xl font-light text-gray-600 dark:text-gray-400">Fullstack Developer</span>
                </h1>

                <p class="text-lg md:text-xl text-gray-600 dark:text-gray-300 max-w-lg mx-auto md:mx-0 leading-relaxed animate-fade-up" style="animation-delay: 0.3s">
                    Saya membangun aplikasi web yang efisien, aman, dan mudah diskalakan untuk memecahkan masalah nyata. Memiliki spesialisasi dalam pengembangan
                    <span class="font-semibold text-gray-900 dark:text-white">Sistem Informasi Rumah Sakit</span> & <span class="font-semibold text-gray-900 dark:text-white">Solusi Bisnis</span>.
                </p>

                <div class="flex flex-wrap gap-3 justify-center md:justify-start mt-6 animate-fade-up" style="animation-delay: 0.4s">
                    <span class="tech-badge"><i class="pi pi-check-circle mr-2"></i>Vue.js</span>
                    <span class="tech-badge"><i class="pi pi-server mr-2"></i>Express.js</span>
                    <span class="tech-badge"><i class="pi pi-database mr-2"></i>MySQL</span>
                </div>

                <div class="flex flex-col sm:flex-row gap-4 mt-10 justify-center md:justify-start animate-fade-up" style="animation-delay: 0.5s">
                    <Button
                        label="Lihat Proyek"
                        icon="pi pi-arrow-down"
                        iconPos="right"
                        @click="$emit('scrollTo', 'projects')"
                        class="p-button-rounded !px-8 !py-3 !text-lg !font-bold shadow-lg hover:shadow-primary/50 transition-all transform hover:-translate-y-1"
                    />
                    <Button label="Hubungi Saya" outlined class="p-button-rounded p-button-secondary !px-8 !py-3 !text-lg !font-bold hover:bg-gray-100 dark:hover:bg-gray-800 transition-all" @click="$emit('scrollTo', 'contact')" />
                </div>

                <div class="mt-8 flex gap-6 justify-center md:justify-start text-gray-500 animate-fade-up" style="animation-delay: 0.6s">
                    <a href="#" class="hover:text-primary transition-colors"><i class="pi pi-github text-2xl"></i></a>
                    <a href="#" class="hover:text-primary transition-colors"><i class="pi pi-linkedin text-2xl"></i></a>
                    <a href="#" class="hover:text-primary transition-colors"><i class="pi pi-envelope text-2xl"></i></a>
                </div>
            </div>

            <div class="md:w-1/2 flex justify-center md:justify-end relative animate-fade-in-right" style="animation-delay: 0.4s">
                <div class="absolute inset-0 bg-gradient-to-tr from-blue-200 to-yellow-100 rounded-full blur-2xl transform rotate-6 scale-90 opacity-60 -z-10"></div>

                <div class="bg-gray-900 rounded-xl shadow-2xl overflow-hidden w-full max-w-md border border-gray-700 transform rotate-2 hover:rotate-0 transition-all duration-500">
                    <div class="bg-gray-800 px-4 py-3 flex items-center gap-2 border-b border-gray-700">
                        <div class="w-3 h-3 rounded-full bg-red-500"></div>
                        <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                        <div class="w-3 h-3 rounded-full bg-green-500"></div>
                        <span class="ml-2 text-xs text-gray-400 font-mono">putra.dev — portfolio</span>
                    </div>
                    <div class="p-6 font-mono text-sm leading-relaxed text-gray-300">
                        <div class="flex">
                            <span class="text-gray-600 mr-4 select-none">1</span>
                            <span class="text-purple-400">const</span> <span class="text-yellow-300">developer</span> = {
                        </div>
                        <div class="flex">
                            <span class="text-gray-600 mr-4 select-none">2</span>
                            &nbsp;&nbsp;name: <span class="text-green-400">'Ma\'ruf Putra'</span>,
                        </div>
                        <div class="flex">
                            <span class="text-gray-600 mr-4 select-none">3</span>
                            &nbsp;&nbsp;skills: [<span class="text-green-400">'Vue'</span>, <span class="text-green-400">'Express'</span>, <span class="text-green-400">'MySQL'</span>],
                        </div>
                        <div class="flex">
                            <span class="text-gray-600 mr-4 select-none">4</span>
                            &nbsp;&nbsp;passion: <span class="text-green-400">'Clean Code'</span>,
                        </div>
                        <div class="flex">
                            <span class="text-gray-600 mr-4 select-none">5</span>
                            &nbsp;&nbsp;status: <span class="text-blue-400">true</span>
                        </div>
                        <div class="flex">
                            <span class="text-gray-600 mr-4 select-none">6</span>
                            };
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
/* Custom Utility Classes for Animation */
.tech-badge {
    @apply px-4 py-2 bg-white dark:bg-gray-800 border border-gray-200 dark:border-gray-700 rounded-lg text-sm font-semibold text-gray-700 dark:text-gray-300 shadow-sm flex items-center;
}

/* Animations */
@keyframes fade-up {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
.animate-fade-up {
    opacity: 0; /* Start hidden */
    animation: fade-up 0.8s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
}

@keyframes fade-in-right {
    from {
        opacity: 0;
        transform: translateX(50px);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}
.animate-fade-in-right {
    opacity: 0;
    animation: fade-in-right 1s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
}

@keyframes wave {
    0% {
        transform: rotate(0deg);
    }
    10% {
        transform: rotate(14deg);
    }
    20% {
        transform: rotate(-8deg);
    }
    30% {
        transform: rotate(14deg);
    }
    40% {
        transform: rotate(-4deg);
    }
    50% {
        transform: rotate(10deg);
    }
    60% {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(0deg);
    }
}
.animate-wave {
    animation: wave 2s infinite;
    transform-origin: 70% 70%;
}

@keyframes pulse-slow {
    0%,
    100% {
        opacity: 0.3;
        transform: scale(1);
    }
    50% {
        opacity: 0.4;
        transform: scale(1.05);
    }
}
.animate-pulse-slow {
    animation: pulse-slow 6s ease-in-out infinite;
}
</style>
