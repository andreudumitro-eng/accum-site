<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ACCUM — The First Fair Proof-of-Work Blockchain</title>
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

        /* Smaller header */
        .site-header {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 0.8rem 0;
            margin-bottom: 2rem;
            border-bottom: 1px solid rgba(46,125,50,0.2);
        }

        .logo {
            font-size: 2.2rem;
            font-weight: 700;
            background: linear-gradient(135deg, #2e7d32, #1b5e20);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -0.5px;
        }

        h2 {
            color: #2e7d32;
            font-size: 2rem;
            margin-bottom: 1.5rem;
            border-left: 6px solid #2e7d32;
            padding-left: 1rem;
        }

        /* HERO SECTION */
        .hero {
            background: linear-gradient(135deg, #1b3b1f 0%, #2e7d32 100%);
            color: white;
            padding: 2.5rem 2rem;
            border-radius: 32px;
            margin-bottom: 2rem;
            box-shadow: 0 20px 40px rgba(46,125,50,0.25);
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 0.8rem;
            text-shadow: 0 2px 5px rgba(0,0,0,0.15);
        }

        .hero .lead {
            font-size: 1.6rem;
            font-weight: 300;
            margin-bottom: 1rem;
        }

        .hero .sublead {
            font-size: 1.2rem;
            max-width: 800px;
            opacity: 0.95;
        }

        .hero-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.2rem;
            margin-top: 2rem;
        }

        .hero-item {
            background: rgba(255,255,255,0.12);
            border-radius: 20px;
            padding: 1.2rem;
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

        /* Sections */
        .section {
            background: rgba(255,255,255,0.85);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(46,125,50,0.15);
            border-radius: 24px;
            padding: 2rem;
            margin: 2rem 0;
            box-shadow: 0 8px 30px rgba(0,20,10,0.06);
        }

        /* Cards grid */
        .glance-grid,
        .tech-grid,
        .features-grid,
        .roadmap-grid,
        .contribute-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            margin-top: 1rem;
        }

        .glance-item,
        .tech-item,
        .feature-card,
        .roadmap-item,
        .contribute-item {
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

        /* Chart with tooltip */
        .chart-container {
            position: relative;
            margin: 2rem 0;
        }

        canvas {
            width: 100%;
            height: 320px;
            background: #ffffff;
            border-radius: 20px;
            padding: 1rem;
            box-shadow: inset 0 2px 8px rgba(0,0,0,0.02);
            display: block;
        }

        .chart-tooltip {
            position: absolute;
            background: #1e293b;
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 8px;
            font-size: 0.9rem;
            pointer-events: none;
            border: 1px solid #2e7d32;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
            z-index: 100;
            transition: opacity 0.1s;
            opacity: 0;
        }

        .graph-caption {
            text-align: center;
            color: #666;
            font-size: 0.9rem;
            margin-top: 0.5rem;
        }

        /* Table */
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

        /* Buttons */
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

        .button.outline:hover {
            background: rgba(46,125,50,0.08);
        }

        /* Code blocks */
        .code-block {
            background: #1e293b;
            color: #a5d6a5;
            padding: 1rem;
            border-radius: 12px;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
            margin: 1rem 0;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 2rem 0;
            color: #64748b;
            border-top: 1px solid #cbd5e1;
            font-size: 0.9rem;
        }

        /* Mobile */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero .lead {
                font-size: 1.3rem;
            }
            
            .hero-grid {
                grid-template-columns: 1fr;
            }
            
            .glance-grid,
            .tech-grid,
            .features-grid,
            .roadmap-grid,
            .contribute-grid {
                grid-template-columns: 1fr;
            }
            
            .site-header {
                padding: 0.5rem 0;
            }
            
            .logo {
                font-size: 1.8rem;
            }
        }
    </style>
</head>
<body>

<!-- SMALL HEADER WITH LOGO CENTERED -->
<div class="site-header">
    <div class="logo">⚡ ACCUM</div>
</div>

<div class="container">

    <!-- HERO SECTION -->
    <div class="hero">
        <h1>Fair Proof-of-Work</h1>
        <p class="lead">Bitcoin is a lottery. ACCUM is a salary.</p>
        <p class="sublead">Every miner gets paid every block. No more winners and losers — just fair, predictable rewards.</p>
        
        <div class="hero-grid">
            <div class="hero-item">
                <strong>💰 Token</strong>
                $ACM · 21M supply · No premine
            </div>
            <div class="hero-item">
                <strong>⚙️ Consensus</strong>
                Proof‑of‑Work + Accumulative
            </div>
            <div class="hero-item">
                <strong>📈 Rewards</strong>
                Concave (logarithmic)
            </div>
            <div class="hero-item">
                <strong>🛡️ Security</strong>
                PoCI · P2P · Ultra‑Light
            </div>
        </div>
    </div>

    <!-- ACCUM AT A GLANCE -->
    <div class="section">
        <h2>⚡ ACCUM at a glance</h2>
        <div class="glance-grid">
            <div class="glance-item">
                <strong>Fair Launch</strong><br>
                February 2026<br>
                <small>no premine, no allocation</small>
            </div>
            <div class="glance-item">
                <strong>Algorithm</strong><br>
                Argon2id<br>
                <small>memory‑hard, ASIC‑resistant</small>
            </div>
            <div class="glance-item">
                <strong>Consensus</strong><br>
                Proof‑of‑Work<br>
                <small>Accumulative + Concave</small>
            </div>
            <div class="glance-item">
                <strong>Platforms</strong><br>
                Windows, Linux, macOS<br>
                <small>RPi, Android (soon)</small>
            </div>
            <div class="glance-item">
                <strong>TICKER</strong><br>
                $ACM
            </div>
            <div class="glance-item">
                <strong>Block time (testnet)</strong><br>
                ~60 seconds
            </div>
            <div class="glance-item">
                <strong>MAX SUPPLY</strong><br>
                21 000 000
            </div>
            <div class="glance-item">
                <strong>Network Status</strong><br>
                2 nodes · 62 blocks · 18 tx
            </div>
        </div>
    </div>

    <!-- TECHNICAL SPECIFICATIONS -->
    <div class="section">
        <h2>⚙️ Technical specifications (testnet)</h2>
        <div class="tech-grid">
            <div class="tech-item">
                <strong>Hash algorithm</strong><br>
                Argon2id<br>
                <small>memory‑hard</small>
            </div>
            <div class="tech-item">
                <strong>Shard target</strong><br>
                00ffff...<br>
                <small>very easy</small>
            </div>
            <div class="tech-item">
                <strong>Block target</strong><br>
                00ffff...<br>
                <small>very easy</small>
            </div>
            <div class="tech-item">
                <strong>Time per shard</strong><br>
                instant<br>
                <small>nonce up to 5000</small>
            </div>
            <div class="tech-item">
                <strong>Block time</strong><br>
                10–60 seconds
            </div>
            <div class="tech-item">
                <strong>Shards per block</strong><br>
                20–40
            </div>
            <div class="tech-item">
                <strong>Block reward</strong><br>
                50 ACM
            </div>
            <div class="tech-item">
                <strong>Platforms</strong><br>
                Windows, Linux, macOS
            </div>
            <div class="tech-item">
                <strong>Min. requirements</strong><br>
                2 cores, 2 GB RAM
            </div>
            <div class="tech-item">
                <strong>Node size</strong><br>
                ~1–2 MB<br>
                <small>will be < 50 MB</small>
            </div>
        </div>
    </div>

    <!-- INTERACTIVE CHART WITH MOUSE TOOLTIP -->
    <div class="section">
        <h2>📈 Concave rewards (logarithmic curve)</h2>
        <p><strong>ACCUM formula:</strong> R(n) = k · log(1 + n), where n is miner's share of the network.</p>
        <p>The derivative dR/dn = k/(1+n) decreases, making dominance less profitable and 51% attacks economically irrational.</p>
        
        <div class="chart-container">
            <canvas id="rewardChart"></canvas>
            <div id="chartTooltip" class="chart-tooltip"></div>
        </div>
        
        <div class="graph-caption">
            Green line — ACCUM logarithmic model | Dashed line — Bitcoin linear model
        </div>
    </div>

    <!-- 5 CORE INNOVATIONS -->
    <div class="section">
        <h2>🔷 5 core innovations</h2>
        <div class="features-grid">
            <div class="feature-card">
                <h3>⛏️ Accumulative Mining</h3>
                <p>Every miner receives a reward for every block. No lottery — stable income for all participants.</p>
            </div>
            <div class="feature-card">
                <h3>📉 Concave Rewards</h3>
                <p>Logarithmic reward curve makes 51% attacks economically unprofitable.</p>
            </div>
            <div class="feature-card">
                <h3>🆔 PoCI</h3>
                <p>Proof-of-Contribution-and-Identity — multi‑metric reputation (uptime, age, verification) for Sybil resistance.</p>
            </div>
            <div class="feature-card">
                <h3>💧 Shard Streams</h3>
                <p>Hashrate futures for instant miner liquidity. Native DeFi layer on PoW.</p>
            </div>
            <div class="feature-card">
                <h3>📱 Ultra‑Light Nodes</h3>
                <p>Full verification with ~50 MB state. Runs on mobile phones and Raspberry Pi.</p>
            </div>
        </div>
    </div>

    <!-- TWO-NODE MINING (LIVE LOGS) -->
    <div class="section">
        <h2>⛏️ Two‑node mining (live testnet)</h2>
        <p>Run two nodes with a single command:</p>
        <div class="code-block">
            python accum.py
        </div>
        <p>Live output from the testnet:</p>
        <div class="code-block">
[Node1] Address: a87df5988f2728f1e110c14644144252a49e39c2<br>
[Node2] Address: 71e37af1536860593bc8f64282207818b7c6294a<br>
[Node2] ✅ Shard 00235416 nonce=13<br>
[Node1] 📥 Shard 00235416<br>
[Node2] ✅ Shard 008e4372 nonce=45<br>
[Node1] 📥 Shard 008e4372<br>
[Node2] ✅ Shard 006c7828 nonce=163<br>
[Node1] 📥 Shard 006c7828<br>
[Node1] 📦 Assembling block from 32 shards, 0 tx<br>
[Node1] ⛏ Mining block...<br>
[Node1] ✅ Block 1 saved, hash 385ba362f2f8d707<br>
[Node2] 💸 Test transaction d4c97e95 (10 coins) to a87df598
        </div>
        <p style="margin-top:1rem;">
            <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 Download accum.py</a>
            <a href="#install" class="button outline">Quick start guide</a>
        </p>
    </div>

    <!-- TESTNET STATUS -->
    <div class="section">
        <h2>✅ Live testnet (Q1 2026)</h2>
        <div style="display:grid; grid-template-columns:repeat(3,1fr); gap:1rem; margin-bottom:1.5rem;">
            <div class="glance-item">
                <strong>62</strong><br>blocks
            </div>
            <div class="glance-item">
                <strong>18</strong><br>transactions
            </div>
            <div class="glance-item">
                <strong>2</strong><br>active nodes
            </div>
        </div>
        <ul style="margin-left:1.5rem;">
            <li>✅ Two independent nodes (ports 12345, 12346) running continuously</li>
            <li>✅ Blocks produced every ~60 seconds</li>
            <li>✅ Test transfers of 10 ACM are confirmed on-chain</li>
            <li>✅ P2P shard and block exchange fully functional</li>
            <li>✅ Logs and demo available upon request</li>
        </ul>
    </div>

    <!-- COMPARISON TABLE -->
    <div class="section">
        <h2>🔍 Comparison with other PoW</h2>
        <table>
            <thead>
                <tr>
                    <th>Parameter</th>
                    <th>Bitcoin</th>
                    <th>Kaspa</th>
                    <th>Monero</th>
                    <th>ACCUM</th>
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
    </div>

    <!-- ECONOMIC MODEL -->
    <div class="section">
        <h2>🔐 Economic model</h2>
        <p><strong>Bitcoin (linear):</strong> E = α·B — reward scales linearly with hashrate share, encouraging centralization.</p>
        <p><strong>ACCUM (logarithmic):</strong> R(n) = k·log(1+n) — increasing hashrate gives diminishing returns:</p>
        <ul style="margin-left:1.5rem;">
            <li>10× hashrate → ~3× reward</li>
            <li>100× hashrate → ~5× reward</li>
            <li>51% attack requires 51% hashrate but yields <51% reward</li>
        </ul>
    </div>

    <!-- ROADMAP -->
    <div class="section">
        <h2>🗺️ Roadmap</h2>
        <div class="roadmap-grid">
            <div class="roadmap-item">
                <strong>Q3 2026</strong><br>
                Public testnet<br>
                <small>Open for everyone</small>
            </div>
            <div class="roadmap-item">
                <strong>Q4 2026</strong><br>
                Security audit<br>
                <small>2 independent firms</small>
            </div>
            <div class="roadmap-item">
                <strong>Q1 2027</strong><br>
                Mainnet Launch<br>
                <small>Genesis block</small>
            </div>
            <div class="roadmap-item">
                <strong>Q2 2027</strong><br>
                Shard Streams<br>
                <small>DeFi layer on PoW</small>
            </div>
        </div>
    </div>

    <!-- CONTRIBUTE -->
    <div class="section">
        <h2>🧑‍💻 Contribute</h2>
        <p>ACCUM is a community project. Join us!</p>
        <div class="contribute-grid">
            <div class="contribute-item">
                <strong>🦀 Rust developers</strong><br>
                Core protocol, P2P, consensus
            </div>
            <div class="contribute-item">
                <strong>🐍 Python testers</strong><br>
                Testnet, bug hunting, optimization
            </div>
            <div class="contribute-item">
                <strong>📝 Documentation</strong><br>
                Translations, guides, articles
            </div>
        </div>
        <div style="margin-top:1.5rem;">
            <a href="https://github.com/andreudumitro-eng/ACCUM/issues" class="button">📌 GitHub Issues</a>
        </div>
    </div>

    <!-- CONTACT & LINKS -->
    <div class="section">
    <h2>📚 Source code & whitepaper</h2>
    <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub Repository</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (EN)</a>
    <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.1.md" class="button outline">📄 Whitepaper (RU)</a>
    <div style="margin-top:1.5rem; font-size:1.1rem;">
        📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro" target="_blank">@Andredumitro</a>
    </div>
</div>
    

    <!-- QUICK START -->
    <div class="code-block">
# 1. Clone the repository
git clone https://github.com/andreudumitro-eng/ACCUM.git
cd ACCUM

# 2. Install dependency
pip install argon2-cffi

# 3. Run two nodes
python accum.py
</div>

# 4. Watch shards and blocks appear in the console
        </div>
    </div>

    <!-- FOOTER -->
    <footer class="footer">
        <p>© 2026 Andrii Dumitro — ACCUM. Open source · Fair launch · No premine</p>
        <p style="margin-top:0.5rem;">⚡ Version 2.1 — Fully aligned with the whitepaper</p>
    </footer>
</div>

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
            
            // Grid
            ctx.strokeStyle = "#ccc";
            ctx.lineWidth = 0.5;
            for (let i = 0; i <= 5; i++) {
                let y = pad.top + (i / 5) * gh;
                ctx.beginPath();
                ctx.moveTo(pad.left, y);
                ctx.lineTo(w - pad.right, y);
                ctx.stroke();
            }
            
            // Bitcoin linear (dashed)
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
            
            // ACCUM logarithmic (green)
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
            
            // Legend
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
        
        // Mouse move handler for tooltip
        function handleMouseMove(e) {
            const rect = canvas.getBoundingClientRect();
            const scaleX = canvas.width / rect.width;
            const scaleY = canvas.height / rect.height;
            
            const mouseX = (e.clientX - rect.left) * scaleX;
            const mouseY = (e.clientY - rect.top) * scaleY;
            
            const pad = { left: 60, right: 20, top: 20, bottom: 30 };
            const gw = canvas.width - pad.left - pad.right;
            const gh = canvas.height - pad.top - pad.bottom;
            
            // Check if mouse is inside the chart area
            if (mouseX >= pad.left && mouseX <= canvas.width - pad.right &&
                mouseY >= pad.top && mouseY <= canvas.height - pad.bottom) {
                
                // Calculate share (x-axis value)
                const share = (mouseX - pad.left) / gw * 100;
                const clampedShare = Math.min(100, Math.max(0, share));
                
                // Calculate rewards
                const linearReward = clampedShare;  // percentage of max reward
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
