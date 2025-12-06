<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
  <meta charset="UTF-8" />
  <title>Omnia AI – Everything starts here</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg-dark: #0B0B0D;
      --bg-dark-soft: #1A1A1D;
      --bg-light: #FFFFFF;
      --bg-light-soft: #F3F3F7;
      --primary: #6C38FF;
      --accent: #00D4FF;
      --text-light: #FFFFFF;
      --text-dark: #0B0B0D;
      --text-muted-dark: #A0A0A5;
      --text-muted-light: #4F4F52;
      --radius-lg: 18px;
      --radius-md: 12px;
      --shadow-soft: 0 18px 45px rgba(0, 0, 0, 0.35);
      --shadow-light: 0 18px 45px rgba(12, 8, 44, 0.18);
      --transition: 0.25s ease;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Inter", "SF Pro Text", sans-serif;
      background: var(--bg-dark);
      color: var(--text-light);
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
      transition: background var(--transition), color var(--transition);
    }
    body.light { background: var(--bg-light); color: var(--text-dark); }

    a { text-decoration: none; color: inherit; }

    .page { min-height: 100vh; display: flex; flex-direction: column; }
    .shell { width: 100%; max-width: 1120px; margin: 0 auto; padding: 20px 20px 56px; }

    header {
      display: flex; justify-content: space-between; align-items: center;
      padding: 8px 0 16px;
    }

    .brand { display: flex; align-items: center; gap: 10px; }
    .logo-mark {
      width: 32px; height: 32px; border-radius: 999px;
      background: radial-gradient(circle at 30% 0%, var(--accent), transparent 60%),
                  radial-gradient(circle at 70% 100%, var(--primary), transparent 60%),
                  #08080A;
      box-shadow: 0 0 18px rgba(108, 56, 255, 0.7);
    }
    .brand-text { display: flex; flex-direction: column; gap: 2px; }
    .brand-title {
      font-weight: 650; letter-spacing: 0.08em; font-size: 0.92rem; text-transform: uppercase;
    }
    .brand-subtitle { font-size: 0.72rem; opacity: 0.72; }

    .header-actions { display: flex; align-items: center; gap: 10px; }

    .toggle {
      border-radius: 999px; border: 1px solid rgba(255, 255, 255, 0.18);
      padding: 5px 10px; display: flex; align-items: center; gap: 6px;
      font-size: 0.72rem; cursor: pointer; background: rgba(12, 12, 16, 0.9);
    }
    body.light .toggle { background: rgba(255, 255, 255, 0.9); border-color: rgba(0,0,0,0.08); }
    .toggle span { opacity: 0.7; }
    .toggle-dot {
      width: 18px; height: 18px; border-radius: 999px;
      background: var(--primary); display: flex; align-items: center;
      justify-content: center; color: #fff; font-size: 0.65rem;
    }

    .pill {
      border-radius: 999px; padding: 7px 14px; font-size: 0.74rem;
      border: 1px solid rgba(255, 255, 255, 0.16); opacity: 0.9;
    }
    body.light .pill { border-color: rgba(0, 0, 0, 0.06); background: rgba(255,255,255,0.75); }

    /* Hero */
    .hero {
      display: grid; grid-template-columns: minmax(0, 1.3fr) minmax(0, 1.1fr);
      gap: 26px; margin-top: 28px; margin-bottom: 30px;
    }
    @media (max-width: 840px) { .hero { grid-template-columns: minmax(0, 1fr); } }

    .hero-left { display: flex; flex-direction: column; gap: 18px; }
    .eyebrow {
      font-size: 0.78rem; text-transform: uppercase;
      letter-spacing: 0.16em; opacity: 0.72;
    }
    .hero-title {
      font-size: clamp(1.9rem, 3.1vw, 2.6rem); font-weight: 720;
      letter-spacing: -0.03em; line-height: 1.18;
    }
    .hero-title span {
      background: linear-gradient(120deg, var(--accent), var(--primary));
      -webkit-background-clip: text; background-clip: text; color: transparent;
    }
    .hero-sub { font-size: 0.95rem; max-width: 460px; opacity: 0.86; }
    .hero-sub-ar {
      font-size: 0.9rem; max-width: 480px; opacity: 0.84;
      direction: rtl; text-align: right;
    }

    .hero-actions { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 6px; }

    .btn-primary, .btn-secondary {
      border-radius: 999px; font-size: 0.9rem; cursor: pointer;
      display: inline-flex; align-items: center; gap: 8px;
    }
    .btn-primary {
      padding: 10px 20px; border: none; font-weight: 600;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      color: #fff; box-shadow: 0 12px 26px rgba(0, 0, 0, 0.65);
    }
    .btn-secondary {
      padding: 9px 18px; border: 1px solid rgba(255, 255, 255, 0.18);
      background: transparent; color: inherit; font-size: 0.88rem; opacity: 0.92;
    }
    body.light .btn-secondary { border-color: rgba(0, 0, 0, 0.08); }

    .hero-meta {
      display: flex; flex-wrap: wrap; gap: 14px;
      margin-top: 12px; font-size: 0.78rem; opacity: 0.8;
    }

    .hero-right { display: flex; flex-direction: column; gap: 12px; }

    .panel {
      border-radius: var(--radius-lg); padding: 18px 18px 16px;
      background:
        radial-gradient(circle at 0 0, rgba(0, 212, 255, 0.16), transparent 55%),
        radial-gradient(circle at 100% 100%, rgba(108, 56, 255, 0.2), transparent 50%),
        var(--bg-dark-soft);
      box-shadow: var(--shadow-soft);
    }
    body.light .panel { background: var(--bg-light-soft); box-shadow: var(--shadow-light); }

    .panel-header {
      display: flex; justify-content: space-between; align-items: center;
      margin-bottom: 10px;
    }
    .panel-title { font-size: 0.86rem; opacity: 0.86; }
    .badge {
      font-size: 0.7rem; border-radius: 999px; padding: 3px 8px;
      border: 1px solid rgba(255, 255, 255, 0.2); opacity: 0.9;
    }
    body.light .badge { border-color: rgba(0,0,0,0.08); }

    .request-label { font-size: 0.76rem; margin-bottom: 6px; opacity: 0.82; }
    .request-box {
      border-radius: var(--radius-md); padding: 10px 11px;
      background: rgba(3, 3, 6, 0.85); border: 1px solid rgba(255, 255, 255, 0.16);
      font-size: 0.8rem; min-height: 76px; resize: vertical; width: 100%;
      color: inherit; font-family: inherit;
    }
    body.light .request-box {
      background: #FFFFFF; border-color: rgba(0,0,0,0.08);
    }

    .panel-footer {
      display: flex; justify-content: space-between; align-items: center;
      margin-top: 8px; font-size: 0.72rem; opacity: 0.8;
    }

    .chip-row { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 12px; }
    .chip {
      font-size: 0.7rem; border-radius: 999px; padding: 4px 9px;
      background: rgba(255, 255, 255, 0.06); opacity: 0.9;
    }
    body.light .chip { background: rgba(0, 0, 0, 0.04); }

    .mini-grid {
      display: grid; grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 8px; margin-top: 10px; font-size: 0.7rem;
    }
    .mini-card {
      border-radius: var(--radius-md); padding: 8px 9px;
      background: rgba(3, 3, 6, 0.9); border: 1px solid rgba(255, 255, 255, 0.12);
    }
    body.light .mini-card {
      background: #FFFFFF; border-color: rgba(0,0,0,0.06);
    }
    .mini-card label { opacity: 0.7; }
    .mini-card strong { display: block; margin-top: 2px; font-size: 0.78rem; }

    /* Sections */
    section { margin-top: 28px; }
    .section-title { font-size: 0.96rem; font-weight: 600; margin-bottom: 10px; }
    .section-sub { font-size: 0.86rem; opacity: 0.8; max-width: 520px; }
    .section-sub-ar {
      font-size: 0.84rem; opacity: 0.82; max-width: 560px;
      direction: rtl; text-align: right; margin-top: 3px;
    }

    .cards-grid {
      display: grid; grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 14px; margin-top: 14px;
    }
    @media (max-width: 840px) { .cards-grid { grid-template-columns: minmax(0, 1fr); } }

    .card {
      border-radius: var(--radius-lg); padding: 14px 14px 12px;
      background:
        radial-gradient(circle at 0 0, rgba(108,56,255,0.16), transparent 55%),
        radial-gradient(circle at 100% 100%, rgba(0,212,255,0.2), transparent 55%),
        var(--bg-dark-soft);
      border: 1px solid rgba(255, 255, 255, 0.12); font-size: 0.84rem;
    }
    body.light .card { background: var(--bg-light-soft); border-color: rgba(0,0,0,0.06); }
    .card h3 { font-size: 0.9rem; margin-bottom: 5px; }
    .card p { opacity: 0.82; }

    .tag-row { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 8px; font-size: 0.7rem; }
    .tag {
      border-radius: 999px; padding: 3px 8px;
      background: rgba(0,0,0,0.56); opacity: 0.9;
    }
    body.light .tag { background: rgba(0,0,0,0.06); }

    /* Pricing */
    .pricing-grid {
      display: grid; grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px; margin-top: 16px;
    }
    @media (max-width: 960px) { .pricing-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); } }
    @media (max-width: 600px) { .pricing-grid { grid-template-columns: minmax(0, 1fr); } }

    .price-card {
      border-radius: var(--radius-lg); padding: 14px;
      background: rgba(3,3,6,0.96); border: 1px solid rgba(255,255,255,0.1);
      font-size: 0.84rem; display: flex; flex-direction: column; gap: 6px;
    }
    body.light .price-card { background: #FFFFFF; border-color: rgba(0,0,0,0.06); }

    .price-name { font-weight: 600; font-size: 0.9rem; }
    .price-tagline { font-size: 0.76rem; opacity: 0.76; }
    .price-value { margin-top: 4px; font-size: 0.96rem; font-weight: 650; }
    .price-list { margin-top: 6px; font-size: 0.78rem; opacity: 0.86; }
    .price-list li { margin-bottom: 3px; }
    .price-cta { margin-top: 8px; margin-bottom: 2px; }
    .price-cta button { width: 100%; justify-content: center; padding: 7px 0; font-size: 0.8rem; }

    /* Footer */
    footer {
      margin-top: 38px; padding-top: 18px;
      border-top: 1px solid rgba(255,255,255,0.1);
      font-size: 0.75rem; opacity: 0.7;
      display: flex; flex-wrap: wrap; gap: 8px; justify-content: space-between;
    }
    body.light footer { border-color: rgba(0,0,0,0.06); }
    .footer-right {
      direction: rtl; text-align: right; max-width: 360px;
    }
  </style>
</head>
<body>
<div class="page">
  <div class="shell">
    <header>
      <div class="brand">
        <div class="logo-mark"></div>
        <div class="brand-text">
          <div class="brand-title">OMNIA AI</div>
          <div class="brand-subtitle">Unified AI execution platform</div>
        </div>
      </div>
      <div class="header-actions">
        <div class="pill">Public Preview · v0.1</div>
        <button class="toggle" id="themeToggle">
          <span>Dark / Light</span>
          <div class="toggle-dot">☾</div>
        </button>
      </div>
    </header>

    <main>
      <section class="hero">
        <div class="hero-left">
          <div class="eyebrow">AI platform · execution first</div>
          <h1 class="hero-title">
            Everything starts with a request. <span>Omnia AI</span> does the rest.
          </h1>
          <p class="hero-sub">
            A unified AI platform where individuals and businesses describe what they want,
            and receive ready-to-use outputs — content, docs, strategies, designs, and more.
          </p>
          <p class="hero-sub-ar">
            منصة ذكاء اصطناعي تختصر عليك الوقت: اكتب طلبك فقط، و Omnia AI تتكفّل
            بتنفيذ المهام، إعداد الملفات، وتقديم نتائج جاهزة بشكل احترافي.
          </p>
          <div class="hero-actions">
            <button class="btn-primary" onclick="document.getElementById('request-section').scrollIntoView({behavior:'smooth'});">
              Start now
              <span>→</span>
            </button>
            <button class="btn-secondary" onclick="document.getElementById('plans').scrollIntoView({behavior:'smooth'});">
              For business & teams
            </button>
          </div>
          <div class="hero-meta">
            <span>• 3 core engines: Core · Discipline · Gold</span>
            <span>• Arabic-first · global-ready</span>
          </div>
        </div>

        <div class="hero-right">
          <div class="panel" id="request-section">
            <div class="panel-header">
              <span class="panel-title">Live request · Omnia Core Engine</span>
              <span class="badge">Demo</span>
            </div>
            <div class="request-label">Describe what you want Omnia to do for you:</div>
            <textarea class="request-box" placeholder="مثال: جهّز لي عرض بوربوينت من 10 شرائح عن منصة Omnia AI، بالعربي والإنجليزي، أسلوب احترافي ومختصر."></textarea>
            <div class="panel-footer">
              <span>Auto-classify: content · business · technical · trading</span>
              <span>ETA: ~60s</span>
            </div>

            <div class="chip-row">
              <div class="chip">Business plan</div>
              <div class="chip">Pitch deck</div>
              <div class="chip">Social content</div>
              <div class="chip">Trading brief</div>
              <div class="chip">Automation idea</div>
            </div>

            <div class="mini-grid">
              <div class="mini-card">
                <label>Engine</label>
                <strong>Core execution</strong>
              </div>
              <div class="mini-card">
                <label>Mode</label>
                <strong>Done-for-you</strong>
              </div>
              <div class="mini-card">
                <label>Language</label>
                <strong>AR · EN</strong>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section>
        <h2 class="section-title">What is Omnia AI?</h2>
        <p class="section-sub">
          Omnia AI is a unified AI execution layer. You write what you need – in Arabic or English –
          and Omnia analyses, breaks it down, and returns polished, ready-to-use outputs.
        </p>
        <p class="section-sub-ar">
          Omnia AI ليست مجرد شات… بل طبقة تنفيذ كاملة تعتمد على الذكاء الاصطناعي.
          اكتب المطلوب، والمنصة تحلّل، تقسّم المهمة، وتعيد لك نتائج جاهزة للاستخدام.
        </p>
      </section>

      <section>
        <h2 class="section-title">Core engines</h2>
        <p class="section-sub">
          Three engines power Omnia today – one for execution, one for discipline, and one for gold trading.
        </p>

        <div class="cards-grid">
          <div class="card">
            <h3>Omnia Core Engine</h3>
            <p>
              The primary engine that understands tasks, breaks them into steps, and delivers
              high-quality outputs: content, business docs, slides, code, and more.
            </p>
          </div>

          <div class="card">
            <h3>Discipline Engine</h3>
            <p>
              A daily discipline layer that keeps you moving: morning question, daily task,
              evening review, and gentle pressure to stay consistent with your goals.
            </p>
          </div>

          <div class="card">
            <h3>Gold Engine · Aggressive</h3>
            <p>
              A gold-focused engine that produces aggressive, but structured, trading briefs:
              trend, key levels, breakout scenarios, multi-target exits, and dynamic stops.
            </p>
          </div>
        </div>
      </section>

      <section>
        <h2 class="section-title">Who is Omnia for?</h2>
        <p class="section-sub">
          Designed for people who value time: founders, students, busy professionals, and traders
          who want an AI layer handling the heavy lifting.
        </p>

        <div class="cards-grid">
          <div class="card">
            <h3>Individuals & students</h3>
            <p>
              Projects, reports, CVs, presentations, study plans, and personal systems –
              Omnia helps you deliver more with less time.
            </p>
          </div>
          <div class="card">
            <h3>Businesses & teams</h3>
            <p>
              Proposals, internal docs, marketing content, and automation concepts. A single
              AI entry point instead of ten scattered tools.
            </p>
          </div>
          <div class="card">
            <h3>Traders</h3>
            <p>
              Structured daily gold briefs, scenarios, and risk-aware aggressive setups
              designed to support your own decision-making.
            </p>
          </div>
        </div>
      </section>

      <section id="plans">
        <h2 class="section-title">Plans</h2>
        <p class="section-sub">
          Start simple, then grow into Pro and Business tiers as Omnia becomes part of your daily workflow.
        </p>

        <div class="pricing-grid">
          <div class="price-card">
            <div class="price-name">Starter</div>
            <div class="price-tagline">Get a feel for Omnia.</div>
            <div class="price-value">Free</div>
            <ul class="price-list">
              <li>3 requests / month</li>
              <li>Access to Omnia Core</li>
              <li>Basic outputs (AR/EN)</li>
            </ul>
            <div class="price-cta">
              <button class="btn-secondary">Start free</button>
            </div>
          </div>

          <div class="price-card">
            <div class="price-name">Pro</div>
            <div class="price-tagline">For individuals who execute daily.</div>
            <div class="price-value">39 SAR / month</div>
            <ul class="price-list">
              <li>20 requests / month</li>
              <li>Core + Discipline Engine</li>
              <li>Priority quality</li>
            </ul>
            <div class="price-cta">
              <button class="btn-primary">Upgrade to Pro</button>
            </div>
          </div>

          <div class="price-card">
            <div class="price-name">Business</div>
            <div class="price-tagline">For small teams & agencies.</div>
            <div class="price-value">199 SAR / month</div>
            <ul class="price-list">
              <li>Shared workspace</li>
              <li>Unlimited requests (fair use)</li>
              <li>Templates & playbooks</li>
              <li>Basic integrations</li>
            </ul>
            <div class="price-cta">
              <button class="btn-secondary">Talk to us</button>
            </div>
          </div>

          <div class="price-card">
            <div class="price-name">Enterprise</div>
            <div class="price-tagline">Custom AI execution layer.</div>
            <div class="price-value">Custom</div>
            <ul class="price-list">
              <li>Dedicated engines</li>
              <li>Private models / prompts</li>
              <li>Advanced integrations</li>
              <li>Onboarding & support</li>
            </ul>
            <div class="price-cta">
              <button class="btn-secondary">Book a call</button>
            </div>
          </div>
        </div>
      </section>

      <section>
        <h2 class="section-title">Next steps</h2>
        <p class="section-sub">
          This layout is ready to be published on GitHub Pages so you can share a live link
          for Omnia AI this week.
        </p>
        <p class="section-sub-ar">
          انسخ هذا الكود كما هو، انشره على GitHub Pages، وشارك الرابط مع أول عملائك
          لتبدأ في تشغيل Omnia AI فعلياً.
        </p>
      </section>
    </main>

    <footer>
      <div class="footer-left">
        © Omnia AI – execution platform. Built to save time and compound your output.
      </div>
      <div class="footer-right">
        منصة موحّدة لخدمات الذكاء الاصطناعي. اكتب ما تريد… ودع Omnia AI تتكفّل بالتنفيذ.
      </div>
    </footer>
  </div>
</div>

<script>
  const toggle = document.getElementById('themeToggle');
  const body = document.body;

  function setTheme(mode) {
    if (mode === 'light') body.classList.add('light');
    else body.classList.remove('light');
    try { localStorage.setItem('omnia-theme', mode); } catch (e) {}
  }

  function initTheme() {
    let mode = 'dark';
    try {
      const saved = localStorage.getItem('omnia-theme');
      if (saved === 'light') mode = 'light';
    } catch (e) {}
    setTheme(mode);
  }

  toggle.addEventListener('click', () => {
    const isLight = body.classList.contains('light');
    setTheme(isLight ? 'dark' : 'light');
  });

  initTheme();
</script>
</body>
</html>
