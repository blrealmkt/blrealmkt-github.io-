<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Manual de Ventas — Arcana Fraccionamiento | BL Real Estate</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700;800;900&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />
  <style>
    /* ─── TOKENS ────────────────────────────────────────────────── */
    :root {
      --navy:   #002c3a;
      --gold:   #E4C292;
      --white:  #ffffff;
      --navy80: rgba(0,44,58,.80);
      --navy60: rgba(0,44,58,.60);
      --navy20: rgba(0,44,58,.15);
      --gold40: rgba(228,194,146,.40);
      --gold10: rgba(228,194,146,.10);
      --slide-w: 1280px;
      --slide-h: 720px;
      --radius: 14px;
      --font: 'Poppins', sans-serif;
    }

    /* ─── RESET ─────────────────────────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    ul { list-style: none; }

    /* ─── PAGE SHELL ─────────────────────────────────────────────── */
    body {
      background: #0a1520;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 48px;
      padding: 60px 20px;
      font-family: var(--font);
      color: var(--white);
    }

    /* section label above each slide */
    .slide-label {
      font-size: 11px;
      font-weight: 600;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: -32px;
      align-self: flex-start;
      margin-left: calc((100vw - var(--slide-w)) / 2);
    }

    /* ─── SLIDE WRAPPER ──────────────────────────────────────────── */
    .slide {
      width: var(--slide-w);
      height: var(--slide-h);
      background: var(--white);
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      box-shadow: 0 40px 80px rgba(0,0,0,.55), 0 0 0 1px rgba(228,194,146,.2);
    }

    /* ─── SHARED DECORATIVE STRIPE (left) ────────────────────────── */
    .slide::after {
      content: '';
      position: absolute;
      left: 0; top: 0; bottom: 0;
      width: 6px;
      background: linear-gradient(180deg, var(--gold) 0%, var(--navy) 100%);
      z-index: 10;
    }

    /* ─── SLIDE HEADER BAR ───────────────────────────────────────── */
    .slide-header {
      background: var(--navy);
      padding: 22px 60px 22px 70px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-shrink: 0;
    }
    .slide-header .brand {
      font-size: 11px;
      font-weight: 600;
      letter-spacing: 5px;
      text-transform: uppercase;
      color: var(--gold);
    }
    .slide-header .slide-number {
      font-size: 11px;
      font-weight: 300;
      color: rgba(255,255,255,.45);
      letter-spacing: 2px;
    }

    /* ─── HERO: SLIDE 1 ──────────────────────────────────────────── */
    .s1 { background: var(--navy); }
    .s1::before {
      content: '';
      position: absolute;
      inset: 0;
      background:
        radial-gradient(ellipse 55% 70% at 82% 50%, rgba(228,194,146,.12) 0%, transparent 70%),
        radial-gradient(ellipse 30% 30% at 15% 80%, rgba(228,194,146,.07) 0%, transparent 60%);
    }
    .s1 .grid-bg {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.03) 1px, transparent 1px);
      background-size: 64px 64px;
    }
    .s1-body {
      position: relative;
      z-index: 2;
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 0 80px;
    }
    .s1 .eyebrow {
      font-size: 11px;
      font-weight: 600;
      letter-spacing: 6px;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 20px;
    }
    .s1 h1 {
      font-size: 72px;
      font-weight: 800;
      line-height: 1;
      color: var(--white);
      text-transform: uppercase;
      letter-spacing: -1px;
    }
    .s1 h1 span { color: var(--gold); display: block; }
    .s1 .subtitle {
      margin-top: 20px;
      font-size: 16px;
      font-weight: 300;
      color: rgba(255,255,255,.65);
      max-width: 540px;
      line-height: 1.7;
    }
    .s1 .tag-row {
      display: flex;
      gap: 14px;
      margin-top: 36px;
    }
    .tag {
      border: 1px solid rgba(228,194,146,.4);
      border-radius: 100px;
      padding: 6px 18px;
      font-size: 11px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: var(--gold);
    }
    .s1 .deco-num {
      position: absolute;
      right: 80px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 240px;
      font-weight: 900;
      color: rgba(228,194,146,.05);
      line-height: 1;
      user-select: none;
      z-index: 1;
    }
    /* golden corner ornament */
    .corner-ornament {
      position: absolute;
      right: 0;
      bottom: 0;
      width: 280px;
      height: 280px;
      border-top: 1px solid rgba(228,194,146,.2);
      border-left: 1px solid rgba(228,194,146,.2);
      border-radius: 100% 0 0 0;
    }
    .s1 .slide-header { background: rgba(0,0,0,.25); border-bottom: 1px solid rgba(255,255,255,.06); }

    /* ─── SLIDE 2: MENTALIDAD ────────────────────────────────────── */
    .s2-body {
      flex: 1;
      display: flex;
      padding: 36px 60px 44px 70px;
      gap: 60px;
    }
    .s2-left {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
    .section-title {
      font-size: 36px;
      font-weight: 800;
      color: var(--navy);
      text-transform: uppercase;
      letter-spacing: -0.5px;
      line-height: 1.1;
      margin-bottom: 6px;
    }
    .section-title span { color: var(--gold); display: block; font-weight: 300; font-size: 28px; text-transform: none; letter-spacing: 0; }
    .divider-gold {
      width: 52px;
      height: 3px;
      background: linear-gradient(90deg, var(--gold), transparent);
      margin: 16px 0 24px;
      border-radius: 2px;
    }
    .lead-text {
      font-size: 15px;
      font-weight: 400;
      line-height: 1.75;
      color: #2a3d4a;
      margin-bottom: 28px;
    }
    /* Mindset cards */
    .mindset-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }
    .mindset-card {
      background: var(--navy);
      border-radius: var(--radius);
      padding: 18px 20px;
      border-left: 3px solid var(--gold);
    }
    .mindset-card .mc-icon {
      font-size: 18px;
      color: var(--gold);
      margin-bottom: 8px;
    }
    .mindset-card .mc-title {
      font-size: 12px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      color: var(--gold);
      margin-bottom: 4px;
    }
    .mindset-card .mc-text {
      font-size: 12px;
      font-weight: 300;
      line-height: 1.55;
      color: rgba(255,255,255,.75);
    }
    .s2-right {
      width: 360px;
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      gap: 14px;
      justify-content: center;
    }
    .stat-card {
      background: var(--navy);
      border-radius: var(--radius);
      padding: 22px 26px;
      position: relative;
      overflow: hidden;
    }
    .stat-card::before {
      content: '';
      position: absolute;
      top: -30px; right: -30px;
      width: 100px; height: 100px;
      background: radial-gradient(circle, rgba(228,194,146,.15) 0%, transparent 70%);
    }
    .stat-card .stat-num {
      font-size: 48px;
      font-weight: 800;
      color: var(--gold);
      line-height: 1;
    }
    .stat-card .stat-label {
      font-size: 11px;
      font-weight: 500;
      letter-spacing: 2px;
      text-transform: uppercase;
      color: rgba(255,255,255,.55);
      margin-top: 4px;
    }
    .stat-card .stat-desc {
      font-size: 12px;
      font-weight: 300;
      color: rgba(255,255,255,.7);
      margin-top: 8px;
      line-height: 1.5;
    }
    /* Corner detail for slide 2 */
    .s2::before {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 220px; height: 220px;
      background: radial-gradient(circle at top right, rgba(0,44,58,.06) 0%, transparent 70%);
    }

    /* ─── SLIDE 3: GUIÓN DE APERTURA ─────────────────────────────── */
    .s3-body {
      flex: 1;
      display: flex;
      padding: 30px 60px 40px 70px;
      gap: 50px;
      align-items: flex-start;
    }
    .s3-left {
      flex: 1;
      display: flex;
      flex-direction: column;
    }
    .s3-right {
      width: 400px;
      flex-shrink: 0;
    }
    /* Script box */
    .script-box {
      background: var(--navy);
      border-radius: var(--radius);
      padding: 28px 30px;
      position: relative;
      overflow: hidden;
    }
    .script-box::before {
      content: '"';
      position: absolute;
      top: -10px; left: 16px;
      font-size: 120px;
      font-weight: 900;
      color: var(--gold);
      opacity: .12;
      font-family: Georgia, serif;
      line-height: 1;
    }
    .script-box .sb-label {
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 14px;
    }
    .script-box .sb-text {
      font-size: 13.5px;
      font-weight: 300;
      line-height: 1.8;
      color: rgba(255,255,255,.88);
      position: relative;
      z-index: 1;
    }
    .script-box .sb-text strong {
      color: var(--gold);
      font-weight: 600;
    }
    /* Step list */
    .step-list { display: flex; flex-direction: column; gap: 14px; }
    .step-item {
      display: flex;
      gap: 16px;
      align-items: flex-start;
    }
    .step-num {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background: var(--navy);
      color: var(--gold);
      font-size: 13px;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      border: 1.5px solid var(--gold40);
    }
    .step-content .step-title {
      font-size: 13px;
      font-weight: 700;
      color: var(--navy);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 3px;
    }
    .step-content .step-text {
      font-size: 12.5px;
      font-weight: 300;
      line-height: 1.55;
      color: #3a5060;
    }

    /* ─── SLIDE 4: MANEJO DE OBJECIONES ──────────────────────────── */
    .s4 { background: var(--white); }
    .s4-body {
      flex: 1;
      padding: 28px 60px 40px 70px;
      display: flex;
      flex-direction: column;
      gap: 22px;
    }
    .objection-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 18px;
      flex: 1;
    }
    .obj-card {
      border-radius: var(--radius);
      overflow: hidden;
      border: 1px solid rgba(0,44,58,.1);
      display: flex;
      flex-direction: column;
    }
    .obj-header {
      background: var(--navy);
      padding: 14px 20px;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .obj-header .obj-icon {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background: var(--gold40);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 13px;
      color: var(--gold);
      flex-shrink: 0;
    }
    .obj-header .obj-q {
      font-size: 13px;
      font-weight: 600;
      color: var(--white);
      font-style: italic;
    }
    .obj-body {
      background: var(--gold10);
      padding: 14px 20px;
      flex: 1;
    }
    .obj-body .obj-a {
      font-size: 12.5px;
      font-weight: 400;
      line-height: 1.65;
      color: var(--navy);
    }
    .obj-body .obj-a strong { font-weight: 700; }
    .s4::before {
      content: '';
      position: absolute;
      bottom: -60px; right: -60px;
      width: 300px; height: 300px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(228,194,146,.15) 0%, transparent 70%);
    }

    /* ─── SLIDE 5: SEGUIMIENTO (FOLLOW-UP) ───────────────────────── */
    .s5-body {
      flex: 1;
      display: flex;
      padding: 28px 60px 40px 70px;
      gap: 50px;
    }
    .s5-left {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
    .s5-right {
      width: 420px;
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      gap: 12px;
      justify-content: center;
    }
    /* Timeline */
    .timeline { display: flex; flex-direction: column; gap: 0; }
    .tl-item {
      display: flex;
      gap: 20px;
      position: relative;
    }
    .tl-item:not(:last-child) .tl-line {
      position: absolute;
      left: 19px;
      top: 38px;
      width: 2px;
      bottom: -10px;
      background: linear-gradient(180deg, var(--gold) 0%, rgba(228,194,146,.2) 100%);
    }
    .tl-dot {
      width: 38px;
      height: 38px;
      border-radius: 50%;
      background: var(--navy);
      border: 2px solid var(--gold);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      font-size: 12px;
      color: var(--gold);
      font-weight: 700;
      z-index: 1;
    }
    .tl-content {
      padding: 8px 0 24px;
    }
    .tl-content .tl-day {
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 2px;
      color: var(--gold);
      margin-bottom: 3px;
    }
    .tl-content .tl-action {
      font-size: 14px;
      font-weight: 600;
      color: var(--navy);
      margin-bottom: 3px;
    }
    .tl-content .tl-detail {
      font-size: 12px;
      font-weight: 300;
      color: #4a6070;
      line-height: 1.5;
    }
    /* Message templates */
    .msg-card {
      background: var(--navy);
      border-radius: var(--radius);
      padding: 18px 22px;
      position: relative;
    }
    .msg-card .msg-channel {
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 10px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .msg-card .msg-text {
      font-size: 12px;
      font-weight: 300;
      line-height: 1.65;
      color: rgba(255,255,255,.82);
    }
    .msg-card .msg-text em { color: var(--gold); font-style: normal; font-weight: 600; }

    /* ─── SLIDE 6: CIERRE + GOLDEN RULE ──────────────────────────── */
    .s6 { background: var(--navy); }
    .s6::before {
      content: '';
      position: absolute;
      inset: 0;
      background:
        radial-gradient(ellipse 60% 60% at 110% 50%, rgba(228,194,146,.08) 0%, transparent 60%),
        radial-gradient(ellipse 40% 40% at -10% 80%, rgba(228,194,146,.06) 0%, transparent 60%);
    }
    .s6 .grid-bg {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.025) 1px, transparent 1px);
      background-size: 64px 64px;
    }
    .s6 .slide-header {
      background: rgba(0,0,0,.25);
      border-bottom: 1px solid rgba(255,255,255,.06);
    }
    .s6-body {
      position: relative;
      z-index: 2;
      flex: 1;
      display: flex;
      padding: 30px 80px 44px 80px;
      gap: 60px;
    }
    .s6-left {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
    .s6-left .big-title {
      font-size: 50px;
      font-weight: 800;
      color: var(--white);
      text-transform: uppercase;
      line-height: 1;
      letter-spacing: -1px;
      margin-bottom: 8px;
    }
    .s6-left .big-title span { color: var(--gold); }
    .s6-left .sub {
      font-size: 14px;
      font-weight: 300;
      color: rgba(255,255,255,.6);
      max-width: 440px;
      line-height: 1.7;
      margin-bottom: 34px;
    }
    /* Closing rule cards */
    .rule-list { display: flex; flex-direction: column; gap: 14px; }
    .rule-item {
      display: flex;
      align-items: center;
      gap: 18px;
      padding: 14px 20px;
      background: rgba(255,255,255,.04);
      border-radius: 10px;
      border: 1px solid rgba(228,194,146,.12);
    }
    .rule-item .ri-icon {
      font-size: 20px;
      color: var(--gold);
      width: 28px;
      flex-shrink: 0;
      text-align: center;
    }
    .rule-item .ri-text {
      font-size: 13px;
      font-weight: 400;
      color: rgba(255,255,255,.85);
      line-height: 1.5;
    }
    .rule-item .ri-text strong { color: var(--gold); }
    .s6-right {
      width: 360px;
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 16px;
    }
    /* Golden quote box */
    .golden-box {
      background: var(--gold);
      border-radius: var(--radius);
      padding: 28px 28px;
      position: relative;
      overflow: hidden;
    }
    .golden-box::before {
      content: '★';
      position: absolute;
      right: -10px; top: -10px;
      font-size: 100px;
      color: rgba(0,44,58,.07);
      line-height: 1;
    }
    .golden-box .gb-label {
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--navy60);
      margin-bottom: 12px;
    }
    .golden-box .gb-quote {
      font-size: 15px;
      font-weight: 600;
      line-height: 1.6;
      color: var(--navy);
    }
    .golden-box .gb-attr {
      margin-top: 14px;
      font-size: 11px;
      font-weight: 500;
      color: rgba(0,44,58,.6);
      letter-spacing: 1px;
    }
    /* Checklist */
    .checklist { display: flex; flex-direction: column; gap: 10px; }
    .check-item {
      display: flex;
      align-items: center;
      gap: 12px;
      font-size: 13px;
      font-weight: 400;
      color: rgba(255,255,255,.82);
    }
    .check-item i { color: var(--gold); font-size: 14px; width: 18px; }

    /* ─── FOOTER ─────────────────────────────────────────────────── */
    footer {
      width: var(--slide-w);
      text-align: center;
      padding: 20px 0 10px;
      border-top: 1px solid rgba(228,194,146,.15);
    }
    footer .footer-brand {
      font-size: 16px;
      font-weight: 700;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: var(--gold);
    }
    footer .footer-brand span { color: rgba(255,255,255,.45); font-weight: 200; }
    footer .footer-sub {
      margin-top: 6px;
      font-size: 11px;
      font-weight: 300;
      letter-spacing: 2px;
      color: rgba(255,255,255,.3);
    }
    footer .footer-divider {
      display: flex;
      align-items: center;
      gap: 14px;
      justify-content: center;
      margin: 14px 0;
    }
    footer .footer-divider .line {
      height: 1px;
      width: 120px;
      background: linear-gradient(90deg, transparent, rgba(228,194,146,.4), transparent);
    }
    footer .footer-divider i { color: var(--gold); font-size: 10px; }
    footer .footer-copy {
      font-size: 10px;
      font-weight: 300;
      color: rgba(255,255,255,.2);
      letter-spacing: 1px;
    }
  </style>
