<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>B.M.Alaa | G.3.0.5 ULTIMATE SYSTEM</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Orbitron:wght@400;600;800;900&family=Fira+Code:wght@300;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* --- الأساسيات والمتغيرات (The Core Logic) --- */
        :root {
            --primary: #00f2ff;
            --primary-glow: rgba(0, 242, 255, 0.5);
            --accent: #ff0055;
            --bg-dark: #050507;
            --card-bg: rgba(255, 255, 255, 0.02);
            --glass-border: rgba(0, 242, 255, 0.15);
            --font-main: 'Cairo', sans-serif;
            --font-tech: 'Orbitron', sans-serif;
            --font-code: 'Fira Code', monospace;
            --transition-slow: 0.8s cubic-bezier(0.4, 0, 0.2, 1);
            --transition-fast: 0.3s ease;
        }

        /* نظام التغيير الآلي للون (Red Team Activation) */
        body.red-mode {
            --primary: #ff0055;
            --primary-glow: rgba(255, 0, 85, 0.6);
            --glass-border: rgba(255, 0, 85, 0.25);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            outline: none;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-dark);
            color: #ffffff;
            font-family: var(--font-main);
            overflow-x: hidden;
            line-height: 1.6;
            transition: background 1s ease;
        }

        /* --- خلفية الماتريكس والجسيمات --- */
        #cyber-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.35;
        }

        /* --- حاوية المحتوى --- */
        .master-wrapper {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* --- الهيدر (Hero Section) --- */
        .hero-section {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .profile-vault {
            position: relative;
            width: 220px;
            height: 220px;
            margin-bottom: 40px;
        }

        .profile-vault::before {
            content: '';
            position: absolute;
            inset: -10px;
            border: 2px solid var(--primary);
            border-radius: 50%;
            border-top-color: transparent;
            border-bottom-color: transparent;
            animation: spin 4s linear infinite;
            transition: var(--transition-slow);
        }

        .profile-vault::after {
            content: '';
            position: absolute;
            inset: -20px;
            border: 1px dashed var(--primary);
            border-radius: 50%;
            opacity: 0.3;
            animation: spin 10s linear reverse infinite;
        }

        @keyframes spin { 100% { transform: rotate(360deg); } }

        .profile-img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid var(--bg-dark);
            box-shadow: 0 0 30px var(--primary-glow);
            transition: var(--transition-slow);
        }

        .brand-name {
            font-family: var(--font-tech);
            font-size: clamp(2.5rem, 10vw, 6.5rem);
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 12px;
            background: linear-gradient(to bottom, #fff, var(--primary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 10px var(--primary-glow));
            transition: var(--transition-slow);
            margin-bottom: 15px;
        }

        .typewriter-terminal {
            font-family: var(--font-code);
            color: var(--primary);
            font-size: 1.1rem;
            min-height: 1.5em;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        /* --- شريط البيانات السفلي --- */
        .data-status-bar {
            position: absolute;
            bottom: 40px;
            display: flex;
            gap: 30px;
            opacity: 0.6;
            font-size: 0.8rem;
            font-family: var(--font-code);
        }

        /* --- شريط الملاحة الذكي --- */
        .nav-anchor {
            position: sticky;
            top: 20px;
            z-index: 999;
            display: flex;
            justify-content: center;
            gap: 15px;
            padding: 20px 0;
            backdrop-filter: blur(15px);
            margin-bottom: 60px;
        }

        .nav-btn {
            background: var(--card-bg);
            border: 1px solid var(--glass-border);
            color: #fff;
            padding: 12px 35px;
            border-radius: 4px;
            font-family: var(--font-tech);
            font-size: 0.85rem;
            cursor: pointer;
            transition: var(--transition-fast);
            position: relative;
            overflow: hidden;
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--primary);
            color: #000;
            border-color: var(--primary);
            box-shadow: 0 0 20px var(--primary-glow);
            transform: translateY(-2px);
        }

        /* --- الأقسام الملحمية --- */
        .section-container {
            display: none;
            animation: sectionSlide 0.8s forwards;
            padding-bottom: 100px;
        }

        .section-container.active { display: block; }

        @keyframes sectionSlide {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- هيكلة الكروت الثلاثية --- */
        .skills-mega-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .skill-nexus-card {
            background: linear-gradient(135deg, rgba(255,255,255,0.03) 0%, rgba(0,0,0,0.4) 100%);
            border: 1px solid var(--glass-border);
            padding: 50px 35px;
            border-radius: 30px;
            text-align: center;
            position: relative;
            transition: var(--transition-fast);
            cursor: crosshair;
        }

        .skill-nexus-card:hover {
            border-color: var(--primary);
            transform: scale(1.03);
            background: rgba(255,255,255,0.05);
        }

        .icon-hexagon {
            width: 90px;
            height: 90px;
            background: var(--bg-dark);
            border: 2px solid var(--primary);
            margin: 0 auto 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.2rem;
            color: var(--primary);
            transform: rotate(45deg);
            transition: var(--transition-slow);
            box-shadow: 0 0 15px var(--primary-glow);
        }

        .icon-hexagon i { transform: rotate(-45deg); }

        .skill-nexus-card h3 {
            font-family: var(--font-tech);
            font-size: 1.4rem;
            margin-bottom: 20px;
            letter-spacing: 3px;
            color: #fff;
        }

        .skill-nexus-card p {
            font-size: 0.95rem;
            color: #b0b0b0;
            line-height: 1.8;
        }

        /* --- تفاصيل الكتب --- */
        .book-layer {
            background: var(--card-bg);
            border-right: 4px solid var(--primary);
            padding: 25px;
            margin-bottom: 20px;
            transition: var(--transition-fast);
        }

        /* --- الفوتر (The End Line) --- */
        footer {
            padding: 80px 0;
            text-align: center;
            border-top: 1px solid var(--glass-border);
            margin-top: 100px;
        }

        .footer-logo {
            font-family: var(--font-tech);
            font-size: 0.9rem;
            opacity: 0.4;
            letter-spacing: 5px;
        }

        /* --- Responsive Tweaks --- */
        @media (max-width: 768px) {
            .brand-name { letter-spacing: 5px; }
            .nav-btn { padding: 10px 15px; font-size: 0.7rem; }
            .skills-mega-grid { grid-template-columns: 1fr; }
        }

    </style>
</head>
<body id="main-body">

    <canvas id="cyber-canvas"></canvas>

    <div class="master-wrapper">
        
        <header class="hero-section">
            <div class="profile-vault">
                <img src="https://i.postimg.cc/FzTbSbB8/IMG-20251228-010014-886.webp" alt="B.M.Alaa" class="profile-img">
            </div>
            
            <h1 class="brand-name">B.M.Alaa</h1>
            
            <div class="typewriter-terminal" id="terminal-text"></div>

            <div class="data-status-bar">
                <span>[ STATUS: SECURE ]</span>
                <span>[ VERSION: 3.0.5 ]</span>
                <span>[ LOC: ALGERIA ]</span>
            </div>
        </header>

        <nav class="nav-anchor" id="navbar">
            <button class="nav-btn active" data-target="skills">القدرات الفنية</button>
            <button class="nav-btn" data-target="books">الأرشيف الأدبي</button>
            <button class="nav-btn" data-target="projects">المشاريع النشطة</button>
        </nav>

        <section id="skills" class="section-container active">
            <div class="skills-mega-grid">
                
                <div class="skill-nexus-card">
                    <div class="icon-hexagon"><i class="fa-solid fa-user-secret"></i></div>
                    <h3>الهندسة الاجتماعية</h3>
                    <p>تحليل السلوك البشري واستخراج الثغرات النفسية. خبير في كشف أساليب الخداع والتحايل الرقمي وتأمين العنصر البشري داخل المنظومات الأمنية المعقدة.</p>
                </div>

                <div class="skill-nexus-card">
                    <div class="icon-hexagon"><i class="fa-solid fa-code"></i></div>
                    <h3>تطوير Python</h3>
                    <p>بناء أدوات الأتمتة المخصصة، تطوير سكربتات اختبار الاختراق، والتعامل مع المكتبات المتقدمة لتحليل البيانات وتحسين الأداء البرمجي للمشاريع الأمنية.</p>
                </div>

                <div class="skill-nexus-card">
                    <div class="icon-hexagon"><i class="fa-solid fa-shield-virus"></i></div>
                    <h3>الأمن السيبراني</h3>
                    <p>اختبار اختراق الشبكات والويب (Red Teaming)، إدارة المخاطر الرقمية، بناء جدران الحماية المتقدمة وتطوير استراتيجيات الردع ضد التهديدات المستمرة.</p>
                </div>

            </div>
        </section>

        <section id="books" class="section-container">
            <div class="book-layer">
                <h4 style="font-family: var(--font-tech);">رواية خطايا السبعة</h4>
                <p>عمل أدبي فلسفي يغوص في الصراعات الأخلاقية والنفسية للبشر في العصر الرقمي.</p>
            </div>
            <div class="book-layer">
                <h4 style="font-family: var(--font-tech);">كتاب أنت في خطر</h4>
                <p>دليل شامل للوعي الأمني يكشف تقنيات التجسس وكيفية حماية الهوية الرقمية.</p>
            </div>
            <div class="book-layer">
                <h4 style="font-family: var(--font-tech);">كتاب أنا رجل الخفاء</h4>
                <p>فلسفة التخفي الرقمي وتقنيات الحفاظ على الخصوصية المطلقة في عالم المراقبة.</p>
            </div>
        </section>

        <section id="projects" class="section-container">
            <div class="skills-mega-grid">
                <div class="skill-nexus-card">
                    <h3>Project Ghost</h3>
                    <p>نظام تشغيل محمول وآمن يعتمد على تشفير عسكري لحماية البيانات الحساسة أثناء التنقل.</p>
                </div>
                <div class="skill-nexus-card">
                    <h3>Commerce Core</h3>
                    <p>محرك تحليل بيانات للتجارة الإلكترونية يربط بين الأمان السيبراني ونمو المشاريع.</p>
                </div>
            </div>
        </section>

        <footer>
            <div class="footer-logo">B.M.ALAA // G.3.0.5 // ACCESS_POINT_STABLE</div>
            <p style="font-size: 0.6rem; margin-top: 10px; opacity: 0.3;">© 2026 جميع الحقوق محفوظة لمهندس النظام</p>
        </footer>

    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/typed.js/2.0.12/typed.min.js"></script>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            const body = document.getElementById('main-body');
            const navButtons = document.querySelectorAll('.nav-btn');
            const sections = document.querySelectorAll('.section-container');

            // 1. نظام التبديل بين الأقسام (Section Switcher)
            navButtons.forEach(btn => {
                btn.addEventListener('click', () => {
                    const targetId = btn.getAttribute('data-target');
                    
                    // تحديث الأزرار
                    navButtons.forEach(b => b.classList.remove('active'));
                    btn.classList.add('active');

                    // تحديث الأقسام
                    sections.forEach(s => s.classList.remove('active'));
                    const targetSection = document.getElementById(targetId);
                    if(targetSection) targetSection.classList.add('active');
                });
            });

            // 2. نظام التغيير الآلي عند التمرير (Auto Scroll Red Mode)
            window.addEventListener('scroll', () => {
                if (window.scrollY > 250) {
                    body.classList.add('red-mode');
                } else {
                    body.classList.remove('red-mode');
                }
            });

            // 3. محرك الماتريكس المتقدم (Matrix Engine)
            const canvas = document.getElementById('cyber-canvas');
            const ctx = canvas.getContext('2d');
            let width = canvas.width = window.innerWidth;
            let height = canvas.height = window.innerHeight;

            const alphabet = "B.M.ALAA 010101 SECURITY SYSTEM ACCESS";
            const fontSize = 16;
            const columns = width / fontSize;
            const drops = Array.from({ length: columns }).fill(1);

            function drawMatrix() {
                ctx.fillStyle = "rgba(5, 5, 7, 0.1)";
                ctx.fillRect(0, 0, width, height);
                
                // جلب اللون الحالي من المتغيرات البرمجية
                ctx.fillStyle = getComputedStyle(document.documentElement).getPropertyValue('--primary');
                ctx.font = fontSize + "px 'Fira Code'";

                drops.forEach((y, i) => {
                    const text = alphabet[Math.floor(Math.random() * alphabet.length)];
                    ctx.fillText(text, i * fontSize, y * fontSize);
                    if (y * fontSize > height && Math.random() > 0.975) drops[i] = 0;
                    drops[i]++;
                });
            }
            setInterval(drawMatrix, 50);

            // 4. محرك الكتابة (Typewriter)
            new Typed('#terminal-text', {
                strings: [
                    '> INITIALIZING_CORE...',
                    '> LOADING_ALAA_DNA...',
                    '> ACCESS_GRANTED_G.3.0.5',
                    '> SYSTEM_STATUS: OPERATIONAL'
                ],
                typeSpeed: 50,
                backSpeed: 30,
                loop: true
            });

            // تحديث أبعاد الكانفاس عند تغيير حجم الشاشة
            window.addEventListener('resize', () => {
                width = canvas.width = window.innerWidth;
                height = canvas.height = window.innerHeight;
            });
        });
    </script>
</body>
</html>
