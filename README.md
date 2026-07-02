<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>SAPPHIRE — Wear the Gem</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=Inter:wght@300;400;500;600&family=DM+Sans:wght@400;500;600&display=swap" rel="stylesheet" />
<style>
  /* ===========================
     CSS CUSTOM PROPERTIES
  =========================== */
  :root {
    --base: #FFFCEF;
    --card: #659BB9;
    --card-light: #dceef8;
    --deep: #1B4F72;
    --gold: #E8B86D;
    --gold-dark: #c99a45;
    --sale: #C0392B;
    --amethyst: #6C3483;
    --text-primary: #1a1a2e;
    --text-secondary: #4a5568;
    --text-muted: #8492a6;
    --white: #ffffff;
    --surface: #f0f8ff;
    --border: rgba(101,155,185,0.2);
    --shadow-sm: 0 2px 12px rgba(27,79,114,0.08);
    --shadow-md: 0 8px 32px rgba(27,79,114,0.14);
    --shadow-lg: 0 20px 60px rgba(27,79,114,0.18);
    --radius-sm: 8px;
    --radius-md: 16px;
    --radius-lg: 24px;
    --radius-xl: 40px;
    --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }

  [data-theme="dark"] {
    --base: #212842;
    --card: #F0E7D5;
    --card-light: #2d3559;
    --deep: #89bcd8;
    --gold: #E8B86D;
    --text-primary: #F0E7D5;
    --text-secondary: #b8ccd8;
    --text-muted: #7a8fa0;
    --white: #2a3050;
    --surface: #1a2038;
    --border: rgba(240,231,213,0.12);
    --shadow-sm: 0 2px 12px rgba(0,0,0,0.3);
    --shadow-md: 0 8px 32px rgba(0,0,0,0.4);
    --shadow-lg: 0 20px 60px rgba(0,0,0,0.5);
  }

  /* ===========================
     RESET & BASE
  =========================== */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Inter', sans-serif;
    background: var(--base);
    color: var(--text-primary);
    transition: background var(--transition), color var(--transition);
    overflow-x: hidden;
    line-height: 1.6;
  }

  img { max-width: 100%; display: block; }
  a { text-decoration: none; color: inherit; }

  /* ===========================
     SCROLLBAR
  =========================== */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--base); }
  ::-webkit-scrollbar-thumb { background: var(--card); border-radius: 10px; }

  /* ===========================
     NAVIGATION
  =========================== */
  .nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 5%;
    height: 72px;
    background: rgba(255,252,239,0.85);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    transition: background var(--transition);
  }

  [data-theme="dark"] .nav {
    background: rgba(33,40,66,0.88);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 900;
    letter-spacing: 0.12em;
    background: linear-gradient(135deg, var(--deep) 0%, var(--card) 50%, var(--gold) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }

  .nav-links a {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.875rem;
    font-weight: 500;
    color: var(--text-secondary);
    letter-spacing: 0.05em;
    transition: color var(--transition);
    position: relative;
  }

  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 0; right: 100%;
    height: 2px;
    background: var(--card);
    transition: right var(--transition);
  }

  .nav-links a:hover { color: var(--deep); }
  .nav-links a:hover::after { right: 0; }

  .nav-actions {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .theme-toggle {
    width: 44px; height: 44px;
    border: none;
    background: var(--card-light);
    border-radius: 50%;
    cursor: pointer;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background var(--transition), transform var(--transition);
    color: var(--text-primary);
  }

  .theme-toggle:hover { transform: rotate(20deg); background: var(--card); }

  .cart-btn {
    position: relative;
    width: 44px; height: 44px;
    border: none;
    background: var(--card-light);
    border-radius: 50%;
    cursor: pointer;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background var(--transition);
    color: var(--text-primary);
  }

  .cart-btn:hover { background: var(--card); }

  .cart-count {
    position: absolute;
    top: -4px; right: -4px;
    width: 18px; height: 18px;
    background: var(--sale);
    color: white;
    border-radius: 50%;
    font-size: 0.65rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .hamburger {
    display: none;
    flex-direction: column;
    gap: 5px;
    cursor: pointer;
    background: none;
    border: none;
    padding: 4px;
  }

  .hamburger span {
    display: block;
    width: 24px; height: 2px;
    background: var(--text-primary);
    border-radius: 2px;
    transition: transform var(--transition), opacity var(--transition);
  }

  /* ===========================
     MOBILE MENU
  =========================== */
  .mobile-menu {
    display: none;
    position: fixed;
    top: 72px; left: 0; right: 0;
    background: var(--base);
    border-bottom: 1px solid var(--border);
    z-index: 999;
    padding: 1.5rem 5%;
    flex-direction: column;
    gap: 1rem;
    backdrop-filter: blur(20px);
    box-shadow: var(--shadow-md);
  }

  .mobile-menu.open { display: flex; }

  .mobile-menu a {
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
    font-weight: 500;
    color: var(--text-secondary);
    padding: 0.5rem 0;
    border-bottom: 1px solid var(--border);
  }

  /* ===========================
     HERO
  =========================== */
  .hero {
    min-height: 100vh;
    padding-top: 72px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 50% at 70% 50%, rgba(101,155,185,0.15) 0%, transparent 70%),
      radial-gradient(ellipse 40% 40% at 20% 80%, rgba(232,184,109,0.1) 0%, transparent 60%),
      radial-gradient(ellipse 30% 30% at 80% 20%, rgba(108,52,131,0.08) 0%, transparent 50%);
    pointer-events: none;
  }

  .hero-content {
    padding: 4rem 8% 4rem 8%;
    position: relative;
    z-index: 2;
  }

  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--card);
    margin-bottom: 1.5rem;
  }

  .hero-eyebrow::before {
    content: '';
    display: inline-block;
    width: 28px; height: 2px;
    background: var(--card);
  }

  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 6vw, 5.5rem);
    font-weight: 900;
    line-height: 1.05;
    margin-bottom: 1.5rem;
    color: var(--text-primary);
  }

  .hero-title .shimmer-word {
    display: inline-block;
    background: linear-gradient(
      90deg,
      var(--deep) 0%,
      var(--card) 30%,
      var(--gold) 50%,
      var(--card) 70%,
      var(--deep) 100%
    );
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: shimmer 3s linear infinite;
  }

  @keyframes shimmer {
    0% { background-position: 0% center; }
    100% { background-position: 200% center; }
  }

  .hero-desc {
    font-size: 1.05rem;
    color: var(--text-secondary);
    line-height: 1.75;
    max-width: 440px;
    margin-bottom: 2.5rem;
  }

  .hero-actions {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.875rem 2rem;
    background: linear-gradient(135deg, var(--deep), var(--card));
    color: white;
    border: none;
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 600;
    cursor: pointer;
    transition: transform var(--transition), box-shadow var(--transition);
    box-shadow: 0 4px 20px rgba(27,79,114,0.3);
    letter-spacing: 0.04em;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(27,79,114,0.4);
  }

  .btn-outline {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.875rem 2rem;
    background: transparent;
    color: var(--deep);
    border: 2px solid var(--deep);
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 600;
    cursor: pointer;
    transition: all var(--transition);
    letter-spacing: 0.04em;
  }

  .btn-outline:hover {
    background: var(--deep);
    color: white;
    transform: translateY(-2px);
  }

  .hero-stats {
    display: flex;
    gap: 2.5rem;
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 1px solid var(--border);
  }

  .stat-item { }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 900;
    color: var(--deep);
    line-height: 1;
  }

  .stat-label {
    font-size: 0.78rem;
    color: var(--text-muted);
    font-family: 'DM Sans', sans-serif;
    font-weight: 500;
    letter-spacing: 0.05em;
  }

  .hero-visual {
    position: relative;
    height: 100vh;
    min-height: 600px;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .hero-ring {
    position: absolute;
    border-radius: 50%;
    border: 1px solid;
    animation: ringRotate 20s linear infinite;
  }

  .hero-ring-1 {
    width: 500px; height: 500px;
    border-color: rgba(101,155,185,0.15);
    animation-direction: normal;
  }

  .hero-ring-2 {
    width: 380px; height: 380px;
    border-color: rgba(232,184,109,0.2);
    animation-direction: reverse;
    animation-duration: 15s;
  }

  .hero-ring-3 {
    width: 260px; height: 260px;
    border-color: rgba(108,52,131,0.15);
    animation-duration: 10s;
  }

  @keyframes ringRotate {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  .hero-card-main {
    position: relative;
    z-index: 3;
    width: 260px;
    background: var(--white);
    border-radius: var(--radius-lg);
    overflow: hidden;
    box-shadow: var(--shadow-lg);
    transform: rotate(-3deg);
    animation: heroFloat 6s ease-in-out infinite;
  }

  @keyframes heroFloat {
    0%, 100% { transform: rotate(-3deg) translateY(0); }
    50% { transform: rotate(-3deg) translateY(-16px); }
  }

  .hero-card-main img, .hero-card-main .hero-img-placeholder {
    width: 100%; height: 320px;
    object-fit: cover;
  }

  .hero-img-placeholder {
    background: linear-gradient(145deg, #dceef8 0%, #b5d4e8 40%, #7fb3d0 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 5rem;
  }

  .hero-card-info {
    padding: 1rem 1.2rem 1.2rem;
  }

  .hero-card-name {
    font-family: 'Playfair Display', serif;
    font-size: 0.95rem;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: 0.25rem;
  }

  .hero-card-price {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--card);
  }

  .float-badge {
    position: absolute;
    z-index: 4;
    background: var(--white);
    border-radius: var(--radius-md);
    padding: 0.75rem 1rem;
    box-shadow: var(--shadow-md);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    font-weight: 600;
    animation: badgeFloat 4s ease-in-out infinite;
  }

  .float-badge-1 {
    top: 25%; right: -20px;
    animation-delay: 1s;
    color: var(--sale);
  }

  .float-badge-2 {
    bottom: 28%; left: -24px;
    animation-delay: 2.5s;
    color: var(--amethyst);
  }

  @keyframes badgeFloat {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }

  .float-badge-label {
    display: flex;
    align-items: center;
    gap: 0.4rem;
  }

  .badge-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: currentColor;
  }

  /* ===========================
     MARQUEE BAND
  =========================== */
  .marquee-band {
    background: linear-gradient(135deg, var(--deep), #2d6a9f);
    padding: 0.9rem 0;
    overflow: hidden;
    white-space: nowrap;
  }

  .marquee-inner {
    display: inline-flex;
    animation: marquee 22s linear infinite;
    gap: 3rem;
  }

  .marquee-inner span {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.8rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: white;
    opacity: 0.9;
  }

  .marquee-inner .dot {
    color: var(--gold);
    opacity: 1;
  }

  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  /* ===========================
     SECTION HEADER
  =========================== */
  .section {
    padding: 6rem 8%;
  }

  .section-header {
    margin-bottom: 3.5rem;
  }

  .section-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--card);
    margin-bottom: 0.75rem;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    font-weight: 900;
    color: var(--text-primary);
    line-height: 1.15;
  }

  .section-subtitle {
    font-size: 1rem;
    color: var(--text-secondary);
    margin-top: 0.75rem;
    max-width: 480px;
  }

  /* ===========================
     CATEGORY PILLS
  =========================== */
  .filter-pills {
    display: flex;
    gap: 0.75rem;
    margin-bottom: 2.5rem;
    flex-wrap: wrap;
  }

  .pill {
    padding: 0.5rem 1.25rem;
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    cursor: pointer;
    border: 2px solid var(--border);
    background: transparent;
    color: var(--text-secondary);
    transition: all var(--transition);
    letter-spacing: 0.03em;
  }

  .pill:hover, .pill.active {
    background: var(--deep);
    border-color: var(--deep);
    color: white;
    transform: translateY(-1px);
  }

  /* ===========================
     PRODUCT GRID
  =========================== */
  .products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 1.75rem;
  }

  .product-card {
    background: var(--white);
    border-radius: var(--radius-lg);
    overflow: hidden;
    box-shadow: var(--shadow-sm);
    transition: transform var(--transition), box-shadow var(--transition);
    cursor: pointer;
    position: relative;
    border: 1px solid var(--border);
  }

  .product-card:hover {
    transform: translateY(-6px);
    box-shadow: var(--shadow-lg);
  }

  .product-img-wrap {
    position: relative;
    overflow: hidden;
    height: 280px;
  }

  .product-img-bg {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 4.5rem;
    transition: transform 0.5s ease;
    position: relative;
  }

  .product-card:hover .product-img-bg {
    transform: scale(1.06);
  }

  .product-img-bg::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(0,0,0,0.12) 0%, transparent 50%);
  }

  .product-tag {
    position: absolute;
    top: 1rem; left: 1rem;
    z-index: 2;
    padding: 0.3rem 0.75rem;
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  .tag-new { background: var(--gold); color: #1a1a2e; }
  .tag-hot { background: var(--sale); color: white; }
  .tag-bestseller { background: var(--amethyst); color: white; }
  .tag-trending { background: var(--deep); color: white; }

  .wishlist-btn {
    position: absolute;
    top: 1rem; right: 1rem;
    z-index: 2;
    width: 36px; height: 36px;
    background: rgba(255,255,255,0.9);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    font-size: 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform var(--transition), background var(--transition);
    backdrop-filter: blur(6px);
  }

  .wishlist-btn:hover { transform: scale(1.15); background: white; }
  .wishlist-btn.liked { background: #ffe4e4; }

  .quick-add {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    z-index: 2;
    background: var(--deep);
    color: white;
    border: none;
    padding: 0.75rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    cursor: pointer;
    transform: translateY(100%);
    transition: transform var(--transition);
    letter-spacing: 0.04em;
  }

  .product-card:hover .quick-add {
    transform: translateY(0);
  }

  .product-info {
    padding: 1.1rem 1.2rem 1.3rem;
  }

  .product-category {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--card);
    margin-bottom: 0.35rem;
  }

  .product-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.02rem;
    font-weight: 700;
    color: var(--text-primary);
    margin-bottom: 0.5rem;
    line-height: 1.3;
  }

  .product-rating {
    display: flex;
    align-items: center;
    gap: 0.4rem;
    margin-bottom: 0.75rem;
  }

  .stars { color: var(--gold); font-size: 0.8rem; letter-spacing: 1px; }

  .rating-count {
    font-size: 0.72rem;
    color: var(--text-muted);
    font-family: 'DM Sans', sans-serif;
  }

  .product-price-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .price-current {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    font-weight: 900;
    color: var(--deep);
  }

  .price-original {
    font-size: 0.85rem;
    color: var(--text-muted);
    text-decoration: line-through;
    font-family: 'DM Sans', sans-serif;
    margin-left: 0.4rem;
  }

  .price-discount {
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--sale);
    font-family: 'DM Sans', sans-serif;
    background: rgba(192,57,43,0.1);
    padding: 0.2rem 0.5rem;
    border-radius: var(--radius-sm);
  }

  /* ===========================
     DEALS SECTION
  =========================== */
  .deals-section {
    padding: 5rem 0;
    background: linear-gradient(135deg, var(--deep) 0%, #1a3a5c 40%, var(--amethyst) 100%);
    position: relative;
    overflow: hidden;
  }

  .deals-section::before {
    content: '';
    position: absolute;
    inset: 0;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.03'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
    opacity: 1;
  }

  .deals-inner {
    padding: 0 8%;
    position: relative;
    z-index: 2;
  }

  .deals-header {
    text-align: center;
    margin-bottom: 3rem;
  }

  .deals-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3.2rem);
    font-weight: 900;
    color: white;
    margin-bottom: 0.5rem;
  }

  .deals-subtitle {
    color: rgba(255,255,255,0.7);
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
  }

  .countdown-box {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.2);
    border-radius: var(--radius-md);
    padding: 0.5rem 1.25rem;
    margin-top: 1rem;
    backdrop-filter: blur(8px);
  }

  .countdown-label {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.8rem;
    color: var(--gold);
    font-weight: 600;
    letter-spacing: 0.05em;
  }

  .countdown-timer {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: white;
    letter-spacing: 0.05em;
  }

  .deals-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1.25rem;
  }

  .deal-card {
    background: rgba(255,255,255,0.09);
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: var(--radius-lg);
    padding: 1.5rem 1.25rem;
    text-align: center;
    cursor: pointer;
    transition: transform var(--transition), background var(--transition);
    backdrop-filter: blur(8px);
    position: relative;
    overflow: hidden;
  }

  .deal-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,255,255,0.06) 0%, transparent 100%);
    opacity: 0;
    transition: opacity var(--transition);
  }

  .deal-card:hover { transform: translateY(-4px) scale(1.02); }
  .deal-card:hover::before { opacity: 1; }

  .deal-icon { font-size: 2.8rem; margin-bottom: 0.75rem; }

  .deal-cat {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: rgba(255,255,255,0.6);
    margin-bottom: 0.3rem;
  }

  .deal-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    font-weight: 700;
    color: white;
    margin-bottom: 0.75rem;
    line-height: 1.3;
  }

  .deal-badge {
    display: inline-block;
    padding: 0.35rem 1rem;
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 800;
    background: var(--gold);
    color: #1a1a2e;
    margin-bottom: 0.5rem;
  }

  .deal-from {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.75rem;
    color: rgba(255,255,255,0.55);
  }

  /* ===========================
     FEATURED BANNER
  =========================== */
  .featured-banner {
    padding: 5rem 8%;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
  }

  .banner-card {
    border-radius: var(--radius-lg);
    padding: 3rem;
    position: relative;
    overflow: hidden;
    min-height: 320px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    cursor: pointer;
    transition: transform var(--transition);
  }

  .banner-card:hover { transform: scale(1.01); }

  .banner-card-1 {
    background: linear-gradient(135deg, #dceef8 0%, #a8cfe0 100%);
  }

  .banner-card-2 {
    background: linear-gradient(135deg, #f9f0d3 0%, #f0d899 100%);
  }

  .banner-emoji {
    position: absolute;
    top: 50%;
    right: 2rem;
    transform: translateY(-50%);
    font-size: 7rem;
    opacity: 0.5;
    filter: drop-shadow(0 8px 16px rgba(0,0,0,0.15));
    animation: bannerFloat 5s ease-in-out infinite;
  }

  .banner-card-2 .banner-emoji { animation-delay: 2s; }

  @keyframes bannerFloat {
    0%, 100% { transform: translateY(-50%) rotate(0deg); }
    50% { transform: translateY(-55%) rotate(5deg); }
  }

  .banner-tag {
    display: inline-block;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    background: var(--deep);
    color: white;
    padding: 0.3rem 0.75rem;
    border-radius: var(--radius-xl);
    margin-bottom: 0.75rem;
    align-self: flex-start;
  }

  .banner-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 900;
    color: var(--text-primary);
    margin-bottom: 0.5rem;
    line-height: 1.2;
  }

  .banner-sub {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.85rem;
    color: var(--text-secondary);
    margin-bottom: 1.25rem;
  }

  .btn-sm {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.65rem 1.5rem;
    background: var(--deep);
    color: white;
    border: none;
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    font-weight: 600;
    cursor: pointer;
    transition: transform var(--transition), box-shadow var(--transition);
    align-self: flex-start;
  }

  .btn-sm:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(27,79,114,0.3);
  }

  /* ===========================
     REVIEWS
  =========================== */
  .reviews-section {
    background: var(--surface);
    transition: background var(--transition);
  }

  [data-theme="dark"] .reviews-section {
    background: var(--surface);
  }

  .reviews-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5rem;
  }

  .review-card {
    background: var(--white);
    border-radius: var(--radius-lg);
    padding: 1.75rem;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border);
    transition: transform var(--transition), box-shadow var(--transition);
    position: relative;
  }

  .review-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-md);
  }

  .review-card::before {
    content: '"';
    position: absolute;
    top: 1rem; right: 1.5rem;
    font-family: 'Playfair Display', serif;
    font-size: 4rem;
    color: var(--card-light);
    line-height: 1;
    pointer-events: none;
  }

  .reviewer-head {
    display: flex;
    align-items: center;
    gap: 0.9rem;
    margin-bottom: 1rem;
  }

  .reviewer-avatar {
    width: 44px; height: 44px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.3rem;
    flex-shrink: 0;
  }

  .reviewer-name {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--text-primary);
  }

  .reviewer-date {
    font-size: 0.72rem;
    color: var(--text-muted);
    font-family: 'DM Sans', sans-serif;
  }

  .review-stars { color: var(--gold); font-size: 0.82rem; margin-bottom: 0.75rem; letter-spacing: 2px; }

  .review-text {
    font-size: 0.88rem;
    color: var(--text-secondary);
    line-height: 1.7;
    font-style: italic;
  }

  .review-product {
    margin-top: 1rem;
    padding-top: 0.75rem;
    border-top: 1px solid var(--border);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.72rem;
    font-weight: 600;
    color: var(--card);
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  /* ===========================
     NEWSLETTER
  =========================== */
  .newsletter-section {
    padding: 5rem 8%;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .newsletter-bg-decor {
    position: absolute;
    border-radius: 50%;
    pointer-events: none;
  }

  .newsletter-bg-decor-1 {
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(101,155,185,0.08) 0%, transparent 70%);
    top: -200px; left: -100px;
  }

  .newsletter-bg-decor-2 {
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(232,184,109,0.08) 0%, transparent 70%);
    bottom: -100px; right: -50px;
  }

  .newsletter-inner {
    max-width: 560px;
    margin: 0 auto;
    position: relative;
    z-index: 2;
  }

  .newsletter-icon {
    width: 70px; height: 70px;
    background: linear-gradient(135deg, var(--deep), var(--card));
    border-radius: 50%;
    margin: 0 auto 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.8rem;
    box-shadow: 0 8px 24px rgba(27,79,114,0.25);
  }

  .newsletter-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.6rem, 3vw, 2.2rem);
    font-weight: 900;
    color: var(--text-primary);
    margin-bottom: 0.75rem;
    line-height: 1.2;
  }

  .newsletter-subtitle {
    font-size: 0.95rem;
    color: var(--text-secondary);
    margin-bottom: 2rem;
    line-height: 1.6;
  }

  .newsletter-form {
    display: flex;
    gap: 0.75rem;
    max-width: 420px;
    margin: 0 auto 1.25rem;
  }

  .newsletter-input {
    flex: 1;
    padding: 0.875rem 1.25rem;
    border: 2px solid var(--border);
    border-radius: var(--radius-xl);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.88rem;
    background: var(--white);
    color: var(--text-primary);
    outline: none;
    transition: border-color var(--transition);
  }

  .newsletter-input:focus { border-color: var(--card); }
  .newsletter-input::placeholder { color: var(--text-muted); }

  .newsletter-offer {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.8rem;
    color: var(--text-muted);
  }

  /* ===========================
     FOOTER
  =========================== */
  .footer {
    background: var(--deep);
    color: white;
    padding: 4rem 8% 2rem;
  }

  .footer-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 3rem;
    margin-bottom: 3rem;
  }

  .footer-brand {}

  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 900;
    letter-spacing: 0.12em;
    color: white;
    margin-bottom: 1rem;
  }

  .footer-desc {
    font-size: 0.85rem;
    color: rgba(255,255,255,0.6);
    line-height: 1.7;
    margin-bottom: 1.5rem;
  }

  .social-links {
    display: flex;
    gap: 0.75rem;
  }

  .social-btn {
    width: 38px; height: 38px;
    background: rgba(255,255,255,0.1);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    cursor: pointer;
    transition: background var(--transition), transform var(--transition);
    text-decoration: none;
  }

  .social-btn:hover {
    background: rgba(255,255,255,0.25);
    transform: translateY(-2px);
  }

  .footer-col-title {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.25rem;
  }

  .footer-links {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
  }

  .footer-links a {
    font-size: 0.85rem;
    color: rgba(255,255,255,0.6);
    transition: color var(--transition);
    font-family: 'DM Sans', sans-serif;
  }

  .footer-links a:hover { color: white; }

  .footer-divider {
    border: none;
    border-top: 1px solid rgba(255,255,255,0.1);
    margin-bottom: 2rem;
  }

  .footer-bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .footer-copy {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.8rem;
    color: rgba(255,255,255,0.45);
  }

  .footer-legal {
    display: flex;
    gap: 1.5rem;
  }

  .footer-legal a {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.8rem;
    color: rgba(255,255,255,0.45);
    transition: color var(--transition);
  }

  .footer-legal a:hover { color: rgba(255,255,255,0.8); }

  /* ===========================
     TOAST NOTIFICATION
  =========================== */
  .toast {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    z-index: 9999;
    background: var(--deep);
    color: white;
    padding: 1rem 1.5rem;
    border-radius: var(--radius-md);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.88rem;
    font-weight: 600;
    box-shadow: var(--shadow-lg);
    display: flex;
    align-items: center;
    gap: 0.6rem;
    transform: translateY(20px);
    opacity: 0;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    pointer-events: none;
    max-width: 320px;
  }

  .toast.show {
    transform: translateY(0);
    opacity: 1;
  }

  /* ===========================
     BACK TO TOP
  =========================== */
  .back-top {
    position: fixed;
    bottom: 2rem;
    left: 2rem;
    z-index: 999;
    width: 44px; height: 44px;
    background: var(--deep);
    color: white;
    border: none;
    border-radius: 50%;
    cursor: pointer;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: var(--shadow-md);
    opacity: 0;
    transform: translateY(20px);
    transition: all var(--transition);
    pointer-events: none;
  }

  .back-top.visible {
    opacity: 1;
    transform: translateY(0);
    pointer-events: all;
  }

  .back-top:hover { background: var(--card); transform: translateY(-2px); }

  /* ===========================
     RESPONSIVE
  =========================== */
  @media (max-width: 900px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }

    .hero {
      grid-template-columns: 1fr;
      min-height: auto;
      padding: 72px 0 3rem;
    }

    .hero-content {
      padding: 2.5rem 6% 0;
      order: 2;
    }

    .hero-visual {
      height: 400px;
      order: 1;
    }

    .hero-ring-1 { width: 320px; height: 320px; }
    .hero-ring-2 { width: 240px; height: 240px; }
    .hero-ring-3 { width: 160px; height: 160px; }
    .hero-card-main { width: 200px; }
    .hero-img-placeholder { height: 240px; }
    .float-badge-1, .float-badge-2 { display: none; }

    .hero-stats { gap: 1.5rem; }

    .section { padding: 3.5rem 6%; }

    .featured-banner {
      grid-template-columns: 1fr;
      padding: 3rem 6%;
    }

    .footer-grid {
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }

    .footer-bottom {
      flex-direction: column;
      text-align: center;
    }
  }

  @media (max-width: 600px) {
    .hero-title { font-size: 2.4rem; }
    .hero-actions { flex-direction: column; }
    .btn-primary, .btn-outline { width: 100%; justify-content: center; }

    .products-grid { grid-template-columns: repeat(2, 1fr); gap: 1rem; }
    .product-img-wrap { height: 200px; }
    .product-img-bg { font-size: 3rem; }

    .deals-grid { grid-template-columns: repeat(2, 1fr); }

    .reviews-grid { grid-template-columns: 1fr; }

    .newsletter-form { flex-direction: column; }

    .footer-grid { grid-template-columns: 1fr; gap: 1.5rem; }
    .footer-legal { flex-direction: column; align-items: center; gap: 0.5rem; }

    .toast { left: 1rem; right: 1rem; bottom: 1rem; }
    .back-top { left: 1rem; bottom: 1rem; }
  }

  /* ===========================
     SCROLL ANIMATIONS
  =========================== */
  .fade-up {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .fade-up.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .fade-up:nth-child(2) { transition-delay: 0.1s; }
  .fade-up:nth-child(3) { transition-delay: 0.2s; }
  .fade-up:nth-child(4) { transition-delay: 0.3s; }
  .fade-up:nth-child(5) { transition-delay: 0.4s; }
  .fade-up:nth-child(6) { transition-delay: 0.5s; }

  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      transition-duration: 0.01ms !important;
    }
  }
