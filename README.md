<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>SRIT — Sistema de Rentas Internas de Solaria</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&display=swap" rel="stylesheet" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --gold: #C9A84C;
    --gold-light: #F0D97A;
    --gold-dark: #8C6A1A;
    --navy: #0D1B2A;
    --navy-mid: #1A2E45;
    --navy-light: #243D56;
    --slate: #4A6078;
    --slate-light: #7A95AE;
    --cream: #FAF7F0;
    --cream-dark: #EDE8DC;
    --white: #FFFFFF;
    --red: #C0392B;
    --green: #1B6B4A;
    --green-light: #E8F5EE;
    --text-on-dark: #E8DFC8;
    --radius: 6px;
    --radius-lg: 12px;
  }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--navy);
    min-height: 100vh;
    font-size: 15px;
    line-height: 1.6;
  }

  /* ── HEADER ─────────────────────────────── */
  header {
    background: var(--navy);
    border-bottom: 3px solid var(--gold);
    padding: 0;
  }

  .header-top {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 18px 48px;
  }

  .emblem {
    width: 56px;
    height: 56px;
    flex-shrink: 0;
  }

  .header-titles h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 22px;
    color: var(--gold-light);
    letter-spacing: 0.04em;
  }

  .header-titles p {
    font-size: 12px;
    color: var(--slate-light);
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .header-strip {
    background: var(--navy-mid);
    padding: 8px 48px;
    display: flex;
    gap: 6px;
    align-items: center;
    font-size: 12px;
    color: var(--slate-light);
  }

  .header-strip span { color: var(--gold); font-weight: 600; }

  /* ── NAV TABS ────────────────────────────── */
  nav {
    background: var(--navy-light);
    padding: 0 48px;
    display: flex;
    gap: 2px;
    border-bottom: 1px solid rgba(201,168,76,0.2);
  }

  .tab-btn {
    padding: 14px 20px;
    border: none;
    background: transparent;
    color: var(--slate-light);
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    border-bottom: 3px solid transparent;
    transition: color 0.2s, border-color 0.2s;
    white-space: nowrap;
    letter-spacing: 0.02em;
    margin-bottom: -1px;
  }

  .tab-btn:hover { color: var(--text-on-dark); }

  .tab-btn.active {
    color: var(--gold-light);
    border-bottom-color: var(--gold);
  }

  /* ── HERO BANNER ─────────────────────────── */
  .hero {
    background: var(--navy-mid);
    padding: 40px 48px;
    border-bottom: 1px solid rgba(201,168,76,0.15);
  }

  .hero h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 30px;
    color: var(--text-on-dark);
    margin-bottom: 6px;
  }

  .hero p {
    color: var(--slate-light);
    max-width: 520px;
    font-size: 14px;
  }

  .type-toggle {
    display: flex;
    gap: 10px;
    margin-top: 20px;
  }

  .type-btn {
    padding: 10px 24px;
    border-radius: 40px;
    border: 1.5px solid rgba(201,168,76,0.4);
    background: transparent;
    color: var(--slate-light);
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
  }

  .type-btn:hover { border-color: var(--gold); color: var(--text-on-dark); }

  .type-btn.active {
    background: var(--gold);
    border-color: var(--gold);
    color: var(--navy);
    font-weight: 600;
  }

  /* ── MAIN LAYOUT ─────────────────────────── */
  main {
    max-width: 1100px;
    margin: 0 auto;
    padding: 36px 48px 64px;
    display: grid;
    grid-template-columns: 1fr 380px;
    gap: 32px;
    align-items: start;
  }

  /* ── SECTIONS ────────────────────────────── */
  .section-card {
    background: var(--white);
    border: 1px solid var(--cream-dark);
    border-radius: var(--radius-lg);
    overflow: hidden;
    margin-bottom: 24px;
  }

  .section-header {
    background: var(--cream-dark);
    padding: 14px 24px;
    display: flex;
    align-items: center;
    gap: 10px;
    border-bottom: 1px solid #D8D0C0;
  }

  .section-header .icon {
    width: 28px;
    height: 28px;
    border-radius: 50%;
    background: var(--navy);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 13px;
    color: var(--gold);
    font-weight: 700;
    flex-shrink: 0;
  }

  .section-header h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 16px;
    color: var(--navy);
  }

  .section-body { padding: 24px; }

  /* ── FORM FIELDS ─────────────────────────── */
  .field-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 16px;
  }

  .field-row.single { grid-template-columns: 1fr; }
  .field-row.triple { grid-template-columns: 1fr 1fr 1fr; }

  .field label {
    display: block;
    font-size: 12px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: var(--slate);
    margin-bottom: 6px;
  }

  .field input,
  .field select {
    width: 100%;
    padding: 10px 14px;
    border: 1.5px solid var(--cream-dark);
    border-radius: var(--radius);
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    color: var(--navy);
    background: var(--cream);
    transition: border-color 0.2s;
    -webkit-appearance: none;
    appearance: none;
  }

  .field input:focus,
  .field select:focus {
    outline: none;
    border-color: var(--gold);
    background: var(--white);
  }

  .field .hint {
    font-size: 11px;
    color: var(--slate-light);
    margin-top: 4px;
  }

  .select-wrap {
    position: relative;
  }

  .select-wrap::after {
    content: '▾';
    position: absolute;
    right: 12px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--slate);
    pointer-events: none;
    font-size: 12px;
  }

  /* ── TRAMOS TABLE ────────────────────────── */
  .tramos-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 13px;
    margin-top: 8px;
  }

  .tramos-table th {
    background: var(--navy);
    color: var(--gold-light);
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    padding: 8px 12px;
    text-align: left;
  }

  .tramos-table td {
    padding: 8px 12px;
    border-bottom: 1px solid var(--cream-dark);
    color: var(--navy);
  }

  .tramos-table tr:last-child td { border-bottom: none; }
  .tramos-table tr.active-tramo td { background: #FFF8E6; font-weight: 600; }
  .tramos-table tr.active-tramo td:first-child { border-left: 3px solid var(--gold); }

  /* ── CALCULATE BUTTON ───────────────────── */
  .calc-btn {
    width: 100%;
    padding: 14px;
    background: var(--navy);
    border: 2px solid var(--gold);
    border-radius: var(--radius);
    color: var(--gold-light);
    font-family: 'DM Serif Display', serif;
    font-size: 17px;
    letter-spacing: 0.04em;
    cursor: pointer;
    transition: all 0.2s;
    margin-top: 8px;
  }

  .calc-btn:hover { background: var(--gold); color: var(--navy); }

  /* ── RESULTS PANEL ──────────────────────── */
  .results-panel {
    background: var(--navy);
    border-radius: var(--radius-lg);
    overflow: hidden;
    position: sticky;
    top: 24px;
  }

  .results-header {
    background: var(--gold);
    padding: 16px 24px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .results-header h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 17px;
    color: var(--navy);
  }

  .results-body { padding: 24px; }

  .result-total {
    border-bottom: 1px solid rgba(255,255,255,0.1);
    padding-bottom: 20px;
    margin-bottom: 20px;
    text-align: center;
  }

  .result-total .label {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--slate-light);
    margin-bottom: 8px;
  }

  .result-total .amount {
    font-family: 'DM Serif Display', serif;
    font-size: 38px;
    color: var(--gold-light);
    line-height: 1;
  }

  .result-total .currency {
    font-size: 16px;
    color: var(--slate-light);
    margin-top: 4px;
  }

  .result-breakdown {}

  .breakdown-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid rgba(255,255,255,0.06);
    font-size: 13px;
  }

  .breakdown-item:last-child { border-bottom: none; }

  .breakdown-item .b-label { color: var(--slate-light); }
  .breakdown-item .b-val { color: var(--text-on-dark); font-weight: 600; }
  .breakdown-item .b-val.highlight { color: var(--gold-light); }

  .effective-rate-bar {
    background: rgba(255,255,255,0.07);
    border-radius: 4px;
    height: 8px;
    margin: 16px 0 8px;
    overflow: hidden;
  }

  .effective-rate-fill {
    background: var(--gold);
    height: 100%;
    border-radius: 4px;
    transition: width 0.6s ease;
  }

  .rate-labels {
    display: flex;
    justify-content: space-between;
    font-size: 11px;
    color: var(--slate-light);
  }

  .empty-state {
    text-align: center;
    padding: 48px 16px;
    color: var(--slate-light);
    font-size: 13px;
    line-height: 1.8;
  }

  .empty-state .icon-lg {
    font-size: 40px;
    margin-bottom: 12px;
    opacity: 0.4;
  }

  .badge {
    display: inline-block;
    padding: 2px 8px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.04em;
    text-transform: uppercase;
  }

  .badge-pn { background: #E8F0FB; color: #1A3A6B; }
  .badge-pj { background: #FFF0D9; color: #7A4800; }

  /* ── INFO BOXES ─────────────────────────── */
  .info-box {
    background: #F0F7FF;
    border: 1px solid #C4DCF5;
    border-radius: var(--radius);
    padding: 12px 16px;
    font-size: 13px;
    color: #1A3A6B;
    margin-bottom: 16px;
    line-height: 1.6;
  }

  .info-box strong { font-weight: 600; }

  /* ── TABS CONTENT ───────────────────────── */
  .tab-content { display: none; }
  .tab-content.active { display: block; }

  /* ── FOOTER ──────────────────────────────── */
  footer {
    background: var(--navy);
    border-top: 3px solid var(--gold);
    padding: 24px 48px;
    color: var(--slate-light);
    font-size: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  footer strong { color: var(--text-on-dark); }

  /* ── RESPONSIVE ──────────────────────────── */
  @media (max-width: 800px) {
    header .header-top, nav, .hero, main, footer { padding-left: 20px; padding-right: 20px; }
    main { grid-template-columns: 1fr; }
    .results-panel { position: static; }
    .field-row { grid-template-columns: 1fr; }
    .field-row.triple { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- ── HEADER ──────────────────────────────── -->
<header>
  <div class="header-top">
    <svg class="emblem" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="28" cy="28" r="27" fill="#0D1B2A" stroke="#C9A84C" stroke-width="2"/>
      <circle cx="28" cy="28" r="4" fill="#C9A84C"/>
      <line x1="28" y1="8" x2="28" y2="20" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="28" y1="36" x2="28" y2="48" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="8" y1="28" x2="20" y2="28" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="36" y1="28" x2="48" y2="28" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="14.1" y1="14.1" x2="22.5" y2="22.5" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="33.5" y1="33.5" x2="41.9" y2="41.9" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="41.9" y1="14.1" x2="33.5" y2="22.5" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <line x1="22.5" y1="33.5" x2="14.1" y2="41.9" stroke="#C9A84C" stroke-width="1.5" stroke-linecap="round"/>
      <circle cx="28" cy="28" r="8" fill="none" stroke="#C9A84C" stroke-width="1" stroke-dasharray="2 3"/>
    </svg>
    <div class="header-titles">
      <h1>Sistema de Rentas Internas de Solaria</h1>
      <p>Ministerio de Hacienda y Finanzas Públicas · República de Solaria</p>
    </div>
  </div>
  <div class="header-strip">
    <span>SRIT</span> &mdash; Calculadora Tributaria Oficial &nbsp;·&nbsp; Año Fiscal 2025
  </div>
</header>

<!-- ── NAV ─────────────────────────────────── -->
<nav>
  <button class="tab-btn active" onclick="switchTab('renta')">Impuesto a la Renta</button>
  <button class="tab-btn" onclick="switchTab('iva')">IVA</button>
  <button class="tab-btn" onclick="switchTab('patrimonio')">Impuesto al Patrimonio</button>
  <button class="tab-btn" onclick="switchTab('sociedades')">Impuesto de Sociedades</button>
  <button class="tab-btn" onclick="switchTab('retencion')">Retenciones</button>
</nav>

<!-- ── HERO ────────────────────────────────── -->
<div class="hero">
  <h2>Calculadora de Impuestos Nacionales</h2>
  <p>Determine el monto exacto de sus obligaciones tributarias conforme a la Ley Tributaria de Solaria vigente para el año fiscal 2025.</p>
  <div class="type-toggle">
    <button class="type-btn active" id="btn-pn" onclick="setPersonType('natural')">Persona Natural</button>
    <button class="type-btn" id="btn-pj" onclick="setPersonType('juridica')">Persona Jurídica</button>
  </div>
</div>

<!-- ── MAIN ────────────────────────────────── -->
<main>
  <div class="left-col">

    <!-- ═══════════════════════════════════════ TAB: RENTA -->
    <div id="tab-renta" class="tab-content active">

      <div class="section-card">
        <div class="section-header">
          <div class="icon">1</div>
          <h3>Datos del Contribuyente</h3>
        </div>
        <div class="section-body">
          <div class="field-row">
            <div class="field">
              <label>Nombre / Razón Social</label>
              <input type="text" id="renta-nombre" placeholder="Ingrese nombre completo" />
            </div>
            <div class="field">
              <label>RIF / Cédula Tributaria</label>
              <input type="text" id="renta-rif" placeholder="SOL-XXXXXXXXXX" />
            </div>
          </div>
          <div class="field-row">
            <div class="field">
              <label>Régimen Tributario</label>
              <div class="select-wrap">
                <select id="renta-regimen">
                  <option value="general">General</option>
                  <option value="simplificado">Simplificado (RESAT)</option>
                  <option value="especial">Especial / Gran Contribuyente</option>
                </select>
              </div>
            </div>
            <div class="field">
              <label>Período Fiscal</label>
              <div class="select-wrap">
                <select id="renta-periodo">
                  <option>2025</option>
                  <option>2024</option>
                  <option>2023</option>
                </select>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="section-card">
        <div class="section-header">
          <div class="icon">2</div>
          <h3>Ingresos y Deducciones</h3>
        </div>
        <div class="section-body">
          <div class="field-row">
            <div class="field">
              <label>Ingresos Brutos Anuales (SOL$)</label>
              <input type="number" id="renta-brutos" placeholder="0.00" min="0" step="100" />
              <div class="hint">Sueldos, honorarios, arrendamientos, dividendos, etc.</div>
            </div>
            <div class="field">
              <label>Ingresos No Gravados (SOL$)</label>
              <input type="number" id="renta-nograv" placeholder="0.00" min="0" step="100" />
              <div class="hint">Herencias, donaciones, indemnizaciones exentas</div>
            </div>
          </div>
          <div class="field-row triple">
            <div class="field">
              <label>Gastos Deducibles (SOL$)</label>
              <input type="number" id="renta-deducibles" placeholder="0.00" min="0" step="100" />
            </div>
            <div class="field">
              <label>Aportes al Seguro Social</label>
              <input type="number" id="renta-ss" placeholder="0.00" min="0" step="100" />
            </div>
            <div class="field">
              <label>Créditos Fiscales (SOL$)</label>
              <input type="number" id="renta-creditos" placeholder="0.00" min="0" step="100" />
            </div>
          </div>

          <div id="pj-fields" style="display:none">
            <div class="info-box">
              <strong>Persona Jurídica:</strong> Las sociedades tributan a tasa fija del 28% sobre renta neta, con depreciación acelerada permitida hasta 40% en activos productivos.
            </div>
            <div class="field-row">
              <div class="field">
                <label>Depreciación de Activos (SOL$)</label>
                <input type="number" id="renta-deprec" placeholder="0.00" min="0" step="100" />
              </div>
              <div class="field">
                <label>Pérdidas de Ejercicios Anteriores</label>
                <input type="number" id="renta-perdidas" placeholder="0.00" min="0" step="100" />
              </div>
            </div>
          </div>

          <button class="calc-btn" onclick="calcRenta()">Calcular Impuesto a la Renta →</button>
        </div>
      </div>

      <div class="section-card">
        <div class="section-header">
          <div class="icon">i</div>
          <h3 id="tramos-title">Tramos del Impuesto a la Renta — Persona Natural (2025)</h3>
        </div>
        <div class="section-body" style="padding:0">
          <table class="tramos-table" id="tramos-table">
            <thead>
              <tr>
                <th>Tramo</th>
                <th>Desde (SOL$)</th>
                <th>Hasta (SOL$)</th>
                <th>Tasa</th>
                <th>Impuesto Fijo</th>
              </tr>
            </thead>
            <tbody id="tramos-body"></tbody>
          </table>
        </div>
      </div>

    </div><!-- end tab-renta -->

    <!-- ═══════════════════════════════════════ TAB: IVA -->
    <div id="tab-iva" class="tab-content">
      <div class="section-card">
        <div class="section-header">
          <div class="icon">1</div>
          <h3>Cálculo del IVA (Impuesto al Valor Agregado)</h3>
        </div>
        <div class="section-body">
          <div class="info-box">
            <strong>Tasas vigentes:</strong> Tasa General 15% · Tasa Reducida 8% (alimentos básicos, medicamentos, libros) · Exportaciones 0% (tasa cero)
          </div>
          <div class="field-row">
            <div class="field">
              <label>Monto Base (SOL$)</label>
              <input type="number" id="iva-monto" placeholder="0.00" min="0" step="0.01" />
            </div>
            <div class="field">
              <label>Categoría del Bien/Servicio</label>
              <div class="select-wrap">
                <select id="iva-tipo">
                  <option value="15">General (15%)</option>
                  <option value="8">Reducida — Alimentos básicos (8%)</option>
                  <option value="8r">Reducida — Medicamentos (8%)</option>
                  <option value="8l">Reducida — Libros y educación (8%)</option>
                  <option value="0">Tasa Cero — Exportaciones (0%)</option>
                  <option value="exento">Exento</option>
                </select>
              </div>
            </div>
          </div>
          <div class="field-row">
            <div class="field">
              <label>¿El monto incluye IVA?</label>
              <div class="select-wrap">
                <select id="iva-incluido">
                  <option value="no">No — es monto neto</option>
                  <option value="si">Sí — es monto total con IVA</option>
                </select>
              </div>
            </div>
            <div class="field">
              <label>IVA Crédito Fiscal (SOL$)</label>
              <input type="number" id="iva-credito" placeholder="0.00" min="0" step="0.01" />
              <div class="hint">IVA soportado en compras del período</div>
            </div>
          </div>
          <button class="calc-btn" onclick="calcIVA()">Calcular IVA →</button>
        </div>
      </div>
    </div>

    <!-- ═══════════════════════════════════════ TAB: PATRIMONIO -->
    <div id="tab-patrimonio" class="tab-content">
      <div class="section-card">
        <div class="section-header">
          <div class="icon">1</div>
          <h3>Impuesto al Patrimonio Neto</h3>
        </div>
        <div class="section-body">
          <div class="info-box">
            <strong>Aplica a:</strong> Personas naturales con patrimonio neto superior a SOL$ 500,000. Tasa anual progresiva del 0.5% al 2.5%.
          </div>
          <div class="field-row">
            <div class="field">
              <label>Bienes Inmuebles (SOL$)</label>
              <input type="number" id="pat-inmuebles" placeholder="0.00" min="0" step="1000" />
            </div>
            <div class="field">
              <label>Vehículos y Maquinaria (SOL$)</label>
              <input type="number" id="pat-vehiculos" placeholder="0.00" min="0" step="1000" />
            </div>
          </div>
          <div class="field-row">
            <div class="field">
              <label>Activos Financieros (SOL$)</label>
              <input type="number" id="pat-financieros" placeholder="0.00" min="0" step="1000" />
              <div class="hint">Cuentas bancarias, acciones, bonos</div>
            </div>
            <div class="field">
              <label>Otros Activos (SOL$)</label>
              <input type="number" id="pat-otros" placeholder="0.00" min="0" step="1000" />
            </div>
          </div>
          <div class="field-row">
            <div class="field">
              <label>Pasivos / Deudas (SOL$)</label>
              <input type="number" id="pat-pasivos" placeholder="0.00" min="0" step="1000" />
              <div class="hint">Hipotecas, créditos, deudas documentadas</div>
            </div>
            <div class="field">
              <label>Mínimo Exento Familiar</label>
              <div class="select-wrap">
                <select id="pat-cargas">
                  <option value="0">Sin cargas familiares — SOL$ 500,000</option>
                  <option value="100000">1-2 dependientes — SOL$ 600,000</option>
                  <option value="200000">3+ dependientes — SOL$ 700,000</option>
                </select>
              </div>
            </div>
          </div>
          <button class="calc-btn" onclick="calcPatrimonio()">Calcular Impuesto al Patrimonio →</button>
        </div>
      </div>
    </div>

    <!-- ═══════════════════════════════════════ TAB: SOCIEDADES -->
    <div id="tab-sociedades" class="tab-content">
      <div class="section-card">
        <div class="section-header">
          <div class="icon">1</div>
          <h3>Impuesto de Sociedades — Personas Jurídicas</h3>
        </div>
        <div class="section-body">
          <div class="info-box">
            <strong>Tasas:</strong> PYME (ingresos &lt; SOL$ 2M): 20% · Mediana empresa (SOL$ 2M–10M): 25% · Gran empresa (&gt; SOL$ 10M): 28% · Sector financiero: 32%
          </div>
          <div class="field-row">
            <div class="field">
              <label>Tipo de Sociedad</label>
              <div class="select-wrap">
                <select id="soc-tipo" onchange="calcSociedades()">
                  <option value="sa">S.A. — Sociedad Anónima</option>
                  <option value="srl">S.R.L. — Responsabilidad Limitada</option>
                  <option value="coop">Cooperativa</option>
                  <option value="fin">Entidad Financiera</option>
                </select>
              </div>
            </div>
            <div class="field">
              <label>Sector Económico</label>
              <div class="select-wrap">
                <select id="soc-sector">
                  <option value="normal">Comercio / Servicios</option>
                  <option value="agro">Agropecuario (beneficio 15%)</option>
                  <option value="tech">Tecnología e Innovación (beneficio 18%)</option>
                  <option value="export">Exportador (beneficio 20%)</option>
                </select>
              </div>
            </div>
          </div>
          <div class="field-row">
            <div class="field">
              <label>Ingresos Netos Anuales (SOL$)</label>
              <input type="number" id="soc-ingresos" placeholder="0.00" min="0" step="1000" />
            </div>
            <div class="field">
              <label>Costos y Gastos Deducibles (SOL$)</label>
              <input type="number" id="soc-gastos" placeholder="0.00" min="0" step="1000" />
            </div>
          </div>
          <div class="field-row triple">
            <div class="field">
              <label>Depreciación (SOL$)</label>
              <input type="number" id="soc-deprec" placeholder="0.00" min="0" step="1000" />
            </div>
            <div class="field">
              <label>Pérdidas Anteriores (SOL$)</label>
              <input type="number" id="soc-perdidas" placeholder="0.00" min="0" step="1000" />
            </div>
            <div class="field">
              <label>Créditos Fiscales (SOL$)</label>
              <input type="number" id="soc-creditos" placeholder="0.00" min="0" step="1000" />
            </div>
          </div>
          <button class="calc-btn" onclick="calcSociedades()">Calcular Impuesto de Sociedades →</button>
        </div>
      </div>
    </div>

    <!-- ═══════════════════════════════════════ TAB: RETENCIONES -->
    <div id="tab-retencion" class="tab-content">
      <div class="section-card">
        <div class="section-header">
          <div class="icon">1</div>
          <h3>Cálculo de Retenciones en la Fuente</h3>
        </div>
        <div class="section-body">
          <div class="info-box">
            <strong>Retención en la fuente:</strong> Mecanismo de recaudo anticipado del impuesto sobre pagos realizados a terceros.
          </div>
          <div class="field-row">
            <div class="field">
              <label>Tipo de Pago / Concepto</label>
              <div class="select-wrap">
                <select id="ret-tipo">
                  <option value="honorarios">Honorarios profesionales (10%)</option>
                  <option value="arrendamiento">Arrendamiento inmuebles (8%)</option>
                  <option value="dividendos">Dividendos (5%)</option>
                  <option value="intereses">Intereses financieros (6%)</option>
                  <option value="servicios">Servicios generales (4%)</option>
                  <option value="compras">Compras de bienes (2.5%)</option>
                  <option value="exterior">Pagos al exterior (15%)</option>
                </select>
              </div>
            </div>
            <div class="field">
              <label>Monto del Pago (SOL$)</label>
              <input type="number" id="ret-monto" placeholder="0.00" min="0" step="100" />
            </div>
          </div>
          <div class="field-row">
            <div class="field">
              <label>¿Beneficiario es Gran Contribuyente?</label>
              <div class="select-wrap">
                <select id="ret-gc">
                  <option value="no">No</option>
                  <option value="si">Sí (reducción 50% de retención)</option>
                </select>
              </div>
            </div>
            <div class="field">
              <label>Cantidad de Pagos en el Mes</label>
              <input type="number" id="ret-cantidad" placeholder="1" min="1" step="1" value="1" />
            </div>
          </div>
          <button class="calc-btn" onclick="calcRetencion()">Calcular Retención →</button>
        </div>
      </div>
    </div>

  </div><!-- end left-col -->

  <!-- ── RESULTS PANEL ──────────────────────── -->
  <div class="results-panel" id="results-panel">
    <div class="results-header">
      <h3>Liquidación Tributaria</h3>
    </div>
    <div class="results-body" id="results-body">
      <div class="empty-state">
        <div class="icon-lg">⚖</div>
        Complete los datos y presione<br/><strong>"Calcular"</strong> para obtener<br/>su liquidación oficial.
      </div>
    </div>
  </div>

</main>

<!-- ── FOOTER ───────────────────────────────── -->
<footer>
  <div>
    <strong>República de Solaria</strong> — Sistema de Rentas Internas (SRIT) <br/>
    Los cálculos son referenciales. Para declaraciones oficiales, acuda a su oficina tributaria regional.
  </div>
  <div style="text-align:right">
    Ley Tributaria N° 2847-S · Vigente desde 01/01/2025<br/>
    <span style="color:var(--gold)">srit.gob.sol</span>
  </div>
</footer>

<script>
  let personType = 'natural';

  // ── PERSON TYPE ────────────────────────────
  function setPersonType(type) {
    personType = type;
    document.getElementById('btn-pn').classList.toggle('active', type === 'natural');
    document.getElementById('btn-pj').classList.toggle('active', type === 'juridica');
    const pjFields = document.getElementById('pj-fields');
    if (pjFields) pjFields.style.display = type === 'juridica' ? 'block' : 'none';
    updateTramos();
    showEmpty();
  }

  // ── TABS ───────────────────────────────────
  function switchTab(tab) {
    document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(t => t.classList.remove('active'));
    document.getElementById('tab-' + tab).classList.add('active');
    event.target.classList.add('active');
    showEmpty();
  }

  function showEmpty() {
    document.getElementById('results-body').innerHTML = `
      <div class="empty-state">
        <div class="icon-lg">⚖</div>
        Complete los datos y presione<br/><strong>"Calcular"</strong> para obtener<br/>su liquidación oficial.
      </div>`;
  }

  // ── TRAMOS ─────────────────────────────────
  const tramosPN = [
    { desde: 0,       hasta: 30000,   tasa: 0,    fijo: 0 },
    { desde: 30001,   hasta: 60000,   tasa: 0.05, fijo: 0 },
    { desde: 60001,   hasta: 100000,  tasa: 0.10, fijo: 1500 },
    { desde: 100001,  hasta: 200000,  tasa: 0.16, fijo: 5500 },
    { desde: 200001,  hasta: 400000,  tasa: 0.22, fijo: 21500 },
    { desde: 400001,  hasta: 800000,  tasa: 0.28, fijo: 65500 },
    { desde: 800001,  hasta: Infinity, tasa: 0.34, fijo: 177500 },
  ];

  const tramosPJ = [
    { desde: 0,      hasta: 2000000,  tasa: 0.20, fijo: 0 },
    { desde: 2000001, hasta: 10000000, tasa: 0.25, fijo: 400000 },
    { desde: 10000001, hasta: Infinity, tasa: 0.28, fijo: 2400000 },
  ];

  function fmtSOL(n) {
    return 'SOL$ ' + Math.round(n).toLocaleString('es-ES');
  }

  function updateTramos() {
    const tramos = personType === 'natural' ? tramosPN : tramosPJ;
    const title = personType === 'natural'
      ? 'Tramos del Impuesto a la Renta — Persona Natural (2025)'
      : 'Tramos del Impuesto a la Renta — Persona Jurídica (2025)';
    document.getElementById('tramos-title').textContent = title;
    const tbody = document.getElementById('tramos-body');
    tbody.innerHTML = tramos.map((t, i) => `
      <tr id="tramo-${i}">
        <td>Tramo ${i+1}</td>
        <td>${fmtSOL(t.desde)}</td>
        <td>${t.hasta === Infinity ? 'En adelante' : fmtSOL(t.hasta)}</td>
        <td>${(t.tasa * 100).toFixed(0)}%</td>
        <td>${fmtSOL(t.fijo)}</td>
      </tr>`).join('');
  }

  updateTramos();

  // ── CALC RENTA ─────────────────────────────
  function calcRenta() {
    const brutos = parseFloat(document.getElementById('renta-brutos').value) || 0;
    const nograv = parseFloat(document.getElementById('renta-nograv').value) || 0;
    const deducibles = parseFloat(document.getElementById('renta-deducibles').value) || 0;
    const ss = parseFloat(document.getElementById('renta-ss').value) || 0;
    const creditos = parseFloat(document.getElementById('renta-creditos').value) || 0;
    const deprec = personType === 'juridica' ? (parseFloat(document.getElementById('renta-deprec')?.value) || 0) : 0;
    const perdidas = personType === 'juridica' ? (parseFloat(document.getElementById('renta-perdidas')?.value) || 0) : 0;

    const rentaGravable = Math.max(0, brutos - nograv - deducibles - ss - deprec - perdidas);

    let impuesto = 0;
    let tramoActivo = -1;

    if (personType === 'natural') {
      const tramos = tramosPN;
      for (let i = 0; i < tramos.length; i++) {
        if (rentaGravable > tramos[i].desde) {
          tramoActivo = i;
          const base = rentaGravable - tramos[i].desde;
          impuesto = tramos[i].fijo + base * tramos[i].tasa;
        }
      }
    } else {
      const tasa = rentaGravable <= 2000000 ? 0.20 : rentaGravable <= 10000000 ? 0.25 : 0.28;
      impuesto = rentaGravable * tasa;
      tramoActivo = rentaGravable <= 2000000 ? 0 : rentaGravable <= 10000000 ? 1 : 2;
    }

    // highlight tramo
    document.querySelectorAll('[id^="tramo-"]').forEach(r => r.classList.remove('active-tramo'));
    if (tramoActivo >= 0) {
      const tr = document.getElementById('tramo-' + tramoActivo);
      if (tr) tr.classList.add('active-tramo');
    }

    const impuestoNeto = Math.max(0, impuesto - creditos);
    const tasaEfectiva = brutos > 0 ? (impuestoNeto / brutos * 100) : 0;

    showResults({
      tipo: 'Impuesto a la Renta',
      badge: personType === 'natural' ? 'badge-pn' : 'badge-pj',
      badgeLabel: personType === 'natural' ? 'Persona Natural' : 'Persona Jurídica',
      total: impuestoNeto,
      tasaEfectiva,
      items: [
        { l: 'Ingresos brutos', v: fmtSOL(brutos) },
        { l: 'Ingresos no gravados', v: '− ' + fmtSOL(nograv) },
        { l: 'Deducciones', v: '− ' + fmtSOL(deducibles + ss + deprec + perdidas) },
        { l: 'Renta gravable neta', v: fmtSOL(rentaGravable), hi: true },
        { l: 'Impuesto calculado', v: fmtSOL(impuesto) },
        { l: 'Créditos fiscales', v: '− ' + fmtSOL(creditos) },
        { l: 'Impuesto a pagar', v: fmtSOL(impuestoNeto), hi: true },
      ]
    });
  }

  // ── CALC IVA ───────────────────────────────
  function calcIVA() {
    let monto = parseFloat(document.getElementById('iva-monto').value) || 0;
    const tipo = document.getElementById('iva-tipo').value;
    const incluido = document.getElementById('iva-incluido').value;
    const credito = parseFloat(document.getElementById('iva-credito').value) || 0;

    const tasas = { '15': 0.15, '8': 0.08, '8r': 0.08, '8l': 0.08, '0': 0, 'exento': 0 };
    const tasa = tasas[tipo] || 0;

    let base = monto;
    let ivaDebito = 0;

    if (tipo === 'exento') {
      base = monto;
      ivaDebito = 0;
    } else if (incluido === 'si') {
      base = monto / (1 + tasa);
      ivaDebito = monto - base;
    } else {
      base = monto;
      ivaDebito = monto * tasa;
    }

    const ivaAPagar = Math.max(0, ivaDebito - credito);
    const tasaStr = tipo === 'exento' ? 'Exento' : (tasa * 100).toFixed(0) + '%';

    showResults({
      tipo: 'IVA — Impuesto al Valor Agregado',
      badge: 'badge-pn',
      badgeLabel: 'Tasa ' + tasaStr,
      total: ivaAPagar,
      tasaEfectiva: base > 0 ? (ivaAPagar / base * 100) : 0,
      items: [
        { l: 'Monto base (sin IVA)', v: fmtSOL(base) },
        { l: 'Tasa aplicable', v: tasaStr },
        { l: 'IVA débito fiscal', v: fmtSOL(ivaDebito) },
        { l: 'IVA crédito fiscal', v: '− ' + fmtSOL(credito) },
        { l: 'IVA neto a pagar', v: fmtSOL(ivaAPagar), hi: true },
        { l: 'Total factura (con IVA)', v: fmtSOL(base + ivaDebito) },
      ]
    });
  }

  // ── CALC PATRIMONIO ────────────────────────
  function calcPatrimonio() {
    const inmuebles = parseFloat(document.getElementById('pat-inmuebles').value) || 0;
    const vehiculos = parseFloat(document.getElementById('pat-vehiculos').value) || 0;
    const financieros = parseFloat(document.getElementById('pat-financieros').value) || 0;
    const otros = parseFloat(document.getElementById('pat-otros').value) || 0;
    const pasivos = parseFloat(document.getElementById('pat-pasivos').value) || 0;
    const exento = 500000 + (parseInt(document.getElementById('pat-cargas').value) || 0);

    const activos = inmuebles + vehiculos + financieros + otros;
    const patrimonioNeto = Math.max(0, activos - pasivos);
    const patrimonioGravable = Math.max(0, patrimonioNeto - exento);

    let tasa = 0;
    let desc = 'Exento';
    if (patrimonioGravable > 0 && patrimonioGravable <= 500000) { tasa = 0.005; desc = '0.5%'; }
    else if (patrimonioGravable > 500000 && patrimonioGravable <= 1500000) { tasa = 0.010; desc = '1.0%'; }
    else if (patrimonioGravable > 1500000 && patrimonioGravable <= 3000000) { tasa = 0.015; desc = '1.5%'; }
    else if (patrimonioGravable > 3000000 && patrimonioGravable <= 6000000) { tasa = 0.020; desc = '2.0%'; }
    else if (patrimonioGravable > 6000000) { tasa = 0.025; desc = '2.5%'; }

    const impuesto = patrimonioGravable * tasa;

    showResults({
      tipo: 'Impuesto al Patrimonio Neto',
      badge: 'badge-pn',
      badgeLabel: 'Persona Natural',
      total: impuesto,
      tasaEfectiva: patrimonioNeto > 0 ? (impuesto / patrimonioNeto * 100) : 0,
      items: [
        { l: 'Total activos declarados', v: fmtSOL(activos) },
        { l: 'Pasivos deducibles', v: '− ' + fmtSOL(pasivos) },
        { l: 'Patrimonio neto', v: fmtSOL(patrimonioNeto), hi: true },
        { l: 'Mínimo exento', v: '− ' + fmtSOL(exento) },
        { l: 'Patrimonio gravable', v: fmtSOL(patrimonioGravable) },
        { l: 'Tasa aplicable', v: desc },
        { l: 'Impuesto a pagar', v: fmtSOL(impuesto), hi: true },
      ]
    });
  }

  // ── CALC SOCIEDADES ────────────────────────
  function calcSociedades() {
    const ingresos = parseFloat(document.getElementById('soc-ingresos').value) || 0;
    const gastos = parseFloat(document.getElementById('soc-gastos').value) || 0;
    const deprec = parseFloat(document.getElementById('soc-deprec').value) || 0;
    const perdidas = parseFloat(document.getElementById('soc-perdidas').value) || 0;
    const creditos = parseFloat(document.getElementById('soc-creditos').value) || 0;
    const tipo = document.getElementById('soc-tipo').value;
    const sector = document.getElementById('soc-sector').value;

    const rentaNeta = Math.max(0, ingresos - gastos - deprec - perdidas);

    let tasa = tipo === 'fin' ? 0.32 : (rentaNeta <= 2000000 ? 0.20 : rentaNeta <= 10000000 ? 0.25 : 0.28);
    let descSector = '';

    if (sector === 'agro' && tipo !== 'fin') { tasa = Math.max(0.15, tasa - 0.05); descSector = '(beneficio agropecuario −5%)'; }
    else if (sector === 'tech' && tipo !== 'fin') { tasa = Math.max(0.18, tasa - 0.05); descSector = '(beneficio tecnología −5%)'; }
    else if (sector === 'export' && tipo !== 'fin') { tasa = Math.max(0.20, tasa - 0.03); descSector = '(beneficio exportador −3%)'; }

    const impuestoBruto = rentaNeta * tasa;
    const impuestoNeto = Math.max(0, impuestoBruto - creditos);

    showResults({
      tipo: 'Impuesto de Sociedades',
      badge: 'badge-pj',
      badgeLabel: tipo.toUpperCase(),
      total: impuestoNeto,
      tasaEfectiva: ingresos > 0 ? (impuestoNeto / ingresos * 100) : 0,
      items: [
        { l: 'Ingresos netos', v: fmtSOL(ingresos) },
        { l: 'Gastos deducibles', v: '− ' + fmtSOL(gastos) },
        { l: 'Depreciación + pérdidas', v: '− ' + fmtSOL(deprec + perdidas) },
        { l: 'Renta neta gravable', v: fmtSOL(rentaNeta), hi: true },
        { l: 'Tasa aplicable ' + descSector, v: (tasa * 100).toFixed(0) + '%' },
        { l: 'Impuesto bruto', v: fmtSOL(impuestoBruto) },
        { l: 'Créditos fiscales', v: '− ' + fmtSOL(creditos) },
        { l: 'Impuesto a pagar', v: fmtSOL(impuestoNeto), hi: true },
      ]
    });
  }

  // ── CALC RETENCION ─────────────────────────
  function calcRetencion() {
    const monto = parseFloat(document.getElementById('ret-monto').value) || 0;
    const tipo = document.getElementById('ret-tipo').value;
    const gc = document.getElementById('ret-gc').value;
    const cantidad = parseInt(document.getElementById('ret-cantidad').value) || 1;

    const tasas = {
      honorarios: 0.10, arrendamiento: 0.08, dividendos: 0.05,
      intereses: 0.06, servicios: 0.04, compras: 0.025, exterior: 0.15
    };

    let tasa = tasas[tipo] || 0;
    if (gc === 'si') tasa = tasa * 0.5;

    const retencionPorPago = monto * tasa;
    const retencionTotal = retencionPorPago * cantidad;
    const netoRecibido = (monto - retencionPorPago) * cantidad;

    showResults({
      tipo: 'Retención en la Fuente',
      badge: 'badge-pn',
      badgeLabel: 'Art. 87 LTS',
      total: retencionTotal,
      tasaEfectiva: tasa * 100,
      items: [
        { l: 'Monto bruto por pago', v: fmtSOL(monto) },
        { l: 'Tasa de retención', v: (tasa * 100).toFixed(1) + '%' },
        { l: 'Retención por pago', v: fmtSOL(retencionPorPago) },
        { l: 'Número de pagos', v: cantidad + ' pago(s)' },
        { l: 'Total retenido en el mes', v: fmtSOL(retencionTotal), hi: true },
        { l: 'Neto a recibir (total)', v: fmtSOL(netoRecibido) },
      ]
    });
  }

  // ── SHOW RESULTS ───────────────────────────
  function showResults({ tipo, badge, badgeLabel, total, tasaEfectiva, items }) {
    const maxRate = 34;
    const barW = Math.min(100, (tasaEfectiva / maxRate * 100));

    const rows = items.map(it => `
      <div class="breakdown-item">
        <span class="b-label">${it.l}</span>
        <span class="b-val ${it.hi ? 'highlight' : ''}">${it.v}</span>
      </div>`).join('');

    document.getElementById('results-body').innerHTML = `
      <div style="margin-bottom:12px">
        <span class="badge ${badge}">${badgeLabel}</span>
        <span style="font-size:12px;color:var(--slate-light);margin-left:8px">${tipo}</span>
      </div>
      <div class="result-total">
        <div class="label">Total a Pagar</div>
        <div class="amount">${Math.round(total).toLocaleString('es-ES')}</div>
        <div class="currency">SOL$ — Soles de Solaria</div>
      </div>
      <div class="result-breakdown">${rows}</div>
      <div style="margin-top:20px">
        <div style="font-size:11px;color:var(--slate-light);margin-bottom:6px;text-transform:uppercase;letter-spacing:.06em">Tasa Efectiva</div>
        <div class="effective-rate-bar">
          <div class="effective-rate-fill" style="width:${barW}%"></div>
        </div>
        <div class="rate-labels">
          <span>${tasaEfectiva.toFixed(2)}%</span>
          <span>Máx. ${maxRate}%</span>
        </div>
      </div>
      <div style="margin-top:24px;padding-top:16px;border-top:1px solid rgba(255,255,255,0.08);font-size:11px;color:var(--slate-light);line-height:1.7">
        ⚠ Cálculo referencial. Sujeto a verificación por el SRIT.<br/>
        Vencimiento declaración: <strong style="color:var(--text-on-dark)">31 de marzo 2026</strong>
      </div>`;
  }
</script>
</body>
</html>
