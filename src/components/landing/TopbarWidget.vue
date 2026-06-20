<script setup>
// Menu Items (Updated IDs based on previous context)
const navItems = [
    { label: 'Beranda', id: 'hero' },
    { label: 'Tentang', id: 'about' }, // Sebelumnya 'features'
    { label: 'Proyek', id: 'highlights' },
    { label: 'Keahlian', id: 'skills' } // Sebelumnya 'pricing'
];

function smoothScroll(id) {
    // Hack: trigger click pada body untuk menutup menu mobile (jika pakai v-styleclass hideOnOutsideClick)
    document.body.click();

    const element = document.getElementById(id);
    if (element) {
        const headerOffset = 80; // Sesuaikan dengan tinggi navbar agar tidak tertutup
        const elementPosition = element.getBoundingClientRect().top;
        const offsetPosition = elementPosition + window.pageYOffset - headerOffset;

        window.scrollTo({
            top: offsetPosition,
            behavior: 'smooth'
        });
    }
}
</script>

<template>
    <div class="fixed top-0 left-0 w-full z-50 bg-white/80 dark:bg-surface-900/80 backdrop-blur-md border-b border-surface-200 dark:border-surface-700 transition-all duration-300">
        <div class="flex items-center justify-between px-6 lg:px-20 py-4 relative">
            <a class="flex items-center gap-3 cursor-pointer group" @click="smoothScroll('hero')">
                <img src="/src/assets/image/PutraDev.png" alt="Logo" class="h-10 w-auto group-hover:rotate-12 transition-transform duration-300" />
                <span class="text-surface-900 dark:text-surface-0 font-bold text-xl tracking-tight"> PUTRA<span class="text-primary">DEV</span> </span>
            </a>

            <!-- <Button
                class="lg:hidden"
                text
                severity="secondary"
                rounded
                v-styleclass="{ selector: '#mobile-menu', enterFromClass: 'hidden', enterActiveClass: 'animate-scalein', leaveToClass: 'hidden', leaveActiveClass: 'animate-fadeout', hideOnOutsideClick: true }"
            >
                <i class="pi pi-bars text-2xl"></i>
            </Button> -->

            <div class="hidden lg:flex items-center gap-8">
                <ul class="flex items-center gap-8 list-none m-0 p-0">
                    <li v-for="item in navItems" :key="item.id">
                        <a @click="smoothScroll(item.id)" class="cursor-pointer text-surface-600 dark:text-surface-200 font-medium text-base hover:text-primary transition-colors relative group">
                            {{ item.label }}
                            <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
                        </a>
                    </li>
                </ul>

                <Button label="Hubungi Saya" rounded size="small" class="font-bold !px-6" @click="smoothScroll('contact')" />
            </div>
        </div>

        <div id="mobile-menu" class="hidden absolute top-full left-0 w-full bg-white dark:bg-surface-900 border-b border-surface-200 dark:border-surface-700 shadow-xl lg:hidden">
            <ul class="flex flex-col list-none p-6 gap-4">
                <li v-for="item in navItems" :key="item.id">
                    <a @click="smoothScroll(item.id)" class="block w-full py-3 px-4 rounded-lg hover:bg-surface-50 dark:hover:bg-surface-800 text-surface-900 dark:text-surface-0 font-medium transition-colors">
                        {{ item.label }}
                    </a>
                </li>
                <li>
                    <Button label="Hubungi Saya" class="w-full mt-2" @click="smoothScroll('contact')" />
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
/* Pastikan navbar selalu di atas elemen lain */
.z-50 {
    z-index: 50;
}
</style>