</style>
</head>
<body>

<!-- ========================= NAVIGATION ========================= -->
<nav class="nav">
  <a href="#" class="nav-logo">SAPPHIRE</a>

  <ul class="nav-links">
    <li><a href="#products">Collections</a></li>
    <li><a href="#deals">Deals</a></li>
    <li><a href="#reviews">Reviews</a></li>
    <li><a href="#newsletter">Newsletter</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>

  <div class="nav-actions">
    <button class="theme-toggle" id="themeToggle" aria-label="Toggle theme">🌙</button>
    <button class="cart-btn" id="cartBtn" aria-label="View cart">
      🛒
      <span class="cart-count" id="cartCount">0</span>
    </button>
    <button class="hamburger" id="hamburger" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </div>
</nav>

<!-- Mobile Menu -->
<div class="mobile-menu" id="mobileMenu">
  <a href="#products">Collections</a>
  <a href="#deals">Deals</a>
  <a href="#reviews">Reviews</a>
  <a href="#newsletter">Newsletter</a>
  <a href="#contact">Contact</a>
</div>

<!-- ========================= HERO ========================= -->
<section class="hero">
  <div class="hero-bg"></div>

  <div class="hero-content">
    <div class="hero-eyebrow">New Collection 2026</div>

    <h1 class="hero-title">
      Wear the<br>
      <span class="shimmer-word">Sapphire</span><br>
      Within You
    </h1>

    <p class="hero-desc">
      Timeless silhouettes meet modern edge. Each SAPPHIRE piece is crafted for
      those who wear their confidence like a second skin.
    </p>

    <div class="hero-actions">
      <button class="btn-primary" onclick="scrollToProducts()">
        Shop Now ✦
      </button>
      <button class="btn-outline" onclick="scrollToSection('deals')">
        View Deals
      </button>
    </div>

    <div class="hero-stats">
      <div class="stat-item">
        <div class="stat-num">12K+</div>
        <div class="stat-label">Happy Customers</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">340+</div>
        <div class="stat-label">Unique Styles</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">4.9★</div>
        <div class="stat-label">Avg. Rating</div>
      </div>
    </div>
  </div>

  <div class="hero-visual">
    <div class="hero-ring hero-ring-1"></div>
    <div class="hero-ring hero-ring-2"></div>
    <div class="hero-ring hero-ring-3"></div>

    <div class="hero-card-main">
      <img src="download (2).jpg" alt="pearl Silk Drape" class="hero-img-placeholder" />
      <div class="hero-card-info">
        <div class="hero-card-name">Azure Silk Drape</div>
        <div class="hero-card-price">₹ 4,299</div>
      </div>
    </div>

    <div class="float-badge float-badge-1">
      <div class="float-badge-label">
        <span class="badge-dot"></span>
        Just Dropped — 23% OFF
      </div>
    </div>

    <div class="float-badge float-badge-2">
      <div class="float-badge-label">
        <span class="badge-dot"></span>
        Bestseller this week ✦
      </div>
    </div>
  </div>
