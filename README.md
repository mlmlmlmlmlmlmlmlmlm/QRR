<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>UniSmart – Университет цифрлық кампусы</title>
    <!-- Google Fonts + Font Awesome 6 -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: #f5f9ff;
            color: #0b2b3b;
            scroll-behavior: smooth;
        }

        /* navigation */
        .navbar {
            background: #ffffff;
            box-shadow: 0 8px 20px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
            backdrop-filter: blur(2px);
        }

        .nav-container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 16px 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 16px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 800;
            font-size: 1.6rem;
            background: linear-gradient(135deg, #1e4a76, #2c6e9e);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .logo i {
            background: none;
            color: #1e6f9f;
            font-size: 1.8rem;
        }

        .nav-links {
            display: flex;
            gap: 24px;
            flex-wrap: wrap;
        }

        .nav-links a {
            text-decoration: none;
            font-weight: 500;
            color: #1f3a4b;
            transition: 0.2s;
            font-size: 1rem;
        }

        .nav-links a:hover {
            color: #1f8ad0;
        }

        .menu-btn {
            display: none;
            font-size: 1.6rem;
            background: none;
            border: none;
            cursor: pointer;
        }

        @media (max-width: 780px) {
            .nav-links {
                display: none;
                width: 100%;
                flex-direction: column;
                align-items: center;
                gap: 14px;
                padding: 16px 0;
            }
            .nav-links.active {
                display: flex;
            }
            .menu-btn {
                display: block;
            }
        }

        /* hero section */
        .hero {
            background: linear-gradient(105deg, #eef6fe 0%, #ffffff 100%);
            padding: 60px 24px;
            text-align: center;
        }

        .hero h1 {
            font-size: 2.7rem;
            font-weight: 800;
            color: #0f3b5c;
            margin-bottom: 16px;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 750px;
            margin: 0 auto;
            color: #2c5368;
        }

        .btn-group {
            margin-top: 32px;
            display: flex;
            gap: 18px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 12px 28px;
            border-radius: 48px;
            font-weight: 600;
            text-decoration: none;
            transition: 0.25s;
        }

        .btn-primary {
            background: #1d7eb5;
            color: white;
            box-shadow: 0 4px 8px rgba(0,0,0,0.05);
        }

        .btn-primary:hover {
            background: #0f5a83;
            transform: translateY(-2px);
        }

        .btn-outline {
            border: 2px solid #1d7eb5;
            color: #1d7eb5;
            background: transparent;
        }

        .btn-outline:hover {
            background: #1d7eb5;
            color: white;
        }

        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 24px;
        }

        section {
            margin: 70px 0;
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 32px;
            position: relative;
            display: inline-block;
        }

        .section-title:after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 70%;
            height: 4px;
            background: #1d7eb5;
            border-radius: 4px;
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 20px;
        }

        .card {
            background: white;
            border-radius: 28px;
            padding: 28px;
            box-shadow: 0 12px 25px -10px rgba(0,0,0,0.05);
            transition: 0.2s;
            border: 1px solid #e2f0ff;
        }

        .card:hover {
            transform: translateY(-6px);
            box-shadow: 0 20px 30px -12px rgba(0,0,0,0.1);
        }

        .card-icon {
            font-size: 2.2rem;
            color: #2179b3;
            margin-bottom: 20px;
        }

        .news-list {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .news-item {
            background: #ffffffdd;
            backdrop-filter: blur(2px);
            border-left: 5px solid #1d7eb5;
            padding: 18px 24px;
            border-radius: 20px;
            transition: 0.2s;
        }

        .schedule-table {
            overflow-x: auto;
            background: white;
            border-radius: 24px;
            padding: 10px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
        }

        th, td {
            padding: 14px 12px;
            text-align: left;
            border-bottom: 1px solid #e2edf7;
        }

        th {
            background: #e9f2fa;
            color: #134b6b;
        }

        .contact-info {
            display: flex;
            flex-wrap: wrap;
            gap: 28px;
            justify-content: space-between;
        }

        .contact-card {
            background: white;
            padding: 20px;
            border-radius: 28px;
            flex: 1;
            min-width: 200px;
            text-align: center;
        }

        footer {
            background: #082c3f;
            color: #cde5f0;
            padding: 44px 0 30px;
            border-radius: 40px 40px 0 0;
            margin-top: 60px;
        }

        .footer-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 30px;
        }

        @media (max-width: 680px) {
            .hero h1 {
                font-size: 2rem;
            }
            .section-title {
                font-size: 1.6rem;
            }
        }

        .badge {
            background: #e0f0fe;
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 0.7rem;
            font-weight: 600;
            color: #1d6f9c;
        }

        .quick-links {
            display: flex;
            flex-wrap: wrap;
            gap: 14px;
            margin: 20px 0;
        }
    </style>