</head>
<body>

  <!-- ═══════════════════════════════════════════════════════════
       SLIDE 1 — PORTADA
  ════════════════════════════════════════════════════════════ -->
  <span class="slide-label">Slide 01 — Portada</span>
  <div class="slide s1">
    <div class="grid-bg"></div>
    <div class="slide-header">
      <span class="brand">BL Real Estate · Arcana</span>
      <span class="slide-number">01 / 06</span>
    </div>
    <div class="s1-body">
      <div class="eyebrow">Manual de Ventas · Prospección en Frío</div>
      <h1>
        ARCANA
        <span>Fraccionamiento</span>
      </h1>
      <p class="subtitle">
        Estrategias de alto impacto para llamadas y mensajes en frío,
        diseñadas para convertir prospectos desconocidos en clientes comprometidos.
      </p>
      <div class="tag-row">
        <div class="tag">Llamadas Frías</div>
        <div class="tag">WhatsApp</div>
        <div class="tag">Seguimiento Inteligente</div>
        <div class="tag">Cierre Efectivo</div>
      </div>
    </div>
    <div class="deco-num">A</div>
    <div class="corner-ornament"></div>
  </div>


  <!-- ═══════════════════════════════════════════════════════════
       SLIDE 2 — MENTALIDAD DEL ASESOR
  ════════════════════════════════════════════════════════════ -->
  <span class="slide-label">Slide 02 — Mentalidad del Asesor</span>
  <div class="slide s2">
    <div class="slide-header">
      <span class="brand">BL Real Estate · Arcana</span>
      <span class="slide-number">02 / 06</span>
    </div>
    <div class="s2-body">
      <div class="s2-left">
        <div class="section-title">
          Mentalidad
          <span>del Asesor de Élite</span>
        </div>
        <div class="divider-gold"></div>
        <p class="lead-text">
          Antes de marcar el primer número, el asesor de bienes raíces de alto rendimiento
          entiende que vende <strong>transformación de vida</strong>, no metros cuadrados.
          Cada llamada es una oportunidad de crear riqueza patrimonial para una familia.
          Esa convicción es lo que separa al prospectador efectivo del que simplemente llama.
        </p>
        <div class="mindset-grid">
          <div class="mindset-card">
            <div class="mc-icon"><i class="fas fa-brain"></i></div>
            <div class="mc-title">Confianza Total</div>
            <div class="mc-text">Crees en el producto antes de venderlo. Si tú dudaras, ¿por qué creería el prospecto?</div>
          </div>
          <div class="mindset-card">
            <div class="mc-icon"><i class="fas fa-shield-alt"></i></div>
            <div class="mc-title">No Personal</div>
            <div class="mc-text">Un "no" no te rechaza a ti; rechaza información incompleta. Tu trabajo: dar más información.</div>
          </div>
          <div class="mindset-card">
            <div class="mc-icon"><i class="fas fa-chart-line"></i></div>
            <div class="mc-title">Juego de Números</div>
            <div class="mc-text">Por cada 10 llamadas, 2–3 serán calificadas. Por cada 5 visitas, 1 cierre. Sé constante.</div>
          </div>
          <div class="mindset-card">
            <div class="mc-icon"><i class="fas fa-heart"></i></div>
            <div class="mc-title">Empatía Estratégica</div>
            <div class="mc-text">Escucha el 70 %, habla el 30 %. Las mejores preguntas revelan los sueños del prospecto.</div>
          </div>
        </div>
      </div>
      <div class="s2-right">
        <div class="stat-card">
          <div class="stat-num">80%</div>
          <div class="stat-label">de los cierres</div>
          <div class="stat-desc">requieren entre 5 y 12 contactos antes de que el prospecto tome una decisión de compra.</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">+60%</div>
          <div class="stat-label">Más conversiones</div>
          <div class="stat-desc">logran los asesores que personalizan el guión con el nombre, zona e interés específico del prospecto.</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">15 seg</div>
          <div class="stat-label">Ventana de impacto</div>
          <div class="stat-desc">Tienes 15 segundos al inicio de una llamada para captar la atención. La apertura lo es todo.</div>
        </div>
      </div>
    </div>
  </div>


  <!-- ═══════════════════════════════════════════════════════════
       SLIDE 3 — GUIÓN DE APERTURA
  ════════════════════════════════════════════════════════════ -->
  <span class="slide-label">Slide 03 — Guión de Apertura</span>
  <div class="slide s3">
    <div class="slide-header">
      <span class="brand">BL Real Estate · Arcana</span>
      <span class="slide-number">03 / 06</span>
    </div>
    <div class="s3-body">
      <div class="s3-left">
        <div class="section-title">
          Guión de
          <span>Apertura Efectiva</span>
        </div>
        <div class="divider-gold"></div>
        <div class="step-list">
          <div class="step-item">
            <div class="step-num">1</div>
            <div class="step-content">
              <div class="step-title">Saludo + Nombre</div>
              <div class="step-text">Di tu nombre completo y empresa con seguridad. Nunca preguntes si llamas en mal momento; asume que el momento es adecuado.</div>
            </div>
          </div>
          <div class="step-item">
            <div class="step-num">2</div>
            <div class="step-content">
              <div class="step-title">Razón de llamada (elevator pitch)</div>
              <div class="step-text">En 1 oración, enlaza el beneficio con su perfil: inversión, plusvalía, primera vivienda, etc. Sé directo y específico.</div>
            </div>
          </div>
          <div class="step-item">
            <div class="step-num">3</div>
            <div class="step-content">
              <div class="step-title">Pregunta de diagnóstico</div>
              <div class="step-text">Invita a hablar: "¿Actualmente estás en búsqueda activa de vivienda o aún en etapa de exploración?" Escucha con atención.</div>
            </div>
          </div>
          <div class="step-item">
            <div class="step-num">4</div>
            <div class="step-content">
              <div class="step-title">Mini-propuesta de valor</div>
              <div class="step-text">Si hay interés, comparte 1–2 datos concretos: precio de entrada, plusvalía proyectada, amenidades clave. Genera urgencia real.</div>
            </div>
          </div>
          <div class="step-item">
            <div class="step-num">5</div>
            <div class="step-content">
              <div class="step-title">CTA claro — agenda la visita</div>
              <div class="step-text">Cierra siempre con una acción concreta: "¿Te funciona este jueves o prefieres el sábado para visitar el modelo?" Dos opciones, nunca preguntas abiertas.</div>
            </div>
          </div>
        </div>
      </div>
      <div class="s3-right">
        <div class="script-box" style="margin-bottom:16px">
          <div class="sb-label">📞 Llamada en Frío — Guión Modelo</div>
          <div class="sb-text">
            "Buenos días, <strong>[Nombre]</strong>. Mi nombre es <strong>[Tu nombre]</strong>,
            soy asesor de BL Real Estate. Te contacto porque estamos lanzando
            <strong>Arcana Fraccionamiento</strong>, un desarrollo residencial privado
            en Guadalajara con pre-ventas desde <strong>$1.8 MDP</strong> y
            una plusvalía proyectada del <strong>18 % anual</strong>.
            Cuéntame, ¿estás evaluando opciones de inversión o de vivienda propia en este momento?"
          </div>
        </div>
        <div class="script-box">
          <div class="sb-label">💬 WhatsApp — Primer Mensaje</div>
          <div class="sb-text">
            "Hola <strong>[Nombre]</strong> 👋 Soy <strong>[Tu nombre]</strong> de
            BL Real Estate. Te comparto algo que creo puede interesarte:
            <strong>Arcana</strong> es un nuevo fraccionamiento residencial privado
            con acceso controlado, áreas verdes y entrega en 2026.
            Precios de preventa disponibles esta semana.
            ¿Te gustaría ver el brochure? 📎"
          </div>
        </div>
      </div>
    </div>
  </div>


  <!-- ═══════════════════════════════════════════════════════════
       SLIDE 4 — MANEJO DE OBJECIONES
  ════════════════════════════════════════════════════════════ -->
  <span class="slide-label">Slide 04 — Manejo de Objeciones</span>
  <div class="slide s4">
    <div class="slide-header">
      <span class="brand">BL Real Estate · Arcana</span>
      <span class="slide-number">04 / 06</span>
    </div>
    <div class="s4-body">
      <div class="section-title" style="color:var(--navy)">
        Manejo de
        <span style="color:var(--gold);font-weight:300;font-size:28px;text-transform:none;letter-spacing:0;">Objeciones Principales</span>
      </div>
      <div class="objection-grid">
        <div class="obj-card">
          <div class="obj-header">
            <div class="obj-icon"><i class="fas fa-clock"></i></div>
            <div class="obj-q">"Ahora no es buen momento para mí."</div>
          </div>
          <div class="obj-body">
            <div class="obj-a">
              "Entiendo perfectamente, y precisamente por eso te llamo ahora.
              Los precios de preventa de <strong>Arcana terminan este trimestre</strong>;
              después del lanzamiento oficial subirán entre un 10 y 15 %.
              ¿Qué tendría que pasar para que fuera el momento correcto para ti?"
            </div>
          </div>
        </div>
        <div class="obj-card">
          <div class="obj-header">
            <div class="obj-icon"><i class="fas fa-peso-sign"></i></div>
            <div class="obj-q">"Está fuera de mi presupuesto."</div>
          </div>
          <div class="obj-body">
            <div class="obj-a">
              "Muchos de nuestros clientes también lo pensaron al inicio.
              Tenemos esquemas de crédito hipotecario desde <strong>$9,500 / mes</strong>,
              y enganche diferido a 12 meses. ¿Me permites que te muestre cómo
              se ajusta a tus números actuales?"
            </div>
          </div>
        </div>
        <div class="obj-card">
          <div class="obj-header">
            <div class="obj-icon"><i class="fas fa-search"></i></div>
            <div class="obj-q">"Estoy viendo otras opciones."</div>
          </div>
          <div class="obj-body">
            <div class="obj-a">
              "Excelente, es lo más inteligente que puedes hacer.
              Lo que distingue a <strong>Arcana</strong> es su plusvalía garantizada por ubicación
              y el modelo de acceso controlado. ¿Puedo enviarte una comparativa
              objetiva con los desarrollos que estás evaluando?"
            </div>
          </div>
        </div>
        <div class="obj-card">
          <div class="obj-header">
            <div class="obj-icon"><i class="fas fa-user-friends"></i></div>
            <div class="obj-q">"Tengo que consultarlo con mi pareja / familia."</div>
          </div>
          <div class="obj-body">
            <div class="obj-a">
              "Claro, es la decisión correcta. ¿Qué tal si agendamos una visita
              para que ambos puedan ver el modelo y resolver dudas en persona?
              Así toman la decisión con toda la información.
              <strong>¿Este fin de semana les funciona?</strong>"
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>


  <!-- ═══════════════════════════════════════════════════════════
       SLIDE 5 — ESTRATEGIA DE SEGUIMIENTO
  ════════════════════════════════════════════════════════════ -->
  <span class="slide-label">Slide 05 — Seguimiento Inteligente</span>
  <div class="slide s5">
    <div class="slide-header">
      <span class="brand">BL Real Estate · Arcana</span>
      <span class="slide-number">05 / 06</span>
    </div>
    <div class="s5-body">
      <div class="s5-left">
        <div class="section-title">
          Seguimiento
          <span>Inteligente Multi-Canal</span>
        </div>
        <div class="divider-gold"></div>
        <div class="timeline">
          <div class="tl-item">
            <div class="tl-line"></div>
            <div class="tl-dot"><i class="fas fa-phone-alt"></i></div>
            <div class="tl-content">
              <div class="tl-day">Día 0 — Primer Contacto</div>
              <div class="tl-action">Llamada en Frío + WhatsApp inmediato</div>
              <div class="tl-detail">Al terminar la llamada, envía el brochure digital con un mensaje personalizado y tu foto de perfil profesional.</div>
            </div>
          </div>
          <div class="tl-item">
            <div class="tl-line"></div>
            <div class="tl-dot"><i class="fab fa-whatsapp"></i></div>
            <div class="tl-content">
              <div class="tl-day">Día 2 — Valor Agregado</div>
              <div class="tl-action">WhatsApp con contenido de valor</div>
              <div class="tl-detail">Envía un video corto del fraccionamiento, una nota de prensa o un dato de plusvalía de la zona. Sin presión de venta.</div>
            </div>
          </div>
          <div class="tl-item">
            <div class="tl-line"></div>
            <div class="tl-dot"><i class="fas fa-phone-alt"></i></div>
            <div class="tl-content">
              <div class="tl-day">Día 5 — Segunda Llamada</div>
              <div class="tl-action">Check-in y calificación profunda</div>
              <div class="tl-detail">Pregunta qué le pareció el material, cuáles son sus principales preguntas y cuál sería su esquema de pago ideal.</div>
            </div>
          </div>
          <div class="tl-item">
            <div class="tl-line"></div>
            <div class="tl-dot"><i class="fas fa-calendar-check"></i></div>
            <div class="tl-content">
              <div class="tl-day">Día 10 — Agendado</div>
              <div class="tl-action">Confirmación de visita al modelo</div>
              <div class="tl-detail">Confirma con 24 h de anticipación. Personaliza la visita con el nombre de pila y el prototipo que más le interesó.</div>
            </div>
          </div>
        </div>
      </div>
      <div class="s5-right">
        <div class="msg-card">
          <div class="msg-channel"><i class="fab fa-whatsapp" style="color:#25D366;font-size:14px"></i> WhatsApp — Día 2</div>
          <div class="msg-text">
            "Hola <em>[Nombre]</em> 😊 Pensé en ti al ver este dato:
            la zona de Arcana creció un <em>22 % en plusvalía</em> los últimos 3 años.
            ¿Te gustaría que te cuente más sobre el potencial de inversión?"
          </div>
        </div>
        <div class="msg-card">
          <div class="msg-channel"><i class="fas fa-phone-alt" style="font-size:12px;color:var(--gold)"></i> Llamada — Día 5</div>
          <div class="msg-text">
            "Hola <em>[Nombre]</em>, soy <em>[Tu nombre]</em>.
            Quería saber qué te pareció la información que te mandé.
            ¿Tuviste oportunidad de revisarla con <em>[pareja / socio]</em>?"
          </div>
        </div>
        <div class="msg-card">
          <div class="msg-channel"><i class="fas fa-calendar-alt" style="font-size:12px;color:var(--gold)"></i> Confirmación — Día 9</div>
          <div class="msg-text">
            "¡Hola <em>[Nombre]</em>! Confirmo tu visita <em>mañana a las [hora]</em>
            en Arcana. Te espero en la caseta modelo 🏡
            Cualquier cambio, escríbeme. ¡Será un gusto recibirlos!"
          </div>
        </div>
      </div>
    </div>
  </div>


  <!-- ═══════════════════════════════════════════════════════════
       SLIDE 6 — TÉCNICAS DE CIERRE
  ════════════════════════════════════════════════════════════ -->
  <span class="slide-label">Slide 06 — Cierre &amp; Reglas de Oro</span>
  <div class="slide s6">
    <div class="grid-bg"></div>
    <div class="slide-header">
      <span class="brand">BL Real Estate · Arcana</span>
      <span class="slide-number">06 / 06</span>
    </div>
    <div class="s6-body">
      <div class="s6-left">
        <div class="big-title">
          El Arte<br>del <span>Cierre</span>
        </div>
        <div class="sub">
          El cierre no es el final del proceso de venta — es el inicio
          de una relación de largo plazo. Cierra con confianza, no con presión.
        </div>
        <div class="rule-list">
          <div class="rule-item">
            <div class="ri-icon"><i class="fas fa-compress-arrows-alt"></i></div>
            <div class="ri-text"><strong>Cierre por alternativa:</strong> "¿Prefieres el lote en esquina o el que da al parque?" Nunca "¿te interesa o no?"</div>
          </div>
          <div class="rule-item">
            <div class="ri-icon"><i class="fas fa-hourglass-half"></i></div>
            <div class="ri-text"><strong>Urgencia real, no fingida:</strong> Usa datos verdaderos — disponibilidad de lotes, fecha de precio de preventa, fases de entrega.</div>
          </div>
          <div class="rule-item">
            <div class="ri-icon"><i class="fas fa-handshake"></i></div>
            <div class="ri-text"><strong>Silencio estratégico:</strong> Después de hacer la pregunta de cierre, calla. El primero en hablar, concede.</div>
          </div>
          <div class="rule-item">
            <div class="ri-icon"><i class="fas fa-redo-alt"></i></div>
            <div class="ri-text"><strong>No hay cierre fallido:</strong> Si hoy no compra, nutrirás la relación. El 80 % de tus futuros cierres vienen de un seguimiento paciente.</div>
          </div>
        </div>
      </div>
      <div class="s6-right">
        <div class="golden-box">
          <div class="gb-label">⚡ Regla de Oro</div>
          <div class="gb-quote">
            "Las personas no compran propiedades. Compran el estilo de vida
            que esa propiedad les promete. Véndeles el sueño con datos."
          </div>
          <div class="gb-attr">— Principio BL Real Estate</div>
        </div>
        <div style="background:rgba(255,255,255,.05);border-radius:14px;padding:22px 24px;border:1px solid rgba(228,194,146,.15)">
          <div style="font-size:11px;font-weight:700;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-bottom:14px;">✅ Checklist Pre-Llamada</div>
          <div class="checklist">
            <div class="check-item"><i class="fas fa-check-circle"></i> CRM actualizado con datos del prospecto</div>
            <div class="check-item"><i class="fas fa-check-circle"></i> Nombre y zona de interés investigados</div>
            <div class="check-item"><i class="fas fa-check-circle"></i> Brochure y fichas técnicas listas para enviar</div>
            <div class="check-item"><i class="fas fa-check-circle"></i> Disponibilidad de lotes actualizada</div>
            <div class="check-item"><i class="fas fa-check-circle"></i> Agenda con slots abiertos para visitas</div>
            <div class="check-item"><i class="fas fa-check-circle"></i> Mentalidad positiva, energía alta ✨</div>
          </div>
        </div>
      </div>
    </div>
  </div>


  <!-- ═══════════════════════════════════════════════════════════
       FOOTER — BL Real Estate
  ════════════════════════════════════════════════════════════ -->
  <footer>
    <div class="footer-brand">BL <span>Real Estate</span></div>
    <div class="footer-sub">Manual de Ventas Profesional · Arcana Fraccionamiento · Guadalajara, México</div>
    <div class="footer-divider">
      <div class="line"></div>
      <i class="fas fa-gem"></i>
      <div class="line"></div>
    </div>
    <div class="footer-copy">© 2025 BL Real Estate · Todos los derechos reservados · Diseñado para uso interno del equipo comercial</div>
  </footer>

</body>
</html>
