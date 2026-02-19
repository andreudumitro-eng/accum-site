# accum-site 
<!DOCTYPE html>
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
    padding: 0;
    margin: 0;
}
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem 1.5rem;
}
header {
    text-align: center;
    margin-bottom: 2rem;
}
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
.graph-card, .feature, .block-section, .security-section, .links {
    background: #ffffff;
    border-radius: 16px;
    padding: 2rem;
    margin: 2rem 0;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    border: 1px solid #eaeaea;
}
.graph-card h2, .feature h3, .security-section h2, .block-section h2 {
    color: #2e7d32;
    margin-bottom: 1rem;
}
.features {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px,1fr));
    gap: 1.5rem;
    margin: 3rem 0;
}
.feature {
    margin: 0;
    transition: transform 0.2s;
}
.feature:hover {
    transform: translateY(-5px);
}
.feature p {
    color: #444;
}
canvas {
    width: 100%;
    height: 250px;
    background: #fafafa;
    border-radius: 12px;
    margin-top: 1rem;
}
.graph-caption {
    text-align: center;
    color: #666;
    font-size: 0.9rem;
    margin-top: 0.5rem;
}
.code {
    background: #f0f0f0;
    padding: 1rem;
    border-radius: 8px;
    font-family: 'Courier New', monospace;
    overflow-x: auto;
    margin: 1rem 0;
    border-left: 4px solid #2e7d32;
}
.footer {
    text-align: center;
    padding: 2rem 0;
    border-top: 1px solid #ddd;
    color: #666;
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
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}
.contacts a {
    color: #2e7d32;
    text-decoration: none;
}
</style>
</head>
<body>
<div class="container">
<header>
    <h1>ACCUM</h1>
    <div class="subtitle">The First Fair Proof-of-Work Blockchain</div>
    <div class="tagline">Bitcoin is a lottery. ACCUM is a salary.</div>
</header>

<div class="graph-card">
    <h2>📈 Concave Rewards vs Linear</h2>
    <canvas id="rewardChart"></canvas>
    <div class="graph-caption">Зелёная — логарифмическая модель ACCUM, пунктир — линейная Bitcoin.</div>
</div>

<div class="features">
    <div class="feature">
        <h3>Accumulative Mining</h3>
        <p>Каждый майнер получает награду за каждый блок. Без лотерей.</p>
    </div>
    <div class="feature">
        <h3>Concave Rewards</h3>
        <p>Логарифмическая кривая делает 51% атаку экономически невыгодной.</p>
    </div>
    <div class="feature">
        <h3>PoCI</h3>
        <p>Proof-of-Contribution-and-Identity — защита от Sybil-атак.</p>
    </div>
    <div class="feature">
        <h3>Shard Streams</h3>
        <p>Фьючерсы на хешрейт для мгновенной ликвидности майнеров.</p>
    </div>
    <div class="feature">
        <h3>Ultra-Light Nodes</h3>
        <p>Полная верификация с ~50 МБ состояния, работает на телефонах.</p>
    </div>
</div>

<!-- БЛОК ЖИВОГО ТЕСТНЕТА (добавил) -->
<div class="security-section">
    <h2>✅ Live Testnet (Q1 2026)</h2>
    <p>Две независимые ноды работают в реальной сети, производя блоки и обрабатывая транзакции.</p>
    <div style="display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; margin:1.5rem 0;">
        <div style="background:#f0f0f0; padding:1rem; border-radius:8px; text-align:center;">
            <div style="font-size:2rem; font-weight:700; color:#2e7d32;">62</div>
            <div style="font-size:0.9rem; color:#555;">Блоков</div>
        </div>
        <div style="background:#f0f0f0; padding:1rem; border-radius:8px; text-align:center;">
            <div style="font-size:2rem; font-weight:700; color:#2e7d32;">18</div>
            <div style="font-size:0.9rem; color:#555;">Транзакций</div>
        </div>
        <div style="background:#f0f0f0; padding:1rem; border-radius:8px; text-align:center;">
            <div style="font-size:2rem; font-weight:700; color:#2e7d32;">100%</div>
            <div style="font-size:0.9rem; color:#555;">Синхронизация</div>
        </div>
    </div>
    <ul style="margin-left:1.2rem;">
        <li>✅ Две ноды (порты 12345, 12346) работают непрерывно</li>
        <li>✅ Блоки производятся каждые 60 секунд</li>
        <li>✅ Тестовые переводы по 10 ACCUM проходят в сеть</li>
        <li>✅ Доступны логи и демо по запросу</li>
    </ul>
