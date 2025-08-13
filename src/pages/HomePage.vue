<template>
    <div class="qmabyte-website bg-gradient-to-r from-gray-50 to-white dark:bg-gradient-to-b dark:from-gray-900 to-black min-h-screen">
        <!-- Hero Section -->
        <section
            class="hero-section flex flex-col lg:flex-row items-center w-full max-w-screen-xl mx-auto px-6 py-20 min-h-[80vh] justify-center gap-12"
            :class="{ 'animate-fade-in': isVisible.hero }"
            ref="heroRef"
        >
            <div class="flex-1 lg:text-start text-center space-y-8">
                <h1 class="text-5xl md:text-6xl lg:text-7xl font-extrabold leading-tight tracking-tight">
                    Acelere o seu
                    <span class="gradient-text block">Futuro Digital</span>
                    <span class="text-gray-200">com a QmaByte</span>
                </h1>
                <p class="text-lg md:text-xl text-gray-600 dark:text-gray-500 lg:text-left text-center max-w-2xl mx-auto lg:mx-0 leading-relaxed">
                    Transformamos sua visão em realidade, desenvolvendo soluções digitais personalizadas que impulsionam seu negócio.
                    De sites e aplicativos a sistemas complexos, nossa equipe de especialistas está pronta para levar sua empresa ao próximo nível.
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start">
                    <button
                        @click="requestQuote"
                        class="cta-button bg-gradient-to-r from-purple-600 to-blue-600 text-white px-8 py-4 rounded-xl font-semibold text-lg shadow-lg hover:shadow-2xl hover:scale-105 transition-all duration-300 flex items-center justify-center gap-2"
                    >
                        Pedir um orçamento
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
                        </svg>
                    </button>
                    <button
                        @click="scrollToServices"
                        class="secondary-button border-2 border-purple-600 text-purple-600 px-8 py-4 rounded-xl font-semibold text-lg hover:bg-purple-600 hover:text-white transition-all duration-300"
                    >
                        Ver Serviços
                    </button>
                </div>
            </div>
            <div class="flex-1 flex justify-center mt-12 lg:mt-0">
                <div class="floating">
                    <img
                        src="../assets/Desktop.svg"
                        alt="Ilustração Desktop"
                        class="max-w-full h-auto rounded-2xl shadow-2xl glass-effect p-4"
                    />
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section
            class="about-section w-full max-w-screen-xl mx-auto px-6 py-20"
            :class="{ 'animate-fade-in': isVisible.about }"
            ref="aboutRef"
        >
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-extrabold mb-6 gradient-text">Sobre Nós</h2>
                <div class="w-24 h-1 bg-gradient-to-r from-purple-600 to-blue-600 mx-auto mb-8 rounded"></div>
            </div>
            <div class="flex flex-col lg:flex-row items-center gap-16">
                <div class="flex-1 space-y-6">
                    <p class="text-lg text-gray-600 dark:text-gray-500 leading-relaxed">
                        Somos apaixonados por tecnologia e inovação. Na QmaByte, unimos experiência técnica e criatividade
                        para entregar soluções digitais que realmente fazem a diferença. Nosso compromisso é entender as
                        necessidades dos clientes e superar expectativas em cada projeto.
                    </p>
                    <p class="text-lg text-gray-600 dark:text-gray-500 leading-relaxed">
                        Com uma equipe multidisciplinar, atuamos desde a concepção até a entrega, sempre focados em
                        qualidade, agilidade e resultados. Venha construir o futuro digital conosco!
                    </p>
                    <div class="grid grid-cols-2 gap-8 mt-12">
                        <div class="text-center">
                            <div class="text-3xl md:text-4xl font-extrabold text-purple-600">{{ stats.projects }}+</div>
                            <div class="text-gray-600 dark:text-gray-500">Projetos Concluídos</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl md:text-4xl font-extrabold text-purple-600">{{ stats.clients }}+</div>
                            <div class="text-gray-600 dark:text-gray-500">Clientes Satisfeitos</div>
                        </div>
                    </div>
                </div>
                <div class="flex-1">
                    <img
                        src="../assets/Desktop.svg"
                        alt="Sobre Nós"
                        class="max-w-full h-auto rounded-2xl shadow-2xl"
                    />
                </div>
            </div>
        </section>

        <!-- Team Section -->
        <section
            class="team-section max-w-screen-xl mx-auto px-6 py-20"
            :class="{ 'animate-fade-in': isVisible.team }"
            ref="teamRef"
        >
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-extrabold mb-6 gradient-text">Nossa Equipa</h2>
                <div class="w-24 h-1 bg-gradient-to-r from-purple-600 to-blue-600 mx-auto rounded"></div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-12 max-w-4xl mx-auto">
                <div
                    v-for="(member, index) in team"
                    :key="index"
                    class="team-card glass-effect rounded-2xl p-8 text-center card-hover"
                >
                    <div class="relative mb-6 flex justify-center">
                        <img
                            :src="member.image"
                            :alt="member.name"
                            class="w-32 h-32 rounded-full object-cover border-4 border-purple-200 shadow-lg"
                        />
                        <div class="absolute bottom-2 right-2 w-8 h-8 bg-green-500 rounded-full border-4 border-white"></div>
                    </div>
                    <h3 class="text-2xl font-bold mb-2 text-gray-800">{{ member.name }}</h3>
                    <p class="text-purple-600 font-semibold mb-4 text-lg">{{ member.role }}</p>
                    <p class="text-gray-600 leading-relaxed">{{ member.description }}</p>
                    <div class="flex justify-center space-x-4 mt-6">
                        <a
                            :href="member.linkedin"
                            target="_blank"
                            rel="noopener noreferrer"
                            class="social-link w-10 h-10 bg-purple-100 dark:bg-purple-900 rounded-full flex items-center justify-center hover:bg-purple-600 hover:text-white transition-all duration-300"
                        >
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                            </svg>
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section
            class="services-section max-w-screen-xl mx-auto px-6 py-20"
            :class="{ 'animate-fade-in': isVisible.services }"
            ref="servicesRef"
        >
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-extrabold mb-6 gradient-text">Nossos Serviços</h2>
                <div class="w-24 h-1 bg-gradient-to-r from-purple-600 to-blue-600 mx-auto rounded"></div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div
                    v-for="(service, index) in services"
                    :key="index"
                    class="service-card glass-effect rounded-2xl p-8 card-hover group flex flex-col"
                >
                    <div class="w-16 h-16 bg-gradient-to-r from-purple-600 to-blue-600 rounded-2xl flex items-center justify-center mb-6 group-hover:scale-110 transition-transform duration-300 text-3xl">
                        {{ service.icon }}
                    </div>
                    <h3 class="text-2xl font-bold mb-4 text-gray-800">{{ service.title }}</h3>
                    <p class="text-gray-600 leading-relaxed mb-6">{{ service.description }}</p>
                    <ul class="space-y-2">
                        <li v-for="feature in service.features" :key="feature" class="flex items-center text-sm text-gray-600">
                            <svg class="w-4 h-4 text-purple-600 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                            </svg>
                            {{ feature }}
                        </li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Pricing Section -->
        <section
            class="pricing-section max-w-screen-xl mx-auto px-6 py-20"
            :class="{ 'animate-fade-in': isVisible.pricing }"
            ref="pricingRef"
        >
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-extrabold mb-6 gradient-text">Nossos Preços</h2>
                <div class="w-24 h-1 bg-gradient-to-r from-purple-600 to-blue-600 mx-auto rounded"></div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div
                    v-for="(plan, index) in pricingPlans"
                    :key="index"
                    class="pricing-card glass-effect rounded-2xl p-8 card-hover relative flex flex-col"
                    :class="{ 'featured-plan': plan.featured, 'scale-105 border-2 border-purple-500': plan.featured }"
                >
                    <div v-if="plan.featured" class="absolute -top-4 left-1/2 transform -translate-x-1/2">
                        <span class="bg-gradient-to-r from-purple-600 to-blue-600 text-white px-4 py-1 rounded-full text-sm font-semibold shadow">
                            Mais Popular
                        </span>
                    </div>
                    <div class="text-center mb-8">
                        <h3 class="text-2xl font-bold mb-4" :class="plan.featured ? 'text-white' : 'text-gray-800'">
                            {{ plan.name }}
                        </h3>
                        <div class="mb-4">
                            <span class="text-4xl font-bold" :class="plan.featured ? 'text-white' : 'text-purple-600'">
                                {{ plan.price }}
                            </span>
                            <span v-if="plan.period" class="text-gray-500 ml-2">{{ plan.period }}</span>
                        </div>
                        <p :class="plan.featured ? 'text-purple-100' : 'text-gray-600'">
                            {{ plan.description }}
                        </p>
                    </div>
                    <ul class="space-y-4 mb-8">
                        <li
                            v-for="feature in plan.features"
                            :key="feature"
                            class="flex items-center"
                            :class="plan.featured ? 'text-purple-100' : 'text-gray-700'"
                        >
                            <svg class="w-5 h-5 mr-3 text-green-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                            </svg>
                            {{ feature }}
                        </li>
                    </ul>
                    <button
                        @click="subscribePlan(plan)"
                        class="w-full py-4 rounded-xl font-semibold text-lg transition-all duration-300 hover:scale-105"
                        :class="plan.featured
                            ? 'bg-white text-purple-600 hover:bg-gray-100'
                            : 'bg-gradient-to-r from-purple-600 to-blue-600 text-white hover:shadow-lg'"
                    >
                        {{ plan.buttonText }}
                    </button>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import { ref, onMounted, reactive } from 'vue'

