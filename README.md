<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Kult — LGBTQ+ Film Rehberi</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0a;
    --surface: #141414;
    --surface2: #1f1f1f;
    --border: rgba(255,255,255,0.08);
    --text: #e5e5e5;
    --muted: #777;
    --accent: #e50914;
    --gay: #e91e8c;
    --lezbiyen: #7c4dff;
    --trans: #00bcd4;
    --biseksüel: #9c27b0;
    --queer: #ff9800;
    --belgesel: #4caf50;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    font-size: 14px;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── HERO SLIDER ── */
  .hero-slides {
    position: absolute;
    inset: 0;
    transition: opacity 0.6s ease;
  }

  .hero-slide {
    position: absolute;
    inset: 0;
    background-size: cover;
    background-position: center top;
    opacity: 0;
    transition: opacity 0.8s ease;
  }
  .hero-slide.active { opacity: 1; }

  .hero-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0,0,0,0.4);
    border: 1px solid rgba(255,255,255,0.2);
    color: white;
    width: 44px;
    height: 44px;
    border-radius: 50%;
    font-size: 24px;
    cursor: pointer;
    z-index: 5;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.2s;
    line-height: 1;
  }
  .hero-arrow:hover { background: rgba(0,0,0,0.7); }
  .hero-arrow-left { left: 24px; }
  .hero-arrow-right { right: 24px; }

  .hero-dots {
    position: absolute;
    bottom: 20px;
    right: 48px;
    display: flex;
    gap: 6px;
    z-index: 5;
  }

  .hero-dot {
    width: 8px;
    height: 2px;
    background: rgba(255,255,255,0.3);
    border-radius: 1px;
    cursor: pointer;
    transition: all 0.3s;
  }
  .hero-dot.active { width: 24px; background: white; }

  .hero-actions {
    display: flex;
    gap: 12px;
    margin-top: 24px;
  }

  .hero-btn-play {
    background: white;
    color: black;
    border: none;
    border-radius: 4px;
    padding: 10px 24px;
    font-family: 'Inter', sans-serif;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: background 0.15s;
  }
  .hero-btn-play:hover { background: rgba(255,255,255,0.85); }
  .hero-btn-play.hidden { display: none; }

  .hero-btn-info {
    background: rgba(109,109,110,0.7);
    color: white;
    border: none;
    border-radius: 4px;
    padding: 10px 24px;
    font-family: 'Inter', sans-serif;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s;
  }
  .hero-btn-info:hover { background: rgba(109,109,110,0.5); }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 48px;
    height: 64px;
    background: linear-gradient(to bottom, rgba(0,0,0,0.9), transparent);
    transition: background 0.3s;
  }
  nav.scrolled { background: rgba(10,10,10,0.98); }

  .logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 3px;
    color: var(--accent);
    text-decoration: none;
  }

  .nav-right {
    display: flex;
    align-items: center;
    gap: 20px;
  }

  .search-btn {
    background: none;
    border: none;
    color: var(--text);
    cursor: pointer;
    font-size: 18px;
    padding: 8px;
    display: flex;
    align-items: center;
    opacity: 0.8;
    transition: opacity 0.2s;
  }
  .search-btn:hover { opacity: 1; }

  /* ── HERO ── */
  .hero {
    height: 70vh;
    min-height: 400px;
    position: relative;
    display: flex;
    align-items: flex-end;
    padding: 0 48px 60px;
    background: linear-gradient(135deg, #0d0d2b 0%, #1a0a1a 50%, #0d1a0d 100%);
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse at 20% 50%, rgba(233,30,140,0.12) 0%, transparent 60%),
      radial-gradient(ellipse at 80% 30%, rgba(124,77,255,0.1) 0%, transparent 60%),
      radial-gradient(ellipse at 60% 80%, rgba(0,188,212,0.08) 0%, transparent 50%);
  }

  .hero-gradient {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 60%;
    background: linear-gradient(to top, var(--bg), transparent);
  }

  .hero-content {
    position: relative;
    z-index: 1;
    max-width: 600px;
  }

  .hero-tag {
    display: inline-block;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
  }

  .hero-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(48px, 8vw, 80px);
    line-height: 0.95;
    letter-spacing: 2px;
    color: white;
    margin-bottom: 16px;
  }

  .hero-desc {
    font-size: 15px;
    line-height: 1.6;
    color: rgba(255,255,255,0.6);
    max-width: 440px;
  }

  /* ── FILTERS ── */
  .filters-wrap {
    position: sticky;
    top: 64px;
    z-index: 90;
    background: rgba(10,10,10,0.95);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid var(--border);
    padding: 0 48px;
  }

  .filters {
    display: flex;
    align-items: center;
    gap: 4px;
    height: 52px;
    overflow-x: auto;
    scrollbar-width: none;
  }
  .filters::-webkit-scrollbar { display: none; }

  .filter-btn {
    flex-shrink: 0;
    background: none;
    border: none;
    color: var(--muted);
    font-family: 'Inter', sans-serif;
    font-size: 13px;
    font-weight: 500;
    padding: 6px 16px;
    border-radius: 4px;
    cursor: pointer;
    transition: all 0.15s;
    white-space: nowrap;
  }
  .filter-btn:hover { color: var(--text); background: var(--surface2); }
  .filter-btn.active { color: white; background: var(--surface2); }
  .filter-btn.active[data-cat="Gay"] { color: var(--gay); }
  .filter-btn.active[data-cat="Lezbiyen"] { color: var(--lezbiyen); }
  .filter-btn.active[data-cat="Trans"] { color: var(--trans); }
  .filter-btn.active[data-cat="Biseksüel"] { color: var(--biseksüel); }
  .filter-btn.active[data-cat="Queer"] { color: var(--queer); }
  .filter-btn.active[data-cat="Belgesel"] { color: var(--belgesel); }

  /* ── GRID ── */
  .grid-wrap { padding: 32px 48px 80px; }

  .film-count {
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 20px;
    letter-spacing: 1px;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 8px;
  }

  .card {
    position: relative;
    aspect-ratio: 2/3;
    border-radius: 4px;
    overflow: hidden;
    cursor: pointer;
    background: var(--surface);
    transition: transform 0.2s, z-index 0s;
  }
  .card:hover {
    transform: scale(1.04);
    z-index: 2;
  }

  .card-poster {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .card-bg {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 15px;
    letter-spacing: 1px;
    text-align: center;
    padding: 12px;
    color: rgba(255,255,255,0.7);
    line-height: 1.3;
  }

  .card-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, transparent 50%);
    opacity: 0;
    transition: opacity 0.2s;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 12px;
  }
  .card:hover .card-overlay { opacity: 1; }

  .card-badge {
    position: absolute;
    top: 8px;
    left: 8px;
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 3px 7px;
    border-radius: 2px;
    color: white;
  }

  .card-title {
    font-size: 12px;
    font-weight: 600;
    color: white;
    line-height: 1.3;
    margin-bottom: 2px;
  }

  .card-year {
    font-size: 11px;
    color: rgba(255,255,255,0.5);
  }

  .card-play {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 44px;
    height: 44px;
    background: rgba(255,255,255,0.9);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.2s;
  }
  .card:hover .card-play { opacity: 1; }
  .card-play svg { width: 16px; height: 16px; fill: #000; margin-left: 2px; }

  /* ── SEARCH OVERLAY ── */
  .search-overlay {
    position: fixed;
    inset: 0;
    z-index: 200;
    background: rgba(0,0,0,0.95);
    display: none;
    flex-direction: column;
    align-items: center;
    padding-top: 120px;
  }
  .search-overlay.open { display: flex; }

  .search-close {
    position: absolute;
    top: 20px;
    right: 24px;
    background: none;
    border: none;
    color: var(--muted);
    font-size: 28px;
    cursor: pointer;
    line-height: 1;
  }

  .search-input {
    width: 100%;
    max-width: 560px;
    background: none;
    border: none;
    border-bottom: 2px solid rgba(255,255,255,0.2);
    color: white;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 36px;
    letter-spacing: 2px;
    padding: 12px 0;
    outline: none;
    text-align: center;
  }
  .search-input::placeholder { color: rgba(255,255,255,0.2); }
  .search-input:focus { border-color: rgba(255,255,255,0.5); }

  .search-results {
    width: 100%;
    max-width: 560px;
    margin-top: 24px;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 8px;
    max-height: 60vh;
    overflow-y: auto;
  }

  /* ── VIDEO MODAL ── */
  .video-modal {
    position: fixed;
    inset: 0;
    z-index: 300;
    background: #000;
    display: none;
    flex-direction: column;
  }
  .video-modal.open { display: flex; }

  .video-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 24px;
    background: rgba(0,0,0,0.8);
    position: absolute;
    top: 0; left: 0; right: 0;
    z-index: 10;
  }

  .video-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 2px;
  }

  .video-close {
    background: none;
    border: none;
    color: white;
    font-size: 28px;
    cursor: pointer;
    line-height: 1;
    opacity: 0.7;
    transition: opacity 0.2s;
  }
  .video-close:hover { opacity: 1; }

  .video-frame {
    width: 100%;
    height: 100%;
    border: none;
  }

  .video-info {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    padding: 24px;
    background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
    display: flex;
    align-items: center;
    gap: 16px;
  }

  /* ── FILM DETAIL PANEL ── */
  .detail-panel {
    position: fixed;
    inset: 0;
    z-index: 200;
    display: none;
    align-items: center;
    justify-content: center;
    background: rgba(0,0,0,0.8);
    backdrop-filter: blur(4px);
  }
  .detail-panel.open { display: flex; }

  .detail-box {
    background: var(--surface);
    border-radius: 8px;
    width: 90%;
    max-width: 480px;
    overflow: hidden;
    position: relative;
  }

  .detail-poster-area {
    height: 200px;
    position: relative;
    overflow: hidden;
  }

  .detail-poster-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .detail-poster-grad {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, var(--surface) 0%, transparent 60%);
  }

  .detail-body {
    padding: 20px 24px 24px;
  }

  .detail-badge {
    display: inline-block;
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 3px 8px;
    border-radius: 2px;
    color: white;
    margin-bottom: 10px;
  }

  .detail-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 1px;
    color: white;
    line-height: 1;
    margin-bottom: 8px;
  }

  .detail-meta {
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 12px;
  }

  .detail-desc {
    font-size: 13px;
    line-height: 1.6;
    color: rgba(255,255,255,0.6);
    margin-bottom: 20px;
  }

  .detail-actions {
    display: flex;
    gap: 10px;
  }

  .btn-play {
    flex: 1;
    background: white;
    color: black;
    border: none;
    border-radius: 4px;
    padding: 10px;
    font-family: 'Inter', sans-serif;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    transition: background 0.15s;
  }
  .btn-play:hover { background: rgba(255,255,255,0.85); }
  .btn-play:disabled { opacity: 0.35; cursor: not-allowed; }

  .btn-close-detail {
    position: absolute;
    top: 12px;
    right: 12px;
    background: rgba(0,0,0,0.6);
    border: none;
    color: white;
    width: 32px;
    height: 32px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 10;
  }

  .no-results {
    grid-column: 1/-1;
    text-align: center;
    color: var(--muted);
    padding: 60px 0;
    font-size: 13px;
  }

  @media (max-width: 600px) {
    nav, .grid-wrap, .filters-wrap { padding-left: 16px; padding-right: 16px; }
    .hero { padding: 0 16px 40px; }
    .grid { grid-template-columns: repeat(auto-fill, minmax(120px, 1fr)); }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav id="nav">
  <a href="#" class="logo">KULT</a>
  <div class="nav-right">
    <button class="search-btn" onclick="openSearch()" title="Ara">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/>
      </svg>
    </button>
  </div>
</nav>

<!-- HERO SLIDER -->
<div class="hero" id="hero">
  <div class="hero-slides" id="heroSlides"></div>
  <div class="hero-gradient"></div>
  <div class="hero-content" id="heroContent">
    <span class="hero-tag" id="heroTag"></span>
    <h1 class="hero-title" id="heroTitle"></h1>
    <p class="hero-desc" id="heroDesc"></p>
    <div class="hero-actions">
      <button class="hero-btn-play" id="heroBtnPlay" onclick="playHeroFilm()">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>
        İzle
      </button>
      <button class="hero-btn-info" onclick="infoHeroFilm()">Detaylar</button>
    </div>
  </div>
  <div class="hero-dots" id="heroDots"></div>
  <button class="hero-arrow hero-arrow-left" onclick="slideHero(-1)">&#8249;</button>
  <button class="hero-arrow hero-arrow-right" onclick="slideHero(1)">&#8250;</button>
</div>

<!-- FILTERS -->
<div class="filters-wrap">
  <div class="filters">
    <button class="filter-btn active" data-cat="Tümü" onclick="setFilter(this)">Tümü</button>
    <button class="filter-btn" data-cat="Gay" onclick="setFilter(this)">Gay</button>
    <button class="filter-btn" data-cat="Lezbiyen" onclick="setFilter(this)">Lezbiyen</button>
    <button class="filter-btn" data-cat="Trans" onclick="setFilter(this)">Trans</button>
    <button class="filter-btn" data-cat="Biseksüel" onclick="setFilter(this)">Biseksüel</button>
    <button class="filter-btn" data-cat="Queer" onclick="setFilter(this)">Queer</button>
    <button class="filter-btn" data-cat="Belgesel" onclick="setFilter(this)">Belgesel</button>
    <button class="filter-btn" data-cat="Türk Yapımı" onclick="setFilter(this)">Türk Yapımı</button>
  </div>
</div>

<!-- GRID -->
<div class="grid-wrap">
  <div class="film-count" id="filmCount"></div>
  <div class="grid" id="grid"></div>
</div>

<!-- SEARCH -->
<div class="search-overlay" id="searchOverlay">
  <button class="search-close" onclick="closeSearch()">×</button>
  <input class="search-input" id="searchInput" type="text" placeholder="FİLM ARA..." oninput="doSearch(this.value)" autocomplete="off">
  <div class="search-results" id="searchResults"></div>
</div>

<!-- DETAIL PANEL -->
<div class="detail-panel" id="detailPanel" onclick="closeDetailOutside(event)">
  <div class="detail-box" id="detailBox">
    <button class="btn-close-detail" onclick="closeDetail()">×</button>
    <div class="detail-poster-area" id="detailPosterArea">
      <img class="detail-poster-img" id="detailPosterImg" src="" alt="" style="display:none">
      <div class="detail-poster-grad"></div>
    </div>
    <div class="detail-body">
      <div class="detail-badge" id="detailBadge"></div>
      <div class="detail-title" id="detailTitle"></div>
      <div class="detail-meta" id="detailMeta"></div>
      <div class="detail-desc" id="detailDesc"></div>
      <div class="detail-actions">
        <button class="btn-play" id="btnPlay" onclick="playCurrentVideo()">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>
          İzle
        </button>
      </div>
    </div>
  </div>
</div>

<!-- VIDEO MODAL -->
<div class="video-modal" id="videoModal">
  <div class="video-header">
    <span class="video-title" id="videoModalTitle"></span>
    <button class="video-close" onclick="closeVideo()">×</button>
  </div>
  <iframe class="video-frame" id="videoFrame" src="" allowfullscreen allow="autoplay; encrypted-media"></iframe>
</div>

<script>
  // ── FILM LİSTESİ ──
  const FILMS = [
    { id: 376867, title: "Moonlight",                       badge: "Gay",       year: 2016, country: "ABD",      desc: "Florida'da buyuyen genc bir Siyah erkegin kimligini kesfetme surecini anlatan Oscar odullu film.", qi: 5, videoUrl: "" },
    { id: 142,    title: "Brokeback Mountain",               badge: "Gay",       year: 2005, country: "ABD",      desc: "Iki rodeo kovboyunun yillar icinde gelisen yasak askini anlatan queer sinema klasigi.", qi: 5, videoUrl: "" },
    { id: 31225,  title: "Paris Is Burning",                 badge: "Belgesel",  year: 1990, country: "ABD",      desc: "New York Harlem drag ball sahnesini anlatan efsanevi belgesel.", qi: 5, videoUrl: "" },
    { id: 258480, title: "Carol",                            badge: "Lezbiyen",  year: 2015, country: "ABD",      desc: "1950 New Yorkunda iki kadin arasinda gelisen yasak aski anlatan sinematik basyapit.", qi: 5, videoUrl: "" },
    { id: 11159,  title: "My Own Private Idaho",             badge: "Gay",       year: 1991, country: "ABD",      desc: "River Phoenix ve Keanu Reeves li queer yolculuk filmi.", qi: 5, videoUrl: "" },
    { id: 10539,  title: "Milk",                             badge: "Gay",       year: 2008, country: "ABD",      desc: "San Francisco ilk escinsel belediye meclis uyesi Harvey Milk in yasami.", qi: 5, videoUrl: "" },
    { id: 10267,  title: "The Rocky Horror Picture Show",    badge: "Queer",     year: 1975, country: "ABD",      desc: "Kult kulturu yaratan efsanevi queer muzikali.", qi: 5, videoUrl: "" },
    { id: 226,    title: "Boys Don't Cry",                   badge: "Trans",     year: 1999, country: "ABD",      desc: "Brandon Teena adli trans erkegin gercek hikayesini anlatan Oscar odullu drama.", qi: 5, videoUrl: "" },
    { id: 522,    title: "Hedwig and the Angry Inch",        badge: "Trans",     year: 2001, country: "ABD",      desc: "Dogu Almanyadan Amerikaya gelen trans bir rock muzisyenin muzikali.", qi: 5, videoUrl: "" },
    { id: 322588, title: "Tangerine",                        badge: "Trans",     year: 2015, country: "ABD",      desc: "Los Angeles trans kadinlarinin bir Noel Gecesini anlatan iPhone ile cekilmis film.", qi: 5, videoUrl: "" },
    { id: 6977,   title: "Philadelphia",                     badge: "Gay",       year: 1993, country: "ABD",      desc: "AIDS hastasi bir avukatin issizlige karsi verdigi hukuki mucadeleyi anlatan drama.", qi: 4, videoUrl: "" },
    { id: 39254,  title: "The Kids Are All Right",           badge: "Lezbiyen",  year: 2010, country: "ABD",      desc: "Iki lezbiyen annenin cocuklari biyolojik babalarini buldugunda yasananlar.", qi: 4, videoUrl: "" },
    { id: 10862,  title: "But I'm a Cheerleader",            badge: "Lezbiyen",  year: 1999, country: "ABD",      desc: "Escinsel duzeltme kampina gonderilen bir liseli kizin komik hikayesi.", qi: 5, videoUrl: "" },
    { id: 8985,   title: "Shortbus",                         badge: "Queer",     year: 2006, country: "ABD",      desc: "New York queer sahnesini anlatan cesur John Cameron Mitchell filmi.", qi: 5, videoUrl: "" },
    { id: 820965, title: "Fire Island",                      badge: "Gay",       year: 2022, country: "ABD",      desc: "Asya Amerikali gay arkadaslarin yaz tatilini anlatan romantik komedi.", qi: 4, videoUrl: "" },
    { id: 301359, title: "The Normal Heart",                 badge: "Gay",       year: 2014, country: "ABD",      desc: "AIDS krizinin baslarinda New Yorkta bir aktivist grubun mucadelesini anlatan drama.", qi: 5, videoUrl: "" },
    { id: 43199,  title: "Desert Hearts",                    badge: "Lezbiyen",  year: 1985, country: "ABD",      desc: "1950 lerde Nevada colunde iki kadinin yasadigi ask hikayesi.", qi: 5, videoUrl: "" },
    { id: 11370,  title: "Bound",                            badge: "Lezbiyen",  year: 1996, country: "ABD",      desc: "Wachowski kardeslerden lezbiyen neo-noir gerilim klasigi.", qi: 5, videoUrl: "" },
    { id: 72976,  title: "Pariah",                           badge: "Lezbiyen",  year: 2011, country: "ABD",      desc: "Brooklynde yasayan genc Siyah bir lezbiyenin kimligini kesfetme sureci.", qi: 5, videoUrl: "" },
    { id: 15592,  title: "Dallas Buyers Club",               badge: "Queer",     year: 2013, country: "ABD",      desc: "AIDS hastasi bir Texasli kovboyun ilac sistemine karsi mucadelesi.", qi: 4, videoUrl: "" },
    { id: 13061,  title: "Velvet Goldmine",                  badge: "Biseksüel", year: 1998, country: "ABD",      desc: "1970 lerin glam rock dunyasinda biseksuel bir rock yildizinin hikayesi.", qi: 5, videoUrl: "" },
    { id: 4348,   title: "Transamerica",                     badge: "Trans",     year: 2005, country: "ABD",      desc: "Ameliyat oncesinde kaybolan oglunu bulmak zorunda kalan trans bir kadinin yolculugu.", qi: 5, videoUrl: "" },
    { id: 458131, title: "Bros",                             badge: "Gay",       year: 2022, country: "ABD",      desc: "Hollywood un ilk buyuk studiyo gay romantik komedisi.", qi: 4, videoUrl: "" },
    { id: 479529, title: "Love Simon",                       badge: "Gay",       year: 2018, country: "ABD",      desc: "Lise ogrencisi Simon in kimligini aciklama surecini anlatan sicak film.", qi: 4, videoUrl: "" },
    { id: 9593,   title: "The Birdcage",                     badge: "Gay",       year: 1996, country: "ABD",      desc: "Robin Williams ve Nathan Lane li efsanevi gay komedi.", qi: 4, videoUrl: "" },
    { id: 9928,   title: "Far from Heaven",                  badge: "Gay",       year: 2002, country: "ABD",      desc: "1950 ler Amerikanin arkasinidaki gercekleri gosteren Todd Haynes melodrami.", qi: 4, videoUrl: "" },
    { id: 829799, title: "Bottoms",                          badge: "Lezbiyen",  year: 2023, country: "ABD",      desc: "Iki lezbiyen liseli kizin kaos dolu dovus kulubu kurmaya calistigi komedi.", qi: 4, videoUrl: "" },
    { id: 774825, title: "Tar",                              badge: "Lezbiyen",  year: 2022, country: "ABD",      desc: "Cate Blanchett in muhtesem performansiyla queer bir orkestra sefjinin dususunu anlatan drama.", qi: 4, videoUrl: "" },
    { id: 30547,  title: "Mysterious Skin",                  badge: "Gay",       year: 2004, country: "ABD",      desc: "Gregg Araki nin genclikte yasanan travmawi anlatan karanlik ve gucu etkili filmi.", qi: 5, videoUrl: "" },
    { id: 22881,  title: "Saving Face",                      badge: "Lezbiyen",  year: 2004, country: "ABD",      desc: "Cin Amerikali bir lezbiyen cerrahin ailesiyle yuzyuze geldigi film.", qi: 4, videoUrl: "" },
    // Fransa
    { id: 426426, title: "Portrait of a Lady on Fire",       badge: "Lezbiyen",  year: 2019, country: "Fransa",   desc: "18. yuzyil Bretanyasinda ressam ile modeli arasindaki sessiz ama yogun ask.", qi: 5, videoUrl: "" },
    { id: 38357,  title: "Blue Is the Warmest Colour",       badge: "Lezbiyen",  year: 2013, country: "Fransa",   desc: "Cannes Altin Palmiyesi kazanan iki genc kadin arasindaki tutkulu ask filmi.", qi: 5, videoUrl: "" },
    { id: 252171, title: "120 BPM",                          badge: "Gay",       year: 2017, country: "Fransa",   desc: "Paris Act Up grubunun AIDS krizindeki aktivizmini anlatan gucu etkili film.", qi: 5, videoUrl: "" },
    { id: 196867, title: "Stranger by the Lake",             badge: "Gay",       year: 2013, country: "Fransa",   desc: "Bir gol kiyisinda gecen gerilimli ve erotik queer ask hikayesi.", qi: 5, videoUrl: "" },
    { id: 12453,  title: "Beau Travail",                     badge: "Gay",       year: 1999, country: "Fransa",   desc: "Claire Denis in Fransiz Yabanci Lejyonunda gecen homoerotik sefi eseri.", qi: 5, videoUrl: "" },
    { id: 33421,  title: "Water Lilies",                     badge: "Lezbiyen",  year: 2007, country: "Fransa",   desc: "Celine Sciamma nin ilk filmi, uc genc kizin yaz askini anlatan hassas drama.", qi: 4, videoUrl: "" },
    { id: 50456,  title: "Tomboy",                           badge: "Trans",     year: 2011, country: "Fransa",   desc: "Yeni bir mahalleye tasinan genc bir cocugun cinsiyet kimligini kesfetmesi.", qi: 5, videoUrl: "" },
    { id: 570984, title: "Benedetta",                        badge: "Lezbiyen",  year: 2021, country: "Fransa",   desc: "17. yuzyilda yasayan bir rahibenin yasak askini anlatan Paul Verhoeven filmi.", qi: 4, videoUrl: "" },
    { id: 664767, title: "Summer of 85",                     badge: "Gay",       year: 2020, country: "Fransa",   desc: "Fransiz sahil kasabasinda iki genc erkek arasindaki yogun yaz askini anlatan film.", qi: 5, videoUrl: "" },
    { id: 379019, title: "Being 17",                         badge: "Gay",       year: 2016, country: "Fransa",   desc: "Iki genc erkegin dusmanligi askin donusumunu anlatan Andre Techine filmi.", qi: 4, videoUrl: "" },
    { id: 826732, title: "Passages",                         badge: "Biseksüel", year: 2023, country: "Fransa",   desc: "Paris te bir yonetmenin iki iliski arasinda sikisip kaldigi tutku dolu drama.", qi: 4, videoUrl: "" },
    // Ingiltere
    { id: 64686,  title: "Weekend",                          badge: "Gay",       year: 2011, country: "İngiltere",desc: "Bir hafta sonu boyunca iki yabancinin arasinda gelisen nazik ask hikayesi.", qi: 5, videoUrl: "" },
    { id: 430826, title: "God's Own Country",                badge: "Gay",       year: 2017, country: "İngiltere",desc: "Yorkshire cercevesinde bir genc ciftci ile Rumen mevsimlik iscinin askini anlatan film.", qi: 5, videoUrl: "" },
    { id: 15776,  title: "Maurice",                          badge: "Gay",       year: 1987, country: "İngiltere",desc: "E.M. Forster in Edwardian doneminde gecen queer ask romaninin uyarlamasi.", qi: 5, videoUrl: "" },
    { id: 11248,  title: "My Beautiful Laundrette",          badge: "Gay",       year: 1985, country: "İngiltere",desc: "Thatcher doneminde Londra da iki erkegin askini anlatan kulturel basyapit.", qi: 5, videoUrl: "" },
    { id: 6006,   title: "Orlando",                          badge: "Queer",     year: 1992, country: "İngiltere",desc: "Virginia Woolf romanindan uyarlanan, cinsiyet otesinde bir varligin 400 yillik hikayesi.", qi: 5, videoUrl: "" },
    { id: 260522, title: "Pride",                            badge: "Gay",       year: 2014, country: "İngiltere",desc: "LGBTQ aktivistlerin 1984 te Galler maden iscilerini destekleme hikayesi.", qi: 4, videoUrl: "" },
    { id: 625281, title: "Ammonite",                         badge: "Lezbiyen",  year: 2020, country: "İngiltere",desc: "Fosil bilimci Mary Anning ve genc bir kadinla olan yasak askini anlatan period drama.", qi: 4, videoUrl: "" },
    // Ispanya
    { id: 1049,   title: "All About My Mother",              badge: "Queer",     year: 1999, country: "İspanya",  desc: "Pedro Almodovar in queer karakterlerle dolu Oscar odullu sefi eseri.", qi: 5, videoUrl: "" },
    { id: 11216,  title: "Bad Education",                    badge: "Gay",       year: 2004, country: "İspanya",  desc: "Almodovar in film noir unsurlarini queer temayla birlestirdigi gerilim filmi.", qi: 5, videoUrl: "" },
    { id: 8883,   title: "Law of Desire",                    badge: "Gay",       year: 1987, country: "İspanya",  desc: "Almodovar in escinsel ask ucgenini anlatan tutkulu erken donem klasigi.", qi: 5, videoUrl: "" },
    { id: 179430, title: "Pain and Glory",                   badge: "Gay",       year: 2019, country: "İspanya",  desc: "Almodovar in otobiyografik queer filmi, Antonio Banderas ile.", qi: 4, videoUrl: "" },
    // Almanya
    { id: 716695, title: "Great Freedom",                    badge: "Gay",       year: 2021, country: "Almanya",  desc: "Escinselligin suc sayildigi Almanyada hapishane duvarlari arasinda gelisen ask.", qi: 5, videoUrl: "" },
    // Turkiye
    { id: 77483,  title: "Zenne",                            badge: "Türk Yapımı",year: 2011,country: "Türkiye",  desc: "Turkiye nin ilk acikca escinsel dansci Ahmet Yildizin hikayesinden esinlenen film.", qi: 5, videoUrl: "" },
    // Italya
    { id: 398978, title: "Call Me by Your Name",             badge: "Gay",       year: 2017, country: "İtalya",   desc: "1983 Italyasinda gecen Elio ve Oliver in buyuleyici yaz aski hikayesi.", qi: 4, videoUrl: "" },
    // Asya
    { id: 290098, title: "The Handmaiden",                   badge: "Lezbiyen",  year: 2016, country: "G.Kore",   desc: "Park Chan-wook un iki kadindan olusan karmasik ve erotik gerilim sefi eseri.", qi: 5, videoUrl: "" },
    { id: 11160,  title: "Happy Together",                   badge: "Gay",       year: 1997, country: "H.Kong",   desc: "Wong Kar-wai in Buenos Aires te iki Honkonglu erkek arasindaki yikici ask hikayesi.", qi: 5, videoUrl: "" },
    { id: 10329,  title: "Farewell My Concubine",            badge: "Gay",       year: 1993, country: "Cin",      desc: "Cin opera dunyasinda elli yila yayilan efsanevi queer ask hikayesi.", qi: 5, videoUrl: "" },
    { id: 254128, title: "The Way He Looks",                 badge: "Gay",       year: 2014, country: "Brezilya", desc: "Kor bir genc erkegin ask ve bagimsizligi kesfettigi Brezilya filmi.", qi: 4, videoUrl: "" },
    // Latin Amerika
    { id: 9529,   title: "Y Tu Mama Tambien",                badge: "Biseksüel", year: 2001, country: "Meksika",  desc: "Alfonso Cuaron in iki genc erkek ve bir kadinin yolculugunu anlatan filmi.", qi: 4, videoUrl: "" },
    { id: 376293, title: "A Fantastic Woman",                badge: "Trans",     year: 2017, country: "Sili",     desc: "Sevgilisinin olumunun ardindan ailesinin onculugune direnen trans bir kadinin hikayesi.", qi: 5, videoUrl: "" },
    // Kanada
    { id: 116492, title: "Laurence Anyways",                 badge: "Trans",     year: 2012, country: "Kanada",   desc: "Xavier Dolan in trans bir kadinin on yillik ask ve donusum hikayesini anlatan epik filmi.", qi: 5, videoUrl: "" },
    { id: 205596, title: "The Imitation Game",               badge: "Gay",       year: 2014, country: "İngiltere",desc: "Escinsel bilgisayar bilimcisi Alan Turing in II. Dunya Savasi sirasindaki hikayesi.", qi: 3, videoUrl: "" },
    // ✏️ YENİ FİLM:
    // { id: TMDB_ID, title: "Film Adi", badge: "Gay/Lezbiyen/Trans/Biseksüel/Queer/Belgesel/Türk Yapımı", year: 2020, country: "Ulke", desc: "Aciklama.", qi: 1-5, videoUrl: "" },
  ];

  const BADGE_COLORS = {
    "Gay":        "#e91e8c",
    "Lezbiyen":   "#7c4dff",
    "Trans":      "#00bcd4",
    "Biseksüel":  "#9c27b0",
    "Queer":      "#ff9800",
    "Belgesel":   "#4caf50",
    "Türk Yapımı":"#e91e8c",
  };

  const IMG_BASE = "https://image.tmdb.org/t/p/w300";
  const IMG_BIG  = "https://image.tmdb.org/t/p/w780";
  let TMDB_KEY   = localStorage.getItem("tmdb_key") || "";
  let posters    = {}; // id -> poster_path
  let currentFilter = "Tümü";
  let currentFilm = null;

  // ── BUILD CARDS ──
  function buildCards(films) {
    const grid = document.getElementById("grid");
    const count = document.getElementById("filmCount");
    grid.innerHTML = "";
    count.textContent = films.length + " film";

    films.forEach(film => {
      const card = document.createElement("div");
      card.className = "card";
      card.onclick = () => openDetail(film);

      const badgeColor = BADGE_COLORS[film.badge] || "#e91e8c";
      const poster = posters[film.id];
      const bgColor = {
        "Gay": "#3a0820", "Lezbiyen": "#1a0a3a", "Trans": "#0a2a2a",
        "Biseksüel": "#1a0a2a", "Queer": "#2a1500", "Belgesel": "#0a2a0a", "Türk Yapımı": "#3a0820"
      }[film.badge] || "#141414";

      card.innerHTML =
        '<div class="card-bg" style="background:' + bgColor + '">' +
          (poster
            ? '<img class="card-poster" src="' + IMG_BASE + poster + '" alt="' + film.title + '" loading="lazy">'
            : film.title) +
        '</div>' +
        '<div class="card-badge" style="background:' + badgeColor + '">' + film.badge + '</div>' +
        '<div class="card-play"><svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg></div>' +
        '<div class="card-overlay">' +
          '<div class="card-title">' + film.title + '</div>' +
          '<div class="card-year">' + film.year + ' · ' + film.country + '</div>' +
        '</div>';

      grid.appendChild(card);
    });
  }

  function getFiltered() {
    if (currentFilter === "Tümü") return FILMS;
    return FILMS.filter(f => f.badge === currentFilter);
  }

  function setFilter(btn) {
    document.querySelectorAll(".filter-btn").forEach(b => b.classList.remove("active"));
    btn.classList.add("active");
    currentFilter = btn.dataset.cat;
    buildCards(getFiltered());
  }

  // ── DETAIL ──
  function openDetail(film) {
    currentFilm = film;
    const badgeColor = BADGE_COLORS[film.badge] || "#e91e8c";
    const poster = posters[film.id];

    document.getElementById("detailBadge").textContent = film.badge;
    document.getElementById("detailBadge").style.background = badgeColor;
    document.getElementById("detailTitle").textContent = film.title;
    document.getElementById("detailMeta").textContent = film.year + " · " + film.country;
    document.getElementById("detailDesc").textContent = film.desc;

    const img = document.getElementById("detailPosterImg");
    const area = document.getElementById("detailPosterArea");
    if (poster) {
      img.src = IMG_BIG + poster;
      img.style.display = "block";
      area.style.background = "";
    } else {
      img.style.display = "none";
      area.style.background = "linear-gradient(135deg, #1a0a1a, #0a1a2a)";
    }

    const btn = document.getElementById("btnPlay");
    if (film.videoUrl) {
      btn.disabled = false;
      btn.textContent = "";
      btn.innerHTML = '<svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8 5v14l11-7z"/></svg> İzle';
    } else {
      btn.disabled = true;
      btn.textContent = "Yakında";
    }

    document.getElementById("detailPanel").classList.add("open");
    document.body.style.overflow = "hidden";
  }

  function closeDetail() {
    document.getElementById("detailPanel").classList.remove("open");
    document.body.style.overflow = "";
    currentFilm = null;
  }

  function closeDetailOutside(e) {
    if (e.target === document.getElementById("detailPanel")) closeDetail();
  }

  // ── VIDEO ──
  function playCurrentVideo() {
    if (!currentFilm || !currentFilm.videoUrl) return;
    document.getElementById("videoModalTitle").textContent = currentFilm.title;
    document.getElementById("videoFrame").src = currentFilm.videoUrl;
    document.getElementById("videoModal").classList.add("open");
    closeDetail();
  }

  function closeVideo() {
    document.getElementById("videoModal").classList.remove("open");
    document.getElementById("videoFrame").src = "";
    document.body.style.overflow = "";
  }

  // ── SEARCH ──
  function openSearch() {
    document.getElementById("searchOverlay").classList.add("open");
    document.getElementById("searchInput").focus();
    document.getElementById("searchInput").value = "";
    document.getElementById("searchResults").innerHTML = "";
    document.body.style.overflow = "hidden";
  }

  function closeSearch() {
    document.getElementById("searchOverlay").classList.remove("open");
    document.body.style.overflow = "";
  }

  function doSearch(q) {
    const results = document.getElementById("searchResults");
    if (!q.trim()) { results.innerHTML = ""; return; }
    const found = FILMS.filter(f =>
      f.title.toLowerCase().includes(q.toLowerCase()) ||
      f.badge.toLowerCase().includes(q.toLowerCase()) ||
      f.country.toLowerCase().includes(q.toLowerCase())
    );
    if (!found.length) {
      results.innerHTML = '<div class="no-results">Sonuç bulunamadı</div>';
      return;
    }
    results.innerHTML = "";
    found.forEach(film => {
      const card = document.createElement("div");
      card.className = "card";
      card.style.aspectRatio = "2/3";
      card.onclick = () => { closeSearch(); openDetail(film); };
      const poster = posters[film.id];
      const badgeColor = BADGE_COLORS[film.badge] || "#e91e8c";
      const bgColor = {"Gay":"#3a0820","Lezbiyen":"#1a0a3a","Trans":"#0a2a2a","Biseksüel":"#1a0a2a","Queer":"#2a1500","Belgesel":"#0a2a0a","Türk Yapımı":"#3a0820"}[film.badge]||"#141414";
      card.innerHTML =
        '<div class="card-bg" style="background:' + bgColor + '">' +
          (poster ? '<img class="card-poster" src="' + IMG_BASE + poster + '" alt="' + film.title + '">' : film.title) +
        '</div>' +
        '<div class="card-badge" style="background:' + badgeColor + '">' + film.badge + '</div>' +
        '<div class="card-overlay" style="opacity:1">' +
          '<div class="card-title">' + film.title + '</div>' +
          '<div class="card-year">' + film.year + '</div>' +
        '</div>';
      results.appendChild(card);
    });
  }

  // ── TMDB POSTERLERİ ──
  async function loadPosters() {
    if (!TMDB_KEY) return;
    const promises = FILMS.map(film =>
      fetch("https://api.themoviedb.org/3/movie/" + film.id + "?api_key=" + TMDB_KEY)
        .then(r => r.json())
        .then(d => { if (d.poster_path) posters[film.id] = d.poster_path; })
        .catch(() => {})
    );
    await Promise.allSettled(promises);
    buildCards(getFiltered());
    buildHero();
  }

  // ── NAV SCROLL ──
  window.addEventListener("scroll", () => {
    document.getElementById("nav").classList.toggle("scrolled", window.scrollY > 20);
  });

  // ── ESC ──
  document.addEventListener("keydown", e => {
    if (e.key === "Escape") { closeSearch(); closeDetail(); closeVideo(); }
  });

  // ── HERO SLIDER ──
  const HERO_FILMS = [
    FILMS.find(f => f.id === 376867), // Moonlight
    FILMS.find(f => f.id === 426426), // Portrait of a Lady on Fire
    FILMS.find(f => f.id === 142),    // Brokeback Mountain
    FILMS.find(f => f.id === 258480), // Carol
    FILMS.find(f => f.id === 290098), // The Handmaiden
    FILMS.find(f => f.id === 64686),  // Weekend
  ].filter(Boolean);

  let heroIndex = 0;
  let heroTimer = null;

  function buildHero() {
    const slidesEl = document.getElementById("heroSlides");
    const dotsEl = document.getElementById("heroDots");
    slidesEl.innerHTML = "";
    dotsEl.innerHTML = "";

    HERO_FILMS.forEach((film, i) => {
      const slide = document.createElement("div");
      slide.className = "hero-slide" + (i === 0 ? " active" : "");
      const poster = posters[film.id];
      if (poster) {
        slide.style.backgroundImage = "url(" + IMG_BIG.replace("w780","original") + poster + ")";
      } else {
        const colors = {"Gay":"#3a0820,#1a0030","Lezbiyen":"#1a0a3a,#0a0020","Trans":"#0a2a2a,#001a2a","Biseksüel":"#1a0a2a,#0a0018","Queer":"#2a1500,#1a0a00","Belgesel":"#0a2a0a,#001800"};
        const c = (colors[film.badge] || "1a0a1a,0a0a1a").split(",");
        slide.style.background = "linear-gradient(135deg, #" + c[0] + ", #" + c[1] + ")";
      }
      slidesEl.appendChild(slide);

      const dot = document.createElement("div");
      dot.className = "hero-dot" + (i === 0 ? " active" : "");
      dot.onclick = () => goToSlide(i);
      dotsEl.appendChild(dot);
    });

    updateHeroContent(0);
    startHeroTimer();
  }

  function updateHeroContent(i) {
    const film = HERO_FILMS[i];
    if (!film) return;
    document.getElementById("heroTag").textContent = film.badge + " · " + film.country + " · " + film.year;
    document.getElementById("heroTitle").textContent = film.title;
    document.getElementById("heroDesc").textContent = film.desc;
    const btn = document.getElementById("heroBtnPlay");
    if (film.videoUrl) { btn.classList.remove("hidden"); } else { btn.classList.add("hidden"); }
  }

  function goToSlide(i) {
    const slides = document.querySelectorAll(".hero-slide");
    const dots = document.querySelectorAll(".hero-dot");
    slides[heroIndex].classList.remove("active");
    dots[heroIndex].classList.remove("active");
    heroIndex = (i + HERO_FILMS.length) % HERO_FILMS.length;
    slides[heroIndex].classList.add("active");
    dots[heroIndex].classList.add("active");
    updateHeroContent(heroIndex);
    resetHeroTimer();
  }

  function slideHero(dir) { goToSlide(heroIndex + dir); }

  function startHeroTimer() {
    heroTimer = setInterval(() => goToSlide(heroIndex + 1), 5000);
  }

  function resetHeroTimer() {
    clearInterval(heroTimer);
    startHeroTimer();
  }

  function playHeroFilm() {
    const film = HERO_FILMS[heroIndex];
    if (film && film.videoUrl) { currentFilm = film; playCurrentVideo(); }
  }

  function infoHeroFilm() {
    const film = HERO_FILMS[heroIndex];
    if (film) openDetail(film);
  }

  // ── İNİT ──
  buildCards(FILMS);
  buildHero();
  if (TMDB_KEY) loadPosters().then(() => buildHero());
</script>
</body>
</html>
