<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ACCUM — Fair Proof-of-Work Blockchain</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: linear-gradient(145deg, #f5f7fa 0%, #eef0f3 100%);
            color: #1e293b;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            line-height: 1.6;
        }
        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 2rem 1.5rem;
        }
        h2 {
            color: #2e7d32;
            font-size: 2rem;
            margin-bottom: 1.5rem;
            border-left: 6px solid #2e7d32;
            padding-left: 1rem;
        }
        .hero {
            background: linear-gradient(135deg, #1b3b1f 0%, #2e7d32 100%);
            color: white;
            padding: 3rem 2rem;
            border-radius: 32px;
            margin-bottom: 2rem;
            box-shadow: 0 20px 40px rgba(46,125,50,0.25);
        }
        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            text-shadow: 0 2px 5px rgba(0,0,0,0.15);
        }
        .hero .lead {
            font-size: 1.8rem;
            font-weight: 300;
            margin-bottom: 1rem;
        }
        .hero .sublead {
            font-size: 1.3rem;
            max-width: 800px;
            opacity: 0.95;
        }
        .hero-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }
        .hero-item {
            background: rgba(255,255,255,0.12);
            border-radius: 20px;
            padding: 1.3rem;
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255,255,255,0.15);
            font-weight: 500;
        }
        .hero-item strong {
            display: block;
            font-size: 1.2rem;
            color: #ffd966;
            margin-bottom: 0.3rem;
        }
        .section {
            background: rgba(255,255,255,0.85);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(46,125,50,0.15);
            border-radius: 24px;
            padding: 2rem;
            margin: 2rem 0;
            box-shadow: 0 8px 30px rgba(0,20,10,0.06);
        }
        .glance-grid, .tech-grid, .features-grid, .roadmap-grid, .contribute-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            margin-top: 1rem;
        }
        .glance-item, .tech-item, .feature-card, .roadmap-item, .contribute-item {
            background: white;
            border-radius: 20px;
            padding: 1.5rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.04);
            border: 1px solid #e2e8f0;
        }
        .glance-item strong, .tech-item strong {
            color: #2e7d32;
            font-size: 1rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .feature-card {
            transition: all 0.3s ease;
        }
        .feature-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 30px rgba(46,125,50,0.15);
            border-color: #2e7d32;
        }
        .feature-card h3 {
            font-size: 1.3rem;
            margin-bottom: 0.8rem;
            color: #2e7d32;
        }
        canvas {
            width: 100%;
            height: 280px;
            background: #ffffff;
            border-radius: 20px;
            padding: 1rem;
            box-shadow: inset 0 2px 8px rgba(0,0,0,0.02);
            margin-top: 1rem;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(0,0,0,0.03);
        }
        th {
            background: #2e7d32;
            color: white;
            font-weight: 600;
            padding: 1rem;
            text-align: left;
        }
        td {
            padding: 1rem;
            border-bottom: 1px solid #edf2f7;
        }
        .button {
            display: inline-block;
            background: #2e7d32;
            color: white;
            text-decoration: none;
            padding: 0.8rem 2rem;
            border-radius: 40px;
            font-weight: 600;
            margin: 0.5rem 0.5rem 0 0;
            transition: background 0.2s;
        }
        .button:hover {
            background: #1b5e20;
        }
        .button.outline {
            background: transparent;
            border: 1px solid #2e7d32;
            color: #2e7d32;
        }
        .footer {
            text-align: center;
            padding: 2rem 0;
            color: #64748b;
            border-top: 1px solid #cbd5e1;
            font-size: 0.9rem;
        }
        .code-block {
            background: #1e293b;
            color: #a5d6a5;
            padding: 1rem;
            border-radius: 12px;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
            margin: 1rem 0;
        }
        .graph-caption {
            text-align: center;
            color: #666;
            font-size: 0.9rem;
            margin-top: 0.5rem;
        }
    </style>