</section>

<!-- ========================= MARQUEE ========================= -->
<div class="marquee-band" aria-hidden="true">
  <div class="marquee-inner" id="marqueeInner">
    <span>Free Shipping Over ₹999</span><span class="dot">✦</span>
    <span>New Arrivals Every Monday</span><span class="dot">✦</span>
    <span>Sustainable Fabrics</span><span class="dot">✦</span>
    <span>Exclusive Member Deals</span><span class="dot">✦</span>
    <span>Easy 30-Day Returns</span><span class="dot">✦</span>
    <span>Handcrafted in India</span><span class="dot">✦</span>
    <span>Free Shipping Over ₹999</span><span class="dot">✦</span>
    <span>New Arrivals Every Monday</span><span class="dot">✦</span>
    <span>Sustainable Fabrics</span><span class="dot">✦</span>
    <span>Exclusive Member Deals</span><span class="dot">✦</span>
    <span>Easy 30-Day Returns</span><span class="dot">✦</span>
    <span>Handcrafted in India</span><span class="dot">✦</span>
  </div>
</div>

<!-- ========================= PRODUCTS ========================= -->
<section class="section" id="products">
  <div class="section-header">
    <div class="section-eyebrow">✦ Collections</div>
    <h2 class="section-title">Curated Just for You</h2>
    <p class="section-subtitle">Discover styles that speak your language — elevated, effortless, iconic.</p>
  </div>

  <div class="filter-pills">
    <button class="pill active" onclick="filterProducts(this, 'all')">All</button>
    <button class="pill" onclick="filterProducts(this, 'dresses')">Dresses</button>
    <button class="pill" onclick="filterProducts(this, 'tops')">Tops</button>
    <button class="pill" onclick="filterProducts(this, 'pants')">Pants</button>
    <button class="pill" onclick="filterProducts(this, 'accessories')">Accessories</button>
    <button class="pill" onclick="filterProducts(this, 'sale')">Sale</button>
  </div>

  <div class="products-grid" id="productsGrid">
    <!-- JS will render products here -->
  </div>
