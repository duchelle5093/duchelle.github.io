
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Frontend Developer | Modern Web Interfaces</title>
    <meta name="description" content="Portfolio of a Frontend Developer specializing in React, Next.js, and pixel-perfect UI.">
    
    <!-- Google Fonts: Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- AOS Animation Library -->
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        bgLight: '#F9FAFB',
                        cardLight: 'rgba(255, 255, 255, 0.6)', // Glass effect
                        textMainLight: '#111827',
                        textSubLight: '#4B5563',
                        
                        bgDark: '#050505', // Deeper black
                        cardDark: 'rgba(23, 23, 23, 0.6)', // Glass effect
                        textMainDark: '#EDEDED',
                        textSubDark: '#A1A1AA',

                        emerald: {
                            400: '#34D399',
                            500: '#10B981',
                            600: '#059669',
                            700: '#047857',
                        }
                    },
                    animation: {
                        'blob': 'blob 7s infinite',
                        'float': 'float 6s ease-in-out infinite',
                    },
                    keyframes: {
                        blob: {
                            '0%': { transform: 'translate(0px, 0px) scale(1)' },
                            '33%': { transform: 'translate(30px, -50px) scale(1.1)' },
                            '66%': { transform: 'translate(-20px, 20px) scale(0.9)' },
                            '100%': { transform: 'translate(0px, 0px) scale(1)' },
                        },
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-20px)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        body {
            transition: color 0.3s ease;
        }

        /* --- BACKGROUND PATTERN SYSTEM --- */
        .bg-grid-pattern {
            background-size: 40px 40px;
            background-image: 
                radial-gradient(circle, #000000 1px, transparent 1px);
            mask-image: radial-gradient(circle at center, black 40%, transparent 100%);
            -webkit-mask-image: radial-gradient(circle at center, black 40%, transparent 100%);
        }

        .dark .bg-grid-pattern {
            background-image: 
                radial-gradient(circle, #ffffff 1px, transparent 1px);
        }

        /* Glass Utility */
        .glass-panel {
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .dark .glass-panel {
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .glass-nav {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-bottom: 1px solid rgba(0,0,0,0.05);
        }
        .dark .glass-nav {
            background: rgba(5, 5, 5, 0.7);
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        
        /* Modal Transitions */
        .modal-enter { opacity: 0; transform: scale(0.95) translateY(10px); }
        .modal-enter-active { opacity: 1; transform: scale(1) translateY(0); transition: all 400ms cubic-bezier(0.16, 1, 0.3, 1); }
        
        /* Scrollbar */
        .custom-scroll::-webkit-scrollbar { width: 6px; }
        .custom-scroll::-webkit-scrollbar-track { background: transparent; }
        .custom-scroll::-webkit-scrollbar-thumb { background-color: #cbd5e1; border-radius: 20px; }
        .dark .custom-scroll::-webkit-scrollbar-thumb { background-color: #333; }
    </style>

    <script>
        if (localStorage.getItem('theme') === 'dark') {
            document.documentElement.classList.add('dark');
        } else {
            document.documentElement.classList.remove('dark');
        }
    </script>
</head>
<body class="antialiased bg-bgLight dark:bg-bgDark text-textMainLight dark:text-textMainDark selection:bg-emerald-500 selection:text-white relative">

    <!-- ==========================================
         NEW BACKGROUND SYSTEM (Fixed Position)
    =========================================== -->
    <div class="fixed inset-0 z-[-1] overflow-hidden pointer-events-none">
        
        <!-- 1. Dot Matrix Pattern (Subtle Tech Feel) -->
        <div class="absolute inset-0 z-0 opacity-[0.03] dark:opacity-[0.07] bg-grid-pattern transition-opacity duration-500"></div>

        <!-- 2. Ambient Aurora Gradients (Animated) -->
        <!-- Top Right - Emerald -->
        <div class="absolute top-0 right-0 -translate-y-12 translate-x-12 w-[500px] h-[500px] bg-emerald-400/20 dark:bg-emerald-500/10 rounded-full blur-[100px] animate-blob mix-blend-multiply dark:mix-blend-screen"></div>
        
        <!-- Bottom Left - Cyan/Teal -->
        <div class="absolute bottom-0 left-0 translate-y-12 -translate-x-12 w-[600px] h-[600px] bg-teal-400/20 dark:bg-teal-600/10 rounded-full blur-[120px] animate-blob animation-delay-2000 mix-blend-multiply dark:mix-blend-screen"></div>
        
        <!-- Center Floating - Purple Hint for depth -->
        <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-purple-300/20 dark:bg-emerald-900/10 rounded-full blur-[120px] animate-blob animation-delay-4000 mix-blend-multiply dark:mix-blend-screen"></div>
    </div>
    <!-- ========================================== -->


    <!-- Navigation -->
    <nav class="fixed w-full z-40 glass-nav transition-all duration-300">
        <div class="max-w-7xl mx-auto px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <a href="#" class="text-2xl font-bold tracking-tight text-textMainLight dark:text-white">
                    Duchelle<span class="text-emerald-600 dark:text-emerald-500">.dev</span>
                </a>
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#about" class="text-sm font-medium text-textSubLight hover:text-emerald-600 dark:text-gray-300 dark:hover:text-emerald-400 transition">About</a>
                    <a href="#projects" class="text-sm font-medium text-textSubLight hover:text-emerald-600 dark:text-gray-300 dark:hover:text-emerald-400 transition">Projects</a>
                    <a href="#experience" class="text-sm font-medium text-textSubLight hover:text-emerald-600 dark:text-gray-300 dark:hover:text-emerald-400 transition">Experience</a>
                    <a href="#contact" class="text-sm font-medium text-textSubLight hover:text-emerald-600 dark:text-gray-300 dark:hover:text-emerald-400 transition">Contact</a>
                    
                    <button id="theme-toggle" class="w-10 h-10 rounded-full bg-white/50 dark:bg-white/5 backdrop-blur text-gray-500 dark:text-emerald-400 flex items-center justify-center hover:bg-emerald-100 dark:hover:bg-white/10 transition focus:outline-none ring-1 ring-gray-200 dark:ring-gray-700 shadow-sm">
                        <i id="theme-icon-sun" class="fas fa-sun hidden dark:block"></i>
                        <i id="theme-icon-moon" class="fas fa-moon block dark:hidden"></i>
                    </button>
                    <a href="#contact" class="px-5 py-2.5 text-sm font-medium text-white bg-emerald-600 rounded-lg hover:bg-emerald-700 dark:hover:bg-emerald-500 transition shadow-lg shadow-emerald-500/20">
                        Download CV
                    </a>
                </div>
                <div class="flex items-center gap-4 md:hidden">
                    <button id="mobile-theme-toggle" class="text-gray-600 dark:text-gray-300">
                        <i class="fas fa-adjust"></i>
                    </button>
                    <button id="mobile-menu-btn" class="text-gray-600 dark:text-gray-300 hover:text-emerald-600 dark:hover:text-white focus:outline-none">
                        <i class="fas fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>
        <div id="mobile-menu" class="hidden md:hidden glass-panel bg-white/90 dark:bg-[#121212]/90 border-t border-gray-200 dark:border-gray-800">
            <div class="px-6 py-4 space-y-4 flex flex-col">
                <a href="#about" class="text-gray-600 dark:text-gray-300 hover:text-emerald-500">About</a>
                <a href="#projects" class="text-gray-600 dark:text-gray-300 hover:text-emerald-500">Projects</a>
                <a href="#experience" class="text-gray-600 dark:text-gray-300 hover:text-emerald-500">Experience</a>
                <a href="#contact" class="text-emerald-600 dark:text-emerald-400 font-medium">Contact Me</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center pt-20">
        <!-- Content -->
        <div class="max-w-7xl mx-auto px-6 lg:px-8 w-full grid grid-cols-1 lg:grid-cols-2 gap-12 items-center relative z-10">
            <div data-aos="fade-up" data-aos-duration="1000">
                <span class="inline-block py-1 px-3 rounded-full bg-emerald-100/50 dark:bg-emerald-500/10 border border-emerald-200 dark:border-emerald-500/20 text-emerald-700 dark:text-emerald-400 text-sm font-medium mb-6 backdrop-blur-md">
                    Frontend Developer
                </span>
                <h1 class="text-5xl lg:text-7xl font-bold leading-tight text-textMainLight dark:text-white mb-6">
                    Frontend Developer — <br>
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-emerald-600 to-teal-500 dark:from-emerald-400 dark:to-teal-400">Modern, Clean & Performant</span>
                    Web Interfaces
                </h1>
                <p class="text-lg text-textSubLight dark:text-gray-300 mb-8 max-w-lg leading-relaxed">
                    I translate designs into pixel-perfect, interactive web applications using React, Next.js, and modern CSS. Focused on accessibility, responsiveness, and clean component architecture.
                </p>
                <div class="flex flex-wrap gap-4">
                    <a href="#projects" class="px-7 py-3.5 bg-textMainLight text-white dark:bg-white dark:text-bgDark font-bold rounded-lg hover:bg-gray-800 dark:hover:bg-gray-200 transition duration-300 shadow-xl shadow-black/5 dark:shadow-white/5">
                        View Work
                    </a>
                    <a href="#" class="px-7 py-3.5 glass-panel bg-white/50 dark:bg-white/5 text-textMainLight dark:text-white font-medium rounded-lg hover:border-emerald-500 hover:text-emerald-600 dark:hover:text-emerald-400 transition duration-300 flex items-center gap-2">
                        <i class="fab fa-github"></i> GitHub
                    </a>
                </div>
            </div>
            <div class="relative lg:h-auto flex justify-center lg:justify-end" data-aos="fade-left" data-aos-duration="1000">
                <div class="relative w-72 h-72 lg:w-96 lg:h-96 animate-float">
                    <div class="absolute inset-0 border-2 border-emerald-500/20 rounded-full transform translate-x-4 translate-y-4"></div>
                    <img src="https://images.unsplash.com/photo-1599566150163-29194dcaad36?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" 
                         alt="Frontend Developer Portrait" 
                         class="w-full h-full object-cover rounded-full border-4 border-white dark:border-[#171717] relative z-10 shadow-2xl grayscale hover:grayscale-0 transition duration-500">
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-24 relative">
        <div class="max-w-7xl mx-auto px-6 lg:px-8 relative z-10">
            <div class="glass-panel bg-white/40 dark:bg-[#121212]/40 rounded-3xl p-8 lg:p-12 shadow-sm">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
                    <!-- Bio -->
                    <div data-aos="fade-right">
                        <h2 class="text-3xl font-bold text-textMainLight dark:text-white mb-6 flex items-center gap-3">
                            <span class="w-12 h-1 bg-emerald-500 rounded-full"></span>
                            About Me
                        </h2>
                        <p class="text-textSubLight dark:text-gray-300 leading-relaxed mb-6">
                            I am a detail-oriented <strong>Frontend Developer</strong> passionate about crafting intuitive and dynamic user experiences. I specialize in the modern JavaScript ecosystem, bridging the gap between design and engineering.
                        </p>
                        <p class="text-textSubLight dark:text-gray-300 leading-relaxed mb-8">
                            My philosophy is simple: <strong>Clean Code</strong>, <strong>Fast Load Times</strong>, and <strong>Accessible UI</strong>. I love working with design systems and transforming static Figma files into lively React components.
                        </p>
                        
                        <!-- Values -->
                        <div class="grid grid-cols-2 gap-6">
                            <div class="flex items-start gap-3">
                                <div class="p-2 bg-emerald-100/80 dark:bg-emerald-900/30 rounded-lg text-emerald-600 dark:text-emerald-400">
                                    <i class="fas fa-layer-group"></i>
                                </div>
                                <div>
                                    <h4 class="text-textMainLight dark:text-white font-semibold">Component Driven</h4>
                                    <p class="text-sm text-textSubLight dark:text-gray-400">Reusable & Scalable</p>
                                </div>
                            </div>
                            <div class="flex items-start gap-3">
                                <div class="p-2 bg-emerald-100/80 dark:bg-emerald-900/30 rounded-lg text-emerald-600 dark:text-emerald-400">
                                    <i class="fas fa-universal-access"></i>
                                </div>
                                <div>
                                    <h4 class="text-textMainLight dark:text-white font-semibold">Accessibility</h4>
                                    <p class="text-sm text-textSubLight dark:text-gray-400">Inclusive Design (A11y)</p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Tech Stack -->
                    <div data-aos="fade-left">
                        <h3 class="text-xl font-semibold text-textMainLight dark:text-white mb-6">Frontend Stack</h3>
                        <div class="grid grid-cols-3 sm:grid-cols-4 gap-4">
                            <!-- Tech Items -->
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fab fa-react text-3xl text-gray-400 dark:text-gray-500 group-hover:text-[#61DAFB] transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">React</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fas fa-bolt text-3xl text-gray-400 dark:text-gray-500 group-hover:text-black dark:group-hover:text-white transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">Next.js</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fab fa-js text-3xl text-gray-400 dark:text-gray-500 group-hover:text-[#F7DF1E] transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">JavaScript</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fas fa-code text-3xl text-gray-400 dark:text-gray-500 group-hover:text-[#3178C6] transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">TypeScript</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fas fa-wind text-3xl text-gray-400 dark:text-gray-500 group-hover:text-[#38B2AC] transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">Tailwind</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fab fa-figma text-3xl text-gray-400 dark:text-gray-500 group-hover:text-[#F24E1E] transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">Figma</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fab fa-git-alt text-3xl text-gray-400 dark:text-gray-500 group-hover:text-[#F05032] transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">Git</span>
                            </div>
                            <div class="flex flex-col items-center justify-center p-4 bg-white/60 dark:bg-white/5 rounded-xl border border-gray-200/50 dark:border-gray-700/50 hover:border-emerald-400 transition group shadow-sm backdrop-blur-sm">
                                <i class="fas fa-database text-3xl text-gray-400 dark:text-gray-500 group-hover:text-purple-400 transition mb-2"></i>
                                <span class="text-xs text-textSubLight dark:text-gray-400">Redux</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section (Featured Work) -->
    <section id="projects" class="py-24 transition-colors">
        <div class="max-w-7xl mx-auto px-6 lg:px-8 relative z-10">
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-3xl font-bold text-textMainLight dark:text-white mb-4">Featured Work</h2>
                <p class="text-textSubLight dark:text-gray-400 max-w-2xl mx-auto">A selection of interfaces focusing on user experience and responsive design.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                
                <!-- Project 1 -->
                <article class="glass-panel bg-cardLight dark:bg-cardDark rounded-xl overflow-hidden hover:shadow-2xl hover:shadow-emerald-900/10 dark:hover:shadow-emerald-900/20 transition duration-300 group" data-aos="fade-up" data-aos-delay="100">
                    <div class="h-48 overflow-hidden relative">
                        <img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="SaaS Dashboard" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition duration-300 flex items-center justify-center gap-4">
                            <a href="#" class="w-10 h-10 bg-white rounded-full flex items-center justify-center text-gray-900 hover:bg-emerald-500 hover:text-white transition" title="View Code"><i class="fab fa-github"></i></a>
                            <a href="#" class="w-10 h-10 bg-white rounded-full flex items-center justify-center text-gray-900 hover:bg-emerald-500 hover:text-white transition" title="Live Demo"><i class="fas fa-external-link-alt"></i></a>
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-textMainLight dark:text-white mb-2 group-hover:text-emerald-600 dark:group-hover:text-emerald-400 transition">Analytics Dashboard</h3>
                        <p class="text-textSubLight dark:text-gray-300 text-sm mb-4 line-clamp-2">A high-performance React dashboard featuring dynamic charts, dark mode support, and draggable widgets.</p>
                        <div class="flex flex-wrap gap-2">
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">React</span>
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">Chart.js</span>
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">Tailwind</span>
                        </div>
                    </div>
                </article>

                <!-- Project 2 -->
                <article class="glass-panel bg-cardLight dark:bg-cardDark rounded-xl overflow-hidden hover:shadow-2xl hover:shadow-emerald-900/10 dark:hover:shadow-emerald-900/20 transition duration-300 group" data-aos="fade-up" data-aos-delay="200">
                    <div class="h-48 overflow-hidden relative">
                        <img src="https://images.unsplash.com/photo-1523474253046-8cd2748b5fd2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="E-commerce UI" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition duration-300 flex items-center justify-center gap-4">
                            <a href="#" class="w-10 h-10 bg-white rounded-full flex items-center justify-center text-gray-900 hover:bg-emerald-500 hover:text-white transition" title="View Code"><i class="fab fa-github"></i></a>
                            <a href="#" class="w-10 h-10 bg-white rounded-full flex items-center justify-center text-gray-900 hover:bg-emerald-500 hover:text-white transition" title="Live Demo"><i class="fas fa-external-link-alt"></i></a>
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-textMainLight dark:text-white mb-2 group-hover:text-emerald-600 dark:group-hover:text-emerald-400 transition">Modern E-Shop UI</h3>
                        <p class="text-textSubLight dark:text-gray-300 text-sm mb-4 line-clamp-2">A pixel-perfect e-commerce storefront with complex filtering, cart state management, and smooth page transitions.</p>
                        <div class="flex flex-wrap gap-2">
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">Next.js</span>
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">Zustand</span>
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">Framer Motion</span>
                        </div>
                    </div>
                </article>

                <!-- Project 3 -->
                <article class="glass-panel bg-cardLight dark:bg-cardDark rounded-xl overflow-hidden hover:shadow-2xl hover:shadow-emerald-900/10 dark:hover:shadow-emerald-900/20 transition duration-300 group" data-aos="fade-up" data-aos-delay="300">
                    <div class="h-48 overflow-hidden relative">
                        <img src="https://images.unsplash.com/photo-1507238691740-187a5b1d37b8?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Design System" class="w-full h-full object-cover group-hover:scale-110 transition duration-500">
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition duration-300 flex items-center justify-center gap-4">
                            <a href="#" class="w-10 h-10 bg-white rounded-full flex items-center justify-center text-gray-900 hover:bg-emerald-500 hover:text-white transition" title="View Code"><i class="fab fa-github"></i></a>
                            <a href="#" class="w-10 h-10 bg-white rounded-full flex items-center justify-center text-gray-900 hover:bg-emerald-500 hover:text-white transition" title="Live Demo"><i class="fas fa-external-link-alt"></i></a>
                        </div>
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-textMainLight dark:text-white mb-2 group-hover:text-emerald-600 dark:group-hover:text-emerald-400 transition">Component Library</h3>
                        <p class="text-textSubLight dark:text-gray-300 text-sm mb-4 line-clamp-2">A documented set of accessible React components built with Storybook, ensuring UI consistency across apps.</p>
                        <div class="flex flex-wrap gap-2">
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">TypeScript</span>
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">Storybook</span>
                            <span class="px-2 py-1 bg-gray-100/80 dark:bg-white/10 border border-gray-200 dark:border-white/10 rounded text-xs text-textSubLight dark:text-gray-300">SCSS</span>
                        </div>
                    </div>
                </article>
            </div>
            
            <div class="mt-12 text-center">
                <a href="#" class="inline-flex items-center gap-2 text-emerald-600 dark:text-emerald-500 font-medium hover:text-emerald-500 dark:hover:text-emerald-400 transition">
                    See More on GitHub <i class="fas fa-arrow-right"></i>
                </a>
            </div>
        </div>
    </section>

    <!-- Experience Section (With SaaS Style Internal Projects Grid) -->
    <section id="experience" class="py-24 relative">
        <div class="max-w-6xl mx-auto px-6 lg:px-8 relative z-10">
            <h2 class="text-3xl font-bold text-textMainLight dark:text-white mb-12 text-center" data-aos="fade-up">Professional Experience</h2>
            
            <div class="relative border-l-2 border-emerald-500 ml-3 pl-8 pb-4" data-aos="fade-up">
                <!-- Timeline Dot -->
                <div class="absolute -left-[9px] top-0 w-4 h-4 rounded-full bg-emerald-500 border-4 border-white dark:border-[#121212] shadow-sm"></div>
                
                <!-- Role Header -->
                <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between mb-8">
                    <div>
                        <h3 class="text-2xl font-bold text-textMainLight dark:text-white">Frontend Developer</h3>
                        <h4 class="text-lg text-emerald-600 dark:text-emerald-400 font-medium">TechFlow Inc.</h4>
                    </div>
                    <span class="mt-2 sm:mt-0 px-3 py-1 bg-emerald-100/80 dark:bg-emerald-900/30 text-emerald-700 dark:text-emerald-300 text-sm font-mono rounded-full self-start sm:self-center border border-emerald-200 dark:border-emerald-800">
                        2024 - Present
                    </span>
                </div>

                <p class="text-textSubLight dark:text-gray-300 leading-relaxed mb-10 max-w-3xl">
                    Spearheading the frontend architecture for the company's core products. Focused on building scalable, component-driven interfaces using React and Next.js, while mentoring junior developers and establishing best practices.
                </p>

                <!-- NEW INTERNAL PROJECTS GRID -->
                <div class="mt-12">
                    <div class="flex items-center gap-3 mb-8">
                        <div class="h-px bg-gray-200 dark:bg-gray-800 flex-1"></div>
                        <h5 class="text-xs font-bold text-gray-400 dark:text-gray-500 uppercase tracking-widest">
                            Key Internal Projects
                        </h5>
                        <div class="h-px bg-gray-200 dark:bg-gray-800 flex-1"></div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                        
                        <!-- Card 1: Customer Portal -->
                        <article class="group glass-panel bg-cardLight dark:bg-cardDark rounded-xl overflow-hidden hover:shadow-xl hover:shadow-emerald-900/5 dark:hover:shadow-emerald-900/20 hover:border-emerald-500/30 transition-all duration-300 hover:scale-[1.02] flex flex-col h-full cursor-pointer" onclick="openModal('portal')">
                            <!-- Image -->
                            <div class="h-48 overflow-hidden relative border-b border-gray-100 dark:border-gray-800/50">
                                <img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Customer Portal" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                            </div>
                            <!-- Content -->
                            <div class="p-6 flex flex-col flex-1">
                                <h4 class="text-lg font-bold text-textMainLight dark:text-white mb-2 group-hover:text-emerald-600 dark:group-hover:text-emerald-400 transition-colors">Customer Portal</h4>
                                <p class="text-sm text-textSubLight dark:text-gray-400 leading-relaxed line-clamp-2 mb-6">
                                    A centralized self-service hub allowing clients to manage subscriptions, billing, and usage data efficiently.
                                </p>
                                <div class="mt-auto">
                                    <button class="w-full py-2.5 px-4 bg-white/50 dark:bg-white/5 hover:bg-emerald-50 dark:hover:bg-emerald-900/20 text-textSubLight dark:text-gray-300 hover:text-emerald-600 dark:hover:text-emerald-400 text-sm font-medium rounded-lg border border-gray-200 dark:border-gray-700 hover:border-emerald-200 dark:hover:border-emerald-800 transition-all flex items-center justify-center gap-2 group-hover:shadow-sm">
                                        View Details <i class="fas fa-arrow-right text-xs opacity-0 group-hover:opacity-100 transform -translate-x-2 group-hover:translate-x-0 transition-all duration-300"></i>
                                    </button>
                                </div>
                            </div>
                        </article>

                        <!-- Card 2: Analytics Dashboard -->
                        <article class="group glass-panel bg-cardLight dark:bg-cardDark rounded-xl overflow-hidden hover:shadow-xl hover:shadow-emerald-900/5 dark:hover:shadow-emerald-900/20 hover:border-emerald-500/30 transition-all duration-300 hover:scale-[1.02] flex flex-col h-full cursor-pointer" onclick="openModal('analytics')">
                            <!-- Image -->
                            <div class="h-48 overflow-hidden relative border-b border-gray-100 dark:border-gray-800/50">
                                <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Analytics Dashboard" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                            </div>
                            <!-- Content -->
                            <div class="p-6 flex flex-col flex-1">
                                <h4 class="text-lg font-bold text-textMainLight dark:text-white mb-2 group-hover:text-emerald-600 dark:group-hover:text-emerald-400 transition-colors">Analytics Dashboard</h4>
                                <p class="text-sm text-textSubLight dark:text-gray-400 leading-relaxed line-clamp-2 mb-6">
                                    Internal tool for visualizing complex datasets, built with custom D3.js charts for real-time KPI tracking.
                                </p>
                                <div class="mt-auto">
                                    <button class="w-full py-2.5 px-4 bg-white/50 dark:bg-white/5 hover:bg-emerald-50 dark:hover:bg-emerald-900/20 text-textSubLight dark:text-gray-300 hover:text-emerald-600 dark:hover:text-emerald-400 text-sm font-medium rounded-lg border border-gray-200 dark:border-gray-700 hover:border-emerald-200 dark:hover:border-emerald-800 transition-all flex items-center justify-center gap-2 group-hover:shadow-sm">
                                        View Details <i class="fas fa-arrow-right text-xs opacity-0 group-hover:opacity-100 transform -translate-x-2 group-hover:translate-x-0 transition-all duration-300"></i>
                                    </button>
                                </div>
                            </div>
                        </article>

                        <!-- Card 3: Auth System -->
                        <article class="group glass-panel bg-cardLight dark:bg-cardDark rounded-xl overflow-hidden hover:shadow-xl hover:shadow-emerald-900/5 dark:hover:shadow-emerald-900/20 hover:border-emerald-500/30 transition-all duration-300 hover:scale-[1.02] flex flex-col h-full cursor-pointer" onclick="openModal('auth')">
                            <!-- Image -->
                            <div class="h-48 overflow-hidden relative border-b border-gray-100 dark:border-gray-800/50">
                                <img src="https://images.unsplash.com/photo-1614064641938-3e852943722d?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Auth System" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                            </div>
                            <!-- Content -->
                            <div class="p-6 flex flex-col flex-1">
                                <h4 class="text-lg font-bold text-textMainLight dark:text-white mb-2 group-hover:text-emerald-600 dark:group-hover:text-emerald-400 transition-colors">Authentication System</h4>
                                <p class="text-sm text-textSubLight dark:text-gray-400 leading-relaxed line-clamp-2 mb-6">
                                    Secure login infrastructure implementing SSO, MFA, and Role-Based Access Control (RBAC) across the platform.
                                </p>
                                <div class="mt-auto">
                                    <button class="w-full py-2.5 px-4 bg-white/50 dark:bg-white/5 hover:bg-emerald-50 dark:hover:bg-emerald-900/20 text-textSubLight dark:text-gray-300 hover:text-emerald-600 dark:hover:text-emerald-400 text-sm font-medium rounded-lg border border-gray-200 dark:border-gray-700 hover:border-emerald-200 dark:hover:border-emerald-800 transition-all flex items-center justify-center gap-2 group-hover:shadow-sm">
                                        View Details <i class="fas fa-arrow-right text-xs opacity-0 group-hover:opacity-100 transform -translate-x-2 group-hover:translate-x-0 transition-all duration-300"></i>
                                    </button>
                                </div>
                            </div>
                        </article>

                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 relative overflow-hidden">
        <div class="max-w-3xl mx-auto px-6 lg:px-8 relative z-10">
            <div class="text-center mb-12" data-aos="fade-up">
                <h2 class="text-3xl font-bold text-textMainLight dark:text-white mb-4">Let's Work Together</h2>
                <p class="text-textSubLight dark:text-gray-400">Looking for a frontend expert to build your next product? Send me a message.</p>
            </div>
            <form class="space-y-6 glass-panel bg-cardLight dark:bg-cardDark p-8 rounded-2xl shadow-xl" data-aos="fade-up" data-aos-delay="100">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div>
                        <label for="name" class="block text-sm font-medium text-textSubLight dark:text-gray-400 mb-2">Name</label>
                        <input type="text" id="name" class="w-full bg-white/50 dark:bg-[#0A0A0A]/50 border border-gray-300 dark:border-gray-700 rounded-lg px-4 py-3 text-textMainLight dark:text-white focus:outline-none focus:border-emerald-500 focus:ring-1 focus:ring-emerald-500 transition" placeholder="John Doe">
                    </div>
                    <div>
                        <label for="email" class="block text-sm font-medium text-textSubLight dark:text-gray-400 mb-2">Email</label>
                        <input type="email" id="email" class="w-full bg-white/50 dark:bg-[#0A0A0A]/50 border border-gray-300 dark:border-gray-700 rounded-lg px-4 py-3 text-textMainLight dark:text-white focus:outline-none focus:border-emerald-500 focus:ring-1 focus:ring-emerald-500 transition" placeholder="john@example.com">
                    </div>
                </div>
                <div>
                    <label for="message" class="block text-sm font-medium text-textSubLight dark:text-gray-400 mb-2">Message</label>
                    <textarea id="message" rows="4" class="w-full bg-white/50 dark:bg-[#0A0A0A]/50 border border-gray-300 dark:border-gray-700 rounded-lg px-4 py-3 text-textMainLight dark:text-white focus:outline-none focus:border-emerald-500 focus:ring-1 focus:ring-emerald-500 transition" placeholder="Tell me about your project..."></textarea>
                </div>
                <button type="button" class="w-full bg-emerald-600 text-white font-bold py-4 rounded-lg hover:bg-emerald-700 dark:hover:bg-emerald-500 transition transform hover:-translate-y-1 shadow-lg shadow-emerald-500/20">
                    Send Message
                </button>
            </form>
            <div class="mt-12 flex justify-center space-x-8" data-aos="fade-up" data-aos-delay="200">
                <a href="#" class="text-gray-400 hover:text-emerald-600 dark:hover:text-emerald-400 transition transform hover:scale-110"><i class="fab fa-github text-3xl"></i></a>
                <a href="#" class="text-gray-400 hover:text-emerald-600 dark:hover:text-emerald-400 transition transform hover:scale-110"><i class="fab fa-linkedin text-3xl"></i></a>
                <a href="#" class="text-gray-400 hover:text-emerald-600 dark:hover:text-emerald-400 transition transform hover:scale-110"><i class="fas fa-envelope text-3xl"></i></a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 text-center glass-panel bg-white/50 dark:bg-[#0A0A0A]/50 transition-colors">
        <p class="text-textSubLight dark:text-gray-500 text-sm">
            &copy; 2025 Duchelle Dev. Built with <span class="text-emerald-600 dark:text-emerald-500">React & Tailwind</span>.
        </p>
    </footer>

    <!-- MODERN MODAL COMPONENT -->
    <div id="project-modal" class="hidden fixed inset-0 z-[60] flex items-center justify-center p-4 sm:p-6" aria-labelledby="modal-title" role="dialog" aria-modal="true">
        <!-- Backdrop -->
        <div id="modal-backdrop" class="absolute inset-0 bg-gray-900/60 backdrop-blur-sm transition-opacity duration-300 opacity-0" onclick="closeModal()"></div>
        
        <!-- Modal Content -->
        <div id="modal-content" class="relative bg-white dark:bg-[#121212] w-full max-w-4xl rounded-2xl shadow-2xl overflow-hidden modal-enter flex flex-col max-h-[90vh] border border-gray-200 dark:border-gray-800">
            
            <!-- Close Button -->
            <button onclick="closeModal()" class="absolute top-4 right-4 z-20 w-8 h-8 flex items-center justify-center rounded-full bg-white/10 text-white hover:bg-white/20 transition backdrop-blur-md shadow-lg border border-white/10">
                <i class="fas fa-times"></i>
            </button>

            <!-- Image Header (Large) -->
            <div class="h-64 sm:h-80 w-full relative shrink-0">
                <img id="modal-image" src="" alt="Project Detail" class="w-full h-full object-cover">
                <!-- Gradient Overlay for text readability -->
                <div class="absolute inset-0 bg-gradient-to-t from-[#121212] to-transparent opacity-60 dark:opacity-80"></div>
                <div class="absolute bottom-6 left-6 sm:left-8">
                    <h3 id="modal-title" class="text-3xl sm:text-4xl font-bold text-white tracking-tight drop-shadow-md"></h3>
                </div>
            </div>

            <!-- Content Body (Scrollable) -->
            <div class="p-6 sm:p-8 overflow-y-auto custom-scroll flex-1 bg-white dark:bg-[#121212]">
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 sm:gap-12">
                    
                    <!-- Main Content (Left Column) -->
                    <div class="lg:col-span-2 space-y-8">
                        <div>
                            <h4 class="text-xs font-bold text-emerald-600 dark:text-emerald-500 uppercase tracking-widest mb-3">Overview</h4>
                            <p id="modal-desc" class="text-textSubLight dark:text-gray-300 text-lg leading-relaxed"></p>
                        </div>
                        
                        <div>
                            <h4 class="text-xs font-bold text-emerald-600 dark:text-emerald-500 uppercase tracking-widest mb-3">Key Features</h4>
                            <ul id="modal-list" class="space-y-3 text-textSubLight dark:text-gray-400">
                                <!-- JS Injected -->
                            </ul>
                        </div>
                    </div>

                    <!-- Sidebar (Right Column) -->
                    <div class="space-y-8 lg:border-l lg:border-gray-100 lg:dark:border-gray-800 lg:pl-8">
                        <div>
                            <h4 class="text-xs font-bold text-gray-900 dark:text-white uppercase tracking-widest mb-3 flex items-center gap-2">
                                <i class="fas fa-user-tag text-emerald-500"></i> My Role
                            </h4>
                            <p id="modal-role" class="text-sm text-textSubLight dark:text-gray-400 leading-relaxed"></p>
                        </div>

                        <div>
                            <h4 class="text-xs font-bold text-gray-900 dark:text-white uppercase tracking-widest mb-3 flex items-center gap-2">
                                <i class="fas fa-code text-emerald-500"></i> Technologies
                            </h4>
                            <div id="modal-tech" class="flex flex-wrap gap-2">
                                <!-- JS Injected Tags -->
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
    </div>

    <!-- Scripts -->
    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // --- Data Source for Modals ---
        const projectData = {
            'portal': {
                title: "Customer Self-Service Portal",
                image: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80",
                description: "A centralized hub designed to empower clients with full control over their subscriptions, billing history, and usage metrics. This project significantly reduced support ticket volume by enabling self-service actions.",
                role: "Lead Frontend Engineer. Responsible for architectural decisions, component design, and integration with the payment gateway API.",
                tech: ["Next.js", "TypeScript", "Tailwind", "SWR", "Stripe API"],
                contributions: [
                    "Architected the frontend using **Next.js** for SEO and performance optimization.",
                    "Implemented real-time data synchronization using **SWR** for instant UI updates.",
                    "Built a fully responsive layout that maintains functionality on mobile devices.",
                    "Integrated Stripe API for seamless billing management and invoice generation."
                ]
            },
            'analytics': {
                title: "Internal Analytics Dashboard",
                image: "https://images.unsplash.com/photo-1551288049-bebda4e38f71?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80",
                description: "A mission-critical internal tool used by data analysts to visualize complex datasets. The dashboard supports real-time KPI tracking, customizable widget layouts, and exportable reports.",
                role: "UI/UX Developer. Focused on data visualization performance and creating an intuitive drag-and-drop workspace.",
                tech: ["React", "D3.js", "Grid Layout", "WebSockets", "Virtualization"],
                contributions: [
                    "Developed custom interactive charts using **D3.js** wrapped in React components.",
                    "Optimized rendering performance for large datasets (10k+ rows) using virtualization.",
                    "Implemented a drag-and-drop grid system for customizable user workspaces.",
                    "Added dark mode support for reduced eye strain during long usage periods."
                ]
            },
            'auth': {
                title: "Unified Authentication System",
                image: "https://images.unsplash.com/photo-1614064641938-3e852943722d?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80",
                description: "A secure, robust login infrastructure that serves as the gateway for the entire platform ecosystem. It handles Single Sign-On (SSO), Multi-Factor Authentication (MFA), and complex permission management.",
                role: "Frontend Security Specialist. Handled the implementation of secure auth flows and the admin management interface.",
                tech: ["React", "OAuth2", "OIDC", "Framer Motion", "Formik"],
                contributions: [
                    "Implemented standard **OAuth2 / OIDC** flows for secure third-party integrations.",
                    "Designed a granular **Role-Based Access Control (RBAC)** UI for admin management.",
                    "Enhanced security with HTTP-only cookies and CSRF protection mechanisms.",
                    "Created smooth, animated login/signup flows using Framer Motion concepts."
                ]
            }
        };

        // --- Modal Logic ---
        const modal = document.getElementById('project-modal');
        const modalBackdrop = document.getElementById('modal-backdrop');
        const modalContent = document.getElementById('modal-content');
        
        const elements = {
            title: document.getElementById('modal-title'),
            image: document.getElementById('modal-image'),
            desc: document.getElementById('modal-desc'),
            list: document.getElementById('modal-list'),
            role: document.getElementById('modal-role'),
            tech: document.getElementById('modal-tech')
        };

        function openModal(projectId) {
            const data = projectData[projectId];
            if (!data) return;

            // Populate Content
            elements.title.textContent = data.title;
            elements.image.src = data.image;
            elements.desc.textContent = data.description;
            elements.role.textContent = data.role;
            
            // Populate Features List
            elements.list.innerHTML = '';
            data.contributions.forEach(item => {
                const li = document.createElement('li');
                li.className = "flex items-start gap-3";
                const formattedText = item.replace(/\*\*(.*?)\*\*/g, '<strong class="text-gray-900 dark:text-white font-semibold">$1</strong>');
                li.innerHTML = `<i class="fas fa-check-circle text-emerald-500 mt-1.5 shrink-0"></i><span class="text-sm leading-relaxed">${formattedText}</span>`;
                elements.list.appendChild(li);
            });

            // Populate Tech Tags
            elements.tech.innerHTML = '';
            data.tech.forEach(tech => {
                const span = document.createElement('span');
                span.className = "px-2.5 py-1 bg-gray-100 dark:bg-gray-800 text-gray-700 dark:text-gray-300 text-xs font-medium rounded border border-gray-200 dark:border-gray-700";
                span.textContent = tech;
                elements.tech.appendChild(span);
            });

            // Show Modal
            modal.classList.remove('hidden');
            document.body.style.overflow = 'hidden';

            // Animation sequence
            setTimeout(() => {
                modalBackdrop.classList.remove('opacity-0');
                modalContent.classList.remove('modal-enter');
                modalContent.classList.add('modal-enter-active');
            }, 10);
        }

        function closeModal() {
            modalBackdrop.classList.add('opacity-0');
            modalContent.classList.remove('modal-enter-active');
            modalContent.classList.add('modal-enter'); // Re-apply start state for exit anim

            setTimeout(() => {
                modal.classList.add('hidden');
                document.body.style.overflow = '';
            }, 300);
        }

        // Close on Escape Key
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && !modal.classList.contains('hidden')) {
                closeModal();
            }
        });

        // --- AOS Init ---
        AOS.init({ once: true, offset: 50, duration: 800, easing: 'ease-out-cubic' });

        // --- Mobile Menu ---
        const menuBtn = document.getElementById('mobile-menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');
        menuBtn.addEventListener('click', () => { mobileMenu.classList.toggle('hidden'); });
        document.querySelectorAll('#mobile-menu a').forEach(link => {
            link.addEventListener('click', () => { mobileMenu.classList.add('hidden'); });
        });

        // --- Theme Toggle ---
        const themeToggleBtn = document.getElementById('theme-toggle');
        const mobileThemeToggleBtn = document.getElementById('mobile-theme-toggle');
        const html = document.documentElement;

        function toggleTheme() {
            if (html.classList.contains('dark')) {
                html.classList.remove('dark');
                localStorage.setItem('theme', 'light');
            } else {
                html.classList.add('dark');
                localStorage.setItem('theme', 'dark');
            }
        }
        themeToggleBtn.addEventListener('click', toggleTheme);
        mobileThemeToggleBtn.addEventListener('click', toggleTheme);
    </script>
</body>
</html>
