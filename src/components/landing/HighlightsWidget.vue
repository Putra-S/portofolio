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

const otherProjects = ref([
    {
        title: 'WhatsApp Gateway API (Baileys)',
        description: 'Microservice gateway WhatsApp multi-session berbasis Baileys library. Mendukung pengiriman pesan massal (broadcast), auto-reply dinamis berbasis database, integrasi webhook, dan antrean pesan pintar untuk pencegahan ban.',
        icon: 'pi pi-whatsapp',
        tech: ['Node.js', 'Baileys', 'Socket.io', 'MySQL']
    },
    {
        title: 'Telegram Notification Gateway',
        description: 'Sistem bot gateway Telegram untuk pengiriman notifikasi otomatis dari SIMRS, mencakup alert kegagalan sistem, notifikasi pendaftaran pasien baru, dan pelaporan berkala.',
        icon: 'pi pi-send',
        tech: ['Node.js', 'Telegram API', 'Express.js', 'Webhook']
    },
    {
        title: 'Dashboard Jadwal Dokter Real-Time',
        description: 'Aplikasi dashboard display jadwal dokter real-time untuk monitor ruang tunggu poli klinik rumah sakit, terhubung langsung secara real-time dengan database SIMRS.',
        icon: 'pi pi-calendar-plus',
        tech: ['Vue 3', 'REST API', 'PrimeVue', 'Flexbox']
    },
    {
        title: 'Sistem Manajemen Anggaran (Budgeting)',
        description: 'Aplikasi backend untuk pengelolaan pengajuan anggaran operasional unit kerja, perencanaan biaya tak terduga, dan tracking persetujuan anggaran internal rumah sakit.',
        icon: 'pi pi-percentage',
        tech: ['Node.js', 'Express.js', 'MySQL', 'JWT Auth']
    }
]);
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

        <!-- Section Proyek Lainnya -->
        <div class="mt-32">
            <div class="text-center mb-16" data-aos="fade-up">
                <h3 class="text-3xl font-bold text-gray-900 dark:text-white mb-4">Proyek Tambahan Lainnya</h3>
                <p class="text-lg text-gray-600 dark:text-gray-400 max-w-2xl mx-auto">Beberapa modul pendukung, microservice, dan pustaka integrasi yang telah saya kembangkan.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div
                    v-for="(project, index) in otherProjects"
                    :key="index"
                    class="bg-white dark:bg-surface-900 p-8 rounded-2xl shadow-sm hover:shadow-md border border-gray-100 dark:border-surface-800 transition-all transform hover:-translate-y-1 flex flex-col justify-between"
                    data-aos="fade-up"
                    :data-aos-delay="index * 100"
                >
                    <div>
                        <div class="flex items-center gap-4 mb-6">
                            <div class="w-12 h-12 bg-primary/10 rounded-xl flex items-center justify-center text-primary text-xl">
                                <i :class="project.icon"></i>
                            </div>
                            <h4 class="text-xl font-bold text-gray-900 dark:text-white">{{ project.title }}</h4>
                        </div>
                        <p class="text-gray-600 dark:text-gray-300 leading-relaxed mb-6">{{ project.description }}</p>
                    </div>
                    <div>
                        <div class="flex flex-wrap gap-2 mb-6">
                            <span v-for="(tech, i) in project.tech" :key="i" class="px-2.5 py-0.5 bg-gray-100 dark:bg-gray-800 text-gray-600 dark:text-gray-300 text-xs font-semibold rounded">
                                {{ tech }}
                            </span>
                        </div>
                        <div class="flex gap-4">
                            <Button label="Source Code" icon="pi pi-github" severity="secondary" outlined size="small" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
