<script setup>
const currentYear = new Date().getFullYear();

// Data Sosial Media dipisah agar bisa dipakai ulang (DRY Principle)
const socialLinks = [
    { name: 'GitHub', url: 'https://github.com/Putra-S', icon: 'pi pi-github', color: 'hover:text-gray-900 dark:hover:text-white' },
    { name: 'LinkedIn', url: 'https://www.linkedin.com/in/ma-ruf-putra-s-901908328/', icon: 'pi pi-linkedin', color: 'hover:text-blue-600' },
    { name: 'WhatsApp', url: 'https://wa.me/6285232406085', icon: 'pi pi-whatsapp', color: 'hover:text-green-500' }
];

const footerLinks = [
    {
        title: 'Navigasi',
        items: [
            { label: 'Beranda', action: () => window.scrollTo({ top: 0, behavior: 'smooth' }) },
            { label: 'Tentang', action: () => document.getElementById('about')?.scrollIntoView({ behavior: 'smooth' }) },
            { label: 'Proyek', action: () => document.getElementById('highlights')?.scrollIntoView({ behavior: 'smooth' }) },
            { label: 'Keahlian', action: () => document.getElementById('skills')?.scrollIntoView({ behavior: 'smooth' }) }
        ]
    },
    {
        title: 'Hubungi Saya',
        items: socialLinks.map((link) => ({ label: link.name, url: link.url }))
    },
    {
        title: 'Kontak',
        items: [
            { label: 'marufp1605@gmail.com', url: 'mailto:marufp1605@gmail.com', icon: 'pi pi-envelope' },
            { label: 'Unduh CV', action: () => window.open('/files/Putra-CV.pdf', '_blank'), icon: 'pi pi-download' }
        ]
    }
];

function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
}
</script>

<template>
    <footer id="contact" class="bg-gray-50 dark:bg-surface-900 border-t border-surface-200 dark:border-surface-800 pt-20 pb-10 px-6 lg:px-20 mt-20 relative overflow-hidden">
        <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-1 bg-gradient-to-r from-transparent via-primary/50 to-transparent opacity-50"></div>

        <div class="container mx-auto">
            <div class="grid grid-cols-1 md:grid-cols-12 gap-12 lg:gap-16">
                <div class="col-span-12 md:col-span-5 lg:col-span-4 flex flex-col justify-between">
                    <div>
                        <a @click="scrollToTop" class="flex items-center gap-3 mb-6 group cursor-pointer w-fit">
                            <div
                                class="w-10 h-10 bg-white dark:bg-surface-800 shadow-sm border border-surface-200 dark:border-surface-700 rounded-lg flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-white transition-all duration-300 group-hover:rotate-6"
                            >
                                <i class="pi pi-code text-xl font-bold"></i>
                            </div>
                            <span class="text-2xl font-bold text-gray-900 dark:text-white group-hover:text-primary transition-colors"> Putra<span class="text-primary">.dev</span> </span>
                        </a>

                        <p class="text-gray-600 dark:text-gray-400 leading-relaxed mb-8 max-w-sm">
                            Membangun <strong>Sistem Informasi Manajemen Rumah Sakit (SIMRS)</strong> yang andal & solusi layanan kesehatan digital. Mari sederhanakan kompleksitas.
                        </p>

                        <div class="flex gap-3">
                            <a
                                v-for="(social, index) in socialLinks"
                                :key="index"
                                :href="social.url"
                                target="_blank"
                                :class="`w-10 h-10 rounded-full bg-white dark:bg-surface-800 border border-gray-200 dark:border-surface-700 flex items-center justify-center text-gray-500 transition-all duration-300 hover:-translate-y-1 hover:shadow-md ${social.color}`"
                            >
                                <i :class="social.icon + ' text-lg'"></i>
                            </a>
                        </div>
                    </div>
                </div>

                <div class="col-span-12 md:col-span-7 lg:col-span-8 grid grid-cols-2 md:grid-cols-3 gap-8 lg:gap-12">
                    <div v-for="(section, index) in footerLinks" :key="index">
                        <h4 class="font-bold text-lg text-gray-900 dark:text-white mb-6 tracking-wide">{{ section.title }}</h4>
                        <ul class="space-y-4">
                            <li v-for="(link, i) in section.items" :key="i">
                                <a v-if="link.url" :href="link.url" target="_blank" class="text-gray-600 dark:text-gray-400 hover:text-primary dark:hover:text-primary transition-colors cursor-pointer flex items-center gap-2 group w-fit">
                                    <i v-if="link.icon" :class="link.icon" class="text-sm opacity-70 group-hover:opacity-100"></i>
                                    <span>{{ link.label }}</span>
                                    <i v-if="!link.icon" class="pi pi-arrow-up-right text-[10px] opacity-0 -ml-2 group-hover:opacity-50 group-hover:ml-0 transition-all"></i>
                                </a>

                                <a v-else @click="link.action" class="text-gray-600 dark:text-gray-400 hover:text-primary dark:hover:text-primary transition-colors cursor-pointer inline-block hover:translate-x-1 duration-200">
                                    {{ link.label }}
                                </a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>

            <div class="border-t border-gray-200 dark:border-gray-800 mt-16 pt-8 flex flex-col-reverse md:flex-row justify-between items-center gap-6">
                <div class="flex flex-col md:flex-row items-center gap-2 text-sm text-gray-500">
                    <span>&copy; {{ currentYear }} Putra. Hak Cipta Dilindungi.</span>
                    <span class="hidden md:inline text-gray-300">|</span>
                    <span class="flex items-center gap-1"> Dibuat dengan <i class="pi pi-heart-fill text-red-500 text-xs animate-pulse"></i> menggunakan Vue 3 </span>
                </div>

                <button @click="scrollToTop" class="group flex items-center gap-2 text-sm font-semibold text-gray-500 hover:text-primary transition-colors">
                    Kembali ke Atas
                    <span class="w-8 h-8 rounded-full bg-gray-100 dark:bg-surface-800 flex items-center justify-center group-hover:-translate-y-1 transition-transform duration-300">
                        <i class="pi pi-arrow-up text-xs"></i>
                    </span>
                </button>
            </div>
        </div>
    </footer>
</template>