</section>

<!-- ========================= DEALS ========================= -->
<section class="deals-section" id="deals">
  <div class="deals-inner">
    <div class="deals-header">
      <h2 class="deals-title">Flash Deals & Offers</h2>
      <p class="deals-subtitle">Unbeatable discounts, limited-time only. Don't blink.</p>
      <div class="countdown-box">
        <span class="countdown-label">⏱ Ends in:</span>
        <span class="countdown-timer" id="countdown">--:--:--</span>
      </div>
    </div>

    <div class="deals-grid">
      <div class="deal-card fade-up">
        <img src="Pink Floral Corset Dress Outfit _ Aesthetic Summer Garden Dress Look.jpg" alt="Dresses" class="hero-img-placeholder" /> 
        <div class="deal-cat">Dresses</div>
        <div class="deal-name">Summer Collection</div>
        <div class="deal-badge">Upto 40% OFF</div>
        <div class="deal-from">Starting ₹1,499</div>
      </div>

      <div class="deal-card fade-up">
        <img src="Pinteresty  top under budget 💙 you NEED this 😭✨ Shop here 👇”.jpg" alt="tops" class="hero-img-placeholder" width="90%" />
        <div class="deal-cat">Tops & Shirts</div>
        <div class="deal-name">Everyday Essentials</div>
        <div class="deal-badge">Flat 30% OFF</div>
        <div class="deal-from">Starting ₹799</div>
      </div>

      <div class="deal-card fade-up">
       <img src="Men's Embroidered Patch & Rivet Decorated Denim Jeans.jpg" alt="bottoms" class="hero-img-placeholder" />
        <div class="deal-cat">Bottoms</div>
        <div class="deal-name">Denim & Trousers</div>
        <div class="deal-badge">Buy 2 Get 1 Free</div>
        <div class="deal-from">Starting ₹1,299</div>
      </div>

      <div class="deal-card fade-up">
      <img src="download (4).jpg" alt="bags" class="hero-img-placeholder"" />
        <div class="deal-cat">Accessories</div>
        <div class="deal-name">Statement Bags</div>
        <div class="deal-badge">25% OFF</div>
        <div class="deal-from">Starting ₹2,199</div>
      </div>

      <div class="deal-card fade-up">
        <img src="download (5).jpg" alt="outerwear" class="hero-img-placeholder" />
        <div class="deal-cat">Outerwear</div>
        <div class="deal-name">Jacket Season</div>
        <div class="deal-badge">Upto 50% OFF</div>
        <div class="deal-from">Starting ₹2,599</div>
      </div>

      <div class="deal-card fade-up">
        <img src="Feathers in the Dark 🕊️.jpg" alt="Azure Silk Drape" class="hero-img-placeholder" />
        <div class="deal-cat">Premium</div>
        <div class="deal-name">Sapphire Select</div>
        <div class="deal-badge">Members Only</div>
        <div class="deal-from">Exclusive Prices</div>
      </div>
    </div>
  </div>