const isVisible = reactive({
    hero: false,
    about: false,
    team: false,
    services: false,
    pricing: false
})

const stats = reactive({
    projects: 150,
    clients: 89
})

const team = ref([
    {
        name: 'Nelson José Anselmo',
        role: 'CO-Founder & CEO',
        image: 'https://media.licdn.com/dms/image/v2/C5603AQEc9AUR_EgECQ/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1610620884336?e=1758153600&v=beta&t=qFF9UXlALBZyppgMGAUQGBQ0W36hO7t_V12Tukl3s78',
        description: 'Especialista em negócios digitais, lidera a estratégia e inovação na QmaByte com mais de 10 anos de experiência.'
    },
    {
        name: 'Fernando Muethea',
        role: 'CTO & Co-Founder',
        image: 'https://media.licdn.com/dms/image/v2/D5603AQFCBcUG540A3Q/profile-displayphoto-shrink_200_200/B56ZVQ2PR7HoAY-/0/1740818153024?e=1758153600&v=beta&t=vBaR2YkGlyVYDOMbZp6WqKdW4haCLSk5mLoydBHYxBw',
        description: 'Responsável pela arquitetura técnica e desenvolvimento de soluções inovadoras. Expert em tecnologias emergentes.'
    }
])

const services = ref([
    {
        title: 'Desenvolvimento Web',
        description: 'Criamos sites e aplicações web responsivas e escaláveis, utilizando as melhores práticas de desenvolvimento.',
        icon: '🌐',
        features: ['Design Responsivo', 'SEO Otimizado', 'Performance Máxima', 'Segurança Avançada']
    },
    {
        title: 'Aplicativos Móveis',
        description: 'Desenvolvemos aplicativos móveis nativos e híbridos para Android e iOS, focando na experiência do usuário.',
        icon: '📱',
        features: ['iOS & Android', 'UI/UX Moderna', 'Performance Nativa', 'Integração API']
    },
    {
        title: 'Consultoria em TI',
        description: 'Oferecemos consultoria especializada para otimizar processos e implementar soluções tecnológicas eficazes.',
        icon: '💡',
        features: ['Análise Técnica', 'Otimização de Processos', 'Arquitetura de Sistemas', 'Suporte Contínuo']
    }
])

