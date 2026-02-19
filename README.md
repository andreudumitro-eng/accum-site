# accum-site 
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
            background: #0a0b0e;
            color: #e1e4e8;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            line-height: 1.6;
        }
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 2rem 1.5rem;
        }
        header {
            text-align: center;
            margin-bottom: 2rem;
        }
        h1 {
            font-size: 4rem;
            font-weight: 700;
            background: linear-gradient(135deg, #2e7d32, #1b5e20);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
        }
        .subtitle {
            font-size: 1.5rem;
            color: #b0b7c4;
            margin-bottom: 1rem;
        }
        .tagline {
            font-size: 2rem;
            font-weight: 500;
            color: #2e7d32;
            margin: 2rem 0;
        }
        .graph-card {
            background: #16181d;
            border: 1px solid #2d2f36;
            border-radius: 16px;
            padding: 2rem;
            margin: 2rem 0;
        }
        .graph-card h2 {
            color: #2e7d32;
            font-size: 1.8rem;
            margin-bottom: 1rem;
        }
        canvas {
            width: 100%;
            height: auto;
            background: #0f1116;
            border-radius: 12px;
            margin: 1rem 0;
        }
        .graph-caption {
            color: #9aa1b0;
            font-size: 0.95rem;
            margin-top: 0.5rem;
            text-align: center;
        }
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin: 3rem 0;
        }
        .feature {
            background: #16181d;
            padding: 1.5rem;
            border-radius: 12px;
            border: 1px solid #2d2f36;
            transition: transform 0.2s, border-color 0.2s;
        }
        .feature:hover {
            transform: translateY(-5px);
            border-color: #2e7d32;
        }
        .feature h3 {
            color: #2e7d32;
            font-size: 1.4rem;
            margin-bottom: 0.8rem;
        }
        .feature p {
            color: #9aa1b0;
        }
        .links {
            text-align: center;
            background: #16181d;
            padding: 2rem;
            border-radius: 16px;
            border: 1px solid #2d2f36;
            margin: 3rem 0;
        }
        .links h2 {
            color: #2e7d32;
            font-size: 2rem;
            margin-bottom: 1.5rem;
        }
        .button {
            display: inline-block;
            background: #2e7d32;
            color: #0a0b0e;
            text-decoration: none;
            padding: 0.9rem 2rem;
            border-radius: 40px;
            font-weight: 600;
            margin: 0.5rem;
            transition: background 0.2s;
            border: none;
            cursor: pointer;
            font-size: 1rem;
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
            background: rgba(46, 125, 50, 0.1);
        }
        .contacts {
            text-align: center;
            margin: 2rem 0;
            font-size: 1.2rem;
        }
        .contacts a {
            color: #2e7d32;
            text-decoration: none;
        }
        .footer {
            text-align: center;
            padding: 2rem 0;
            border-top: 1px solid #2d2f36;
            color: #6f7887;
        }
        @media (max-width: 600px) {
            h1 { font-size: 3rem; }
            .tagline { font-size: 1.5rem; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>ACCUM</h1>
            <div class="subtitle">The First Fair Proof-of-Work Blockchain</div>
            <div class="tagline">Bitcoin is a lottery. Accum is a salary.</div>
        </header>

        <!-- Кривая -->
        <div class="graph-card">
            <h2>📈 Concave Rewards (Anti-Whale)</h2>
            <canvas id="rewardChart" height="250"></canvas>
            <div class="graph-caption">
                Зелёная кривая — логарифмическая модель ACCUM (вогнутые награды).<br>
                Пунктир — линейная модель Bitcoin.
            </div>
        </div>

        <!-- 5 инноваций -->
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

        <!-- Ссылки -->
        <div class="links">
            <h2>Source Code & Whitepaper</h2>
            <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub</a>
            <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">📄 Whitepaper (EN)</a>
            <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">📄 Whitepaper (RU)</a>
        </div>

        <!-- Контакты -->
        <div class="contacts">
            <p>📧 <strong>andreudumitro@gmail.com</strong> &nbsp; | &nbsp; 🐦 <a href="https://twitter.com/Andredumitro">@Andredumitro</a></p>
        </div>

        <footer class="footer">
            <p>© 2026 Andrii Dumitro — ACCUM. All rights reserved.</p>
        </footer>
    </div>

    <script>
        function drawChart() {
            const canvas = document.getElementById('rewardChart');
            const ctx = canvas.getContext('2d');
            const w = canvas.clientWidth;
            const h = 250;
            canvas.width = w;
            canvas.height = h;

            const pad = { left: 50, right: 20, top: 20, bottom: 30 };
            const gw = w - pad.left - pad.right;
            const gh = h - pad.top - pad.bottom;

            // Сетка
            ctx.strokeStyle = "#333";
            ctx.lineWidth = 0.5;
            for (let i = 0; i <= 5; i++) {
                let y = pad.top + (i / 5) * gh;
                ctx.beginPath();
                ctx.moveTo(pad.left, y);
                ctx.lineTo(w - pad.right, y);
                ctx.stroke();
            }

            // Линейная (пунктир)
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

            // Логарифмическая (зелёная)
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

            // Подписи
            ctx.fillStyle = "#aaa";
            ctx.font = "12px Arial";
            ctx.textAlign = "right";
            ctx.fillText("награда", pad.left - 10, pad.top + 10);
            ctx.textAlign = "center";
            ctx.fillText("шарды", w / 2, h - 5);

            // Легенда
            ctx.fillStyle = "#2e7d32";
            ctx.fillRect(w - 150, pad.top + 5, 12, 12);
            ctx.fillStyle = "#aaa";
            ctx.font = "12px Arial";
            ctx.textAlign = "left";
            ctx.fillText("Логарифмическая (ACCUM)", w - 130, pad.top + 16);

            ctx.fillStyle = "#777";
            ctx.fillRect(w - 150, pad.top + 30, 12, 12);
            ctx.fillStyle = "#aaa";
            ctx.fillText("Линейная (Bitcoin)", w - 130, pad.top + 41);
        }

        window.addEventListener('load', drawChart);
        window.addEventListener('resize', drawChart);
    </script>
</body>
</html>
