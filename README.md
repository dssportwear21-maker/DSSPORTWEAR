<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DS SPORTWEAR — Kontrol Produksi</title>
<style>
:root{
  --glass-bg:rgba(255,255,255,.10);
  --glass-border:rgba(255,255,255,.22);
  --accent:#818cf8;
  --green:#34d399;
  --amber:#fbbf24;
  --red:#f87171;
  --text:#f8fafc;
  --muted:rgba(248,250,252,.72);
  --radius:18px;
}
*{margin:0;padding:0;box-sizing:border-box}
body{
  min-height:100vh;
  font-family:"Segoe UI",Tahoma,Geneva,Verdana,sans-serif;
  color:var(--text);
  background:#0b1020;
  padding:24px 16px;
  overflow-x:hidden;
}
body::before{content:"";position:fixed;inset:0;z-index:-1;pointer-events:none;background:
  radial-gradient(1100px 600px at 18% 8%,rgba(129,140,248,.20),transparent 60%),
  radial-gradient(1000px 620px at 85% 92%,rgba(236,72,153,.16),transparent 60%),
  linear-gradient(135deg,#0b1020 0%,#191636 50%,#0b1020 100%)}
@keyframes gradientShift{0%{background-position:0% 50%}50%{background-position:100% 50%}100%{background-position:0% 50%}}
/* ===== Landing Page ===== */
.landing{position:fixed;inset:0;z-index:200;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:24px;overflow:hidden;
  background:radial-gradient(1100px 600px at 18% 8%,rgba(129,140,248,.28),transparent 60%),
             radial-gradient(1000px 620px at 85% 92%,rgba(236,72,153,.24),transparent 60%),
             linear-gradient(135deg,#0b1020 0%,#1e1b4b 45%,#0b1020 100%);
  transition:opacity .6s ease,visibility .6s ease,transform .7s cubic-bezier(.22,1,.36,1)}
.landing::before{content:"";position:absolute;inset:-25%;background:repeating-linear-gradient(115deg,rgba(255,255,255,.045) 0 2px,transparent 2px 42px);animation:slide 14s linear infinite}
@keyframes slide{to{transform:translateX(42px)}}
body.entered .landing{opacity:0;visibility:hidden;pointer-events:none;transform:scale(1.07)}
.landing-inner{position:relative;z-index:2;max-width:840px;animation:rise .8s ease both}
@keyframes rise{from{opacity:0;transform:translateY(26px)}to{opacity:1;transform:none}}
.landing-emblem{width:78px;height:78px;border-radius:20px;margin:0 auto 22px;display:flex;align-items:center;justify-content:center;font-size:36px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.25);box-shadow:0 10px 40px rgba(0,0,0,.45);backdrop-filter:blur(8px)}
.landing-emblem img{width:100%;height:100%;object-fit:cover;border-radius:20px}
.landing-brand{font-size:.9rem;letter-spacing:7px;font-weight:700;color:#c7d2fe;text-transform:uppercase;margin-bottom:16px}
.landing-title{font-size:clamp(2.7rem,9vw,6rem);line-height:.94;font-weight:900;letter-spacing:-1px;text-transform:uppercase;
  background:linear-gradient(180deg,#ffffff 30%,#a5b4fc 74%,#6366f1 100%);-webkit-background-clip:text;background-clip:text;color:transparent}
.landing-rule{width:130px;height:4px;border-radius:99px;margin:24px auto;background:linear-gradient(90deg,#818cf8,#ec4899)}
.landing-sub{font-size:clamp(.95rem,2.4vw,1.15rem);color:var(--muted);max-width:580px;margin:0 auto 36px;line-height:1.65}
.landing-btn{font:inherit;font-size:1.05rem;font-weight:700;cursor:pointer;color:#fff;border:none;border-radius:14px;padding:16px 36px;background:linear-gradient(135deg,#6366f1,#8b5cf6);box-shadow:0 12px 40px rgba(99,102,241,.45);transition:transform .18s ease,box-shadow .18s ease}
.landing-btn:hover{transform:translateY(-3px);box-shadow:0 18px 52px rgba(99,102,241,.6)}
.landing-foot{position:absolute;bottom:22px;left:0;right:0;font-size:.75rem;letter-spacing:3px;color:rgba(248,250,252,.5);text-transform:uppercase}
@media (max-width:520px){.landing-brand{letter-spacing:4px}.landing-foot{letter-spacing:2px}}
.glass{
  background:var(--glass-bg);
  backdrop-filter:blur(16px);
  -webkit-backdrop-filter:blur(16px);
  border:1px solid var(--glass-border);
  border-radius:var(--radius);
  box-shadow:0 8px 32px rgba(0,0,0,.28);
}
.app{max-width:1100px;margin:0 auto;display:flex;flex-direction:column;gap:20px;opacity:0;transform:translateY(24px) scale(.985);transition:opacity .7s cubic-bezier(.22,1,.36,1),transform .7s cubic-bezier(.22,1,.36,1)}
body.entered .app{opacity:1;transform:none}
.app-header{display:flex;align-items:center;justify-content:space-between;gap:16px;flex-wrap:wrap;padding:20px 24px}
.brand{display:flex;align-items:center;gap:14px}
.logo{width:52px;height:52px;border-radius:14px;display:flex;align-items:center;justify-content:center;font-size:26px;background:rgba(129,140,248,.28);border:1px solid rgba(129,140,248,.45);overflow:hidden;position:relative;flex-shrink:0}
.logo img{width:100%;height:100%;object-fit:cover}
.logo-edit{position:absolute;right:-6px;bottom:-6px;width:22px;height:22px;border-radius:50%;background:#6366f1;color:#fff;border:2px solid rgba(255,255,255,.65);display:flex;align-items:center;justify-content:center;font-size:11px;cursor:pointer;padding:0;line-height:1;transition:transform .15s ease}
.logo-edit:hover{transform:scale(1.15)}
.app-header h1{font-size:1.35rem;font-weight:700;letter-spacing:.3px}
.app-header p{font-size:.85rem;color:var(--muted);margin-top:2px}
.btn{font:inherit;cursor:pointer;border:none;color:var(--text);border-radius:12px;padding:10px 18px;font-size:.92rem;font-weight:600;transition:transform .15s ease,background .2s ease,box-shadow .2s ease}
.btn:hover{transform:translateY(-2px)}
.btn:disabled{opacity:.45;cursor:not-allowed;transform:none}
.btn-primary{background:linear-gradient(135deg,#818cf8,#6366f1);box-shadow:0 6px 18px rgba(99,102,241,.4)}
.btn-primary:hover{box-shadow:0 8px 24px rgba(99,102,241,.55)}
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:16px}
.stat{padding:18px 20px}
.stat-label{font-size:.8rem;color:var(--muted);text-transform:uppercase;letter-spacing:.8px}
.stat-value{font-size:1.6rem;font-weight:700;margin-top:6px}
.stat-sub{font-size:.78rem;color:var(--muted);margin-top:4px}
.stat-icon{float:right;font-size:1.5rem;opacity:.85}
.toolbar{display:flex;gap:12px;flex-wrap:wrap;padding:16px 18px;align-items:center}
.toolbar input,.toolbar select{font:inherit;color:var(--text);background:rgba(255,255,255,.12);border:1px solid var(--glass-border);border-radius:10px;padding:9px 12px;outline:none}
.toolbar input{flex:1;min-width:180px}
.toolbar input::placeholder{color:rgba(248,250,252,.5)}
.toolbar select option{color:#1e293b}
/* ===== Order Cards ===== */
.orders{display:grid;grid-template-columns:1fr;gap:20px}
.order-card{padding:22px 24px;display:flex;flex-direction:column;gap:16px;position:relative;overflow:hidden}
.order-card::before{content:"";position:absolute;left:0;top:0;bottom:0;width:4px;background:var(--accent)}
.order-card.stage-8::before{background:var(--green)}
.order-top{display:flex;justify-content:space-between;align-items:flex-start;gap:12px;flex-wrap:wrap}
.order-id{font-size:.72rem;color:var(--muted);letter-spacing:1px;text-transform:uppercase}
.order-customer{font-size:1.25rem;font-weight:700;margin-top:2px}
.order-badges{display:flex;gap:8px;flex-wrap:wrap}
.badge{font-size:.72rem;font-weight:700;padding:5px 12px;border-radius:99px;border:1px solid transparent;letter-spacing:.4px}
.badge-type{background:rgba(129,140,248,.18);color:#c7d2fe;border-color:rgba(129,140,248,.4)}
.badge-dp{background:rgba(251,191,36,.16);color:#fde68a;border-color:rgba(251,191,36,.4)}
.badge-lunas{background:rgba(52,211,153,.16);color:#a7f3d0;border-color:rgba(52,211,153,.4)}
.badge-ready{background:rgba(52,211,153,.16);color:#a7f3d0;border-color:rgba(52,211,153,.45)}
.badge-overdue{background:rgba(248,113,113,.16);color:#fecaca;border-color:rgba(248,113,113,.4)}

.order-meta{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px}
.meta-item{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);border-radius:12px;padding:10px 14px}
.meta-label{font-size:.7rem;color:var(--muted);text-transform:uppercase;letter-spacing:.6px}
.meta-value{font-size:1rem;font-weight:600;margin-top:3px}
.meta-value.green{color:var(--green)}
.meta-value.amber{color:var(--amber)}
.meta-value.red{color:var(--red)}

/* ===== Payment bar ===== */
.payment-box{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);border-radius:12px;padding:12px 16px}
.payment-row{display:flex;justify-content:space-between;font-size:.85rem;margin-bottom:8px}
.payment-row .muted{color:var(--muted)}
.pay-bar{height:8px;border-radius:99px;background:rgba(255,255,255,.14);overflow:hidden}
.pay-fill{height:100%;border-radius:99px;background:linear-gradient(90deg,#818cf8,#34d399);transition:width .5s ease}

/* ===== Stage Stepper ===== */
.stages-label{display:flex;justify-content:space-between;align-items:center;font-size:.75rem;color:var(--muted)}
.stepper{display:flex;align-items:flex-start;gap:0;overflow-x:auto;padding:6px 2px 2px}
.step{display:flex;flex-direction:column;align-items:center;gap:8px;min-width:74px;position:relative;flex:1}
.step .dot{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;background:rgba(255,255,255,.1);border:2px solid rgba(255,255,255,.25);transition:all .3s ease;z-index:1}
.step .name{font-size:.68rem;text-align:center;color:var(--muted);line-height:1.2;max-width:76px}
.step::after{content:"";position:absolute;top:16px;left:50%;width:100%;height:2px;background:rgba(255,255,255,.15);z-index:0}
.step:last-child::after{display:none}
.step.done .dot{background:rgba(52,211,153,.25);border-color:var(--green)}
.step.done .name{color:#a7f3d0}
.step.done::after{background:var(--green)}
.step.current .dot{background:var(--accent);border-color:#c7d2fe;box-shadow:0 0 0 5px rgba(129,140,248,.25);transform:scale(1.1)}
.step.current .name{color:#e0e7ff;font-weight:700}
.step.current::after{background:linear-gradient(90deg,var(--green),rgba(255,255,255,.15))}

/* ===== Card actions ===== */
.order-actions{display:flex;gap:8px;flex-wrap:wrap;padding-top:4px;border-top:1px solid rgba(255,255,255,.12)}
.btn-sm{padding:7px 13px;font-size:.8rem;border-radius:9px}
.btn-next{background:linear-gradient(135deg,#34d399,#10b981);box-shadow:0 4px 12px rgba(16,185,129,.35)}
.btn-prev{background:rgba(255,255,255,.12);border:1px solid var(--glass-border)}
.btn-edit{background:rgba(129,140,248,.2);border:1px solid rgba(129,140,248,.4)}
.btn-del{background:rgba(248,113,113,.15);border:1px solid rgba(248,113,113,.4);color:#fecaca}
.btn-pay{background:rgba(251,191,36,.16);border:1px solid rgba(251,191,36,.4);color:#fde68a}
.btn-invoice{background:rgba(56,189,248,.16);border:1px solid rgba(56,189,248,.42);color:#bae6fd}

/* ===== Empty state ===== */
.empty{grid-column:1/-1;text-align:center;padding:56px 20px;color:var(--muted)}
.empty .big{font-size:3rem;margin-bottom:12px}

/* ===== Modal ===== */
.modal-overlay{position:fixed;inset:0;background:rgba(15,10,40,.6);backdrop-filter:blur(6px);-webkit-backdrop-filter:blur(6px);display:none;align-items:flex-start;justify-content:center;padding:40px 16px;z-index:100;overflow-y:auto}
.modal-overlay.open{display:flex}
.modal{width:100%;max-width:560px;padding:26px 28px;background:rgba(49,46,129,.55);border:1px solid rgba(255,255,255,.25);border-radius:20px;box-shadow:0 20px 60px rgba(0,0,0,.4);margin:auto}
.modal h2{font-size:1.3rem;margin-bottom:4px}
.modal .sub{font-size:.82rem;color:var(--muted);margin-bottom:20px}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.field{display:flex;flex-direction:column;gap:6px}
.field.full{grid-column:1/-1}
.field label{font-size:.78rem;color:var(--muted);font-weight:600}
.field input,.field select,.field textarea{font:inherit;color:var(--text);background:rgba(255,255,255,.1);border:1px solid var(--glass-border);border-radius:10px;padding:9px 12px;outline:none;width:100%}
.field input:focus,.field select:focus,.field textarea:focus{border-color:var(--accent);background:rgba(255,255,255,.16)}
.field select option{color:#1e293b}
.field textarea{resize:vertical;min-height:64px}
.modal-actions{display:flex;justify-content:flex-end;gap:10px;margin-top:22px}

@media (max-width:640px){
  .stats{grid-template-columns:1fr 1fr}
  .form-grid{grid-template-columns:1fr}
  .app-header h1{font-size:1.1rem}
}
.btn-back{background:rgba(255,255,255,.1);border:1px solid var(--glass-border)}
.btn-back:hover{background:rgba(255,255,255,.18)}
.app-actions{display:flex;gap:10px;align-items:center;flex-wrap:wrap}
.app-footer{text-align:center;padding:10px 0 2px;color:rgba(248,250,252,.42);font-size:.75rem;letter-spacing:3px;text-transform:uppercase}
.app-footer b{background:linear-gradient(90deg,#818cf8,#ec4899);-webkit-background-clip:text;background-clip:text;color:transparent;font-weight:800}
</style>
</head>
<body>
<div class="landing" id="landing">
  <div class="landing-inner">
    <div class="landing-emblem" id="landingEmblem">🥊</div>
    <div class="landing-brand">DS Sportwear</div>
    <h1 class="landing-title">Beyond<br>The Fight</h1>
    <div class="landing-rule"></div>
    <p class="landing-sub">Kontrol penuh atas setiap tahap produksi apparel — dari desain, produksi, hingga siap kirim. Dibuat untuk mereka yang tidak pernah berhenti bertarung.</p>
    <button class="landing-btn" onclick="enterApp()">Masuk ke Panel Kontrol →</button>
  </div>
  <div class="landing-foot">Gondanglegi • Malang • Jawa Timur</div>
</div>
<div class="app">
  <header class="app-header glass">
    <div class="brand">
      <div class="logo" id="logoBox" title="Klik kanan untuk hapus logo kustom" oncontextmenu="resetLogo(event)">
        <span id="logoEmoji">🧵</span>
        <img id="logoImg" alt="Logo Perusahaan" style="display:none">
        <button type="button" class="logo-edit" onclick="triggerLogoUpload()" title="Ganti logo perusahaan">✎</button>
      </div>
      <div>
        <h1>DS SPORTWEAR</h1>
        <p>Sistem Kontrol Produksi &amp; Pembayaran</p>
      </div>
    </div>
    <input type="file" id="logoInput" accept="image/*" style="display:none" onchange="handleLogoUpload(event)">
    <div class="app-actions">
      <button class="btn btn-back" onclick="backToLanding()" title="Kembali ke Landing Page">← Landing</button>
      <button class="btn btn-primary" onclick="openModal()">+ Tambah Pesanan</button>
    </div>
  </header>
  <section class="stats">
    <div class="stat glass"><span class="stat-icon">📦</span><div class="stat-label">Total Pesanan</div><div class="stat-value" id="statTotal">0</div></div>
    <div class="stat glass"><span class="stat-icon">⚙️</span><div class="stat-label">Dalam Proses</div><div class="stat-value" id="statProgress">0</div></div>
    <div class="stat glass"><span class="stat-icon">🚚</span><div class="stat-label">Siap Kirim</div><div class="stat-value" id="statReady">0</div></div>
    <div class="stat glass"><span class="stat-icon">👕</span><div class="stat-label">Total Jumlah</div><div class="stat-value" id="statValue">0 pcs</div><div class="stat-sub" id="statPaid">Dari 0 pesanan</div></div>
  </section>
  <section class="toolbar glass">
    <input type="text" id="searchInput" placeholder="Cari nama konsumen / jenis / ID...">
    <select id="stageFilter"><option value="">Semua Tahapan</option></select>
    <select id="paymentFilter">
      <option value="">Semua Pembayaran</option>
      <option value="DP">DP</option>
      <option value="Lunas">Lunas</option>
      <option value="Transfer">Transfer</option>
      <option value="Tunai">Tunai</option>
    </select>
    <select id="sortSelect">
      <option value="newest">Terbaru</option>
      <option value="deadline">Deadline Terdekat</option>
      <option value="name">Nama A-Z</option>
      <option value="qty">Jumlah Terbanyak</option>
    </select>
  </section>
  <main class="orders" id="orders"></main>
  <footer class="app-footer">© 2026 <b>DS Sportwear</b> — Beyond The Fight</footer>
</div>
<div class="modal-overlay" id="modalOverlay" onclick="if(event.target===this)closeModal()">
  <div class="modal glass">
    <h2 id="modalTitle">Tambah Pesanan</h2>
    <p class="sub">Isi data pemesan, detail pesanan, jenis pembayaran, dan bahan.</p>
    <form id="orderForm" onsubmit="saveOrder(event)">
      <input type="hidden" id="editId">
      <div class="form-grid">
        <div class="field">
          <label for="fCustomer">Nama Pemesan *</label>
          <input type="text" id="fCustomer" required placeholder="cth: Budi Santoso">
        </div>
        <div class="field">
          <label for="fType">Jenis Pesanan *</label>
          <select id="fType" required>
            <option value="Kaos">Kaos</option>
            <option value="Kemeja">Kemeja</option>
            <option value="Jaket">Jaket / Hoodie</option>
            <option value="Seragam">Seragam</option>
            <option value="Jersey">Jersey</option>
            <option value="Lainnya">Lainnya</option>
          </select>
        </div>
        <div class="field">
          <label for="fQty">Jumlah Pesanan (pcs) *</label>
          <input type="number" id="fQty" min="1" required placeholder="cth: 100">
        </div>
        <div class="field">
          <label for="fPayment">Jenis Pembayaran *</label>
          <select id="fPayment" required>
            <option value="DP">DP (Uang Muka)</option>
            <option value="Lunas">Lunas (Cash)</option>
            <option value="Transfer">Transfer Bank</option>
            <option value="Tunai">Tunai</option>
          </select>
        </div>
        <div class="field">
          <label for="fPrice">Harga Satuan (Rp)</label>
          <input type="number" id="fPrice" min="0" step="500" placeholder="cth: 50000">
        </div>
        <div class="field full">
          <label for="fMaterial">Bahan yang Dipakai *</label>
          <input type="text" id="fMaterial" required placeholder="cth: Cotton Combed 30s, Drill, Fleece...">
        </div>
        <div class="field">
          <label for="fDeadline">Deadline Pengiriman</label>
          <input type="date" id="fDeadline">
        </div>
        <div class="field">
          <label for="fStage">Tahap Saat Ini</label>
          <select id="fStage"></select>
        </div>
      </div>
      <div class="modal-actions">
        <button type="button" class="btn btn-sm btn-prev" onclick="closeModal()">Batal</button>
        <button type="submit" class="btn btn-primary">Simpan Pesanan</button>
      </div>
    </form>
  </div>
</div>
<script>
/* ===== Konstanta Tahapan Produksi ===== */
const STAGES = [
  { name: "Pengerjaan",    icon: "📝" },
  { name: "Desain",        icon: "🎨" },
  { name: "Layout Desain", icon: "📐" },
  { name: "Print Press",   icon: "🖨️" },
  { name: "Cutting",       icon: "✂️" },
  { name: "Sewing",        icon: "🧵" },
  { name: "QC",            icon: "🔍" },
  { name: "Packing",       icon: "📦" },
  { name: "Siap Kirim",    icon: "🚚" }
];

/* ===== Data Awal (contoh) ===== */
const seedData = [
  { id:"ORD-001", customer:"Budi Santoso", type:"Kaos", qty:120, price:50000, payment:"DP", material:"Cotton Combed 30s", stage:3, deadline:"2026-11-01", created:"2026-10-01" },
  { id:"ORD-002", customer:"CV Maju Jaya", type:"Seragam", qty:200, price:75000, payment:"Lunas", material:"Drill Katun", stage:6, deadline:"2026-10-20", created:"2026-09-15" },
  { id:"ORD-003", customer:"Siti Nurhaliza", type:"Jaket", qty:50, price:180000, payment:"DP", material:"Fleece", stage:1, deadline:"2026-11-10", created:"2026-10-05" },
  { id:"ORD-004", customer:"PT Tekstil Nusantara", type:"Jersey", qty:300, price:40000, payment:"Transfer", material:"Polyester Micromesh", stage:0, deadline:"2026-11-25", created:"2026-10-08" }
];

let orders = [];
let filters = { search:"", stage:"", payment:"", sort:"newest" };

/* ===== Identitas Perusahaan (untuk Invoice & Faktur) ===== */
const COMPANY = {
  name: "DS SPORTWEAR",
  address: "Gondanglegi, Malang, Jawa Timur",
  phone: "0895-6312-00043",
  email: "dssportwear21@gmail.com",
  npwp: "-"
};

/* ===== Utility ===== */
const $ = id => document.getElementById(id);
const fmtRp = n => "Rp " + Number(n||0).toLocaleString("id-ID");
const esc = s => String(s??"").replace(/[&<>"']/g, c => ({ "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;" }[c]));
const payStatus = o => o.payment || "DP";
const payBadgeClass = o => payStatus(o) === "DP" ? "badge-dp" : "badge-lunas";
const isOverdue = o => o.deadline && o.stage < STAGES.length-1 && new Date(o.deadline) < new Date(new Date().toDateString());
/* ===== Inisialisasi ===== */
function init(){
  const saved = localStorage.getItem("apc_orders");
  orders = saved ? JSON.parse(saved) : seedData.slice();
  persist();
  buildStageSelects();
  bindToolbar();
  loadLogo();
  render();
  if(localStorage.getItem("apc_entered") === "1"){ document.body.classList.add("entered"); }
}
function persist(){ localStorage.setItem("apc_orders", JSON.stringify(orders)); }

/* ===== Logo Perusahaan ===== */
function loadLogo(){
  const saved = localStorage.getItem("apc_logo");
  const le = $("landingEmblem");
  if(saved){
    $("logoImg").src = saved;
    $("logoImg").style.display = "block";
    $("logoEmoji").style.display = "none";
    if(le) le.innerHTML = '<img src="'+saved+'" alt="logo">';
  }
}
function triggerLogoUpload(){ $("logoInput").click(); }
function handleLogoUpload(e){
  const file = e.target.files && e.target.files[0];
  if(!file) return;
  if(!file.type.startsWith("image/")){ alert("File harus berupa gambar (PNG/JPG/SVG)."); return; }
  if(file.size > 2 * 1024 * 1024){ alert("Ukuran gambar terlalu besar (maks 2MB)."); return; }
  const reader = new FileReader();
  reader.onload = function(ev){
    try{
      localStorage.setItem("apc_logo", ev.target.result);
      loadLogo();
    }catch(err){
      alert("Gagal menyimpan logo. Coba gambar yang lebih kecil.");
    }
  };
  reader.readAsDataURL(file);
  e.target.value = "";
}
function resetLogo(e){
  if(e) e.preventDefault();
  if(!localStorage.getItem("apc_logo")){ alert("Belum ada logo kustom yang di-set."); return; }
  if(!confirm("Hapus logo kustom dan kembalikan ke logo default?")) return;
  localStorage.removeItem("apc_logo");
  $("logoImg").style.display = "none";
  $("logoEmoji").style.display = "";
  const le = $("landingEmblem"); if(le) le.innerHTML = "🥊";
}

/* ===== Landing Page ===== */
function enterApp(){
  document.body.classList.add("entered");
  try{ localStorage.setItem("apc_entered","1"); }catch(e){}
  window.scrollTo({top:0,behavior:"smooth"});
}
function backToLanding(){
  document.body.classList.remove("entered");
  try{ localStorage.removeItem("apc_entered"); }catch(e){}
  window.scrollTo({top:0,behavior:"smooth"});
}

/* ===== Cetak Invoice & Faktur ===== */
function printDocument(id, type){
  const o = orders.find(x=>x.id===id);
  if(!o) return;
  const logo = localStorage.getItem("apc_logo") || "";
  const isFaktur = type === "faktur";
  const unitPrice = Number(o.price||0);
  const total = unitPrice * Number(o.qty||0);
  const docNo = (isFaktur ? "FKT-" : "INV-") + String(o.id).replace(/\D/g,"");
  const today = new Date().toLocaleDateString("id-ID",{day:"numeric",month:"long",year:"numeric"});
  const paid = payStatus(o) === "Lunas" || payStatus(o) === "Tunai";
  const desc = esc(o.type) + (o.material ? " — " + esc(o.material) : "");
  const logoHTML = logo ? '<img src="'+logo+'" alt="logo">' : '<div class="logo-fallback">🧵</div>';

  const html = `<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>${docNo}</title>
<style>
*{box-sizing:border-box}
body{font-family:"Segoe UI",Arial,sans-serif;color:#1e293b;margin:0;padding:32px;background:#fff}
.doc{max-width:760px;margin:0 auto}
.toolbar{text-align:center;margin-bottom:20px}
.toolbar button{font:inherit;cursor:pointer;border:none;padding:10px 22px;border-radius:8px;background:#4f46e5;color:#fff;font-weight:600}
.head{display:flex;justify-content:space-between;align-items:flex-start;border-bottom:3px solid #4f46e5;padding-bottom:16px;gap:16px}
.company{display:flex;gap:14px;align-items:center}
.company img{width:64px;height:64px;object-fit:cover;border-radius:10px}
.logo-fallback{width:64px;height:64px;border-radius:10px;background:#eef2ff;display:flex;align-items:center;justify-content:center;font-size:30px}
.cname{font-size:20px;font-weight:800;color:#312e81}
.cmeta{font-size:12px;color:#64748b;line-height:1.5;margin-top:4px}
.doctitle{text-align:right}
.doctitle h1{margin:0;font-size:26px;letter-spacing:2px;color:#4f46e5}
.doctitle .no{font-size:13px;color:#475569;margin-top:6px;line-height:1.5}
.parties{display:flex;justify-content:space-between;margin:22px 0;gap:20px}
.party h3{font-size:11px;text-transform:uppercase;letter-spacing:1px;color:#94a3b8;margin:0 0 6px}
.party .val{font-size:15px;font-weight:600}
table{width:100%;border-collapse:collapse;margin-top:8px}
th{background:#4f46e5;color:#fff;text-align:left;padding:10px 12px;font-size:13px}
td{padding:10px 12px;border-bottom:1px solid #e2e8f0;font-size:14px}
.num{text-align:right}
.total-box{margin-top:16px;display:flex;justify-content:flex-end}
.total-box .inner{min-width:280px}
.total-line{display:flex;justify-content:space-between;padding:8px 12px;font-size:14px}
.total-line.grand{background:#eef2ff;font-weight:800;font-size:16px;border-radius:8px;margin-top:6px}
.pay-status{display:inline-block;padding:5px 14px;border-radius:99px;font-size:12px;font-weight:700;background:#fef3c7;color:#92400e}
.pay-status.lunas{background:#d1fae5;color:#065f46}
.notes{margin-top:22px;font-size:12px;color:#64748b;line-height:1.6}
.sign{margin-top:48px;display:flex;justify-content:space-between}
.sign .box{text-align:center;width:200px;font-size:13px}
.sign .line{margin-top:64px;border-top:1px solid #334155;padding-top:6px}
.footer{margin-top:36px;text-align:center;font-size:11px;color:#94a3b8;border-top:1px solid #e2e8f0;padding-top:12px}
@media print{body{padding:0}.noprint{display:none}}
</style>
</head>
<body>
<div class="doc">
  <div class="toolbar noprint"><button onclick="window.print()">🖨️ Cetak / Simpan sebagai PDF</button></div>
  <div class="head">
    <div class="company">
      ${logoHTML}
      <div>
        <div class="cname">${COMPANY.name}</div>
        <div class="cmeta">${COMPANY.address}<br>Telp: ${COMPANY.phone} &bull; ${COMPANY.email}${(isFaktur && COMPANY.npwp && COMPANY.npwp !== "-") ? "<br>NPWP: "+COMPANY.npwp : ""}</div>
      </div>
    </div>
    <div class="doctitle">
      <h1>${isFaktur ? "FAKTUR" : "INVOICE"}</h1>
      <div class="no">No: ${docNo}<br>Tanggal: ${today}</div>
    </div>
  </div>
  <div class="parties">
    <div class="party">
      <h3>Ditagihkan Kepada</h3>
      <div class="val">${esc(o.customer)}</div>
    </div>
    <div class="party" style="text-align:right">
      <h3>Status Pembayaran</h3>
      <span class="pay-status ${paid?"lunas":""}">${esc(payStatus(o))}</span>
    </div>
  </div>
  <table>
    <thead><tr><th>Deskripsi</th><th class="num">Qty</th><th class="num">Harga Satuan</th><th class="num">Jumlah</th></tr></thead>
    <tbody>
      <tr><td>${desc}</td><td class="num">${o.qty}</td><td class="num">${fmtRp(unitPrice)}</td><td class="num">${fmtRp(total)}</td></tr>
    </tbody>
  </table>
  <div class="total-box">
    <div class="inner">
      <div class="total-line"><span>Subtotal</span><span>${fmtRp(total)}</span></div>
      <div class="total-line grand"><span>TOTAL</span><span>${fmtRp(total)}</span></div>
    </div>
  </div>
  <div class="notes">Deadline Pengiriman: ${esc(o.deadline||"-")} &bull; Jenis Pesanan: ${esc(o.type)} &bull; Bahan: ${esc(o.material||"-")}<br>Terima kasih atas kepercayaan Anda.</div>
  <div class="sign">
    <div class="box"><div class="line">Penerima</div></div>
    <div class="box"><div class="line">Hormat Kami,<br>${COMPANY.name}</div></div>
  </div>
  <div class="footer">Dokumen ini dibuat secara otomatis oleh ${COMPANY.name}.</div>
</div>
</body>
</html>`;

  const w = window.open("", "_blank", "width=820,height=920");
  if(!w){ alert("Popup diblokir. Izinkan popup pada browser untuk mencetak dokumen."); return; }
  w.document.open();
  w.document.write(html);
  w.document.close();
  w.focus();
}

/* ===== Dropdown tahapan ===== */
function buildStageSelects(){
  const sf = $("stageFilter"), fs = $("fStage");
  STAGES.forEach((s,i)=>{
    sf.insertAdjacentHTML("beforeend", `<option value="${i}">${i+1}. ${s.name}</option>`);
    fs.insertAdjacentHTML("beforeend", `<option value="${i}">${i+1}. ${s.name}</option>`);
  });
}

/* ===== Toolbar events ===== */
function bindToolbar(){
  $("searchInput").addEventListener("input", e => { filters.search = e.target.value.toLowerCase(); render(); });
  $("stageFilter").addEventListener("change", e => { filters.stage = e.target.value; render(); });
  $("paymentFilter").addEventListener("change", e => { filters.payment = e.target.value; render(); });
  $("sortSelect").addEventListener("change", e => { filters.sort = e.target.value; render(); });
}

/* ===== Filter + Sort ===== */
function getVisible(){
  let list = orders.filter(o=>{
    const q = filters.search;
    const matchQ = !q || o.customer.toLowerCase().includes(q) || o.type.toLowerCase().includes(q) || o.id.toLowerCase().includes(q);
    const matchS = filters.stage==="" || o.stage === Number(filters.stage);
    const matchP = filters.payment==="" || payStatus(o) === filters.payment;
    return matchQ && matchS && matchP;
  });
  switch(filters.sort){
    case "deadline": list.sort((a,b)=> (a.deadline||"9999").localeCompare(b.deadline||"9999")); break;
    case "name": list.sort((a,b)=> a.customer.localeCompare(b.customer)); break;
    case "qty": list.sort((a,b)=> b.qty - a.qty); break;
    default: list.sort((a,b)=> (b.created||"").localeCompare(a.created||""));
  }
  return list;
}
/* ===== Render utama ===== */
function render(){
  renderStats();
  const list = getVisible();
  const box = $("orders");
  if(!list.length){
    box.innerHTML = `<div class="empty glass"><div class="big">🗂️</div><h3>Tidak ada pesanan</h3><p>Belum ada data yang cocok dengan filter, atau tambahkan pesanan baru.</p></div>`;
    return;
  }
  box.innerHTML = list.map(cardHTML).join("");
}

function renderStats(){
  $("statTotal").textContent = orders.length;
  $("statProgress").textContent = orders.filter(o=> o.stage < STAGES.length-1).length;
  $("statReady").textContent = orders.filter(o=> o.stage === STAGES.length-1).length;
  $("statValue").textContent = orders.reduce((s,o)=> s + Number(o.qty||0), 0) + " pcs";
  $("statPaid").textContent = "Dari " + orders.length + " pesanan";
}

function stepperHTML(o){
  return STAGES.map((s,i)=>{
    let cls = "step";
    if(i < o.stage) cls += " done";
    else if(i === o.stage) cls += " current";
    return `<div class="${cls}" title="${s.name}"><div class="dot">${i < o.stage ? "✓" : s.icon}</div><div class="name">${s.name}</div></div>`;
  }).join("");
}
function cardHTML(o){
  const done = o.stage === STAGES.length-1;
  const badges = [
    `<span class="badge badge-type">${esc(o.type)}</span>`,
    `<span class="badge ${payBadgeClass(o)}">${esc(payStatus(o))}</span>`
  ];
  if(done) badges.push(`<span class="badge badge-ready">✓ Siap Kirim</span>`);
  if(isOverdue(o)) badges.push(`<span class="badge badge-overdue">⚠ Terlambat</span>`);

  return `
  <article class="order-card glass stage-${o.stage}">
    <div class="order-top">
      <div>
        <div class="order-id">${esc(o.id)} • dibuat ${esc(o.created||"-")}</div>
        <div class="order-customer">${esc(o.customer)}</div>
      </div>
      <div class="order-badges">${badges.join("")}</div>
    </div>
    <div class="order-meta">
      <div class="meta-item"><div class="meta-label">Jenis Pesanan</div><div class="meta-value">${esc(o.type)}</div></div>
      <div class="meta-item"><div class="meta-label">Jumlah Pesanan</div><div class="meta-value">${o.qty} pcs</div></div>
      <div class="meta-item"><div class="meta-label">Jenis Pembayaran</div><div class="meta-value">${esc(payStatus(o))}</div></div>
      <div class="meta-item"><div class="meta-label">Harga Satuan</div><div class="meta-value">${fmtRp(o.price||0)}</div></div>
      <div class="meta-item"><div class="meta-label">Bahan</div><div class="meta-value">${esc(o.material||"-")}</div></div>
      <div class="meta-item"><div class="meta-label">Deadline</div><div class="meta-value ${isOverdue(o)?"red":""}">${esc(o.deadline||"-")}</div></div>
    </div>
    <div>
      <div class="stages-label"><span>Tahap Produksi</span><span>${o.stage+1} / ${STAGES.length} — <b style="color:var(--text)">${STAGES[o.stage].name}</b></span></div>
      <div class="stepper">${stepperHTML(o)}</div>
    </div>
    <div class="order-actions">
      <button class="btn btn-sm btn-prev" onclick="moveStage('${o.id}',-1)" ${o.stage===0?"disabled":""}>◀ Sebelumnya</button>
      <button class="btn btn-sm btn-next" onclick="moveStage('${o.id}',1)" ${done?"disabled":""}>${done?"Selesai":"Berikutnya ▶"}</button>
      <button class="btn btn-sm btn-pay" onclick="changePayment('${o.id}')">💳 Pembayaran</button>
      <button class="btn btn-sm btn-invoice" onclick="printDocument('${o.id}','invoice')">🧾 Invoice</button>
      <button class="btn btn-sm btn-invoice" onclick="printDocument('${o.id}','faktur')">📄 Faktur</button>
      <button class="btn btn-sm btn-edit" onclick="openModal('${o.id}')">✏️ Edit</button>
      <button class="btn btn-sm btn-del" onclick="deleteOrder('${o.id}')">🗑 Hapus</button>
    </div>
  </article>`;
}
/* ===== Aksi tahapan ===== */
function moveStage(id, dir){
  const o = orders.find(x=>x.id===id);
  if(!o) return;
  const next = o.stage + dir;
  if(next < 0 || next >= STAGES.length) return;
  o.stage = next;
  persist();
  render();
}

/* ===== Modal CRUD ===== */
function openModal(id){
  $("orderForm").reset();
  if(id){
    const o = orders.find(x=>x.id===id);
    if(!o) return;
    $("modalTitle").textContent = "Edit Pesanan " + o.id;
    $("editId").value = o.id;
    $("fCustomer").value = o.customer;
    $("fType").value = o.type;
    $("fQty").value = o.qty;
    $("fPayment").value = o.payment || "DP";
    $("fPrice").value = o.price || 0;
    $("fMaterial").value = o.material || "";
    $("fDeadline").value = o.deadline || "";
    $("fStage").value = o.stage;
  } else {
    $("modalTitle").textContent = "Tambah Pesanan";
    $("editId").value = "";
    $("fStage").value = 0;
  }
  $("modalOverlay").classList.add("open");
}
function closeModal(){ $("modalOverlay").classList.remove("open"); }

function saveOrder(e){
  e.preventDefault();
  const id = $("editId").value;
  const data = {
    customer: $("fCustomer").value.trim(),
    type: $("fType").value,
    qty: Number($("fQty").value),
    payment: $("fPayment").value,
    price: Number($("fPrice").value) || 0,
    material: $("fMaterial").value.trim(),
    deadline: $("fDeadline").value,
    stage: Number($("fStage").value)
  };
  if(!data.customer){ alert("Nama pemesan wajib diisi."); return; }
  if(!data.material){ alert("Bahan yang dipakai wajib diisi."); return; }
  if(id){
    Object.assign(orders.find(x=>x.id===id), data);
  } else {
    data.id = nextId();
    data.created = new Date().toISOString().slice(0,10);
    orders.push(data);
  }
  persist();
  closeModal();
  render();
}

function nextId(){
  const max = orders.reduce((m,o)=>{
    const n = parseInt(String(o.id).replace(/\D/g,""),10) || 0;
    return n > m ? n : m;
  }, 0);
  return "ORD-" + String(max+1).padStart(3,"0");
}

/* ===== Ubah jenis pembayaran ===== */
function changePayment(id){
  const o = orders.find(x=>x.id===id);
  if(!o) return;
  const input = prompt(
    `Ubah Jenis Pembayaran untuk ${o.customer}\nSaat ini: ${payStatus(o)}\n\nPilih salah satu: DP / Lunas / Transfer / Tunai`,
    payStatus(o)
  );
  if(input === null) return;
  const match = ["DP","Lunas","Transfer","Tunai"].find(a => a.toLowerCase() === input.trim().toLowerCase());
  if(!match){ alert("Jenis pembayaran tidak valid. Gunakan: DP, Lunas, Transfer, atau Tunai."); return; }
  o.payment = match;
  persist();
  render();
}

/* ===== Hapus ===== */
function deleteOrder(id){
  const o = orders.find(x=>x.id===id);
  if(!o) return;
  if(!confirm(`Hapus pesanan ${o.id} milik ${o.customer}?`)) return;
  orders = orders.filter(x=>x.id!==id);
  persist();
  render();
}

/* ===== Shortcut ===== */
document.addEventListener("keydown", e => { if(e.key === "Escape") closeModal(); });

init();
</script>
</body>
</html>
