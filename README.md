# accum-site 
  <!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ACCUM — Economic Model Demo</title>
    <style>
        body {
            margin: 0;
            font-family: 'Segoe UI', Arial, sans-serif;
            background: #0f1116;
            color: #e6e6e6;
        }
        .container {
            max-width: 1000px;
            margin: auto;
            padding: 20px;
        }
        h1 {
            text-align: center;
            font-size: 42px;
            margin-bottom: 10px;
            background: linear-gradient(135deg, #2e7d32, #1b5e20);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .section {
            margin-top: 50px;
        }
        .card {
            background: #161a22;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 20px;
            transition: 0.3s ease;
            border: 1px solid #2d2f36;
        }
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 25px rgba(46, 125, 50, 0.3);
            border-color: #2e7d32;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            background: #0f1116;
            border: 1px solid #333;
            color: white;
            border-radius: 6px;
            font-size: 16px;
        }
        button {
            padding: 12px 20px;
            margin-top: 15px;
            background: #2e7d32;
            border: none;
            color: black;
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            transition: background 0.2s;
        }
        button:hover {
            background: #1b5e20;
        }
        a.button {
            display: inline-block;
            text-decoration: none;
            margin: 10px 10px 0 0;
        }
        canvas {
            width: 100%;
            height: auto;
            background: #111;
            border-radius: 10px;
            display: block;
            margin-top: 15px;
        }
        .chart-container {
            position: relative;
        }
        .axis-labels {
            display: flex;
            justify-content: space-between;
            margin-top: 5px;
            color: #888;
            font-size: 14px;
        }
        .explanation {
            margin-top: 20px;
            padding: 15px;
            background: #1e232c;
            border-left: 4px solid #2e7d32;
            border-radius: 8px;
            font-size: 15px;
            line-height: 1.5;
            color: #ccc;
        }
        .footer {
            text-align: center;
            margin-top: 60px;
            opacity: 0.6;
            font-size: 14px;
            border-top: 1px solid #2d2f36;
            padding-top: 20px;
        }
        @media(max-width:600px){
            h1 { font-size: 28px; }
        }
    </style>
</head>
<body>

<div class="container">

    <h1>ACCUM Economic Model</h1>
    <p style="text-align:center; opacity:0.8;">Интерактивная демонстрация вогнутых наград (concave rewards)</p>

    <!-- Калькулятор -->
    <div class="section card">
        <h2>🧮 Калькулятор награды</h2>
        <label>Количество шардов (вклад майнера):</label>
        <input type="number" id="shards" value="10" min="1" step="1">

        <label>Базовая награда блока (ACM):</label>
        <input type="number" id="reward" value="100" min="1" step="1">

        <button onclick="calculate()">Рассчитать награду</button>

        <p id="result" style="margin-top:15px; font-weight:bold; font-size:18px;"></p>
        <p style="opacity:0.6; font-size:14px;">
            * Награда рассчитывается по формуле: <code>reward × log₂(1 + shards)</code>
        </p>
    </div>

    <!-- График -->
    <div class="section card">
        <h2>📈 Логарифмическая кривая наград</h2>
        <div class="chart-container">
            <canvas id="chart" height="300"></canvas>
        </div>
        <div class="axis-labels">
            <span>0 шардов</span>
            <span>Количество шардов →</span>
            <span>100+</span>
        </div>
        <div class="explanation">
            <strong>Почему это важно?</strong> Линейная модель (пунктир) позволяет крупным майнерам получать непропорционально много. Логарифмическая кривая (зелёная) делает награду вогнутой: 10× больше шардов дают лишь ~3× награду. Это экономически предотвращает 51% атаки и централизацию.
        </div>
    </div>

    <!-- Ссылки на проект -->
    <div class="section card" style="text-align:center;">
        <h2>🔗 Исходный код и документы</h2>
        <a href="https://github.com/andreudumitro-eng/ACCUM" class="button"><button>📦 GitHub</button></a>
        <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button"><button>📄 Whitepaper (EN)</button></a>
        <a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button"><button>📄 Whitepaper (RU)</button></a>
        <p style="margin-top:15px;">📧 <strong>andreudumitro@gmail.com</strong> | 🐦 <a href="https://twitter.com/Andredumitro" style="color:#2e7d32;">@Andredumitro</a></p>
    </div>

    <div class="footer">
        ACCUM © 2026 — The First Fair Proof-of-Work Blockchain
    </div>

</div>

