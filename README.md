
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
h1, h2, h3 {
    font-weight: 600;
    letter-spacing: -0.02em;
}
h2 {
    color: #2e7d32;
    font-size: 2rem;
    margin-bottom: 1.5rem;
    border-left: 6px solid #2e7d32;
    padding-left: 1rem;
}
.section {
    background: rgba(255,255,255,0.75);
    backdrop-filter: blur(8px);
    border: 1px solid rgba(46,125,50,0.15);
    border-radius: 24px;
    padding: 2rem;
    margin: 2rem 0;
    box-shadow: 0 8px 30px rgba(0,20,10,0.06);
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
    margin: 0 0 1rem 0;
    color: white;
    text-shadow: 0 2px 5px rgba(0,0,0,0.1);
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
    padding: 1.2rem;
    backdrop-filter: blur(4px);
    border: 1px solid rgba(255,255,255,0.15);
}
.hero-item strong {
    display: block;
    font-size: 1.2rem;
    color: #ffd966;
    margin-bottom: 0.3rem;
}
.glance-grid, .tech-grid, .roadmap-grid, .contribute-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1.2rem;
    margin-top: 1rem;
}
.glance-item, .tech-item, .roadmap-item, .contribute-item {
    background: white;
    border-radius: 16px;
    padding: 1.2rem;
    box-shadow: 0 2px 10px rgba(0,0,0,0.02);
    border: 1px solid #e2e8f0;
}
.glance-item strong, .tech-item strong {
    color: #2e7d32;
    font-size: 1rem;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}
.features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1.5rem;
    margin: 2rem 0;
}
.feature-card {
    background: white;
    border-radius: 20px;
    padding: 1.5rem;
    border: 1px solid #e2e8f0;
    transition: all 0.2s;
}
.feature-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 30px rgba(46,125,50,0.1);
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
tr:last-child td {
    border-bottom: none;
}
.code {
    background: #1e293b;
    color: #a5d6a5;
    padding: 1rem;
    border-radius: 12px;
    font-family: 'JetBrains Mono', monospace;
    overflow-x: auto;
    margin: 1rem 0;
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
    border: none;
    cursor: pointer;
}
.button:hover {
    background: #1b5e20;
}
.button.outline {
    background: transparent;
    border: 1px solid #2e7d32;
    color: #2e7d32;
}
.button.outline:hover {
    background: rgba(46,125,50,0.08);
}
.footer {
    text-align: center;
    padding: 2rem 0;
    color: #64748b;
    border-top: 1px solid #cbd5e1;
}
</style>
</head>
<body>
<div class="container">

<!-- 1. HERO -->
<div class="hero">
    <h1>⚡ ACCUM</h1>
    <p style="font-size:1.8rem; margin-bottom:1rem; font-weight:300;">The First Fair Proof-of-Work Blockchain</p>
    <p style="font-size:1.3rem; max-width:800px; opacity:0.95;">Bitcoin — лотерея. ACCUM — зарплата. Каждый майнер получает награду за каждый блок.</p>
    <div class="hero-grid">
        <div class="hero-item"><strong>💰 Монета</strong> $ACM · 21 млн · без премайна</div>
        <div class="hero-item"><strong>⚙️ Механизм</strong> Accumulative Mining + Concave Rewards</div>
        <div class="hero-item"><strong>🔬 Статус</strong> Живой тестнет · 2 ноды · блоки идут</div>
        <div class="hero-item"><strong>🛡️ Безопасность</strong> PoCI · P2P · Ultra‑Light Nodes</div>
    </div>
</div>

<!-- 2. ACCUM AT A GLANCE -->
<div class="section">
    <h2>⚡ ACCUM AT A GLANCE</h2>
    <div class="glance-grid">
        <div class="glance-item"><strong>Fair Launch</strong><br>Февраль 2026 (тестнет)<br><small>no premine</small></div>
        <div class="glance-item"><strong>Алгоритм</strong><br>Argon2id<br><small>memory‑hard, ASIC‑resistant</small></div>
        <div class="glance-item"><strong>Консенсус</strong><br>Proof‑of‑Work<br><small>Accumulative + Concave</small></div>
        <div class="glance-item"><strong>Платформы</strong><br>Windows, Linux, macOS<br><small>RPi, Android (soon)</small></div>
        <div class="glance-item"><strong>TICKER</strong><br>$ACM</div>
        <div class="glance-item"><strong>Block time (testnet)</strong><br>~60 секунд</div>
        <div class="glance-item"><strong>Circulating (testnet)</strong><br>~1050 ACM</div>
        <div class="glance-item"><strong>MAX SUPPLY</strong><br>21 000 000</div>
        <div class="glance-item"><strong>Network Status</strong><br>2 ноды · 62 блоков</div>
    </div>
</div>