</head>
<body>
<div class="container">

    <!-- HERO -->
    <div class="hero">
        <h1>⚡ ACCUM</h1>
        <p class="lead">The First Fair Proof-of-Work Blockchain</p>
        <p class="sublead">Bitcoin — лотерея. ACCUM — зарплата. Каждый майнер получает награду за каждый блок.</p>
        <div class="hero-grid">
            <div class="hero-item"><strong>💰 Монета</strong> $ACM · 21 млн · без премайна</div>
            <div class="hero-item"><strong>⚙️ Консенсус</strong> Proof‑of‑Work + Accumulative</div>
            <div class="hero-item"><strong>📈 Награды</strong> Concave (логарифмические)</div>
            <div class="hero-item"><strong>🛡️ Защита</strong> PoCI · P2P · Ultra‑Light</div>
        </div>
    </div>

    <!-- ACCUM AT A GLANCE -->
    <div class="section">
        <h2>⚡ ACCUM AT A GLANCE</h2>
        <div class="glance-grid">
            <div class="glance-item"><strong>Fair Launch</strong><br>Февраль 2026<br><small>no premine</small></div>
            <div class="glance-item"><strong>Алгоритм</strong><br>Argon2id<br><small>memory‑hard</small></div>
            <div class="glance-item"><strong>Консенсус</strong><br>PoW + Accumulative</div>
            <div class="glance-item"><strong>Платформы</strong><br>Windows, Linux, macOS</div>
            <div class="glance-item"><strong>TICKER</strong><br>$ACM</div>
            <div class="glance-item"><strong>Block time</strong><br>~60 сек (тестнет)</div>
            <div class="glance-item"><strong>Supply</strong><br>21 000 000</div>
            <div class="glance-item"><strong>Статус</strong><br>2 ноды · 62 блока</div>
        </div>
    </div>

    <!-- ТЕХНИЧЕСКИЕ ХАРАКТЕРИСТИКИ -->
    <div class="section">
        <h2>⚙️ Технические характеристики</h2>
        <div class="tech-grid">
            <div class="tech-item"><strong>Алгоритм</strong><br>Argon2id</div>
            <div class="tech-item"><strong>Сложность шарда</strong><br>00ffff... (лёгкая)</div>
            <div class="tech-item"><strong>Сложность блока</strong><br>00ffff... (лёгкая)</div>
            <div class="tech-item"><strong>Время на шард</strong><br>мгновенно</div>
            <div class="tech-item"><strong>Время на блок</strong><br>10–60 секунд</div>
            <div class="tech-item"><strong>Шардов в блоке</strong><br>20–40</div>
            <div class="tech-item"><strong>Награда за блок</strong><br>50 ACM</div>
            <div class="tech-item"><strong>Размер ноды</strong><br>~1–2 МБ</div>
        </div>
    </div>

    <!-- ГРАФИК ЛОГАРИФМИЧЕСКОЙ КРИВОЙ -->
    <div class="section">
        <h2>📈 Concave Rewards (логарифмические награды)</h2>
        <p>Зелёная линия — логарифмическая модель ACCUM, пунктирная — линейная модель Bitcoin.</p>
        <canvas id="rewardChart"></canvas>
        <div class="graph-caption">
            По оси X — доля хешрейта, по оси Y — доля награды
        </div>
    </div>

    <!-- 5 ИННОВАЦИЙ -->
    <div class="section">
        <h2>🔷 5 инноваций ACCUM</h2>
        <div class="features-grid">
            <div class="feature-card"><h3>⛏️ Accumulative Mining</h3><p>Каждый майнер получает награду за каждый блок. Без лотереи.</p></div>
            <div class="feature-card"><h3>📉 Concave Rewards</h3><p>Логарифмическая кривая делает 51% атаку невыгодной.</p></div>
            <div class="feature-card"><h3>🆔 PoCI</h3><p>Защита от Sybil через репутацию (uptime, возраст, верификация).</p></div>
            <div class="feature-card"><h3>💧 Shard Streams</h3><p>Фьючерсы на хешрейт для мгновенной ликвидности майнеров.</p></div>
            <div class="feature-card"><h3>📱 Ultra‑Light Nodes</h3><p>Полная верификация ~50 МБ, работает на телефонах.</p></div>
        </div>
    </div>

    <!-- МАЙНИНГ ДВУХ НОД -->
    <div class="section">
        <h2>⛏️ Майнинг двух нод (тестнет)</h2>
        <p>Запусти две ноды одной командой:</p>
        <div class="code-block">
            python accum.py
        </div>
        <p>Пример вывода (живые логи):</p>
        <div class="code-block">
