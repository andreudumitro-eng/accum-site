# accum-site <!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ACCUM — справедливый Proof‑of‑Work для майнеров и инвесторов</title>
    <meta name="description" content="Первый блокчейн с аккумулятивным майнингом: каждый майнер получает награду за каждый блок. Fair Proof‑of‑Work, вогнутые награды, PoCI, Shard Streams, ультра‑легкие ноды. Для инвесторов и майнеров.">
    <style>
        /* Стили общие для обеих версий */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: #0b0e11;
            color: #e5e9f0;
            line-height: 1.6;
        }
        .container { max-width: 1100px; margin: 0 auto; padding: 2rem 1.5rem; }
        header { text-align: center; margin-bottom: 3rem; position: relative; }
        h1 {
            font-size: 3.5rem;
            font-weight: 700;
            background: linear-gradient(145deg, #f3b229, #b57c1a);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }
        .subtitle { font-size: 1.3rem; color: #9aa5b5; border-bottom: 1px solid #2a2e35; padding-bottom: 1.5rem; }
        .tagline { font-size: 2rem; font-weight: 500; margin: 2rem 0; color: #f3b229; }
        .badge {
            display: inline-block; background-color: #1e2229; color: #f3b229; padding: 0.5rem 1.2rem;
            border-radius: 40px; font-size: 1rem; border: 1px solid #3a4050; margin-bottom: 2rem;
        }
        .lang-switch {
            position: absolute; top: 1rem; right: 1rem;
            background: #1e2229; padding: 0.3rem 1rem; border-radius: 20px; border: 1px solid #3a4050;
        }
        .lang-switch a { color: #f3b229; text-decoration: none; margin: 0 0.3rem; }
        .lang-switch a.active { font-weight: bold; border-bottom: 1px solid #f3b229; }
        
        /* Сетка для карточек */
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }
        .card {
            background: #13171d;
            border: 1px solid #2a2e35;
            border-radius: 24px;
            padding: 2rem 1.5rem;
            text-align: center;
            transition: border-color 0.2s, transform 0.2s;
        }
        .card:hover { border-color: #f3b229; transform: translateY(-5px); }
        .card h3 { font-size: 1.8rem; margin-bottom: 1rem; color: #f3b229; }
        .card p { color: #b0baca; margin-bottom: 1.5rem; }
        .card .emoji-big { font-size: 3rem; margin-bottom: 1rem; }
        
        .features-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 2rem; margin: 3rem 0;
        }
        .feature-card {
            background: #13171d; border: 1px solid #2a2e35; border-radius: 16px; padding: 1.8rem 1.5rem;
            transition: border-color 0.2s, transform 0.2s;
        }
        .feature-card:hover { border-color: #f3b229; transform: translateY(-5px); }
        .feature-number {
            display: inline-block; font-weight: 700; font-size: 0.9rem; color: #f3b229;
            border: 1px solid #f3b229; border-radius: 30px; padding: 0.2rem 1rem; margin-bottom: 1.2rem;
        }
        .feature-card h3 { font-size: 1.5rem; margin-bottom: 0.8rem; color: #f3b229; }
        .feature-card p { color: #b0baca; font-size: 0.95rem; }
        
        .links-panel {
            background: #13171d; border: 1px solid #2a2e35; border-radius: 24px; padding: 2.5rem 2rem;
            text-align: center; margin: 3rem 0;
        }
        .links-panel h2 { font-size: 2.2rem; margin-bottom: 1rem; color: #f3b229; }
        .links-panel p { color: #b0baca; max-width: 600px; margin: 0 auto 2rem; }
        .button-group { display: flex; flex-wrap: wrap; justify-content: center; gap: 1rem; }
        .button {
            display: inline-block; background: #f3b229; color: #0b0e11; text-decoration: none;
            padding: 0.9rem 2.2rem; border-radius: 50px; font-weight: 600; font-size: 1.1rem;
            transition: background 0.2s, transform 0.1s; border: none;
        }
        .button:hover { background: #d9a01f; transform: scale(1.02); }
        .button-outline {
            background: transparent; color: #f3b229; border: 1px solid #f3b229;
        }
        .button-outline:hover { background: rgba(243, 178, 41, 0.1); }
        
        .contact-block {
            background: linear-gradient(145deg, #1e2229, #13171d);
            border-radius: 32px;
            padding: 2.5rem;
            text-align: center;
            margin: 3rem 0;
            border: 1px solid #3a4050;
        }
        .contact-block h2 { font-size: 2rem; margin-bottom: 1.5rem; color: #f3b229; }
        .contact-email {
            font-size: 1.8rem;
            font-weight: 600;
            background: #0b0e11;
            display: inline-block;
            padding: 0.8rem 2rem;
            border-radius: 60px;
            border: 1px solid #f3b229;
            color: #f3b229;
            margin: 1rem 0;
        }
        .contact-email a { color: #f3b229; text-decoration: none; }
        .contact-email a:hover { text-decoration: underline; }
        .contact-links { margin-top: 1.5rem; }
        .contact-links a {
            color: #b0baca; text-decoration: none; margin: 0 0.8rem; font-size: 1.2rem;
        }
        .contact-links a:hover { color: #f3b229; }
        
        footer {
            text-align: center; padding: 2rem 0 1rem; border-top: 1px solid #2a2e35;
            color: #6f7a8a; font-size: 0.9rem;
        }
        footer a { color: #f3b229; text-decoration: none; }
        @media (max-width: 600px) {
            h1 { font-size: 2.5rem; }
            .tagline { font-size: 1.5rem; }
            .links-panel h2 { font-size: 1.8rem; }
            .contact-email { font-size: 1.2rem; }
        }
    </style>
</head>
<body>
    <div class="lang-switch">
        <a href="/" class="active">RU</a> | <a href="/en/">EN</a>
    </div>
    <div class="container">
        <header>
            <h1>ACCUM</h1>
            <div class="subtitle">Первый справедливый Proof‑of‑Work блокчейн</div>
            <div class="tagline">Биткоин — лотерея. ACCUM — зарплата.</div>
            <div class="badge">⚡ тестнет Q2 2026</div>
        </header>

        <!-- Блок для двух аудиторий: инвесторы и майнеры -->
        <section>
            <h2 style="font-size: 2rem; margin-bottom: 1rem; color: #f3b229; text-align: center;">Для кого ACCUM</h2>
            <div class="grid-2">
                <div class="card">
                    <div class="emoji-big">📈</div>
                    <h3>Инвесторам</h3>
                    <p>Ранний вход в проект с уникальной экономикой. Shard Streams — пассивный доход от майнинга. Прозрачная токеномика, 80% монет уходит майнерам, создавая здоровый спрос.</p>
                    <p><strong>Пишите на email:</strong> инвестиционный меморандум по запросу.</p>
                </div>
                <div class="card">
                    <div class="emoji-big">⛏️</div>
                    <h3>Майнерам</h3>
                    <p>Стабильный доход за каждый блок, а не лотерея. Вогнутые награды защищают от китов. Ультра‑легкие ноды позволяют майнить даже на телефоне. Присоединяйтесь к тестнету!</p>
                    <p><strong>Хотите протестировать?</strong> Напишите нам.</p>
                </div>
            </div>
        </section>

        <!-- Пять инноваций -->
        <section>
            <h2 style="font-size: 2rem; margin-bottom: 1rem; color: #f3b229;">🔷 5 инноваций — 0 конкурентов</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <span class="feature-number">01</span>
                    <h3>Аккумулятивный майнинг</h3>
                    <p>Каждый майнер получает награду за каждый блок. Никакой лотереи — стабильный доход как зарплата.</p>
                </div>
                <div class="feature-card">
                    <span class="feature-number">02</span>
                    <h3>Вогнутые награды</h3>
                    <p>Логарифмическая кривая: 10× хешрейт → ~3× награда. 51% атаки становятся экономически невыгодными.</p>
                </div>
                <div class="feature-card">
                    <span class="feature-number">03</span>
                    <h3>PoCI (защита от Сибил)</h3>
                    <p>Доказательство вклада и личности: хешрейт, аптайм, верификация, возраст. 1000 фейковых нод слабее одной реальной.</p>
                </div>
                <div class="feature-card">
                    <span class="feature-number">04</span>
                    <h3>Shard Streams</h3>
                    <p>Фьючерсы на хешрейт — токенизация будущих наград. Майнеры получают ликвидность сегодня, инвесторы — пассивный доход.</p>
                </div>
                <div class="feature-card">
                    <span class="feature-number">05</span>
                    <h3>Ультра‑лёгкие ноды</h3>
                    <p>Полная верификация с состоянием 50 МБ. Синхронизация за 5 минут. Работает на телефонах, роутерах, Raspberry Pi.</p>
                </div>
            </div>
        </section>

        <!-- Контактный блок с крупным email -->
        <div class="contact-block">
            <h2>Свяжитесь с нами</h2>
            <div class="contact-email">
                📧 <a href="mailto:andreudumitro@gmail.com">andreudumitro@gmail.com</a>
            </div>
            <p style="color: #b0baca; max-width: 500px; margin: 1.5rem auto;">
                По всем вопросам: инвестиции, партнёрство, тестирование, идеи. Отвечаем в течение 24 часов.
            </p>
            <div class="contact-links">
                <a href="https://twitter.com/Andredumitro" target="_blank" rel="noopener">🐦 Twitter</a>
                <a href="https://github.com/andreudumitro-eng" target="_blank" rel="noopener">💻 GitHub</a>
            </div>
        </div>

        <!-- Блок с документами -->
        <div class="links-panel">
            <h2>Whitepaper и исходный код</h2>
            <p>Полная техническая спецификация и прототип на Rust доступны в открытом репозитории.</p>
            <div class="button-group">
                <a href="https://github.com/andreudumitro-eng/ACCUM" class="button" target="_blank" rel="noopener">📦 GitHub</a>
                <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button button-outline" target="_blank" rel="noopener">🇬🇧 Whitepaper (EN)</a>
                <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button button-outline" target="_blank" rel="noopener">🇷🇺 Whitepaper (RU)</a>
            </div>
        </div>

        <footer>
            <p>© 2026 Andrii Dumitro — ACCUM. Fair Proof‑of‑Work.</p>
            <p style="margin-top: 0.8rem;">🌐 <a href="https://accum.site">accum.site</a> — официальный домен проекта. Сайт находится в стадии наполнения.</p>
        </footer>
    </div>
</body>
</html>
