<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>ACCUM — справедливый Proof-of-Work блокчейн</title>
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
  header {
    background: #2e7d32;
    color: white;
    padding: 1rem 2rem;
    position: sticky;
    top: 0;
    z-index: 1000;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }
  header nav {
    max-width: 1300px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }
  header nav a {
    color: white;
    text-decoration: none;
    font-weight: 600;
    margin-left: 1.2rem;
    font-size: 1.1rem;
  }
  header nav a:hover {
    text-decoration: underline;
  }
  header nav ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem 1rem;
  }
  header nav ul li a {
    margin-left: 0;
    padding: 0.3rem 0.8rem;
    border-radius: 30px;
    transition: background 0.2s;
  }
  header nav ul li a:hover {
    background: rgba(255,255,255,0.15);
    text-decoration: none;
  }
  .container {
    max-width: 1300px;
    margin: 2rem auto 4rem;
    padding: 0 1.5rem;
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
    background: rgba(255,255,255,0.85);
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
  .glance-grid,
  .tech-grid,
  .roadmap-grid,
  .contribute-grid,
  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1.5rem;
    margin-top: 1rem;
  }
  .glance-item,
  .tech-item,
  .roadmap-item,
  .contribute-item,
  .feature-card {
    background: white;
    border-radius: 20px;
    padding: 1.5rem;
    box-shadow: 0 2px 10px rgba(0,0,0,0.04);
    border: 1px solid #e2e8f0;
  }
  .glance-item strong,
  .tech-item strong {
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
  .chart-container {
    position: relative;
    width: 100%;
    margin: 1rem 0;
  }
  canvas {
    width: 100%;
    height: 300px;
    background: #ffffff;
    border-radius: 20px;
    padding: 1rem;
    box-shadow: inset 0 2px 8px rgba(0,0,0,0.02);
    display: block;
  }
  .tooltip-value {
    position: absolute;
    background: #1e293b;
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 30px;
    font-size: 0.9rem;
    pointer-events: none;
    opacity: 0;
    transition: opacity 0.2s;
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    z-index: 100;
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
  .code-block {
    background: #1e293b;
    color: #a5d6a5;
    padding: 1.5rem;
    border-radius: 12px;
    font-family: 'JetBrains Mono', monospace;
    overflow-x: auto;
    margin: 1rem 0;
    font-size: 0.9rem;
    line-height: 1.4;
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
    user-select: none;
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
  footer.footer {
    text-align: center;
    padding: 2rem 0;
    color: #64748b;
    border-top: 1px solid #cbd5e1;
    font-size: 0.9rem;
  }
  ol {
    margin-left: 1.5rem;
  }
  ol li {
    margin-bottom: 0.5rem;
    font-size: 1.1rem;
  }
  @media (max-width: 600px) {
    .hero h1 { font-size: 2.6rem; }
    header nav ul { flex-direction: column; gap: 0.5rem; }
    header nav ul li a { display: block; padding: 0.3rem 0; }
  }
</style>
</head>
<body>

<header>
  <nav id="page-nav">
    <div><a href="#hero">⚡ ACCUM</a></div>
    <ul>
      <li><a href="#about">О проекте</a></li>
      <li><a href="#glance">Ключевые факты</a></li>
      <li><a href="#technical">Характеристики</a></li>
      <li><a href="#rewards">Награды</a></li>
      <li><a href="#comparison">Сравнение</a></li>
      <li><a href="#features">Инновации</a></li>
      <li><a href="#testnet">Тестнет</a></li>
      <li><a href="#economics">Экономика</a></li>
      <li><a href="#roadmap">Roadmap</a></li>
      <li><a href="#mining-code">Код майнинга</a></li>
      <li><a href="#contribute">Участие</a></li>
      <li><a href="#contacts">Контакты</a></li>
    </ul>
  </nav>
</header>

<div class="container">

<!-- 1. HERO -->
<section id="hero" class="hero">
  <h1>⚡ ACCUM</h1>
  <p class="lead">Первый справедливый Proof-of-Work блокчейн</p>
  <p class="sublead">Bitcoin — лотерея. ACCUM — зарплата. Каждый майнер получает награду за каждый блок.</p>
  <div class="hero-grid">
    <div class="hero-item"><strong>💰 Монета</strong> $ACM · 21 млн · без премайна</div>
    <div class="hero-item"><strong>⚙️ Механизм</strong> Accumulative Mining + Concave Rewards</div>
    <div class="hero-item"><strong>🔬 Статус</strong> Живой тестнет · 2 ноды · блоки идут</div>
    <div class="hero-item"><strong>🛡️ Безопасность</strong> PoCI · P2P · Ultra‑Light Nodes</div>
  </div>
</section>

<!-- О ПРОЕКТЕ -->
<section id="about" class="section">
  <h2>ℹ️ О проекте ACCUM</h2>
  <p>ACCUM — это блокчейн с честным консенсусом Proof-of-Work. В отличие от Bitcoin, где майнинг — лотерея с одним победителем, ACCUM предлагает стабильный доход для каждого участника майнинга.</p>
  <p>Идея возникла из несправедливости классических моделей: в Bitcoin награду получает только один майнер за блок, что создаёт неравенство и нестабильность доходов. ACCUM меняет модель, чтобы майнеры получали зарплату, а не выигрывали в лотерее.</p>
  <p>В основе лежит <strong>Accumulative Mining</strong> с <strong>Concave Rewards</strong> — логарифмическое распределение наград, снижающее мотивацию захвата сети и повышающее безопасность. Проект ориентирован на широкое участие и доступность даже на мобильных устройствах.</p>
</section>

<!-- КЛЮЧЕВЫЕ ФАКТЫ -->
<section id="glance" class="section">
  <h2>⚡ ACCUM в цифрах</h2>
  <div class="glance-grid">
    <div class="glance-item"><strong>Fair Launch</strong><br>Февраль 2026 (тестнет)<br><small>без премайна</small></div>
    <div class="glance-item"><strong>Алгоритм</strong><br>Argon2id<br><small>memory‑hard, ASIC‑resistant</small></div>
    <div class="glance-item"><strong>Консенсус</strong><br>Proof‑of‑Work<br><small>Accumulative + Concave</small></div>
    <div class="glance-item"><strong>Платформы</strong><br>Windows, Linux, macOS<br><small>RPi, Android (скоро)</small></div>
    <div class="glance-item"><strong>Тикер</strong><br>$ACM</div>
    <div class="glance-item"><strong>Блок (тестнет)</strong><br>~60 секунд</div>
    <div class="glance-item"><strong>В обращении (тестнет)</strong><br>~1050 ACM</div>
    <div class="glance-item"><strong>Макс. предложение</strong><br>21 000 000</div>
    <div class="glance-item"><strong>Статус сети</strong><br>2 ноды · 62 блока</div>
  </div>
</section>

<!-- ТЕХНИЧЕСКИЕ ХАРАКТЕРИСТИКИ -->
<section id="technical" class="section">
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
    <div class="tech-item"><strong>Мин. требования</strong><br>2 ядра, 2 ГБ RAM</div>
    <div class="tech-item"><strong>Размер ноды</strong><br>~1–2 МБ (будет < 50 МБ)</div>
  </div>
</section>

<!-- ГРАФИК НАГРАД (ИНТЕРАКТИВНЫЙ) -->
<section id="rewards" class="section">
  <h2>📈 Логарифмические награды (наведи мышкой)</h2>
  <p><strong>Формула:</strong> R(n) = 50 · log₂(1 + n) / log₂(101), где n — доля майнера в сети.</p>
  <p>Производная убывает, что снижает выгоду доминирования и делает 51% атаку экономически невыгодной.</p>
  <div class="chart-container">
    <canvas id="rewardChart" width="800" height="300"></canvas>
    <div id="chartTooltip" class="tooltip-value" style="opacity:0;">0</div>
  </div>
</section>

<!-- ТАБЛИЦА СРАВНЕНИЯ -->
<section id="comparison" class="section">
  <h2>🔍 Сравнение с другими PoW</h2>
  <table>
    <thead><tr><th>Параметр</th><th>Bitcoin</th><th>Kaspa</th><th>Monero</th><th>ACCUM</th></tr></thead>
    <tbody>
      <tr><td>Модель наград</td><td>Линейная лотерея</td><td>Block DAG Linear</td><td>Линейная лотерея</td><td>Вогнутая (все получают)</td></tr>
      <tr><td>Премайн</td><td>Нет</td><td>Нет</td><td>Нет</td><td>Нет</td></tr>
      <tr><td>Награда за блок</td><td>1 победитель</td><td>1 победитель</td><td>1 победитель</td><td>Все участники</td></tr>
      <tr><td>Защита от Sybil</td><td>Нет</td><td>Нет</td><td>Нет</td><td>PoCI</td></tr>
      <tr><td>51% атака</td><td>Выгодна</td><td>Выгодна</td><td>Выгодна</td><td>Экономически невыгодна</td></tr>
      <tr><td>Ультра‑легкие ноды</td><td>Нет</td><td>Нет</td><td>Нет</td><td>Да (~50 МБ)</td></tr>
    </tbody>
  </table>
</section>

<!-- 5 КЛЮЧЕВЫХ ФИЧ -->
<section id="features" class="section">
  <h2>🔷 5 инноваций ACCUM</h2>
  <div class="features-grid">
    <div class="feature-card"><h3>⛏️ Accumulative Mining</h3><p>Каждый майнер получает награду за каждый блок. Без лотереи.</p></div>
    <div class="feature-card"><h3>📉 Вогнутые награды</h3><p>Логарифмическая кривая делает 51% атаку невыгодной.</p></div>
    <div class="feature-card"><h3>🆔 PoCI</h3><p>Многокомпонентная репутация против Sybil-атак.</p></div>
    <div class="feature-card"><h3>💧 Shard Streams</h3><p>Фьючерсы на хешрейт для мгновенной ликвидности.</p></div>
    <div class="feature-card"><h3>📱 Ultra‑Light Nodes</h3><p>Полная верификация ~50 МБ, работает на телефонах.</p></div>
  </div>
</section>

<!-- СТАТУС ТЕСТНЕТА -->
<section id="testnet" class="section">
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
</section>

<!-- ЭКОНОМИЧЕСКАЯ МОДЕЛЬ -->
<section id="economics" class="section">
  <h2>🔐 Экономическая модель</h2>
  <p><strong>Bitcoin (линейная):</strong> E = α·B — награда линейно зависит от вложений.</p>
  <p><strong>ACCUM (логарифмическая):</strong> R(n) = k·log(1+n) — награда растёт медленнее доли.</p>
  <p>С увеличением доли майнера доходы растут, но с убывающей скоростью, уменьшая преимущества доминирования.</p>
</section>

<!-- ДОРОЖНАЯ КАРТА -->
<section id="roadmap" class="section">
  <h2>🗺️ Дорожная карта</h2>
  <div class="roadmap-grid">
    <div class="roadmap-item"><strong>Q3 2026</strong><br>Публичный тестнет</div>
    <div class="roadmap-item"><strong>Q4 2026</strong><br>Аудит безопасности</div>
    <div class="roadmap-item"><strong>Q1 2027</strong><br>Запуск Mainnet</div>
    <div class="roadmap-item"><strong>Q2 2027</strong><br>Shard Streams</div>
  </div>
</section>

<!-- КОД МАЙНИНГА ДВУХ НОД -->
<section id="mining-code" class="section">
  <h2>⛏️ Код майнинга (две ноды)</h2>
  <p>Ниже представлен упрощённый код, запускающий две ноды, майнинг шардов и обмен блоками.</p>
  <div class="code-block">
<pre>import asyncio
from wallet import Wallet
from node import P2PNode, Miner
from db import Database

async def run_node(name, port, db_file, connect_to=None):
    wallet = Wallet()
    db = Database(db_file)
    p2p = P2PNode(port, db, wallet.get_address(), name)
    await p2p.start()
    print(f"[{name}] Адрес: {wallet.get_address()}")
    if connect_to:
        host, cport = connect_to
        await p2p.connect_to_peer(host, cport)
        if name == "Node2":
            asyncio.create_task(send_test_tx(p2p, wallet))
    miner = Miner(wallet.get_address(), db, p2p, name)
    await asyncio.gather(miner.mine(), miner.assemble_blocks())

async def main():
    await asyncio.gather(
        run_node("Node1", 12345, "node1.db", None),
        run_node("Node2", 12346, "node2.db", ("127.0.0.1", 12345))
    )

if __name__ == "__main__":
    asyncio.run(main())</pre>
  </div>
  <p>Полный код доступен в <a href="https://github.com/andreudumitro-eng/ACCUM" target="_blank" rel="noopener">репозитории GitHub</a>.</p>
</section>

<!-- УЧАСТИЕ В ПРОЕКТЕ -->
<section id="contribute" class="section">
  <h2>🧑‍💻 Нам нужны ваши навыки</h2>
  <p>ACCUM живёт благодаря сообществу. Присоединяйся!</p>
  <div class="contribute-grid">
    <div class="contribute-item"><strong>🦀 Rust‑разработчики</strong><br>Ядро, P2P, консенсус</div>
    <div class="contribute-item"><strong>🐍 Python‑тестеры</strong><br>Тестнет, баги, оптимизация</div>
    <div class="contribute-item"><strong>📝 Документация</strong><br>Переводы, гайды, статьи</div>
  </div>
  <a href="https://github.com/andreudumitro-eng/ACCUM/issues" class="button">📌 GitHub Issues</a>
</section>

<!-- КОНТАКТЫ И ССЫЛКИ -->
<section id="contacts" class="section">
  <h2>📚 Исходный код и документы</h2>
  <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
  <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">📄 Whitepaper (RU)</a>
  <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">📄 Whitepaper (EN)</a>
  <div style="margin-top:1.5rem; font-size:1.1rem;">
    📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a>
  </div>
</section>

</div>

<footer class="footer">
  © 2026 Andrii Dumitro — ACCUM. Открытый код · Честный запуск · Без премайна
</footer>

<script>
(function() {
  const canvas = document.getElementById('rewardChart');
  if (!canvas) return;
  
  const ctx = canvas.getContext('2d');
  const tooltip = document.getElementById('chartTooltip');
  
  function resizeCanvas() {
    const containerWidth = canvas.parentElement.clientWidth;
    canvas.width = containerWidth;
    canvas.height = 300;
    drawChart();
  }
  
  function drawChart() {
    const w = canvas.width;
    const h = canvas.height;
    const pad = { left: 60, right: 20, top: 20, bottom: 30 };
    const gw = w - pad.left - pad.right;
    const gh = h - pad.top - pad.bottom;
    
    ctx.clearRect(0, 0, w, h);
    
    // Сетка
    ctx.strokeStyle = "#ccc";
    ctx.lineWidth = 0.5;
    for (let i = 0; i <= 5; i++) {
      let y = pad.top + (i/5) * gh;
      ctx.beginPath();
      ctx.moveTo(pad.left, y);
      ctx.lineTo(w - pad.right, y);
      ctx.stroke();
    }
    
    // Ось X
    ctx.fillStyle = "#555";
    ctx.font = "11px Arial";
    ctx.textAlign = "center";
    for (let i = 0; i <= 5; i++) {
      let x = pad.left + (i/5) * gw;
      let label = Math.round(i/5 * 100);
      ctx.fillText(label + "%", x, h - pad.bottom + 18);
    }
    
    // Bitcoin (пунктир)
    ctx.strokeStyle = "#777";
    ctx.lineWidth = 2;
    ctx.setLineDash([5, 3]);
    ctx.beginPath();
    for (let x = 0; x <= 100; x++) {
      let dx = pad.left + (x/100) * gw;
      let dy = h - pad.bottom - (x/100) * gh;
      if (x === 0) ctx.moveTo(dx, dy);
      else ctx.lineTo(dx, dy);
    }
    ctx.stroke();
    
    // ACCUM (логарифмическая)
    ctx.strokeStyle = "#2e7d32";
    ctx.lineWidth = 3;
    ctx.setLineDash([]);
    ctx.beginPath();
    const maxLog = Math.log2(101);
    for (let x = 0; x <= 100; x++) {
      let val = Math.log2(1 + x) / maxLog;
      let dx = pad.left + (x/100) * gw;
      let dy = h - pad.bottom - val * gh;
      if (x === 0) ctx.moveTo(dx, dy);
      else ctx.lineTo(dx, dy);
    }
    ctx.stroke();
    
    // Легенда
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
  
  // Интерактивность при наведении мыши
  function handleMouseMove(e) {
    const rect = canvas.getBoundingClientRect();
    const scaleX = canvas.width / rect.width;
    const scaleY = canvas.height / rect.height;
    
    const mouseX = (e.clientX - rect.left) * scaleX;
    const mouseY = (e.clientY - rect.top) * scaleY;
    
    const w = canvas.width;
    const h = canvas.height;
    const pad = { left: 60, right: 20, top: 20, bottom: 30 };
    const gw = w - pad.left - pad.right;
    const gh = h - pad.top - pad.bottom;
    
    // Проверяем, попадает ли мышь в область графика
    if (mouseX >= pad.left && mouseX <= w - pad.right && mouseY >= pad.top && mouseY <= h - pad.bottom) {
      const xPercent = (mouseX - pad.left) / gw;
      const xValue = Math.round(xPercent * 100);
      const yBitcoin = h - pad.bottom - xPercent * gh;
      const maxLog = Math.log2(101);
      const yAccum = h - pad.bottom - (Math.log2(1 + xValue) / maxLog) * gh;
      
      // Находим ближайшую точку на кривой ACCUM
      let minDist = Infinity;
      let bestValue = 0;
      for (let testX = 0; testX <= 100; testX++) {
        let testDx = pad.left + (testX/100) * gw;
        let testVal = Math.log2(1 + testX) / maxLog;
        let testDy = h - pad.bottom - testVal * gh;
        let dist = Math.hypot(testDx - mouseX, testDy - mouseY);
        if (dist < minDist) {
          minDist = dist;
          bestValue = testX;
        }
      }
      
      if (minDist < 30) {
        let rewardPercent = (Math.log2(1 + bestValue) / maxLog * 100).toFixed(1);
        tooltip.style.opacity = 1;
        tooltip.style.left = (e.clientX - rect.left + 20) + 'px';
        tooltip.style.top = (e.clientY - rect.top - 40) + 'px';
        tooltip.textContent = `${bestValue}% хешрейта → ${rewardPercent}% награды`;
      } else {
        tooltip.style.opacity = 0;
      }
    } else {
      tooltip.style.opacity = 0;
    }
  }
  
  window.addEventListener('resize', () => {
    resizeCanvas();
    drawChart();
  });
  
  canvas.addEventListener('mousemove', handleMouseMove);
  canvas.addEventListener('mouseleave', () => {
    tooltip.style.opacity = 0;
  });
  
  resizeCanvas();
  drawChart();
})();
</script>

</body>
</html>