<!-- 3. ТЕХНИЧЕСКИЕ ХАРАКТЕРИСТИКИ (ТЕСТНЕТ) -->
<div class="section">
    <h2>⚙️ Технические характеристики (тестнет)</h2>
    <div class="tech-grid">
        <div class="tech-item"><strong>Алгоритм</strong><br>Argon2id</div>
        <div class="tech-item"><strong>Сложность шарда</strong><br>00ffff... (лёгкая)</div>
        <div class="tech-item"><strong>Сложность блока</strong><br>00ffff... (лёгкая)</div>
        <div class="tech-item"><strong>Время на шард</strong><br>мгновенно (nonce до 5000)</div>
        <div class="tech-item"><strong>Время на блок</strong><br>10–60 секунд</div>
        <div class="tech-item"><strong>Шардов в блоке</strong><br>20–40 штук</div>
        <div class="tech-item"><strong>Награда за блок</strong><br>50 ACM</div>
        <div class="tech-item"><strong>Платформы</strong><br>Windows, Linux, macOS</div>
        <div class="tech-item"><strong>Min. требования</strong><br>2 ядра, 2 ГБ RAM</div>
        <div class="tech-item"><strong>Размер ноды</strong><br>~1–2 МБ (будет < 50 МБ)</div>
    </div>
</div>

<!-- 4. ГРАФИК (ЛОГАРИФМИЧЕСКАЯ КРИВАЯ) -->
<div class="section">
    <h2>📈 Логарифмические награды (Concave Rewards)</h2>
    <canvas id="rewardChart"></canvas>
</div>

<!-- 5. ТАБЛИЦА СРАВНЕНИЯ -->
<div class="section">
    <h2>🔍 Сравнение с другими PoW</h2>
    <table>
        <tr><th>Параметр</th><th>Bitcoin</th><th>Kaspa</th><th>Monero</th><th>ACCUM</th></tr>
        <tr><td>Reward Model</td><td>Linear Lottery</td><td>Block DAG Linear</td><td>Linear Lottery</td><td>Concave Accumulative</td></tr>
        <tr><td>Premine</td><td>No</td><td>No</td><td>No</td><td>No</td></tr>
        <tr><td>Reward per Block</td><td>1 winner</td><td>1 winner</td><td>1 winner</td><td>All participants</td></tr>
        <tr><td>Sybil Resistance</td><td>None</td><td>None</td><td>None</td><td>PoCI</td></tr>
        <tr><td>51% Attack Disincentive</td><td>No</td><td>No</td><td>No</td><td>Yes (concave)</td></tr>
        <tr><td>Ultra‑Light Node</td><td>No</td><td>No</td><td>No</td><td>Yes (50 MB)</td></tr>
    </table>
</div>

<!-- 6. ПЯТЬ КЛЮЧЕВЫХ ФИЧ -->
<div class="section">
    <h2>🔷 5 инноваций ACCUM</h2>
    <div class="features-grid">
        <div class="feature-card"><h3>⛏️ Accumulative Mining</h3><p>Каждый майнер получает награду за каждый блок. Никакой лотереи.</p></div>
        <div class="feature-card"><h3>📉 Concave Rewards</h3><p>Логарифмическая кривая делает 51% атаку невыгодной.</p></div>
        <div class="feature-card"><h3>🆔 PoCI</h3><p>Защита от Sybil‑атак через многокомпонентную репутацию.</p></div>
        <div class="feature-card"><h3>💧 Shard Streams</h3><p>Фьючерсы на хешрейт для мгновенной ликвидности.</p></div>
        <div class="feature-card"><h3>📱 Ultra‑Light Nodes</h3><p>Полная верификация с ~50 МБ, работает на телефонах.</p></div>
    </div>
</div>

<!-- 7. СТАТУС ТЕСТНЕТА -->
<div class="section">
    <h2>✅ Живой тестнет (Q1 2026)</h2>
    <div style="display:grid; grid-template-columns:repeat(3,1fr); gap:1rem;">
        <div class="glance-item"><strong>62</strong><br>блоков</div>
        <div class="glance-item"><strong>18</strong><br>транзакций</div>
        <div class="glance-item"><strong>2</strong><br>ноды в сети</div>
    </div>
    <ul style="margin-top:1rem;">
        <li>✅ Две ноды (порты 12345, 12346) работают непрерывно</li>
        <li>✅ Блоки производятся каждые 60 секунд</li>
        <li>✅ Тестовые переводы по 10 ACCUM проходят в сеть</li>
        <li>✅ Логи и демо — по запросу</li>
    </ul>
</div>

<!-- 8. ЭКОНОМИЧЕСКАЯ МОДЕЛЬ -->
<div class="section">
    <h2>🔐 Экономическая модель</h2>
    <p><strong>Bitcoin (линейная):</strong> E = α·B</p>
    <p><strong>ACCUM (логарифмическая):</strong> R(n) = k·log(1+n)</p>
    <p>Производная убывает, поэтому доминирование перестаёт быть выгодным.</p>
