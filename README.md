<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>ACCUM — The First Fair Proof-of-Work Blockchain</title>
  <style>
    :root {
      --color-primary-dark: #0d1b2a;
      --color-primary: #1b263b;
      --color-primary-light: #415a77;
      --color-secondary: #778da9;
      --color-accent: #e0e1dd;
      --color-success: #4caf50;
      --color-warning: #ffb300;
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
      justify-content: center;
      align-items: center;
      padding: 1rem 0;
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

    h2 {
      color: var(--color-success);
      font-size: 2.2rem;
      margin-bottom: 1.5rem;
      border-left: 6px solid var(--color-success);
      padding-left: 1rem;
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
    }

    .hero .sublead {
      font-size: 1.3rem;
      max-width: 800px;
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
    .roadmap-grid,
    .contribute-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1.8rem;
      margin-top: 1.5rem;
    }

    .glance-item,
    .tech-item,
    .feature-card,
    .roadmap-item,
    .contribute-item {
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

    table {
      width: 100%;
      border-collapse: collapse;
      background: var(--color-primary);
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 6px 20px rgba(0, 40, 80, 0.3);
      color: var(--color-accent);
    }

    th,
    td {
      padding: 1rem 1.3rem;
      text-align: left;
      border-bottom: 1px solid var(--color-primary-light);
    }

    th {
      background: var(--color-primary-light);
      font-weight: 700;
    }

    tr:last-child td {
      border-bottom: none;
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
      .roadmap-grid,
      .contribute-grid {
        grid-template-columns: 1fr;
      }

      header.site-header {
        padding: 0.75rem 0;
      }

      .logo {
        font-size: 2.4rem;
      }
    }
  </style>
</head>
<body>
  <header class="site-header" role="banner">
    <div class="logo" aria-label="ACCUM logo">⚡ ACCUM</div>
  </header>

  <main class="container" role="main">
    <!-- HERO SECTION -->
    <section class="hero" aria-labelledby="hero-title">
      <h1 id="hero-title">Fair Proof-of-Work</h1>
      <p class="lead">Bitcoin is a lottery. ACCUM is a salary.</p>
      <p class="sublead">
        Every miner gets paid every block. No more winners and losers — just fair,
        predictable rewards.
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
      <h2 id="about-title">About ACCUM</h2>
      <p>
        ACCUM is a Layer-1 blockchain protocol introducing <strong>Fair Proof-of-Work (Fair PoW)</strong>: every participant miner receives proportional rewards every block, removing lottery elements from mining and enabling stable incomes.
      </p>
      <p><strong>Key features include:</strong></p>
      <ul>
        <li><strong>Accumulative Mining:</strong> deterministic reward distribution to all miners per block.</li>
        <li><strong>Concave Reward Function:</strong> logarithmic scaling that economically discourages 51% attacks and whale dominance.</li>
        <li><strong>Proof-of-Contribution-and-Identity (PoCI):</strong> multi-metric reputation system for Sybil resistance.</li>
        <li><strong>Ultra-Light Nodes:</strong> full verification with ~50 MB state size suitable for mobile devices and Raspberry Pi.</li>
        <li><strong>Shard Streams:</strong> innovative hashrate futures providing instant miner liquidity and enabling native DeFi on PoW.</li>
      </ul>
      <p><strong>Token:</strong> $ACM • Maximum supply: 21,000,000<br />
      <strong>Launch date:</strong> February 2026 • <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.1.md" target="_blank" class="button outline" style="font-size:1rem; padding:0.6rem 1.2rem; border-radius:16px;">Read Whitepaper</a></p>
    </section>

    <!-- ACCUM AT A GLANCE -->
    <section class="section" aria-labelledby="glance-title">
      <h2 id="glance-title">⚡ ACCUM at a glance</h2>
      <div class="glance-grid">
        <article class="glance-item">
          <strong>Fair Launch</strong><br />
          February 2026<br />
          <small>no premine, no allocation</small>
        </article>
        <article class="glance-item">
          <strong>Algorithm</strong><br />
          Argon2id<br />
          <small>memory‑hard, ASIC‑resistant</small>
        </article>
        <article class="glance-item">
          <strong>Consensus</strong><br />
          Proof‑of‑Work<br />
          <small>Accumulative + Concave</small>
        </article>
        <article class="glance-item">
          <strong>Platforms</strong><br />
          Windows, Linux, macOS<br />
          <small>RPi, Android (soon)</small>
        </article>
        <article class="glance-item">
          <strong>TICKER</strong><br />
          $ACM
        </article>
        <article class="glance-item">
          <strong>Block time (testnet)</strong><br />
          ~60 seconds
        </article>
        <article class="glance-item">
          <strong>MAX SUPPLY</strong><br />
          21 000 000
        </article>
        <article class="glance-item">
          <strong>Network Status</strong><br />
          2 nodes · 62 blocks · 18 tx
        </article>
      </div>
    </section>

    <!-- TECHNICAL SPECIFICATIONS -->
    <section class="section" aria-labelledby="tech-title">
      <h2 id="tech-title">⚙️ Technical specifications (testnet)</h2>
      <div class="tech-grid">
        <article class="tech-item">
          <strong>Hash algorithm</strong><br />
          Argon2id<br />
          <small>memory‑hard</small>
        </article>
        <article class="tech-item">
          <strong>Shard target</strong><br />
          00ffff...<br />
          <small>very easy</small>
        </article>
        <article class="tech-item">
          <strong>Block target</strong><br />
          00ffff...<br />
          <small>very easy</small>
        </article>
        <article class="tech-item">
          <strong>Time per shard</strong><br />
          instant<br />
          <small>nonce up to 5000</small>
        </article>
        <article class="tech-item">
          <strong>Block time</strong><br />
          10–60 seconds
        </article>
        <article class="tech-item">
          <strong>Shards per block</strong><br />
          20–40
        </article>
        <article class="tech-item">
          <strong>Block reward</strong><br />
          50 ACM
        </article>
        <article class="tech-item">
          <strong>Platforms</strong><br />
          Windows, Linux, macOS
        </article>
        <article class="tech-item">
          <strong>Min. requirements</strong><br />
          2 cores, 2 GB RAM
        </article>
        <article class="tech-item">
          <strong>Node size</strong><br />
          ~1–2 MB<br />
          <small>will be &lt; 50 MB</small>
        </article>
      </div>
    </section>

    <!-- INTERACTIVE CHART WITH MOUSE TOOLTIP -->
    <section class="section" aria-labelledby="chart-title">
      <h2 id="chart-title">📈 Concave rewards (logarithmic curve)</h2>
      <p>
        <strong>ACCUM formula:</strong> R(n) = k · log(1 + n), where n is miner's share of the network.
      </p>
      <p>
        The derivative dR/dn = k/(1+n) decreases, making dominance less profitable and 51%
        attacks economically irrational.
      </p>

      <div class="chart-container">
        <canvas id="rewardChart" aria-label="Graph comparing ACCUM logarithmic reward and Bitcoin linear reward" role="img"></canvas>
        <div id="chartTooltip" class="chart-tooltip" role="tooltip" aria-hidden="true"></div>
      </div>

      <div class="graph-caption">
        Green line — ACCUM logarithmic model | Dashed line — Bitcoin linear model
      </div>
    </section>

    <!-- 5 CORE INNOVATIONS -->
    <section class="section" aria-labelledby="innovations-title">
      <h2 id="innovations-title">🔷 5 core innovations</h2>
      <div class="features-grid">
        <article class="feature-card" tabindex="0">
          <h3>⛏️ Accumulative Mining</h3>
          <p>Every miner receives a reward for every block. No lottery — stable income for all participants.</p>
        </article>
        <article class="feature-card" tabindex="0">
          <h3>📉 Concave Rewards</h3>
          <p>Logarithmic reward curve makes 51% attacks economically unprofitable.</p>
        </article>
        <article class="feature-card" tabindex="0">
          <h3>🆔 PoCI</h3>
          <p>
            Proof-of-Contribution-and-Identity — multi‑metric reputation (uptime, age,
            verification) for Sybil resistance.
          </p>
        </article>
        <article class="feature-card" tabindex="0">
          <h3>💧 Shard Streams</h3>
          <p>Hashrate futures for instant miner liquidity. Native DeFi layer on PoW.</p>
        </article>
        <article class="feature-card" tabindex="0">
          <h3>📱 Ultra‑Light Nodes</h3>
          <p>Full verification with ~50 MB state. Runs on mobile phones and Raspberry Pi.</p>
        </article>
      </div>
    </section>

    <!-- TWO-NODE MINING (LIVE LOGS) -->
    <section class="section" aria-labelledby="mining-title">
      <h2 id="mining-title">⛏️ Two‑node mining (live testnet)</h2>
      <p>Run two nodes with a single command:</p>
      <pre class="code-block" tabindex="0">python accum.py</pre>
      <p>Live output from the testnet:</p>
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
[Node2] 💸 Test transaction d4c97e95 (10 coins) to a87df598
      </pre>
      <div style="margin-top: 1.5rem;">
        <a href="https://github.com/andreudumitro-eng/ACCUM" class="button" role="button">📦 Download accum.py</a>
        <a href="#install" class="button outline" role="button">Quick start guide</a>
      </div>
    </section>

    <!-- TESTNET STATUS -->
    <section class="section" aria-labelledby="testnet-title">
      <h2 id="testnet-title">✅ Live testnet (Q1 2026)</h2>
      <div
        style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem; margin-bottom: 1.5rem"
      >
        <div class="glance-item">
          <strong>62</strong><br />
          blocks
        </div>
        <div class="glance-item">
          <strong>18</strong><br />
          transactions
        </div>
        <div class="glance-item">
          <strong>2</strong><br />
          active nodes
        </div>
      </div>
      <ul style="margin-left: 1.5rem;">
        <li>✅ Two independent nodes (ports 12345, 12346) running continuously</li>
        <li>✅ Blocks produced every ~60 seconds</li>
        <li>✅ Test transfers of 10 ACM are confirmed on-chain</li>
        <li>✅ P2P shard and block exchange fully functional</li>
        <li>✅ Logs and demo available upon request</li>
      </ul>
    </section>

    <!-- COMPARISON TABLE -->
    <section class="section" aria-labelledby="comparison-title">
      <h2 id="comparison-title">🔍 Comparison with other PoW</h2>
      <table role="table" aria-describedby="comparison-description">
        <caption id="comparison-description" class="visually-hidden" style="display:none;">
          Comparison of reward models, premine, sybil resistance, and node size across Bitcoin,
          Kaspa, Monero, and ACCUM.
        </caption>
        <thead>
          <tr>
            <th scope="col">Parameter</th>
            <th scope="col">Bitcoin</th>
            <th scope="col">Kaspa</th>
            <th scope="col">Monero</th>
            <th scope="col">ACCUM</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Reward Model</td>
            <td>Linear Lottery</td>
            <td>Block DAG Linear</td>
            <td>Linear Lottery</td>
            <td><strong>Concave Accumulative</strong></td>
          </tr>
          <tr>
            <td>Premine</td>
            <td>No</td>
            <td>No</td>
            <td>No</td>
            <td><strong>No</strong></td>
          </tr>
          <tr>
            <td>Reward per Block</td>
            <td>1 winner</td>
            <td>1 winner</td>
            <td>1 winner</td>
            <td><strong>All participants</strong></td>
          </tr>
          <tr>
            <td>Sybil Resistance</td>
            <td>None</td>
            <td>None</td>
            <td>None</td>
            <td><strong>PoCI</strong></td>
          </tr>
          <tr>
            <td>51% Attack Disincentive</td>
            <td>No</td>
            <td>No</td>
            <td>No</td>
            <td><strong>Yes (concave)</strong></td>
          </tr>
          <tr>
            <td>Ultra‑Light Node</td>
            <td>No</td>
            <td>No</td>
            <td>No</td>
            <td><strong>~50 MB</strong></td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- ECONOMIC MODEL -->
    <section class="section" aria-labelledby="economic-title">
      <h2 id="economic-title">🔐 Economic model</h2>
      <p><strong>Bitcoin (linear):</strong> E = α·B — reward scales linearly with hashrate share, encouraging centralization.</p>
      <p><strong>ACCUM (logarithmic):</strong> R(n) = k·log(1+n) — increasing hashrate gives diminishing returns:</p>
      <ul style="margin-left: 1.5rem;">
        <li>10× hashrate → ~3× reward</li>
        <li>100× hashrate → ~5× reward</li>
        <li>51% attack requires 51% hashrate but yields &lt;51% reward</li>
      </ul>
    </section>

    <!-- ROADMAP -->
    <section class="section" aria-labelledby="roadmap-title">
      <h2 id="roadmap-title">🗺️ Roadmap</h2>
      <div class="roadmap-grid">
        <article class="roadmap-item">
          <strong>Q3 2026</strong><br />
          Public testnet<br />
          <small>Open for everyone</small>
        </article>
        <article class="roadmap-item">
          <strong>Q4 2026</strong><br />
          Security audit<br />
          <small>2 independent firms</small>
        </article>
        <article class="roadmap-item">
          <strong>Q1 2027</strong><br />
          Mainnet Launch<br />
          <small>Genesis block</small>
        </article>
        <article class="roadmap-item">
          <strong>Q2 2027</strong><br />
          Shard Streams<br />
          <small>DeFi layer on PoW</small>
        </article>
      </div>
    </section>

    <!-- CONTRIBUTE -->
    <section class="section">
      <h2>🧑‍💻 Contribute</h2>
      <p>ACCUM is a community project. Join us!</p>
      <div class="contribute-grid">
        <div class="contribute-item"><strong>🦀 Rust developers</strong><br />Core protocol, P2P, consensus</div>
        <div class="contribute-item"><strong>🐍 Python testers</strong><br />Testnet, bug hunting, optimization</div>
        <div class="contribute-item"><strong>📝 Documentation</strong><br />Translations, guides, articles</div>
      </div>
      <a href="https://github.com/andreudumitro-eng/ACCUM/issues" class="button">📌 GitHub Issues</a>
    </section>

    <!-- CONTACT & LINKS -->
    <section class="section">
      <h2>📚 Source code & whitepaper</h2>
      <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
      <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (EN)</a>
      <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (RU)</a>
      <div style="margin-top:1.5rem;">
        📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro" target="_blank">@Andredumitro</a>
      </div>
    </section>

    <!-- QUICK START -->
    <section class="section" id="install">
      <h2>📦 Quick start</h2>
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
      <p>© 2026 Andrii Dumitro — ACCUM. Open source · Fair launch · No premine</p>
      <p style="margin-top:0.5rem;">⚡ Version 2.1 — Fully aligned with the whitepaper</p>
    </footer>
  </main>

  <!-- CHART WITH INTERACTIVE TOOLTIP -->
  <script>
    (function() {
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
            
            const pad = { left: 60, right: 20, top: 20, bottom: 30 };
            const gw = w - pad.left - pad.right;
            const gh = h - pad.top - pad.bottom;
            
            ctx.strokeStyle = "#ccc";
            ctx.lineWidth = 0.5;
            for (let i = 0; i <= 5; i++) {
                let y = pad.top + (i / 5) * gh;
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
                let dx = pad.left + (x / 100) * gw;
                let dy = h - pad.bottom - (x / 100) * gh;
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
                let dx = pad.left + (x / 100) * gw;
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
        
        function handleMouseMove(e) {
            const rect = canvas.getBoundingClientRect();
            const scaleX = canvas.width / rect.width;
            const scaleY = canvas.height / rect.height;
            
            const mouseX = (e.clientX - rect.left) * scaleX;
            const mouseY = (e.clientY - rect.top) * scaleY;
            
            const pad = { left: 60, right: 20, top: 20, bottom: 30 };
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
                tooltip.innerHTML = `
                    <strong>Hashrate share: ${clampedShare.toFixed(1)}%</strong><br>
                    Bitcoin reward: ${linearReward.toFixed(1)}%<br>
                    ACCUM reward: ${logReward.toFixed(1)}%
                `;
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
    })();
  </script>
</body>
</html>