</section>

<!-- ========================= FEATURED BANNERS ========================= -->
<section class="featured-banner">
  <div class="banner-card banner-card-1">
    <div class="banner-emoji">🌊</div>
    <span class="banner-tag">Limited Time</span>
    <h3 class="banner-title">Ocean Blue<br>Summer Edit</h3>
    <p class="banner-sub">Cool hues for warmer days. Dive into the season's must-haves.</p>
    <button class="btn-sm" onclick="scrollToProducts()">Explore Collection →</button>
  </div>

  <div class="banner-card banner-card-2">
    <div class="banner-emoji">✨</div>
    <span class="banner-tag">New In</span>
    <h3 class="banner-title">Golden Hour<br>Evening Wear</h3>
    <p class="banner-sub">Shimmer and silk for every soirée. Your most iconic night awaits.</p>
    <button class="btn-sm" onclick="scrollToProducts()">Shop Now →</button>
  </div>
</section>

<!-- ========================= REVIEWS ========================= -->
<section class="section reviews-section" id="reviews">
  <div class="section-header">
    <div class="section-eyebrow">✦ Real Reviews</div>
    <h2 class="section-title">What Our Community Says</h2>
    <p class="section-subtitle">Over 12,000 customers share their SAPPHIRE story every month.</p>
  </div>

  <div class="reviews-grid">
    <div class="review-card fade-up">
      <div class="reviewer-head">
        <div class="reviewer-avatar" style="background:linear-gradient(135deg,#dceef8,#659BB9)">😊</div>
        <div>
          <div class="reviewer-name">Ananya Sharma</div>
          <div class="reviewer-date">June 2026 · Verified Buyer</div>
        </div>
      </div>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">The Azure Silk Drape is everything I imagined and more. The fabric feels incredibly luxurious, and the fit is absolutely perfect. I received so many compliments at the wedding!</p>
      <div class="review-product">Reviewed: Azure Silk Drape</div>
    </div>

    <div class="review-card fade-up">
      <div class="reviewer-head">
        <div class="reviewer-avatar" style="background:linear-gradient(135deg,#f9f0d3,#E8B86D)">🌟</div>
        <div>
          <div class="reviewer-name">Riya Mehta</div>
          <div class="reviewer-date">May 2026 · Verified Buyer</div>
        </div>
      </div>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">I ordered three dresses during the flash sale and every single one arrived beautifully packaged. The indigo maxi dress has become my absolute go-to for everything.</p>
      <div class="review-product">Reviewed: Indigo Maxi Dress</div>
    </div>

    <div class="review-card fade-up">
      <div class="reviewer-head">
        <div class="reviewer-avatar" style="background:linear-gradient(135deg,#e8d5f0,#6C3483)">💜</div>
        <div>
          <div class="reviewer-name">Priya Nair</div>
          <div class="reviewer-date">May 2026 · Verified Buyer</div>
        </div>
      </div>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">The quality of SAPPHIRE clothing is just unmatched at this price point. Fast delivery, stunning packaging, and a brand that genuinely cares. Will shop again for sure!</p>
      <div class="review-product">Reviewed: Amethyst Blazer Set</div>
    </div>

    <div class="review-card fade-up">
      <div class="reviewer-head">
        <div class="reviewer-avatar" style="background:linear-gradient(135deg,#fde8e8,#C0392B)">❤️</div>
        <div>
          <div class="reviewer-name">Sneha Kapoor</div>
          <div class="reviewer-date">April 2026 · Verified Buyer</div>
        </div>
      </div>
      <div class="review-stars">★★★★★</div>
      <p class="review-text">Finally a brand that delivers on its promise. The sustainable fabric initiative is real — you can feel the difference. Proud to wear and recommend SAPPHIRE to everyone I know.</p>
      <div class="review-product">Reviewed: Coral Linen Co-ord</div>
    </div>
  </div>
