
<html lang="es" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eternal | IA & Nutrición Funcional</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'eternal-cream': '#FAF6F0',
                        'eternal-gold': '#C9A84C',
                        'eternal-dark': '#1A1A1A',
                        'eternal-wa': '#25D366',
                    },
                    fontFamily: {
                        serif: ['Cormorant Garamond', 'serif'],
                        sans: ['Inter', 'sans-serif'],
                    },
                }
            }
        }
    </script>

    <style>
        .reveal { opacity: 0; transform: translateY(20px); transition: all 0.7s cubic-bezier(0.4, 0, 0.2, 1); }
        .reveal.active { opacity: 1; transform: translateY(0); }
        .nav-scrolled { background-color: rgba(250, 246, 240, 0.98); box-shadow: 0 4px 20px rgba(0,0,0,0.03); }
        .chip-active { border-color: #C9A84C; background-color: #FAF6F0; color: #C9A84C; }
        
        /* Chat UI Glassmorphism */
        #ai-chat-window {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            transform: scale(0);
            transform-origin: bottom right;
        }
        #ai-chat-window.open { transform: scale(1); }
        .glass-dark { background: rgba(26, 26, 26, 0.95); backdrop-filter: blur(12px); }
        
        /* Typing animation */
        .dot { width: 6px; height: 6px; background: #C9A84C; border-radius: 50%; display: inline-block; animation: bounce 1.4s infinite ease-in-out; }
        .dot:nth-child(1) { animation-delay: -0.32s; }
        .dot:nth-child(2) { animation-delay: -0.16s; }
        @keyframes bounce { 0%, 80%, 100% { transform: scale(0); } 40% { transform: scale(1.0); } }
    </style>
</head>
<body class="bg-eternal-cream text-eternal-dark font-sans selection:bg-eternal-gold selection:text-white">

    <nav id="main-nav" class="fixed top-0 w-full z-50 transition-all duration-300 py-6">
        <div class="container mx-auto px-6 flex justify-between items-center">
            <a href="#inicio" class="flex items-center">
                <img src="logo.png.png" alt="ETERNAL" class="h-8 md:h-10 object-contain" onerror="this.style.display='none'">
                <span class="font-serif text-2xl font-bold tracking-widest text-eternal-gold italic ml-2 md:hidden">ETERNAL</span>
            </a>
            <ul class="hidden md:flex space-x-10 text-xs font-semibold uppercase tracking-widest">
                <li><a href="#inicio" class="hover:text-eternal-gold transition-colors">Inicio</a></li>
                <li><a href="#beneficios" class="hover:text-eternal-gold transition-colors">Ciencia</a></li>
                <li><a href="#catalogo" class="hover:text-eternal-gold transition-colors">Productos</a></li>
                <li><a href="#ia-section" class="text-eternal-gold border-b border-eternal-gold pb-1 font-bold">Nutri-AI</a></li>
            </ul>
            <button id="menu-btn" class="md:hidden text-2xl"><i class="fas fa-bars"></i></button>
        </div>
    </nav>

    <header id="inicio" class="relative h-screen flex items-center justify-center overflow-hidden bg-white">
        <div class="container mx-auto px-6 relative z-10 text-center">
            <div class="reveal max-w-4xl mx-auto">
                <!-- Logo Principal -->
                <div class="mb-10 flex justify-center">
                    <img src="logo.png.png" alt="Eternal Logo" class="w-64 md:w-80 object-contain" onerror="this.src='https://placehold.co/400x100/FFF/C9A84C?text=ETERNAL'">
                </div>
                <div class="mb-6 inline-block px-4 py-1 border border-eternal-gold rounded-full text-[10px] font-bold tracking-[0.2em] text-eternal-gold uppercase">
                    Innovación Nutricional & IA
                </div>
                <h1 class="font-serif text-5xl md:text-7xl mb-8 leading-tight text-eternal-dark">Vivir es un <span class="italic text-eternal-gold">arte continuo</span>.</h1>
                    <a href="#catalogo" class="bg-eternal-dark text-white px-10 py-5 uppercase text-xs tracking-widest font-bold hover:bg-eternal-gold transition-all">Ver Selección</a>
                    <button onclick="toggleChat()" class="bg-eternal-gold text-white px-10 py-5 uppercase text-xs tracking-widest font-bold hover:bg-eternal-dark transition-all">Hablar con IA</button>
                </div>
            </div>
        </div>
    </header>

    <section id="catalogo" class="py-24 bg-eternal-cream">
        <div class="container mx-auto px-6">
            <div class="text-center mb-16 reveal">
                <span class="text-eternal-gold uppercase tracking-[0.3em] text-[10px] font-bold mb-4 block">Experiencia Personalizada</span>
                <h2 class="font-serif text-4xl md:text-5xl">Gama Eternal</h2>
                <p class="mt-4 text-gray-400 max-w-xl mx-auto text-sm">Explora nuestros productos y genera recetas inteligentes con un clic.</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8" id="product-grid">
                <!-- Productos se inyectan via JS -->
            </div>
        </div>
    </section>

    <section id="ia-section" class="py-24 bg-eternal-dark text-white overflow-hidden relative">
        <div class="absolute inset-0 opacity-10">
            <div class="w-full h-full" style="background-image: radial-gradient(#C9A84C 1px, transparent 1px); background-size: 40px 40px;"></div>
        </div>
        <div class="container mx-auto px-6 relative z-10">
            <div class="grid md:grid-cols-2 gap-16 items-center">
                <div class="reveal">
                    <h2 class="font-serif text-5xl mb-8">Ciencia al servicio de tu bienestar.</h2>
                    <p class="text-gray-400 text-lg mb-8 font-light">Nuestro **Nutri-Advisor AI** utiliza el modelo Gemini para ofrecerte asesoría científica sobre cómo los probióticos y proteínas de Eternal mejoran tu longevidad activa.</p>
                    <ul class="space-y-4 mb-10">
                        <li class="flex items-center space-x-4"><i class="fas fa-microscope text-eternal-gold"></i> <span>Análisis basado en estudios geriátricos.</span></li>
                        <li class="flex items-center space-x-4"><i class="fas fa-brain text-eternal-gold"></i> <span>Recomendaciones personalizadas por perfil.</span></li>
                    </ul>
                    <button onclick="toggleChat()" class="border border-eternal-gold text-eternal-gold px-10 py-4 uppercase text-xs font-bold tracking-widest hover:bg-eternal-gold hover:text-white transition-all">Iniciar Consulta Gratuita</button>
                </div>
                <div class="reveal">
                    <div class="bg-eternal-cream/5 p-1 border border-white/10 rounded-[40px]">
                        <div class="bg-eternal-dark rounded-[38px] p-8">
                            <div class="flex items-center space-x-4 mb-8">
                                <div class="w-12 h-12 bg-eternal-gold rounded-full flex items-center justify-center"><i class="fas fa-robot text-white"></i></div>
                                <div>
                                    <h4 class="font-bold text-sm">IA Advisor</h4>
                                    <p class="text-[10px] text-gray-500 uppercase">En línea ahora</p>
                                </div>
                            </div>
                            <div class="space-y-4">
                                <div class="bg-white/5 p-4 rounded-2xl text-sm italic text-gray-300">"¿Cómo ayuda el Eternal Greek a mi densidad ósea después de los 60 años?"</div>
                                <div class="bg-eternal-gold/10 p-4 rounded-2xl text-sm border-l-2 border-eternal-gold text-eternal-gold font-light">"El calcio iónico en nuestra fórmula Greek, potenciado con Vitamina D3, acelera la absorción mineral en un 22% según estudios..."</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <div id="ai-chat-window" class="fixed bottom-24 right-6 w-[90%] md:w-[400px] h-[550px] z-[60] glass-dark border border-white/10 rounded-[30px] flex flex-col shadow-2xl overflow-hidden">
        <div class="p-6 border-b border-white/5 flex justify-between items-center bg-eternal-gold/10">
            <div class="flex items-center space-x-3">
                <div class="w-10 h-10 bg-eternal-gold rounded-full flex items-center justify-center shadow-lg"><i class="fas fa-leaf text-white"></i></div>
                <div>
                    <h3 class="text-white text-sm font-bold">Nutri-Advisor Eternal</h3>
                    <p class="text-[9px] text-eternal-gold font-bold uppercase tracking-widest">Powered by Gemini AI</p>
                </div>
            </div>
            <button onclick="toggleChat()" class="text-gray-400 hover:text-white"><i class="fas fa-times"></i></button>
        </div>
        
        <div id="chat-messages" class="flex-1 overflow-y-auto p-6 space-y-4 scroll-smooth">
            <div class="bg-white/5 p-4 rounded-2xl text-xs text-gray-300 max-w-[85%] self-start border border-white/5">
                Hola, soy el asistente de salud de **Eternal**. ¿Deseas saber cómo optimizar tu nutrición funcional hoy?
            </div>
        </div>

        <div id="typing-indicator" class="px-6 py-2 hidden">
            <div class="flex space-x-1">
                <div class="dot"></div>
                <div class="dot"></div>
                <div class="dot"></div>
            </div>
        </div>

        <div class="p-6 bg-eternal-dark">
            <div class="relative">
                <input type="text" id="user-input" placeholder="Pregunta sobre tu salud..." class="w-full bg-white/5 border border-white/10 rounded-2xl p-4 text-sm text-white focus:outline-none focus:border-eternal-gold transition-all pr-12">
                <button onclick="sendMessage()" class="absolute right-3 top-1/2 -translate-y-1/2 text-eternal-gold hover:text-white transition-colors">
                    <i class="fas fa-paper-plane"></i>
                </button>
            </div>
            <p class="text-[8px] text-gray-500 mt-4 text-center">Asesoría de carácter informativo. Consulte siempre a su médico.</p>
        </div>
    </div>

    <!-- Botón Flotante AI -->
    <button onclick="toggleChat()" class="fixed bottom-6 right-6 w-14 h-14 bg-eternal-gold text-white rounded-full flex items-center justify-center text-xl shadow-2xl z-50 hover:scale-110 transition-transform">
        <i class="fas fa-magic"></i>
    </button>

    <footer class="bg-eternal-cream py-20 border-t border-gray-100">
        <div class="container mx-auto px-6 text-center">
            <h2 class="font-serif text-4xl font-bold italic text-eternal-gold mb-4">ETERNAL</h2>
            <p class="text-[10px] text-gray-400 uppercase tracking-widest">&copy; 2024 Eternal México. Ciencia, nutrición y madurez plena.</p>
        </div>
    </footer>

    <script>
        const apiKey = ""; // Canvas proveerá la key
        const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${apiKey}`;

        const productos = [
            { 
                id: 1, 
                sabor: 'natural', 
                nombre: 'Eternal Natural', 
                tipo: 'Botella 1 Litro', 
                basePrice: 85, 
                img: 'natural-1lt.jpg.png',
                context: 'Nutrición pura sin azúcar para vitalidad diaria.' 
            },
            { 
                id: 2, 
                sabor: 'natural', 
                nombre: 'Eternal Natural Go', 
                tipo: 'Botella 250 ml', 
                basePrice: 28, 
                img: 'natural-250ml.jpg.png',
                context: 'Formato práctico para llevar.' 
            },
            { 
                id: 3, 
                sabor: 'fresa', 
                nombre: 'Eternal Wild Berry', 
                tipo: 'Botella 1 Litro', 
                basePrice: 89, 
                img: 'fresa-1lt.jpg.png',
                context: 'Rico en antioxidantes naturales de fresas seleccionadas.' 
            },
            { 
                id: 4, 
                sabor: 'fresa', 
                nombre: 'Eternal Berry Go', 
                tipo: 'Botella 250 ml', 
                basePrice: 30, 
                img: 'fresa-250ml.jpg.jpg',
                context: 'Energía y sabor en cada sorbo.' 
            },
            { 
                id: 5, 
                sabor: 'durazno', 
                nombre: 'Eternal Peach', 
                tipo: 'Botella 1 Litro', 
                basePrice: 89, 
                img: 'durazno-1lt.jpg.png',
                context: 'Digestión suave y sabor aterciopelado.' 
            },
            { 
                id: 6, 
                sabor: 'durazno', 
                nombre: 'Eternal Peach Go', 
                tipo: 'Botella 250 ml', 
                basePrice: 30, 
                img: 'durazno-250ml.jpg.png',
                context: 'Tu snack saludable favorito.' 
            },
            { 
                id: 7, 
                sabor: 'fresa', 
                nombre: 'Fresa Edición Espesa', 
                tipo: 'Frasco Premium 1L', 
                basePrice: 99, 
                img: 'fresa-espesa-1lt.jpg.jpg',
                context: 'Textura cremosa estilo griego con trozos de fruta.' 
            },
            { 
                id: 8, 
                sabor: 'durazno', 
                nombre: 'Durazno Edición Espesa', 
                tipo: 'Frasco Premium 1L', 
                basePrice: 99, 
                img: 'durazno-espesa-1lt.jpg.jpg',
                context: 'La máxima expresión de cremosidad y nutrición.' 
            },
            { 
                id: 9, 
                sabor: 'durazno', 
                nombre: 'Durazno Espesa Petit', 
                tipo: 'Tarro 150g', 
                basePrice: 34, 
                img: 'durazno-espesa-150g.jpg.jpg',
                context: 'Dosis perfecta de proteína y probióticos.' 
            },
            { 
                id: 10, 
                sabor: 'natural', 
                nombre: 'Natural Edición Espesa', 
                tipo: 'Frasco Premium 1L', 
                basePrice: 95, 
                img: 'natural-espesa-1lt.jpg.jpg',
                context: 'La pureza de Eternal en textura estilo griego.' 
            },
            { 
                id: 11, 
                sabor: 'natural', 
                nombre: 'Natural Espesa Petit', 
                tipo: 'Tarro 150g', 
                basePrice: 32, 
                img: 'natural-250ml.jpg.jpg',
                context: 'Snack puro y denso para nutrición muscular.' 
            }
        ];

        function renderProducts() {
            const productGrid = document.getElementById('product-grid');
            productGrid.innerHTML = '';
            productos.forEach((p, idx) => {
                const card = document.createElement('div');
                card.className = 'reveal bg-white p-6 rounded-[30px] border border-gray-100 hover:border-eternal-gold/30 transition-all group shadow-sm hover:shadow-xl';
                card.style.transitionDelay = `${idx * 0.05}s`;
                card.innerHTML = `
                    <div class="relative mb-6 overflow-hidden rounded-2xl bg-eternal-cream aspect-square flex items-center justify-center p-4">
                        <img src="${p.img}" alt="${p.nombre}" class="w-full h-full object-contain group-hover:scale-105 transition-transform duration-700" onerror="this.src='https://placehold.co/400x400/FAF6F0/C9A84C?text=Cargando...'">
                        ${p.nombre.includes('Espesa') ? '<span class="absolute top-4 right-4 bg-eternal-gold text-white text-[8px] font-bold px-3 py-1 rounded-full uppercase tracking-widest">Premium</span>' : ''}
                    </div>
                    <h3 class="font-serif text-xl mb-1">${p.nombre}</h3>
                    <p class="text-[10px] text-gray-400 mb-4 uppercase tracking-widest">${p.tipo}</p>
                    <div class="mb-6"><span class="text-2xl font-bold text-eternal-gold">$${p.basePrice} <small class="text-[10px]">MXN</small></span></div>
                    <div class="flex flex-col gap-2">
                        <button onclick="generateRecipe('${p.nombre}')" class="w-full py-3 bg-white border border-eternal-dark text-eternal-dark rounded-xl text-[10px] font-bold uppercase tracking-widest hover:bg-eternal-dark hover:text-white transition-all">
                            <i class="fas fa-utensils mr-2"></i> Receta IA
                        </button>
                        <button onclick="orderWA('${p.nombre}')" class="w-full py-3 bg-eternal-dark text-white rounded-xl text-[10px] font-bold uppercase tracking-widest hover:bg-eternal-gold transition-all">
                            Solicitar Pedido
                        </button>
                    </div>
                `;
                productGrid.appendChild(card);
            });
        }

        function toggleChat() {
            document.getElementById('ai-chat-window').classList.toggle('open');
        }

        async function callGemini(query, systemPrompt) {
            try {
                const payload = {
                    contents: [{ parts: [{ text: query }] }],
                    tools: [{ "google_search": {} }],
                    systemInstruction: { parts: [{ text: systemPrompt }] }
                };
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                const result = await response.json();
                return result.candidates?.[0]?.content?.parts?.[0]?.text || "Lo siento, tuve un problema al procesar tu solicitud.";
            } catch (e) {
                return "Error de conexión con el servidor de salud IA.";
            }
        }

        async function sendMessage() {
            const input = document.getElementById('user-input');
            const container = document.getElementById('chat-messages');
            const query = input.value.trim();
            if (!query) return;

            // UI Feedback
            appendMessage('user', query);
            input.value = '';
            const indicator = document.getElementById('typing-indicator');
            indicator.classList.remove('hidden');

            const systemPrompt = `Eres el "Nutri-Advisor" oficial de Eternal Premium Yogurt México. 
            Tu misión es asesorar a personas de 50+ años sobre nutrición funcional. 
            Usa un tono empático, profesional y elegante (Premium). 
            Eternal ofrece 4 variantes: Natural (sin azúcar), Greek (alta proteína), Fresa (antioxidantes) y Durazno (digestivo). 
            Cita beneficios científicos del calcio, vitamina D y probióticos.
            IMPORTANTE: Si te preguntan algo médico grave, sugiere siempre consultar a un profesional.`;

            const responseText = await callGemini(query, systemPrompt);
            indicator.classList.add('hidden');
            appendMessage('ai', responseText);
        }

        function appendMessage(role, text) {
            const container = document.getElementById('chat-messages');
            const div = document.createElement('div');
            div.className = role === 'user' 
                ? 'bg-eternal-gold p-4 rounded-2xl rounded-tr-none text-xs text-white max-w-[85%] self-end ml-auto'
                : 'bg-white/5 p-4 rounded-2xl rounded-tl-none text-xs text-gray-300 max-w-[85%] self-start border border-white/5';
            div.innerHTML = text.replace(/\*\*(.*?)\*\*/g, '<b>$1</b>');
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
        }

        async function generateRecipe(productName) {
            toggleChat();
            const container = document.getElementById('chat-messages');
            container.innerHTML += `<div class="text-[10px] text-gray-500 text-center italic py-2">Generando receta saludable con ${productName}...</div>`;
            
            const recipePrompt = `Genera una receta de snack o desayuno saludable de menos de 10 minutos usando ${productName}. 
            Enfócate en beneficios para una persona mayor de 50 años (fácil de digerir, alto en calcio o proteína). 
            Estructura: Nombre, Ingredientes, Paso a paso breve.`;
            
            const systemPrompt = "Eres un Chef especializado en nutrición gerontológica.";
            const recipe = await callGemini(recipePrompt, systemPrompt);
            
            appendMessage('ai', recipe);
        }

        window.onload = () => {
            renderProducts();
            
            // Animaciones Scroll
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) entry.target.classList.add('active');
                });
            }, { threshold: 0.1 });
            document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

            // Escuchar Enter en Chat
            document.getElementById('user-input').addEventListener('keypress', (e) => {
                if (e.key === 'Enter') sendMessage();
            });
        };

        window.orderWA = (name) => {
            const msg = encodeURIComponent(`Hola Eternal 🥛, me interesa pedir: ${name}. Vi una recomendación de la IA.`);
            window.open(`https://wa.me/521234567890?text=${msg}`, '_blank');
        };

        window.addEventListener('scroll', () => {
            const nav = document.getElementById('main-nav');
            window.scrollY > 50 ? nav.classList.add('nav-scrolled') : nav.classList.remove('nav-scrolled');
        });
    </script>
</body>
</html>
