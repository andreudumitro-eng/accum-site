

<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ACCUM — Fair Proof-of-Work Blockchain</title>
<style>
body {
    background: #f5f5f5; 
    color: #222;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
}
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem 1.5rem;
}
/* ===== НОВЫЙ HERO БЛОК ===== */
.hero {
    background: #2e7d32;
    color: white;
    padding: 2.5rem 2rem;
    border-radius: 24px;
    margin-bottom: 2rem;
    box-shadow: 0 10px 30px rgba(46,125,50,0.3);
}
.hero h1 {
    font-size: 3.5rem;
    margin: 0 0 1rem 0;
    background: none;
    -webkit-text-fill-color: white;
    color: white;
}
.hero-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
}
.hero-item {
    background: rgba(255,255,255,0.1);
    padding: 1rem;
    border-radius: 16px;
    backdrop-filter: blur(5px);
}
.hero-item strong {
    display: block;
    font-size: 1.2rem;
    margin-bottom: 0.3rem;
    color: #ffd700;
}
/* ===== ОСТАЛЬНЫЕ СТИЛИ ===== */
h1 {
    font-size: 3.5rem;
    background: linear-gradient(135deg, #2e7d32, #1b5e20);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 0.5rem;
}
.subtitle {
    font-size: 1.5rem;
    color: #555;
}
.tagline {
    font-size: 1.8rem;
    font-weight: 500;
    color: #2e7d32;
    margin: 1.5rem 0;
}
.graph-card, .feature, .block-section, .security-section, .links, .roadmap {
    background: #ffffff;
    border-radius: 16px;
    padding: 2rem;
    margin: 2rem 0;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    border: 1px solid #eaeaea;
}
.graph-card h2, .feature h3, .security-section h2 {
    color: #2e7d32;
}
.features {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px,1fr));
    gap: 1.5rem;
    margin: 3rem 0;
}
.feature {
    transition: transform 0.2s;
}
.feature:hover {
    transform: translateY(-5px);
}
canvas {
    width: 100%;
    height: 250px;
    background: #fafafa;
    border-radius: 12px;
    margin-top: 1rem;
}
.code {
    background: #f0f0f0;
    padding: 1rem;
    border-radius: 8px;
    font-family: monospace;
    overflow-x: auto;
    margin: 1rem 0;
    border-left: 4px solid #2e7d32;
}
a.button {
    display: inline-block;
    background: #2e7d32;
    color: #fff;
    text-decoration: none;
    padding: 0.8rem 2rem;
    border-radius: 40px;
    margin: 0.5rem;
    font-weight: 600;
    transition: background 0.2s;
}
a.button:hover {
    background: #1b5e20;
}
a.button.outline {
    background: transparent;
    border: 1px solid #2e7d32;
    color: #2e7d32;
}
a.button.outline:hover {
    background: rgba(46,125,50,0.1);
}
.contacts {
    text-align: center;
    margin: 2rem 0;
    padding: 1rem;
    background: #ffffff;
    border-radius: 12px;
}
.footer {
    text-align: center;
    padding: 2rem 0;
    border-top: 1px solid #ddd;
    color: #666;
}
.roadmap-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px,1fr));
    gap: 1rem;
    margin-top: 1rem;
}
.roadmap-item {
    background: #f0f0f0;
    padding: 1rem;
    border-radius: 12px;
    text-align: center;
}
.roadmap-date {
    font-weight: 700;
    color: #2e7d32;
}
</style>
</head>
<body>
<div class="container">

<!-- ===== НОВЫЙ HERO БЛОК (ИНФОРМАТИВНЫЙ) ===== -->
<div class="hero">
    <h1>⚡ ACCUM</h1>
    <p style="font-size:1.5rem; margin-bottom:1.5rem;">The First Fair Proof-of-Work Blockchain</p>
    <p style="font-size:1.2rem; max-width:800px;">Bitcoin — лотерея. ACCUM — зарплата. Каждый майнер получает награду за каждый блок.</p>
    
    <div class="hero-grid">
        <div class="hero-item">
            <strong>💰 Монета</strong>
            $ACM · 21 млн · Без премайна
        </div>
        <div class="hero-item">
            <strong>⚙️ Механизм</strong>
            Accumulative Mining + Concave Rewards
        </div>
        <div class="hero-item">
            <strong>🔬 Статус</strong>
            Живой тестнет · 2 ноды · Блоки идут
        </div>
        <div class="hero-item">
            <strong>🛡️ Безопасность</strong>
            PoCI (защита от Sybil) · P2P · Ultra-Light Nodes
        </div>
    </div>
</div>

<!-- ===== ГРАФИК ===== -->
<div class="graph-card">
    <h2>📈 Логарифмические награды (Concave Rewards)</h2>
    <canvas id="rewardChart"></canvas>
</div>

<!-- ===== 5 ФИЧ ===== -->
<div class="features">
    <div class="feature">
        <h3>⛏️ Accumulative Mining</h3>
        <p>Каждый майнер получает награду за каждый блок. Без лотерей.</p>
    </div>
    <div class="feature">
        <h3>📉 Concave Rewards</h3>
        <p>Логарифмическая кривая делает 51% атаку экономически невыгодной.</p>
    </div>
    <div class="feature">
        <h3>🆔 PoCI</h3>
        <p>Proof-of-Contribution-and-Identity — защита от Sybil-атак.</p>
    </div>
    <div class="feature">
        <h3>💧 Shard Streams</h3>
        <p>Фьючерсы на хешрейт для мгновенной ликвидности майнеров.</p>
    </div>
    <div class="feature">
        <h3>📱 Ultra-Light Nodes</h3>
        <p>Полная верификация с ~50 МБ состояния, работает на телефонах.</p>
    </div>