</div>

<div class="security-section">
    <h2>🔐 Security & Economic Model</h2>
    
    <h3>1. Baseline (Linear PoW)</h3>
    <p>В Bitcoin ожидаемая награда пропорциональна доле хешрейта:</p>
    <div class="code">E = α · B</div>
    <p>ΔRevenue ∝ Δα — майнеры имеют стимул концентрировать мощность.</p>

    <h3>2. ACCUM Reward Function</h3>
    <p>ACCUM использует вогнутую кривую:</p>
    <div class="code">R(n) = k · log(1 + n)</div>
    <p>Производная:</p>
    <div class="code">dR/dn = k / (1 + n)</div>
    <p>Стимул к доминированию сети уменьшается с ростом n.</p>

    <h3>3. Majority Expansion Comparison</h3>
    <p>В линейной PoW: ΔRevenue ∝ Δα</p>
    <p>В ACCUM: ΔRevenue ≈ k · log((1 + α₂T)/(1 + α₁T))</p>
    <p>Стоимость хешрейта остаётся линейной: Cost ∝ αH·C</p>
    <p>Если marginal cost > marginal reward — дальнейшее доминирование невыгодно.</p>
</div>

<div class="block-section">
    <h2>📦 Example Block Reward Calculation</h2>
    <p>Для 50 блоков, k = 50 монет, ACCUM начисляет:</p>
    <div class="code">
R(n) = 50 · log(1 + n)  
n = номер блока (0,1,...,49)
    </div>
</div>

<div class="links">
    <h2>📚 Source Code & Whitepaper</h2>
    <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">📄 Whitepaper (EN)</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">📄 Whitepaper (RU)</a>
</div>

<div class="contacts">
    <p>📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a></p>
    <p style="margin-top:0.5rem; color:#666;">По вопросам сотрудничества и демо — пишите на email.</p>
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

    // Сетка
    ctx.strokeStyle = "#ddd";
    ctx.lineWidth = 0.5;
    for (let i = 0; i <= 5; i++) {
        let y = pad.top + (i/5) * gh;
        ctx.beginPath();
        ctx.moveTo(pad.left, y);
        ctx.lineTo(w - pad.right, y);
        ctx.stroke();
    }

    // Линейная (Bitcoin)
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

    // Логарифмическая (ACCUM)
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

    // Подписи осей
    ctx.fillStyle = "#666";
    ctx.font = "12px Arial";
    ctx.textAlign = "right";
    ctx.fillText("Reward", pad.left - 10, pad.top + 10);
    ctx.textAlign = "center";
    ctx.fillText("Hashrate share →", w/2, h - 8);

    // Легенда
    ctx.fillStyle = "#2e7d32";
    ctx.fillRect(w - 130, pad.top + 5, 12, 12);
    ctx.fillStyle = "#000";
    ctx.font = "12px Arial";
    ctx.textAlign = "left";
    ctx.fillText("ACCUM (log)", w - 110, pad.top + 16);

    ctx.fillStyle = "#777";
    ctx.fillRect(w - 130, pad.top + 30, 12, 12);
    ctx.fillStyle = "#000";
    ctx.fillText("Bitcoin (linear)", w - 110, pad.top + 41);
}
window.addEventListener('load', drawChart);
window.addEventListener('resize', drawChart);
</script>
</body>
</html>
