[index.html](https://github.com/user-attachments/files/27719299/index.html)
<!-- Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<!-- Tailwind CSS (via CDN para utilitários extras se necessário, mas as estilos principais estão no style) -->
<script src="https://cdn.tailwindcss.com"></script>

<style>
    /* Variáveis CSS */
    :root {
        --primary-green: #00FF7F;
        --dark-bg: #0a0a0a;
        --dark-secondary: #1a1a1a;
        --dark-tertiary: #2a2a2a;
        --text-light: #e0e0e0;
        --text-muted: #a0a0a0;
        --accent-blue: #00d4ff;
        --glass-bg: rgba(255, 255, 255, 0.05);
        --glass-border: rgba(0, 255, 127, 0.2);
    }

    /* Reset e Base */
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    html {
        scroll-behavior: smooth;
    }

    body {
        font-family: 'Rajdhani', sans-serif;
        background: var(--dark-bg);
        color: var(--text-light);
        line-height: 1.6;
        overflow-x: hidden;
    }

    /* Gradient Background */
    body::before {
        content: '';
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: 
            radial-gradient(circle at 20% 80%, rgba(0, 255, 127, 0.1) 0%, transparent 50%),
            radial-gradient(circle at 80% 20%, rgba(0, 212, 255, 0.05) 0%, transparent 50%),
            radial-gradient(circle at 40% 40%, rgba(0, 255, 127, 0.03) 0%, transparent 50%);
        pointer-events: none;
        z-index: 1;
    }

    /* Typography */
    h1, h2, h3 {
        font-family: 'Orbitron', monospace;
        font-weight: 700;
        line-height: 1.2;
    }

    h1 {
        font-size: clamp(2rem, 5vw, 3.5rem);
        font-weight: 900;
        background: linear-gradient(135deg, var(--primary-green), var(--accent-blue));
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        text-transform: uppercase;
        letter-spacing: 0.05em;
    }

    h2 {
        font-size: clamp(1.5rem, 3vw, 2.5rem);
        color: var(--primary-green);
        margin-bottom: 1rem;
        text-transform: uppercase;
        letter-spacing: 0.03em;
        text-align: center;
    }

    h3 {
        font-size: clamp(1.2rem, 2vw, 1.8rem);
        color: var(--accent-blue);
        margin-bottom: 0.5rem;
    }

    /* Header e Navegação */
    header {
        position: fixed;
        top: 0;
        width: 100%;
        background: rgba(10, 10, 10, 0.95);
        backdrop-filter: blur(20px);
        border-bottom: 1px solid var(--glass-border);
        z-index: 1000;
        transition: all 0.3s ease;
    }

    header.scrolled {
        background: rgba(10, 10, 10, 0.98);
        box-shadow: 0 4px 20px rgba(0, 255, 127, 0.1);
    }

    nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 5%;
        max-width: 1400px;
        margin: 0 auto;
    }

    @keyframes neonPulse {
        from { text-shadow: 0 0 20px rgba(0, 255, 127, 0.5); }
        to { text-shadow: 0 0 30px rgba(0, 255, 127, 0.8), 0 0 40px rgba(0, 255, 127, 0.4); }
    }

    .nav-links {
        display: flex;
        list-style: none;
        gap: 2rem;
        align-items: center;
    }

    .nav-links a {
        color: var(--text-light);
        text-decoration: none;
        font-weight: 500;
        transition: all 0.3s ease;
        position: relative;
        padding: 0.5rem 0;
    }

    .nav-links a::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 0;
        height: 2px;
        background: linear-gradient(90deg, var(--primary-green), var(--accent-blue));
        transition: width 0.3s ease;
    }

    .nav-links a:hover::after {
        width: 100%;
    }

    .nav-links a:hover {
        color: var(--primary-green);
    }

    .cta-button {
        background: linear-gradient(135deg, var(--primary-green), var(--accent-blue));
        color: var(--dark-bg);
        padding: 0.8rem 1.5rem;
        border: none;
        border-radius: 5px;
        font-weight: 700;
        text-transform: uppercase;
        letter-spacing: 0.05em;
        cursor: pointer;
        text-decoration: none;
        display: inline-block;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(0, 255, 127, 0.3);
    }

    .cta-button:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 25px rgba(0, 255, 127, 0.5);
    }

    /* Main Container */
    main {
        position: relative;
        z-index: 2;
    }

    /* Sections */
    section {
        padding: 5rem 5%;
        max-width: 1400px;
        margin: 0 auto;
        opacity: 0;
        transform: translateY(20px);
        transition: opacity 0.8s ease, transform 0.8s ease;
    }

    section.fade-in {
        opacity: 1;
        transform: translateY(0);
    }

    /* Hero Section */
    #hero {
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        padding: 0;
        overflow: hidden;
        opacity: 1; /* Hero shows immediately */
        transform: none;
    }

    .hero-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: url('https://picsum.photos/seed/cyberpunk-barber-interior/1920x1080.jpg') center/cover;
        filter: brightness(0.3) saturate(1.2);
        z-index: -1;
    }

    .hero-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(
            135deg,
            rgba(0, 255, 127, 0.1) 0%,
            rgba(0, 212, 255, 0.05) 50%,
            rgba(10, 10, 10, 0.8) 100%
        );
        z-index: -1;
    }

    .hero-content {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 4rem;
        align-items: center;
        max-width: 1400px;
        width: 100%;
        padding: 2rem;
    }

    .hero-text {
        text-align: left;
    }

    .hero-subtitle {
        font-size: 1.2rem;
        color: var(--text-muted);
        margin-bottom: 2rem;
        font-weight: 300;
    }

    .hero-cta {
        margin-top: 2rem;
        display: inline-block;
    }

    /* Diferenciais Cards */
    .hero-diferenciais {
        position: relative;
        height: 440px;
    }

    .carousel-container {
        position: relative;
        height: 440px;
        width: 100%;
        margin-top: 1.5rem;
    }

    .diferencial-card {
        position: absolute;
        background: var(--dark-bg);
        border: 1px solid rgba(0, 255, 127, 0.1);
        border-radius: 20px;
        padding: 0;
        width: 280px;
        height: 400px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        text-align: center;
        box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5), 0 0 15px rgba(0, 255, 127, 0.05);
        overflow: hidden;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .diferencial-card::after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        border-radius: 20px;
        border: 2px solid transparent;
        background: linear-gradient(135deg, rgba(0, 255, 127, 0.8), rgba(0, 212, 255, 0.8)) border-box;
        -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
        -webkit-mask-composite: xor;
        mask-composite: exclude;
        pointer-events: none;
        opacity: 0.2;
        transition: opacity 0.5s ease;
    }

    .diferencial-card:hover::after {
        opacity: 0.8;
    }

    .diferencial-card:hover {
        box-shadow: 0 15px 50px rgba(0, 0, 0, 0.6), 0 0 30px rgba(0, 255, 127, 0.2);
        transform: translate(-50%, calc(-50% - 5px)) !important;
    }

    .hero-diferenciais-text {
        text-align: center;
        margin-bottom: 2rem;
        font-size: 1.1rem;
        color: var(--primary-green);
        font-weight: 500;
    }

    /* Glassmorphism Cards */
    .glass-card {
        background: var(--glass-bg);
        backdrop-filter: blur(10px);
        border: 1px solid var(--glass-border);
        border-radius: 15px;
        padding: 2rem;
        transition: all 0.3s ease;
    }

    .glass-card:hover {
        transform: translateY(-5px);
        box-shadow: 0 10px 30px rgba(0, 255, 127, 0.2);
        border-color: rgba(0, 255, 127, 0.4);
    }

    /* Sobre Section */
    #sobre {
        background: linear-gradient(135deg, var(--dark-secondary), var(--dark-bg));
        border-radius: 20px;
        margin: 2rem auto;
    }

    .mission-card {
        text-align: center;
        max-width: 800px;
        margin: 0 auto;
    }

    /* Serviços Section */
    #servicos {
        background: var(--dark-secondary);
        border-radius: 20px;
        margin: 2rem auto;
    }

    .servicos-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
        margin-top: 3rem;
    }

    .servico-card {
        background: var(--glass-bg);
        border: 1px solid var(--glass-border);
        border-radius: 15px;
        padding: 2rem;
        text-align: center;
        transition: all 0.3s ease;
        position: relative;
        overflow: hidden;
    }

    .servico-card::before {
        content: '';
        position: absolute;
        top: -50%;
        left: -50%;
        width: 200%;
        height: 200%;
        background: linear-gradient(45deg, transparent, rgba(0, 255, 127, 0.1), transparent);
        transform: rotate(45deg);
        transition: all 0.5s ease;
        opacity: 0;
    }

    .servico-card:hover::before {
        animation: sweep 0.5s ease forwards;
    }

    @keyframes sweep {
        0% { transform: rotate(45deg) translateX(-100%); opacity: 0; }
        50% { opacity: 1; }
        100% { transform: rotate(45deg) translateX(100%); opacity: 0; }
    }

    .servico-card:hover {
        transform: translateY(-10px);
        border-color: var(--primary-green);
    }

    .servico-icon {
        font-size: 3rem;
        margin-bottom: 1rem;
        color: var(--primary-green);
    }

    /* Equipe Section */
    #equipe {
        background: linear-gradient(135deg, var(--dark-bg), var(--dark-secondary));
        border-radius: 20px;
        margin: 2rem auto;
    }

    .equipe-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
        margin-top: 3rem;
    }

    .equipe-card {
        background: var(--glass-bg);
        border: 1px solid var(--glass-border);
        border-radius: 15px;
        padding: 2rem;
        text-align: center;
        transition: all 0.3s ease;
    }

    .equipe-card:hover {
        transform: translateY(-5px);
        border-color: var(--accent-blue);
    }

    .equipe-foto {
        width: 250px;
        height: 300px;
        border-radius: 15px;
        margin: 0 auto 1rem;
        border: 3px solid var(--primary-green);
        object-fit: cover;
    }

    /* Avaliações Section */
    #avaliacoes {
        background: var(--dark-secondary);
        border-radius: 20px;
        margin: 2rem auto;
    }

    .avaliacoes-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
        margin-top: 3rem;
    }

    .avaliacao-card {
        background: var(--glass-bg);
        border: 1px solid var(--glass-border);
        border-radius: 15px;
        padding: 2rem;
        transition: all 0.3s ease;
    }

    .avaliacao-card:hover {
        transform: translateY(-5px);
        border-color: var(--primary-green);
    }

    .stars {
        color: #ffd700;
        margin-bottom: 1rem;
    }

    .avaliacao-texto {
        font-style: italic;
        margin-bottom: 1rem;
        color: var(--text-light);
    }

    .avaliacao-cliente {
        font-weight: 600;
        color: var(--primary-green);
    }

    /* Contato Section */
    #contato {
        background: linear-gradient(135deg, var(--dark-bg), var(--dark-secondary));
        border-radius: 20px;
        margin: 2rem auto;
    }

    .contato-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 3rem;
        margin-top: 3rem;
    }

    .contato-info {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
    }

    .contato-item {
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .contato-icon {
        font-size: 1.5rem;
        color: var(--primary-green);
    }

    .map-container {
        border-radius: 15px;
        overflow: hidden;
        height: 400px;
        border: 1px solid var(--glass-border);
    }

    .map-container iframe {
        width: 100%;
        height: 100%;
        border: none;
    }

    .whatsapp-cta {
        background: linear-gradient(135deg, #25D366, #128C7E);
        color: white;
        padding: 1rem 2rem;
        border: none;
        border-radius: 50px;
        font-weight: 700;
        text-transform: uppercase;
        letter-spacing: 0.05em;
        cursor: pointer;
        text-decoration: none;
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(37, 211, 102, 0.3);
        font-size: 1.1rem;
        justify-content: center;
    }

    .whatsapp-cta:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 25px rgba(37, 211, 102, 0.5);
    }

    /* Footer */
    footer {
        background: var(--dark-bg);
        border-top: 1px solid var(--glass-border);
        padding: 3rem 5%;
        margin-top: 4rem;
    }

    .footer-content {
        max-width: 1400px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 2rem;
    }

    .footer-section h3 {
        color: var(--primary-green);
        margin-bottom: 1rem;
        font-size: 1.2rem;
    }

    .footer-links {
        list-style: none;
    }

    .footer-links li {
        margin-bottom: 0.5rem;
    }

    .footer-links a {
        color: var(--text-muted);
        text-decoration: none;
        transition: color 0.3s ease;
    }

    .footer-links a:hover {
        color: var(--primary-green);
    }

    .social-links {
        display: flex;
        gap: 1rem;
        margin-top: 1rem;
    }

    .social-links a {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
        background: var(--glass-bg);
        border: 1px solid var(--glass-border);
        border-radius: 50%;
        color: var(--primary-green);
        text-decoration: none;
        transition: all 0.3s ease;
    }

    .social-links a:hover {
        background: var(--primary-green);
        color: var(--dark-bg);
        transform: translateY(-3px);
    }

    .footer-bottom {
        text-align: center;
        margin-top: 2rem;
        padding-top: 2rem;
        border-top: 1px solid var(--glass-border);
        color: var(--text-muted);
    }

    /* Responsive Design */
    .mobile-menu-toggle {
        display: none;
        background: none;
        border: none;
        color: var(--primary-green);
        font-size: 1.5rem;
        cursor: pointer;
        z-index: 1001;
    }

    @media (max-width: 968px) {
        .hero-content {
            grid-template-columns: 1fr;
            gap: 2rem;
            text-align: center;
        }

        .hero-text {
            text-align: center;
        }

        .hero-diferenciais {
            height: 480px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1rem;
            margin-top: 2rem;
            width: 100%;
        }
    }

    @media (max-width: 768px) {
        .nav-links {
            position: fixed;
            top: 0;
            right: -100%;
            width: 250px;
            height: 100vh;
            background: rgba(10, 10, 10, 0.98);
            flex-direction: column;
            padding: 5rem 2rem 2rem;
            transition: right 0.3s ease;
            border-left: 1px solid var(--glass-border);
        }

        .nav-links.active {
            right: 0;
        }

        .mobile-menu-toggle {
            display: block;
        }

        .contato-grid {
            grid-template-columns: 1fr;
        }

        .hero-background {
            filter: brightness(0.2);
        }

        h1 {
            font-size: 2rem;
        }

        section {
            padding: 3rem 5%;
        }

        .avaliacoes-grid {
            grid-template-columns: 1fr;
        }
    }

    /* Scroll Indicator */
    .scroll-indicator {
        position: absolute;
        bottom: 30px;
        left: 50%;
        transform: translateX(-50%);
        color: var(--primary-green);
        font-size: 2rem;
        animation: bounce 2s infinite;
    }

    @keyframes bounce {
        0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
        40% { transform: translateX(-50%) translateY(-10px); }
        60% { transform: translateX(-50%) translateY(-5px); }
    }

    /* Neon Lines Animation */
    .neon-line {
        height: 1px;
        background: linear-gradient(90deg, transparent, var(--primary-green), transparent);
        margin: 2rem auto;
        animation: neonFlow 3s ease-in-out infinite;
        max-width: 200px;
    }

    @keyframes neonFlow {
        0%, 100% { opacity: 0.3; transform: scaleX(0.8); }
        50% { opacity: 1; transform: scaleX(1); }
    }
</style><header id="mainHeader">
    <nav>
        <a href="#hero" class="flex items-center gap-3 no-underline group" aria-label="Barbearia Styllus Mafra - Início">
            <!-- Brasão Oval -->
            <div class="relative flex items-center justify-center w-12 h-14 sm:w-14 sm:h-16 bg-[#0a0a0a] rounded-[50%] border-2 border-[#00FF7F] shadow-none overflow-hidden transition-all duration-300">
                <span class="text-2xl sm:text-3xl z-10 transition-transform duration-300 hover:scale-110">💈</span>
            </div>
            <!-- Textos Principais -->
            <div class="flex flex-col items-start justify-center text-left">
                <span class="font-['Orbitron'] text-lg sm:text-xl font-bold text-[#00FF7F] tracking-wide uppercase transition-colors">
                    Styllus Mafra
                </span>
                <span class="font-['Rajdhani'] text-[0.65rem] sm:text-xs font-bold text-gray-300 tracking-[0.35em] uppercase mt-0.5">
                    Barbearia
                </span>
            </div>
        </a>
        <ul class="nav-links" id="navLinks">
            <li><a href="#servicos" aria-label="Navegar para Serviços">Serviços</a></li>
            <li><a href="#equipe" aria-label="Navegar para Equipe">Equipe</a></li>
            <li><a href="#avaliacoes" aria-label="Navegar para Avaliações">Avaliações</a></li>
            <li><a href="#contato" aria-label="Navegar para Contato">Contato</a></li>
            <li>
                <a href="https://wa.me/5511983930836?text=Ol%C3%A1%2C%20vi%20o%20site%20da%20Barbearia%20Styllus%20Mafra%20e%20gostaria%20de%20agendar%20um%20hor%C3%A1rio." class="cta-button" aria-label="Agendar horário via WhatsApp" target="_blank" rel="noreferrer">
                    Agendar Horário
                </a>
            </li>
        </ul>
        <button class="mobile-menu-toggle" id="mobileMenuToggle" aria-label="Menu mobile">
            ☰
        </button>
    </nav>
</header>

<main>
    <section id="hero" aria-labelledby="hero-title">
        <div class="hero-background"></div>
        <div class="hero-overlay"></div>
        <div class="hero-content">
            <div class="hero-text">
                <h1 id="hero-title">Barbearia Styllus Mafra: O Futuro do Estilo Masculino em Osasco</h1>
                <p class="hero-subtitle">
                    Experimente a revolução nos cuidados masculinos com cortes modernos, ambiente futurista e atendimento de excelência
                </p>
                <div class="hero-cta">
                    <a href="https://wa.me/5511983930836?text=Ol%C3%A1%2C%20vi%20o%20site%20da%20Barbearia%20Styllus%20Mafra%20e%20gostaria%20de%20agendar%20um%20hor%C3%A1rio." class="cta-button" aria-label="Agende seu horário agora" target="_blank" rel="noreferrer">
                        Agende Seu Horário
                    </a>
                </div>
            </div>
            <div class="hero-diferenciais">
                <div class="hero-diferenciais-text leading-tight mb-2 font-['Orbitron'] tracking-wide">
                    💈 Sua barbearia com áreas de jogos, TV, game, fliperama, narguile, churrasco e drinks 💈
                </div>
                <div class="carousel-container" id="carouselContainer">
                    <!-- Cards will be populated by JS -->
                </div>
            </div>
        </div>
        <div class="scroll-indicator">↓</div>
    </section>

    <section id="sobre" aria-labelledby="sobre-title">
        <div class="glass-card">
            <h2 id="sobre-title">Sobre a Styllus Mafra</h2>
            <div class="neon-line"></div>
            <div class="sobre-content">
                <div class="mission-card">
                    <h3>Nossa Missão</h3>
                    <p>
                        A Barbearia Styllus Mafra, localizada no centro de Osasco, oferece serviços de cortes em geral e com preço ótimo. Nossa equipe de barbeiros experientes está pronta para proporcionar uma experiência única, com atendimento personalizado e cortes variados como degrade, social, design navalhado e muito mais. Venha nos visitar e descubra o melhor em cuidados masculinos.
                    </p>
                    <p>
                        Combinamos tradição e tecnologia para criar um ambiente onde cada cliente se sente especial. Nossa filosofia é simples: qualidade excepcional, atenção aos detalhes e um toque futurista em cada serviço.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <section id="servicos" aria-labelledby="servicos-title">
        <h2 id="servicos-title">Nossos Serviços</h2>
        <div class="neon-line"></div>
        <div class="servicos-grid">
            <article class="servico-card">
                <div class="servico-icon">⚡</div>
                <h3>Corte Degrade</h3>
                <p>
                    Transforme seu visual com nosso degrade moderno e preciso. Técnica avançada que cria transições suaves e um acabamento impecável.
                </p>
            </article>
            
            <article class="servico-card">
                <div class="servico-icon">🎯</div>
                <h3>Corte Social</h3>
                <p>
                    O clássico que nunca sai de moda. Corte elegante e versátil, perfeito para qualquer ocasião profissional ou casual.
                </p>
            </article>
            
            <article class="servico-card">
                <div class="servico-icon">🔥</div>
                <h3>Design Navalhado</h3>
                <p>
                    Expressão máxima de estilo com designs personalizados. Arte navalhada que transforma seu cabelo em uma obra prima única.
                </p>
            </article>
            
            <article class="servico-card">
                <div class="servico-icon">💎</div>
                <h3>Barba Modelada</h3>
                <p>
                    Barba perfeitamente alinhada e estilizada. Inclui tratamento com produtos premium para uma barba saudável e com aspecto impecável.
                </p>
            </article>
            
            <article class="servico-card">
                <div class="servico-icon">🚀</div>
                <h3>Pacote Completo</h3>
                <p>
                    Experiência completa com corte + barba. O pacote premium que combina todos nossos serviços para uma transformação total.
                </p>
            </article>
            
            <article class="servico-card">
                <div class="servico-icon">✨</div>
                <h3>Tratamento Capilar</h3>
                <p>
                    Hidratação e tratamento personalizado para seu cabelo. Produtos de última geração para cabelos saudáveis e com brilho intenso.
                </p>
            </article>
        </div>
    </section>

    <section id="equipe" aria-labelledby="equipe-title">
        <h2 id="equipe-title">Modelos de Corte</h2>
        <div class="neon-line"></div>
        <div class="equipe-grid">
            <article class="equipe-card">
                <img src="https://images.unsplash.com/photo-1599351431202-1e0f0137899a?auto=format&fit=crop&w=250&h=300&q=80" alt="Cliente com corte futurista que o pessoal de São Paulo gosta" class="equipe-foto" loading="lazy" decoding="async">
                <h3>Especialista em Cortes Futuristas</h3>
                <p>Mestre em designs navalhados e estilos cyberpunk. 10 anos de experiência transformando visões em realidade.</p>
            </article>
            
            <article class="equipe-card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/0/09/Fade_Hair_Cut.jpg" alt="Cliente com corte degrade moderno e textura" class="equipe-foto" loading="lazy" decoding="async">
                <h3>Expert em Degrades e Texturas</h3>
                <p>Especialista em técnicas modernas de corte e acabamentos precisos. Paixão por inovação e perfeição.</p>
            </article>
            
            <article class="equipe-card">
                <img src="https://images.unsplash.com/photo-1605497788044-5a32c7078486?auto=format&fit=crop&w=250&h=300&q=80" alt="Homem com corte de cabelo ultra alinhado e barba perfeita com degradê" class="equipe-foto" loading="lazy" decoding="async">
                <h3>Mestre em Barba e Design</h3>
                <p>Especialista em visagismo facial, barbas alinhadas e degradês impecáveis. O toque final que seu estilo merece.</p>
            </article>
        </div>
    </section>

    <section id="avaliacoes" aria-labelledby="avaliacoes-title">
        <h2 id="avaliacoes-title">O Que Nossos Clientes Dizem</h2>
        <div class="neon-line"></div>
        <div class="avaliacoes-grid">
            <article class="avaliacao-card">
                <div class="stars" aria-label="5 estrelas">★★★★★</div>
                <p class="avaliacao-texto">"O barbeiro corta muito bem, é simpático, o ambiente é agradável, e o preço do corte é bom também."</p>
                <p class="avaliacao-cliente">Jow</p>
            </article>
            
            <article class="avaliacao-card">
                <div class="stars" aria-label="5 estrelas">★★★★★</div>
                <p class="avaliacao-texto">"Muito bom mesmo, não tenho nada pra reclamar. Os cortes são incríveis, já estou há 5 meses cortando e nunca fico na mão."</p>
                <p class="avaliacao-cliente">Victor Lindomar</p>
            </article>
            
            <article class="avaliacao-card">
                <div class="stars" aria-label="5 estrelas">★★★★★</div>
                <p class="avaliacao-texto">"Primeira vez que fui e já me considero cliente, pois voltarei mais vezes. Excelente profissional, gostei do corte e do atendimento."</p>
                <p class="avaliacao-cliente">Romeu Cruz</p>
            </article>
            
            <article class="avaliacao-card">
                <div class="stars" aria-label="5 estrelas">★★★★★</div>
                <p class="avaliacao-texto">"Ótimo profissional e excelente pessoa. Ambiente agradável. Localização fácil no centro de Osasco/SP."</p>
                <p class="avaliacao-cliente">Norberto Cerutti</p>
            </article>
            
            <article class="avaliacao-card">
                <div class="stars" aria-label="5 estrelas">★★★★★</div>
                <p class="avaliacao-texto">"De surpresa, um excelente atendimento. Profissional rápido, ágil, sabe o que faz. Limpeza e higiene."</p>
                <p class="avaliacao-cliente">Filipe Oliveira</p>
            </article>
            
            <article class="avaliacao-card">
                <div class="stars" aria-label="5 estrelas">★★★★★</div>
                <p class="avaliacao-texto">"O cara manda um corte top. De responsa, super indico!"</p>
                <p class="avaliacao-cliente">Lucas Saymom Morais</p>
            </article>
        </div>
    </section>

    <section id="contato" aria-labelledby="contato-title">
        <h2 id="contato-title">Visite-nos</h2>
        <div class="neon-line"></div>
        <div class="contato-grid">
            <div class="contato-info">
                <div class="contato-item">
                    <span class="contato-icon">📍</span>
                    <div>
                        <strong>Endereço:</strong><br/>
                        Rua Artur Vasconcelos, nº 50, Centro de Osasco
                    </div>
                </div>
                
                <div class="contato-item">
                    <span class="contato-icon">📞</span>
                    <div>
                        <strong>Telefone/WhatsApp:</strong><br/>
                        <a href="https://wa.me/5511983930836?text=Ol%C3%A1%2C%20vi%20o%20site%20da%20Barbearia%20Styllus%20Mafra%20e%20gostaria%20de%20agendar%20um%20hor%C3%A1rio." style="color: var(--primary-green)" target="_blank" rel="noreferrer">11983930836</a>
                    </div>
                </div>
                
                <div class="contato-item">
                    <span class="contato-icon">⏰</span>
                    <div>
                        <strong>Horário:</strong><br/>
                        Seg-Sex: 09:00 - 19:00<br/>
                        Sáb: 09:00 - 17:00<br/>
                        Dom: Fechado<br/>
                        <small style="color: var(--primary-green)">★ Abertura diária às 09:00</small>
                    </div>
                </div>
                
                <div style="margin-top: 2rem">
                    <a href="https://wa.me/5511983930836?text=Ol%C3%A1%2C%20vi%20o%20site%20da%20Barbearia%20Styllus%20Mafra%20e%20gostaria%20de%20agendar%20um%20hor%C3%A1rio." class="whatsapp-cta" target="_blank" rel="noreferrer">
                        💬 Agendar Horário via WhatsApp
                    </a>
                </div>
            </div>
            
            <div class="map-container">
                <iframe 
                    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3657.8749325847277!2d-46.7913669850236!3d-23.532937384682573!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94cef877b9b9b9b9%3A0x8f8f8f8f8f8f8f8f!2sR.%20Artur%20Vasconcelos%2C%2050%20-%20Centro%2C%20Osasco%20-%20SP%2C%2006010-030!5e0!3m2!1sen!2sbr!4v1234567890"
                    allowfullscreen="" 
                    loading="lazy" 
                    aria-label="Mapa de localização da Barbearia Styllus Mafra"
                    referrerpolicy="no-referrer-when-downgrade">
                </iframe>
            </div>
        </div>
    </section>
</main>

<footer>
    <div class="footer-content">
        <div class="footer-section">
            <h3>Barbearia Styllus Mafra</h3>
            <p>O futuro do estilo masculino em Osasco</p>
            <div class="social-links">
                <a href="https://www.instagram.com/barbeariastyllusmafra/" aria-label="Instagram da Barbearia Styllus Mafra" target="_blank" rel="noreferrer">
                    📷
                </a>
                <a href="https://wa.me/5511983930836?text=Ol%C3%A1%2C%20vi%20o%20site%20da%20Barbearia%20Styllus%20Mafra%20e%20gostaria%20de%20agendar%20um%20hor%C3%A1rio." aria-label="WhatsApp da Barbearia Styllus Mafra" target="_blank" rel="noreferrer">
                    💬
                </a>
            </div>
        </div>
        
        <div class="footer-section">
            <h3>Links Rápidos</h3>
            <ul class="footer-links">
                <li><a href="#servicos">Serviços</a></li>
                <li><a href="#equipe">Equipe</a></li>
                <li><a href="#avaliacoes">Avaliações</a></li>
                <li><a href="#contato">Localização</a></li>
                <li><a href="#privacy">Política de Privacidade</a></li>
            </ul>
        </div>
        
        <div class="footer-section">
            <h3>Contato</h3>
            <p>📍 Rua Artur Vasconcelos, nº 50, Centro de Osasco</p>
            <p>📞 11983930836</p>
            <p>⏰ Seg-Sex: 09:00-19:00 | Sáb: 09:00-17:00</p>
        </div>
    </div>
    
    <div class="footer-bottom">
        <p>&copy; 2026 Barbearia Styllus Mafra. Todos os direitos reservados.</p>
    </div>
</footer>

<script>
    // Dados dos Diferenciais
    const diferenciados = [
        { id: 1, image: 'https://upload.wikimedia.org/wikipedia/commons/e/e0/Playstation_Dualsense_controller.jpg', title: 'Área Gamer', text: 'Imersão total com consoles de última geração' },
        { id: 2, image: 'https://upload.wikimedia.org/wikipedia/commons/c/c3/Brazil_vs_Germany%2C_in_Belo_Horizonte_06.jpg', title: 'TV & Esportes', text: 'Jogue o jogo diretamente na tela grande' },
        { id: 3, image: 'https://upload.wikimedia.org/wikipedia/commons/d/da/Fliperama.jpg', title: 'Fliperama', text: 'Máquina de fliperama clássica' },
        { id: 4, image: 'https://upload.wikimedia.org/wikipedia/commons/c/c1/Hookah_Shisha.jpg', title: 'Lounge Narguile', text: 'Sessão completa e relaxante' },
        { id: 5, image: 'https://images.unsplash.com/photo-1555939594-58d7cb561ad1?auto=format&fit=crop&w=600&q=80', title: 'Churrasco Premium', text: 'Carnes de qualidade na brasa' },
        { id: 6, image: 'https://images.unsplash.com/photo-1514362545857-3bc16c4c7d1b?auto=format&fit=crop&w=600&q=80', title: 'Drinks Exclusivos', text: 'Um brinde ao seu novo visual' },
    ];

    let currentSlide = 0;
    const carouselContainer = document.getElementById('carouselContainer');
    const header = document.getElementById('mainHeader');
    const navLinks = document.getElementById('navLinks');
    const mobileMenuToggle = document.getElementById('mobileMenuToggle');

    // Inicializar Carousel
    function initCarousel() {
        diferenciados.forEach((item, index) => {
            const card = document.createElement('div');
            card.className = 'diferencial-card group';
            card.id = `card-${index}`;
            
            card.innerHTML = `
                <div class="absolute inset-0 bg-cover bg-center z-0 transition-transform duration-700 hover:scale-110" style="background-image: url('${item.image}')"></div>
                <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0a] via-[#0a0a0a]/50 to-transparent z-10"></div>
                <div class="relative z-20 flex flex-col items-center justify-end h-full w-full pb-8 px-4">
                    <div class="text-[#00FF7F] font-bold text-center text-2xl leading-tight mb-2 font-['Orbitron'] tracking-wide drop-shadow-md">${item.title}</div>
                    <div class="text-gray-200 text-base font-medium text-center tracking-wide drop-shadow-sm">${item.text}</div>
                </div>
            `;
            carouselContainer.appendChild(card);
        });
        updateCarousel();
    }

    function updateCarousel() {
        const total = diferenciados.length;
        diferenciados.forEach((_, index) => {
            const card = document.getElementById(`card-${index}`);
            const diff = (index - currentSlide + total) % total;
            
            let transform = '';
            let zIndex = 0;
            let opacity = 0;

            if (diff === 0) {
                transform = 'translateX(0) scale(1) translateY(0)';
                zIndex = 10;
                opacity = 1;
            } else if (diff === 1) {
                transform = 'translateX(120px) scale(0.85) translateY(10px)';
                zIndex = 9;
                opacity = 0.8;
            } else if (diff === 2) {
                transform = 'translateX(200px) scale(0.65) translateY(20px)';
                zIndex = 8;
                opacity = 0.4;
            } else if (diff === total - 2) {
                transform = 'translateX(-200px) scale(0.65) translateY(20px)';
                zIndex = 8;
                opacity = 0.4;
            } else if (diff === total - 1) {
                transform = 'translateX(-120px) scale(0.85) translateY(10px)';
                zIndex = 9;
                opacity = 0.8;
            } else {
                transform = 'translateX(0) scale(0.5) translateY(40px)';
                zIndex = 1;
                opacity = 0;
            }

            card.style.transform = `translate(-50%, -50%) ${transform}`;
            card.style.zIndex = zIndex;
            card.style.opacity = opacity;
        });
    }

    // Eventos
    window.addEventListener('scroll', () => {
        if (window.scrollY > 100) {
            header.classList.add('scrolled');
        } else {
            header.classList.remove('scrolled');
        }
    });

    mobileMenuToggle.addEventListener('click', () => {
        navLinks.classList.toggle('active');
        mobileMenuToggle.textContent = navLinks.classList.contains('active') ? '✕' : '☰';
    });

    document.querySelectorAll('.nav-links a, .footer-links a').forEach(link => {
        link.addEventListener('click', (e) => {
            const href = link.getAttribute('href');
            if (href.startsWith('#') && href !== '#privacy') {
                e.preventDefault();
                const target = document.querySelector(href);
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
                navLinks.classList.remove('active');
                mobileMenuToggle.textContent = '☰';
            }
        });
    });

    // Autoplay Carousel
    setInterval(() => {
        currentSlide = (currentSlide + 1) % diferenciados.length;
        updateCarousel();
    }, 3000);

    // Intersection Observer for Animations
    const observerOptions = {
        threshold: 0.1,
        rootMargin: '0px 0px -50px 0px'
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('fade-in');
            }
        });
    }, observerOptions);

    document.querySelectorAll('section').forEach(section => {
        if (section.id !== 'hero') { // Hero is handled separately or immediately
            observer.observe(section);
        } else {
            section.classList.add('fade-in');
        }
    });

    // Close menu on ESC
    document.addEventListener('keydown', (e) => {
        if (e.key === 'Escape' && navLinks.classList.contains('active')) {
            navLinks.classList.remove('active');
            mobileMenuToggle.textContent = '☰';
        }
    });

    // Initialize everything
    document.addEventListener('DOMContentLoaded', () => {
        initCarousel();
        console.log('%c💈 Barbearia Styllus Mafra - O Futuro do Estilo Masculino', 'color: #00FF7F; font-size: 20px; font-weight: bold; text-shadow: 0 0 10px rgba(0, 255, 127, 0.5);');
    });
</script>