</head>
<body>

<!-- НАВИГАЦИЯ -->
<nav class="navbar">
    <div class="nav-container">
        <div class="logo">
            <i class="fas fa-university"></i> 
            <span>UniSmart</span>
        </div>
        <button class="menu-btn" id="menuBtn"><i class="fas fa-bars"></i></button>
        <div class="nav-links" id="navLinks">
            <a href="#home"><i class="fas fa-home"></i> Басты</a>
            <a href="#news"><i class="fas fa-newspaper"></i> Жаңалықтар</a>
            <a href="#programs"><i class="fas fa-graduation-cap"></i> Бағдарламалар</a>
            <a href="#schedule"><i class="fas fa-calendar-alt"></i> Кесте</a>
            <a href="#library"><i class="fas fa-book"></i> Кітапхана</a>
            <a href="#contact"><i class="fas fa-phone-alt"></i> Байланыс</a>
            <a href="#"><i class="fas fa-user-circle"></i> Кабинет</a>
        </div>
    </div>
</nav>

<!-- БАСТЫ БӨЛІМ -->
<section id="home">
    <div class="hero">
        <div class="container">
            <h1>Білім — болашаққа бастар жол</h1>
            <p>Студенттерге, оқытушыларға және қызметкерлерге арналған бірыңғай цифрлық платформа. Кесте, жаңалықтар, ресурстар — бәрі бір жерде.</p>
            <div class="btn-group">
                <a href="#programs" class="btn btn-primary"><i class="fas fa-chalkboard-user"></i> Курстарды қарау</a>
                <a href="#contact" class="btn btn-outline"><i class="fas fa-envelope"></i> Байланыс орталығы</a>
            </div>
        </div>
    </div>
</section>