const pricingPlans = ref([
    {
        name: 'Plano Básico',
        price: '10.000 MT',
        period: '/mês',
        description: 'Ideal para pequenas empresas e startups.',
        features: [
            'Site institucional',
            'Suporte básico',
            'Hospedagem inclusa',
            'SSL Certificate',
            '3 páginas'
        ],
        buttonText: 'Assinar Agora',
        featured: false
    },
    {
        name: 'Plano Profissional',
        price: '25.000 MT',
        period: '/mês',
        description: 'Para empresas em crescimento com necessidades avançadas.',
        features: [
            'Site + Aplicativo',
            'Suporte prioritário',
            'Consultoria mensal',
            'Hospedagem dedicada',
            'Analytics avançado',
            'SEO Premium'
        ],
        buttonText: 'Assinar Agora',
        featured: true
    },
    {
        name: 'Plano Premium',
        price: 'Sob consulta',
        description: 'Soluções exclusivas e personalizadas para grandes empresas.',
        features: [
            'Projetos sob medida',
            'Equipe dedicada',
            'Suporte 24/7',
            'Consultoria estratégica',
            'Desenvolvimento custom',
            'Integração completa'
        ],
        buttonText: 'Solicitar Orçamento',
        featured: false
    }
])

const heroRef = ref(null)
const aboutRef = ref(null)
const teamRef = ref(null)
const servicesRef = ref(null)
const pricingRef = ref(null)

