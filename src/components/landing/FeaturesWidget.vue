<script setup>
function downloadCV() {
    // Pastikan file ada di folder public/files/
    window.open('/files/Putra-CV.pdf', '_blank');
}

function scrollToSection(id) {
    const element = document.getElementById(id);
    if (element) {
        const headerOffset = 80;
        const elementPosition = element.getBoundingClientRect().top;
        const offsetPosition = elementPosition + window.pageYOffset - headerOffset;
        window.scrollTo({
            top: offsetPosition,
            behavior: 'smooth'
        });
    }
}

// Data statis untuk visualisasi "Experience Card"
const stats = [
    { label: 'Pengalaman Kerja', value: '5+ Tahun', icon: 'pi pi-calendar' },
    { label: 'Proyek Selesai', value: '20+ Proyek', icon: 'pi pi-check-circle' },
    { label: 'Uptime Sistem', value: '99.9%', icon: 'pi pi-server' }
];
</script>

<template>
    <section id="about" class="py-24 px-6 lg:px-20 bg-surface-0 dark:bg-surface-900 overflow-hidden relative">
        <div class="absolute top-0 right-0 -mr-20 -mt-20 w-96 h-96 bg-primary/5 rounded-full blur-3xl -z-10"></div>
        <div class="absolute bottom-0 left-0 -ml-20 -mb-20 w-80 h-80 bg-blue-100 dark:bg-blue-900/20 rounded-full blur-3xl -z-10"></div>

        <div class="container mx-auto grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
            <div class="relative group" data-aos="fade-right">
                <div class="absolute -inset-1 bg-gradient-to-r from-primary to-blue-400 rounded-2xl blur opacity-25 group-hover:opacity-50 transition duration-1000 group-hover:duration-200"></div>

                <div class="relative bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8 border border-gray-100 dark:border-gray-700">
                    <div class="flex items-center gap-4 mb-6">
                        <div class="w-16 h-16 rounded-full bg-primary/10 flex items-center justify-center text-primary">
                            <i class="pi pi-user text-2xl"></i>
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-gray-900 dark:text-white">Ma'ruf Putra</h3>
                            <p class="text-gray-500 dark:text-gray-400 text-sm">Fullstack System Engineer</p>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <div v-for="(item, index) in stats" :key="index" class="flex items-center justify-between p-4 bg-gray-50 dark:bg-gray-700/50 rounded-xl hover:bg-blue-50 dark:hover:bg-gray-700 transition-colors">
                            <div class="flex items-center gap-3">
                                <i :class="item.icon" class="text-primary text-lg"></i>
                                <span class="text-gray-600 dark:text-gray-300 font-medium">{{ item.label }}</span>
                            </div>
                            <span class="font-bold text-gray-900 dark:text-white">{{ item.value }}</span>
                        </div>
                    </div>

                    <div class="mt-6 pt-6 border-t border-gray-100 dark:border-gray-600 text-center">
                        <p class="italic text-gray-500 text-sm">"Mengubah alur kerja rumah sakit yang kompleks menjadi baris kode yang sederhana."</p>
                    </div>
                </div>
            </div>

            <div class="text-left" data-aos="fade-left">
                <div class="inline-block px-3 py-1 mb-4 text-xs font-semibold tracking-wider text-primary uppercase bg-blue-50 dark:bg-blue-900/30 rounded-full">Tentang Saya</div>

                <h2 class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mb-6 leading-tight">
                    Dedikasi Tinggi Membangun <br />
                    <span class="text-primary relative inline-block">
                        Sistem Terpercaya
                        <svg class="absolute w-full h-2 bottom-0 left-0 text-blue-200 -z-10" viewBox="0 0 100 10" preserveAspectRatio="none"><path d="M0 5 Q 50 10 100 5" stroke="currentColor" stroke-width="8" fill="none" /></svg>
                    </span>
                </h2>

                <p class="text-lg text-gray-600 dark:text-gray-300 leading-relaxed mb-4">
                    Saya adalah seorang Fullstack Developer dengan fokus utama pada pengembangan <span class="font-semibold text-gray-900 dark:text-white">Infrastruktur IT Layanan Kesehatan</span>. Saya memiliki spesialisasi dalam menyederhanakan
                    aliran data medis yang rumit menjadi antarmuka yang ramah pengguna.
                </p>

                <p class="text-lg text-gray-600 dark:text-gray-300 leading-relaxed mb-8">
                    Keahlian utama saya mencakup pembangunan platform <strong>SIMRS</strong> (Sistem Informasi Manajemen Rumah Sakit) yang tangguh, integrasi sistem bridging
                    <span class="text-primary font-medium">BPJS Kesehatan & SATUSEHAT HL7 FHIR</span> Kemenkes, serta pengamanan transaksi data medis menggunakan teknologi modern.
                </p>

                <div class="mb-8">
                    <h4 class="text-sm font-bold text-gray-900 dark:text-white uppercase tracking-wide mb-3">Technology Stack</h4>
                    <div class="flex flex-wrap gap-2">
                        <span class="skill-pill border-l-4 border-green-500 bg-green-50 text-green-700">Node.js</span>
                        <span class="skill-pill border-l-4 border-gray-500 bg-gray-50 text-gray-700">Express.js</span>
                        <span class="skill-pill border-l-4 border-orange-500 bg-orange-50 text-orange-700">MySQL</span>

                        <span class="skill-pill border-l-4 border-emerald-500 bg-emerald-50 text-emerald-700">Vue 3</span>
                        <span class="skill-pill border-l-4 border-blue-500 bg-blue-50 text-blue-700">Tailwind CSS</span>

                        <span class="skill-pill border-l-4 border-purple-500 bg-purple-50 text-purple-700">Linux/VPS</span>
                        <span class="skill-pill border-l-4 border-sky-500 bg-sky-50 text-sky-700">Docker</span>
                    </div>
                </div>

                <div class="flex flex-wrap gap-4">
                    <Button
                        label="Unduh CV"
                        icon="pi pi-download"
                        class="p-button-rounded !px-6 !py-3 bg-primary border-primary hover:bg-primary-600 shadow-lg hover:shadow-primary/30 transition-all transform hover:-translate-y-1"
                        @click="downloadCV"
                    />
                    <Button label="Hubungi Saya" icon="pi pi-arrow-right" iconPos="right" outlined class="p-button-rounded p-button-secondary !px-6 !py-3 hover:bg-gray-100 dark:hover:bg-gray-800 transition-all" @click="scrollToSection('contact')" />
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
/* Custom Class untuk Skill Pill agar rapi */
.skill-pill {
    @apply px-4 py-2 rounded-r-lg text-sm font-semibold shadow-sm transition-transform hover:scale-105 cursor-default;
}

/* Sedikit animasi tambahan jika elemen masuk viewport */
[data-aos] {
    transition:
        opacity 0.8s ease-out,
        transform 0.8s ease-out;
}
</style>
