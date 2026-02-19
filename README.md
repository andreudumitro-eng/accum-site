# accum-site 
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ACCUM — Fair Proof-of-Work Blockchain</title>
<style>
    * { margin:0; padding:0; box-sizing:border-box; }
    body { background:#f4f5f7; color:#1c1c1c; font-family:-apple-system,Segoe UI,Roboto,Helvetica,Arial,sans-serif; line-height:1.6; }
    .container { max-width:1000px; margin:0 auto; padding:2rem 1.5rem; }
    header { text-align:center; margin-bottom:2rem; }
    h1 { font-size:4rem; font-weight:700; background:linear-gradient(135deg,#2e7d32,#1b5e20); -webkit-background-clip:text; -webkit-text-fill-color:transparent; margin-bottom:0.5rem; }
    .subtitle { font-size:1.5rem; color:#4a4a4a; margin-bottom:1rem; }
    .tagline { font-size:1.8rem; font-weight:500; color:#2e7d32; margin:1rem 0; }
    .section { margin:2rem 0; }
    .graph-card, .feature, .status-card { background:#ffffff; border:1px solid #c1c1c1; border-radius:16px; padding:1.5rem; margin-bottom:1.5rem; }
    canvas { width:100%; height:250px; border-radius:12px; background:#f4f5f7; }
    h2 { color:#2e7d32; font-size:1.8rem; margin-bottom:1rem; }
    .features { display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr)); gap:1.5rem; margin:2rem 0; }
    .feature h3 { color:#2e7d32; font-size:1.4rem; margin-bottom:0.8rem; }
    .feature p { color:#4a4a4a; }
    .status-grid { display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; margin-top:1.5rem; }
    .stat-item { background:#f4f5f7; padding:1rem; border-radius:12px; text-align:center; }
    .stat-value { font-size:2rem; font-weight:700; color:#2e7d32; }
    .stat-label { font-size:0.9rem; color:#4a4a4a; }
    .links { text-align:center; padding:2rem; border-radius:16px; border:1px solid #c1c1c1; margin:2rem 0; }
    .button { display:inline-block; background:#2e7d32; color:#fff; text-decoration:none; padding:0.9rem 2rem; border-radius:40px; font-weight:600; margin:0.5rem; transition:background 0.2s; border:none; cursor:pointer; font-size:1rem; }
    .button:hover { background:#1b5e20; }
    .button.outline { background:transparent; border:1px solid #2e7d32; color:#2e7d32; }
    .button.outline:hover { background:rgba(46,125,50,0.1); }
    .contacts { text-align:center; margin:2rem 0; font-size:1.2rem; }
    .contacts a { color:#2e7d32; text-decoration:none; }
    .footer { text-align:center; padding:2rem 0; border-top:1px solid #c1c1c1; color:#6f7887; }
    @media (max-width:600px){ h1{ font-size:3rem; } .tagline{ font-size:1.5rem; } }
</style>
</head>
<body>
<div class="container">
    <header>
        <h1>ACCUM</h1>
        <div class="subtitle">The First Fair Proof-of-Work Blockchain</div>
        <div class="tagline">Bitcoin is a lottery. ACCUM is a salary.</div>
    </header>

    <div class="section">
        <h2>Что такое ACCUM?</h2>
        <p>ACCUM — это блокчейн нового поколения с честным Proof-of-Work, где каждый майнер получает награду за каждый найденный блок, без лотерей и случайных выигрышей.</p>
        <p>Создаётся новая монета <strong>ACCUM</strong>, которая начисляется автоматически каждому участнику сети в зависимости от его участия и количества найденных шардов.</p>
        <p>Механизм <strong>PoCI</strong> (Proof-of-Contribution-and-Identity) защищает сеть от Sybil-атак, а <strong>Ultra-Light Nodes</strong> позволяют держать полную верификацию состояния всего в 50 МБ.</p>
    </div>

    <!-- LIVE TESTNET STATUS -->
    <div class="status-card">
        <h2>✅ Live Testnet (Q1 2026)</h2>
        <p>Две независимые ноды работают в реальной сети, производя блоки и обрабатывая транзакции.</p>
        <div class="status-grid">
            <div class="stat-item"><div class="stat-value">62</div><div class="stat-label">Блоков</div></div>
            <div class="stat-item"><div class="stat-value">18</div><div class="stat-label">Транзакций</div></div>
            <div class="stat-item"><div class="stat-value">100%</div><div class="stat-label">Синхронизация</div></div>
        </div>
        <ul style="margin-top:1rem; margin-left:1.2rem;">
            <li>✅ Две ноды (порты 12345, 12346) работают непрерывно</li>
            <li>✅ Блоки производятся каждые 60 секунд</li>
            <li>✅ Тестовые переводы по 10 ACCUM проходят в сеть</li>
            <li>✅ Доступны логи и демо по запросу</li>
        </ul>
    </div>

    <div class="graph-card">
        <h2>📈 Награды майнеров</h2>
        <canvas id="rewardChart"></canvas>
        <div style="margin-top:0.5rem; color:#555; font-size:0.95rem; text-align:center;">
            Зеленая — логарифмическая кривая ACCUM (вогнутые награды), пунктир — линейная модель Bitcoin.
        </div>
        <p style="margin-top:1rem; color:#333;">
            Формула ACCUM: <strong>Reward = total_reward × (s × (1 - α × s)) / Σ</strong>, где s — доля шардов майнера в блоке, α = 0.3.<br>
            Пример: если 10 шардов в блоке, 3 принадлежат майнеру A, то доля s = 3/10, вес = s*(1-0.3*s), и его награда = 50 × (w/Σw) ACCUM.
        </p>
    </div>

    <div class="features">
        <div class="feature">
            <h3>Accumulative Mining</h3>
            <p>Каждый майнер получает награду за каждый блок. Никакой лотереи.</p>
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
            <p>Полная верификация с 50 МБ состояния. Работает на телефонах.</p>
        </div>
    </div>

    <div class="links">
        <h2>Source Code & Whitepaper</h2>
        <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
        <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">📄 Whitepaper (EN)</a>
        <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">📄 Whitepaper (RU)</a>
    </div>

    <div class="contacts">
        <p>📧 <strong>andreudumitro@gmail.com</strong> &nbsp; | &nbsp; 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a></p>
        <p style="margin-top:0.5rem; font-size:1rem; color:#4a4a4a;">По вопросам сотрудничества и демо — пишите на email.</p>
    </div>

    <footer class="footer">
        <p>© 2026 Andrii Dumitro — ACCUM. All rights reserved.</p>
    </footer>
</div>

<script>
function drawChart(){
    const canvas = document.getElementById('rewardChart');
    const ctx = canvas.getContext('2d');
    const w = canvas.clientWidth; const h = 250;
    canvas.width = w; canvas.height = h;
    const pad = {left:50,right:20,top:20,bottom:30};
    const gw = w-pad.left-pad.right; const gh = h-pad.top-pad.bottom;

    // Сетка
    ctx.strokeStyle="#ccc"; ctx.lineWidth=0.5;
    for(let i=0;i<=5;i++){
        let y=pad.top+(i/5)*gh;
        ctx.beginPath(); ctx.moveTo(pad.left,y); ctx.lineTo(w-pad.right,y); ctx.stroke();
    }

    // Линейная Bitcoin (пунктир)
    ctx.strokeStyle="#777"; ctx.lineWidth=2; ctx.setLineDash([5,3]); ctx.beginPath();
    for(let x=1;x<=100;x++){
        let dx=pad.left+(x/100)*gw; let dy=h-pad.bottom-(x/100)*gh;
        if(x===1) ctx.moveTo(dx,dy); else ctx.lineTo(dx,dy);
    }
    ctx.stroke();

    // Логарифмическая ACCUM
    ctx.strokeStyle="#2e7d32"; ctx.lineWidth=3; ctx.setLineDash([]); ctx.beginPath();
    const maxLog=Math.log2(101);
    for(let x=1;x<=100;x++){
        let val=Math.log2(1+x)/maxLog;
        let dx=pad.left+(x/100)*gw; let dy=h-pad.bottom-val*gh;
        if(x===1) ctx.moveTo(dx,dy); else ctx.lineTo(dx,dy);
    }
    ctx.stroke();

    // Легенда
    ctx.fillStyle="#2e7d32"; ctx.fillRect(w-180,pad.top+5,12,12);
    ctx.fillStyle="#333"; ctx.font="12px Arial"; ctx.textAlign="left"; ctx.fillText("Логарифмическая (ACCUM)",w-160,pad.top+16);
    ctx.fillStyle="#777"; ctx.fillRect(w-180,pad.top+30,12,12); ctx.fillStyle="#333";
    ctx.fillText("Линейная (Bitcoin)",w-160,pad.top+41);

    // Подписи
    ctx.fillStyle="#333"; ctx.font="12px Arial"; ctx.textAlign="right"; ctx.fillText("Награда",pad.left-10,pad.top+10);
    ctx.textAlign="center"; ctx.fillText("Шарды",w/2,h-5);
}
window.addEventListener('load',drawChart);
window.addEventListener('resize',drawChart);
</script>
</body>
</html>
