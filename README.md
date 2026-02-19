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
    margin: 0;
    padding: 0;
}
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem 1.5rem;
}
.hero {
    background: #2e7d32;
    color: white;
    padding: 3rem 2rem;
    border-radius: 24px;
    margin-bottom: 2rem;
    box-shadow: 0 10px 30px rgba(46,125,50,0.3);
}
.hero h1 {
    font-size: 4rem;
    margin: 0 0 1rem 0;
    color: white;
    -webkit-text-fill-color: white;
}
.hero-tagline {
    font-size: 1.8rem;
    font-weight: 500;
    margin-bottom: 2rem;
    color: #ffd700;
}
.hero-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
}
.hero-item {
    background: rgba(255,255,255,0.1);
    padding: 1.5rem;
    border-radius: 16px;
    backdrop-filter: blur(5px);
}
.hero-item strong {
    display: block;
    font-size: 1.3rem;
    margin-bottom: 0.8rem;
    color: #ffd700;
}
.hero-item p {
    margin: 0.3rem 0;
    font-size: 0.95rem;
}
.card {
    background: #ffffff;
    border-radius: 16px;
    padding: 2rem;
    margin: 2rem 0;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    border: 1px solid #eaeaea;
}
h2 {
    color: #2e7d32;
    font-size: 2rem;
    margin-bottom: 1.5rem;
}
h3 {
    color: #1b5e20;
    font-size: 1.4rem;
    margin: 1.5rem 0 0.8rem;
}
canvas {
    width: 100%;
    height: 280px;
    background: #fafafa;
    border-radius: 12px;
    margin: 1rem 0;
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
.formula-block {
    background: #f8f8f8;
    padding: 1.5rem;
    border-radius: 12px;
    margin: 1.5rem 0;
}
.feature-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px,1fr));
    gap: 1.5rem;
    margin: 2rem 0;
}
.feature-item {
    padding: 1.2rem;
    background: #f8f8f8;
    border-radius: 12px;
}
.feature-item h4 {
    color: #2e7d32;
    margin-bottom: 0.5rem;
    font-size: 1.2rem;
}
.testnet-status {
    background: #e8f5e9;
    border-left: 4px solid #2e7d32;
    padding: 1rem;
    border-radius: 8px;
    margin: 1rem 0;
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
.contacts {
    text-align: center;
    margin: 2rem 0;
    padding: 1.5rem;
    background: #ffffff;
    border-radius: 12px;
}
.footer {
    text-align: center;
    padding: 2rem 0;
    border-top: 1px solid #ddd;
    color: #666;
}
</style>
</head>
<body>
<div class="container">

<!-- ===== HERO-БЛОК (ВСЯ ВАЖНАЯ ИНФОРМАЦИЯ СВЕРХУ) ===== -->
<div class="hero">
    <h1>⚡ ACCUM</h1>
    <div class="hero-tagline">Bitcoin is a lottery. ACCUM is a salary.</div>
    
    <div class="hero-grid">
        <div class="hero-item">
            <strong>💰 Монета $ACM</strong>
            <p>• Максимум: 21 000 000</p>
            <p>• Без премайна</p>
            <p>• Только майнинг</p>
        </div>
        <div class="hero-item">
            <strong>⚙️ Accumulative Mining</strong>
            <p>Каждый майнер получает награду за каждый блок</p>
            <p style="font-family:monospace; background:rgba(0,0,0,0.2); padding:0.3rem; border-radius:4px;">R_i = R_block · (h_i / H)</p>
        </div>
        <div class="hero-item">
            <strong>📉 Concave Rewards</strong>
            <p>Логарифмическая кривая делает 51% атаку невыгодной</p>
            <p style="font-family:monospace; background:rgba(0,0,0,0.2); padding:0.3rem; border-radius:4px;">R ∼ log₂(1 + h/h₀)</p>
        </div>
        <div class="hero-item">
            <strong>🛡️ PoCI (Anti-Sybil)</strong>
            <p>Репутация = хешрейт (40%) + аптайм (20%) + верификация (15%) + возраст (10%) + история (5%)</p>
        </div>
    </div>
    
    <div style="margin-top:2rem; background:rgba(0,0,0,0.2); padding:1rem; border-radius:12px;">
        <strong>🔬 ТЕСТИРУЕТСЯ:</strong> Две ноды в P2P-сети, майнинг, транзакции, сборка блоков
    </div>
</div>

<!-- ===== ГРАФИК ===== -->
<div class="card">
    <h2>📈 Логарифмические награды</h2>
    <canvas id="rewardChart"></canvas>
    <p style="text-align:center; margin-top:0.5rem;">Зелёный — ACCUM (log), пунктир — Bitcoin (linear)</p>
</div>

<!-- ===== ДЕТАЛЬНОЕ ОПИСАНИЕ МЕХАНИЗМОВ ===== -->
<div class="card">
    <h2>⚙️ Механизмы ACCUM</h2>
    
    <h3>1. Accumulative Mining</h3>
    <p>В Bitcoin только один майнер получает награду за блок. В ACCUM — все участники пропорционально вкладу:</p>
    <div class="code">R_i = R_block · (h_i / H)</div>
    <p>где h_i — хешрейт майнера, H — общий хешрейт сети.</p>
    
    <h3>2. Concave Rewards</h3>
    <p>Чтобы предотвратить доминирование крупных майнеров, используется логарифмическое масштабирование:</p>
    <div class="code">R_i = R_block · log₂(1 + h_i/h₀) / log₂(1 + H/h₀)</div>
    <p><strong>Эффект:</strong> 10-кратный рост хешрейта даёт лишь ~3-кратный рост награды.</p>
    
    <div class="formula-block">
        <p><strong>Пример:</strong></p>
        <p>10 MH/s → 5 ACM/блок</p>
        <p>100 MH/s → 15 ACM/блок</p>
        <p>1000 MH/s → 25 ACM/блок</p>
    </div>
</div>

<!-- ===== БЕЗОПАСНОСТЬ (PoCI) ===== -->
<div class="card">
    <h2>🛡️ Proof-of-Contribution-and-Identity (PoCI)</h2>
    <p>Защита от Sybil-атак через многокомпонентную репутацию:</p>
    
    <div class="code">S = 0.4·C_hash + 0.2·T_uptime + 0.15·V_tx + 0.1·B_bandwidth + 0.1·A_age + 0.05·H_history</div>
    
    <div class="feature-grid">
        <div class="feature-item">
            <h4>Хешрейт (40%)</h4>
            <p>Доказанная вычислительная работа</p>
        </div>
        <div class="feature-item">
            <h4>Аптайм (20%)</h4>
            <p>Время непрерывной работы ноды</p>
        </div>
        <div class="feature-item">
            <h4>Верификация транзакций (15%)</h4>
            <p>Количество проверенных и разосланных транзакций</p>
        </div>
        <div class="feature-item">
            <h4>Пропускная способность (10%)</h4>
            <p>Вклад в пиринговую сеть</p>
        </div>
        <div class="feature-item">
            <h4>Возраст в сети (10%)</h4>
            <p>Как долго нода участвует</p>
        </div>
        <div class="feature-item">
            <h4>Честная история (5%)</h4>
            <p>Отсутствие вредоносных действий</p>
        </div>
    </div>
    
    <p><strong>Итог:</strong> 1000 фейковых нод имеют репутацию ниже, чем одна реальная нода с годом истории.</p>
</div>

<!-- ===== ЭКОНОМИЧЕСКАЯ МОДЕЛЬ (ПОЛНЫЕ ФОРМУЛЫ) ===== -->
<div class="card">
    <h2>🔐 Экономическая модель</h2>
    
    <h3>Линейная модель (Bitcoin)</h3>
    <div class="code">E = α · B</div>
    <p>ΔRevenue ∝ Δα — стимул к централизации</p>
    
    <h3>Вогнутая модель (ACCUM)</h3>
    <div class="code">R(n) = k · log(1 + n)</div>
    <p>Производная (предельная награда):</p>
    <div class="code">dR/dn = k / (1 + n)</div>
    <p>С ростом n стимул наращивать хешрейт падает.</p>
    
    <h3>Сравнение эффекта доминирования</h3>
    <div class="formula-block">
        <p><strong>Bitcoin:</strong> увеличение доли с 10% до 20% удваивает доход</p>
        <p><strong>ACCUM:</strong> увеличение с 10% до 20% даёт прирост дохода ~1.3×</p>
    </div>
    
    <h3>Условие невыгодности 51% атаки</h3>
    <div class="code">R_attacker = R_block · log₂(1 + 0.51H/h₀) / log₂(1 + H/h₀) &lt; 0.51 · R_block</div>
    <p>Атакующий платит за 51% хешрейта, но получает меньше 51% награды.</p>
</div>

<!-- ===== ДОПОЛНИТЕЛЬНЫЕ ТЕХНОЛОГИИ ===== -->
<div class="card">
    <h2>🔧 Дополнительные возможности</h2>
    
    <div class="feature-grid">
        <div class="feature-item">
            <h4>Shard Streams</h4>
            <p>Токенизация будущих наград майнеров для мгновенной ликвидности (DeFi-слой)</p>
        </div>
        <div class="feature-item">
            <h4>Ultra-Light Nodes</h4>
            <p>Полная верификация с состоянием ~50 МБ, синхронизация за 5 минут, работа на телефонах и роутерах</p>
        </div>
        <div class="feature-item">
            <h4>Argon2id PoW</h4>
            <p>Memory-hard хеширование для ASIC-устойчивости на уровне шардов</p>
        </div>
    </div>
</div>

<!-- ===== ССЫЛКИ (ТОЛЬКО ВНИЗУ) ===== -->
<div class="card" style="text-align:center;">
    <h2>📚 Исходный код и whitepaper</h2>
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
    const w = canvas.clientWidth, h = 280;
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
    ctx.fillText("ACCUM (log)", w - 110, pad.top + 16);

    ctx.fillStyle = "#777";
    ctx.fillRect(w - 130, pad.top + 30, 12, 12);
    ctx.fillText("Bitcoin (linear)", w - 110, pad.top + 41);
}
window.addEventListener('load', drawChart);
window.addEventListener('resize', drawChart);
</script>
</body>
</html>