</section>

<!-- ========================= NEWSLETTER ========================= -->
<section class="newsletter-section" id="newsletter">
  <div class="newsletter-bg-decor newsletter-bg-decor-1"></div>
  <div class="newsletter-bg-decor newsletter-bg-decor-2"></div>
  <div class="newsletter-inner">
    <div class="newsletter-icon">💌</div>
    <h2 class="newsletter-title">Stay in the Loop</h2>
    <p class="newsletter-subtitle">
      Get early access to new drops, exclusive member deals, and style inspiration delivered to your inbox. No spam, only sapphires.
    </p>
    <div class="newsletter-form">
      <input
        type="email"
        class="newsletter-input"
        placeholder="your@email.com"
        id="emailInput"
        aria-label="Email address"
      />
      <button class="btn-primary" onclick="handleSubscribe()">Subscribe</button>
    </div>
    <div class="newsletter-offer">
      🎁 Get 15% off your first order when you subscribe
    </div>
  </div>
</section>

<!-- ========================= FOOTER ========================= -->
<footer class="footer" id="contact">
  <div class="footer-grid">
    <div class="footer-brand">
      <div class="footer-logo">SAPPHIRE</div>
      <p class="footer-desc">
        Crafting timeless fashion with an edge. Every piece is designed to
        make you feel seen, celebrated, and unstoppable.
      </p>
      <div class="social-links">
        <a class="social-btn" href="#" aria-label="Instagram">📷</a>
        <a class="social-btn" href="#" aria-label="Facebook">👍</a>
        <a class="social-btn" href="#" aria-label="Pinterest">📌</a>
        <a class="social-btn" href="#" aria-label="Twitter">🐦</a>
      </div>
    </div>

    <div>
      <div class="footer-col-title">Shop</div>
      <ul class="footer-links">
        <li><a href="#products">New Arrivals</a></li>
        <li><a href="#products">Dresses</a></li>
        <li><a href="#products">Tops</a></li>
        <li><a href="#products">Accessories</a></li>
        <li><a href="#deals">Sale</a></li>
      </ul>
    </div>

    <div>
      <div class="footer-col-title">Support</div>
      <ul class="footer-links">
        <li><a href="#">Size Guide</a></li>
        <li><a href="#">Track Order</a></li>
        <li><a href="#">Returns</a></li>
        <li><a href="#">FAQs</a></li>
        <li><a href="#">Contact Us</a></li>
      </ul>
    </div>

    <div>
      <div class="footer-col-title">Brand</div>
      <ul class="footer-links">
        <li><a href="#">Our Story</a></li>
        <li><a href="#">Sustainability</a></li>
        <li><a href="#">Press</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Affiliates</a></li>
      </ul>
    </div>
  </div>

  <hr class="footer-divider" />

  <div class="footer-bottom">
    <p class="footer-copy">© 2026 SAPPHIRE. All rights reserved. Made with ♥ in India.</p>
    <div class="footer-legal">
      <a href="#">Privacy Policy</a>
      <a href="#">Terms of Service</a>
      <a href="#">Cookie Settings</a>
    </div>
  </div>
