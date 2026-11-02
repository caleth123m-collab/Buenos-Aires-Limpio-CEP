<!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Fonts: Plus Jakarta Sans -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">

    <!-- Configuración de Tema de Tailwind -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                    },
                    colors: {
                        eco: {
                            50: '#f0fdf4',
                            100: '#dcfce7',
                            200: '#bbf7d0',
                            300: '#86efac',
                            400: '#4ade80',
                            500: '#22c55e',
                            600: '#16a34a',
                            700: '#15803d',
                            800: '#166534',
                            900: '#14532d',
                        }
                    }
                }
            }
        }
    </script>

    <!-- Estilos Personalizados -->
    <style>
        .buenos-aires-limpio-wrapper {
            background-color: #f4fbf6;
            background-image: radial-gradient(#dcfce7 1.5px, transparent 1.5px), radial-gradient(#dcfce7 1.5px, #f4fbf6 1.5px);
            background-size: 60px 60px;
            background-position: 0 0, 30px 30px;
        }

        /* Hojas flotantes decorativas */
        .leaf-bg {
            position: absolute;
            pointer-events: none;
            z-index: 0;
            opacity: 0.15;
        }

        .circle-chart-circle {
            transition: stroke-dasharray 0.8s ease-in-out;
        }

        /* Animación suave entre pantallas */
        .fade-in {
            animation: fadeIn 0.4s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="bg-slate-50 font-sans text-slate-800 antialiased selection:bg-eco-200">

<!-- Contenido Principal de la aplicación -->
<div class="buenos-aires-limpio-wrapper text-slate-800 min-h-screen flex flex-col justify-between relative overflow-x-hidden">

    <!-- Decoraciones Botánicas de Fondo -->
    <div class="leaf-bg top-5 left-5 text-eco-700 text-9xl">
        <i class="fa-solid fa-leaf transform -rotate-45"></i>
    </div>
    <div class="leaf-bg bottom-5 right-5 text-eco-700 text-9xl">
        <i class="fa-solid fa-seedling transform rotate-12"></i>
    </div>
    <div class="leaf-bg top-1/3 -right-10 text-eco-600 text-8xl">
        <i class="fa-solid fa-tree"></i>
    </div>
    <div class="leaf-bg bottom-1/4 -left-10 text-eco-600 text-8xl">
        <i class="fa-solid fa-plant-wilt"></i>
    </div>

    <!-- Encabezado / Barra superior -->
    <header class="relative z-10 w-full py-6 px-4 sm:px-8 border-b border-eco-200/60 bg-white/70 backdrop-blur-md">
        <div class="max-w-6xl mx-auto flex justify-between items-center">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-full bg-eco-500 text-white flex items-center justify-center shadow-lg shadow-eco-500/30">
                    <i class="fa-solid fa-leaf text-xl"></i>
                </div>
                <span class="font-extrabold text-xl sm:text-2xl tracking-tight text-eco-900">Buenos Aires <span class="text-eco-600">Limpio</span></span>
            </div>
            <div id="survey-counter-badge" class="flex items-center gap-2 bg-eco-100 text-eco-800 px-4 py-1.5 rounded-full text-xs sm:text-sm font-semibold shadow-sm">
                <i class="fa-solid fa-users text-eco-600"></i>
                <span id="total-responses-count">0</span> Participaciones
            </div>
        </div>
    </header>

    <!-- Contenido Principal -->
    <main class="relative z-10 flex-grow flex items-center justify-center p-4 sm:p-6 md:p-10">
        <div class="w-full max-w-5xl">

            <!-- PANTALLA DE INICIO -->
            <section id="home-screen" class="fade-in space-y-10">
                <!-- Banner Principal -->
                <div class="bg-white/90 backdrop-blur-md rounded-3xl p-8 sm:p-12 shadow-xl shadow-eco-900/5 border border-eco-100 text-center max-w-3xl mx-auto relative overflow-hidden">
                    <div class="absolute -top-12 -right-12 w-32 h-32 bg-eco-100 rounded-full blur-2xl"></div>
                    <div class="absolute -bottom-12 -left-12 w-32 h-32 bg-blue-100 rounded-full blur-2xl"></div>

                    <span class="inline-block px-4 py-1.5 bg-eco-100 text-eco-700 text-xs font-bold rounded-full uppercase tracking-wider mb-4">
                        Iniciativa Ciudadana
                    </span>
                    
                    <h1 class="text-3xl sm:text-5xl font-extrabold text-slate-900 tracking-tight mb-4">
                        Buenos Aires Limpio
                    </h1>
                    
                    <p class="text-slate-600 text-lg sm:text-xl max-w-xl mx-auto font-medium mb-8">
                        Conoce cómo cuidamos nuestro entorno
                    </p>

                    <!-- Botón Principal -->
                    <button id="start-btn" onclick="startSurvey()" class="w-full sm:w-auto px-8 py-4 bg-blue-600 hover:bg-blue-700 text-white font-bold text-lg rounded-2xl shadow-lg shadow-blue-500/30 hover:shadow-xl hover:shadow-blue-500/40 transform hover:-translate-y-0.5 transition-all duration-200 flex items-center justify-center gap-3 mx-auto group">
                        <span>Empezar con la encuesta</span>
                        <i class="fa-solid fa-arrow-right text-sm transition-transform group-hover:translate-x-1"></i>
                    </button>
                </div>

                <!-- Sección de Resultados (4 Círculos de Porcentaje) -->
                <div>
                    <div class="text-center mb-8">
                        <h2 class="text-2xl font-bold text-slate-800">Resultados Actuales de la Encuesta</h2>
                        <p class="text-slate-500 text-sm mt-1">Estadísticas en tiempo real compartidas entre todos los usuarios</p>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                        
                        <!-- Círculo 1 -->
                        <div class="bg-white/90 backdrop-blur-sm p-6 rounded-2xl border border-slate-100 shadow-md shadow-slate-200/50 flex flex-col items-center text-center hover:shadow-lg transition-shadow">
                            <h3 class="font-bold text-slate-800 text-sm mb-4 h-10 flex items-center justify-center">
                                Círculo 1 — Conocimiento del código de colores
                            </h3>
                            <div class="relative w-36 h-36 mb-4">
                                <svg class="w-full h-full transform -rotate-90" viewBox="0 0 36 36">
                                    <!-- Fondo Rojo (No) -->
                                    <path class="text-red-500" stroke-width="3.8" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                    <!-- Frente Azul (Sí) -->
                                    <path id="circle-1-path" class="text-blue-600 circle-chart-circle" stroke-dasharray="0, 100" stroke-width="3.8" stroke-linecap="round" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                </svg>
                                <div class="absolute inset-0 flex flex-col items-center justify-center">
                                    <span id="circle-1-percent" class="text-2xl font-extrabold text-slate-800">0%</span>
                                    <span class="text-[10px] uppercase font-bold text-blue-600">Lo conoce</span>
                                </div>
                            </div>
                            <!-- Leyenda -->
                            <div class="w-full space-y-1.5 text-xs text-left pt-2 border-t border-slate-100">
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-blue-600 inline-block"></span> Azul: Conoce</span>
                                    <span id="c1-yes-count" class="font-semibold text-slate-700">0</span>
                                </div>
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-red-500 inline-block"></span> Rojo: No lo conoce</span>
                                    <span id="c1-no-count" class="font-semibold text-slate-700">0</span>
                                </div>
                            </div>
                        </div>

                        <!-- Círculo 2 -->
                        <div class="bg-white/90 backdrop-blur-sm p-6 rounded-2xl border border-slate-100 shadow-md shadow-slate-200/50 flex flex-col items-center text-center hover:shadow-lg transition-shadow">
                            <h3 class="font-bold text-slate-800 text-sm mb-4 h-10 flex items-center justify-center">
                                Círculo 2 — Composta casera
                            </h3>
                            <div class="relative w-36 h-36 mb-4">
                                <svg class="w-full h-full transform -rotate-90" viewBox="0 0 36 36">
                                    <path class="text-red-500" stroke-width="3.8" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                    <path id="circle-2-path" class="text-blue-600 circle-chart-circle" stroke-dasharray="0, 100" stroke-width="3.8" stroke-linecap="round" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                </svg>
                                <div class="absolute inset-0 flex flex-col items-center justify-center">
                                    <span id="circle-2-percent" class="text-2xl font-extrabold text-slate-800">0%</span>
                                    <span class="text-[10px] uppercase font-bold text-blue-600">Hace composta</span>
                                </div>
                            </div>
                            <!-- Leyenda -->
                            <div class="w-full space-y-1.5 text-xs text-left pt-2 border-t border-slate-100">
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-blue-600 inline-block"></span> Azul: Hace composta</span>
                                    <span id="c2-yes-count" class="font-semibold text-slate-700">0</span>
                                </div>
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-red-500 inline-block"></span> Rojo: No la hace</span>
                                    <span id="c2-no-count" class="font-semibold text-slate-700">0</span>
                                </div>
                            </div>
                        </div>

                        <!-- Círculo 3 -->
                        <div class="bg-white/90 backdrop-blur-sm p-6 rounded-2xl border border-slate-100 shadow-md shadow-slate-200/50 flex flex-col items-center text-center hover:shadow-lg transition-shadow">
                            <h3 class="font-bold text-slate-800 text-sm mb-4 h-10 flex items-center justify-center">
                                Círculo 3 — Reciclaje con código de colores
                            </h3>
                            <div class="relative w-36 h-36 mb-4">
                                <svg class="w-full h-full transform -rotate-90" viewBox="0 0 36 36">
                                    <path class="text-red-500" stroke-width="3.8" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                    <path id="circle-3-path" class="text-blue-600 circle-chart-circle" stroke-dasharray="0, 100" stroke-width="3.8" stroke-linecap="round" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                </svg>
                                <div class="absolute inset-0 flex flex-col items-center justify-center">
                                    <span id="circle-3-percent" class="text-2xl font-extrabold text-slate-800">0%</span>
                                    <span class="text-[10px] uppercase font-bold text-blue-600">Recicla</span>
                                </div>
                            </div>
                            <!-- Leyenda -->
                            <div class="w-full space-y-1.5 text-xs text-left pt-2 border-t border-slate-100">
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-blue-600 inline-block"></span> Azul: Recicla y usa código</span>
                                    <span id="c3-yes-count" class="font-semibold text-slate-700">0</span>
                                </div>
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-red-500 inline-block"></span> Rojo: No recicla</span>
                                    <span id="c3-no-count" class="font-semibold text-slate-700">0</span>
                                </div>
                            </div>
                        </div>

                        <!-- Círculo 4 -->
                        <div class="bg-white/90 backdrop-blur-sm p-6 rounded-2xl border border-slate-100 shadow-md shadow-slate-200/50 flex flex-col items-center text-center hover:shadow-lg transition-shadow">
                            <h3 class="font-bold text-slate-800 text-sm mb-4 h-10 flex items-center justify-center">
                                Círculo 4 — Uso de bolsas transparentes
                            </h3>
                            <div class="relative w-36 h-36 mb-4">
                                <svg class="w-full h-full transform -rotate-90" viewBox="0 0 36 36">
                                    <path class="text-red-500" stroke-width="3.8" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                    <path id="circle-4-path" class="text-blue-600 circle-chart-circle" stroke-dasharray="0, 100" stroke-width="3.8" stroke-linecap="round" stroke="currentColor" fill="none" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
                                </svg>
                                <div class="absolute inset-0 flex flex-col items-center justify-center">
                                    <span id="circle-4-percent" class="text-2xl font-extrabold text-slate-800">0%</span>
                                    <span class="text-[10px] uppercase font-bold text-blue-600">Usa bolsas</span>
                                </div>
                            </div>
                            <!-- Leyenda -->
                            <div class="w-full space-y-1.5 text-xs text-left pt-2 border-t border-slate-100">
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-blue-600 inline-block"></span> Azul: Utiliza bolsas</span>
                                    <span id="c4-yes-count" class="font-semibold text-slate-700">0</span>
                                </div>
                                <div class="flex items-center justify-between">
                                    <span class="flex items-center gap-1.5"><span class="w-2.5 h-2.5 rounded-full bg-red-500 inline-block"></span> Rojo: No las utiliza</span>
                                    <span id="c4-no-count" class="font-semibold text-slate-700">0</span>
                                </div>
                            </div>
                        </div>

                    </div>
                </div>
            </section>


            <!-- CONTENEDOR DE LA ENCUESTA (Oculto inicialmente) -->
            <section id="survey-screen" class="hidden max-w-xl mx-auto">
                <div class="bg-white/95 backdrop-blur-md rounded-3xl p-8 sm:p-10 shadow-2xl shadow-eco-900/10 border border-eco-100 relative">
                    
                    <!-- Barra de Progreso -->
                    <div class="mb-8">
                        <div class="flex justify-between items-center mb-2">
                            <span id="question-indicator" class="text-xs font-bold text-eco-700 uppercase tracking-wider">
                                Pregunta 1 de 4
                            </span>
                            <span id="progress-percent-text" class="text-xs font-semibold text-slate-400">
                                25% completado
                            </span>
                        </div>
                        <div class="w-full h-2.5 bg-slate-100 rounded-full overflow-hidden">
                            <div id="progress-bar" class="h-full bg-eco-500 rounded-full transition-all duration-300 w-1/4"></div>
                        </div>
                    </div>

                    <!-- PREGUNTA 1 -->
                    <div id="q1-step" class="survey-step fade-in">
                        <h3 class="text-xl sm:text-2xl font-bold text-slate-800 mb-6 leading-snug">
                            ¿Conoces el código de colores para la separación de residuos?
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <button onclick="answerQuestion(1, true)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-eco-500 bg-slate-50/50 hover:bg-eco-50 text-slate-700 hover:text-eco-800 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">✅</span> Sí
                            </button>
                            <button onclick="answerQuestion(1, false)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-red-400 bg-slate-50/50 hover:bg-red-50 text-slate-700 hover:text-red-700 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">❌</span> No
                            </button>
                        </div>
                    </div>

                    <!-- PREGUNTA 2 -->
                    <div id="q2-step" class="survey-step hidden fade-in">
                        <h3 class="text-xl sm:text-2xl font-bold text-slate-800 mb-6 leading-snug">
                            ¿Realizas composta casera en tu casa?
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <button onclick="answerQuestion(2, true)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-eco-500 bg-slate-50/50 hover:bg-eco-50 text-slate-700 hover:text-eco-800 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">✅</span> Sí
                            </button>
                            <button onclick="answerQuestion(2, false)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-red-400 bg-slate-50/50 hover:bg-red-50 text-slate-700 hover:text-red-700 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">❌</span> No
                            </button>
                        </div>
                    </div>

                    <!-- PREGUNTA 3 -->
                    <div id="q3-step" class="survey-step hidden fade-in">
                        <h3 class="text-xl sm:text-2xl font-bold text-slate-800 mb-6 leading-snug">
                            ¿Separas tus residuos y reciclas utilizando el código de colores?
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <button onclick="answerQuestion(3, true)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-eco-500 bg-slate-50/50 hover:bg-eco-50 text-slate-700 hover:text-eco-800 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">✅</span> Sí
                            </button>
                            <button onclick="answerQuestion(3, false)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-red-400 bg-slate-50/50 hover:bg-red-50 text-slate-700 hover:text-red-700 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">❌</span> No
                            </button>
                        </div>
                    </div>

                    <!-- PREGUNTA 4 -->
                    <div id="q4-step" class="survey-step hidden fade-in">
                        <h3 class="text-xl sm:text-2xl font-bold text-slate-800 mb-6 leading-snug">
                            ¿Utilizas bolsas transparentes para separar tus residuos?
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <button onclick="answerQuestion(4, true)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-eco-500 bg-slate-50/50 hover:bg-eco-50 text-slate-700 hover:text-eco-800 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">✅</span> Sí
                            </button>
                            <button onclick="answerQuestion(4, false)" class="p-5 rounded-2xl border-2 border-slate-100 hover:border-red-400 bg-slate-50/50 hover:bg-red-50 text-slate-700 hover:text-red-700 font-bold text-lg flex items-center justify-center gap-3 transition-all duration-200 shadow-sm hover:shadow">
                                <span class="text-2xl">❌</span> No
                            </button>
                        </div>
                    </div>

                    <!-- CANCELAR ENCUESTA -->
                    <div class="mt-6 text-center">
                        <button onclick="cancelSurvey()" class="text-xs font-semibold text-slate-400 hover:text-slate-600 underline">
                            Cancelar y volver al inicio
                        </button>
                    </div>

                </div>
            </section>


            <!-- PANTALLA FINAL / AGRADECIMIENTO (Oculta inicialmente) -->
            <section id="thanks-screen" class="hidden max-w-lg mx-auto fade-in">
                <div class="bg-white/95 backdrop-blur-md rounded-3xl p-8 sm:p-12 shadow-2xl shadow-eco-900/10 border border-eco-100 text-center">
                    <div class="w-20 h-20 bg-eco-100 text-eco-600 rounded-full flex items-center justify-center mx-auto mb-6 text-4xl shadow-inner">
                        🌱
                    </div>
                    
                    <h2 class="text-3xl font-extrabold text-slate-900 mb-2">
                        ¡Gracias por participar!
                    </h2>
                    
                    <p class="text-slate-600 text-base mb-8">
                        Tus respuestas ayudan a mejorar la gestión de residuos y cuidar nuestro medio ambiente en Buenos Aires.
                    </p>

                    <button onclick="resetToHome()" class="px-8 py-3.5 bg-eco-600 hover:bg-eco-700 text-white font-bold rounded-2xl shadow-lg shadow-eco-600/30 transition-all duration-200">
                        Volver a los resultados
                    </button>
                </div>
            </section>

        </div>
    </main>

    <!-- Pie de Página -->
    <footer class="relative z-10 w-full py-6 text-center text-xs font-medium text-slate-500 border-t border-eco-200/40 bg-white/40">
        <p>© Proyecto Buenos Aires Limpio — Por un futuro más verde y sostenible.</p>
    </footer>

</div>

<!-- Firebase SDK para tiempo real en GitHub -->
<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
    import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
    import { getFirestore, doc, onSnapshot, runTransaction } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

    // Configuración de la base de datos
    const appId = typeof __app_id !== 'undefined' ? __app_id : 'buenos-aires-limpio-github';
    const firebaseConfig = typeof __firebase_config !== 'undefined' 
        ? JSON.parse(__firebase_config) 
        : {
            apiKey: "demo-api-key",
            authDomain: "demo-app.firebaseapp.com",
            projectId: "demo-app",
            storageBucket: "demo-app.appspot.com",
            messagingSenderId: "123456789",
            appId: "1:123456789:web:demo"
        };

    const app = initializeApp(firebaseConfig);
    const auth = getAuth(app);
    const db = getFirestore(app);

    const statsDocRef = doc(db, 'artifacts', appId, 'public', 'data', 'stats', 'global');

    // Cargar estado inicial desde LocalStorage para garantizar persistencia local si no hay Firebase configurado
    function loadLocalState() {
        const saved = localStorage.getItem('ba_limpio_stats');
        if (saved) {
            try {
                return JSON.parse(saved);
            } catch (e) {
                console.error("Error al leer datos locales", e);
            }
        }
        return { totalParticipants: 0, q1Yes: 0, q2Yes: 0, q3Yes: 0, q4Yes: 0 };
    }

    // Estado global de los datos
    window.surveyData = loadLocalState();

    function saveLocalState(data) {
        localStorage.setItem('ba_limpio_stats', JSON.stringify(data));
    }

    // Sincronización en directo con fallback a almacenamiento local
    async function initRealtimeData() {
        // Renderizar inmediatamente con los datos guardados en el navegador
        window.updateDashboard();

        try {
            if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                await signInWithCustomToken(auth, __initial_auth_token);
            } else {
                await signInAnonymously(auth);
            }

            onSnapshot(statsDocRef, (snapshot) => {
                if (snapshot.exists()) {
                    const data = snapshot.data();
                    window.surveyData = {
                        totalParticipants: data.totalParticipants || 0,
                        q1Yes: data.q1Yes || 0,
                        q2Yes: data.q2Yes || 0,
                        q3Yes: data.q3Yes || 0,
                        q4Yes: data.q4Yes || 0
                    };
                    saveLocalState(window.surveyData);
                }
                window.updateDashboard();
            }, (error) => {
                console.warn("Usando almacenamiento persistente local:", error);
                window.updateDashboard();
            });
        } catch (error) {
            console.log("Modo local persistente activo:", error);
            window.updateDashboard();
        }
    }

    // Enviar resultados (guardado inmediato)
    window.saveSurveyToCloud = async function(answers) {
        // 1. Actualizar el estado local y guardarlo en LocalStorage de inmediato
        window.surveyData.totalParticipants = (window.surveyData.totalParticipants || 0) + 1;
        if (answers.q1) window.surveyData.q1Yes = (window.surveyData.q1Yes || 0) + 1;
        if (answers.q2) window.surveyData.q2Yes = (window.surveyData.q2Yes || 0) + 1;
        if (answers.q3) window.surveyData.q3Yes = (window.surveyData.q3Yes || 0) + 1;
        if (answers.q4) window.surveyData.q4Yes = (window.surveyData.q4Yes || 0) + 1;

        saveLocalState(window.surveyData);
        window.updateDashboard();

        // 2. Intentar guardar en la nube de fondo si está conectado
        try {
            await runTransaction(db, async (transaction) => {
                const sfDoc = await transaction.get(statsDocRef);
                let current = { totalParticipants: 0, q1Yes: 0, q2Yes: 0, q3Yes: 0, q4Yes: 0 };
                if (sfDoc.exists()) {
                    current = sfDoc.data();
                }

                const updatedData = {
                    totalParticipants: (current.totalParticipants || 0) + 1,
                    q1Yes: (current.q1Yes || 0) + (answers.q1 ? 1 : 0),
                    q2Yes: (current.q2Yes || 0) + (answers.q2 ? 1 : 0),
                    q3Yes: (current.q3Yes || 0) + (answers.q3 ? 1 : 0),
                    q4Yes: (current.q4Yes || 0) + (answers.q4 ? 1 : 0)
                };

                transaction.set(statsDocRef, updatedData, { merge: true });
            });
        } catch (e) {
            console.log("Respuesta registrada exitosamente de forma local.");
        }
    };

    initRealtimeData();
</script>

<!-- Interacciones de la encuesta -->
<script>
    let currentStep = 1;
    let currentAnswers = {};

    document.addEventListener("DOMContentLoaded", function() {
        updateDashboard();
    });

    function startSurvey() {
        currentStep = 1;
        currentAnswers = {};
        
        document.getElementById('home-screen').classList.add('hidden');
        document.getElementById('thanks-screen').classList.add('hidden');
        document.getElementById('survey-screen').classList.remove('hidden');

        showStep(1);
    }

    function showStep(step) {
        for (let i = 1; i <= 4; i++) {
            document.getElementById(`q${i}-step`).classList.add('hidden');
        }
        
        document.getElementById(`q${step}-step`).classList.remove('hidden');
        document.getElementById('question-indicator').innerText = `Pregunta ${step} de 4`;
        const percentage = (step / 4) * 100;
        document.getElementById('progress-bar').style.width = `${percentage}%`;
        document.getElementById('progress-percent-text').innerText = `${percentage}% completado`;
    }

    function answerQuestion(questionNum, answer) {
        currentAnswers[`q${questionNum}`] = answer;

        if (questionNum < 4) {
            currentStep++;
            showStep(currentStep);
        } else {
            submitSurvey();
        }
    }

    async function submitSurvey() {
        if (typeof window.saveSurveyToCloud === 'function') {
            await window.saveSurveyToCloud(currentAnswers);
        } else {
            window.surveyData.totalParticipants++;
            if (currentAnswers.q1) window.surveyData.q1Yes++;
            if (currentAnswers.q2) window.surveyData.q2Yes++;
            if (currentAnswers.q3) window.surveyData.q3Yes++;
            if (currentAnswers.q4) window.surveyData.q4Yes++;
            updateDashboard();
        }

        document.getElementById('survey-screen').classList.add('hidden');
        document.getElementById('thanks-screen').classList.remove('hidden');
    }

    function cancelSurvey() {
        document.getElementById('survey-screen').classList.add('hidden');
        document.getElementById('home-screen').classList.remove('hidden');
    }

    function resetToHome() {
        document.getElementById('thanks-screen').classList.add('hidden');
        document.getElementById('home-screen').classList.remove('hidden');
    }

    function updateDashboard() {
        const data = window.surveyData || { totalParticipants: 0, q1Yes: 0, q2Yes: 0, q3Yes: 0, q4Yes: 0 };
        const total = data.totalParticipants;
        document.getElementById('total-responses-count').innerText = total;

        if (total === 0) {
            for (let i = 1; i <= 4; i++) {
                updateCircle(i, 0, 0, 0);
            }
            return;
        }

        const c1Percent = Math.round((data.q1Yes / total) * 100);
        updateCircle(1, c1Percent, data.q1Yes, total - data.q1Yes);

        const c2Percent = Math.round((data.q2Yes / total) * 100);
        updateCircle(2, c2Percent, data.q2Yes, total - data.q2Yes);

        const c3Percent = Math.round((data.q3Yes / total) * 100);
        updateCircle(3, c3Percent, data.q3Yes, total - data.q3Yes);

        const c4Percent = Math.round((data.q4Yes / total) * 100);
        updateCircle(4, c4Percent, data.q4Yes, total - data.q4Yes);
    }

    function updateCircle(index, percentage, yesCount, noCount) {
        const pathElement = document.getElementById(`circle-${index}-path`);
        const percentText = document.getElementById(`circle-${index}-percent`);
        const yesText = document.getElementById(`c${index}-yes-count`);
        const noText = document.getElementById(`c${index}-no-count`);

        if (pathElement) pathElement.setAttribute('stroke-dasharray', `${percentage}, 100`);
        if (percentText) percentText.innerText = `${percentage}%`;
        if (yesText) yesText.innerText = yesCount;
        if (noText) noText.innerText = noCount;
    }
</script>

</body>
</html>