const requestQuote = () => {
    console.log('Solicitando orçamento...')
}

const scrollToServices = () => {
    const servicesElement = servicesRef.value
    if (servicesElement) {
        servicesElement.scrollIntoView({ behavior: 'smooth' })
    }
}

const subscribePlan = (plan) => {
    console.log('Assinando plano:', plan.name)
}

const setupIntersectionObserver = () => {
    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    const target = entry.target
                    if (target === heroRef.value) isVisible.hero = true
                    if (target === aboutRef.value) isVisible.about = true
                    if (target === teamRef.value) isVisible.team = true
                    if (target === servicesRef.value) isVisible.services = true
                    if (target === pricingRef.value) isVisible.pricing = true
                }
            })
        },
        { threshold: 0.1 }
    )
    setTimeout(() => {
        if (heroRef.value) observer.observe(heroRef.value)
        if (aboutRef.value) observer.observe(aboutRef.value)
        if (teamRef.value) observer.observe(teamRef.value)
        if (servicesRef.value) observer.observe(servicesRef.value)
        if (pricingRef.value) observer.observe(pricingRef.value)
    }, 100)
}

onMounted(() => {
    setupIntersectionObserver()
    setTimeout(() => {
        let projectCount = 0
        let clientCount = 0
        const projectInterval = setInterval(() => {
            if (projectCount < 150) {
                projectCount += 5
                stats.projects = projectCount
            } else {
                clearInterval(projectInterval)
            }
        }, 50)
        const clientInterval = setInterval(() => {
            if (clientCount < 89) {
                clientCount += 3
                stats.clients = clientCount
            } else {
                clearInterval(clientInterval)
            }
        }, 60)
    }, 2000)
})
</script>

<style scoped>
.gradient-text {
    @apply bg-gradient-to-r from-purple-600 to-blue-600 bg-clip-text text-transparent;
}
.glass-effect {
    @apply bg-white/80 backdrop-blur-md border border-white/30;
}

.card-hover:hover {
    @apply -translate-y-2 scale-105 shadow-2xl;
}
.floating {
    animation: float 6s ease-in-out infinite;
}
@keyframes float {
    0%, 100% { transform: translateY(0px); }
    50% { transform: translateY(-20px); }
}
.animate-fade-in {
    animation: fadeInUp 0.8s ease-out forwards;
}
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(50px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
.featured-plan {
    @apply bg-gradient-to-r from-purple-600 to-blue-600;
}

.social-link {
    @apply transition-all duration-300 ease-in-out;
}
.social-link:hover {
    @apply -translate-y-0.5;
}
</style>