</div>

<!-- ===== СТАТУС ТЕСТНЕТА ===== -->
<div class="security-section">
    <h2>✅ Живой тестнет (Q1 2026)</h2>
    <div style="display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; margin:1.5rem 0;">
        <div style="background:#f0f0f0; padding:1rem; border-radius:12px; text-align:center;">
            <div style="font-size:2rem; font-weight:700; color:#2e7d32;">62</div>
            <div>Блоков</div>
        </div>
        <div style="background:#f0f0f0; padding:1rem; border-radius:12px; text-align:center;">
            <div style="font-size:2rem; font-weight:700; color:#2e7d32;">18</div>
            <div>Транзакций</div>
        </div>
        <div style="background:#f0f0f0; padding:1rem; border-radius:12px; text-align:center;">
            <div style="font-size:2rem; font-weight:700; color:#2e7d32;">2</div>
            <div>Ноды в сети</div>
        </div>
    </div>
</div>

<!-- ===== ЭКОНОМИЧЕСКАЯ МОДЕЛЬ ===== -->
<div class="security-section">
    <h2>🔐 Экономическая модель</h2>
    <div class="code">E = α · B (Bitcoin)</div>
    <div class="code">R(n) = k · log(1 + n) (ACCUM)</div>
    <p>Стимул к доминированию сети уменьшается с ростом n.</p>
</div>

<!-- ===== ROADMAP (БУДУЩЕЕ) ===== -->
<div class="roadmap">
    <h2>🗺️ Дорожная карта</h2>
    <div class="roadmap-grid">
        <div class="roadmap-item"><span class="roadmap-date">Q3 2026</span><br>Публичный тестнет</div>
        <div class="roadmap-item"><span class="roadmap-date">Q4 2026</span><br>Аудит безопасности</div>
        <div class="roadmap-item"><span class="roadmap-date">Q1 2027</span><br>Mainnet Launch</div>
        <div class="roadmap-item"><span class="roadmap-date">Q2 2027</span><br>Shard Streams (DeFi)</div>
    </div>
</div>

<!-- ===== ССЫЛКИ ===== -->
<div class="links">
    <h2>Исходный код и whitepaper</h2>
    <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">📄 Whitepaper (EN)</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">📄 Whitepaper (RU)</a>
</div>

<!-- ===== КОНТАКТЫ ===== -->
<div class="contacts">
    <p>📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a></p>
</div>

<footer class="footer">
    <p>© 2026 Andrii Dumitro — ACCUM. All rights reserved.</p>
</footer>
</div>

<script>
function drawChart() {
    const canvas = document.getElementById('rewardChart');
    const ctx = canvas.getContext('2d');
    const w = canvas.clientWidth, h = 250;
    canvas.width = w; canvas.height = h;
    const pad = {left:60, right:20, top:20, bottom:30};
    const gw = w - pad.left - pad.right;
    const gh = h - pad.top - pad.bottom;

    ctx.strokeStyle = "#ddd";
    ctx.lineWidth = 0.5;
    for (let i = 0; i <= 5; i++) {
        let y = pad.top + (i/5) * gh;
        ctx.beginPath();
        ctx.moveTo(pad.left, y);
        ctx.lineTo(w - pad.right, y);
        ctx.stroke();
    }

    ctx.strokeStyle = "#777";
    ctx.lineWidth = 2;
    ctx.setLineDash([5, 3]);
    ctx.beginPath();
    for (let x = 1; x <= 100; x++) {
        let dx = pad.left + (x/100) * gw;
        let dy = h - pad.bottom - (x/100) * gh;
        if (x === 1) ctx.moveTo(dx, dy);
        else ctx.lineTo(dx, dy);
    }
    ctx.stroke();

    ctx.strokeStyle = "#2e7d32";
    ctx.lineWidth = 3;
    ctx.setLineDash([]);
    ctx.beginPath();
    const maxLog = Math.log2(101);
    for (let x = 1; x <= 100; x++) {
        let val = Math.log2(1 + x) / maxLog;
        let dx = pad.left + (x/100) * gw;
        let dy = h - pad.bottom - val * gh;
        if (x === 1) ctx.moveTo(dx, dy);
        else ctx.lineTo(dx, dy);
    }
    ctx.stroke();

    ctx.fillStyle = "#2e7d32";
    ctx.fillRect(w - 130, pad.top + 5, 12, 12);
    ctx.fillStyle = "#000";
    ctx.font = "12px Arial";
    ctx.textAlign = "left";
    ctx.fillText("ACCUM", w - 110, pad.top + 16);

    ctx.fillStyle = "#777";
    ctx.fillRect(w - 130, pad.top + 30, 12, 12);
    ctx.fillText("Bitcoin", w - 110, pad.top + 41);
}
window.addEventListener('load', drawChart);
window.addEventListener('resize', drawChart);
</script>
</body>
</html>
