<script setup>
import { ref } from 'vue';

const projects = ref([
    {
        title: 'Custom SIMRS & Bridging System',
        description:
            'Sistem Informasi Manajemen Rumah Sakit (SIMRS) yang dirancang untuk mengintegrasikan seluruh layanan klinis dan administratif secara real-time. Sistem ini terhubung langsung dengan layanan eksternal penting seperti BPJS Kesehatan (VClaim, Antrean Online JKN, iCare), E-Klaim Kemenkes untuk efisiensi klaim asuransi, kepatuhan integrasi data SATUSEHAT berbasis standar HL7 FHIR, serta integrasi PACS/DICOM Orthanc untuk visualisasi pencitraan medis (radiologi).',
        image: '/projects/simrs.png',
        color: 'blue',
        icon: 'pi pi-hospital',
        tech: ['Vue 3', 'Express.js', 'SatuSehat HL7 FHIR', 'Bridging BPJS', 'Orthanc PACS']
    },
    {
        title: 'Custom Pengembangan SIMRS Khanza',
        description:
            'Modifikasi tingkat lanjut dan pengembangan modul khusus untuk SIMRS Khanza guna menyesuaikan dengan kebutuhan operasional spesifik rumah sakit. Mencakup implementasi Rekam Medis Elektronik (RME) yang komprehensif, modul bridging e-resep farmasi, manajemen sistem antrean pasien otomatis, pembuatan laporan analitis kustom menggunakan JasperReports, serta optimalisasi struktur query dan database MariaDB untuk kecepatan transaksi data.',
        image: '/projects/khanza.png',
        color: 'emerald',
        icon: 'pi pi-cog',
        tech: ['Java (Swing)', 'MariaDB', 'JasperReports', 'NetBeans IDE', 'REST API']
    },
    {
        title: 'IT Helpdesk & Ticketing System',
        description:
            'Sistem manajemen tiket gangguan dan layanan IT internal rumah sakit yang dibangun menggunakan runtime modern Bun untuk memastikan latensi rendah dan throughput tinggi. Aplikasi ini dilengkapi fitur keamanan tingkat tinggi dengan enkripsi database AES-256 untuk melindungi data kredensial sensitif, sistem notifikasi otomatis, serta dideploy menggunakan aaPanel dan PM2 untuk stabilitas layanan 24/7.',
        image: '/projects/helpdesk.png',
        color: 'purple',
        icon: 'pi pi-ticket',
        tech: ['Bun', 'Express.js', 'AES-256 Encryption', 'aaPanel', 'PM2']
    }
]);

// Helper untuk warna dinamis
const getColorClasses = (color) => {
    const map = {
        blue: 'bg-blue-100 text-blue-600 ring-blue-200',
        emerald: 'bg-emerald-100 text-emerald-600 ring-emerald-200',
        purple: 'bg-purple-100 text-purple-600 ring-purple-200'
    };
    return map[color] || map.blue;
};
</script>

<template>
    <div id="highlights" class="py-20 px-6 lg:px-20 bg-surface-50 dark:bg-surface-900 overflow-hidden">
        <div class="text-center mb-16" data-aos="fade-up">
            <h2 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">Featured Projects</h2>
            <p class="text-xl text-gray-600 dark:text-gray-400 max-w-2xl mx-auto">Solusi digital yang telah saya bangun untuk memecahkan masalah nyata di industri kesehatan dan bisnis.</p>
        </div>

        <div class="flex flex-col gap-24">
            <div v-for="(project, index) in projects" :key="index" class="flex flex-col lg:flex-row items-center gap-12" :class="{ 'lg:flex-row-reverse': index % 2 !== 0 }">
                <div class="w-full lg:w-1/2 group" data-aos="zoom-in" :data-aos-delay="index * 100">
                    <div class="relative rounded-xl bg-gray-900 p-2 shadow-2xl transform transition-transform duration-500 group-hover:-translate-y-2 border border-gray-700">
                        <div class="flex gap-2 mb-2 px-2">
                            <div class="w-3 h-3 rounded-full bg-red-500"></div>
                            <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                            <div class="w-3 h-3 rounded-full bg-green-500"></div>
                        </div>

                        <div class="relative overflow-hidden rounded-lg bg-gray-950 aspect-video flex items-center justify-center group-hover:brightness-110 transition-all">
                            <!-- Blurred background backdrop for premium contain view -->
                            <div v-if="project.image" class="absolute inset-0 bg-cover bg-center blur-md opacity-35" :style="{ backgroundImage: `url(${project.image})` }"></div>

                            <img v-if="project.image" :src="project.image" :alt="project.title" class="relative z-10 max-w-full max-h-full object-contain shadow-2xl" />
                            <div v-else class="relative z-10 text-center p-10 opacity-30">
                                <i :class="project.icon" class="text-6xl text-white mb-4 block"></i>
                                <span class="text-white font-mono text-sm">Preview: {{ project.title }}</span>
                            </div>

                            <div class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center z-20">
                                <Button label="View Live Demo" rounded icon="pi pi-external-link" />
                            </div>
                        </div>
                    </div>
                </div>

                <div class="w-full lg:w-1/2 text-center lg:text-left" data-aos="fade-up" :data-aos-delay="index * 100">
                    <div class="flex items-center justify-center lg:justify-start gap-4 mb-4">
                        <div :class="`p-3 rounded-xl ${getColorClasses(project.color)} bg-opacity-20`">
                            <i :class="`${project.icon} text-2xl`"></i>
                        </div>
                        <span class="text-sm font-bold tracking-widest uppercase text-gray-500">{{ project.tech[0] }} Project</span>
                    </div>

                    <h3 class="text-3xl font-bold text-gray-900 dark:text-white mb-4">{{ project.title }}</h3>

                    <p class="text-lg text-gray-600 dark:text-gray-300 leading-relaxed mb-6">
                        {{ project.description }}
                    </p>

                    <div class="flex flex-wrap gap-2 justify-center lg:justify-start mb-8">
                        <span v-for="(tech, i) in project.tech" :key="i" class="px-3 py-1 bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-300 text-sm font-medium rounded-md border border-gray-200 dark:border-gray-700">
                            {{ tech }}
                        </span>
                    </div>

                    <div class="flex gap-4 justify-center lg:justify-start">
                        <Button label="Detail Project" icon="pi pi-arrow-right" iconPos="right" />
                        <Button label="Source Code" icon="pi pi-github" severity="secondary" outlined />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
