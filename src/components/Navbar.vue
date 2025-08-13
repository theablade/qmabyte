<template>
    <nav class="fixed top-0 left-0 right-0 z-50 flex items-center justify-between px-4 py-3 lg:px-8 bg-white dark:bg-gray-900 text-gray-800 dark:text-white transition-all duration-300 shadow-lg">
        <!-- Logo -->
        <div class="flex-shrink-0">
            <a href="/" @click="setActiveSection('/')" class="block">
                <img src="/vite.svg" alt="Logo" class="h-10 transition-transform duration-300 hover:scale-105" />
            </a>
        </div>

        <!-- Mobile Menu Toggle -->
        <button 
            @click="toggleMenu" 
            :aria-expanded="menuOpen"
            class="md:hidden relative z-50 p-2 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 rounded-lg"
        >
            <span class="sr-only">Menu</span>
            <div class="w-6 h-5 relative transition-transform duration-300">
                <span :class="[
                    'absolute block h-0.5 w-full bg-current rounded-sm transition-all duration-300',
                    menuOpen ? 'top-2 rotate-45' : 'top-0'
                ]"></span>
                <span :class="[
                    'absolute block h-0.5 w-full bg-current rounded-sm transition-all duration-300 top-2',
                    menuOpen ? 'opacity-0 -left-16' : 'opacity-100'
                ]"></span>
                <span :class="[
                    'absolute block h-0.5 w-full bg-current rounded-sm transition-all duration-300',
                    menuOpen ? 'top-2 -rotate-45' : 'top-4'
                ]"></span>
            </div>
        </button>

        <!-- Navigation Links -->
        <ul :class="[
            'list-none m-0 p-0 transition-all duration-300 ease-out',
            'md:flex md:items-center md:justify-center md:flex-1 md:gap-8',
            'fixed md:static top-0 left-0 right-0 bottom-0',
            'flex-col md:flex-row items-center justify-center gap-8 md:gap-8',
            'bg-white dark:bg-gray-900 md:bg-transparent',
            'p-8 md:p-0',
            menuOpen ? 'flex opacity-100 visible translate-y-0' : 'hidden md:flex opacity-0 md:opacity-100 invisible md:visible -translate-y-full md:translate-y-0'
        ]">
            <li v-for="link in links" :key="link.text">
                <a 
                    :href="link.href" 
                    :class="[
                        'relative block text-lg md:text-base font-medium py-4 md:py-2 transition-all duration-300',
                        'hover:text-blue-500',
                        'after:absolute after:bottom-0 after:left-0 after:h-0.5 after:bg-blue-500 after:transition-all after:duration-300',
                        link.active ? 'text-blue-500 after:w-full' : 'after:w-0 hover:after:w-full'
                    ]"
                    @click="setActiveSection(link.href)"
                >
                    {{ link.text }}
                </a>
            </li>
            
            <!-- Mobile Actions -->
            <div class="flex flex-col items-center gap-4 mt-6 md:hidden">
                <!-- Mobile Quote Button -->
                <button class="flex items-center justify-center gap-2 bg-blue-500 hover:bg-blue-600 text-white px-8 py-3 rounded-full font-medium transition-all duration-300 hover:-translate-y-0.5 shadow-lg">
                    Solicitar Orçamento
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <line x1="5" y1="12" x2="19" y2="12"></line>
                        <polyline points="12 5 19 12 12 19"></polyline>
                    </svg>
                </button>
                
                <!-- Mobile Theme Button -->
                <button 
                    @click="toggleTheme" 
                    :title="isDark ? 'Mudar para modo claro' : 'Mudar para modo escuro'"
                    class="flex items-center justify-center p-3 rounded-full bg-gray-100 dark:bg-gray-700 hover:bg-gray-200 dark:hover:bg-gray-600 transition-all duration-300 hover:rotate-12"
                >
                    <span class="sr-only">Alternar tema</span>
                    <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="text-yellow-500">
                        <circle cx="12" cy="12" r="5"/>
                        <line x1="12" y1="1" x2="12" y2="3"/>
                        <line x1="12" y1="21" x2="12" y2="23"/>
                        <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
                        <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
                        <line x1="1" y1="12" x2="3" y2="12"/>
                        <line x1="21" y1="12" x2="23" y2="12"/>
                        <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
                        <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
                    </svg>
                    <svg v-else xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="text-gray-600">
                        <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
                    </svg>
                </button>
            </div>
        </ul>

        <!-- Desktop Actions -->
        <div class="hidden md:flex items-center gap-4">
            <!-- Desktop Quote Button -->
            <button class="flex items-center gap-2 bg-blue-500 hover:bg-blue-600 text-white px-6 py-3 rounded-full font-medium transition-all duration-300 hover:-translate-y-0.5 shadow-lg">
                Solicitar Orçamento
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <line x1="5" y1="12" x2="19" y2="12"></line>
                    <polyline points="12 5 19 12 12 19"></polyline>
                </svg>
            </button>
            
            <!-- Desktop Theme Button -->
            <button 
                @click="toggleTheme" 
                :title="isDark ? 'Mudar para modo claro' : 'Mudar para modo escuro'"
                class="flex items-center justify-center p-2 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-700 transition-all duration-300 hover:rotate-12 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2"
            >
                <span class="sr-only">Alternar tema</span>
                <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="text-yellow-500">
                    <circle cx="12" cy="12" r="5"/>
                    <line x1="12" y1="1" x2="12" y2="3"/>
                    <line x1="12" y1="21" x2="12" y2="23"/>
                    <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
                    <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
                    <line x1="1" y1="12" x2="3" y2="12"/>
                    <line x1="21" y1="12" x2="23" y2="12"/>
                    <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
                    <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
                </svg>
                <svg v-else xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="text-gray-600">
                    <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
                </svg>
            </button>
        </div>
    </nav>
   <div class="h-[88px]"></div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const links = [
    { text: 'Home', href: '/', active: true },
    { text: 'About', href: '/about', active: false },
    { text: 'Team', href: '/team', active: false },
    { text: 'Services', href: '/services', active: false },
    { text: 'Pricing', href: '/pricing', active: false },
    { text: 'Portfolio', href: '/portfolio', active: false },
    { text: 'Contato', href: '/contato', active: false }
]

const menuOpen = ref(false)
const isDark = ref(false)
const currentSection = ref('/')

function toggleMenu() {
    menuOpen.value = !menuOpen.value
    if (menuOpen.value) {
        document.body.style.overflow = 'hidden'
    } else {
        document.body.style.overflow = 'auto'
    }
}

function toggleTheme() {
    isDark.value = !isDark.value
    document.documentElement.classList.toggle('dark', isDark.value)
    localStorage.setItem('theme', isDark.value ? 'dark' : 'light')
}

function setActiveSection(href) {
    currentSection.value = href
    links.forEach(link => link.active = link.href === href)
    // Fechar menu ao clicar em um link (mobile)
    if (menuOpen.value) {
        toggleMenu()
    }
}

onMounted(() => {
    const savedTheme = localStorage.getItem('theme')
    if (savedTheme) {
        isDark.value = savedTheme === 'dark'
        document.documentElement.classList.toggle('dark', isDark.value)
    }
    
    // Set active section based on current route
    const path = window.location.pathname
    setActiveSection(path)
})
</script>

<style scoped>
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}
</style>