[index (2).html](https://github.com/user-attachments/files/33186932/index.2.html)
# Statistical-Analysis-and-data-visualization-Lab
Projects and practice files 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Educational undergraduate AIML laboratory web application for discrete probability distributions." />
  <title>Discrete Probability Distributions</title>
  <style>
    :root {
      --bg: #f6f8fb;
      --surface: #ffffff;
      --surface-2: #f8fafc;
      --text: #172033;
      --muted: #667085;
      --border: #e4e7ec;
      --primary: #4f46e5;
      --primary-soft: #eef2ff;
      --success: #067647;
      --success-soft: #ecfdf3;
      --danger: #b42318;
      --danger-soft: #fef3f2;
      --warning: #b54708;
      --warning-soft: #fffaeb;
      --shadow: 0 10px 30px rgba(16, 24, 40, .06);
      --radius: 16px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      color: var(--text);
      background: var(--bg);
      line-height: 1.6;
    }
    a { color: inherit; text-decoration: none; }
    button, input { font: inherit; }
    button { cursor: pointer; }

    .container { width: min(1120px, calc(100% - 32px)); margin: 0 auto; }

    .site-header {
      position: sticky;
      top: 0;
      z-index: 20;
      background: rgba(255,255,255,.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }
    .header-inner {
      min-height: 72px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
    }
    .brand-wrap { display: flex; align-items: center; gap: 12px; }
    .brand-mark {
      width: 38px; height: 38px; border-radius: 11px;
      display: grid; place-items: center;
      background: var(--primary); color: white; font-weight: 800;
      box-shadow: 0 8px 20px rgba(79,70,229,.2);
    }
    .brand-title { font-weight: 800; letter-spacing: -.02em; }
    .brand-subtitle { font-size: .78rem; color: var(--muted); }

    nav { display: flex; flex-wrap: wrap; gap: 6px; }
    nav a {
      padding: 9px 13px;
      border-radius: 10px;
      color: var(--muted);
      font-size: .94rem;
      font-weight: 650;
    }
    nav a:hover, nav a.active { background: var(--primary-soft); color: var(--primary); }

    main { padding: 38px 0 72px; }
    .page { display: none; }
    .page.active { display: block; }

    .hero {
      background: linear-gradient(135deg, #ffffff, #f8faff);
      border: 1px solid var(--border);
      border-radius: 24px;
      padding: clamp(30px, 6vw, 58px);
      box-shadow: var(--shadow);
    }
    .eyebrow {
      margin: 0 0 8px;
      color: var(--primary);
      font-size: .78rem;
      font-weight: 800;
      letter-spacing: .1em;
      text-transform: uppercase;
    }
    h1, h2, h3, p { margin-top: 0; }
    h1 { font-size: clamp(2.1rem, 5vw, 3.7rem); line-height: 1.05; letter-spacing: -.045em; margin-bottom: 16px; }
    h2 { font-size: clamp(1.55rem, 2.8vw, 2.15rem); line-height: 1.15; letter-spacing: -.035em; }
    h3 { font-size: 1.04rem; }
    .lead { max-width: 760px; color: var(--muted); font-size: 1.06rem; margin-bottom: 0; }

    .module-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; margin-top: 22px; }
    .module-card {
      background: var(--surface); border: 1px solid var(--border); border-radius: 16px;
      padding: 24px; min-height: 206px; display: flex; flex-direction: column;
      box-shadow: 0 3px 15px rgba(16,24,40,.03);
    }
    .module-card:hover { transform: translateY(-2px); transition: 160ms ease; }
    .module-icon { width: 42px; height: 42px; border-radius: 12px; display: grid; place-items: center; background: var(--primary-soft); color: var(--primary); font-weight: 800; margin-bottom: 18px; }
    .module-card p { color: var(--muted); font-size: .94rem; }
    .module-card .action { margin-top: auto; color: var(--primary); font-weight: 700; font-size: .92rem; }
    .coming { color: var(--muted) !important; font-size: .9rem !important; }

    .section-top { margin-bottom: 22px; }
    .section-top p { color: var(--muted); max-width: 780px; }
    .pill {
      display: inline-flex; align-items: center; gap: 7px; padding: 7px 11px;
      border-radius: 999px; background: var(--primary-soft); color: var(--primary);
      font-size: .78rem; font-weight: 800; margin-bottom: 10px;
    }

    .card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      box-shadow: 0 3px 16px rgba(16,24,40,.03);
      padding: 24px;
    }
    .inputs-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
    .inputs-grid.two { grid-template-columns: repeat(2, 1fr); }
    .field { display: flex; flex-direction: column; gap: 7px; }
    .field label { font-weight: 750; font-size: .9rem; }
    .field small { color: var(--muted); font-weight: 500; }
    input[type="number"] {
      width: 100%; border: 1px solid #d0d5dd; border-radius: 10px;
      background: #fff; color: var(--text); padding: 12px 13px; outline: none;
      transition: border-color .15s, box-shadow .15s;
    }
    input[type="number"]:focus { border-color: var(--primary); box-shadow: 0 0 0 3px rgba(79,70,229,.1); }
    input.invalid { border-color: var(--danger); box-shadow: 0 0 0 3px rgba(180,35,24,.08); }
    .error { color: var(--danger); font-size: .82rem; min-height: 20px; }

    .selected {
      margin-top: 18px; padding: 14px 16px; border-radius: 11px;
      background: var(--surface-2); border: 1px solid var(--border);
      display: flex; gap: 14px; flex-wrap: wrap; align-items: center;
    }
    .selected strong { color: var(--primary); }

    .stats-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 12px; margin-top: 18px; }
    .stat {
      padding: 16px; border: 1px solid var(--border); border-radius: 13px;
      background: #fff; min-height: 106px;
    }
    .stat .label { font-size: .8rem; color: var(--muted); font-weight: 700; }
    .stat .value { margin-top: 6px; font-size: 1.32rem; font-weight: 800; letter-spacing: -.025em; }

    .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; margin-top: 18px; }
    .result-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
    .result-card { border: 1px solid var(--border); background: var(--surface-2); border-radius: 13px; padding: 17px; }
    .result-card .result-label { color: var(--muted); font-size: .84rem; font-weight: 750; }
    .result-card .result-number { margin-top: 6px; font-size: 1.55rem; font-weight: 850; letter-spacing: -.03em; }
    .result-card .percentage { color: var(--muted); font-size: .86rem; margin-top: 2px; }

    .formula { padding: 16px; border-radius: 12px; background: #0f172a; color: #fff; overflow-x: auto; font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace; font-size: .92rem; margin-top: 14px; }
    .subtle-note { color: var(--muted); font-size: .88rem; margin: 12px 0 0; }
    .meaning { margin: 14px 0 0; padding: 13px 15px; border-left: 3px solid var(--primary); background: var(--primary-soft); border-radius: 8px; font-size: .92rem; }

    .chart-card { margin-top: 18px; }
    .chart-head { display: flex; align-items: baseline; justify-content: space-between; gap: 16px; margin-bottom: 10px; }
    .chart-wrap { position: relative; width: 100%; height: 370px; }
    canvas { width: 100%; height: 100%; display: block; }
    .legend { color: var(--muted); font-size: .84rem; }
    .tooltip {
      position: absolute; display: none; pointer-events: none;
      background: rgba(15, 23, 42, .96); color: white;
      border-radius: 9px; padding: 9px 11px; font-size: .82rem;
      box-shadow: 0 8px 24px rgba(0,0,0,.16); white-space: nowrap;
      z-index: 5;
    }

    .verified { margin-top: 18px; padding: 13px 15px; border-radius: 11px; background: var(--success-soft); border: 1px solid #abefc6; color: var(--success); font-size: .9rem; font-weight: 700; }
    .info-banner { margin-top: 18px; padding: 13px 15px; border-radius: 11px; background: var(--warning-soft); border: 1px solid #fedf89; color: #93370d; font-size: .88rem; }

    footer { padding: 22px 0 40px; color: var(--muted); font-size: .82rem; text-align: center; }

    @media (max-width: 900px) {
      .module-grid { grid-template-columns: 1fr; }
      .stats-grid { grid-template-columns: repeat(2, 1fr); }
      .inputs-grid, .inputs-grid.two, .two-col { grid-template-columns: 1fr; }
    }
    @media (max-width: 640px) {
      .container { width: min(100% - 22px, 1120px); }
      .header-inner { align-items: flex-start; flex-direction: column; padding: 12px 0; }
      nav { width: 100%; }
      nav a { flex: 1 1 auto; text-align: center; }
      main { padding-top: 22px; }
      .hero { padding: 28px 22px; border-radius: 18px; }
      .card { padding: 19px; }
      .stats-grid, .result-grid { grid-template-columns: 1fr; }
      .chart-wrap { height: 300px; }
    }
  </style>
</head>
<body>
  <header class="site-header">
    <div class="container header-inner">
      <a href="#home" class="brand-wrap" data-page="home" aria-label="Go to home">
        <div class="brand-mark">P</div>
        <div>
          <div class="brand-title">Discrete Probability Distributions</div>
          <div class="brand-subtitle">Undergraduate AIML Laboratory</div>
        </div>
      </a>
      <nav aria-label="Primary navigation">
        <a href="#home" data-page="home">Home</a>
        <a href="#binomial" data-page="binomial">Binomial</a>
        <a href="#poisson" data-page="poisson">Poisson</a>
        <a href="#geometric" data-page="geometric">Geometric</a>
      </nav>
    </div>
  </header>

  <main class="container">
    <section id="home" class="page active">
      <div class="hero">
        <p class="eyebrow">Probability Laboratory</p>
        <h1>Discrete Probability Distributions</h1>
        <p class="lead">A simple interactive learning tool for understanding common discrete probability distributions through formulas, calculations, and visualizations.</p>
      </div>

      <div class="module-grid">
        <div class="module-card">
          <div class="module-icon">B</div>
          <h3>Binomial Distribution</h3>
          <p>Study repeated trials with two possible outcomes using n, p, and k.</p>
          <a class="action" href="#binomial" data-page="binomial">Open module →</a>
        </div>
        <div class="module-card">
          <div class="module-icon">P</div>
          <h3>Poisson Distribution</h3>
          <p>Study the number of events occurring in a fixed interval using the Poisson rate λ.</p>
          <a class="action" href="#poisson" data-page="poisson">Open module →</a>
        </div>
        <div class="module-card">
          <div class="module-icon">G</div>
          <h3>Geometric Distribution</h3>
          <p>Study the number of trials until the first success using p and k.</p>
          <a class="action" href="#geometric" data-page="geometric">Open module →</a>
        </div>
      </div>
    </section>

    <section id="binomial" class="page">
      <div class="section-top">
        <span class="pill">Module 1 · Binomial</span>
        <h2>Binomial Distribution</h2>
        <p>For <strong>X ~ Binomial(n,p)</strong>, use the controls below to explore the distribution, calculate point and cumulative probabilities, and view the PMF.</p>
      </div>

      <div class="card">
        <h3>1. Inputs</h3>
        <div class="inputs-grid">
          <div class="field">
            <label for="b-n">Number of trials n</label>
            <input id="b-n" type="number" value="20" min="1" step="1" inputmode="numeric" />
            <small>n must be a positive integer.</small>
            <div id="b-n-error" class="error"></div>
          </div>
          <div class="field">
            <label for="b-p">Probability of success p</label>
            <input id="b-p" type="number" value="0.35" min="0" max="1" step="0.01" inputmode="decimal" />
            <small>p must be between 0 and 1.</small>
            <div id="b-p-error" class="error"></div>
          </div>
          <div class="field">
            <label for="b-k">Number of successes k</label>
            <input id="b-k" type="number" value="7" min="0" step="1" inputmode="numeric" />
            <small>0 ≤ k ≤ n.</small>
            <div id="b-k-error" class="error"></div>
          </div>
        </div>
        <div class="selected" id="b-selected"></div>
      </div>

      <div class="stats-grid">
        <div class="stat"><div class="label">Mean</div><div class="value" id="b-mean">—</div></div>
        <div class="stat"><div class="label">Variance</div><div class="value" id="b-variance">—</div></div>
        <div class="stat"><div class="label">Standard deviation</div><div class="value" id="b-sd">—</div></div>
        <div class="stat"><div class="label">Second moment E[X²]</div><div class="value" id="b-second">—</div></div>
        <div class="stat"><div class="label">Skewness</div><div class="value" id="b-skew">—</div></div>
      </div>

      <div id="b-verified" class="verified"></div>

      <div class="two-col">
        <div class="card">
          <h3>2. PMF Calculator</h3>
          <p class="subtle-note">Calculate the probability of exactly k successes.</p>
          <div class="formula">P(X = k) = C(n,k) · p<sup>k</sup> · (1-p)<sup>(n-k)</sup></div>
          <div class="formula" id="b-pmf-sub"></div>
          <div class="result-card" style="margin-top:14px">
            <div class="result-label">P(X = k)</div>
            <div class="result-number" id="b-pmf">—</div>
            <div class="percentage" id="b-pmf-pct">—</div>
          </div>
          <div class="meaning">This is the probability of getting exactly k successes in n trials.</div>
        </div>

        <div class="card">
          <h3>3. CDF Calculator</h3>
          <p class="subtle-note">Use the same k value to calculate the cumulative probability.</p>
          <div class="result-grid">
            <div class="result-card">
              <div class="result-label">P(X ≤ k)</div>
              <div class="result-number" id="b-cdf">—</div>
              <div class="percentage" id="b-cdf-pct">—</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(X &gt; k)</div>
              <div class="result-number" id="b-tail">—</div>
              <div class="percentage" id="b-tail-pct">—</div>
            </div>
          </div>
          <div class="formula">P(X &gt; k) = 1 - P(X ≤ k)</div>
          <div class="meaning">P(X ≤ k) means the probability of getting k or fewer successes.</div>
        </div>
      </div>

      <div class="card chart-card">
        <div class="chart-head">
          <div>
            <h3 style="margin-bottom:4px">4. Binomial PMF</h3>
            <div class="legend">X-axis: Number of successes X · Y-axis: Probability P(X) · Dashed line: mean</div>
          </div>
          <span class="legend" id="b-chart-summary"></span>
        </div>
        <div class="chart-wrap">
          <canvas id="b-chart"></canvas>
          <div id="b-tooltip" class="tooltip"></div>
        </div>
      </div>
    </section>

    <section id="poisson" class="page">
      <div class="section-top">
        <span class="pill">Module 2 · Poisson</span>
        <h2>Poisson Distribution</h2>
        <p>For <strong>X ~ Poisson(λ)</strong>, use the controls below to calculate probabilities, study the distribution statistics, and view the PMF.</p>
      </div>

      <div class="card">
        <h3>1. Inputs</h3>
        <div class="inputs-grid two">
          <div class="field">
            <label for="p-lambda">Average rate λ</label>
            <input id="p-lambda" type="number" value="4" min="0.0001" step="0.1" inputmode="decimal" />
            <small>λ must be greater than 0.</small>
            <div id="p-lambda-error" class="error"></div>
          </div>
          <div class="field">
            <label for="p-k">Number of events k</label>
            <input id="p-k" type="number" value="4" min="0" step="1" inputmode="numeric" />
            <small>k must be a non-negative integer.</small>
            <div id="p-k-error" class="error"></div>
          </div>
        </div>
        <div class="selected" id="p-selected"></div>
      </div>

      <div class="stats-grid">
        <div class="stat"><div class="label">Mean</div><div class="value" id="p-mean">—</div></div>
        <div class="stat"><div class="label">Variance</div><div class="value" id="p-variance">—</div></div>
        <div class="stat"><div class="label">Standard deviation</div><div class="value" id="p-sd">—</div></div>
        <div class="stat"><div class="label">Second moment E[X²]</div><div class="value" id="p-second">—</div></div>
        <div class="stat"><div class="label">Skewness</div><div class="value" id="p-skew">—</div></div>
      </div>

      <div class="verified" id="p-verified">For a Poisson distribution, the mean and variance are both λ.</div>

      <div class="two-col">
        <div class="card">
          <h3>2. PMF Calculator</h3>
          <p class="subtle-note">Calculate the probability of exactly k events.</p>
          <div class="formula">P(X = k) = e<sup>-λ</sup> λ<sup>k</sup> / k!</div>
          <div class="formula" id="p-pmf-sub"></div>
          <div class="result-card" style="margin-top:14px">
            <div class="result-label">P(X = k)</div>
            <div class="result-number" id="p-pmf">—</div>
            <div class="percentage" id="p-pmf-pct">—</div>
          </div>
          <div class="meaning">This is the probability of observing exactly k events when the average rate is λ.</div>
        </div>

        <div class="card">
          <h3>3. CDF Calculator</h3>
          <p class="subtle-note">Use the same k value to calculate the cumulative probability.</p>
          <div class="result-grid">
            <div class="result-card">
              <div class="result-label">P(X ≤ k)</div>
              <div class="result-number" id="p-cdf">—</div>
              <div class="percentage" id="p-cdf-pct">—</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(X &gt; k)</div>
              <div class="result-number" id="p-tail">—</div>
              <div class="percentage" id="p-tail-pct">—</div>
            </div>
          </div>
          <div class="formula">P(X &gt; k) = 1 - P(X ≤ k)</div>
          <div class="meaning">P(X ≤ k) means the probability of observing k or fewer events.</div>
        </div>
      </div>

      <div class="card chart-card">
        <div class="chart-head">
          <div>
            <h3 style="margin-bottom:4px">4. Poisson PMF</h3>
            <div class="legend">X-axis: Number of events X · Y-axis: Probability P(X) · Dashed line: mean</div>
          </div>
          <span class="legend" id="p-chart-summary"></span>
        </div>
        <div class="chart-wrap">
          <canvas id="p-chart"></canvas>
          <div id="p-tooltip" class="tooltip"></div>
        </div>
      </div>

      <div class="info-banner">Poisson distribution is used to model the number of times an event occurs in a fixed interval when the average rate λ is known.</div>
    </section>

    <section id="geometric" class="page">
      <div class="section-top">
        <span class="pill">Module 3 · Geometric</span>
        <h2>Geometric Distribution</h2>
        <p>For <strong>X ~ Geometric(p)</strong>, X is the number of trials needed to get the first success.</p>
      </div>

      <div class="card">
        <h3>1. Inputs</h3>
        <div class="inputs-grid two">
          <div class="field">
            <label for="g-p">Probability of success p</label>
            <input id="g-p" type="number" value="0.35" min="0.0001" max="1" step="0.01" inputmode="decimal" />
            <small>p must be greater than 0 and at most 1.</small>
            <div id="g-p-error" class="error"></div>
          </div>
          <div class="field">
            <label for="g-k">Number of trials k</label>
            <input id="g-k" type="number" value="3" min="1" step="1" inputmode="numeric" />
            <small>k must be a positive integer (k ≥ 1).</small>
            <div id="g-k-error" class="error"></div>
          </div>
        </div>
        <div class="selected" id="g-selected"></div>
      </div>

      <div class="stats-grid">
        <div class="stat"><div class="label">Mean</div><div class="value" id="g-mean">—</div></div>
        <div class="stat"><div class="label">Variance</div><div class="value" id="g-variance">—</div></div>
        <div class="stat"><div class="label">Standard deviation</div><div class="value" id="g-sd">—</div></div>
        <div class="stat"><div class="label">Second moment E[X²]</div><div class="value" id="g-second">—</div></div>
        <div class="stat"><div class="label">Skewness</div><div class="value" id="g-skew">—</div></div>
      </div>

      <div class="verified" id="g-verified"></div>

      <div class="two-col">
        <div class="card">
          <h3>2. PMF Calculator</h3>
          <p class="subtle-note">Calculate the probability that the first success occurs on trial k.</p>
          <div class="formula">P(X = k) = p · (1-p)<sup>(k-1)</sup></div>
          <div class="formula" id="g-pmf-sub"></div>
          <div class="result-card" style="margin-top:14px">
            <div class="result-label">P(X = k)</div>
            <div class="result-number" id="g-pmf">—</div>
            <div class="percentage" id="g-pmf-pct">—</div>
          </div>
          <div class="meaning">This is the probability that the first success occurs exactly on trial k.</div>
        </div>

        <div class="card">
          <h3>3. CDF Calculator</h3>
          <p class="subtle-note">Use the same k value to calculate the cumulative probability.</p>
          <div class="result-grid">
            <div class="result-card">
              <div class="result-label">P(X ≤ k)</div>
              <div class="result-number" id="g-cdf">—</div>
              <div class="percentage" id="g-cdf-pct">—</div>
            </div>
            <div class="result-card">
              <div class="result-label">P(X &gt; k)</div>
              <div class="result-number" id="g-tail">—</div>
              <div class="percentage" id="g-tail-pct">—</div>
            </div>
          </div>
          <div class="formula">P(X ≤ k) = 1 - (1-p)<sup>k</sup></div>
          <div class="formula">P(X &gt; k) = (1-p)<sup>k</sup></div>
          <div class="meaning">P(X ≤ k) means the probability of getting the first success on trial k or earlier.</div>
        </div>
      </div>

      <div class="card chart-card">
        <div class="chart-head">
          <div>
            <h3 style="margin-bottom:4px">4. Geometric PMF</h3>
            <div class="legend">X-axis: Trial number X · Y-axis: Probability P(X) · Dashed line: mean</div>
          </div>
          <span class="legend" id="g-chart-summary"></span>
        </div>
        <div class="chart-wrap">
          <canvas id="g-chart"></canvas>
          <div id="g-tooltip" class="tooltip"></div>
        </div>
      </div>

      <div class="info-banner">The geometric distribution models the number of independent trials needed to get the first success.</div>
    </section>
  </main>

  <footer>Discrete Probability Distributions · Undergraduate AIML Laboratory</footer>

  <script>
    function factorial(n) {
      if (n < 0 || !Number.isInteger(n)) return NaN;
      let result = 1;
      for (let i = 2; i <= n; i++) result *= i;
      return result;
    }

    function combination(n, k) {
      if (!Number.isInteger(n) || !Number.isInteger(k) || k < 0 || k > n) return 0;
      k = Math.min(k, n - k);
      let result = 1;
      for (let i = 1; i <= k; i++) result = result * (n - k + i) / i;
      return result;
    }

    // -------------------- Binomial: kept as before --------------------
    function pmf(n, p, k) {
      if (k < 0 || k > n || !Number.isInteger(k)) return 0;
      return combination(n, k) * Math.pow(p, k) * Math.pow(1 - p, n - k);
    }

    function cdf(n, p, k) {
      let total = 0;
      for (let x = 0; x <= k; x++) total += pmf(n, p, x);
      return Math.min(1, Math.max(0, total));
    }

    function formatNumber(value, digits = 6) {
      if (!Number.isFinite(value)) return '—';
      return value.toFixed(digits).replace(/\.?0+$/, '');
    }

    function formatPercent(value) {
      if (!Number.isFinite(value)) return '—';
      return (value * 100).toFixed(4).replace(/\.?0+$/, '') + '%';
    }

    function setText(id, value) { document.getElementById(id).textContent = value; }

    function validateBinomialInputs() {
      const nEl = document.getElementById('b-n');
      const pEl = document.getElementById('b-p');
      const kEl = document.getElementById('b-k');
      const nErr = document.getElementById('b-n-error');
      const pErr = document.getElementById('b-p-error');
      const kErr = document.getElementById('b-k-error');
      nErr.textContent = pErr.textContent = kErr.textContent = '';
      [nEl,pEl,kEl].forEach(el => el.classList.remove('invalid'));

      const n = Number(nEl.value), p = Number(pEl.value), k = Number(kEl.value);
      let valid = true;
      if (!Number.isInteger(n) || n <= 0) { nErr.textContent = 'Enter a positive integer.'; nEl.classList.add('invalid'); valid = false; }
      if (!Number.isFinite(p) || p < 0 || p > 1) { pErr.textContent = 'Enter a value from 0 to 1.'; pEl.classList.add('invalid'); valid = false; }
      if (!Number.isInteger(k) || k < 0 || (Number.isInteger(n) && k > n)) { kErr.textContent = 'Enter an integer with 0 ≤ k ≤ n.'; kEl.classList.add('invalid'); valid = false; }
      return { valid, n, p, k };
    }

    function updateBinomial() {
      const { valid, n, p, k } = validateBinomialInputs();
      if (!valid) {
        setText('b-selected', 'Please correct the highlighted inputs.');
        ['mean','variance','sd','second','skew','pmf','cdf','tail','pmf-pct','cdf-pct','tail-pct'].forEach(key => {
          const node = document.getElementById('b-' + key); if (node) node.textContent = '—';
        });
        setText('b-verified', '');
        drawChart('b-chart', 'b-tooltip', 0, 0, [], 'Number of successes X');
        return;
      }

      const mean = n * p;
      const variance = n * p * (1 - p);
      const sd = Math.sqrt(variance);
      const second = variance + mean * mean;
      const skew = variance > 0 ? (1 - 2 * p) / Math.sqrt(variance) : 0;
      const prob = pmf(n, p, k);
      const cumulative = cdf(n, p, k);
      const tail = Math.max(0, 1 - cumulative);

      setText('b-selected', `Selected values: n = ${n}, p = ${p}, k = ${k}`);
      setText('b-mean', formatNumber(mean));
      setText('b-variance', formatNumber(variance));
      setText('b-sd', formatNumber(sd));
      setText('b-second', formatNumber(second));
      setText('b-skew', formatNumber(skew));
      setText('b-pmf', formatNumber(prob, 8));
      setText('b-pmf-pct', formatPercent(prob));
      setText('b-cdf', formatNumber(cumulative, 8));
      setText('b-cdf-pct', formatPercent(cumulative));
      setText('b-tail', formatNumber(tail, 8));
      setText('b-tail-pct', formatPercent(tail));
      setText('b-pmf-sub', `P(X=${k}) = C(${n},${k}) · (${p})^${k} · (${1-p})^${n-k} = ${formatNumber(prob, 8)}`);
      setText('b-verified', `Default-value check: for n = 20 and p = 0.35, Mean = ${formatNumber(20 * 0.35)} and Variance = ${formatNumber(20 * 0.35 * 0.65)}.`);

      const values = Array.from({length: n + 1}, (_, x) => pmf(n, p, x));
      setText('b-chart-summary', `n = ${n}, p = ${p}, mean = ${formatNumber(mean)}`);
      drawChart('b-chart', 'b-tooltip', n, mean, values, 'Number of successes X');
    }

    // -------------------- Poisson: rebuilt correctly --------------------
    function poissonPmf(lambda, k) {
      if (lambda < 0 || k < 0 || !Number.isInteger(k)) return 0;
      if (lambda === 0) return k === 0 ? 1 : 0;
      return Math.exp(-lambda) * Math.pow(lambda, k) / factorial(k);
    }

    function poissonCdf(lambda, k) {
      let total = 0;
      for (let x = 0; x <= k; x++) total += poissonPmf(lambda, x);
      return Math.min(1, Math.max(0, total));
    }

    function validatePoissonInputs() {
      const lambdaEl = document.getElementById('p-lambda');
      const kEl = document.getElementById('p-k');
      const lambdaErr = document.getElementById('p-lambda-error');
      const kErr = document.getElementById('p-k-error');
      lambdaErr.textContent = kErr.textContent = '';
      [lambdaEl, kEl].forEach(el => el.classList.remove('invalid'));

      const lambda = Number(lambdaEl.value), k = Number(kEl.value);
      let valid = true;
      if (!Number.isFinite(lambda) || lambda <= 0) {
        lambdaErr.textContent = 'Enter a value greater than 0.';
        lambdaEl.classList.add('invalid');
        valid = false;
      }
      if (!Number.isInteger(k) || k < 0) {
        kErr.textContent = 'Enter a non-negative integer.';
        kEl.classList.add('invalid');
        valid = false;
      }
      return { valid, lambda, k };
    }

    function updatePoisson() {
      const { valid, lambda, k } = validatePoissonInputs();
      if (!valid) {
        setText('p-selected', 'Please correct the highlighted inputs.');
        ['mean','variance','sd','second','skew','pmf','cdf','tail','pmf-pct','cdf-pct','tail-pct'].forEach(key => {
          const node = document.getElementById('p-' + key); if (node) node.textContent = '—';
        });
        setText('p-pmf-sub', '');
        setText('p-verified', '');
        setText('p-chart-summary', '');
        drawChart('p-chart', 'p-tooltip', 0, 0, [], 'Number of events X');
        return;
      }

      const mean = lambda;
      const variance = lambda;
      const sd = Math.sqrt(lambda);
      const second = lambda + lambda * lambda;
      const skew = 1 / Math.sqrt(lambda);
      const prob = poissonPmf(lambda, k);
      const cumulative = poissonCdf(lambda, k);
      const tail = Math.max(0, 1 - cumulative);

      setText('p-selected', `Selected values: λ = ${formatNumber(lambda)}, k = ${k}`);
      setText('p-mean', formatNumber(mean));
      setText('p-variance', formatNumber(variance));
      setText('p-sd', formatNumber(sd));
      setText('p-second', formatNumber(second));
      setText('p-skew', formatNumber(skew));
      setText('p-pmf', formatNumber(prob, 8));
      setText('p-pmf-pct', formatPercent(prob));
      setText('p-cdf', formatNumber(cumulative, 8));
      setText('p-cdf-pct', formatPercent(cumulative));
      setText('p-tail', formatNumber(tail, 8));
      setText('p-tail-pct', formatPercent(tail));
      setText('p-pmf-sub', `P(X=${k}) = e^(-${formatNumber(lambda)}) · (${formatNumber(lambda)})^${k} / ${k}! = ${formatNumber(prob, 8)}`);
      setText('p-verified', `Poisson check: for λ = ${formatNumber(lambda)}, Mean = Variance = ${formatNumber(lambda)}.`);

      const chartMax = Math.max(10, Math.ceil(lambda + 6 * Math.sqrt(lambda)), k + 3);
      const values = Array.from({length: chartMax + 1}, (_, x) => poissonPmf(lambda, x));
      setText('p-chart-summary', `λ = ${formatNumber(lambda)}, mean = ${formatNumber(mean)}`);
      drawChart('p-chart', 'p-tooltip', chartMax, mean, values, 'Number of events X');
    }

    // -------------------- Geometric --------------------
    function geometricPmf(p, k) {
      if (!(p > 0 && p <= 1) || k < 1 || !Number.isInteger(k)) return 0;
      return p * Math.pow(1 - p, k - 1);
    }

    function geometricCdf(p, k) {
      if (!(p > 0 && p <= 1) || k < 1 || !Number.isInteger(k)) return 0;
      return 1 - Math.pow(1 - p, k);
    }

    function validateGeometricInputs() {
      const pEl = document.getElementById('g-p');
      const kEl = document.getElementById('g-k');
      const pErr = document.getElementById('g-p-error');
      const kErr = document.getElementById('g-k-error');
      pErr.textContent = kErr.textContent = '';
      [pEl, kEl].forEach(el => el.classList.remove('invalid'));

      const prob = Number(pEl.value), k = Number(kEl.value);
      let valid = true;
      if (!Number.isFinite(prob) || prob <= 0 || prob > 1) {
        pErr.textContent = 'Enter a value greater than 0 and at most 1.';
        pEl.classList.add('invalid');
        valid = false;
      }
      if (!Number.isInteger(k) || k < 1) {
        kErr.textContent = 'Enter a positive integer (k ≥ 1).';
        kEl.classList.add('invalid');
        valid = false;
      }
      return { valid, p: prob, k };
    }

    function updateGeometric() {
      const { valid, p, k } = validateGeometricInputs();
      if (!valid) {
        setText('g-selected', 'Please correct the highlighted inputs.');
        ['mean','variance','sd','second','skew','pmf','cdf','tail','pmf-pct','cdf-pct','tail-pct'].forEach(key => {
          const node = document.getElementById('g-' + key); if (node) node.textContent = '—';
        });
        setText('g-pmf-sub', '');
        setText('g-verified', '');
        setText('g-chart-summary', '');
        drawGeometricChart('g-chart', 'g-tooltip', 0, 0, [], 1);
        return;
      }

      const mean = 1 / p;
      const variance = (1 - p) / (p * p);
      const sd = Math.sqrt(variance);
      const second = (2 - p) / (p * p);
      const skew = p < 1 ? (2 - p) / Math.sqrt(1 - p) : 0;
      const prob = geometricPmf(p, k);
      const cumulative = geometricCdf(p, k);
      const tail = Math.max(0, 1 - cumulative);

      setText('g-selected', `Selected values: p = ${formatNumber(p)}, k = ${k}`);
      setText('g-mean', formatNumber(mean));
      setText('g-variance', formatNumber(variance));
      setText('g-sd', formatNumber(sd));
      setText('g-second', formatNumber(second));
      setText('g-skew', formatNumber(skew));
      setText('g-pmf', formatNumber(prob, 8));
      setText('g-pmf-pct', formatPercent(prob));
      setText('g-cdf', formatNumber(cumulative, 8));
      setText('g-cdf-pct', formatPercent(cumulative));
      setText('g-tail', formatNumber(tail, 8));
      setText('g-tail-pct', formatPercent(tail));
      setText('g-pmf-sub', `P(X=${k}) = (${formatNumber(p)}) · (1-${formatNumber(p)})^${k-1} = ${formatNumber(prob, 8)}`);
      setText('g-verified', `Geometric check: with p = ${formatNumber(p)}, Mean = 1/p = ${formatNumber(mean)} and Variance = (1-p)/p² = ${formatNumber(variance)}.`);

      const chartMax = Math.max(12, Math.ceil(mean + 4 * sd), k + 4);
      const values = Array.from({length: chartMax}, (_, i) => geometricPmf(p, i + 1));
      setText('g-chart-summary', `p = ${formatNumber(p)}, mean = ${formatNumber(mean)}`);
      drawGeometricChart('g-chart', 'g-tooltip', chartMax, mean, values, 1);
    }

    function drawGeometricChart(canvasId, tooltipId, maxX, mean, values, startX) {
      const canvas = document.getElementById(canvasId);
      if (!canvas) return;
      const wrap = canvas.parentElement;
      const rect = wrap.getBoundingClientRect();
      const dpr = Math.max(1, window.devicePixelRatio || 1);
      const width = Math.max(320, rect.width);
      const height = Math.max(250, rect.height);
      canvas.width = Math.floor(width * dpr);
      canvas.height = Math.floor(height * dpr);
      canvas.style.width = width + 'px'; canvas.style.height = height + 'px';
      const ctx = canvas.getContext('2d');
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
      ctx.clearRect(0, 0, width, height);
      if (!values.length) return;

      const pad = {left: 58, right: 22, top: 20, bottom: 48};
      const plotW = width - pad.left - pad.right;
      const plotH = height - pad.top - pad.bottom;
      const maxY = Math.max(...values, .1) * 1.18;

      ctx.strokeStyle = '#dfe3e8'; ctx.lineWidth = 1;
      ctx.beginPath();
      ctx.moveTo(pad.left, pad.top); ctx.lineTo(pad.left, height-pad.bottom); ctx.lineTo(width-pad.right, height-pad.bottom); ctx.stroke();

      ctx.fillStyle = '#667085'; ctx.font = '12px system-ui, sans-serif'; ctx.textAlign = 'right'; ctx.textBaseline = 'middle';
      for (let i=0; i<=4; i++) {
        const yVal = maxY * i / 4;
        const y = height - pad.bottom - (yVal/maxY)*plotH;
        ctx.strokeStyle = '#eef1f4'; ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(width-pad.right, y); ctx.stroke();
        ctx.fillText(yVal.toFixed(2), pad.left-9, y);
      }

      const barGap = Math.max(2, Math.min(7, plotW/(values.length*3)));
      const barW = Math.max(2, (plotW/values.length) - barGap);
      values.forEach((v, i) => {
        const x = startX + i;
        const bx = pad.left + i*(plotW/values.length) + barGap/2;
        const bh = (v/maxY)*plotH;
        const by = height - pad.bottom - bh;
        ctx.fillStyle = '#6366f1';
        ctx.fillRect(bx, by, barW, bh);
      });

      const meanIndex = mean - startX + 0.5;
      const meanX = pad.left + (meanIndex / values.length) * plotW;
      ctx.save(); ctx.setLineDash([7,5]); ctx.strokeStyle = '#ef4444'; ctx.lineWidth = 2;
      ctx.beginPath(); ctx.moveTo(meanX, pad.top); ctx.lineTo(meanX, height-pad.bottom); ctx.stroke(); ctx.restore();

      ctx.fillStyle = '#475467'; ctx.textAlign = 'center'; ctx.textBaseline = 'top';
      const step = values.length <= 18 ? 1 : Math.ceil(values.length/14);
      for (let i=0; i<values.length; i+=step) {
        const tx = pad.left + (i+.5)*(plotW/values.length);
        ctx.fillText(String(startX+i), tx, height-pad.bottom+10);
      }
      ctx.fillText('Trial number X', pad.left + plotW/2, height-20);

      ctx.save(); ctx.translate(16, pad.top+plotH/2); ctx.rotate(-Math.PI/2); ctx.fillText('Probability P(X)', 0, 0); ctx.restore();

      canvas._chart = { startX, values, pad, plotW, width };
      canvas.onmousemove = (e) => {
        const chart = canvas._chart;
        if (!chart.values.length) return;
        const r = canvas.getBoundingClientRect();
        const mx = e.clientX - r.left;
        const idx = Math.floor((mx - chart.pad.left) / (chart.plotW/chart.values.length));
        const within = idx >= 0 && idx < chart.values.length;
        const tooltip = document.getElementById(tooltipId);
        if (!within) { tooltip.style.display='none'; return; }
        const x = chart.startX + idx;
        const val = chart.values[idx];
        tooltip.textContent = `X = ${x}   ·   P(X=${x}) = ${val.toFixed(8)}`;
        tooltip.style.display='block';
        tooltip.style.left = Math.min(Math.max(mx+12, 8), chart.width-210) + 'px';
        tooltip.style.top = '10px';
      };
      canvas.onmouseleave = () => { document.getElementById(tooltipId).style.display='none'; };
    }

    function drawChart(canvasId, tooltipId, n, mean, values, xAxisLabel) {
      const canvas = document.getElementById(canvasId);
      if (!canvas) return;
      const wrap = canvas.parentElement;
      const rect = wrap.getBoundingClientRect();
      const dpr = Math.max(1, window.devicePixelRatio || 1);
      const width = Math.max(320, rect.width);
      const height = Math.max(250, rect.height);
      canvas.width = Math.floor(width * dpr);
      canvas.height = Math.floor(height * dpr);
      canvas.style.width = width + 'px'; canvas.style.height = height + 'px';
      const ctx = canvas.getContext('2d');
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
      ctx.clearRect(0, 0, width, height);
      if (!values.length) return;

      const pad = {left: 58, right: 22, top: 20, bottom: 48};
      const plotW = width - pad.left - pad.right;
      const plotH = height - pad.top - pad.bottom;
      const maxY = Math.max(...values, .1) * 1.18;

      ctx.strokeStyle = '#dfe3e8'; ctx.lineWidth = 1;
      ctx.beginPath();
      ctx.moveTo(pad.left, pad.top); ctx.lineTo(pad.left, height-pad.bottom); ctx.lineTo(width-pad.right, height-pad.bottom); ctx.stroke();

      ctx.fillStyle = '#667085'; ctx.font = '12px system-ui, sans-serif'; ctx.textAlign = 'right'; ctx.textBaseline = 'middle';
      for (let i=0; i<=4; i++) {
        const yVal = maxY * i / 4;
        const y = height - pad.bottom - (yVal/maxY)*plotH;
        ctx.strokeStyle = '#eef1f4'; ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(width-pad.right, y); ctx.stroke();
        ctx.fillText(yVal.toFixed(2), pad.left-9, y);
      }

      const barGap = Math.max(2, Math.min(7, plotW/(values.length*3)));
      const barW = Math.max(2, (plotW/values.length) - barGap);
      values.forEach((v, x) => {
        const bx = pad.left + x*(plotW/values.length) + barGap/2;
        const bh = (v/maxY)*plotH;
        const by = height - pad.bottom - bh;
        ctx.fillStyle = '#6366f1';
        ctx.fillRect(bx, by, barW, bh);
      });

      const meanX = pad.left + ((mean + .5) / values.length) * plotW;
      ctx.save(); ctx.setLineDash([7,5]); ctx.strokeStyle = '#ef4444'; ctx.lineWidth = 2;
      ctx.beginPath(); ctx.moveTo(meanX, pad.top); ctx.lineTo(meanX, height-pad.bottom); ctx.stroke(); ctx.restore();

      ctx.fillStyle = '#475467'; ctx.textAlign = 'center'; ctx.textBaseline = 'top';
      const step = values.length <= 18 ? 1 : Math.ceil(values.length/14);
      for (let x=0; x<values.length; x+=step) {
        const tx = pad.left + (x+.5)*(plotW/values.length);
        ctx.fillText(String(x), tx, height-pad.bottom+10);
      }
      ctx.fillText(xAxisLabel, pad.left + plotW/2, height-20);

      ctx.save(); ctx.translate(16, pad.top+plotH/2); ctx.rotate(-Math.PI/2); ctx.fillText('Probability P(X)', 0, 0); ctx.restore();

      canvas._chart = { n, mean, values, pad, plotW, plotH, width, height };
      canvas.onmousemove = (e) => {
        const chart = canvas._chart;
        if (!chart.values.length) return;
        const r = canvas.getBoundingClientRect();
        const mx = e.clientX - r.left;
        const idx = Math.floor((mx - chart.pad.left) / (chart.plotW/chart.values.length));
        const within = idx >= 0 && idx < chart.values.length;
        const tooltip = document.getElementById(tooltipId);
        if (!within) { tooltip.style.display='none'; return; }
        const val = chart.values[idx];
        tooltip.textContent = `X = ${idx}   ·   P(X=${idx}) = ${val.toFixed(8)}`;
        tooltip.style.display='block';
        tooltip.style.left = Math.min(Math.max(mx+12, 8), chart.width-210) + 'px';
        tooltip.style.top = '10px';
      };
      canvas.onmouseleave = () => { document.getElementById(tooltipId).style.display='none'; };
    }

    function navigate() {
      const hash = location.hash.replace('#','') || 'home';
      const target = document.getElementById(hash) ? hash : 'home';
      document.querySelectorAll('.page').forEach(p => p.classList.toggle('active', p.id === target));
      document.querySelectorAll('nav a, .brand-wrap, .action').forEach(a => a.classList.toggle('active', a.dataset.page === target));
      if (target === 'binomial') updateBinomial();
      if (target === 'poisson') updatePoisson();
      if (target === 'geometric') updateGeometric();
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    document.querySelectorAll('[data-page]').forEach(link => link.addEventListener('click', () => {
      setTimeout(navigate, 0);
    }));
    window.addEventListener('hashchange', navigate);
    window.addEventListener('resize', () => {
      if (document.getElementById('binomial').classList.contains('active')) updateBinomial();
      if (document.getElementById('poisson').classList.contains('active')) updatePoisson();
    });
    ['b-n','b-p','b-k'].forEach(id => document.getElementById(id).addEventListener('input', updateBinomial));
    ['p-lambda','p-k'].forEach(id => document.getElementById(id).addEventListener('input', updatePoisson));
    ['g-p','g-k'].forEach(id => document.getElementById(id).addEventListener('input', updateGeometric));

    navigate();
    updateBinomial();
    updatePoisson();
    updateGeometric();
  </script>
</body>
</html>
