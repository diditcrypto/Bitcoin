<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="DiditStore - Platform jual beli cryptocurrency." />
  <title>DiditStore — Crypto Marketplace</title>

  <style>
    :root {
      --bg:#070b14;
      --panel:#0d1422;
      --panel2:#111a2b;
      --text:#f5f7fb;
      --muted:#8d99ad;
      --line:#1c2940;
      --primary:#7c5cff;
      --primary2:#00d4ff;
      --green:#20d67a;
      --red:#ff5d6c;
      --shadow:0 20px 60px rgba(0,0,0,.35);
    }

    * {
      box-sizing:border-box;
      margin:0;
      padding:0;
    }

    html {
      scroll-behavior:smooth;
    }

    body {
      font-family:Inter,system-ui,-apple-system,"Segoe UI",sans-serif;
      background:
        radial-gradient(circle at 15% 10%,rgba(124,92,255,.18),transparent 28%),
        radial-gradient(circle at 85% 15%,rgba(0,212,255,.10),transparent 25%),
        var(--bg);
      color:var(--text);
      min-height:100vh;
    }

    a {
      color:inherit;
      text-decoration:none;
    }

    button,input,select {
      font:inherit;
    }

    .container {
      width:min(1160px,92%);
      margin:auto;
    }

    header {
      position:sticky;
      top:0;
      z-index:20;
      background:rgba(7,11,20,.78);
      backdrop-filter:blur(18px);
      border-bottom:1px solid rgba(255,255,255,.06);
    }

    .nav {
      height:72px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:24px;
    }

    .logo {
      font-size:23px;
      font-weight:900;
      display:flex;
      align-items:center;
      gap:10px;
    }

    .logo-mark {
      width:34px;
      height:34px;
      border-radius:11px;
      display:grid;
      place-items:center;
      background:linear-gradient(135deg,var(--primary),var(--primary2));
      box-shadow:0 8px 25px rgba(124,92,255,.35);
      animation:pulseGlow 2.6s ease-in-out infinite;
    }

    nav {
      display:flex;
      gap:22px;
      color:var(--muted);
      font-size:14px;
    }

    nav a:hover {
      color:white;
    }

    .nav-actions {
      display:flex;
      gap:10px;
    }

    .btn {
      border:1px solid var(--line);
      color:white;
      background:var(--panel);
      padding:10px 16px;
      border-radius:11px;
      cursor:pointer;
      font-weight:700;
    }

    .btn:hover {
      border-color:#344766;
    }

    .btn-primary {
      border:none;
      background:linear-gradient(135deg,var(--primary),#5d7cff);
      box-shadow:0 10px 25px rgba(124,92,255,.22);
    }

    .hero {
      padding:78px 0 55px;
      text-align:center;
      animation:fadeUp .8s ease both;
    }

    .badge {
      display:inline-flex;
      gap:8px;
      align-items:center;
      color:#c9c1ff;
      background:rgba(124,92,255,.10);
      border:1px solid rgba(124,92,255,.25);
      padding:7px 12px;
      border-radius:999px;
      font-size:13px;
      font-weight:700;
    }

    .dot {
      width:7px;
      height:7px;
      border-radius:50%;
      background:var(--green);
      box-shadow:0 0 12px var(--green);
      animation:pulseGlow 1.7s ease-in-out infinite;
    }

    h1 {
      font-size:clamp(42px,7vw,76px);
      line-height:.98;
      letter-spacing:-3px;
      margin:20px auto;
      max-width:900px;
    }

    .gradient-text {
      background:linear-gradient(90deg,#fff,#a99cff,#62eaff);
      -webkit-background-clip:text;
      color:transparent;
    }

    .hero p {
      color:var(--muted);
      max-width:650px;
      margin:auto;
      line-height:1.7;
      font-size:17px;
    }

    .hero-actions {
      margin-top:28px;
      display:flex;
      justify-content:center;
      gap:12px;
      flex-wrap:wrap;
    }

    .stats {
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:14px;
      margin-bottom:45px;
    }

    .stat {
      background:rgba(13,20,34,.75);
      border:1px solid var(--line);
      border-radius:17px;
      padding:21px;
      box-shadow:var(--shadow);
      animation:fadeUp .7s ease both;
    }

    .stat:nth-child(2) {
      animation-delay:.12s;
    }

    .stat:nth-child(3) {
      animation-delay:.24s;
    }

    .stat small {
      color:var(--muted);
    }

    .stat strong {
      display:block;
      font-size:24px;
      margin-top:7px;
    }

    .section-head {
      display:flex;
      justify-content:space-between;
      align-items:end;
      gap:15px;
      margin-bottom:18px;
    }

    .section-head h2 {
      font-size:28px;
    }

    .live {
      color:var(--green);
      font-size:13px;
      font-weight:800;
    }

    .market {
      background:rgba(13,20,34,.78);
      border:1px solid var(--line);
      border-radius:20px;
      overflow:hidden;
      box-shadow:var(--shadow);
    }

    .market-head,
    .coin {
      display:grid;
      grid-template-columns:2fr 1.2fr 1fr 1fr;
      gap:15px;
      align-items:center;
      padding:16px 20px;
    }

    .market-head {
      color:#647188;
      font-size:12px;
      text-transform:uppercase;
      border-bottom:1px solid var(--line);
    }

    .coin {
      border-bottom:1px solid rgba(28,41,64,.65);
      transition:transform .2s ease,background .2s ease;
    }

    .coin:hover {
      transform:translateX(5px);
      background:rgba(124,92,255,.06);
    }

    .coin-name {
      display:flex;
      align-items:center;
      gap:12px;
    }

    .coin-icon {
      width:38px;
      height:38px;
      border-radius:50%;
      display:grid;
      place-items:center;
      background:var(--panel2);
      font-weight:900;
      transition:transform .25s ease;
    }

    .coin:hover .coin-icon {
      transform:rotate(8deg) scale(1.12);
    }

    .coin-name strong {
      display:block;
    }

    .coin-name small {
      color:var(--muted);
    }

    .price {
      font-weight:800;
    }

    .change.up {
      color:var(--green);
      font-weight:800;
    }

    .volume {
      color:var(--muted);
      font-size:13px;
    }

    .info {
      display:grid;
      grid-template-columns:repeat(3,1fr);
      gap:15px;
      margin:45px 0 70px;
    }

    .card {
      border:1px solid var(--line);
      background:rgba(13,20,34,.7);
      border-radius:18px;
      padding:25px;
      transition:transform .25s ease,box-shadow .25s ease;
    }

    .card:hover {
      transform:translateY(-7px);
      box-shadow:0 18px 45px rgba(0,0,0,.32);
    }

    .card .emoji {
      font-size:25px;
    }

    .card h3 {
      margin:13px 0 8px;
    }

    .card p {
      color:var(--muted);
      line-height:1.6;
      font-size:14px;
    }

    /* P2P */

    .p2p-tabs {
      display:flex;
      gap:8px;
      margin-bottom:14px;
      background:rgba(13,20,34,.78);
      border:1px solid var(--line);
      padding:5px;
      border-radius:13px;
      width:max-content;
    }

    .p2p-tab {
      border:0;
      background:transparent;
      color:var(--muted);
      padding:10px 17px;
      border-radius:9px;
      cursor:pointer;
      font-weight:800;
    }

    .p2p-tab.active {
      background:linear-gradient(135deg,var(--primary),#5d7cff);
      color:white;
    }

    .p2p-filters {
      display:grid;
      grid-template-columns:160px 190px 1fr;
      gap:10px;
      margin-bottom:14px;
    }

    .p2p-filters select,
    .p2p-filters input {
      width:100%;
      background:#0d1422;
      color:white;
      border:1px solid var(--line);
      border-radius:10px;
      padding:11px 12px;
      outline:none;
    }

    .p2p-list {
      display:grid;
      gap:10px;
    }

    .p2p-row {
      display:grid;
      grid-template-columns:1.5fr 1fr 1fr 1fr auto;
      gap:15px;
      align-items:center;
      padding:18px 20px;
      background:rgba(13,20,34,.78);
      border:1px solid var(--line);
      border-radius:16px;
      transition:transform .2s ease,box-shadow .2s ease;
    }

    .p2p-row:hover {
      transform:translateY(-4px);
      box-shadow:0 14px 35px rgba(0,0,0,.25);
    }

    .merchant {
      display:flex;
      align-items:center;
      gap:11px;
    }

    .avatar {
      width:40px;
      height:40px;
      border-radius:50%;
      display:grid;
      place-items:center;
      background:linear-gradient(135deg,#273553,#182238);
      font-weight:900;
    }

    .merchant strong {
      display:block;
    }

    .merchant small,
    .p2p-label {
      color:var(--muted);
      font-size:12px;
    }

    .verified {
      color:var(--green);
      font-size:11px;
    }

    .p2p-action {
      border:0;
      border-radius:9px;
      padding:10px 15px;
      cursor:pointer;
      color:white;
      background:linear-gradient(135deg,var(--primary),#5d7cff);
      font-weight:800;
    }

    .p2p-action.sell {
      background:#142b24;
      border:1px solid #235e48;
      color:#62eaa8;
    }

    .escrow-card {
      display:flex;
      gap:14px;
      align-items:flex-start;
      margin-top:15px;
      padding:18px;
      border:1px solid rgba(98,234,255,.16);
      background:rgba(0,212,255,.045);
      border-radius:15px;
    }

    .escrow-icon {
      font-size:25px;
    }

    .escrow-card p {
      color:var(--muted);
      line-height:1.5;
      font-size:13px;
    }

    /* CARA BELI */

    .steps-grid {
      display:grid;
      grid-template-columns:repeat(4,1fr);
      gap:13px;
    }

    .step-card {
      padding:22px 18px;
      min-height:205px;
      background:rgba(13,20,34,.78);
      border:1px solid var(--line);
      border-radius:17px;
      box-shadow:var(--shadow);
      transition:transform .25s ease;
    }

    .step-card:hover {
      transform:translateY(-6px);
    }

    .step-number {
      width:36px;
      height:36px;
      border-radius:50%;
      display:grid;
      place-items:center;
      background:linear-gradient(135deg,var(--primary),var(--primary2));
      font-weight:900;
      margin-bottom:17px;
      animation:float 3s ease-in-out infinite;
    }

    .step-card h3 {
      font-size:16px;
      margin-bottom:8px;
    }

    .step-card p {
      color:var(--muted);
      font-size:13px;
      line-height:1.6;
    }

    .wa-link {
      display:inline-block;
      margin-top:13px;
      color:#62eaa8;
      font-size:13px;
      font-weight:800;
    }

    footer {
      border-top:1px solid var(--line);
      padding:28px 0;
      color:var(--muted);
      font-size:13px;
    }

    footer .container {
      display:flex;
      justify-content:space-between;
      gap:15px;
    }

    /* MODAL */

    .modal {
      position:fixed;
      inset:0;
      z-index:50;
      display:none;
      place-items:center;
      background:rgba(0,0,0,.7);
      backdrop-filter:blur(6px);
      padding:20px;
    }

    .modal.show {
      display:grid;
    }

    .modal-box {
      width:min(440px,100%);
      background:#0d1422;
      border:1px solid #293a57;
      border-radius:20px;
      padding:25px;
      box-shadow:var(--shadow);
    }

    .modal-top {
      display:flex;
      justify-content:space-between;
      align-items:center;
      margin-bottom:20px;
    }

    .close {
      background:none;
      border:0;
      color:#9aa7ba;
      font-size:25px;
      cursor:pointer;
    }

    .form-group {
      margin-bottom:15px;
    }

    .form-group label {
      display:block;
      color:var(--muted);
      font-size:13px;
      margin-bottom:7px;
    }

    .form-group input {
      width:100%;
      padding:12px;
      background:#09101d;
      color:white;
      border:1px solid var(--line);
      border-radius:10px;
      outline:none;
    }

    .notice {
      color:var(--muted);
      font-size:12px;
      line-height:1.5;
      margin-top:12px;
    }

    /* ANIMASI */

    @keyframes fadeUp {
      from {
        opacity:0;
        transform:translateY(22px);
      }
      to {
        opacity:1;
        transform:translateY(0);
      }
    }

    @keyframes pulseGlow {
      0%,100% {
        box-shadow:0 0 0 rgba(124,92,255,0);
      }
      50% {
        box-shadow:0 0 25px rgba(124,92,255,.45);
      }
    }

    @keyframes float {
      0%,100% {
        transform:translateY(0);
      }
      50% {
        transform:translateY(-6px);
      }
    }

    @media(max-width:760px) {
      nav {
        display:none;
      }

      .nav-actions .btn:first-child {
        display:none;
      }

      .stats,
      .info,
      .steps-grid {
        grid-template-columns:1fr;
      }

      .market-head {
        display:none;
      }

      .coin {
        grid-template-columns:1.6fr 1fr auto;
      }

      .coin .volume {
        display:none;
      }

      .p2p-filters {
        grid-template-columns:1fr;
      }

      .p2p-row {
        grid-template-columns:1fr 1fr;
      }

      .p2p-action {
        grid-column:1/-1;
      }

      footer .container {
        flex-direction:column;
      }

      h1 {
        letter-spacing:-2px;
      }
    }
  </style>
</head>

<body>

<header>
  <div class="container nav">

    <a class="logo" href="#">
      <span class="logo-mark">₿</span>
      DiditStore
    </a>

    <nav>
      <a href="#market">Market</a>
      <a href="#p2p">P2P</a>
      <a href="#cara-beli">Cara Beli</a>
    </nav>

    <div class="nav-actions">
      <button class="btn" onclick="openModal('login')">Masuk</button>
      <button class="btn btn-primary" onclick="openModal('signup')">Daftar</button>
    </div>

  </div>
</header>

<main>

<section class="hero container">

  <span class="badge">
    <span class="dot"></span>
    Market Crypto Live
  </span>

  <h1>
    Jual Beli Crypto Jadi
    <span class="gradient-text">Lebih Simpel.</span>
  </h1>

  <p>
    DiditStore menyediakan marketplace crypto dan P2P
    dengan proses mudah, cepat, dan aman.
  </p>

  <div class="hero-actions">
    <a class="btn btn-primary" href="#market">Lihat Market</a>

    <a
      class="btn"
      href="https://wa.me/6281229567050"
      target="_blank"
      rel="noopener"
    >
      WhatsApp
    </a>
  </div>

</section>

<section class="container stats">

  <div class="stat">
    <small>Total Market Cap</small>
    <strong id="marketCap">$1,000 USD</strong>
  </div>

  <div class="stat">
    <small>Volume 24 Jam</small>
    <strong id="volume">$68 USD</strong>
  </div>

  <div class="stat">
    <small>Update Terakhir</small>
    <strong id="updated">1 menit yang lalu</strong>
  </div>

</section>

<section id="market" class="container">

  <div class="section-head">

    <div>
      <div class="live">● LIVE MARKET</div>
      <h2>Harga Crypto</h2>
    </div>

    <small id="status" style="color:var(--muted)">
      Lihat harga live di CoinMarketCap
    </small>

  </div>

  <div class="market">

    <div class="market-head">
      <div>Aset</div>
      <div>Harga</div>
      <div>24 Jam</div>
      <div>Market</div>
    </div>

    <div id="coins"></div>

  </div>

  <div style="display:flex;justify-content:center;margin-top:14px;">

    <a
      class="btn btn-primary"
      href="https://coinmarketcap.com/"
      target="_blank"
      rel="noopener noreferrer"
    >
      Buka CoinMarketCap — Harga Live ↗
    </a>

  </div>

</section>

<!-- P2P -->

<section id="p2p" class="container" style="margin-top:55px;">

  <div class="section-head">

    <div>
      <div class="live" style="color:#62eaff;">
        ● P2P MARKET
      </div>

      <h2>Jual Beli Crypto P2P</h2>
    </div>

    <small style="color:var(--muted)">
      Marketplace
    </small>

  </div>

  <div class="p2p-tabs">

    <button
      class="p2p-tab active"
      onclick="switchP2P('buy',this)"
    >
      Beli Crypto
    </button>

    <button
      class="p2p-tab"
      onclick="switchP2P('sell',this)"
    >
      Jual Crypto
    </button>

  </div>

  <div class="p2p-filters">

    <select id="p2pCoin" onchange="renderP2P()">
      <option value="USDT">USDT</option>
      <option value="BTC">BTC</option>
      <option value="ETH">ETH</option>
      <option value="BNB">BNB</option>
    </select>

    <select id="p2pPayment" onchange="renderP2P()">
      <option value="all">Semua Pembayaran</option>
      <option value="bank">Transfer Bank</option>
      <option value="ewallet">E-Wallet</option>
    </select>

    <input
      id="p2pSearch"
      oninput="renderP2P()"
      placeholder="Cari merchant..."
    />

  </div>

  <div id="p2pList" class="p2p-list"></div>

  <div class="escrow-card">

    <div class="escrow-icon">🛡️</div>

    <div>

      <strong>Escrow DiditStore</strong>

      <p>
        Dalam transaksi P2P, aset dapat ditahan sementara
        sampai pembayaran terkonfirmasi.
      </p>

    </div>

  </div>

</section>

<!-- CARA BELI -->

<section
  id="cara-beli"
  class="container"
  style="margin-top:55px;"
>

  <div class="section-head">

    <div>

      <div
        class="live"
        style="color:#62eaff;"
      >
        ● CARA BELI CRYPTO
      </div>

      <h2>Cara Beli Crypto</h2>

    </div>

  </div>

  <div class="steps-grid">

    <div class="step-card">

      <div class="step-number">1</div>

      <h3>Konfirmasi ke WhatsApp</h3>

      <p>
        Hubungi WhatsApp DiditStore untuk memilih
        crypto dan jumlah yang ingin dibeli.
      </p>

      <a
        class="wa-link"
        href="https://wa.me/6281229567050"
        target="_blank"
        rel="noopener"
      >
        Chat WhatsApp →
      </a>

    </div>

    <div class="step-card">

      <div class="step-number">2</div>

      <h3>Transfer / QRIS</h3>

      <p>
        Lakukan pembayaran melalui metode pembayaran
        yang diberikan oleh DiditStore.
      </p>

    </div>

    <div class="step-card">

      <div class="step-number">3</div>

      <h3>Isi Alamat Wallet Crypto</h3>

      <p>
        Kirim alamat wallet crypto tujuan dengan
        jaringan yang sesuai.
      </p>

    </div>

    <div class="step-card">

      <div class="step-number">4</div>

      <h3>Selesai</h3>

      <p>
        Setelah pembayaran dan alamat wallet dikonfirmasi,
        crypto dikirim ke wallet Anda.
      </p>

    </div>

  </div>

</section>

<!-- FITUR -->

<section id="features" class="container info">

  <div class="card">

    <div class="emoji">⚡</div>

    <h3>Harga Live</h3>

    <p>
      Klik aset atau tombol market untuk melihat
      harga live langsung di CoinMarketCap.
    </p>

  </div>

  <div class="card">

    <div class="emoji">🔒</div>

    <h3>Simple & Modern</h3>

    <p>
      Desain dark-mode yang ringan, responsif,
      dan cocok untuk marketplace crypto.
    </p>

  </div>

  <div class="card">

    <div class="emoji">📊</div>

    <h3>Market Overview</h3>

    <p>
      Lihat beberapa aset crypto populer
      dan akses market CoinMarketCap.
    </p>

  </div>

</section>

</main>

<footer>

  <div class="container">

    <span>
      © 2026 DiditStore. Crypto Marketplace.
    </span>

    <span>
      WhatsApp:
      <a
        href="https://wa.me/6281229567050"
        target="_blank"
        rel="noopener"
        style="color:#62eaff;"
      >
        081229567050
      </a>
    </span>

    <span>
      Market:
      CoinMarketCap
    </span>

  </div>

</footer>

<!-- LOGIN / DAFTAR -->

<div
  class="modal"
  id="modal"
  onclick="if(event.target===this)closeModal()"
>

  <div class="modal-box">

    <div class="modal-top">

      <h2 id="modalTitle">Masuk</h2>

      <button
        class="close"
        onclick="closeModal()"
      >
        ×
      </button>

    </div>

    <form onsubmit="submitForm(event)">

      <div class="form-group">

        <label>Email</label>

        <input
          type="email"
          placeholder="nama@email.com"
          required
        />

      </div>

      <div class="form-group">

        <label>Password</label>

        <input
          type="password"
          placeholder="••••••••"
          required
        />

      </div>

      <button
        class="btn btn-primary"
        style="width:100%;"
        type="submit"
      >
        Lanjut
      </button>

    </form>

    <p class="notice">
      Keamanan akun dan transaksi diproses
      sesuai ketentuan DiditStore.
    </p>

  </div>

</div>

<script>

  /* =========================
     MARKET COINMARKETCAP
  ========================= */

  function loadMarket() {

    const links = {

      BTC:
        "https://coinmarketcap.com/currencies/bitcoin/",

      ETH:
        "https://coinmarketcap.com/currencies/ethereum/",

      USDT:
        "https://coinmarketcap.com/currencies/tether/",

      BNB:
        "https://coinmarketcap.com/currencies/bnb/",

      SOL:
        "https://coinmarketcap.com/currencies/solana/",

      XRP:
        "https://coinmarketcap.com/currencies/xrp/",

      DOGE:
        "https://coinmarketcap.com/currencies/dogecoin/"

    };

    const prices = {

      BTC:
        '<span id="btcLivePrice">Memuat...</span>',

      ETH:"$—",
      USDT:"$—",
      BNB:"$—",
      SOL:"$—",
      XRP:"$—",
      DOGE:"$—"

    };

    const coins = [

      ["Bitcoin","BTC"],
      ["Ethereum","ETH"],
      ["Tether","USDT"],
      ["BNB","BNB"],
      ["Solana","SOL"],
      ["XRP","XRP"],
      ["Dogecoin","DOGE"]

    ];

    document.getElementById("coins").innerHTML =
      coins.map(([name,symbol]) => `

        <a
          class="coin"
          href="${links[symbol]}"
          target="_blank"
          rel="noopener noreferrer"
          style="
            display:grid;
            color:inherit;
            text-decoration:none;
            cursor:pointer;
          "
        >

          <div class="coin-name">

            <div class="coin-icon">
              ${
                symbol === "BTC"
                ? "₿"
                : symbol.slice(0,2)
              }
            </div>

            <div>

              <strong>${name}</strong>

              <small>${symbol}</small>

            </div>

          </div>

          <div class="price">
            ${prices[symbol]}
          </div>

          <div class="change up">
            Live ↗
          </div>

          <div class="volume">
            CoinMarketCap ↗
          </div>

        </a>

      `).join("");

    document.getElementById("marketCap")
      .textContent = "$1,000 USD";

    document.getElementById("volume")
      .textContent = "$68 USD";

    document.getElementById("updated")
      .textContent = "1 menit yang lalu";

    document.getElementById("status")
      .textContent =
      "● Lihat harga live di CoinMarketCap";

    document.getElementById("status")
      .style.color = "var(--green)";

    loadBitcoinLivePrice();

  }


  /* =========================
     BITCOIN LIVE PRICE
  ========================= */

  async function loadBitcoinLivePrice() {

    const priceEl =
      document.getElementById("btcLivePrice");

    if (!priceEl) return;

    try {

      const response = await fetch(
        "https://api.coinmarketcap.com/data-api/v3/cryptocurrency/quotes/latest?slug=bitcoin&convertId=2781"
      );

      if (!response.ok)
        throw new Error("BTC unavailable");

      const result =
        await response.json();

      const quote =
        result?.data?.[0]?.quotes?.[0];

      const price =
        Number(quote?.price);

      if (!Number.isFinite(price))
        throw new Error("Invalid price");

      priceEl.textContent =
        new Intl.NumberFormat(
          "en-US",
          {
            style:"currency",
            currency:"USD",
            maximumFractionDigits:2
          }
        ).format(price);

      document.getElementById("updated")
        .textContent = "Baru saja";

    }

    catch(error) {

      console.error(error);

      priceEl.textContent =
        "Lihat di CMC ↗";

    }

  }


  /* =========================
     MODAL
  ========================= */

  function openModal(type) {

    document.getElementById("modalTitle")
      .textContent =
      type === "signup"
      ? "Buat Akun"
      : "Masuk";

    document.getElementById("modal")
      .classList.add("show");

  }


  function closeModal() {

    document.getElementById("modal")
      .classList.remove("show");

  }


  function submitForm(event) {

    event.preventDefault();

    alert("Formulir berhasil dikirim.");

    closeModal();

  }


  /* =========================
     P2P
  ========================= */

  let p2pMode = "buy";

  const p2pData = {

    buy: [

      {
        merchant:"AndiCrypto",
        rating:"99.8%",
        price:1.01,
        available:"12,500 USDT",
        limit:"Rp50K – Rp25JT",
        method:"Transfer Bank",
        type:"bank"
      },

      {
        merchant:"NusaTrade",
        rating:"99.5%",
        price:1.02,
        available:"8,200 USDT",
        limit:"Rp100K – Rp15JT",
        method:"E-Wallet",
        type:"ewallet"
      },

      {
        merchant:"CryptoJaya",
        rating:"98.9%",
        price:1.03,
        available:"5,750 USDT",
        limit:"Rp200K – Rp10JT",
        method:"Transfer Bank",
        type:"bank"
      }

    ],

    sell: [

      {
        merchant:"BudiCoin",
        rating:"99.7%",
        price:.99,
        available:"10,800 USDT",
        limit:"Rp100K – Rp20JT",
        method:"Transfer Bank",
        type:"bank"
      },

      {
        merchant:"JatengPay",
        rating:"99.4%",
        price:.98,
        available:"7,600 USDT",
        limit:"Rp50K – Rp12JT",
        method:"E-Wallet",
        type:"ewallet"
      }

    ]

  };


  function switchP2P(mode,button) {

    p2pMode = mode;

    document
      .querySelectorAll(".p2p-tab")
      .forEach(
        b => b.classList.remove("active")
      );

    button.classList.add("active");

    renderP2P();

  }


  function renderP2P() {

    const coin =
      document.getElementById("p2pCoin").value;

    const payment =
      document.getElementById("p2pPayment").value;

    const search =
      document.getElementById("p2pSearch")
        .value
        .toLowerCase()
        .trim();

    const rows =
      p2pData[p2pMode]

        .filter(
          x =>
            payment === "all" ||
            x.type === payment
        )

        .filter(
          x =>
            x.merchant
              .toLowerCase()
              .includes(search)
        );

    document.getElementById("p2pList")
      .innerHTML = rows.length

      ? rows.map(x => `

        <div class="p2p-row">

          <div class="merchant">

            <div class="avatar">
              ${x.merchant.slice(0,1)}
            </div>

            <div>

              <strong>
                ${x.merchant}
                <span class="verified">
                  ✓ Terverifikasi
                </span>
              </strong>

              <small>
                Rating ${x.rating}
              </small>

            </div>

          </div>

          <div>

            <span class="p2p-label">
              Harga
            </span>

            <br>

            <strong>
              $${x.price.toFixed(2)}
              / ${coin}
            </strong>

          </div>

          <div>

            <span class="p2p-label">
              Tersedia
            </span>

            <br>

            <strong>
              ${x.available.replace(
                "USDT",
                coin
              )}
            </strong>

          </div>

          <div>

            <span class="p2p-label">
              Limit
            </span>

            <br>

            ${x.limit}

            <br>

            <span class="p2p-label">
              ${x.method}
            </span>

          </div>

          <button
            class="p2p-action ${
              p2pMode === "sell"
              ? "sell"
              : ""
            }"
            onclick="
              p2pAction(
                '${p2pMode}',
                '${x.merchant}',
                '${coin}'
              )
            "
          >

            ${
              p2pMode === "buy"
              ? "Beli"
              : "Jual"
            }

          </button>

        </div>

      `).join("")

      : `

        <div
          style="
            padding:25px;
            text-align:center;
            color:var(--muted);
            background:rgba(13,20,34,.78);
            border:1px solid var(--line);
            border-radius:16px;
          "
        >
          Tidak ada merchant yang sesuai.
        </div>

      `;

  }


  function p2pAction(
    mode,
    merchant,
    coin
  ) {

    const action =
      mode === "buy"
      ? "membeli"
      : "menjual";

    alert(
      `Kamu memilih ${action} ${coin} dengan ${merchant}.`
    );

  }


  /* =========================
     ANIMASI SCROLL
  ========================= */

  const revealItems =
    document.querySelectorAll(
      ".market,.p2p-row,.step-card,.card"
    );

  revealItems.forEach(el => {

    el.style.opacity = "0";

    el.style.transform =
      "translateY(16px)";

    el.style.transition =
      "opacity .55s ease, transform .55s ease";

  });

  const revealObserver =
    new IntersectionObserver(
      entries => {

        entries.forEach(entry => {

          if (entry.isIntersecting) {

            entry.target.style.opacity = "1";

            entry.target.style.transform =
              "translateY(0)";

            revealObserver
              .unobserve(entry.target);

          }

        });

      },
      {
        threshold:.12
      }
    );

  revealItems.forEach(
    el => revealObserver.observe(el)
  );


  /* START */

  loadMarket();

  renderP2P();

  setInterval(
    loadBitcoinLivePrice,
    60000
  );

</script>

</body>
</html>
