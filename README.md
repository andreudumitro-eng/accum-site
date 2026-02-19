# accum-site 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ACCUM — Concave Proof-of-Work Architecture</title>

<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{
background:#0b0f14;
color:#e4e8ef;
font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Arial,sans-serif;
line-height:1.7;
}
.container{
max-width:1100px;
margin:0 auto;
padding:3rem 1.5rem;
}
header{text-align:center;margin-bottom:4rem;}
h1{
font-size:4rem;
font-weight:700;
background:linear-gradient(135deg,#2e7d32,#1b5e20);
-webkit-background-clip:text;
-webkit-text-fill-color:transparent;
}
.subtitle{color:#9aa4b3;margin-top:1rem;font-size:1.3rem;}
section{margin-bottom:3.5rem;}
h2{color:#2e7d32;margin-bottom:1.2rem;font-size:1.8rem;}
h3{color:#2e7d32;margin:1.5rem 0 0.8rem;font-size:1.4rem;}
.card{
background:#141a22;
border:1px solid #27303c;
padding:2rem;
border-radius:16px;
}
p{margin-bottom:1rem;color:#c7ceda;}
ul, ol{margin-left:1.2rem;margin-bottom:1rem;}
li{margin-bottom:0.6rem;color:#b6bfcc;}
.formula{
background:#0f141c;
padding:1rem;
border-radius:12px;
font-family:monospace;
color:#2e7d32;
margin:1rem 0;
overflow-x:auto;
}
.grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
gap:1.5rem;
}
table{
width:100%;
border-collapse:collapse;
margin-top:1rem;
}
th,td{
padding:0.8rem;
border-bottom:1px solid #27303c;
text-align:left;
color:#cbd3df;
}
th{color:#2e7d32;}
td{font-size:0.95rem;}
canvas{
background:#0f141c;
border-radius:12px;
margin-top:1rem;
width:100%;
height:auto;
}
.button{
display:inline-block;
background:#2e7d32;
color:#0b0f14;
padding:0.8rem 2rem;
border-radius:40px;
text-decoration:none;
font-weight:600;
margin:0.5rem 0.5rem 0 0;
border:none;
cursor:pointer;
}
.button.outline{
background:transparent;
border:1px solid #2e7d32;
color:#2e7d32;
}
.button.small{
padding:0.4rem 1.2rem;
font-size:0.9rem;
}
.status-grid{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:1rem;
margin-top:1.5rem;
}
.stat-item{
background:#0f141c;
padding:1rem;
border-radius:12px;
text-align:center;
}
.stat-value{
font-size:2.2rem;
font-weight:700;
color:#2e7d32;
line-height:1.2;
}
.stat-label{
font-size:0.9rem;
color:#9aa4b3;
text-transform:uppercase;
letter-spacing:0.5px;
}
footer{
margin-top:4rem;
padding-top:2rem;
border-top:1px solid #27303c;
text-align:center;
color:#6f7887;
font-size:0.9rem;
}
</style>
</head>
<body>
<div class="container">

<header>
<h1>ACCUM</h1>
<div class="subtitle">
Fair Proof-of-Work with Concave Rewards<br>
Accumulative Mining • Economic Game-Theory Redesign
</div>
</header>

<section>
<div class="card">
<h2>Protocol Overview</h2>
<p>
ACCUM is a Layer-1 Proof-of-Work blockchain that introduces concave reward distribution and accumulative mining. 
Instead of the winner-takes-all lottery mechanism, rewards accumulate proportionally to sustained contribution, 
transforming mining from a probabilistic event into a deterministic salary.
</p>
<p>
Native asset: <strong>$ACM</strong>. Issued exclusively through mining. No premine. No insider allocation. 
Max supply: 21,000,000.
</p>
</div>
</section>

<!-- ===== LIVE TESTNET STATUS ===== -->
<section>
<div class="card">
<h2>Live Testnet Status (Q1 2026)</h2>
<p>
A two-node testnet has been operational since February 2026, demonstrating the complete protocol stack 
in a real-world P2P environment.
</p>

<div class="status-grid">
<div class="stat-item">
<div class="stat-value">62</div>
<div class="stat-label">Blocks Produced</div>
</div>
<div class="stat-item">
<div class="stat-value">18</div>
<div class="stat-label">Transactions</div>
</div>
<div class="stat-item">
<div class="stat-value">100%</div>
<div class="stat-label">P2P Sync</div>
</div>
</div>

<ul style="margin-top:1.5rem;">
<li>✅ Two independent nodes (ports 12345, 12346) running continuously</li>
<li>✅ Block production: ~1 block per minute per node (60s target)</li>
<li>✅ Shard exchange via P2P — all shards propagated between nodes</li>
<li>✅ Test transactions: 10 ACM transfers confirmed in blocks</li>
<li>✅ Concave reward calculation verified — balances update correctly</li>
<li>✅ Network synchronization — both nodes maintain identical chain state</li>
</ul>

<p style="color:#2e7d32; margin-top:1rem;">
📡 Live dashboard and node logs available upon request (local demonstration or video).
</p>
</div>
</section>

<section>
<div class="card">
<h2>Economic Function</h2>
<p>The core reward function is concave logarithmic:</p>
<div class="formula">
R(h) = R_block · log₂(1 + h / h₀) / log₂(1 + H / h₀)
</div>
<p>
Where h is miner's hashrate, H is total network hashrate, and h₀ is a normalization constant. 
This formulation ensures that marginal gain decreases with increasing hashrate share.
</p>

<canvas id="curve" height="260"></canvas>

<p style="margin-top:1rem; font-size:0.95rem; color:#9aa4b3;">
Solid green: ACCUM logarithmic curve. Dashed grey: linear model (Bitcoin).
</p>
</div>
</section>

<section>
<div class="card">
<h2>Game-Theoretic Analysis</h2>

<h3>Formal Model</h3>
<p>
Consider a set of miners \(N\) with hashrates \(h_i\). Total hashrate \(H = \sum h_i\). 
The expected reward per block for miner i is:
</p>
<div class="formula">
U_i = R · f(h_i / H) - c · h_i
</div>
<p>
where f is a concave function (f'' < 0) and c is the marginal cost of hashrate.
</p>

<h3>Nash Equilibrium</h3>
<p>
In a linear system (f(x)=x), any miner with cost advantage can increase market share indefinitely. 
In ACCUM, concavity creates diminishing returns. The first-order condition for optimum:
</p>
<div class="formula">
R · f'(h_i/H) · (1/H) = c
</div>
<p>
Since f' is decreasing, there exists a unique symmetric equilibrium where all miners 
choose the same hashrate. Deviation (increasing h) yields negative marginal profit.
</p>

<h3>51% Attack (In)feasibility</h3>
<p>
An attacker acquiring 51% of hashrate would have share x = 0.51. Their reward share is f(0.51). 
For a concave f, f(0.51) &lt; 0.51. The attacker pays for 51% of network cost but receives 
less than 51% of rewards. The difference f(0.5) - 0.5 represents the security margin.
</p>
<p>
In logarithmic model with α=0.3, f(0.51) ≈ 0.37. Attacker would need to sustain 
operational losses, making attack economically irrational.
</p>
</div>
</section>

<section>
<div class="card">
<h2>Proof-of-Contribution-and-Identity (PoCI)</h2>

<p>
Sybil resistance is achieved through a multi-metric reputation score:
</p>

<div class="formula">
S = w₁·C_hash + w₂·T_uptime + w₃·V_tx + w₄·B_bandwidth + w₅·A_age + w₆·H_history
</div>

<p>Weights are calibrated as:</p>
<ul>
<li>Hashrate contribution (C_hash): 40%</li>
<li>Uptime (T_uptime): 20%</li>
<li>Transactions verified (V_tx): 15%</li>
<li>Bandwidth provided (B_bandwidth): 10%</li>
<li>Network age (A_age): 10%</li>
<li>Historical honesty (H_history): 5%</li>
</ul>

<h3>Sybil Cost Analysis</h3>
<p>
A Sybil attacker deploying k ephemeral nodes gains at most k·δ, where δ is the 
minimal per-node contribution (mostly from hashrate). An honest node with age T 
accumulates at least δ + w₂·T + w₅·T.
</p>
<p>
To outweigh one honest node, the attacker needs:
</p>
<div class="formula">
k · δ > δ + (w₂ + w₅)·T   →   k > 1 + (w₂ + w₅)·T/δ
</div>
<p>
With typical values (δ ≈ 0.01, w₂+w₅ = 0.3, T=1 year), k > 1 + 30 = 31. 
Creating 31 real Sybils with year-long history is prohibitively expensive compared 
to the cost of one honest node. Temporal components make large-scale Sybil attacks 
economically unfeasible.
</p>
</div>
</section>

<section>
<div class="card">
<h2>Cryptographic Primitives</h2>
<p>
ACCUM employs <strong>Argon2id</strong> as the memory-hard hash function for shard mining. 
Argon2id provides resistance against GPU/ASIC optimization, ensuring that mining 
remains accessible to consumer hardware at the shard level.
</p>
<p>
Block headers are hashed with SHA256 for compatibility with existing verification 
tooling. The combination creates a hybrid security model: memory-hard shard 
production for decentralization, and fast block verification for efficiency.
</p>
</div>
</section>

<section>
<div class="card">
<h2>Shard Streams (Future Primitive)</h2>
<p>
Shard Streams are a proposed protocol extension for tokenizing future block rewards. 
Miners will be able to issue non-fungible tokens representing a claim on a fraction 
of their future mining income. This provides:
</p>
<ul>
<li><strong>Miners:</strong> Immediate liquidity without selling hardware</li>
<li><strong>Investors:</strong> Exposure to mining revenue without operational overhead</li>
<li><strong>Network:</strong> Native DeFi layer directly on PoW</li>
</ul>
<p>
Shard Streams are designed as an opt-in feature, not affecting core consensus.
</p>
</div>
</section>

<section>
<div class="card">
<h2>Comparative Architecture</h2>
<table>
<tr>
<th>Property</th>
<th>Bitcoin</th>
<th>Monero</th>
<th>Kaspa</th>
<th>ACCUM</th>
</tr>
<tr>
<td>Reward Model</td>
<td>Linear Lottery</td>
<td>Linear Lottery</td>
<td>Block DAG Linear</td>
<td>Concave Accumulative</td>
</tr>
<tr>
<td>Premine</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
<tr>
<td>Marginal Dominance Incentive</td>
<td>Linear</td>
<td>Linear</td>
<td>Linear</td>
<td>Logarithmically Reduced</td>
</tr>
<tr>
<td>Reward Distribution per Block</td>
<td>1 winner</td>
<td>1 winner</td>
<td>1 winner</td>
<td>All participants</td>
</tr>
<tr>
<td>Sybil Resistance Mechanism</td>
<td>None</td>
<td>None</td>
<td>None</td>
<td>PoCI (Reputation)</td>
</tr>
<tr>
<td>Economic Disincentive for 51% Attack</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>Yes (concave function)</td>
</tr>
<tr>
<td>Native Liquidity Instrument</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>Shard Streams*</td>
</tr>
<tr>
<td>Ultra-Light Node Support</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>Yes (50 MB state)</td>
</tr>
</table>
<p style="font-size:0.85rem; margin-top:0.5rem;">* Future protocol extension</p>
</div>
</section>

<section>
<div class="card">
<h2>Resources</h2>
<a href="https://github.com/andreudumitro-eng/ACCUM" class="button">GitHub</a>
<a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/en/ACCUM_whitepaper_v2.0_en.md" class="button outline">Whitepaper (EN)</a>
<a href="https://github.com/andreudumitro-eng/ACCUM/blob/main/whitepaper/ru/ACCUM_whitepaper_v2.0_ru.md" class="button outline">Whitepaper (RU)</a>
<a href="#" class="button outline small">Research Paper (PDF, soon)</a>
</div>
</section>

<footer>
© 2026 Andrii Dumitro — ACCUM Protocol Research Initiative
</footer>

</div>

<script>
function drawCurve(){
const c=document.getElementById("curve");
const ctx=c.getContext("2d");
const w=c.clientWidth;
const h=260;
c.width=w;
c.height=h;

const pad=50;
const maxLog=Math.log2(101);

// grid
ctx.strokeStyle="#27303c";
ctx.lineWidth=0.5;
for(let i=0;i<=5;i++){
let y=pad+(i/5)*(h-2*pad);
ctx.beginPath();
ctx.moveTo(pad,y);
ctx.lineTo(w-pad,y);
ctx.stroke();
}

// linear (dashed)
ctx.strokeStyle="#777";
ctx.lineWidth=2;
ctx.setLineDash([5,3]);
ctx.beginPath();
for(let x=1;x<=100;x++){
let dx=pad+(x/100)*(w-2*pad);
let dy=h-pad-(x/100)*(h-2*pad);
if(x===1)ctx.moveTo(dx,dy);
else ctx.lineTo(dx,dy);
}
ctx.stroke();

// logarithmic (solid)
ctx.strokeStyle="#2e7d32";
ctx.lineWidth=3;
ctx.setLineDash([]);
ctx.beginPath();
for(let x=1;x<=100;x++){
let dx=pad+(x/100)*(w-2*pad);
let val=Math.log2(1+x)/maxLog;
let dy=h-pad-val*(h-2*pad);
if(x===1)ctx.moveTo(dx,dy);
else ctx.lineTo(dx,dy);
}
ctx.stroke();

// labels
ctx.fillStyle="#9aa4b3";
ctx.font="12px monospace";
ctx.textAlign="right";
ctx.fillText("reward",pad-10,pad+10);
ctx.textAlign="center";
ctx.fillText("hashrate share →",w/2,h-10);
}
window.addEventListener("load",drawCurve);
window.addEventListener("resize",drawCurve);
</script>

</body>
</html>