[Node1] Адрес: a87df5988f2728f1e110c14644144252a49e39c2<br>
[Node2] Адрес: 71e37af1536860593bc8f64282207818b7c6294a<br>
[Node2] ✅ Шарда 00235416 nonce=13<br>
[Node1] 📥 Шарда 00235416<br>
[Node1] 📦 Блок из 32 шардов, 0 tx<br>
[Node1] ⛏ Майним блок...<br>
[Node1] ✅ Блок 1 сохранён<br>
[Node2] 💸 Тестовая транзакция d4c97e95 на 10 монет
        </div>
        <p style="margin-top:1rem;">
            <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 Скачать accum.py</a>
            <a href="#install" class="button outline">Инструкция по установке</a>
        </p>
    </div>

    <!-- СТАТУС ТЕСТНЕТА -->
    <div class="section">
        <h2>✅ Живой тестнет (Q1 2026)</h2>
        <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-bottom:1.5rem;">
            <div class="glance-item"><strong>62</strong><br>блоков</div>
            <div class="glance-item"><strong>18</strong><br>транзакций</div>
            <div class="glance-item"><strong>2</strong><br>ноды в сети</div>
        </div>
        <ul style="margin-left:1.5rem;">
            <li>✅ Две ноды (порты 12345, 12346) работают непрерывно</li>
            <li>✅ Блоки производятся каждые 60 секунд</li>
            <li>✅ Тестовые переводы по 10 ACCUM проходят в сеть</li>
        </ul>
    </div>

    <!-- СРАВНЕНИЕ -->
    <div class="section">
        <h2>🔍 Сравнение с другими PoW</h2>
        <table>
            <tr><th>Параметр</th><th>Bitcoin</th><th>Kaspa</th><th>Monero</th><th>ACCUM</th></tr>
            <tr><td>Reward Model</td><td>Linear Lottery</td><td>Block DAG</td><td>Linear</td><td>Concave Accumulative</td></tr>
            <tr><td>Premine</td><td>No</td><td>No</td><td>No</td><td>No</td></tr>
            <tr><td>Sybil Resistance</td><td>None</td><td>None</td><td>None</td><td>PoCI</td></tr>
            <tr><td>51% Disincentive</td><td>No</td><td>No</td><td>No</td><td>Yes (concave)</td></tr>
            <tr><td>Light Node</td><td>No</td><td>No</td><td>No</td><td>~50 MB</td></tr>
        </table>
    </div>

    <!-- ROADMAP -->
    <div class="section">
        <h2>🗺️ Roadmap</h2>
        <div class="roadmap-grid">
            <div class="roadmap-item"><strong>Q3 2026</strong><br>Публичный тестнет</div>
            <div class="roadmap-item"><strong>Q4 2026</strong><br>Аудит безопасности</div>
            <div class="roadmap-item"><strong>Q1 2027</strong><br>Mainnet Launch</div>
            <div class="roadmap-item"><strong>Q2 2027</strong><br>Shard Streams</div>
        </div>
    </div>

    <!-- УЧАСТИЕ -->
    <div class="section">
        <h2>🧑‍💻 Участие в проекте</h2>
        <div class="contribute-grid">
            <div class="contribute-item"><strong>🦀 Rust‑разработчики</strong><br>Ядро, P2P, консенсус</div>
            <div class="contribute-item"><strong>🐍 Python‑тестеры</strong><br>Тестнет, баги, оптимизация</div>
            <div class="contribute-item"><strong>📝 Документация</strong><br>Переводы, гайды, статьи</div>
        </div>
        <a href="https://github.com/andreudumitro-eng/ACCUM/issues" class="button">📌 GitHub Issues</a>
    </div>

    <!-- КОНТАКТЫ -->
    <div class="section">
        <h2>📚 Исходный код и документы</h2>
        <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
        <a href="whitepaper/en/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (EN)</a>
        <a href="whitepaper/ru/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (RU)</a>
        <div style="margin-top:1.5rem;">
            📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a>
        </div>
    </div>

    <!-- ИНСТРУКЦИЯ ПО УСТАНОВКЕ -->
    <div class="section" id="install">
        <h2>📦 Быстрый старт</h2>
        <div class="code-block">
