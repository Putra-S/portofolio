<script setup>
import { ref } from 'vue';

const skillCategories = ref([
    {
        title: 'Ekosistem Frontend',
        icon: 'pi pi-desktop',
        color: 'blue',
        description: 'Membangun antarmuka yang responsif, interaktif, dan terstruktur rapi.',
        skills: ['Vue 3 (Composition API)', 'PrimeVue & Tailwind CSS', 'Vite & Build Tools', 'Responsive Web Design (CSS Print)']
    },
    {
        title: 'Rekayasa Backend',
        icon: 'pi pi-server',
        color: 'emerald',
        description: 'Merancang arsitektur API berkinerja tinggi, aman, dan patuh regulasi.',
        skills: ['Node.js (Express.js) & Bun Runtime', 'Bridging API BPJS & SatuSehat HL7 FHIR', 'REST API & Socket.io (WebSocket)', 'AES-256 DB Encryption & JWT']
    },
    {
        title: 'DevOps & Infrastruktur',
        icon: 'pi pi-cloud',
        color: 'purple',
        description: 'Manajemen server, otomatisasi deploy, keamanan, dan keandalan sistem.',
        skills: ['Cloudflare (DNS, Load Balancing, WAF)', 'aaPanel, PM2, & Docker Deployment', 'Mikrotik RouterOS & WireGuard VPN', 'Orthanc DICOM / PACS Server', 'MySQL / PostgreSQL Database']
    }
]);

// Helper untuk styling dinamis berdasarkan warna kategori
const getColorStyle = (color) => {
    const styles = {
        blue: { bg: 'bg-blue-50 dark:bg-blue-900/20', text: 'text-blue-600 dark:text-blue-400', border: 'hover:border-blue-400', icon: 'bg-blue-100 text-blue-600' },
        emerald: { bg: 'bg-emerald-50 dark:bg-emerald-900/20', text: 'text-emerald-600 dark:text-emerald-400', border: 'hover:border-emerald-400', icon: 'bg-emerald-100 text-emerald-600' },
        purple: { bg: 'bg-purple-50 dark:bg-purple-900/20', text: 'text-purple-600 dark:text-purple-400', border: 'hover:border-purple-400', icon: 'bg-purple-100 text-purple-600' }
    };
    return styles[color];
};
</script>

<template>
    <section id="skills" class="py-24 px-6 lg:px-20 relative overflow-hidden">
        <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[500px] bg-primary/5 rounded-full blur-3xl -z-10"></div>

        <div class="container mx-auto">
            <div class="text-center mb-16" data-aos="fade-down">
                <span class="text-primary font-semibold tracking-wider uppercase text-sm">Keahlian</span>
                <h2 class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mt-2 mb-4">Keahlian Teknis</h2>
                <p class="text-lg text-gray-600 dark:text-gray-400 max-w-2xl mx-auto">Kombinasi teknologi yang saya gunakan untuk membangun sistem handal, mulai dari tampilan depan hingga infrastruktur server.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div
                    v-for="(category, index) in skillCategories"
                    :key="index"
                    class="group relative bg-white dark:bg-surface-900 p-8 rounded-2xl shadow-sm hover:shadow-xl border border-gray-100 dark:border-gray-800 transition-all duration-300 transform hover:-translate-y-2"
                    :class="getColorStyle(category.color).border"
                    data-aos="fade-up"
                    :data-aos-delay="index * 100"
                >
                    <div class="mb-6 inline-flex items-center justify-center w-16 h-16 rounded-xl transition-colors duration-300" :class="getColorStyle(category.color).bg">
                        <i :class="[category.icon, getColorStyle(category.color).text]" class="text-3xl"></i>
                    </div>

                    <h3 class="text-2xl font-bold text-gray-900 dark:text-white mb-3 group-hover:text-primary transition-colors">
                        {{ category.title }}
                    </h3>
                    <p class="text-gray-600 dark:text-gray-400 mb-8 leading-relaxed h-16">
                        {{ category.description }}
                    </p>

                    <ul class="space-y-3">
                        <li v-for="(skill, idx) in category.skills" :key="idx" class="flex items-center text-gray-700 dark:text-gray-300">
                            <span class="w-6 h-6 rounded-full flex items-center justify-center mr-3 bg-gray-100 dark:bg-gray-800 group-hover:scale-110 transition-transform">
                                <i class="pi pi-check text-xs font-bold" :class="getColorStyle(category.color).text"></i>
                            </span>
                            <span class="font-medium text-sm lg:text-base">{{ skill }}</span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
/* Opsional: Jika ingin efek glassmorphism yang lebih kuat */
.glass-effect {
    backdrop-filter: blur(10px);
    background: rgba(255, 255, 255, 0.7);
}
.dark .glass-effect {
    background: rgba(30, 41, 59, 0.7);
}
</style>
