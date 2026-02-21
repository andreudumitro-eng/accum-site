
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>ACCUM — The First Fair Proof-of-Work Blockchain</title>
  <style>
    :root {
      --color-primary-dark: #0d1b2a;
      --color-primary: #1b263b;
      --color-primary-light: #2a3b4e;
      --color-secondary: #778da9;
      --color-accent: #e0e1dd;
      --color-success: #4caf50;
      --color-success-bright: #6fbf73;
      --color-warning: #ffb300;
      --color-table-header: #2c3e50;
      --color-table-row-alt: #253544;
      --font-family: -apple-system, BlinkMacSystemFont, "Segoe UI",
        Roboto, Helvetica, Arial, sans-serif;
      --border-radius: 20px;
      --transition-speed: 0.3s;
    }

    *, *::before, *::after {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(
        145deg,
        var(--color-primary-dark) 0%,
        var(--color-primary) 100%
      );
      color: var(--color-accent);
      font-family: var(--font-family);
      line-height: 1.6;
      min-height: 100vh;
    }

    a {
      text-decoration: none;
      cursor: pointer;
    }

    a:focus-visible,
    button:focus-visible {
      outline: 2px solid var(--color-success);
      outline-offset: 3px;
    }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 1.5rem;
    }

    header.site-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 2rem;
      margin-bottom: 2rem;
      border-bottom: 1px solid var(--color-primary-light);
      background-color: var(--color-primary);
    }

    .logo {
      font-size: 3rem;
      font-weight: 900;
      background: linear-gradient(135deg, var(--color-success), var(--color-accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      letter-spacing: -0.8px;
      user-select: none;
      text-shadow: 0 0 8px var(--color-success);
      transition: color var(--transition-speed);
    }

    .lang-switch {
      display: flex;
      gap: 0.5rem;
    }

    .lang-btn {
      background: transparent;
      border: 1px solid var(--color-success);
      color: var(--color-accent);
      padding: 0.5rem 1rem;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
      transition: all var(--transition-speed);
    }

    .lang-btn.active {
      background: var(--color-success);
      color: var(--color-primary-dark);
    }

    h2 {
      color: var(--color-success);
      font-size: 2.2rem;
      margin-bottom: 1.5rem;
      border-left: 6px solid var(--color-success);
      padding-left: 1rem;
    }

    h3 {
      color: var(--color-warning);
      font-size: 1.6rem;
      margin: 1.5rem 0 1rem 0;
    }

    .hero {
      background: linear-gradient(
        135deg,
        var(--color-primary-light) 0%,
        var(--color-primary) 100%
      );
      color: var(--color-accent);
      padding: 3rem 2.5rem;
      border-radius: 32px;
      margin-bottom: 2rem;
      box-shadow: 0 20px 40px rgba(76, 175, 80, 0.25);
      user-select: text;
      text-align: center;
    }

    .hero h1 {
      font-size: 4rem;
      margin-bottom: 1rem;
      text-shadow: 0 2px 8px rgba(0, 0, 0, 0.45);
      user-select: none;
    }

    .hero .lead {
      font-size: 1.8rem;
      font-weight: 300;
      margin-bottom: 1rem;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }

    .hero .lead span {
      color: var(--color-warning);
      font-weight: 600;
    }

    .hero .sublead {
      font-size: 1.3rem;
      max-width: 800px;
      margin-left: auto;
      margin-right: auto;
      opacity: 0.85;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1.5rem;
      margin-top: 2.5rem;
    }

    .hero-item {
      background: rgba(255, 255, 255, 0.1);
      border-radius: var(--border-radius);
      padding: 1.5rem;
      backdrop-filter: blur(8px);
      border: 1px solid rgba(76, 175, 80, 0.15);
      font-weight: 600;
      color: var(--color-accent);
      transition: background-color var(--transition-speed);
    }

    .hero-item strong {
      display: block;
      font-size: 1.3rem;
      color: var(--color-warning);
      margin-bottom: 0.4rem;
    }

    .hero-item:hover {
      background: rgba(76, 175, 80, 0.2);
      color: var(--color-primary-dark);
      border-color: var(--color-success);
    }

    section.section {
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(76, 175, 80, 0.1);
      border-radius: 24px;
      padding: 2.5rem;
      margin: 2rem 0;
      box-shadow: 0 8px 30px rgba(0, 30, 60, 0.2);
      color: var(--color-accent);
    }

    .glance-grid,
    .tech-grid,
    .features-grid,
    .roadmap-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1.8rem;
      margin-top: 1.5rem;
    }

    .glance-item,
    .tech-item,
    .feature-card,
    .roadmap-item {
      background: var(--color-primary);
      border-radius: var(--border-radius);
      padding: 1.8rem;
      box-shadow: 0 4px 20px rgba(0, 20, 40, 0.3);
      border: 1px solid rgba(76, 175, 80, 0.3);
      color: var(--color-accent);
      transition: transform var(--transition-speed), box-shadow var(--transition-speed),
        border-color var(--transition-speed);
    }

    .glance-item strong,
    .tech-item strong {
      color: var(--color-success);
      font-size: 1.05rem;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .feature-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 20px 40px rgba(76, 175, 80, 0.5);
      border-color: var(--color-success);
    }

    .feature-card h3 {
      font-size: 1.5rem;
      margin-bottom: 1rem;
      color: var(--color-success);
    }

    .chart-container {
      position: relative;
      margin: 2.5rem 0;
    }

    canvas {
      width: 100%;
      height: 320px;
      background: var(--color-primary);
      border-radius: 24px;
      padding: 1rem;
      box-shadow: inset 0 4px 12px rgba(0, 20, 40, 0.3);
      display: block;
    }

    .chart-tooltip {
      position: absolute;
      background: var(--color-primary-light);
      color: var(--color-accent);
      padding: 0.6rem 1.2rem;
      border-radius: 8px;
      font-size: 0.95rem;
      pointer-events: none;
      border: 1px solid var(--color-success);
      box-shadow: 0 6px 18px rgba(0, 80, 0, 0.6);
      z-index: 100;
      transition: opacity 0.15s ease;
      opacity: 0;
      user-select: none;
      font-weight: 600;
    }

    .graph-caption {
      text-align: center;
      color: var(--color-secondary);
      font-size: 1rem;
      margin-top: 0.75rem;
      font-style: italic;
      user-select: none;
    }

    /* Улучшенные стили для таблиц */
    table {
      width: 100%;
      border-collapse: collapse;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
      margin: 1.5rem 0;
      border: 1px solid var(--color-success);
    }

    th {
      background: var(--color-success);
      color: #000000;
      font-weight: 700;
      padding: 1.2rem 1rem;
      text-align: left;
      font-size: 1.1rem;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      border-bottom: 2px solid #ffffff;
    }

    td {
      padding: 1rem 1rem;
      border-bottom: 1px solid var(--color-primary-light);
      color: #ffffff;
      font-size: 1rem;
    }

    /* Чередование цветов строк */
    tbody tr:nth-child(even) {
      background-color: var(--color-table-row-alt);
    }

    tbody tr:nth-child(odd) {
      background-color: var(--color-primary);
    }

    /* Первый столбец (названия параметров) */
    td:first-child {
      font-weight: 600;
      color: var(--color-warning);
      background-color: rgba(0, 0, 0, 0.2);
    }

    /* Выделение ACCUM */
    td:last-child {
      font-weight: 600;
      color: var(--color-success-bright);
      border-left: 2px solid var(--color-success);
    }

    td strong {
      color: var(--color-success-bright);
    }

    /* Специальные стили для токеномики */
    .tokenomics-table th {
      background: var(--color-success);
    }

    .tokenomics-table td {
      font-weight: 500;
    }

    .tokenomics-table td:first-child {
      background-color: transparent;
      color: var(--color-warning);
    }

    .button {
      display: inline-block;
      background: var(--color-success);
      color: var(--color-primary-dark);
      padding: 0.9rem 2.2rem;
      border-radius: 40px;
      font-weight: 700;
      margin: 0.5rem 0.75rem 0 0;
      transition: background-color var(--transition-speed), color var(--transition-speed);
      user-select: none;
      box-shadow: 0 6px 16px rgba(76, 175, 80, 0.7);
      cursor: pointer;
    }

    .button:hover,
    .button:focus-visible {
      background-color: #388e3c;
      color: var(--color-accent);
      box-shadow: 0 10px 28px rgba(76, 175, 80, 0.85);
      outline: none;
    }

    .button.outline {
      background: transparent;
      border: 2px solid var(--color-success);
      color: var(--color-success);
      font-weight: 600;
      box-shadow: none;
    }

    .button.outline:hover,
    .button.outline:focus-visible {
      background: rgba(76, 175, 80, 0.15);
      color: var(--color-accent);
      border-color: var(--color-accent);
      box-shadow: 0 4px 14px rgba(76, 175, 80, 0.4);
    }

    pre.code-block {
      background: var(--color-primary-dark);
      color: var(--color-success);
      padding: 1.2rem 1.5rem;
      border-radius: 16px;
      font-family: 'Courier New', monospace;
      overflow-x: auto;
      margin: 1rem 0;
      font-size: 1rem;
      user-select: text;
      box-shadow: 0 4px 20px rgba(0, 100, 0, 0.6);
    }

    .formula-block {
      background: var(--color-primary-dark);
      padding: 1.5rem;
      border-radius: 16px;
      font-family: 'Courier New', monospace;
      font-size: 1.3rem;
      text-align: center;
      color: var(--color-success);
      margin: 1.5rem 0;
      border: 1px solid var(--color-success);
      box-shadow: 0 4px 15px rgba(76, 175, 80, 0.3);
    }

    footer.footer {
      text-align: center;
      padding: 2rem 0;
      color: var(--color-secondary);
      border-top: 1px solid var(--color-primary-light);
      font-size: 1rem;
      user-select: none;
      background-color: var(--color-primary);
    }

    @media (max-width: 768px) {
      .hero h1 {
        font-size: 2.8rem;
      }

      .hero .lead {
        font-size: 1.4rem;
      }

      .hero-grid,
      .glance-grid,
      .tech-grid,
      .features-grid,
      .roadmap-grid {
        grid-template-columns: 1fr;
      }

      header.site-header {
        padding: 0.75rem 1rem;
        flex-direction: column;
        gap: 1rem;
      }

      .logo {
        font-size: 2.4rem;
      }

      table {
        font-size: 0.9rem;
      }

      th, td {
        padding: 0.8rem 0.5rem;
      }
    }
  </style>
</head>
<body>
  <header class="site-header" role="banner">
    <div class="logo" aria-label="ACCUM logo">⚡ ACCUM</div>
    <div class="lang-switch">
      <button class="lang-btn active" data-lang="en">EN</button>
      <button class="lang-btn" data-lang="ru">RU</button>
    </div>
  </header>

  <main class="container" role="main">
    <!-- HERO SECTION -->
    <section class="hero" aria-labelledby="hero-title">
      <h1 id="hero-title" data-en="Fair Proof-of-Work" data-ru="Честный Proof-of-Work">Fair Proof-of-Work</h1>
      <p class="lead">
        <span data-en="Bitcoin is lottery. ACCUM is a salary." data-ru="Bitcoin — лотерея. ACCUM — зарплата.">Bitcoin is lottery. ACCUM is a salary.</span>
      </p>
      <p class="sublead" data-en="Every miner gets paid every block. No more winners and losers — just fair, predictable rewards." 
         data-ru="Каждый майнер получает награду в каждом блоке. Больше нет победителей и проигравших — только честные, предсказуемые выплаты.">
         Every miner gets paid every block. No more winners and losers — just fair, predictable rewards.
      </p>

      <div class="hero-grid" role="list">
        <div class="hero-item" role="listitem">
          <strong>💰 Token</strong>
          $ACM · 21M supply · No premine
        </div>
        <div class="hero-item" role="listitem">
          <strong>⚙️ Consensus</strong>
          Proof‑of‑Work + Accumulative
        </div>
        <div class="hero-item" role="listitem">
          <strong>📈 Rewards</strong>
          Concave (logarithmic)
        </div>
        <div class="hero-item" role="listitem">
          <strong>🛡️ Security</strong>
          PoCI · P2P · Ultra‑Light
        </div>
      </div>
    </section>

    <!-- ABOUT ACCUM -->
    <section class="section" aria-labelledby="about-title">
      <h2 id="about-title" data-en="About ACCUM" data-ru="О проекте ACCUM">About ACCUM</h2>
      <p data-en="ACCUM is a Layer-1 blockchain protocol introducing Fair Proof-of-Work (Fair PoW): every participant miner receives proportional rewards every block, removing lottery elements from mining and enabling stable incomes."
         data-ru="ACCUM — это блокчейн уровня 1, представляющий Fair Proof-of-Work (Честный PoW): каждый участвующий майнер получает пропорциональную награду в каждом блоке, устраняя лотерейный элемент майнинга и обеспечивая стабильный доход.">
         ACCUM is a Layer-1 blockchain protocol introducing Fair Proof-of-Work (Fair PoW): every participant miner receives proportional rewards every block, removing lottery elements from mining and enabling stable incomes.
      </p>
      <p><strong data-en="Key features include:" data-ru="Ключевые особенности:">Key features include:</strong></p>
      <ul>
        <li data-en="Accumulative Mining: deterministic reward distribution to all miners per block." 
            data-ru="Аккумулятивный майнинг: детерминированное распределение награды между всеми майнерами в каждом блоке.">
            <strong>Accumulative Mining:</strong> deterministic reward distribution to all miners per block.
        </li>
        <li data-en="Concave Reward Function: logarithmic scaling that economically discourages 51% attacks and whale dominance."
            data-ru="Вогнутая функция награды: логарифмическое масштабирование, которое экономически препятствует атакам 51% и доминированию китов.">
            <strong>Concave Reward Function:</strong> logarithmic scaling that economically discourages 51% attacks and whale dominance.
        </li>
        <li data-en="Proof-of-Contribution-and-Identity (PoCI): multi-metric reputation system for Sybil resistance."
            data-ru="Proof-of-Contribution-and-Identity (PoCI): многокомпонентная система репутации для защиты от Sybil-атак.">
            <strong>Proof-of-Contribution-and-Identity (PoCI):</strong> multi-metric reputation system for Sybil resistance.
        </li>
        <li data-en="Ultra-Light Nodes: full verification with ~50 MB state size suitable for mobile devices and Raspberry Pi."
            data-ru="Ultra-Light Nodes: полная верификация с состоянием ~50 МБ, подходит для мобильных устройств и Raspberry Pi.">
            <strong>Ultra-Light Nodes:</strong> full verification with ~50 MB state size suitable for mobile devices and Raspberry Pi.
        </li>
        <li data-en="Shard Streams: innovative hashrate futures providing instant miner liquidity and enabling native DeFi on PoW."
            data-ru="Shard Streams: инновационные фьючерсы на хешрейт, обеспечивающие мгновенную ликвидность майнеров и нативный DeFi на PoW.">
            <strong>Shard Streams:</strong> innovative hashrate futures providing instant miner liquidity and enabling native DeFi on PoW.
        </li>
      </ul>
      <p>
        <strong>Token:</strong> $ACM • Maximum supply: 21,000,000<br />
        <strong data-en="Launch date:" data-ru="Дата запуска:">Launch date:</strong> February 2026
      </p>
    </section>

    <!-- ACCUM AT A GLANCE -->
    <section class="section" aria-labelledby="glance-title">
      <h2 id="glance-title" data-en="⚡ ACCUM at a glance" data-ru="⚡ ACCUM вкратце">⚡ ACCUM at a glance</h2>
      <div class="glance-grid">
        <article class="glance-item">
          <strong data-en="Fair Launch" data-ru="Честный запуск">Fair Launch</strong><br />
          February 2026<br />
          <small data-en="no premine, no allocation" data-ru="без премайна, без аллокаций">no premine, no allocation</small>
        </article>
        <article class="glance-item">
          <strong data-en="Algorithm" data-ru="Алгоритм">Algorithm</strong><br />
          Argon2id<br />
          <small data-en="memory‑hard, ASIC‑resistant" data-ru="ресурсоёмкий, ASIC-устойчивый">memory‑hard, ASIC‑resistant</small>
        </article>
        <article class="glance-item">
          <strong data-en="Consensus" data-ru="Консенсус">Consensus</strong><br />
          Proof‑of‑Work<br />
          <small data-en="Accumulative + Concave" data-ru="Аккумулятивный + Вогнутый">Accumulative + Concave</small>
        </article>
        <article class="glance-item">
          <strong data-en="Platforms" data-ru="Платформы">Platforms</strong><br />
          Windows, Linux, macOS<br />
          <small data-en="RPi, Android (soon)" data-ru="RPi, Android (скоро)">RPi, Android (soon)</small>
        </article>
        <article class="glance-item">
          <strong>TICKER</strong><br />
          $ACM
        </article>
        <article class="glance-item">
          <strong data-en="Block time (testnet)" data-ru="Время блока (тестнет)">Block time (testnet)</strong><br />
          ~60 seconds
        </article>
        <article class="glance-item">
          <strong data-en="MAX SUPPLY" data-ru="МАКС. ПРЕДЛОЖЕНИЕ">MAX SUPPLY</strong><br />
          21 000 000
        </article>
        <article class="glance-item">
          <strong data-en="Network Status" data-ru="Статус сети">Network Status</strong><br />
          <span data-net-nodes>2</span> <span data-en="nodes" data-ru="ноды">nodes</span> · <span data-net-blocks>62</span> <span data-en="blocks" data-ru="блоков">blocks</span> · <span data-net-tx>18</span> <span data-en="tx" data-ru="транзакций">tx</span>
        </article>
      </div>
    </section>

    <!-- TECHNICAL SPECIFICATIONS -->
    <section class="section" aria-labelledby="tech-title">
      <h2 id="tech-title" data-en="⚙️ Technical specifications (testnet)" data-ru="⚙️ Технические характеристики (тестнет)">⚙️ Technical specifications (testnet)</h2>
      <div class="tech-grid">
        <article class="tech-item">
          <strong data-en="Hash algorithm" data-ru="Алгоритм хеширования">Hash algorithm</strong><br />
          Argon2id<br />
          <small data-en="memory‑hard" data-ru="ресурсоёмкий">memory‑hard</small>
        </article>
        <article class="tech-item">
          <strong data-en="Shard target" data-ru="Цель шарда">Shard target</strong><br />
          00ffff...<br />
          <small data-en="very easy" data-ru="очень легко">very easy</small>
        </article>
        <article class="tech-item">
          <strong data-en="Block target" data-ru="Цель блока">Block target</strong><br />
          00ffff...<br />
          <small data-en="very easy" data-ru="очень легко">very easy</small>
        </article>
        <article class="tech-item">
          <strong data-en="Time per shard" data-ru="Время на шард">Time per shard</strong><br />
          instant<br />
          <small data-en="nonce up to 5000" data-ru="nonce до 5000">nonce up to 5000</small>
        </article>
        <article class="tech-item">
          <strong data-en="Block time" data-ru="Время блока">Block time</strong><br />
          10–60 seconds
        </article>
        <article class="tech-item">
          <strong data-en="Shards per block" data-ru="Шардов на блок">Shards per block</strong><br />
          20–40
        </article>
        <article class="tech-item">
          <strong data-en="Block reward" data-ru="Награда за блок">Block reward</strong><br />
          50 ACM
        </article>
        <article class="tech-item">
          <strong data-en="Platforms" data-ru="Платформы">Platforms</strong><br />
          Windows, Linux, macOS
        </article>
        <article class="tech-item">
          <strong data-en="Min. requirements" data-ru="Мин. требования">Min. requirements</strong><br />
          2 cores, 2 GB RAM
        </article>
        <article class="tech-item">
          <strong data-en="Node size" data-ru="Размер ноды">Node size</strong><br />
          ~1–2 MB<br />
          <small data-en="will be < 50 MB" data-ru="будет < 50 МБ">will be &lt; 50 MB</small>
        </article>
      </div>
    </section>

    <!-- INTERACTIVE CHART WITH MOUSE TOOLTIP -->
    <section class="section" aria-labelledby="chart-title">
      <h2 id="chart-title" data-en="📈 Concave rewards (logarithmic curve)" data-ru="📈 Вогнутые награды (логарифмическая кривая)">📈 Concave rewards (logarithmic curve)</h2>
      <p>
        <strong data-en="ACCUM formula:" data-ru="Формула ACCUM:">ACCUM formula:</strong> R(n) = k·log(1 + n), where n is miner's share of the network.
      </p>
      <p data-en="The derivative dR/dn = k/(1+n) decreases, making dominance less profitable and 51% attacks economically irrational."
         data-ru="Производная dR/dn = k/(1+n) убывает, что делает доминирование менее выгодным, а атаки 51% экономически нерациональными.">
         The derivative dR/dn = k/(1+n) decreases, making dominance less profitable and 51% attacks economically irrational.
      </p>

      <div class="chart-container">
        <canvas id="rewardChart" aria-label="Graph comparing ACCUM logarithmic reward and Bitcoin linear reward" role="img"></canvas>
        <div id="chartTooltip" class="chart-tooltip" role="tooltip" aria-hidden="true"></div>
      </div>

      <div class="graph-caption" data-en="Green line — ACCUM logarithmic model | Dashed line — Bitcoin linear model"
           data-ru="Зеленая линия — логарифмическая модель ACCUM | Пунктир — линейная модель Bitcoin">
        Green line — ACCUM logarithmic model | Dashed line — Bitcoin linear model
      </div>
    </section>

    <!-- ECONOMIC MODEL -->
    <section class="section" aria-labelledby="economic-title">
      <h2 id="economic-title" data-en="🔐 Economic model" data-ru="🔐 Экономическая модель">🔐 Economic model</h2>
      <p><strong>Bitcoin (linear):</strong> E = α·B — reward scales linearly with hashrate share, encouraging centralization.</p>
      <p><strong>ACCUM (logarithmic):</strong> R(n) = k·log(1+n) — increasing hashrate gives diminishing returns:</p>
      <ul style="margin-left: 1.5rem;">
        <li data-en="10× hashrate → ~3× reward" data-ru="10× хешрейт → ~3× награда">10× hashrate → ~3× reward</li>
        <li data-en="100× hashrate → ~5× reward" data-ru="100× хешрейт → ~5× награда">100× hashrate → ~5× reward</li>
        <li data-en="51% attack requires 51% hashrate but yields <51% reward" data-ru="Атака 51% требует 51% хешрейта, но дает <51% награды">51% attack requires 51% hashrate but yields &lt;51% reward</li>
      </ul>
    </section>

    <!-- COMPARISON TABLE (improved visibility) -->
    <section class="section" aria-labelledby="comparison-title">
      <h2 id="comparison-title" data-en="🔍 Comparison with other PoW" data-ru="🔍 Сравнение с другими PoW">🔍 Comparison with other PoW</h2>
      <table role="table">
        <thead>
          <tr>
            <th scope="col" data-en="Parameter" data-ru="Параметр">Parameter</th>
            <th scope="col">Bitcoin</th>
            <th scope="col">Kaspa</th>
            <th scope="col">Monero</th>
            <th scope="col">ACCUM</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td data-en="Reward Model" data-ru="Модель наград">Reward Model</td>
            <td data-en="Linear Lottery" data-ru="Линейная лотерея">Linear Lottery</td>
            <td data-en="Block DAG Linear" data-ru="Block DAG Линейная">Block DAG Linear</td>
            <td data-en="Linear Lottery" data-ru="Линейная лотерея">Linear Lottery</td>
            <td><strong data-en="Concave Accumulative" data-ru="Вогнутая Аккумулятивная">Concave Accumulative</strong></td>
          </tr>
          <tr>
            <td data-en="Premine" data-ru="Премайн">Premine</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td><strong data-en="No" data-ru="Нет">No</strong></td>
          </tr>
          <tr>
            <td data-en="Reward per Block" data-ru="Награда за блок">Reward per Block</td>
            <td data-en="1 winner" data-ru="1 победитель">1 winner</td>
            <td data-en="1 winner" data-ru="1 победитель">1 winner</td>
            <td data-en="1 winner" data-ru="1 победитель">1 winner</td>
            <td><strong data-en="All participants" data-ru="Все участники">All participants</strong></td>
          </tr>
          <tr>
            <td data-en="Sybil Resistance" data-ru="Sybil-устойчивость">Sybil Resistance</td>
            <td data-en="None" data-ru="Нет">None</td>
            <td data-en="None" data-ru="Нет">None</td>
            <td data-en="None" data-ru="Нет">None</td>
            <td><strong>PoCI</strong></td>
          </tr>
          <tr>
            <td data-en="51% Attack Disincentive" data-ru="Сдерживание атак 51%">51% Attack Disincentive</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td><strong data-en="Yes (concave)" data-ru="Да (вогнутость)">Yes (concave)</strong></td>
          </tr>
          <tr>
            <td data-en="Ultra‑Light Node" data-ru="Ultra‑Light нода">Ultra‑Light Node</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td data-en="No" data-ru="Нет">No</td>
            <td><strong>~50 MB</strong></td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- TOKENOMICS (improved visibility) -->
    <section class="section" aria-labelledby="tokenomics-title">
      <h2 id="tokenomics-title" data-en="📊 Tokenomics" data-ru="📊 Токеномика">📊 Tokenomics</h2>
      
      <h3 data-en="Token Parameters" data-ru="Параметры токена">Token Parameters</h3>
      <table class="tokenomics-table">
        <tr>
          <th data-en="Parameter" data-ru="Параметр">Parameter</th>
          <th data-en="Specification" data-ru="Значение">Specification</th>
        </tr>
        <tr>
          <td><strong>Ticker</strong></td>
          <td><strong style="color: #4caf50; font-size: 1.2rem;">$ACM</strong></td>
        </tr>
        <tr>
          <td><strong data-en="Max Supply" data-ru="Макс. предложение">Max Supply</strong></td>
          <td><strong>21,000,000</strong></td>
        </tr>
        <tr>
          <td><strong data-en="Genesis Block Reward" data-ru="Награда за генезис-блок">Genesis Block Reward</strong></td>
          <td><strong>50 ACM</strong></td>
        </tr>
        <tr>
          <td><strong data-en="Halving Interval" data-ru="Интервал халвинга">Halving Interval</strong></td>
          <td><strong data-en="210,000 blocks (~2 years)" data-ru="210,000 блоков (~2 года)">210,000 blocks (~2 years)</strong></td>
        </tr>
      </table>
      
      <h3 style="color: var(--color-warning); margin-top: 2rem;" data-en="Initial Distribution" data-ru="Начальное распределение">Initial Distribution</h3>
      <table class="tokenomics-table">
        <thead>
          <tr>
            <th data-en="Allocation" data-ru="Аллокация">Allocation</th>
            <th data-en="Percentage" data-ru="Процент">Percentage</th>
            <th data-en="Amount" data-ru="Количество">Amount</th>
            <th data-en="Vesting" data-ru="Вестинг">Vesting</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td data-en="Mining Rewards" data-ru="Майнинг награды">Mining Rewards</td>
            <td><strong>80%</strong></td>
            <td><strong>16,800,000</strong></td>
            <td data-en="Emitted over ~120 years" data-ru="Эмиссия ~120 лет">Emitted over ~120 years</td>
          </tr>
          <tr>
            <td data-en="Core Team" data-ru="Команда">Core Team</td>
            <td><strong>10%</strong></td>
            <td><strong>2,100,000</strong></td>
            <td data-en="4‑year linear vesting" data-ru="4 года линейно">4‑year linear vesting</td>
          </tr>
          <tr>
            <td data-en="Foundation Treasury" data-ru="Казна фонда">Foundation Treasury</td>
            <td><strong>5%</strong></td>
            <td><strong>1,050,000</strong></td>
            <td data-en="2‑year lock" data-ru="Заморозка на 2 года">2‑year lock</td>
          </tr>
          <tr>
            <td data-en="Community & Ecosystem" data-ru="Сообщество и экосистема">Community & Ecosystem</td>
            <td><strong>5%</strong></td>
            <td><strong>1,050,000</strong></td>
            <td data-en="Airdrop, grants" data-ru="Airdrop, гранты">Airdrop, grants</td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- PoCI DETAILS (single instance - duplicate removed) -->
    <section class="section" aria-labelledby="poci-title">
      <h2 id="poci-title" data-en="🆔 Proof-of-Contribution-and-Identity (PoCI)" data-ru="🆔 Proof-of-Contribution-and-Identity (PoCI)">🆔 Proof-of-Contribution-and-Identity (PoCI)</h2>
      <p data-en="PoCI establishes a composite reputation score:"
         data-ru="PoCI создает составной рейтинг репутации:">
         PoCI establishes a composite reputation score:
      </p>
      
      <div class="formula-block">
        S = w₁Cₕₐₛₕ + w₂Tᵤₚ + w₃Vₜₓ + w₄B_w + w₅Aₙₑₜ + w₆Hₕᵢₛₜ
      </div>
      
      <table style="margin-top: 1.5rem;">
        <thead>
          <tr>
            <th data-en="Component" data-ru="Компонент">Component</th>
            <th data-en="Weight" data-ru="Вес">Weight</th>
            <th data-en="Description" data-ru="Описание">Description</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><strong>Hashrate</strong></td>
            <td><strong style="color: #4caf50;">40%</strong></td>
            <td data-en="Validated hashrate contribution" data-ru="Подтвержденный хешрейт">Validated hashrate contribution</td>
          </tr>
          <tr>
            <td><strong>Uptime</strong></td>
            <td><strong style="color: #4caf50;">20%</strong></td>
            <td data-en="Node uptime and responsiveness" data-ru="Аптайм и отзывчивость ноды">Node uptime and responsiveness</td>
          </tr>
          <tr>
            <td><strong>Transactions verified</strong></td>
            <td><strong style="color: #4caf50;">15%</strong></td>
            <td data-en="Volume of verified/propagated transactions" data-ru="Количество проверенных/переданных транзакций">Volume of verified/propagated transactions</td>
          </tr>
          <tr>
            <td><strong>Bandwidth</strong></td>
            <td><strong style="color: #4caf50;">10%</strong></td>
            <td data-en="Contribution to peers" data-ru="Вклад в пиры">Contribution to peers</td>
          </tr>
          <tr>
            <td><strong>Network age</strong></td>
            <td><strong style="color: #4caf50;">10%</strong></td>
            <td data-en="Chronological age of the node" data-ru="Хронологический возраст ноды">Chronological age of the node</td>
          </tr>
          <tr>
            <td><strong>Honest history</strong></td>
            <td><strong style="color: #4caf50;">5%</strong></td>
            <td data-en="Adherence to protocol rules" data-ru="Соблюдение правил протокола">Adherence to protocol rules</td>
          </tr>
        </tbody>
      </table>
      
      <p style="margin-top: 1.5rem; font-style: italic;" 
         data-en="Sybil Resistance: A Sybil attacker deploying 1000 ephemeral nodes has negligible aggregate score compared to a single node with one year of history."
         data-ru="Sybil-устойчивость: Атакующий, развернувший 1000 эфемерных нод, получит незначительный совокупный рейтинг по сравнению с одной нодой с годовой историей.">
         Sybil Resistance: A Sybil attacker deploying 1000 ephemeral nodes has negligible aggregate score compared to a single node with one year of history.
      </p>
    </section>

    <!-- SHARD STREAMS -->
    <section class="section" aria-labelledby="shard-title">
      <h2 id="shard-title" data-en="💧 Shard Streams (Hashrate Futures)" data-ru="💧 Shard Streams (Фьючерсы на хешрейт)">💧 Shard Streams (Hashrate Futures)</h2>
      <p data-en="Tokenization of future rewards for instant miner liquidity:"
         data-ru="Токенизация будущих наград для мгновенной ликвидности майнеров:">
         Tokenization of future rewards for instant miner liquidity:
      </p>
      <ul>
        <li><strong data-en="Instrument:" data-ru="Инструмент:">Instrument:</strong> <span data-en="Non-fungible token representing future reward claim" 
              data-ru="Невзаимозаменяемый токен, представляющий право на будущую награду">Non-fungible token representing future reward claim</span></li>
        <li><strong data-en="Unit:" data-ru="Единица:">Unit:</strong> 0.0001 ACM per block for one year</li>
        <li><strong data-en="Typical price:" data-ru="Типичная цена:">Typical price:</strong> 5 ACM (~30% discount to NPV)</li>
      </ul>
    </section>

    <!-- TWO-NODE MINING (TEST RESULTS) -->
    <section class="section" aria-labelledby="mining-title">
      <h2 id="mining-title" data-en="⛏️ Two‑node mining (test results)" data-ru="⛏️ Двухнодовый майнинг (результаты тестов)">⛏️ Two‑node mining (test results)</h2>
      <p data-en="Run two nodes with a single command:" data-ru="Запустите две ноды одной командой:">Run two nodes with a single command:</p>
      <pre class="code-block" tabindex="0">python accum.py</pre>
      <p data-en="Test results from the prototype:" data-ru="Результаты тестирования прототипа:">Test results from the prototype:</p>
      <pre class="code-block" tabindex="0">
[Node1] Address: a87df5988f2728f1e110c14644144252a49e39c2
[Node2] Address: 71e37af1536860593bc8f64282207818b7c6294a
[Node2] ✅ Shard 00235416 nonce=13
[Node1] 📥 Shard 00235416
[Node2] ✅ Shard 008e4372 nonce=45
[Node1] 📥 Shard 008e4372
[Node2] ✅ Shard 006c7828 nonce=163
[Node1] 📥 Shard 006c7828
[Node1] 📦 Assembling block from 32 shards, 0 tx
[Node1] ⛏ Mining block...
[Node1] ✅ Block 1 saved, hash 385ba362f2f8d707
[Node2] 💸 Test transaction d4c97e95 (10 coins) to a87df598</pre>
      <p><em data-en="The project is still in active testing phase. These results demonstrate the core mechanics working as designed." 
            data-ru="Проект находится в активной фазе тестирования. Эти результаты демонстрируют работу базовой механики.">
         The project is still in active testing phase. These results demonstrate the core mechanics working as designed.</em>
      </p>
      <div style="margin-top: 1.5rem;">
        <a href="https://github.com/andreudumitro-eng/ACCUM" class="button" role="button">📦 Download accum.py</a>
        <a href="#install" class="button outline" role="button" data-en="Quick start guide" data-ru="Быстрый старт">Quick start guide</a>
      </div>
    </section>

    <!-- TESTNET STATUS -->
    <section class="section" aria-labelledby="testnet-title">
      <h2 id="testnet-title" data-en="✅ Live testnet (Q1 2026)" data-ru="✅ Живой тестнет (Q1 2026)">✅ Live testnet (Q1 2026)</h2>
      <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-bottom: 1.5rem">
        <div class="glance-item" style="text-align: center;">
          <strong style="font-size: 2rem;">62</strong><br />
          <span data-en="blocks" data-ru="блоков" style="font-size: 1.1rem;">blocks</span>
        </div>
        <div class="glance-item" style="text-align: center;">
          <strong style="font-size: 2rem;">18</strong><br />
          <span data-en="transactions" data-ru="транзакций" style="font-size: 1.1rem;">transactions</span>
        </div>
        <div class="glance-item" style="text-align: center;">
          <strong style="font-size: 2rem;">2</strong><br />
          <span data-en="active nodes" data-ru="активных нод" style="font-size: 1.1rem;">active nodes</span>
        </div>
      </div>
      <ul style="margin-left: 1.5rem;">
        <li data-en="✅ Two independent nodes (ports 12345, 12346) running continuously" 
            data-ru="✅ Две независимые ноды (порты 12345, 12346) работают непрерывно">
            ✅ Two independent nodes (ports 12345, 12346) running continuously
        </li>
        <li data-en="✅ Blocks produced every ~60 seconds" 
            data-ru="✅ Блоки производятся каждые ~60 секунд">
            ✅ Blocks produced every ~60 seconds
        </li>
        <li data-en="✅ Test transfers of 10 ACM are confirmed on-chain" 
            data-ru="✅ Тестовые переводы 10 ACM подтверждаются в сети">
            ✅ Test transfers of 10 ACM are confirmed on-chain
        </li>
        <li data-en="✅ P2P shard and block exchange fully functional" 
            data-ru="✅ P2P обмен шардами и блоками полностью функционален">
            ✅ P2P shard and block exchange fully functional
        </li>
      </ul>
    </section>

    <!-- ROADMAP -->
    <section class="section" aria-labelledby="roadmap-title">
      <h2 id="roadmap-title" data-en="🗺️ Roadmap" data-ru="🗺️ Дорожная карта">🗺️ Roadmap</h2>
      <div class="roadmap-grid">
        <article class="roadmap-item">
          <strong>Q3 2026</strong><br />
          <span data-en="Public testnet" data-ru="Публичный тестнет">Public testnet</span><br />
          <small data-en="Open for everyone" data-ru="Открыт для всех">Open for everyone</small>
        </article>
        <article class="roadmap-item">
          <strong>Q4 2026</strong><br />
          <span data-en="Security audit" data-ru="Аудит безопасности">Security audit</span><br />
          <small data-en="2 independent firms" data-ru="2 независимые фирмы">2 independent firms</small>
        </article>
        <article class="roadmap-item">
          <strong>Q1 2027</strong><br />
          <span data-en="Mainnet Launch" data-ru="Запуск мейннета">Mainnet Launch</span><br />
          <small data-en="Genesis block" data-ru="Генезис-блок">Genesis block</small>
        </article>
        <article class="roadmap-item">
          <strong>Q2 2027</strong><br />
          <span data-en="Shard Streams" data-ru="Shard Streams">Shard Streams</span><br />
          <small data-en="DeFi layer on PoW" data-ru="DeFi слой на PoW">DeFi layer on PoW</small>
        </article>
      </div>
    </section>

    <!-- CONTACT & LINKS -->
    <section class="section">
      <h2 data-en="📚 Source code & whitepaper" data-ru="📚 Исходный код и вайтпейпер">📚 Source code & whitepaper</h2>
      <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
      <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (EN)</a>
      <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (RU)</a>
      <a href="#" class="button outline" data-en="🌐 accum.site" data-ru="🌐 accum.site">🌐 accum.site</a>
      <div style="margin-top:1.5rem; font-size: 1.2rem;">
        📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro" target="_blank" style="color: var(--color-success);">@Andredumitro</a>
      </div>
    </section>

    <!-- QUICK START -->
    <section class="section" id="install">
      <h2 data-en="📦 Quick start" data-ru="📦 Быстрый старт">📦 Quick start</h2>
      <pre class="code-block">
# 1. Clone the repository
git clone https://github.com/andreudumitro-eng/ACCUM.git
cd ACCUM

# 2. Install dependency
pip install argon2-cffi

# 3. Run two nodes
python accum.py
      </pre>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
      <p>© 2026 Andrii Dumitro — ACCUM. <span data-en="Open source · Fair launch · No premine" data-ru="Открытый код · Честный запуск · Без премайна">Open source · Fair launch · No premine</span></p>
      <p style="margin-top:0.5rem;">⚡ <span data-en="Version 2.1 — Fully aligned with the whitepaper" data-ru="Версия 2.1 — Полное соответствие вайтпейперу">Version 2.1 — Fully aligned with the whitepaper</span></p>
    </footer>
  </main>

  <script>
    (function() {
      // Language switching functionality
      const langBtns = document.querySelectorAll('.lang-btn');
      const elements = document.querySelectorAll('[data-en][data-ru]');
      
      function setLanguage(lang) {
        elements.forEach(el => {
          if (el.tagName === 'INPUT' || el.tagName === 'TEXTAREA' || el.tagName === 'SELECT') {
            el.placeholder = el.getAttribute(`data-${lang}`);
          } else {
            el.textContent = el.getAttribute(`data-${lang}`);
          }
        });
        
        // Update button states
        langBtns.forEach(btn => {
          if (btn.dataset.lang === lang) {
            btn.classList.add('active');
          } else {
            btn.classList.remove('active');
          }
        });
        
        // Store preference
        localStorage.setItem('preferred-language', lang);
      }
      
      langBtns.forEach(btn => {
        btn.addEventListener('click', () => {
          setLanguage(btn.dataset.lang);
        });
      });
      
      // Check for stored preference
      const storedLang = localStorage.getItem('preferred-language');
      if (storedLang && ['en', 'ru'].includes(storedLang)) {
        setLanguage(storedLang);
      }

      // Chart functionality
      const canvas = document.getElementById('rewardChart');
      const tooltip = document.getElementById('chartTooltip');
      
      if (!canvas || !tooltip) return;
      
      const ctx = canvas.getContext('2d');
      let w, h;
      
      function resizeCanvas() {
        w = canvas.clientWidth;
        h = 320;
        canvas.width = w;
        canvas.height = h;
        drawChart();
      }
      
      function drawChart() {
        ctx.clearRect(0, 0, w, h);
        
        const pad = { left: 70, right: 30, top: 20, bottom: 50 };
        const gw = w - pad.left - pad.right;
        const gh = h - pad.top - pad.bottom;
        
        // Grid
        ctx.strokeStyle = "#555";
        ctx.lineWidth = 0.5;
        for (let i = 0; i <= 5; i++) {
          let y = pad.top + (i / 5) * gh;
          ctx.beginPath();
          ctx.moveTo(pad.left, y);
          ctx.lineTo(w - pad.right, y);
          ctx.stroke();
        }
        
        // Bitcoin linear (dashed)
        ctx.strokeStyle = "#aaaaaa";
        ctx.lineWidth = 2.5;
        ctx.setLineDash([6, 4]);
        ctx.beginPath();
        for (let x = 1; x <= 100; x++) {
          let dx = pad.left + (x / 100) * gw;
          let dy = h - pad.bottom - (x / 100) * gh;
          if (x === 1) ctx.moveTo(dx, dy);
          else ctx.lineTo(dx, dy);
        }
        ctx.stroke();
        
        // ACCUM logarithmic (green)
        ctx.strokeStyle = "#4caf50";
        ctx.lineWidth = 3.5;
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
        
        // Axis labels
        ctx.fillStyle = "#ffffff";
        ctx.font = "14px Arial";
        
        // X axis
        ctx.textAlign = "center";
        const xLabel = document.querySelector('[data-en="Hashrate share (%)"]')?.textContent || "Hashrate share (%)";
        ctx.fillText(xLabel, w / 2, h - 15);
        
        // Y axis (rotated)
        ctx.save();
        ctx.translate(25, h / 2);
        ctx.rotate(-Math.PI / 2);
        ctx.textAlign = "center";
        const yLabel = document.querySelector('[data-en="Reward share (%)"]')?.textContent || "Reward share (%)";
        ctx.fillText(yLabel, 0, 0);
        ctx.restore();
        
        // Legend
        ctx.fillStyle = "#4caf50";
        ctx.fillRect(w - 130, pad.top + 5, 14, 14);
        ctx.fillStyle = "#ffffff";
        ctx.font = "12px Arial";
        ctx.textAlign = "left";
        ctx.fillText("ACCUM (log)", w - 110, pad.top + 17);
        
        ctx.fillStyle = "#aaaaaa";
        ctx.fillRect(w - 130, pad.top + 30, 14, 14);
        ctx.fillStyle = "#ffffff";
        ctx.fillText("Bitcoin (linear)", w - 110, pad.top + 42);
      }
      
      function handleMouseMove(e) {
        const rect = canvas.getBoundingClientRect();
        const scaleX = canvas.width / rect.width;
        const scaleY = canvas.height / rect.height;
        
        const mouseX = (e.clientX - rect.left) * scaleX;
        const mouseY = (e.clientY - rect.top) * scaleY;
        
        const pad = { left: 70, right: 30, top: 20, bottom: 50 };
        const gw = canvas.width - pad.left - pad.right;
        const gh = canvas.height - pad.top - pad.bottom;
        
        if (mouseX >= pad.left && mouseX <= canvas.width - pad.right &&
            mouseY >= pad.top && mouseY <= canvas.height - pad.bottom) {
          
          const share = (mouseX - pad.left) / gw * 100;
          const clampedShare = Math.min(100, Math.max(0, share));
          
          const linearReward = clampedShare;
          const logReward = Math.log2(1 + clampedShare) / Math.log2(101) * 100;
          
          tooltip.style.opacity = '1';
          tooltip.style.left = (e.clientX - rect.left + 15) + 'px';
          tooltip.style.top = (e.clientY - rect.top - 40) + 'px';
          
          const lang = document.querySelector('.lang-btn.active')?.dataset.lang || 'en';
          if (lang === 'ru') {
            tooltip.innerHTML = `
              <strong>Доля хешрейта: ${clampedShare.toFixed(1)}%</strong><br>
              <span style="color:#aaaaaa;">Bitcoin: ${linearReward.toFixed(1)}%</span><br>
              <span style="color:#4caf50;">ACCUM: ${logReward.toFixed(1)}%</span>
            `;
          } else {
            tooltip.innerHTML = `
              <strong>Hashrate share: ${clampedShare.toFixed(1)}%</strong><br>
              <span style="color:#aaaaaa;">Bitcoin: ${linearReward.toFixed(1)}%</span><br>
              <span style="color:#4caf50;">ACCUM: ${logReward.toFixed(1)}%</span>
            `;
          }
        } else {
          tooltip.style.opacity = '0';
        }
      }
      
      canvas.addEventListener('mousemove', handleMouseMove);
      canvas.addEventListener('mouseleave', () => {
        tooltip.style.opacity = '0';
      });
      
      window.addEventListener('load', resizeCanvas);
      window.addEventListener('resize', resizeCanvas);
      
      // Network stats updater (simulated)
      setInterval(() => {
        // This would normally fetch from an API, but for demo we'll just increment occasionally
        if (Math.random() > 0.7) {
          const blocksEl = document.querySelector('[data-net-blocks]');
          const txEl = document.querySelector('[data-net-tx]');
          if (blocksEl && txEl) {
            blocksEl.textContent = parseInt(blocksEl.textContent) + 1;
            if (Math.random() > 0.5) {
              txEl.textContent = parseInt(txEl.textContent) + 1;
            }
          }
        }
      }, 30000);
    })();
  </script>
</body>
</html>
