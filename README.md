[servicio-tecnico (1).html](https://github.com/user-attachments/files/29766706/servicio-tecnico.1.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>Nickcel — Servicio Técnico</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#0d1117;--surface:#161b22;--surface2:#21262d;--border:#30363d;
  --accent:#2e8bc0;--accent2:#1a6fa0;--success:#238636;--warn:#d29922;
  --danger:#da3633;--text:#e6edf3;--text2:#8b949e;--text3:#6e7681;
  --radius:8px;--radius-lg:12px;
}
body{font-family:'Segoe UI',system-ui,sans-serif;background:var(--bg);color:var(--text);font-size:14px;min-height:100vh}
/* HEADER */
.header{background:var(--surface);border-bottom:1px solid var(--border);padding:0 24px;display:flex;align-items:center;justify-content:space-between;height:56px;position:sticky;top:0;z-index:100}
.header-brand{display:flex;align-items:center;gap:12px}
.header-logo{width:32px;height:32px;background:var(--accent);border-radius:6px;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:14px;color:#fff}
.header-title{font-weight:700;font-size:15px}
.header-sub{font-size:11px;color:var(--text2);margin-top:1px}
.header-nav{display:flex;gap:4px}
.nav-btn{padding:6px 14px;border:none;background:none;color:var(--text2);font-size:13px;cursor:pointer;border-radius:6px;font-family:inherit;transition:all .15s;border-bottom:2px solid transparent}
.nav-btn:hover{background:var(--surface2);color:var(--text)}
.nav-btn.active{color:var(--accent);border-bottom:2px solid var(--accent);background:rgba(46,139,192,.08)}
/* LAYOUT */
.main{padding:24px;max-width:1200px;margin:0 auto}
.screen{display:none}.screen.active{display:block}
/* CARDS */
.card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:20px}
.card-title{font-size:13px;font-weight:700;color:var(--text2);text-transform:uppercase;letter-spacing:.06em;margin-bottom:16px}
/* GRID */
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.grid3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px}
.grid4{display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:12px}
/* FORM */
.field{margin-bottom:12px}
.field label{display:block;font-size:12px;color:var(--text2);margin-bottom:5px;font-weight:500}
.field label span.req{color:var(--danger)}
.input{width:100%;padding:9px 12px;background:var(--surface2);border:1px solid var(--border);border-radius:var(--radius);color:var(--text);font-size:13px;font-family:inherit;outline:none;transition:border-color .15s}
.input:focus{border-color:var(--accent)}
.input::placeholder{color:var(--text3)}
select.input option{background:var(--surface2)}
textarea.input{resize:vertical;min-height:80px}
/* BUTTONS */
.btn{padding:9px 18px;border:none;border-radius:var(--radius);font-size:13px;font-weight:600;cursor:pointer;font-family:inherit;transition:all .15s;display:inline-flex;align-items:center;gap:6px}
.btn-primary{background:var(--accent);color:#fff}.btn-primary:hover{background:var(--accent2)}
.btn-success{background:var(--success);color:#fff}.btn-success:hover{filter:brightness(1.1)}
.btn-danger{background:var(--danger);color:#fff}.btn-danger:hover{filter:brightness(1.1)}
.btn-ghost{background:var(--surface2);color:var(--text);border:1px solid var(--border)}.btn-ghost:hover{border-color:var(--accent);color:var(--accent)}
.btn-full{width:100%;justify-content:center}
.btn-sm{padding:5px 12px;font-size:12px}
/* BADGES */
.badge{padding:3px 10px;border-radius:20px;font-size:11px;font-weight:700;display:inline-block}
.badge-ingresado{background:rgba(46,139,192,.15);color:#58a6ff}
.badge-proceso{background:rgba(210,153,34,.15);color:#e3b341}
.badge-listo{background:rgba(35,134,54,.15);color:#3fb950}
.badge-entregado{background:rgba(110,118,129,.15);color:#8b949e}
/* TABLA */
.table-wrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:13px}
th{text-align:left;padding:10px 12px;font-size:11px;color:var(--text2);font-weight:700;text-transform:uppercase;letter-spacing:.05em;border-bottom:1px solid var(--border)}
td{padding:10px 12px;border-bottom:1px solid var(--border);vertical-align:middle}
tr:last-child td{border-bottom:none}
tr:hover td{background:rgba(255,255,255,.02)}
/* STATS */
.stats-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:20px}
.stat-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:16px}
.stat-n{font-size:28px;font-weight:700;color:var(--accent)}
.stat-l{font-size:12px;color:var(--text2);margin-top:4px}
/* MODAL */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.7);z-index:200;align-items:center;justify-content:center;padding:20px}
.modal-overlay.open{display:flex}
.modal{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:24px;max-width:640px;width:100%;max-height:90vh;overflow-y:auto}
.modal-title{font-size:16px;font-weight:700;margin-bottom:20px;display:flex;justify-content:space-between;align-items:center}
.modal-close{background:none;border:none;color:var(--text2);font-size:20px;cursor:pointer;padding:0 4px}
/* CODIGO */
.codigo-badge{background:rgba(46,139,192,.15);color:#58a6ff;border:1px solid rgba(46,139,192,.3);border-radius:6px;padding:4px 10px;font-size:13px;font-weight:700;font-family:monospace}
/* PRESUPUESTO PREVIEW */
.presup{background:#fff;color:#111;border-radius:8px;padding:24px;font-size:13px;line-height:1.6}
.presup-header{background:#1e3a5f;color:#fff;padding:14px 20px;margin:-24px -24px 20px;border-radius:8px 8px 0 0;display:flex;justify-content:space-between;align-items:center}
.presup-title{font-size:16px;font-weight:700}
.presup-sub{font-size:11px;opacity:.75}
.presup-section{margin-bottom:16px;padding-bottom:12px;border-bottom:1px solid #eee}
.presup-section:last-child{border-bottom:none}
.presup-row{display:flex;justify-content:space-between;padding:3px 0;font-size:13px}
.presup-total{font-size:15px;font-weight:700;color:#1e3a5f}
/* SEARCH */
.search-bar{display:flex;gap:8px;margin-bottom:16px}
.search-bar .input{flex:1}
/* TOAST */
#toast{position:fixed;bottom:24px;right:24px;background:var(--surface2);border:1px solid var(--border);border-radius:var(--radius);padding:12px 18px;font-size:13px;z-index:999;display:none;box-shadow:0 4px 12px rgba(0,0,0,.3)}
#toast.ok{border-color:var(--success);color:#3fb950}
#toast.err{border-color:var(--danger);color:#ff7b72}
#toast.warn{border-color:var(--warn);color:#e3b341}
/* SEÑA BOX */
.sena-box{background:rgba(35,134,54,.08);border:1px solid rgba(35,134,54,.25);border-radius:var(--radius);padding:12px;margin-top:8px}
.sena-row{display:flex;justify-content:space-between;font-size:13px;padding:2px 0}
.sena-total{font-weight:700;color:#3fb950;font-size:14px;margin-top:6px;padding-top:6px;border-top:1px solid rgba(35,134,54,.2)}
/* ESTADO SELECT */
.estado-select{padding:5px 10px;border-radius:20px;border:1px solid var(--border);font-size:12px;font-weight:700;cursor:pointer;font-family:inherit;outline:none}
.estado-ingresado{background:rgba(46,139,192,.15);color:#58a6ff;border-color:rgba(46,139,192,.3)}
.estado-proceso{background:rgba(210,153,34,.15);color:#e3b341;border-color:rgba(210,153,34,.3)}
.estado-listo{background:rgba(35,134,54,.15);color:#3fb950;border-color:rgba(35,134,54,.3)}
.estado-entregado{background:rgba(110,118,129,.15);color:#8b949e;border-color:rgba(110,118,129,.3)}
@media(max-width:700px){
  .grid2,.grid3,.grid4{grid-template-columns:1fr}
  .stats-grid{grid-template-columns:1fr 1fr}
  .header-nav{display:none}
}
</style>
</head>
<body>

<div class="header">
  <div class="header-brand">
    <div class="header-logo">N</div>
    <div>
      <div class="header-title">Nickcel — Servicio Técnico</div>
      <div class="header-sub">San Martín 514, Quitilipi, Chaco</div>
    </div>
  </div>
  <div class="header-nav">
    <button class="nav-btn active" onclick="showScreen('ingresar',this)">+ Ingresar Equipo</button>
    <button class="nav-btn" onclick="showScreen('ordenes',this)">Órdenes</button>
  </div>
</div>

<div class="main">

<!-- SCREEN: INGRESAR -->
<div id="screen-ingresar" class="screen active">
  <div style="display:grid;grid-template-columns:1fr 380px;gap:20px;align-items:start">
    
    <div>
      <div class="card" style="margin-bottom:16px">
        <div class="card-title">Datos del cliente</div>
        <div class="grid2">
          <div class="field"><label>Nombre y Apellido <span class="req">*</span></label><input class="input" id="cli-nombre" placeholder="Ej: García Juan Carlos"></div>
          <div class="field"><label>Teléfono (WhatsApp) <span class="req">*</span></label><input class="input" id="cli-tel" placeholder="Ej: 3624-123456" type="tel"></div>
        </div>
      </div>

      <div class="card" style="margin-bottom:16px">
        <div class="card-title">Datos del equipo</div>
        <div class="grid3">
          <div class="field"><label>Marca <span class="req">*</span></label>
            <select class="input" id="eq-marca">
              <option value="">Seleccioná...</option>
              <option>Samsung</option><option>Motorola</option><option>Xiaomi</option>
              <option>iPhone</option><option>Tecno</option><option>Infinix</option>
              <option>Huawei</option><option>LG</option><option>Nokia</option><option>Otra</option>
            </select>
          </div>
          <div class="field"><label>Modelo <span class="req">*</span></label><input class="input" id="eq-modelo" placeholder="Ej: Galaxy A15"></div>
          <div class="field"><label>IMEI</label><input class="input" id="eq-imei" placeholder="15 dígitos" maxlength="15"></div>
        </div>
        <div class="grid3">
          <div class="field"><label>Estado de ingreso</label>
            <select class="input" id="eq-estado-ingreso">
              <option>Pantalla rota</option><option>Pantalla ok</option>
              <option>Sin pantalla</option><option>Mojado</option>
              <option>No enciende</option><option>Golpeado</option><option>Otro</option>
            </select>
          </div>
          <div class="field"><label>Ingresa</label>
            <select class="input" id="eq-encendido">
              <option value="prendido">Prendido</option>
              <option value="apagado">Apagado</option>
            </select>
          </div>
          <div class="field"><label>Accesorios incluidos</label>
            <select class="input" id="eq-accesorios">
              <option value="sin accesorios">Sin accesorios</option>
              <option value="con cargador">Con cargador</option>
              <option value="con funda">Con funda</option>
              <option value="con cargador y funda">Con cargador y funda</option>
              <option value="otros accesorios">Otros accesorios</option>
            </select>
          </div>
        </div>
        <div class="field"><label>Observaciones del equipo al ingreso</label>
          <textarea class="input" id="eq-obs" placeholder="Ej: Pantalla con una fisura en la esquina superior derecha, carcasa con raspones..."></textarea>
        </div>
      </div>

      <div class="card">
        <div class="card-title">Servicio a realizar</div>
        <div class="grid2">
          <div class="field"><label>Tipo de servicio <span class="req">*</span></label>
            <select class="input" id="serv-tipo">
              <option value="">Seleccioná...</option>
              <option>Cambio de pantalla</option><option>Cambio de batería</option>
              <option>Reparación de carga</option><option>Reparación placa</option>
              <option>Limpieza por humedad</option><option>Cambio de táctil</option>
              <option>Cambio de modulo</option><option>Diagnóstico</option>
              <option>Cambio de pin de carga</option><option>Otro</option>
            </select>
          </div>
          <div class="field"><label>Costo del servicio ($) <span class="req">*</span></label>
            <input class="input" id="serv-costo" type="number" placeholder="0" oninput="calcSena()">
          </div>
        </div>
        <div class="field"><label>Detalle del trabajo / Diagnóstico</label>
          <textarea class="input" id="serv-detalle" placeholder="Describí qué se va a hacer o qué se encontró en el diagnóstico..." style="min-height:100px"></textarea>
        </div>
        <div class="field"><label>Tiempo estimado de entrega</label>
          <select class="input" id="serv-tiempo">
            <option>En el momento</option><option>24 horas</option><option>48 horas</option>
            <option>3 días</option><option>1 semana</option><option>A confirmar</option>
          </select>
        </div>

        <div class="sena-box" id="sena-box" style="display:none">
          <div style="font-size:12px;font-weight:700;color:#3fb950;margin-bottom:8px">💰 Seña mínima (50%)</div>
          <div class="sena-row"><span>Costo total del servicio</span><span id="s-total">$0</span></div>
          <div class="sena-row"><span>Seña mínima requerida (50%)</span><span id="s-sena-min">$0</span></div>
          <div class="sena-row sena-total"><span>Saldo restante</span><span id="s-saldo">$0</span></div>
        </div>

        <div style="margin-top:16px">
          <div class="field"><label>Seña recibida ($) <span class="req">*</span></label>
            <input class="input" id="serv-sena" type="number" placeholder="Mínimo 50% del costo" oninput="calcSena()">
          </div>
        </div>
      </div>
    </div>

    <!-- PANEL DERECHO -->
    <div>
      <div class="card" style="position:sticky;top:72px">
        <div class="card-title">Vista previa del presupuesto</div>
        <div id="preview-presup" style="color:var(--text2);font-size:13px;text-align:center;padding:40px 0">
          Completá los datos para ver el presupuesto
        </div>
        <div style="margin-top:16px;display:flex;flex-direction:column;gap:8px">
          <button class="btn btn-primary btn-full" onclick="registrarOrden()">✓ Registrar orden</button>
          <button class="btn btn-ghost btn-full" onclick="limpiarForm()">↺ Limpiar</button>
        </div>
      </div>
    </div>

  </div>
</div>

<!-- SCREEN: ÓRDENES -->
<div id="screen-ordenes" class="screen">
  <div class="stats-grid" id="stats-container"></div>
  <div class="card">
    <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;flex-wrap:wrap;gap:10px">
      <div class="card-title" style="margin-bottom:0">Órdenes de servicio</div>
      <div style="display:flex;gap:8px;flex-wrap:wrap">
        <input class="input" id="buscar-orden" placeholder="Buscar por código, cliente o IMEI..." style="width:260px" oninput="filtrarOrdenes()">
        <select class="input" id="filtro-estado" style="width:160px" onchange="filtrarOrdenes()">
          <option value="">Todos los estados</option>
          <option value="ingresado">Ingresado</option>
          <option value="proceso">En proceso</option>
          <option value="listo">Listo para retirar</option>
          <option value="entregado">Entregado</option>
        </select>
      </div>
    </div>
    <div class="table-wrap">
      <table id="tabla-ordenes">
        <thead>
          <tr>
            <th>Código</th><th>Cliente</th><th>Equipo</th><th>Servicio</th>
            <th>Costo</th><th>Seña</th><th>Saldo</th><th>Estado</th><th>Acciones</th>
          </tr>
        </thead>
        <tbody id="tbody-ordenes"></tbody>
      </table>
    </div>
  </div>
</div>

</div><!-- /main -->

<!-- MODAL DETALLE -->
<div class="modal-overlay" id="modal-detalle">
  <div class="modal" style="max-width:700px">
    <div class="modal-title">
      <span id="modal-titulo">Orden de servicio</span>
      <button class="modal-close" onclick="cerrarModal('modal-detalle')">×</button>
    </div>
    <div id="modal-body"></div>
    <div style="display:flex;gap:8px;margin-top:20px;flex-wrap:wrap">
      <button class="btn btn-success" onclick="enviarWP()">📱 Enviar por WhatsApp</button>
      <button class="btn btn-primary" onclick="generarPDF()">📄 Descargar PDF</button>
      <button class="btn btn-ghost" onclick="cerrarModal('modal-detalle')">Cerrar</button>
    </div>
  </div>
</div>

<!-- MODAL PAGO -->
<div class="modal-overlay" id="modal-pago">
  <div class="modal" style="max-width:420px">
    <div class="modal-title">
      <span>Registrar pago adicional</span>
      <button class="modal-close" onclick="cerrarModal('modal-pago')">×</button>
    </div>
    <div id="modal-pago-body"></div>
    <div class="field" style="margin-top:16px">
      <label>Monto a cobrar ($)</label>
      <input class="input" id="pago-monto" type="number" placeholder="0">
    </div>
    <div style="display:flex;gap:8px;margin-top:16px">
      <button class="btn btn-success" onclick="confirmarPago()" style="flex:1">✓ Confirmar pago</button>
      <button class="btn btn-ghost" onclick="cerrarModal('modal-pago')">Cancelar</button>
    </div>
  </div>
</div>

<div id="toast"></div>

<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/12.12.0/firebase-app.js";
import { getFirestore, collection, doc, setDoc, getDocs, updateDoc, deleteDoc, query, orderBy, onSnapshot } from "https://www.gstatic.com/firebasejs/12.12.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyAhBYwPQJ2MU2U4wFdu58JS826dOV1-h9c",
  authDomain: "nickcel-pagares.firebaseapp.com",
  projectId: "nickcel-pagares",
  storageBucket: "nickcel-pagares.firebasestorage.app",
  messagingSenderId: "235121339876",
  appId: "1:235121339876:web:981870b479117906822bf1"
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

let ordenes = [];
let ordenActual = null;
let pagoOrdenId = null;

// =============================================
// UTILS
// =============================================
function fmt(n){ return '$' + Math.round(n||0).toLocaleString('es-AR'); }
function fmtFecha(ts){ return new Date(ts).toLocaleDateString('es-AR',{day:'2-digit',month:'2-digit',year:'numeric',hour:'2-digit',minute:'2-digit'}); }
function toast(msg, type='ok'){
  const el = document.getElementById('toast');
  el.textContent = msg; el.className = type; el.style.display='block';
  setTimeout(()=>el.style.display='none', 3000);
}
function genCodigo(){
  const d = new Date();
  return `ST-${String(d.getFullYear()).slice(-2)}${String(d.getMonth()+1).padStart(2,'0')}-${String(Math.floor(Math.random()*9000)+1000)}`;
}
function badgeEstado(e){
  const m = {ingresado:'badge-ingresado',proceso:'badge-proceso',listo:'badge-listo',entregado:'badge-entregado'};
  const l = {ingresado:'Ingresado',proceso:'En proceso',listo:'Listo para retirar',entregado:'Entregado'};
  return `<span class="badge ${m[e]||'badge-ingresado'}">${l[e]||e}</span>`;
}

// =============================================
// NAVEGACION
// =============================================
window.showScreen = function(s, btn){
  document.querySelectorAll('.screen').forEach(el=>el.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('screen-'+s).classList.add('active');
  btn.classList.add('active');
  if(s==='ordenes') renderOrdenes();
}

// =============================================
// CÁLCULO SEÑA
// =============================================
window.calcSena = function(){
  const costo = parseFloat(document.getElementById('serv-costo').value)||0;
  const senaMin = Math.ceil(costo*0.5);
  const senaRec = parseFloat(document.getElementById('serv-sena').value)||0;
  const saldo = costo - senaRec;
  const box = document.getElementById('sena-box');
  if(costo>0){
    box.style.display='block';
    document.getElementById('s-total').textContent = fmt(costo);
    document.getElementById('s-sena-min').textContent = fmt(senaMin);
    document.getElementById('s-saldo').textContent = fmt(Math.max(0,saldo));
  } else { box.style.display='none'; }
  actualizarPreview();
}

// =============================================
// PREVIEW EN TIEMPO REAL
// =============================================
function actualizarPreview(){
  const nombre = document.getElementById('cli-nombre').value.trim();
  const tel    = document.getElementById('cli-tel').value.trim();
  const marca  = document.getElementById('eq-marca').value;
  const modelo = document.getElementById('eq-modelo').value.trim();
  const imei   = document.getElementById('eq-imei').value.trim();
  const serv   = document.getElementById('serv-tipo').value;
  const costo  = parseFloat(document.getElementById('serv-costo').value)||0;
  const sena   = parseFloat(document.getElementById('serv-sena').value)||0;
  const tiempo = document.getElementById('serv-tiempo').value;
  const detalle= document.getElementById('serv-detalle').value.trim();

  const el = document.getElementById('preview-presup');
  if(!nombre || !marca || !serv || !costo){
    el.innerHTML='<div style="color:var(--text2);text-align:center;padding:40px 0">Completá los datos para ver el presupuesto</div>';
    return;
  }
  const saldo = Math.max(0, costo - sena);
  el.innerHTML = `
    <div class="presup">
      <div class="presup-header">
        <div><div class="presup-title">NICKCEL TECNO & HOGAR S.R.L.</div><div class="presup-sub">San Martín 514, Quitilipi, Chaco | WhatsApp: 3644924970</div></div>
        <div style="font-size:12px;opacity:.8">PRESUPUESTO</div>
      </div>
      <div class="presup-section">
        <div style="font-size:11px;color:#888;text-transform:uppercase;font-weight:700;margin-bottom:6px">Cliente</div>
        <div><strong>${nombre}</strong></div>
        <div style="color:#555;font-size:12px">Tel: ${tel||'—'}</div>
      </div>
      <div class="presup-section">
        <div style="font-size:11px;color:#888;text-transform:uppercase;font-weight:700;margin-bottom:6px">Equipo</div>
        <div><strong>${marca} ${modelo}</strong></div>
        ${imei?`<div style="color:#555;font-size:12px">IMEI: ${imei}</div>`:''}
        <div style="color:#555;font-size:12px">Estado ingreso: ${document.getElementById('eq-estado-ingreso').value} | ${document.getElementById('eq-encendido').value}</div>
      </div>
      <div class="presup-section">
        <div style="font-size:11px;color:#888;text-transform:uppercase;font-weight:700;margin-bottom:6px">Servicio</div>
        <div><strong>${serv}</strong></div>
        ${detalle?`<div style="color:#444;font-size:12px;margin-top:4px">${detalle}</div>`:''}
        <div style="color:#555;font-size:12px;margin-top:4px">Tiempo estimado: ${tiempo}</div>
      </div>
      <div>
        <div class="presup-row"><span>Costo del servicio</span><span><strong>${fmt(costo)}</strong></span></div>
        <div class="presup-row"><span>Seña recibida</span><span style="color:#1a7a4a"><strong>- ${fmt(sena)}</strong></span></div>
        <div class="presup-row presup-total" style="border-top:1px solid #ddd;padding-top:6px;margin-top:4px"><span>Saldo a pagar al retirar</span><span>${fmt(saldo)}</span></div>
      </div>
    </div>`;
}

// Actualizar preview al escribir
['cli-nombre','cli-tel','eq-marca','eq-modelo','eq-imei','serv-tipo','serv-detalle','serv-tiempo','eq-estado-ingreso','eq-encendido'].forEach(id=>{
  const el = document.getElementById(id);
  if(el) el.addEventListener('input', actualizarPreview);
  if(el) el.addEventListener('change', actualizarPreview);
});

// =============================================
// REGISTRAR ORDEN
// =============================================
window.registrarOrden = async function(){
  const nombre = document.getElementById('cli-nombre').value.trim();
  const tel    = document.getElementById('cli-tel').value.trim();
  const marca  = document.getElementById('eq-marca').value;
  const modelo = document.getElementById('eq-modelo').value.trim();
  const imei   = document.getElementById('eq-imei').value.trim();
  const costo  = parseFloat(document.getElementById('serv-costo').value)||0;
  const sena   = parseFloat(document.getElementById('serv-sena').value)||0;
  const serv   = document.getElementById('serv-tipo').value;

  if(!nombre){ toast('Ingresá el nombre del cliente','err'); return; }
  if(!tel){ toast('Ingresá el teléfono del cliente','err'); return; }
  if(!marca){ toast('Seleccioná la marca del equipo','err'); return; }
  if(!modelo){ toast('Ingresá el modelo del equipo','err'); return; }
  if(!serv){ toast('Seleccioná el tipo de servicio','err'); return; }
  if(!costo){ toast('Ingresá el costo del servicio','err'); return; }
  if(!sena){ toast('Ingresá la seña recibida','err'); return; }
  if(sena < costo*0.5){ toast(`La seña mínima es ${fmt(costo*0.5)} (50%)`, 'warn'); return; }

  const codigo = genCodigo();
  const orden = {
    codigo, nombre, tel, marca, modelo, imei,
    estadoIngreso: document.getElementById('eq-estado-ingreso').value,
    encendido: document.getElementById('eq-encendido').value,
    accesorios: document.getElementById('eq-accesorios').value,
    obsIngreso: document.getElementById('eq-obs').value.trim(),
    servicio: serv,
    detalle: document.getElementById('serv-detalle').value.trim(),
    tiempo: document.getElementById('serv-tiempo').value,
    costo, sena, saldo: Math.max(0, costo-sena),
    estado: 'ingresado',
    pagos: [{monto:sena, fecha:new Date().toISOString(), tipo:'seña inicial'}],
    fechaIngreso: new Date().toISOString(),
    fechaActualizacion: new Date().toISOString()
  };

  try {
    await setDoc(doc(db,'servicio_tecnico',codigo), orden);
    ordenes.unshift(orden);
    toast(`✅ Orden ${codigo} registrada`);
    ordenActual = orden;
    verDetalle(codigo);
    limpiarForm();
  } catch(e){ toast('Error al guardar: '+e.message,'err'); }
}

// =============================================
// FIREBASE — CARGAR ÓRDENES
// =============================================
async function cargarOrdenes(){
  const snap = await getDocs(query(collection(db,'servicio_tecnico'), orderBy('fechaIngreso','desc')));
  ordenes = [];
  snap.forEach(d => ordenes.push(d.data()));
  renderOrdenes();
  renderStats();
}

// =============================================
// RENDER ÓRDENES
// =============================================
function renderStats(){
  const total    = ordenes.length;
  const ingresado= ordenes.filter(o=>o.estado==='ingresado').length;
  const proceso  = ordenes.filter(o=>o.estado==='proceso').length;
  const listo    = ordenes.filter(o=>o.estado==='listo').length;
  document.getElementById('stats-container').innerHTML=`
    <div class="stat-card"><div class="stat-n">${total}</div><div class="stat-l">Total órdenes</div></div>
    <div class="stat-card"><div class="stat-n" style="color:#58a6ff">${ingresado}</div><div class="stat-l">Ingresados</div></div>
    <div class="stat-card"><div class="stat-n" style="color:#e3b341">${proceso}</div><div class="stat-l">En proceso</div></div>
    <div class="stat-card"><div class="stat-n" style="color:#3fb950">${listo}</div><div class="stat-l">Listos para retirar</div></div>`;
}

window.filtrarOrdenes = function(){
  const busq   = document.getElementById('buscar-orden').value.toLowerCase();
  const filtro = document.getElementById('filtro-estado').value;
  const lista  = ordenes.filter(o=>{
    const matchBusq = !busq || o.codigo.toLowerCase().includes(busq) || o.nombre.toLowerCase().includes(busq) || (o.imei||'').includes(busq);
    const matchEstado = !filtro || o.estado===filtro;
    return matchBusq && matchEstado;
  });
  renderTabla(lista);
}

function renderOrdenes(){
  renderStats();
  renderTabla(ordenes);
}

function renderTabla(lista){
  const tbody = document.getElementById('tbody-ordenes');
  if(!lista.length){
    tbody.innerHTML=`<tr><td colspan="9" style="text-align:center;color:var(--text2);padding:40px">No hay órdenes que mostrar</td></tr>`;
    return;
  }
  tbody.innerHTML = lista.map(o=>`
    <tr>
      <td><span class="codigo-badge">${o.codigo}</span></td>
      <td><div style="font-weight:600">${o.nombre}</div><div style="font-size:11px;color:var(--text2)">${o.tel}</div></td>
      <td><div>${o.marca} ${o.modelo}</div>${o.imei?`<div style="font-size:11px;color:var(--text2)">IMEI: ${o.imei}</div>`:''}</td>
      <td>${o.servicio}</td>
      <td style="font-weight:600">${fmt(o.costo)}</td>
      <td style="color:#3fb950">${fmt(o.sena)}</td>
      <td style="color:${o.saldo>0?'#e3b341':'#3fb950'};font-weight:600">${fmt(o.saldo)}</td>
      <td>
        <select class="estado-select estado-${o.estado}" onchange="cambiarEstado('${o.codigo}',this.value,this)">
          <option value="ingresado" ${o.estado==='ingresado'?'selected':''}>Ingresado</option>
          <option value="proceso" ${o.estado==='proceso'?'selected':''}>En proceso</option>
          <option value="listo" ${o.estado==='listo'?'selected':''}>Listo para retirar</option>
          <option value="entregado" ${o.estado==='entregado'?'selected':''}>Entregado</option>
        </select>
      </td>
      <td>
        <div style="display:flex;gap:4px;flex-wrap:wrap">
          <button class="btn btn-ghost btn-sm" onclick="verDetalle('${o.codigo}')">Ver</button>
          <button class="btn btn-ghost btn-sm" onclick="abrirPago('${o.codigo}')" style="color:#3fb950">+ Pago</button>
          <button class="btn btn-ghost btn-sm" onclick="eliminarOrden('${o.codigo}')" style="color:var(--danger)">×</button>
        </div>
      </td>
    </tr>`).join('');
}

// =============================================
// CAMBIAR ESTADO
// =============================================
window.cambiarEstado = async function(codigo, nuevoEstado, selectEl){
  try{
    await updateDoc(doc(db,'servicio_tecnico',codigo),{estado:nuevoEstado,fechaActualizacion:new Date().toISOString()});
    const o = ordenes.find(x=>x.codigo===codigo);
    if(o){ o.estado=nuevoEstado; }
    selectEl.className = `estado-select estado-${nuevoEstado}`;
    renderStats();
    toast(`Estado actualizado: ${nuevoEstado}`);
  }catch(e){ toast('Error: '+e.message,'err'); }
}

// =============================================
// VER DETALLE
// =============================================
window.verDetalle = function(codigo){
  const o = ordenes.find(x=>x.codigo===codigo);
  if(!o) return;
  ordenActual = o;
  document.getElementById('modal-titulo').textContent = `Orden ${o.codigo}`;
  const pagosHtml = (o.pagos||[]).map(p=>`
    <div style="display:flex;justify-content:space-between;font-size:12px;padding:3px 0;border-bottom:1px solid var(--border)">
      <span>${p.tipo} — ${new Date(p.fecha).toLocaleDateString('es-AR')}</span>
      <span style="color:#3fb950;font-weight:600">${fmt(p.monto)}</span>
    </div>`).join('');

  document.getElementById('modal-body').innerHTML=`
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px">
      <div>
        <div style="font-size:11px;color:var(--text2);text-transform:uppercase;font-weight:700;margin-bottom:8px">Cliente</div>
        <div style="font-weight:600">${o.nombre}</div>
        <div style="color:var(--text2);font-size:13px">${o.tel}</div>
      </div>
      <div>
        <div style="font-size:11px;color:var(--text2);text-transform:uppercase;font-weight:700;margin-bottom:8px">Equipo</div>
        <div style="font-weight:600">${o.marca} ${o.modelo}</div>
        ${o.imei?`<div style="color:var(--text2);font-size:12px">IMEI: ${o.imei}</div>`:''}
        <div style="color:var(--text2);font-size:12px">${o.estadoIngreso} | ${o.encendido} | ${o.accesorios}</div>
      </div>
    </div>
    ${o.obsIngreso?`<div style="background:var(--surface2);border-radius:6px;padding:10px;margin-bottom:12px;font-size:12px;color:var(--text2)"><strong>Observaciones ingreso:</strong> ${o.obsIngreso}</div>`:''}
    <div style="background:var(--surface2);border-radius:8px;padding:14px;margin-bottom:14px">
      <div style="font-size:11px;color:var(--text2);text-transform:uppercase;font-weight:700;margin-bottom:8px">Servicio</div>
      <div style="font-weight:600">${o.servicio}</div>
      ${o.detalle?`<div style="color:var(--text2);font-size:12px;margin-top:6px">${o.detalle}</div>`:''}
      <div style="color:var(--text2);font-size:12px;margin-top:4px">⏱ ${o.tiempo}</div>
    </div>
    <div style="background:var(--surface2);border-radius:8px;padding:14px">
      <div style="font-size:11px;color:var(--text2);text-transform:uppercase;font-weight:700;margin-bottom:8px">Pagos</div>
      ${pagosHtml}
      <div style="display:flex;justify-content:space-between;margin-top:8px;font-size:14px;font-weight:700">
        <span>Saldo pendiente</span>
        <span style="color:${o.saldo>0?'#e3b341':'#3fb950'}">${fmt(o.saldo)}</span>
      </div>
    </div>`;
  document.getElementById('modal-detalle').classList.add('open');
}

// =============================================
// ENVIAR WHATSAPP
// =============================================
window.enviarWP = function(){
  if(!ordenActual) return;
  const o = ordenActual;
  const tel = o.tel.replace(/\D/g,'');
  const telWP = tel.startsWith('0') ? '549'+tel.slice(1) : tel.startsWith('54') ? tel : '549'+tel;
  const msg = [
    `🔧 *NICKCEL TECNO & HOGAR S.R.L.*`,
    `San Martín 514, Quitilipi, Chaco`,
    `WhatsApp: 3644924970`,
    ``,
    `📋 *ORDEN DE SERVICIO*`,
    `Código: *${o.codigo}*`,
    `Fecha: ${new Date(o.fechaIngreso).toLocaleDateString('es-AR')}`,
    ``,
    `👤 *CLIENTE*`,
    `${o.nombre} | ${o.tel}`,
    ``,
    `📱 *EQUIPO*`,
    `${o.marca} ${o.modelo}${o.imei?' | IMEI: '+o.imei:''}`,
    `Estado ingreso: ${o.estadoIngreso} | ${o.encendido}`,
    o.accesorios !== 'sin accesorios' ? `Accesorios: ${o.accesorios}` : '',
    ``,
    `🔧 *SERVICIO*`,
    `${o.servicio}`,
    o.detalle ? o.detalle : '',
    `⏱ Tiempo estimado: ${o.tiempo}`,
    ``,
    `💰 *PRESUPUESTO*`,
    `Costo total: ${fmt(o.costo)}`,
    `Seña abonada: ${fmt(o.sena)}`,
    `Saldo al retirar: *${fmt(o.saldo)}*`,
    ``,
    `_Guardá este mensaje como comprobante._`,
    `_Ante cualquier consulta mencioná tu código: ${o.codigo}_`
  ].filter(l=>l!==null).join('\n');

  window.open(`https://wa.me/${telWP}?text=${encodeURIComponent(msg)}`,'_blank');
}

// =============================================
// GENERAR PDF
// =============================================
window.generarPDF = function(){
  if(!ordenActual) return;
  const o = ordenActual;
  const { jsPDF } = window.jspdf;
  const doc2 = new jsPDF({unit:'mm',format:'a4'});
  const W = 210, ml = 15, mr = 195;
  let y = 0;

  // Header
  doc2.setFillColor(30,58,95);
  doc2.rect(0,0,W,32,'F');
  doc2.setTextColor(255,255,255);
  doc2.setFontSize(16); doc2.setFont('helvetica','bold');
  doc2.text('NICKCEL TECNO & HOGAR S.R.L.',ml,13);
  doc2.setFontSize(9); doc2.setFont('helvetica','normal');
  doc2.text('San Martín 514, Quitilipi, Chaco | WhatsApp: 3644924970 | CUIT: 30-71899140-0',ml,20);
  doc2.setFontSize(11); doc2.setFont('helvetica','bold');
  doc2.text('ORDEN DE SERVICIO TÉCNICO',ml,28);
  doc2.text(o.codigo, mr, 28, {align:'right'});

  y = 42;
  doc2.setTextColor(30,58,95);
  doc2.setFontSize(10); doc2.setFont('helvetica','bold');
  doc2.text(`Fecha: ${new Date(o.fechaIngreso).toLocaleDateString('es-AR')}`, mr, y, {align:'right'});

  // Sección cliente
  const seccion = (titulo, yy) => {
    doc2.setFillColor(240,246,255);
    doc2.rect(ml,yy-5,mr-ml,7,'F');
    doc2.setTextColor(30,58,95);
    doc2.setFontSize(9); doc2.setFont('helvetica','bold');
    doc2.text(titulo.toUpperCase(), ml+2, yy);
    return yy+8;
  };

  const linea = (label, val, yy) => {
    doc2.setFont('helvetica','bold'); doc2.setTextColor(80,80,80); doc2.setFontSize(9);
    doc2.text(label+':', ml+2, yy);
    doc2.setFont('helvetica','normal'); doc2.setTextColor(30,30,30);
    doc2.text(String(val||'—'), ml+45, yy);
    return yy+6;
  };

  y = seccion('Datos del cliente', y);
  y = linea('Nombre', o.nombre, y);
  y = linea('Teléfono', o.tel, y);
  y += 4;

  y = seccion('Equipo', y);
  y = linea('Marca / Modelo', `${o.marca} ${o.modelo}`, y);
  if(o.imei) y = linea('IMEI', o.imei, y);
  y = linea('Estado ingreso', o.estadoIngreso, y);
  y = linea('Ingresa', o.encendido, y);
  y = linea('Accesorios', o.accesorios, y);
  if(o.obsIngreso) y = linea('Observaciones', o.obsIngreso, y);
  y += 4;

  y = seccion('Servicio', y);
  y = linea('Tipo de servicio', o.servicio, y);
  y = linea('Tiempo estimado', o.tiempo, y);
  if(o.detalle){
    doc2.setFont('helvetica','bold'); doc2.setTextColor(80,80,80); doc2.setFontSize(9);
    doc2.text('Detalle:', ml+2, y);
    doc2.setFont('helvetica','normal'); doc2.setTextColor(30,30,30);
    const lines = doc2.splitTextToSize(o.detalle, mr-ml-50);
    doc2.text(lines, ml+45, y);
    y += lines.length*6+2;
  }
  y += 4;

  y = seccion('Presupuesto', y);
  y = linea('Costo del servicio', fmt(o.costo), y);
  y = linea('Seña recibida', fmt(o.sena), y);
  doc2.setFontSize(11); doc2.setFont('helvetica','bold'); doc2.setTextColor(30,58,95);
  doc2.text(`Saldo al retirar: ${fmt(o.saldo)}`, ml+2, y+2); y+=10;

  // Firmas
  y += 10;
  doc2.setDrawColor(100,100,100);
  doc2.line(ml, y+15, 85, y+15);
  doc2.line(125, y+15, mr, y+15);
  doc2.setFont('helvetica','normal'); doc2.setFontSize(9); doc2.setTextColor(80,80,80);
  doc2.text('Firma del cliente', ml, y+20);
  doc2.text('Firma Nickcel S.R.L.', 125, y+20);

  // Footer
  doc2.setFillColor(30,58,95);
  doc2.rect(0,280,W,17,'F');
  doc2.setTextColor(255,255,255); doc2.setFontSize(8); doc2.setFont('helvetica','normal');
  doc2.text(`Código: ${o.codigo} | Emitido: ${new Date().toLocaleDateString('es-AR')} | Nickcel Tecno & Hogar S.R.L.`,W/2,290,{align:'center'});

  doc2.save(`OrdenServicio_${o.codigo}.pdf`);
  toast('PDF descargado');
}

// =============================================
// PAGO ADICIONAL
// =============================================
window.abrirPago = function(codigo){
  const o = ordenes.find(x=>x.codigo===codigo);
  if(!o) return;
  pagoOrdenId = codigo;
  document.getElementById('modal-pago-body').innerHTML=`
    <div style="background:var(--surface2);border-radius:8px;padding:12px;font-size:13px">
      <div style="font-weight:700;margin-bottom:6px">${o.nombre} — ${o.codigo}</div>
      <div>Saldo pendiente: <strong style="color:#e3b341">${fmt(o.saldo)}</strong></div>
    </div>`;
  document.getElementById('pago-monto').value = o.saldo;
  document.getElementById('modal-pago').classList.add('open');
}

window.confirmarPago = async function(){
  const o = ordenes.find(x=>x.codigo===pagoOrdenId);
  if(!o) return;
  const monto = parseFloat(document.getElementById('pago-monto').value)||0;
  if(!monto){ toast('Ingresá el monto','warn'); return; }
  const nuevoSaldo = Math.max(0, o.saldo - monto);
  const pagos = [...(o.pagos||[]), {monto, fecha:new Date().toISOString(), tipo:'pago adicional'}];
  try{
    await updateDoc(doc(db,'servicio_tecnico',pagoOrdenId),{
      saldo: nuevoSaldo, pagos,
      sena: (o.sena||0)+monto,
      fechaActualizacion: new Date().toISOString()
    });
    o.saldo = nuevoSaldo; o.pagos = pagos; o.sena = (o.sena||0)+monto;
    cerrarModal('modal-pago');
    renderTabla(ordenes);
    toast(`Pago de ${fmt(monto)} registrado. Saldo: ${fmt(nuevoSaldo)}`);
  }catch(e){ toast('Error: '+e.message,'err'); }
}

// =============================================
// ELIMINAR
// =============================================
window.eliminarOrden = async function(codigo){
  if(!confirm(`¿Eliminar la orden ${codigo}?`)) return;
  try{
    await deleteDoc(doc(db,'servicio_tecnico',codigo));
    ordenes = ordenes.filter(o=>o.codigo!==codigo);
    renderOrdenes();
    toast('Orden eliminada');
  }catch(e){ toast('Error: '+e.message,'err'); }
}

// =============================================
// MODAL / FORM
// =============================================
window.cerrarModal = function(id){ document.getElementById(id).classList.remove('open'); }
window.limpiarForm = function(){
  ['cli-nombre','cli-tel','eq-modelo','eq-imei','eq-obs','serv-detalle','serv-costo','serv-sena'].forEach(id=>{
    document.getElementById(id).value='';
  });
  document.getElementById('eq-marca').value='';
  document.getElementById('serv-tipo').value='';
  document.getElementById('sena-box').style.display='none';
  document.getElementById('preview-presup').innerHTML='<div style="color:var(--text2);text-align:center;padding:40px 0">Completá los datos para ver el presupuesto</div>';
}

// =============================================
// INIT
// =============================================
cargarOrdenes();

// Listener tiempo real
onSnapshot(collection(db,'servicio_tecnico'), ()=>{ cargarOrdenes(); });
</script>
</body>
</html>
