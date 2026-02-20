<index.html>
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

        /* Переключатель языков */
        .language-switcher {
            position: fixed;
            top: 1rem;
            right: 1.5rem;
            z-index: 1001;
        }
        .lang-btn {
            background: rgba(255, 255, 255, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.3);
            color: white;
            padding: 0.4rem 0.8rem;
            margin-left: 0.5rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        .lang-btn.active {
            background: #ffd966;
            color: #1e293b;
        }
        .lang-btn:hover {
            background: #ffd966;
            color: #1e293b;
        }

        h2 {
            color: #2e7d32;
            font-size: 2rem;
            margin-bottom: 1.5rem;
            border-left: 6px solid #2e7d32;
            padding-left: 1rem;
        }
        .hero {
            background: linear-gradient(135deg, #1b3b1f 0%, #2e7d32 100%);
            color: white;
            padding: 3rem 2rem;
            border-radius: 32px;
            margin-bottom: 2rem;
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
        .section {
            background: rgba(255,255,255,0.85);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(46,125,50,0.15);
            border-radius: 24px;
            padding: 2rem;
            margin: 2rem 0;
            box-shadow: 0 8px 30px rgba(0,20,10,0.06);
        }
        .glance-grid, .tech-grid, .features-grid, .roadmap-grid, .contribute-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            margin-top: 1rem;
        }
        .glance-item, .tech-item, .feature-card, .roadmap-item, .contribute-item {
            background: white;
            border-radius: 20px;
            padding: 1.5rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.04);
            border: 1px solid #e2e8f0;
        }
        .glance-item strong, .tech-item strong {
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
        canvas {
            width: 100%;
            height: 280px;
            background: #ffffff;
            border-radius: 20px;
            padding: 1rem;
            box-shadow: inset 0 2px 8px rgba(0,0,0,0.02);
            margin-top: 1rem;
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
        .footer {
            text-align: center;
            padding: 2rem 0;
            color: #6474