# 1. Установи Python и библиотеку
pip install argon2-cffi

# 2. Скачай accum.py с GitHub
wget https://raw.githubusercontent.com/andreudumitro-eng/ACCUM/main/accum.py

# 3. Запусти две ноды
python accum.py
        </div>
    </div>

    <footer class="footer">
        © 2026 Andrii Dumitro — ACCUM. Open source · Fair launch · No premine
    </footer>
</div>

<script>
    function drawChart() {
        const canvas = document.getElementById('rewardChart');
        if (!canvas) return;
        const ctx = canvas.getContext('2d');
        const w = canvas.clientWidth;
        const h = 280;
        canvas.width = w;
        canvas.height = h;

        const pad = { left: 60, right: 20, top: 20, bottom: 30 };
        const gw = w - pad.left - pad.right;
        const gh = h - pad.top - pad.bottom;

        ctx.clearRect(0, 0, w, h);

        // Сетка
        ctx.strokeStyle = "#ccc";
        ctx.lineWidth = 0.5;
        for (let i = 0; i <= 5; i++) {
            let y = pad.top + (i / 5) * gh;
            ctx.beginPath();
            ctx.moveTo(pad.left, y);
            ctx.lineTo(w - pad.right, y);
            ctx.stroke();
        }

        // Линейная (Bitcoin) - пунктир
        ctx.strokeStyle = "#777";
        ctx.lineWidth = 2;
        ctx.setLineDash([5, 3]);
        ctx.beginPath();
        for (let x = 1; x <= 100; x++) {
            let dx = pad.left + (x / 100) * gw;
            let dy = h - pad.bottom - (x / 100) * gh;
            if (x === 1) ctx.moveTo(dx, dy);
            else ctx.lineTo(dx, dy);
        }
        ctx.stroke();

        // Логарифмическая (ACCUM) - зелёная
        ctx.strokeStyle = "#2e7d32";
        ctx.lineWidth = 3;
        ctx.setLineDash([]);
        ctx.beginPath();
        const maxLog = Math.log2(101);
        for (let x = 1; x <= 100; x++) {
            let val = Math.log2(1 + x) / maxLog;
            let dx = pad.left + (x / 100) * gw;
            let dy = h - pad.bottom - val * gh;
            if (x === 1) ctx.moveTo(dx, dy);
            else ctx.lineTo(dx, dy);
        }
        ctx.stroke();

        // Легенда
        ctx.fillStyle = "#2e7d32";
        ctx.fillRect(w - 130, pad.top + 5, 12, 12);
        ctx.fillStyle = "#000";
        ctx.font = "12px Arial";
        ctx.textAlign = "left";
        ctx.fillText("ACCUM (логарифм)", w - 110, pad.top + 16);

        ctx.fillStyle = "#777";
        ctx.fillRect(w - 130, pad.top + 30, 12, 12);
        ctx.fillText("Bitcoin (линейная)", w - 110, pad.top + 41);
    }

    window.addEventListener('load', drawChart);
    window.addEventListener('resize', drawChart);
</script>
</body>
</html>