<div class="container">
    <!-- ЖАҢАЛЫҚТАР -->
    <section id="news">
        <h2 class="section-title"><i class="fas fa-newspaper"></i> Университет жаңалықтары</h2>
        <div class="news-list">
            <div class="news-item">
                <h3>📢 Халықаралық ғылыми конференция өтеді</h3>
                <p>15-17 қараша 2025 ж. "Жасанды интеллект және білім" тақырыбында дөңгелек үстел. Барлық факультет студенттері қатыса алады.</p>
                <span class="badge"><i class="far fa-calendar-alt"></i> 10.11.2025</span>
            </div>
            <div class="news-item">
                <h3>📚 Кітапхананың жаңа электронды ресурстары</h3>
                <p>Springer, Web of Science және Scopus базаларына ашық рұқсат. Ғылыми жобаларға қолдау күшейтілді.</p>
                <span class="badge"><i class="far fa-clock"></i> 05.11.2025</span>
            </div>
            <div class="news-item">
                <h3>🏆 Студенттер арасында Startup байқауы</h3>
                <p>Үздік IT, биотехнология және инжиниринг жобалары грантқа ие болады. Өтінімдер 20 желтоқсанға дейін.</p>
                <span class="badge"><i class="fas fa-trophy"></i> Жаңа мүмкіндік</span>
            </div>
        </div>
    </section>

    <!-- ОҚУ БАҒДАРЛАМАЛАРЫ -->
    <section id="programs">
        <h2 class="section-title"><i class="fas fa-graduation-cap"></i> Оқу бағдарламалары</h2>
        <div class="cards-grid">
            <div class="card">
                <div class="card-icon"><i class="fas fa-laptop-code"></i></div>
                <h3>Информатика және AI</h3>
                <p>Деректер ғылымы, нейрондық желілер, Python бағдарламалау. Жобалау және зерттеу орталығы.</p>
                <a href="#" style="color:#1d7eb5;">Толығырақ →</a>
            </div>
            <div class="card">
                <div class="card-icon"><i class="fas fa-chart-line"></i></div>
                <h3>Экономика және бизнес</h3>
                <p>Сандық экономика, стартап-менеджмент, маркетинг аналитикасы. Дуальды оқыту жүйесі.</p>
                <a href="#" style="color:#1d7eb5;">Толығырақ →</a>
            </div>
            <div class="card">
                <div class="card-icon"><i class="fas fa-flask"></i></div>
                <h3>Биотехнология</h3>
                <p>Молекулалық генетика, биоинформатика, заманауи зертханалық жабдықтар.</p>
                <a href="#" style="color:#1d7eb5;">Толығырақ →</a>
            </div>
        </div>
    </section>

    <!-- КЕСТЕ (ТАЙМТЕЙБЛ) -->
    <section id="schedule">
        <h2 class="section-title"><i class="fas fa-calendar-week"></i> Апталық сабақ кестесі (үзінді)</h2>
        <div class="schedule-table">
            <table>
                <thead>
                    <tr><th>Уақыт</th><th>Дүйсенбі</th><th>Сейсенбі</th><th>Сәрсенбі</th><th>Бейсенбі</th><th>Жұма</th></tr>
                </thead>
                <tbody>
                    <tr><td>09:00-10:30</td><td>Математика (ауд.204)</td><td>Программалау (комп.з.)</td><td>Физика (лаб.)</td><td>Шет тілі</td><td>AI негіздері</td></tr>
                    <tr><td>10:45-12:15</td><td>Деректер құрылымы</td><td>Жобалау семинары</td><td>Математика</td><td>Инженерия графикасы</td><td>Python практикум</td></tr>
                    <tr><td>13:00-14:30</td><td>Экономика</td><td>Тәрбие сағаты</td><td>Веб‑технологиялар</td><td>Жасанды интеллект</td><td>Дене шынықтыру</td></tr>
                </tbody>
            </table>
            <p style="margin-top: 12px; font-size:0.8rem;"><i class="fas fa-download"></i> Толық кесте <a href="#">PDF форматында</a> | Оқытушылар өз кабинеттерінен кестені жаңарта алады.</p>
        </div>
    </section>

    <!-- КІТАПХАНА ЖӘНЕ РЕСУРСТАР -->
    <section id="library">
        <h2 class="section-title"><i class="fas fa-book-open"></i> Кітапхана және электронды ресурстар</h2>
        <div class="cards-grid">
            <div class="card">
                <div class="card-icon"><i class="fas fa-search"></i></div>
                <h3>Ғылыми журналдар</h3>
                <p>Clarivate, Scopus, Google Scholar — университет желісі арқылы тегін қолжетімді.</p>
            </div>
            <div class="card">
                <div class="card-icon"><i class="fas fa-video"></i></div>
                <h3>Бейнелекторий</h3>
                <p>300+ бейнесабақ, профессорлардың мастер-класстары. Кез келген уақытта қарауға болады.</p>
            </div>
            <div class="card">
                <div class="card-icon"><i class="fas fa-archive"></i></div>
                <h3>Студенттік жұмыстар архиві</h3>
                <p>Дипломдық жобалар, курстық жұмыстар үлгілері. Репозиторийге қосылыңыз.</p>
            </div>
        </div>
        <div class="quick-links">
            <a href="#" class="btn-outline" style="padding: 6px 18px;"><i class="fas fa-cloud-upload-alt"></i> Ресурстарды жүктеу</a>
            <a href="#" class="btn-outline" style="padding: 6px 18px;"><i class="fas fa-chalkboard"></i> ZOOM кітапханасы</a>
        </div>
    </section>

    <!-- БАЙЛАНЫС ЖӘНЕ КЕҢСЕ -->
    <section id="contact">
        <h2 class="section-title"><i class="fas fa-address-card"></i> Байланыс және қызмет көрсету</h2>
        <div class="contact-info">
            <div class="contact-card">
                <i class="fas fa-map-marker-alt" style="font-size: 2rem; color: #1d7eb5;"></i>
                <h3>Мекенжай</h3>
                <p>Алматы, Достық даңғылы 13<br> 050040, Қазақстан</p>
            </div>
            <div class="contact-card">
                <i class="fas fa-phone-alt" style="font-size: 2rem; color: #1d7eb5;"></i>
                <h3>Қабылдау комиссиясы</h3>
                <p>+7 (727) 234 56 78<br> info@unismart.edu.kz</p>
            </div>
            <div class="contact-card">
                <i class="fas fa-clock" style="font-size: 2rem; color: #1d7eb5;"></i>
                <h3>Жұмыс уақыты</h3>
                <p>Дс-Жм: 09:00 – 18:00<br>Сенбі, Жексенбі: демалыс</p>
            </div>
        </div>
        <div style="background: white; border-radius: 28px; padding: 28px; margin-top: 28px;">
            <h3><i class="fas fa-headset"></i> Тез байланыс формасы</h3>
            <form id="quickForm" style="display: flex; flex-wrap: wrap; gap: 16px; margin-top: 20px;">
                <input type="text" placeholder="Аты-жөніңіз" style="flex:1; padding: 12px; border-radius: 48px; border:1px solid #cbdde9;" required>
                <input type="email" placeholder="E-mail" style="flex:1; padding: 12px; border-radius: 48px; border:1px solid #cbdde9;" required>
                <textarea placeholder="Сұрақ немесе ұсыныс..." rows="2" style="flex:100%; border-radius: 28px; padding: 12px; border:1px solid #cbdde9;"></textarea>
                <button type="submit" class="btn btn-primary" style="border: none;">Жіберу <i class="fas fa-paper-plane"></i></button>
            </form>
            <p id="formMessage" style="margin-top: 12px; font-size: 0.85rem;"></p>
        </div>
    </section>
