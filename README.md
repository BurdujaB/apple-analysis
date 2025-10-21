<!DOCTYPE html>
<html lang="ro">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Apple Inc. (AAPL) — Live Analysis</title>
  <meta name="description" content="Pagină minimalistă cu TradingView live și grafic interactiv de revenue (Chart.js)." />
  <style>
    :root{
      --bg:#0b0b0f; --panel:#14141b; --muted:#a1a1aa; --text:#fafafa;
      --border:#262633; --card:#0f0f15;
      --rev-h: clamp(300px, 42vh, 420px);
    }
    *{box-sizing:border-box}
    html,body{margin:0;padding:0;background:var(--bg);color:var(--text);font:16px/1.5 system-ui,-apple-system,Segoe UI,Roboto,Inter,Arial}
    .container{max-width:1100px;margin:0 auto;padding:0 20px}
    .row{display:flex;gap:12px}.row.between{justify-content:space-between}.row.center{align-items:center}
    .grid-2{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:16px}
    @media (max-width:800px){.grid-2{grid-template-columns:1fr}}

    .nav{position:sticky;top:0;backdrop-filter:saturate(120%) blur(6px);background:#0b0b0fc0;border-bottom:1px solid var(--border);z-index:40}
    .brand .logo{width:30px;height:30px;display:grid;place-items:center;background:#14141b;border-radius:10px;font-size:18px}
    .brand-text{margin-left:8px;font-weight:600;color:#e5e7eb}

    .hero{padding:48px 0 18px}
    h1{font-size:clamp(28px,4vw,46px);line-height:1.1;margin:0 0 8px}
    h2{font-size:clamp(20px,3vw,28px);margin:0 0 8px}
    .muted{color:var(--muted)} .small{font-size:13px}

    .btn{display:inline-flex;align-items:center;gap:8px;padding:10px 14px;border-radius:14px;border:1px solid var(--border);color:var(--text);text-decoration:none;background:transparent}
    .btn.primary{background:linear-gradient(90deg,#1e293b,#111827);border-color:#1f2937}
    .btn.ghost{background:transparent}

    .kpis{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:14px;padding:10px 20px 0}
    @media (max-width:900px){.kpis{grid-template-columns:repeat(2,minmax(0,1fr))}}
    .card{background:var(--card);border:1px solid var(--border);border-radius:18px;padding:14px}
    .k{color:#cbd5e1;font-size:13px}
    .v{font-weight:700;font-size:22px}

    .section{padding:26px 0}
    .embed{background:var(--panel);border:1px solid var(--border)}
    .rounded{border-radius:18px;overflow:hidden}

    .revenue-wrap{border-radius:18px;overflow:hidden;background:#14141b;border:1px solid #262633}
    #appleRevenueChart{display:block;width:100%;height:var(--rev-h)}

    .footer{border-top:1px solid var(--border);padding:18px 0;margin-top:26px}
  </style>
</head>
<body>
  <header class="nav">
    <div class="container row between center">
      <div class="brand row center">
        <div class="logo"></div>
        <div class="brand-text">Company Analysis</div>
      </div>
      <nav class="row">
        <a href="#live-chart" class="btn primary">Live Chart</a>
        <a href="#financials" class="btn">Revenue</a>
        <a href="#sources" class="btn ghost">Sources</a>
      </nav>
    </div>
  </header>

  <main>
    <section class="hero container">
      <h1>Apple Inc. (AAPL) — Interactive Analysis</h1>
      <p class="muted">Minimalist design featuring a live TradingView chart and an interactive revenue graph (Chart.js).</p>
      <div class="row">
        <a href="#live-chart" class="btn primary">Open live graph</a>
        <a href="#financials" class="btn">Revenue & KPI</a>
      </div>
    </section>

    <section class="kpis container">
      <div class="card"><div class="k">Market Cap</div><div class="v">$3.0T (live)</div></div>
      <div class="card"><div class="k">P/E (TTM)</div><div class="v">~30.3</div></div>
      <div class="card"><div class="k">EPS (TTM)</div><div class="v">6.59</div></div>
      <div class="card"><div class="k">5Y CAGR (Revenue)</div><div class="v">~7–8%</div></div>
    </section>

    <section id="live-chart" class="container section">
      <h2>Live Stock Chart</h2>
      <p class="muted">Advanced TradingView — switch intervals, add indicators, compare symbols.</p>
      <div class="embed rounded"><div id="tradingview_container" style="height:560px;"></div></div>
      <script src="https://s3.tradingview.com/tv.js"></script>
      <script>
        new TradingView.widget({
          "width":"100%","height":560,"symbol":"NASDAQ:AAPL","interval":"D",
          "timezone":"Etc/UTC","theme":"dark","style":"1","locale":"en",
          "withdateranges":true,"allow_symbol_change":true,"details":true,
          "container_id":"tradingview_container"
        });
      </script>
    </section>

    <section id="financials" class="container section">
      <h2>Revenue & Financials</h2>
      <p class="muted">Interactive revenue chart of Apple (in billions of USD) — data aggregated by years.</p>

      <div class="revenue-wrap">
        <canvas id="appleRevenueChart"></canvas>
      </div>

      <div class="grid-2" style="margin-top:16px">
        <div class="card">
          <div class="k small">Methodology</div>
          <p class="muted small">Annual revenue (FY), in billions of USD. Sources: Apple reports (10-K / IR). Values may slightly differ from aggregators due to rounding.</p>
        </div>
        <div class="card">
          <div class="k small">Note</div>
          <p class="muted small">Despite market fluctuations, Apple’s long-term growth remains consistent, supported by strong brand loyalty and high-margin service segments.</p>
        </div>
      </div>
    </section>

    <section id="sources" class="container section">
      <h2>Sources & Disclosures</h2>
      <ul class="muted">
        <li>
          Companiesmarketcap — 
          <a href="https://investor.apple.com/financials/default.aspx" target="_blank" class="muted" style="color:#38bdf8; text-decoration:none;">
            Annual Reports
          </a>
        </li>
        <li>
          TradingView — 
          <a href="https://www.tradingview.com/symbols/NASDAQ-AAPL/" target="_blank" class="muted" style="color:#38bdf8; text-decoration:none;">
            Market prices
          </a>
        </li>
        <li>
          SEC EDGAR — 
          <a href="https://www.sec.gov/edgar/browse/?CIK=0000320193" target="_blank" class="muted" style="color:#38bdf8; text-decoration:none;">
            Reports archive
          </a>
        </li>
      </ul>
      
      <p class="small muted">Educational material; not intended as investment advice.
      </p>
    </section>
  </main>

  <footer class="footer">
    <div class="container row between center">
      <span class="muted small">
        © <span id="year"></span> 
        <a href="https://www.linkedin.com/in/bogdan-burduja-33b064317/" 
           target="_blank" 
           style="color:#38bdf8; text-decoration:none; font-weight:600;">
          Bogdan Burduja
        </a>
        — Analysis Template
      </span>
      
      <a href="#live-chart" class="btn ghost">Back up ↑</a>
    </div>
  </footer>

  <script>document.getElementById('year').textContent=new Date().getFullYear();</script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    const revYears = ['2000','2005','2010','2015','2018','2019','2020','2021','2022','2023','2024','2025'];
    const revData  = [8,14,65,233,265,260,274,365,394,383,385,409];
    const rctx = document.getElementById('appleRevenueChart');
    new Chart(rctx, {
      type: 'bar',
      data: { labels: revYears, datasets: [{
        label: 'Revenue (Billion USD)',
        data: revData,
        backgroundColor: 'rgba(0,255,132,.20)',
        borderColor: '#00ff84',
        borderWidth: 2,
        borderRadius: 6,
        barPercentage: 0.7,
        categoryPercentage: 0.8
      }]},
      options: {
        maintainAspectRatio: false,
        layout: { padding: { top: 6, right: 10, bottom: 6, left: 10 } },
        scales: {
          x: { ticks: { color: '#bbb' }, grid: { color: '#1f1f28' } },
          y: { beginAtZero: true, suggestedMax: 420,
               ticks: { color: '#bbb', callback: v => '$' + v + 'B' },
               grid: { color: '#1f1f28' } }
        },
        plugins: {
          legend: { position: 'top', labels: { color: '#fff', boxWidth: 10 } },
          tooltip: { callbacks: { label: (c) => 'Revenue: $' + c.raw + 'B' } }
        },
        animation: { duration: 500 }
      }
    });
  </script>
</body>
</html>
