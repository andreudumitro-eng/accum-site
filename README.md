# accum-site 
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
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: #0a0b0e;
            color: #e1e4e8;
            line-height: 1.6;
        }
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 2rem 1.5rem;
        }
        header {
            text-align: center;
            margin-bottom: 3rem;
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
            border-bottom: 1px solid #2d2f36;
            padding-bottom: 1.5rem;
        }
        .tagline {
            font-size: 2rem;
            font-weight: 500;
            margin: 2rem 0;
            color: #2e7d32;
        }
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }
        .feature {
            background: #16181d;
            padding: 2rem;
            border-radius: 12px;
            border: 1px solid #2d2f36;
            transition: transform 0.2s, border-color 0.2s;
        }
        .feature:hover {
            transform: translateY(-5px);
            border-color: #2e7d32;
        }
        .feature h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #2e7d32;
        }
        .feature p {
            color: #9aa1b0;
        }
        .github-section {
            text-align: center;
            background: #16181d;
            padding: 2rem;
            border-radius: 16px;
            border: 1px solid #2d2f36;
            margin: 3rem 0;
        }
        .github-section h2 {
            font-size: 2rem;
            color: #2e7d32;
            margin-bottom: 1rem;
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
        }
        .button:hover {
            background: #1b5e20;
        }
        .footer {
            text-align: center;
            padding: 2rem 0;
            border-top: 1px solid #2d2f36;
            color: #6f7887;
        }
        .footer a {
            color: #2e7d32;
            text-decoration: none;
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

        <div class="features">
            <div class="feature">
                <h3>Accumulative Mining</h3>
                <p>Every miner gets paid <strong>every block</strong>. No lottery — proportional rewards for all participants.</p>
            </div>
            <div class="feature">
                <h3>Concave Rewards</h3>
                <p>Logarithmic reward curve makes 51% attacks <strong>economically unprofitable</strong> and prevents whale dominance.</p>
            </div>
            <div class="feature">
                <h3>PoCI</h3>
                <p>Proof-of-Contribution-and-Identity — multi-metric reputation kills Sybil attacks with zero extra cost.</p>
            </div>
            <div class="feature">
                <h3>Shard Streams</h3>
                <p>Hashrate futures for instant miner liquidity. Native DeFi layer on PoW without bridges or oracles.</p>
            </div>
            <div class="feature">
                <h3>Ultra-Light Nodes</h3>
                <p>Full verification with <strong>50 MB state</strong>, sync in 5 minutes, runs on phones, routers, Raspberry Pi.</p>
            </div>
        </div>

        <div class="github-section">
            <h2>Source Code & Whitepaper</h2>
            <p style="margin-bottom: 1.5rem;">All technical specifications and the Rust prototype are available in the open repository.</p>
            <a href="https://github.com/andreudumitro-eng/ACCUM" class="button">📦 GitHub Repository</a>
        </div>

        <div style="text-align: center; margin: 3rem 0;">
            <p style="font-size: 1.2rem;">📧 <strong>andreudumitro@gmail.com</strong> &nbsp; | &nbsp; 🐦 <a href="https://twitter.com/Andredumitro" style="color: #2e7d32; text-decoration: none;">@Andredumitro</a></p>
        </div>
    </div>
    <footer class="footer">
        <p>© 2026 Andrii Dumitro — ACCUM. All rights reserved.</p>
    </footer>
</body>
</html>