</footer>

<!-- ========================= TOAST ========================= -->
<div class="toast" id="toast" role="alert" aria-live="polite"></div>

<!-- ========================= BACK TO TOP ========================= -->
<button class="back-top" id="backTop" aria-label="Back to top" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button>

<!-- ========================= JAVASCRIPT ========================= -->
<script>
  // ─── Products Data ───────────────────────────────────────────
  const products = [
    {
      id:1, name:'Azure Silk Drape', category:'dresses',
      emoji:'👗', color:'linear-gradient(145deg, #dceef8 0%, #7fb3d0 100%)',
      price:4299, original:5999, discount:28, tag:'new',
      rating:'★★★★★', reviews:842
    },
    {
      id:2, name:'Indigo Pleated Maxi', category:'dresses',
      emoji:'🌊', color:'linear-gradient(145deg, #c8d8f0 0%, #5070a0 100%)',
      price:3499, original:4500, discount:22, tag:'hot',
      rating:'★★★★★', reviews:1203
    },
    {
      id:3, name:'Pearl Linen Shirt', category:'tops',
      emoji:'👔', color:'linear-gradient(145deg, #f5efe0 0%, #d4bc95 100%)',
      price:1299, original:1800, discount:28, tag:'bestseller',
      rating:'★★★★☆', reviews:677
    },
    {
      id:4, name:'Sapphire Blazer Set', category:'tops',
      emoji:'🥻', color:'linear-gradient(145deg, #d5c4e8 0%, #8056a0 100%)',
      price:5499, original:7200, discount:24, tag:'new',
      rating:'★★★★★', reviews:389
    },
    {
      id:5, name:'Cobalt Wide-Leg', category:'pants',
      emoji:'👖', color:'linear-gradient(145deg, #d0e4f0 0%, #4080a8 100%)',
      price:2199, original:2800, discount:21, tag:'trending',
      rating:'★★★★★', reviews:544
    },
    {
      id:6, name:'Gold Chain Tote', category:'accessories',
      emoji:'👜', color:'linear-gradient(145deg, #f9ead0 0%, #c89850 100%)',
      price:3799, original:5500, discount:31, tag:'hot',
      rating:'★★★★★', reviews:991
    },
    {
      id:7, name:'Coral Linen Co-ord', category:'sale',
      emoji:'🧡', color:'linear-gradient(145deg, #ffe4d0 0%, #e07840 100%)',
      price:1899, original:3500, discount:46, tag:'hot',
      rating:'★★★★☆', reviews:722
    },
    {
      id:8, name:'Diamond Silk Scarf', category:'accessories',
      emoji:'💎', color:'linear-gradient(145deg, #e8f0f8 0%, #b0c8e0 100%)',
      price:899, original:1200, discount:25, tag:'bestseller',
      rating:'★★★★★', reviews:1560
    },
  ];

  let cartCount = 0;
  let activeFilter = 'all';

  const tagLabels = { new:'New', hot:'🔥 Hot', bestseller:'Bestseller', trending:'Trending', sale:'Sale' };
  const tagClasses = { new:'tag-new', hot:'tag-hot', bestseller:'tag-bestseller', trending:'tag-trending', sale:'tag-hot' };

  function renderProducts(data) {
    const grid = document.getElementById('productsGrid');
    grid.innerHTML = '';
    if (!data.length) {
      grid.innerHTML = '<p style="color:var(--text-muted);font-family:DM Sans,sans-serif;padding:2rem 0;">No products found in this category.</p>';
      return;
    }
    data.forEach((p, i) => {
      const card = document.createElement('div');
      card.className = 'product-card fade-up';
      card.innerHTML = `
        <div class="product-img-wrap">
          <div class="product-img-bg" style="background:${p.color}">${p.emoji}</div>
          <span class="product-tag ${tagClasses[p.tag]}">${tagLabels[p.tag]}</span>
          <button class="wishlist-btn" onclick="toggleWish(this, event)" aria-label="Add to wishlist">🤍</button>
          <button class="quick-add" onclick="addToCart(${p.id}, event)">+ Add to Cart</button>
        </div>
        <div class="product-info">
          <div class="product-category">${p.category}</div>
          <div class="product-name">${p.name}</div>
          <div class="product-rating">
            <span class="stars">${p.rating}</span>
            <span class="rating-count">(${p.reviews.toLocaleString()})</span>
          </div>
          <div class="product-price-row">
            <div>
              <span class="price-current">₹${p.price.toLocaleString()}</span>
              <span class="price-original">₹${p.original.toLocaleString()}</span>
            </div>
            <span class="price-discount">-${p.discount}%</span>
          </div>
        </div>`;
      grid.appendChild(card);
    });
    observeFadeEls();
  }

  function filterProducts(btn, cat) {
    document.querySelectorAll('.pill').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    activeFilter = cat;
    const filtered = cat === 'all' ? products : products.filter(p => p.category === cat);
    renderProducts(filtered);
  }

  function toggleWish(btn, e) {
    e.stopPropagation();
    btn.classList.toggle('liked');
    btn.textContent = btn.classList.contains('liked') ? '❤️' : '🤍';
    showToast(btn.classList.contains('liked') ? '❤️ Added to wishlist!' : 'Removed from wishlist');
  }

  function addToCart(id, e) {
    if (e) e.stopPropagation();
    cartCount++;
    document.getElementById('cartCount').textContent = cartCount;
    const p = products.find(pr => pr.id === id);
    showToast(`🛒 ${p ? p.name : 'Item'} added to cart!`);
  }

  // ─── Toast ───────────────────────────────────────────────────
  let toastTimer;
  function showToast(msg) {
    const toast = document.getElementById('toast');
    toast.textContent = msg;
    toast.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(() => toast.classList.remove('show'), 3000);
  }

  // ─── Countdown Timer ─────────────────────────────────────────
  function startCountdown() {
    const endTime = Date.now() + 8 * 3600 * 1000 + 47 * 60 * 1000;
    function tick() {
      const diff = endTime - Date.now();
      if (diff <= 0) {
        document.getElementById('countdown').textContent = '00:00:00';
        return;
      }
      const h = Math.floor(diff / 3600000);
      const m = Math.floor((diff % 3600000) / 60000);
      const s = Math.floor((diff % 60000) / 1000);
      document.getElementById('countdown').textContent =
        `${String(h).padStart(2,'0')}:${String(m).padStart(2,'0')}:${String(s).padStart(2,'0')}`;
      requestAnimationFrame(tick);
    }
    tick();
  }

  // ─── Theme Toggle ─────────────────────────────────────────────
  const themeToggle = document.getElementById('themeToggle');
  let isDark = false;
  themeToggle.addEventListener('click', () => {
    isDark = !isDark;
    document.documentElement.setAttribute('data-theme', isDark ? 'dark' : 'light');
    themeToggle.textContent = isDark ? '☀️' : '🌙';
  });

  // ─── Hamburger ────────────────────────────────────────────────
  const hamburger = document.getElementById('hamburger');
  const mobileMenu = document.getElementById('mobileMenu');
  hamburger.addEventListener('click', () => {
    mobileMenu.classList.toggle('open');
  });
  mobileMenu.querySelectorAll('a').forEach(a => {
    a.addEventListener('click', () => mobileMenu.classList.remove('open'));
  });

  // ─── Back to Top ──────────────────────────────────────────────
  const backTop = document.getElementById('backTop');
  window.addEventListener('scroll', () => {
    backTop.classList.toggle('visible', window.scrollY > 400);
  }, { passive: true });

  // ─── Fade-in on Scroll ────────────────────────────────────────
  function observeFadeEls() {
    const els = document.querySelectorAll('.fade-up:not(.observed)');
    const obs = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          obs.unobserve(e.target);
        }
      });
    }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });
    els.forEach(el => { el.classList.add('observed'); obs.observe(el); });
  }

  // ─── Newsletter ───────────────────────────────────────────────
  function handleSubscribe() {
    const input = document.getElementById('emailInput');
    const val = input.value.trim();
    if (!val || !val.includes('@')) {
      showToast('⚠️ Please enter a valid email address.');
      input.focus();
      return;
    }
    showToast('🎉 Welcome! Your 15% discount is on its way!');
    input.value = '';
  }

  document.getElementById('emailInput').addEventListener('keypress', e => {
    if (e.key === 'Enter') handleSubscribe();
  });

  // ─── Scroll Helpers ───────────────────────────────────────────
  function scrollToProducts() {
    document.getElementById('products').scrollIntoView({ behavior: 'smooth' });
  }

  function scrollToSection(id) {
    document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
  }

  // ─── Init ─────────────────────────────────────────────────────
  document.addEventListener('DOMContentLoaded', () => {
    renderProducts(products);
    startCountdown();
    observeFadeEls();
  });
</script>
</body>
</html>