<script>
    // Функция расчёта
    function calculate() {
        let shards = parseFloat(document.getElementById("shards").value);
        let reward = parseFloat(document.getElementById("reward").value);

        if (shards <= 0 || reward <= 0 || isNaN(shards) || isNaN(reward)) {
            document.getElementById("result").innerText = "❌ Введите корректные положительные числа.";
            return;
        }

        // Логарифмическая модель: reward * log2(1 + shards)
        let total = reward * Math.log2(1 + shards);
        document.getElementById("result").innerHTML = 
            `✅ Награда майнера: <span style="color:#2e7d32;">${total.toFixed(4)} ACM</span> (при вкладе ${shards} шардов)`;
    }

    // Рисование графика
    function drawChart() {
        const canvas = document.getElementById("chart");
        const ctx = canvas.getContext("2d");
        const w = canvas.clientWidth;
        const h = 300; // фиксированная высота
        canvas.width = w;
        canvas.height = h;

        ctx.clearRect(0, 0, w, h);

        // Настройки отступов
        const padding = { left: 50, right: 20, top: 20, bottom: 40 };
        const graphW = w - padding.left - padding.right;
        const graphH = h - padding.top - padding.bottom;

        // Оси
        ctx.strokeStyle = "#555";
        ctx.lineWidth = 1;
        ctx.beginPath();
        // ось Y
        ctx.moveTo(padding.left, padding.top);
        ctx.lineTo(padding.left, h - padding.bottom);
        // ось X
        ctx.moveTo(padding.left, h - padding.bottom);
        ctx.lineTo(w - padding.right, h - padding.bottom);
        ctx.stroke();

        // Сетка (горизонтальные линии)
        ctx.strokeStyle = "#333";
        ctx.lineWidth = 0.5;
        for (let i = 0; i <= 5; i++) {
            let y = padding.top + (i / 5) * graphH;
            ctx.beginPath();
            ctx.moveTo(padding.left, y);
            ctx.lineTo(w - padding.right, y);
            ctx.stroke();
        }

        // Подписи оси Y (награда)
        ctx.fillStyle = "#aaa";
        ctx.font = "12px Arial";
        ctx.textAlign = "right";
        ctx.textBaseline = "middle";
        for (let i = 0; i <= 5; i++) {
            let y = padding.top + (i / 5) * graphH;
            let value = 5 - i; // 5,4,3,2,1,0 (условные единицы)
            ctx.fillText(value.toFixed(1), padding.left - 10, y);
        }
        ctx.fillText("награда", padding.left - 45, padding.top + 10);

        // Подпись оси X
        ctx.fillStyle = "#aaa";
        ctx.font = "12px Arial";
        ctx.textAlign = "center";
        ctx.fillText("шарды", w/2, h - 5);

        // Рисуем логарифмическую кривую
        ctx.strokeStyle = "#2e7d32";
        ctx.lineWidth = 3;
        ctx.beginPath();

        // Линейная для сравнения (пунктир)
        ctx.strokeStyle = "#777";
        ctx.lineWidth = 1.5;
        ctx.setLineDash([5, 3]);
        ctx.beginPath();
        for (let x = 1; x <= 100; x++) {
            let drawX = padding.left + (x / 100) * graphW;
            let yLinear = (x / 100) * graphH; // линейный рост от 0 до 1
            let drawY = h - padding.bottom - yLinear;
            if (x === 1) ctx.moveTo(drawX, drawY);
            else ctx.lineTo(drawX, drawY);
        }
        ctx.stroke();
        ctx.setLineDash([]); // сброс пунктира

        // Логарифмическая кривая
        ctx.strokeStyle = "#2e7d32";
        ctx.lineWidth = 3;
        ctx.beginPath();

        // Нормализуем логарифм так, чтобы при x=100 y занимал почти всю высоту
        const maxLog = Math.log2(101); // log2(101) ≈ 6.66
        for (let x = 1; x <= 100; x++) {
            let val = Math.log2(1 + x) / maxLog; // от 0 до 1
            let drawX = padding.left + (x / 100) * graphW;
            let drawY = h - padding.bottom - val * graphH;
            if (x === 1) ctx.moveTo(drawX, drawY);
            else ctx.lineTo(drawX, drawY);
        }
        ctx.stroke();

        // Добавим маленькую легенду
        ctx.fillStyle = "#2e7d32";
        ctx.fillRect(w - 150, padding.top + 5, 12, 12);
        ctx.fillStyle = "#aaa";
        ctx.font = "12px Arial";
        ctx.textAlign = "left";
        ctx.fillText("Логарифмическая (ACCUM)", w - 130, padding.top + 16);

        ctx.fillStyle = "#777";
        ctx.fillRect(w - 150, padding.top + 30, 12, 12);
        ctx.fillStyle = "#aaa";
        ctx.fillText("Линейная (Bitcoin)", w - 130, padding.top + 41);
    }

    // Вызов при загрузке и изменении размера окна
    window.addEventListener('load', () => {
        calculate(); // начальное значение
        drawChart();
    });
    window.addEventListener('resize', drawChart);
</script>

</body>
</html>
