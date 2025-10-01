<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Painel de e-mails — Setembro 2025 | Datatem</title>
<style>
  :root{
    --bg:#f7fafc; --surface:#ffffff; --muted:#eef2f7; --line:#e5e7eb; --ink:#0f172a; --soft:#475569;
    --shadow:0 8px 24px rgba(2,6,23,.08);

    /* Paleta unificada (azul + verde) */
    --p-blue:#38bdf8;          /* sky-400 */
    --p-blue-strong:#0ea5e9;   /* sky-500 */
    --p-green:#22c55e;         /* green-500 */
  }
  *{box-sizing:border-box}
  html,body{margin:0;background:var(--bg);color:var(--ink);font:15px/1.5 system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Inter,Arial,sans-serif}

  /* Abrimos a tela e garantimos nada “comer” info */
  .app{max-width:1580px;margin:28px auto;padding:0 16px 72px}

  header{display:flex;flex-wrap:wrap;gap:12px;align-items:center;justify-content:space-between;margin-bottom:12px}
  .title{font-size:22px;font-weight:700}
  .controls{display:flex;flex-wrap:wrap;gap:12px;align-items:center} .controls .legend{margin-left:auto}
  .pill{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:10px 12px;display:flex;gap:8px;align-items:center;box-shadow:var(--shadow)}
  select{border:1px solid var(--line);background:#fff;border-radius:8px;padding:8px 10px;font:inherit;color:var(--ink);min-width:160px}

  .layout{display:grid;grid-template-columns:340px 1fr;gap:22px;margin-top:18px} .left-col{display:grid;gap:16px;align-content:start}

  aside{background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:16px;box-shadow:var(--shadow);position:static;height:auto}
  aside h3{margin:6px 0 10px;font-size:14px}
  aside .help{font-size:13px;color:var(--soft)}
  .disclaimer{margin-top:10px;padding:10px 12px;border-radius:10px;background:#7a1b2c0f;border:1px dashed #7a1b2c30;color:#7a1b2c;opacity:.9;font-size:12px}

  main{display:grid;gap:16px}
  .card{background:var(--surface);border:1px solid var(--line);border-radius:14px;box-shadow:var(--shadow);transition:transform .12s ease, box-shadow .12s ease; overflow:visible}
  .card:hover{transform:translateY(-1px);box-shadow:0 12px 32px rgba(2,6,23,.12)}
  .card h2{margin:0;padding:16px 18px;border-bottom:1px solid var(--line);font-size:16px;display:flex;justify-content:space-between;align-items:center}

  .card .body{padding:18px}

  /* KPIs */
  .kpi-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
  .kpi{border:1px solid var(--line);border-radius:12px;padding:12px;background:#fff;min-width:0}
  .kpi .label{font-size:12px;color:var(--soft)}
  .kpi .v{font-weight:700;font-size:18px;white-space:nowrap;color:var(--p-blue)}

  /* Charts */
  .dual{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:10px}
  .mini{border:1px dashed var(--line);border-radius:12px;padding:10px;background:#fff}
  .legend{display:flex;gap:10px;align-items:center;font-size:12px;color:#475569;justify-content:space-between}
  .dot{width:10px;height:10px;border-radius:999px;display:inline-block}
  canvas{width:100%;height:280px;border:1px solid var(--line);border-radius:12px;background:#fff}

  /* Tabela */
  .table-wrap{overflow-x:auto; overflow-y:visible; border:1px solid var(--line);border-radius:12px}
  table{width:100%;border-collapse:separate;border-spacing:0}
  th,td{border-bottom:1px solid var(--line);text-align:left;padding:12px 12px;font-size:13px}
  th{font-size:12px;color:#64748b;font-weight:600}
  .num{ text-align:right } .center{ text-align:center }

  /* Agora com coluna extra “Disparos” */
  .emails-table th:nth-child(1){min-width:520px}                 /* Nome */
  .emails-table th:nth-child(2){width:220px; white-space:nowrap} /* Tags */
  .emails-table th:nth-child(3){width:130px; white-space:nowrap} /* Disparos */
  .emails-table th:nth-child(4),
  .emails-table th:nth-child(5),
  .emails-table th:nth-child(7),
  .emails-table th:nth-child(8){width:120px; white-space:nowrap} /* % cols */
  .emails-table th:nth-child(6){width:180px; white-space:nowrap} /* Data e hora */
  .emails-table th:nth-child(9){width:170px; white-space:nowrap} /* Mês */
  .emails-table th:nth-child(10){width:160px; white-space:nowrap}/* Segmento */

  .emails-table td.name-cell{white-space:normal; line-height:1.35; word-break:break-word}
  .emails-table td.tags-cell{white-space:nowrap}

  .seg-badge{border:1px solid var(--line);border-radius:999px;padding:4px 10px;font-size:12px}
  .seg-badge.clientes{background:#dbeafe;color:#1e40af}
  .seg-badge.leads{background:#ecfeff;color:#0369a1}
  .seg-badge.inativos{background:#fef3c7;color:#92400e}
  .month-pill{display:inline-flex;align-items:center;gap:6px;padding:4px 10px;border-radius:999px;font-size:12px;font-weight:600;box-shadow:var(--shadow);background:#dcfce7;color:#065f46}

  /* RD Station totals + Donut (alinhado à direita) */
  .stats-wrap{display:grid;grid-template-columns:1fr;gap:12px;align-items:start}
  .stats-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px;align-content:start}
  .stat{border:1px solid var(--line);border-radius:12px;padding:12px;background:#fff}
  .stat .label{font-size:12px;color:#64748b;margin-bottom:6px}
  .stat .value{font-weight:800;font-size:22px}
  .stat .hint{font-size:12px;color:#64748b;margin-top:4px}
  .stat.total{grid-column:1/-1;display:flex;justify-content:space-between;align-items:baseline;gap:12px}

  .pie-card{border:1px solid var(--line);border-radius:12px;background:#fff;padding:12px}
  .pie-card canvas{width:100%;height:300px;border:1px solid var(--line);border-radius:12px;background:#fff}
  .pie-legend{display:flex;flex-direction:column;gap:6px;margin-top:8px;font-size:12px;color:#475569}
  .pie-legend .row{display:flex;justify-content:space-between;gap:10px}
  .pie-legend .dot{width:10px;height:10px;border-radius:999px;display:inline-block;margin-right:6px}

  /* Tags/Badges */
  .badge{display:inline-block;padding:4px 10px;border-radius:999px;border:1px solid var(--line);font-size:12px}
  .badge.mc{background:#dbeafe;color:#1e40af;border-color:#bfdbfe}
  .badge.warn{background:#fff7ed;color:#7c2d12;border-color:#fde68a}

  /* Tooltip + Toast */
  .floating-tip{position:fixed;pointer-events:none;background:#0b1220;color:#fff;font:12px system-ui;padding:10px 12px;border-radius:10px;border:1px solid #0f172a;box-shadow:0 10px 24px rgba(0,0,0,.35);max-width:420px;z-index:9999;display:none}
  .floating-tip b{color:#fff}
  .floating-tip .muted{color:#cbd5e1}
  .toast{position:fixed;right:16px;bottom:16px;background:#e0f2fe;color:#1e40af;border:1px solid #bfdbfe;padding:10px 12px;border-radius:10px;box-shadow:var(--shadow);font-size:13px;display:none}
</style>
</head>
<body>
<div class="app">
  <header>
    <div class="title">Painel de e-mails: Setembro/2025</div>
    <div class="controls">
      <div class="pill">
        <label for="segmento">Segmento:</label>
        <select id="segmento">
          <option>Geral</option>
          <option>Clientes</option>
          <option>Leads</option>
          <option>Inativos</option>
        </select>
      </div>
      <div class="pill">
        <label for="semana">Semana:</label>
        <select id="semana">
          <option value="all">Todas</option>
          <option value="w1">Semana 1 (01–07)</option>
          <option value="w2">Semana 2 (08–14)</option>
          <option value="w3">Semana 3 (15–21)</option>
          <option value="w4">Semana 4 (22–31)</option>
        </select>
      </div>
      <div class="pill legend">
        <span><span class="dot" style="background:var(--p-blue)"></span> Setembro/2025</span>
      </div>
    </div>
  </header>

  <!-- Números por segmentos atualmente no RD Station + Donut -->
<div class="layout">
    <div class="left-col">
<aside>
      <h3>Como ler esta página</h3>
      <div class="help">
        <p><b>Entrega</b>: <span class="tip-anchor" data-tip="Fórmula: entregues ÷ selecionados × 100">percentual que chega à caixa de entrada</span>.</p>
        <p><b>Abertura</b>: <span class="tip-anchor" data-tip="Fórmula: aberturas únicas ÷ entregues × 100">quem recebeu e abriu</span>.</p>
        <p><b>CTR</b>: <span class="tip-anchor" data-tip="Fórmula: cliques únicos ÷ entregues × 100">quem recebeu e clicou</span>.</p>
        <p><b>CTOR</b>: <span class="tip-anchor" data-tip="Fórmula: cliques únicos ÷ aberturas únicas × 100">qualidade do conteúdo/CTA</span>.</p>
        <p>Use os seletores de <b>Segmento</b> e <b>Semana</b> para fatiar os resultados.</p>
      </div>
      <div class="disclaimer">
        Dashboard interna do time Datatem (Marketing), desenvolvida por <b>Mozart - Marketing</b>. Resultados calculados a partir dos envios de <b>Setembro/2025</b>.
      </div>
    </aside>
<section class="card stats-card">
    <h2>Números por segmentos atualmente no RD Station</h2>
    <div class="body">
      <div class="stats-wrap">
        <div class="stats-grid">
          <div class="stat">
            <div class="label">Leads que são <b>Clientes</b></div>
            <div class="value" data-key="clientes">—</div>
            <div class="hint">Integram a base de leads com status de cliente</div>
          </div>
          <div class="stat">
            <div class="label">Leads que são <b>Inativos</b></div>
            <div class="value" data-key="inativos">—</div>
            <div class="hint">Contatos inativos no RD</div>
          </div>
          <div class="stat">
            <div class="label"><b>Leads</b> com potencial</div>
            <div class="value" data-key="leads_potenciais">—</div>
            <div class="hint">Não clientes e não inativos</div>
          </div>
          <div class="stat total">
            <div>
              <div class="label">Total de <b>Leads da Base</b> (inclui clientes, inativos e potenciais)</div>
              <div class="hint">Somatório global atual no RD Station</div>
            </div>
            <div class="value" data-key="total_base">—</div>
          </div>
        </div>

        <div class="pie-card" id="pieCard">
          <div class="label">Distribuição por segmento (respeita o filtro “Segmento”)</div>
          <canvas id="pieCanvas" width="560" height="340"></canvas>
          <div class="pie-legend" id="pieLegend"></div>
        </div>
      </div>
    </div>
  </section>
</div>

    <main>
      <section class="card">
        <h2>KPIs principais</h2>
        <div class="body">
          <div class="kpi-grid" id="kpis"></div>
          <div class="dual">
            <div class="mini">
              <div class="legend"><div>Percentuais do recorte</div><div class="muted">Entrega, Abertura, CTR, CTOR</div></div>
              <canvas id="chart1" height="280"></canvas>
            </div>
            <div class="mini">
              <div class="legend"><div>Volumes absolutos do recorte</div><div class="muted">selecionados, entregues, aberturas, cliques</div></div>
              <canvas id="chart2" height="280"></canvas>
            </div>
          </div>
        </div>
      </section>

      <section class="card">
        <h2>Envios detalhados</h2>
        <div class="body">
          <div class="table-wrap">
            <table class="emails-table">
              <thead>
                <tr>
                  <th>Nome</th>
                  <th>Tags</th>
                  <th>Disparos</th>
                  <th>Entrega</th>
                  <th>Abertura</th>
                  <th>Data e hora</th>
                  <th>CTR</th>
                  <th>CTOR</th>
                  <th>Mês</th>
                  <th>Segmento</th>
                </tr>
              </thead>
              <tbody id="emailsTable"></tbody>
            </table>
          </div>
        </div>
      </section>
    </main>
  </div>
</div>

<div id="tip" class="floating-tip" style="display:none"></div>
<div id="toast" class="toast"></div>

<script>
'use strict';

/********************** CONFIG E DADOS **********************/
const ROTULO_MES = 'Setembro/2025';
const RD_SEGMENTOS = { clientes:1515, inativos:1666, leads_potenciais:3516, total_base:8753 };

const CSV_MES = `segment;name;date;sent;delivered;opens;clicks
Leads;[LEADS] [REENVIO] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];29/09/2025 11:21;3222;3188;76;6
Clientes;[CLIENTES] [REENVIO] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];29/09/2025 11:11;608;604;5;0
Inativos;[INATIVOS] [UPDATE INATIVOS V2] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];25/09/2025 14:45;464;396;75;0
Clientes;[CLIENTES] [UPDATE ATIVOS V2] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];25/09/2025 14:45;682;632;129;1
Leads;[LEADS] [OUTBOUND] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];23/09/2025 14:11;275;248;40;1
Leads;[LEADS] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];23/09/2025 11:11;5219;4969;1114;25
Clientes;[CLIENTES] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];23/09/2025 10:11;1275;1237;285;2
Inativos;[INATIVOS] [MÊS DO CLIENTE] [AÇÃO 4] [SETEMBRO 2025];23/09/2025 10:11;1177;1104;159;0
Leads;[LEADS] [REENVIO] [MÊS DO CLIENTE] [AÇÃO 3] [SETEMBRO 2025];18/09/2025 10:41;1215;1201;150;8
Clientes;[CLIENTES] [REENVIO] [MÊS DO CLIENTE] [AÇÃO 3] [SETEMBRO 2025];18/09/2025 10:11;810;797;38;0
Leads;[LEADS] [MÊS DO CLIENTE] [AÇÃO 3] [SETEMBRO 2025];16/09/2025 11:11;2873;2770;1138;16
Inativos;[INATIVOS] [MÊS DO CLIENTE] [AÇÃO 3] [SETEMBRO 2025];16/09/2025 10:11;1182;1126;155;0
Clientes;[CLIENTES] [MÊS DO CLIENTE] [AÇÃO 3] [SETEMBRO 2025];15/09/2025 10:11;1280;1268;286;7
Clientes;[CLIENTES] [REENVIAR] [MÊS DO CLIENTE] [AÇÃO 2] [SETEMBRO 2025];12/09/2025 10:11;830;822;41;1
Leads;[LEADS] [OUTBOUND] [MÊS DO CLIENTE] [AÇÃO 2] [SETEMBRO 2025];11/09/2025 14:51;610;529;103;2
Leads;[LEADS] [MÊS DO CLIENTE] [AÇÃO 2] [SETEMBRO 2025];10/09/2025 11:11;4910;4756;1160;11
Inativos;[INATIVOS] [MÊS DO CLIENTE] [AÇÃO 2] [SETEMBRO 2025];10/09/2025 10:41;1186;1124;174;1
Clientes;[CLIENTES] [MÊS DO CLIENTE] [AÇÃO 2] [SETEMBRO 2025];09/09/2025 16:11;1289;1267;305;5
Clientes;[CLIENTES] [MÊS DO CLIENTE] [AÇÃO 1] [SETEMBRO 2025];05/09/2025 15:41;1292;1261;379;0
Leads;[LEADS] [MÊS DO CLIENTE] [AÇÃO 1] [SETEMBRO 2025];05/09/2025 11:41;3519;3325;865;0
Inativos;[INATIVOS] [MÊS DO CLIENTE] [AÇÃO 1] [SETEMBRO 2025];05/09/2025 11:41;1250;1118;171;0`;

/********************** HELPERS **********************/
const $ = id => document.getElementById(id);
const nf = v => new Intl.NumberFormat('pt-BR').format(v);
const pct = v => Number.isFinite(v) ? v.toFixed(2)+'%' : '—';
const tipBox = $('tip');
const toast = $('toast');

/* Paleta para canvas */
function cssVar(name){ return getComputedStyle(document.documentElement).getPropertyValue(name).trim(); }
const PAL = { blue: cssVar('--p-blue'), blueStrong: cssVar('--p-blue-strong'), green: cssVar('--p-green') };

function showToast(msg){ toast.textContent=msg; toast.style.display='block'; setTimeout(()=>toast.style.display='none', 3000); }
function openTip(html,x,y){
  tipBox.innerHTML = html;
  const w = Math.min(420, tipBox.offsetWidth || 300);
  tipBox.style.left = Math.min(window.innerWidth - w - 10, x + 14)+'px';
  tipBox.style.top  = Math.min(window.innerHeight - 140, y + 14)+'px';
  tipBox.style.display='block';
}
function closeTip(){ tipBox.style.display='none'; }
function bindTips(root=document){
  root.querySelectorAll('.tip-anchor,[data-tip]').forEach(el=>{
    const html = el.getAttribute('data-tip'); if(!html) return;
    el.addEventListener('mouseover',e=>openTip(html,e.clientX,e.clientY));
    el.addEventListener('mousemove',e=>openTip(html,e.clientX,e.clientY));
    el.addEventListener('mouseleave',closeTip);
  });
}

function parseCSV(csv){
  const lines = csv.trim().split(/\r?\n/);
  const head = lines[0].split(';').map(s=>s.trim());
  const rows = [];
  for(let i=1;i<lines.length;i++){
    const L = lines[i].trim(); if(!L) continue;
    const p = L.split(';'); const rec={};
    head.forEach((k,idx)=>{
      rec[k] = (k==='sent'||k==='delivered'||k==='opens'||k==='clicks')
        ? Number(p[idx]||0)
        : (p[idx]||'').trim();
    });
    rec.month = ROTULO_MES;
    rows.push(rec);
  }
  return rows;
}

const dataset = { emails: parseCSV(CSV_MES) };

/********************** FILTRO/AGREGAÇÃO **********************/
function parseDateStr(s){
  const [d,h] = s.split(' ');
  const [dd,mm,yyyy]=d.split('/').map(Number);
  const [HH,MM]=(h||'00:00').split(':').map(Number);
  return new Date(yyyy,mm-1,dd,HH,MM);
}
function weekOfMonth(dt){
  const day=dt.getDate();
  if(day<=7) return 'w1'; if(day<=14) return 'w2'; if(day<=21) return 'w3'; if(day<=31) return 'w4'; return 'wX';
}
function inWeek(dateStr, weekSel){
  if(weekSel==='all') return true;
  return weekOfMonth(parseDateStr(dateStr))===weekSel;
}
function filteredEmails(){
  const segSel=$('segmento').value, weekSel=$('semana').value;
  return dataset.emails.filter(e=> (segSel==='Geral'||e.segment===segSel) && inWeek(e.date, weekSel));
}
function aggregate(rows){
  const sent=rows.reduce((a,b)=>a+b.sent,0),
        delivered=rows.reduce((a,b)=>a+b.delivered,0),
        opens=rows.reduce((a,b)=>a+b.opens,0),
        clicks=rows.reduce((a,b)=>a+b.clicks,0);
  return {
    sent, delivered, opens, clicks,
    delivery: sent? Math.min(100, Math.max(0, delivered/sent*100)):0,
    open: delivered? Math.min(100, Math.max(0, opens/delivered*100)):0,
    ctr: delivered? Math.min(100, Math.max(0, clicks/delivered*100)):0,
    ctor: opens? Math.min(100, Math.max(0, clicks/opens*100)):0
  };
}

/********************** DONUT 2D (flat, anima 1x e depois fica estático) **********************/
const PIE_COLORS = {
  clientes: PAL.blue,
  inativos: PAL.blueStrong,
  leads_potenciais: PAL.green
};
let PIE_ANIMATED_ONCE = false;

function renderRDStats(){
  const mp=document.getElementById('monthPill'); if(mp) mp.textContent = ROTULO_MES;
  const rt=document.getElementById('rdTopTotal'); if(rt) rt.textContent = 'Total: '+nf(RD_SEGMENTOS.total_base||0);
  ['clientes','inativos','leads_potenciais','total_base'].forEach(k=>{
    const node=document.querySelector(`.stats-card [data-key="${k}"]`);
    if(node) node.textContent = nf(RD_SEGMENTOS[k]||0);
  });
}

function renderPie(){
  const c = document.getElementById('pieCanvas');
  if(!c) return;

  // Dados respeitando filtro "Segmento"
  const segSel = $('segmento').value;
  const baseData = [
    {k:'clientes',label:'Clientes',v:RD_SEGMENTOS.clientes,c:PIE_COLORS.clientes},
    {k:'inativos',label:'Inativos',v:RD_SEGMENTOS.inativos,c:PIE_COLORS.inativos},
    {k:'leads_potenciais',label:'Leads com potencial',v:RD_SEGMENTOS.leads_potenciais,c:PIE_COLORS.leads_potenciais}
  ];
  const map = { 'Clientes':'clientes', 'Inativos':'inativos', 'Leads':'leads_potenciais' };
  const data = segSel==='Geral' ? baseData : baseData.filter(d => d.k === map[segSel]);

  const ctx=c.getContext('2d');
  const w = c.width = (c.clientWidth || 560);
  const h = c.height= (c.clientHeight|| 340);
  const cx=w/2, cy=h/2;
  const r=Math.min(w,h)/2-28;
  const ir=r*0.62;

  const total=data.reduce((a,b)=>a+b.v,0)||1;
  const angs=data.map(d=>d.v/total*Math.PI*2);

  // Easing apenas na primeira vez
  const shouldAnimate = !PIE_ANIMATED_ONCE;
  let t=0; const step=1/60;
  function easeOutCubic(x){ return 1 - Math.pow(1 - x, 3); }

  function drawFrame(anim){
    const ctx=c.getContext('2d');
    ctx.clearRect(0,0,w,h);

    // sombra suave sob os arcos
    ctx.save();
    ctx.shadowColor = 'rgba(2,6,23,0.12)';
    ctx.shadowBlur = 16;
    ctx.shadowOffsetY = 6;

    let a0=-Math.PI/2;
    data.forEach((d,i)=>{
      const a=angs[i]*(anim?anim:1);
      if(a<=0) return;
      // gradiente radial discreto para dar “corpo”
      const mid=a0+a/2;
      const grad=ctx.createRadialGradient(
        cx+Math.cos(mid)*(r*0.12), cy+Math.sin(mid)*(r*0.12), r*0.08,
        cx, cy, r
      );
      grad.addColorStop(0, d.c);
      grad.addColorStop(1, d.c);
      ctx.beginPath(); ctx.moveTo(cx,cy); ctx.arc(cx,cy,r,a0,a0+a); ctx.closePath(); ctx.fillStyle=grad; ctx.fill();

      // “Fura” o centro
      ctx.globalCompositeOperation='destination-out';
      ctx.beginPath(); ctx.arc(cx,cy,ir,0,Math.PI*2); ctx.fill();
      ctx.globalCompositeOperation='source-over';

      // borda fina
      ctx.beginPath(); ctx.arc(cx,cy,r,a0,a0+a); ctx.strokeStyle='#fff'; ctx.lineWidth=1; ctx.stroke();

      a0+=a;
    });
    ctx.restore();

    // Borda externa cinza
    ctx.beginPath(); ctx.arc(cx,cy,r,0,Math.PI*2); ctx.strokeStyle='#e5e7eb'; ctx.lineWidth=1; ctx.stroke();

    // Texto central
    ctx.fillStyle='#0f172a'; ctx.textAlign='center';
    let centerLabel='Total da base', centerValue=nf(RD_SEGMENTOS.total_base||0);
    if(segSel!=='Geral'){
      const key = map[segSel];
      centerLabel = segSel;
      centerValue = nf(RD_SEGMENTOS[key]||0);
    }
    ctx.font='12px system-ui'; ctx.fillText(centerLabel, cx, cy-8);
    ctx.font='700 20px system-ui'; ctx.fillText(centerValue, cx, cy+14);
  }

  function animate(){
    const anim = easeOutCubic(Math.min(1,t));
    drawFrame(anim);
    if(t<1){ t+=step; requestAnimationFrame(animate); }
    else { PIE_ANIMATED_ONCE = true; }
  }

  if(shouldAnimate){ animate(); } else { drawFrame(1); }

  // Legenda
  const leg=document.getElementById('pieLegend');
  if(leg){
    leg.innerHTML='';
    const totalRow=document.createElement('div');
    totalRow.className='row';
    totalRow.innerHTML=`<div><span class="dot" style="background:#94a3b8"></span>Total da base</div><div>${nf(RD_SEGMENTOS.total_base||0)}</div>`;
    leg.appendChild(totalRow);

    const totSlices = data.reduce((a,b)=>a+b.v,0)||1;
    data.forEach(d=>{
      const p=(d.v/totSlices)*100;
      const row=document.createElement('div'); row.className='row';
      row.innerHTML=`<div><span class="dot" style="background:${d.c}"></span>${d.label}</div><div>${nf(d.v)} • ${p.toFixed(1)}%</div>`;
      leg.appendChild(row);
    });
  }

  // Tooltip
  c.onmousemove=(ev)=>{
    const rct=c.getBoundingClientRect(), x=ev.clientX-rct.left, y=ev.clientY-rct.top;
    const dx=x-cx, dy=y-cy; const dist=Math.sqrt(dx*dx+dy*dy);
    if(dist<ir||dist>r){ closeTip(); return; }
    let ang=Math.atan2(dy,dx); if(ang<-Math.PI/2) ang+=2*Math.PI;
    let a0=-Math.PI/2, acc=0;
    const tot=data.reduce((a,b)=>a+b.v,0)||1;
    for(const d of data){
      const frac=d.v/tot; const a=a0+acc*2*Math.PI; const b=a+frac*2*Math.PI;
      if(ang>=a&&ang<=b){ openTip(`${d.label}: <b>${nf(d.v)}</b> (${(frac*100).toFixed(1)}%)`, ev.clientX, ev.clientY); return; }
      acc+=frac;
    }
    closeTip();
  };
  c.onmouseleave=closeTip;
}

/********************** KPIs & BARRAS **********************/
function renderKPIs(){
  const box=$('kpis'); box.innerHTML='';
  const rows=filteredEmails(); const agg=aggregate(rows);
  const items=[ {k:'delivery',label:'Entrega'}, {k:'open',label:'Abertura'}, {k:'ctr',label:'CTR'}, {k:'ctor',label:'CTOR'} ];
  items.forEach(it=>{
    const el=document.createElement('div'); el.className='kpi';
    el.innerHTML=`<div class="label">${it.label}</div><div class="v">${pct(agg[it.k])}</div>`;
    box.appendChild(el);
  });
}

const BAR_MAP={},HOVER={};
function attachTooltipToCanvas(c){
  c.onmousemove=ev=>{
    const r=c.getBoundingClientRect(),x=ev.clientX-r.left,y=ev.clientY-r.top,b=BAR_MAP[c.id]||[];
    const hit=b.find(b=>x>=b.x&&x<=b.x+b.w&&y>=b.y&&y<=b.y+b.h);
    if(hit){ openTip(`${hit.label}: <b>${hit.value}</b>`,ev.clientX,ev.clientY); HOVER[c.id]=hit; }
    else { closeTip(); HOVER[c.id]=null; }
  };
  c.onmouseleave=()=>{ closeTip(); HOVER[c.id]=null; };
}
function drawBars(id,labels,vals,mode='percent',color){
  const c=document.getElementById(id); if(!c) return;
  const ctx=c.getContext('2d');
  const W=c.width=(c.clientWidth||560), H=c.height=(c.clientHeight||280);
  ctx.clearRect(0,0,W,H);
  const v=(vals||[]).map(x=>Number.isFinite(x)?x:0);
  const max=Math.max(...v,1)*1.2;
  const padL=56,padB=42,padR=24,padT=22;
  const innerW=W-padL-padR, innerH=H-padT-padB;
  const colW=innerW/labels.length, barW=colW*0.55; const bars=[];
  ctx.strokeStyle='#e5e7eb'; ctx.fillStyle='#64748b';
  for(let i=0;i<=5;i++){
    const y=padT+innerH-(innerH*i/5);
    ctx.beginPath(); ctx.moveTo(padL,y); ctx.lineTo(W-padR,y); ctx.stroke();
    const val=(max*i/5);
    const lab=mode==='percent'?val.toFixed(2)+'%':new Intl.NumberFormat('pt-BR').format(Math.round(val));
    ctx.font='12px system-ui'; ctx.textAlign='right'; ctx.fillText(lab,padL-8,y+4);
  }
  labels.forEach((lab,i)=>{
    const h=(v[i]/max)*innerH, x=padL+i*colW+(colW-barW)/2, y=padT+innerH-h;
    const disp=mode==='percent'?v[i].toFixed(2)+'%':new Intl.NumberFormat('pt-BR').format(Math.round(v[i]));
    ctx.save(); ctx.fillStyle=color; ctx.fillRect(x,y,barW,h); ctx.restore();
    ctx.fillStyle='#0f172a'; ctx.font='12px system-ui'; ctx.textAlign='center';
    const safeY=Math.max(padT+12,y-6); ctx.fillText(disp,x+barW/2,safeY);
    ctx.fillStyle='#475569'; ctx.textAlign='center'; ctx.fillText(lab,x+barW/2,H-12);
    bars.push({x,y,w:barW,h,label:lab,value:disp});
  });
  BAR_MAP[id]=bars; attachTooltipToCanvas(c);
}
function renderCharts(){
  const rows=filteredEmails(); const agg=aggregate(rows);
  drawBars('chart1',['Entrega','Abertura','CTR','CTOR'],[agg.delivery,agg.open,agg.ctr,agg.ctor],'percent', cssVar('--p-blue'));
  drawBars('chart2',['Selecionados','Entregues','Aberturas','Cliques'],[agg.sent,agg.delivered,agg.opens,agg.clicks],'abs', cssVar('--p-green'));
}

/********************** TABELA **********************/
function renderTable(){
  const tbody=$('emailsTable'); tbody.innerHTML='';
  const segSel=$('segmento').value, weekSel=$('semana').value;
  const rows=dataset.emails
    .filter(e=>(segSel==='Geral'||e.segment===segSel))
    .filter(e=>inWeek(e.date,weekSel))
    .sort((a,b)=>parseDateStr(b.date)-parseDateStr(a.date));

  rows.forEach(x=>{
    const delivery=x.sent?x.delivered/x.sent*100:0,
          open=x.delivered?x.opens/x.delivered*100:0,
          ctr=x.delivered?x.clicks/x.delivered*100:0,
          ctor=x.opens?x.clicks/x.opens*100:0;

    const isMCli   = /MÊS DO CLIENTE/i.test(x.name||'');
    const isMCons  = /MÊS DO CONSUMIDOR/i.test(x.name||'');
    const tagHtml = isMCli ? '<span class="badge mc">Mês do Cliente</span>'
                  : isMCons ? '<span class="badge mc">Mês do Consumidor</span>'
                  : '<span class="badge warn">Aviso</span>';

    const segCls = x.segment==='Clientes'?'clientes':x.segment==='Leads'?'leads':'inativos';
    const tr=document.createElement('tr');
    tr.innerHTML=
      `<td class="name-cell">${x.name}</td>
       <td class="tags-cell">${tagHtml}</td>
       <td class="num">${nf(x.sent)}</td>
       <td class="num">${pct(delivery)}</td>
       <td class="num">${pct(open)}</td>
       <td class="center">${x.date}</td>
       <td class="num">${pct(ctr)}</td>
       <td class="num">${pct(ctor)}</td>
       <td class="center"><span class="month-pill">${ROTULO_MES}</span></td>
       <td class="center"><span class="seg-badge ${segCls}">${x.segment}</span></td>`;
    tbody.appendChild(tr);
  });
}

/********************** ORQUESTRAÇÃO **********************/
function renderAll(){
  try{
    renderRDStats();
    renderPie();       // donut 2D, animado só 1x
    renderKPIs();
    renderCharts();
    renderTable();
    showToast('Renderizado • '+(dataset.emails?.length||0)+' envios');
  } catch(e){
    console.error(e); showToast('Erro: '+e.message);
  }
}

bindTips(document);
$('segmento').addEventListener('change', renderAll);
$('semana').addEventListener('change', renderAll);

// Bootstrap robusto
let __DASH_STARTED__ = false;
function startOnce(){
  if(__DASH_STARTED__) return; __DASH_STARTED__ = true;
  renderAll();
  window.addEventListener('resize', ()=>{ try{ renderPie(); renderCharts(); }catch(e){ console.error(e); }});
  const root=document.querySelector('.app');
  try{
    const mo=new MutationObserver(()=>{
      const kpisOk = (document.getElementById('kpis')?.children.length||0)>0;
      const tblOk  = (document.getElementById('emailsTable')?.children.length||0)>0;
      const rdOk   = (document.querySelector('.stats-card [data-key="clientes"]')?.textContent||'').trim()!=='—';
      if(!(kpisOk && tblOk && rdOk)){ renderAll(); }
    });
    mo.observe(root,{childList:true,subtree:true});
  }catch(e){ /* ambiente sem MutationObserver */ }
  document.addEventListener('visibilitychange',()=>{ if(!document.hidden) renderAll(); });
}
if(document.readyState!=='loading') startOnce();
document.addEventListener('DOMContentLoaded', startOnce);
window.addEventListener('load', startOnce);
window.addEventListener('focus', startOnce);
</script>
</body>
</html>