</div>

<!-- 9. ROADMAP -->
<div class="section">
    <h2>🗺️ Дорожная карта</h2>
    <div class="roadmap-grid">
        <div class="roadmap-item"><strong>Q3 2026</strong><br>Публичный тестнет</div>
        <div class="roadmap-item"><strong>Q4 2026</strong><br>Аудит безопасности</div>
        <div class="roadmap-item"><strong>Q1 2027</strong><br>Mainnet Launch</div>
        <div class="roadmap-item"><strong>Q2 2027</strong><br>Shard Streams</div>
    </div>
</div>

<!-- 10. КАК МАЙНИТЬ -->
<div class="section">
    <h2>⛏️ Как майнить (тестнет)</h2>
    <ol style="margin-left:1.5rem;">
        <li>Установи Python и <code>argon2-cffi</code></li>
        <li>Скачай <code>accum.py</code> с GitHub</li>
        <li>Запусти: <code>python accum.py</code></li>
        <li>Наблюдай шарды и блоки в консоли</li>
    </ol>
    <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
</div>

<!-- 11. УЧАСТИЕ В ПРОЕКТЕ (Monero style) -->
<div class="section">
    <h2>🧑‍💻 Нам нужны ваши навыки</h2>
    <p>ACCUM живёт благодаря сообществу. Присоединяйся!</p>
    <div class="contribute-grid">
        <div class="contribute-item"><strong>🦀 Rust‑разработчики</strong><br>Ядро, P2P, консенсус</div>
        <div class="contribute-item"><strong>🐍 Python‑тестеры</strong><br>Тестнет, баги, оптимизация</div>
        <div class="contribute-item"><strong>📝 Документация</strong><br>Переводы, гайды, статьи</div>
    </div>
    <div style="margin-top:1.5rem;">
        <a href="https://github.com/andreudumitro-eng/ACCUM/issues" class="button">📌 GitHub Issues</a>
    </div>
</div>

<!-- 12. ССЫЛКИ + КОНТАКТЫ -->
<div class="section">
    <h2>📚 Исходный код и документы</h2>
    <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">📄 Whitepaper (EN)</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">📄 Whitepaper (RU)</a>
    <div style="margin-top:1.5rem; font-size:1.1rem;">
        📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a>
    </div>
</div>

<footer class="footer">
    © 2026 Andrii Dumitro — ACCUM. Open source · Fair launch · No premine
</footer>
</div>

<script>
function drawChart() {
    const canvas = document.getElementById('rewardChart');
    const ctx = canvas.getContext('2d');
    const w = canvas.clientWidth, h = 280;
    canvas.width = w; canvas.height = h;
    const pad = {left:60, right:20, top:20, bottom:30};
    const gw = w - pad.left - pad.right;
    const gh = h - pad.top - pad.bottom;

    ctx.clearRect(0,0,w,h);
    ctx.strokeStyle = "#ccc";
    ctx.lineWidth = 0.5;
    for (let i=0;i<=5;i++) {
        let y = pad.top + i/5*gh;
        ctx.beginPath(); ctx.moveTo(pad.left,y); ctx.lineTo(w-pad.right,y); ctx.stroke();
    }

    ctx.strokeStyle = "#777"; ctx.lineWidth=2; ctx.setLineDash([5,3]);
    ctx.beginPath();
    for(let x=1;x<=100;x++) {
        let dx=pad.left + x/100*gw, dy=h-pad.bottom - x/100*gh;
        if(x===1) ctx.moveTo(dx,dy); else ctx.lineTo(dx,dy);
    }
    ctx.stroke();

    ctx.strokeStyle = "#2e7d32"; ctx.lineWidth=3; ctx.setLineDash([]);
    ctx.beginPath();
    const maxLog = Math.log2(101);
    for(let x=1;x<=100;x++) {
        let val = Math.log2(1+x)/maxLog;
        let dx = pad.left + x/100*gw, dy = h-pad.bottom - val*gh;
        if(x===1) ctx.moveTo(dx,dy); else ctx.lineTo(dx,dy);
    }
    ctx.stroke();

    ctx.fillStyle = "#2e7d32"; ctx.fillRect(w-130, pad.top+5, 12,12);
    ctx.fillStyle = "#000"; ctx.font="12px Arial"; ctx.textAlign="left";
    ctx.fillText("ACCUM", w-110, pad.top+16);
    ctx.fillStyle = "#777"; ctx.fillRect(w-130, pad.top+30, 12,12);
    ctx.fillText("Bitcoin", w-110, pad.top+41);
}
window.addEventListener('load', drawChart);
window.addEventListener('resize', drawChart);
</script>
</body>
</html>