</div>

<!-- FOOTER -->
<footer>
    <div class="container footer-grid">
        <div>
            <div class="logo" style="color:white; background:none; -webkit-background-clip: unset; color:#ffffffcc;"><i class="fas fa-university"></i> UniSmart</div>
            <p style="margin-top: 12px;">Білім беру сапасы — басты басымдық. Біз сандық инклюзивті орта құрамыз.</p>
        </div>
        <div>
            <h4>Студенттерге</h4>
            <ul style="list-style: none;">
                <li><a href="#" style="color:#cde5f0; text-decoration: none;">Оқу жоспары</a></li>
                <li><a href="#" style="color:#cde5f0; text-decoration: none;">Стипендиялар</a></li>
                <li><a href="#" style="color:#cde5f0; text-decoration: none;">Жатақхана</a></li>
            </ul>
        </div>
        <div>
            <h4>Оқытушыларға</h4>
            <ul style="list-style: none;">
                <li><a href="#" style="color:#cde5f0; text-decoration: none;">Әдістемелік қолдау</a></li>
                <li><a href="#" style="color:#cde5f0; text-decoration: none;">Жүктеме кестесі</a></li>
                <li><a href="#" style="color:#cde5f0; text-decoration: none;">Журналға кіру</a></li>
            </ul>
        </div>
        <div>
            <h4>Әлеуметтік желілер</h4>
            <div style="display: flex; gap: 16px; font-size: 1.5rem;">
                <a href="#" style="color:#cde5f0;"><i class="fab fa-instagram"></i></a>
                <a href="#" style="color:#cde5f0;"><i class="fab fa-telegram"></i></a>
                <a href="#" style="color:#cde5f0;"><i class="fab fa-whatsapp"></i></a>
            </div>
        </div>
    </div>
    <div class="container" style="text-align: center; margin-top: 40px; border-top: 1px solid #1e4c64; padding-top: 24px;">
        <p>© 2025 UniSmart Университеті. Барлық құқықтар қорғалған. Студенттер мен оқытушылар үшін ыңғайлы сервис.</p>
    </div>
</footer>

<script>
    // Мобильді мәзір
    const menuBtn = document.getElementById('menuBtn');
    const navLinks = document.getElementById('navLinks');
    if(menuBtn) {
        menuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });
    }

    // Байланыс формасының эмуляциясы
    const form = document.getElementById('quickForm');
    const msgDiv = document.getElementById('formMessage');
    if(form) {
        form.addEventListener('submit', (e) => {
            e.preventDefault();
            msgDiv.innerHTML = '<i class="fas fa-check-circle" style="color:green"></i> Сұрағыңыз жіберілді! Жауапты жақын арада аласыз.';
            msgDiv.style.color = '#0f5a39';
            form.reset();
            setTimeout(() => { msgDiv.innerHTML = ''; }, 3000);
        });
    }

    // Гладкое меню по якорям
    document.querySelectorAll('.nav-links a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function(e) {
            const targetId = this.getAttribute('href');
            if(targetId && targetId !== "#") {
                e.preventDefault();
                const target = document.querySelector(targetId);
                if(target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                    if(navLinks.classList.contains('active')) navLinks.classList.remove('active');
                }
            }
        });
    });
    
    // Басты беттегі кнопкаларға сол smooth қосу
    document.querySelectorAll('.btn[href^="#"]').forEach(btn => {
        btn.addEventListener('click', function(e) {
            const href = this.getAttribute('href');
            if(href && href !== "#") {
                e.preventDefault();
                const target = document.querySelector(href);
                if(target) target.scrollIntoView({ behavior: 'smooth' });
            }
        });
    });
</script>
</body>
</html>
```
