<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Blooming Smoothies 🌺</title>
<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root {
    --pink: #e8206a;
    --magenta: #c0145c;
    --green: #2d8a35;
    --lime: #5cb85c;
    --orange: #f5a623;
    --purple: #7b5ea7;
    --yellow: #f5d020;
    --cream: #fffbf0;
    --dark: #1a1a2e;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Nunito', sans-serif;
    background: var(--cream);
    color: var(--dark);
    overflow-x: hidden;
    cursor: none;
  }

  /* CUSTOM CURSOR */
  .cursor {
    width: 20px; height: 20px;
    background: var(--pink);
    border-radius: 50%;
    position: fixed;
    top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform 0.1s ease, width 0.2s, height 0.2s, background 0.2s;
    mix-blend-mode: multiply;
  }
  .cursor-ring {
    width: 40px; height: 40px;
    border: 2px solid var(--pink);
    border-radius: 50%;
    position: fixed;
    top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: left 0.08s ease, top 0.08s ease;
    opacity: 0.5;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; width: 100%;
    z-index: 1000;
    padding: 18px 60px;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(255,251,240,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 2px solid rgba(232,32,106,0.12);
  }
  .nav-logo {
    font-family: 'Pacifico', cursive;
    font-size: 1.6rem;
    color: var(--pink);
    letter-spacing: -0.5px;
  }
  .nav-logo span { color: var(--green); }
  nav ul { list-style: none; display: flex; gap: 36px; }
  nav ul li a {
    text-decoration: none;
    font-weight: 800;
    font-size: 0.9rem;
    color: var(--dark);
    letter-spacing: 0.5px;
    text-transform: uppercase;
    transition: color 0.2s;
    position: relative;
  }
  nav ul li a::after {
    content: '';
    position: absolute; bottom: -4px; left: 0;
    width: 0; height: 3px;
    background: var(--pink);
    border-radius: 2px;
    transition: width 0.3s;
  }
  nav ul li a:hover { color: var(--pink); }
  nav ul li a:hover::after { width: 100%; }
  .nav-cta {
    background: var(--pink);
    color: white !important;
    padding: 10px 24px;
    border-radius: 50px;
    font-weight: 800 !important;
    transition: transform 0.2s, box-shadow 0.2s !important;
    box-shadow: 0 4px 15px rgba(232,32,106,0.35);
  }
  .nav-cta:hover { transform: translateY(-2px) !important; box-shadow: 0 8px 25px rgba(232,32,106,0.45) !important; }
  .nav-cta::after { display: none !important; }

  /* HERO */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center;
    position: relative;
    overflow: hidden;
    padding: 120px 60px 80px;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 70% at 70% 40%, rgba(245,166,35,0.18) 0%, transparent 60%),
                radial-gradient(ellipse 60% 60% at 20% 60%, rgba(232,32,106,0.13) 0%, transparent 60%),
                radial-gradient(ellipse 50% 50% at 80% 80%, rgba(92,184,92,0.12) 0%, transparent 50%),
                var(--cream);
  }
  /* Floating blobs */
  .blob {
    position: absolute;
    border-radius: 50%;
    filter: blur(60px);
    opacity: 0.35;
    animation: blobFloat 8s ease-in-out infinite alternate;
  }
  .blob-1 { width: 400px; height: 400px; background: var(--pink); top: -100px; right: -100px; animation-delay: 0s; }
  .blob-2 { width: 300px; height: 300px; background: var(--orange); bottom: 0; left: -100px; animation-delay: 2s; }
  .blob-3 { width: 200px; height: 200px; background: var(--lime); top: 50%; left: 40%; animation-delay: 4s; }

  @keyframes blobFloat {
    0% { transform: translate(0, 0) scale(1); }
    100% { transform: translate(30px, -30px) scale(1.1); }
  }

  .hero-content {
    position: relative; z-index: 2;
    max-width: 600px;
    animation: fadeUp 1s ease both;
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(40px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .hero-badge {
    display: inline-block;
    background: linear-gradient(135deg, var(--green), var(--lime));
    color: white;
    font-size: 0.75rem;
    font-weight: 900;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 8px 20px;
    border-radius: 50px;
    margin-bottom: 24px;
    box-shadow: 0 4px 15px rgba(45,138,53,0.3);
    animation: fadeUp 1s 0.1s ease both;
  }

  h1 {
    font-family: 'Pacifico', cursive;
    font-size: clamp(3.5rem, 7vw, 6rem);
    line-height: 1.05;
    color: var(--dark);
    margin-bottom: 12px;
    animation: fadeUp 1s 0.2s ease both;
  }
  h1 .accent { color: var(--pink); }
  h1 .accent2 { color: var(--green); }

  .hero-sub {
    font-size: 1.2rem;
    font-weight: 600;
    color: #555;
    line-height: 1.7;
    margin-bottom: 40px;
    max-width: 480px;
    animation: fadeUp 1s 0.3s ease both;
  }

  .hero-buttons {
    display: flex; gap: 16px; flex-wrap: wrap;
    animation: fadeUp 1s 0.4s ease both;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--pink), var(--magenta));
    color: white;
    padding: 16px 36px;
    border-radius: 50px;
    font-weight: 800;
    font-size: 1rem;
    text-decoration: none;
    box-shadow: 0 8px 30px rgba(232,32,106,0.4);
    transition: transform 0.2s, box-shadow 0.2s;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-primary:hover { transform: translateY(-4px); box-shadow: 0 14px 40px rgba(232,32,106,0.5); }
  .btn-secondary {
    background: white;
    color: var(--dark);
    padding: 16px 36px;
    border-radius: 50px;
    font-weight: 800;
    font-size: 1rem;
    text-decoration: none;
    border: 2px solid rgba(0,0,0,0.1);
    transition: transform 0.2s, border-color 0.2s;
    box-shadow: 0 4px 15px rgba(0,0,0,0.06);
  }
  .btn-secondary:hover { transform: translateY(-4px); border-color: var(--pink); }

  .hero-visual {
    position: absolute;
    right: 5%;
    top: 50%;
    transform: translateY(-50%);
    animation: heroFloat 6s ease-in-out infinite;
  }
  @keyframes heroFloat {
    0%, 100% { transform: translateY(-50%) rotate(-2deg); }
    50% { transform: translateY(calc(-50% - 20px)) rotate(2deg); }
  }
  .hero-circle {
    width: 520px; height: 520px;
    background: radial-gradient(circle at 35% 35%, rgba(255,255,255,0.9), rgba(245,166,35,0.2), rgba(232,32,106,0.25));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 30px 80px rgba(232,32,106,0.2), inset 0 0 60px rgba(255,255,255,0.5);
    position: relative;
  }
  .hero-emoji-large {
    font-size: 14rem;
    filter: drop-shadow(0 20px 40px rgba(0,0,0,0.15));
    animation: spin3d 12s linear infinite;
  }
  @keyframes spin3d {
    0%,100% { transform: rotateY(0deg); }
    50% { transform: rotateY(20deg); }
  }
  /* Orbiting pills */
  .orbit-pill {
    position: absolute;
    background: white;
    border-radius: 50px;
    padding: 10px 18px;
    font-weight: 800;
    font-size: 0.85rem;
    box-shadow: 0 8px 25px rgba(0,0,0,0.12);
    white-space: nowrap;
    display: flex; align-items: center; gap: 6px;
  }
  .op-1 { top: 5%; left: -8%; background: var(--pink); color: white; animation: float1 5s ease-in-out infinite; }
  .op-2 { bottom: 10%; right: -10%; background: var(--green); color: white; animation: float1 5s 1.5s ease-in-out infinite; }
  .op-3 { top: 50%; left: -14%; background: white; animation: float1 5s 1s ease-in-out infinite; }
  .op-4 { top: 15%; right: -5%; background: var(--orange); color: white; animation: float1 5s 2s ease-in-out infinite; }
  @keyframes float1 {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-12px); }
  }

  /* STATS BAR */
  .stats-bar {
    background: linear-gradient(135deg, var(--dark), #2d1b4e);
    color: white;
    padding: 30px 60px;
    display: flex; justify-content: space-around; align-items: center;
    gap: 20px; flex-wrap: wrap;
  }
  .stat-item { text-align: center; }
  .stat-num {
    font-family: 'Pacifico', cursive;
    font-size: 2.4rem;
    color: var(--orange);
    display: block;
  }
  .stat-label { font-size: 0.85rem; font-weight: 600; color: rgba(255,255,255,0.65); text-transform: uppercase; letter-spacing: 1px; }
  .stat-divider { width: 1px; height: 60px; background: rgba(255,255,255,0.1); }

  /* SECTION STYLES */
  section { padding: 100px 60px; }
  .section-label {
    font-size: 0.75rem;
    font-weight: 900;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--pink);
    margin-bottom: 12px;
    display: block;
  }
  .section-title {
    font-family: 'Pacifico', cursive;
    font-size: clamp(2.2rem, 4vw, 3.2rem);
    line-height: 1.1;
    margin-bottom: 16px;
  }
  .section-subtitle {
    font-size: 1.05rem;
    color: #666;
    font-weight: 600;
    line-height: 1.7;
    max-width: 560px;
  }

  /* ABOUT */
  #about {
    background: white;
    position: relative;
    overflow: hidden;
  }
  #about::before {
    content: '';
    position: absolute;
    top: -200px; right: -200px;
    width: 600px; height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(232,32,106,0.06) 0%, transparent 70%);
  }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
    max-width: 1200px;
    margin: 60px auto 0;
  }
  .about-cards { display: flex; flex-direction: column; gap: 20px; }
  .about-card {
    background: var(--cream);
    border-radius: 24px;
    padding: 28px 32px;
    display: flex;
    gap: 20px;
    align-items: flex-start;
    border: 2px solid transparent;
    transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
    position: relative;
    overflow: hidden;
  }
  .about-card:hover { border-color: var(--pink); transform: translateX(8px); box-shadow: 0 10px 35px rgba(232,32,106,0.1); }
  .about-icon {
    width: 52px; height: 52px;
    border-radius: 16px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.5rem;
    flex-shrink: 0;
  }
  .ai-green { background: rgba(45,138,53,0.12); }
  .ai-pink { background: rgba(232,32,106,0.1); }
  .ai-orange { background: rgba(245,166,35,0.15); }
  .about-card h3 { font-size: 1.05rem; font-weight: 900; margin-bottom: 6px; }
  .about-card p { font-size: 0.9rem; color: #666; font-weight: 600; line-height: 1.6; }

  .about-visual {
    position: relative;
    height: 500px;
  }
  .about-main-card {
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 320px;
    background: linear-gradient(145deg, #fff5f8, #fff0e6);
    border-radius: 32px;
    padding: 40px 32px;
    text-align: center;
    box-shadow: 0 30px 80px rgba(232,32,106,0.15);
    border: 2px solid rgba(232,32,106,0.08);
  }
  .about-main-emoji { font-size: 5rem; margin-bottom: 16px; display: block; animation: heroFloat 4s ease-in-out infinite; }
  .about-main-card h3 { font-family: 'Pacifico', cursive; font-size: 1.8rem; color: var(--pink); margin-bottom: 8px; }
  .about-main-card p { font-size: 0.9rem; color: #777; font-weight: 600; line-height: 1.6; }
  .about-badge {
    position: absolute;
    background: linear-gradient(135deg, var(--green), var(--lime));
    color: white;
    border-radius: 20px;
    padding: 14px 20px;
    font-weight: 800;
    font-size: 0.85rem;
    text-align: center;
    box-shadow: 0 8px 25px rgba(45,138,53,0.3);
  }
  .ab-1 { top: 5%; left: 0; animation: float1 4s ease-in-out infinite; }
  .ab-2 { bottom: 5%; right: 0; animation: float1 4s 1s ease-in-out infinite; background: linear-gradient(135deg, var(--pink), var(--magenta)); box-shadow: 0 8px 25px rgba(232,32,106,0.3); }
  .ab-3 { top: 50%; right: -5%; transform: translateY(-50%); animation: float1 4s 2s ease-in-out infinite; background: linear-gradient(135deg, var(--orange), #f5a623cc); box-shadow: 0 8px 25px rgba(245,166,35,0.3); }

  /* MENU */
  #menu {
    background: linear-gradient(180deg, var(--cream) 0%, #fff5f0 100%);
    position: relative;
  }
  .menu-header { text-align: center; margin-bottom: 60px; }
  .menu-header .section-label { justify-content: center; display: flex; }
  .menu-tabs {
    display: flex;
    justify-content: center;
    gap: 12px;
    margin-top: 32px;
    flex-wrap: wrap;
  }
  .tab-btn {
    padding: 10px 28px;
    border-radius: 50px;
    border: 2px solid rgba(0,0,0,0.08);
    background: white;
    font-family: 'Nunito', sans-serif;
    font-weight: 800;
    font-size: 0.9rem;
    cursor: none;
    transition: all 0.2s;
  }
  .tab-btn.active, .tab-btn:hover { background: var(--pink); color: white; border-color: var(--pink); }
  .menu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 24px;
    max-width: 1200px;
    margin: 0 auto;
  }
  .menu-card {
    background: white;
    border-radius: 28px;
    overflow: hidden;
    box-shadow: 0 8px 30px rgba(0,0,0,0.06);
    transition: transform 0.3s, box-shadow 0.3s;
    position: relative;
  }
  .menu-card:hover { transform: translateY(-10px); box-shadow: 0 20px 50px rgba(232,32,106,0.15); }
  .menu-card-img {
    height: 180px;
    display: flex; align-items: center; justify-content: center;
    font-size: 5rem;
    position: relative;
    overflow: hidden;
  }
  .mc-pink { background: linear-gradient(135deg, #ffe0ed, #ffd0e8); }
  .mc-green { background: linear-gradient(135deg, #e0f5e0, #d0f0d0); }
  .mc-orange { background: linear-gradient(135deg, #fff0d0, #ffe8b8); }
  .mc-purple { background: linear-gradient(135deg, #ede0f5, #e0d0f0); }
  .mc-yellow { background: linear-gradient(135deg, #fff8d0, #fff0b0); }
  .mc-blue { background: linear-gradient(135deg, #d0eaf5, #c0e0f0); }
  .menu-tag {
    position: absolute; top: 14px; right: 14px;
    background: var(--pink); color: white;
    font-size: 0.7rem; font-weight: 900;
    padding: 4px 12px; border-radius: 50px;
    text-transform: uppercase; letter-spacing: 1px;
  }
  .menu-tag.vegan { background: var(--green); }
  .menu-tag.new { background: var(--orange); color: white; }
  .menu-body { padding: 22px 24px 24px; }
  .menu-body h3 { font-weight: 900; font-size: 1.1rem; margin-bottom: 6px; }
  .menu-body p { font-size: 0.85rem; color: #888; font-weight: 600; line-height: 1.5; margin-bottom: 16px; }
  .menu-footer { display: flex; align-items: center; justify-content: space-between; }
  .price {
    font-family: 'Pacifico', cursive;
    font-size: 1.4rem;
    color: var(--pink);
  }
  .add-btn {
    width: 36px; height: 36px;
    background: var(--pink);
    color: white;
    border: none;
    border-radius: 50%;
    font-size: 1.3rem;
    cursor: none;
    display: flex; align-items: center; justify-content: center;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 12px rgba(232,32,106,0.35);
  }
  .add-btn:hover { transform: scale(1.15); box-shadow: 0 6px 20px rgba(232,32,106,0.5); }

  /* MISSION */
  #mission {
    background: linear-gradient(145deg, var(--dark), #0f2318);
    color: white;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  #mission::before {
    content: '🌿';
    position: absolute;
    font-size: 30rem;
    opacity: 0.04;
    top: -100px; left: -80px;
    filter: grayscale(1);
  }
  #mission .section-label { color: var(--lime); }
  #mission .section-title { color: white; }
  .mission-content { position: relative; z-index: 2; }
  .mission-quote {
    font-size: clamp(1.2rem, 2.5vw, 1.7rem);
    font-weight: 700;
    line-height: 1.7;
    max-width: 800px;
    margin: 0 auto 60px;
    color: rgba(255,255,255,0.85);
  }
  .mission-quote span { color: var(--orange); }
  .mission-pillars {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 24px;
    max-width: 1000px;
    margin: 0 auto;
  }
  .pillar {
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 24px;
    padding: 32px 24px;
    transition: background 0.3s, transform 0.3s;
  }
  .pillar:hover { background: rgba(255,255,255,0.1); transform: translateY(-6px); }
  .pillar-icon { font-size: 2.5rem; margin-bottom: 14px; display: block; }
  .pillar h3 { font-weight: 900; font-size: 1rem; margin-bottom: 8px; color: white; }
  .pillar p { font-size: 0.85rem; color: rgba(255,255,255,0.6); font-weight: 600; line-height: 1.6; }

  /* PRICING */
  #pricing { background: white; }
  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
    max-width: 1000px;
    margin: 60px auto 0;
  }
  .price-card {
    border-radius: 32px;
    padding: 40px 36px;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s;
  }
  .price-card:hover { transform: translateY(-8px); }
  .pc-standard {
    background: var(--cream);
    border: 2px solid rgba(0,0,0,0.06);
  }
  .pc-featured {
    background: linear-gradient(145deg, var(--pink), var(--magenta));
    color: white;
    box-shadow: 0 30px 70px rgba(232,32,106,0.4);
    transform: scale(1.04);
  }
  .pc-featured:hover { transform: scale(1.04) translateY(-8px); }
  .pc-eco {
    background: linear-gradient(145deg, var(--green), #1e6b26);
    color: white;
    box-shadow: 0 30px 70px rgba(45,138,53,0.3);
  }
  .price-badge {
    position: absolute; top: 20px; right: 20px;
    background: var(--orange); color: white;
    font-size: 0.7rem; font-weight: 900; padding: 4px 12px;
    border-radius: 50px; text-transform: uppercase; letter-spacing: 1px;
  }
  .price-icon { font-size: 2.5rem; margin-bottom: 16px; display: block; }
  .price-category { font-size: 0.8rem; font-weight: 900; letter-spacing: 2px; text-transform: uppercase; opacity: 0.6; margin-bottom: 6px; }
  .price-card h3 { font-weight: 900; font-size: 1.3rem; margin-bottom: 20px; }
  .price-amount {
    font-family: 'Pacifico', cursive;
    font-size: 3rem;
    line-height: 1;
    margin-bottom: 6px;
    display: block;
  }
  .price-note { font-size: 0.8rem; font-weight: 600; opacity: 0.65; margin-bottom: 28px; }
  .price-features { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .price-features li { font-size: 0.9rem; font-weight: 700; display: flex; align-items: center; gap: 10px; }
  .price-features li::before { content: '✓'; font-size: 1rem; width: 22px; height: 22px; background: rgba(255,255,255,0.2); border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .pc-standard .price-features li::before { background: rgba(45,138,53,0.15); color: var(--green); }

  /* AUDIENCE */
  #audience {
    background: linear-gradient(180deg, #fff5f0 0%, var(--cream) 100%);
  }
  .audience-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
    max-width: 1200px;
    margin: 60px auto 0;
  }
  .audience-cards { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .aud-card {
    background: white;
    border-radius: 24px;
    padding: 28px 22px;
    text-align: center;
    box-shadow: 0 6px 25px rgba(0,0,0,0.06);
    transition: transform 0.3s;
    border: 2px solid transparent;
  }
  .aud-card:hover { transform: translateY(-6px); border-color: var(--pink); }
  .aud-card .aud-emoji { font-size: 3rem; display: block; margin-bottom: 12px; }
  .aud-card h3 { font-weight: 900; font-size: 0.95rem; margin-bottom: 6px; }
  .aud-card p { font-size: 0.8rem; color: #888; font-weight: 600; line-height: 1.5; }
  .audience-text .section-subtitle { margin-bottom: 30px; }
  .location-card {
    background: linear-gradient(135deg, var(--pink), var(--magenta));
    color: white;
    border-radius: 24px;
    padding: 28px 32px;
    box-shadow: 0 16px 50px rgba(232,32,106,0.3);
  }
  .location-card h3 { font-weight: 900; font-size: 1.1rem; margin-bottom: 10px; }
  .location-card p { font-size: 0.9rem; font-weight: 600; line-height: 1.6; opacity: 0.9; }
  .location-flag { font-size: 1.5rem; margin-right: 8px; }

  /* MARKETING */
  #marketing { background: white; }
  .marketing-flex {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
    max-width: 1200px;
    margin: 60px auto 0;
  }
  .social-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .social-card {
    border-radius: 24px;
    padding: 28px 24px;
    position: relative;
    overflow: hidden;
    transition: transform 0.3s;
    cursor: none;
  }
  .social-card:hover { transform: translateY(-6px) rotate(-1deg); }
  .sc-ig { background: linear-gradient(135deg, #f09433 0%,#e6683c 25%,#dc2743 50%,#cc2366 75%,#bc1888 100%); color: white; }
  .sc-tk { background: linear-gradient(135deg, #010101, #69C9D0); color: white; }
  .sc-yt { background: linear-gradient(135deg, #FF0000, #CC0000); color: white; }
  .sc-bb { background: linear-gradient(135deg, #4267B2, #1a1a2e); color: white; }
  .social-icon { font-size: 2.2rem; display: block; margin-bottom: 10px; }
  .social-card h3 { font-weight: 900; font-size: 1rem; margin-bottom: 4px; }
  .social-card p { font-size: 0.8rem; font-weight: 600; opacity: 0.8; line-height: 1.4; }
  .marketing-text .section-subtitle { margin-bottom: 32px; }
  .marketing-steps { display: flex; flex-direction: column; gap: 18px; }
  .mstep {
    display: flex; align-items: flex-start; gap: 16px;
  }
  .mstep-num {
    width: 36px; height: 36px;
    background: linear-gradient(135deg, var(--pink), var(--magenta));
    color: white;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-weight: 900; font-size: 0.9rem;
    flex-shrink: 0;
    box-shadow: 0 4px 15px rgba(232,32,106,0.3);
  }
  .mstep-text h4 { font-weight: 900; font-size: 0.95rem; margin-bottom: 4px; }
  .mstep-text p { font-size: 0.85rem; color: #888; font-weight: 600; line-height: 1.5; }

  /* CTA */
  #cta {
    background: linear-gradient(135deg, var(--pink) 0%, #c0145c 40%, #7b1fa2 100%);
    color: white;
    text-align: center;
    padding: 100px 60px;
    position: relative;
    overflow: hidden;
  }
  #cta::after {
    content: '';
    position: absolute; inset: 0;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.04'%3E%3Ccircle cx='30' cy='30' r='20'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }
  .cta-content { position: relative; z-index: 2; }
  #cta .section-label { color: rgba(255,255,255,0.7); }
  #cta h2 {
    font-family: 'Pacifico', cursive;
    font-size: clamp(2.5rem, 5vw, 4rem);
    margin-bottom: 16px;
  }
  #cta p { font-size: 1.1rem; font-weight: 600; max-width: 500px; margin: 0 auto 40px; opacity: 0.85; line-height: 1.7; }
  .cta-form {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
    max-width: 480px;
    margin: 0 auto;
  }
  .cta-input {
    flex: 1;
    min-width: 220px;
    padding: 16px 24px;
    border-radius: 50px;
    border: none;
    font-family: 'Nunito', sans-serif;
    font-size: 0.95rem;
    font-weight: 700;
    outline: none;
    box-shadow: 0 4px 20px rgba(0,0,0,0.2);
  }
  .cta-submit {
    background: var(--orange);
    color: white;
    padding: 16px 32px;
    border-radius: 50px;
    border: none;
    font-family: 'Nunito', sans-serif;
    font-weight: 900;
    font-size: 0.95rem;
    cursor: none;
    box-shadow: 0 8px 25px rgba(245,166,35,0.5);
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .cta-submit:hover { transform: translateY(-3px); box-shadow: 0 12px 35px rgba(245,166,35,0.6); }

  /* FOOTER */
  footer {
    background: var(--dark);
    color: white;
    padding: 60px 60px 32px;
  }
  .footer-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 40px;
    margin-bottom: 48px;
  }
  .footer-brand .nav-logo { font-size: 2rem; display: block; margin-bottom: 14px; }
  .footer-brand p { font-size: 0.88rem; color: rgba(255,255,255,0.5); line-height: 1.7; font-weight: 600; max-width: 260px; }
  .footer-socials { display: flex; gap: 10px; margin-top: 20px; }
  .fsoc {
    width: 38px; height: 38px;
    background: rgba(255,255,255,0.08);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem;
    transition: background 0.2s, transform 0.2s;
    cursor: none;
  }
  .fsoc:hover { background: var(--pink); transform: translateY(-3px); }
  .footer-col h4 { font-weight: 900; font-size: 0.85rem; letter-spacing: 1px; text-transform: uppercase; color: rgba(255,255,255,0.4); margin-bottom: 18px; }
  .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
  .footer-col ul li a { text-decoration: none; color: rgba(255,255,255,0.65); font-weight: 600; font-size: 0.9rem; transition: color 0.2s; }
  .footer-col ul li a:hover { color: var(--orange); }
  .footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.08);
    padding-top: 28px;
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 12px;
  }
  .footer-bottom p { font-size: 0.82rem; color: rgba(255,255,255,0.35); font-weight: 600; }
  .eco-badge {
    display: flex; align-items: center; gap: 8px;
    background: rgba(45,138,53,0.2);
    border: 1px solid rgba(92,184,92,0.3);
    padding: 8px 16px;
    border-radius: 50px;
    font-size: 0.8rem;
    font-weight: 700;
    color: var(--lime);
  }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  @media (max-width: 900px) {
    nav { padding: 16px 24px; }
    nav ul { display: none; }
    section { padding: 70px 24px; }
    #hero { padding: 120px 24px 60px; }
    .hero-visual { display: none; }
    .about-grid, .audience-grid, .marketing-flex, .footer-grid { grid-template-columns: 1fr; gap: 40px; }
    .stats-bar { padding: 24px; }
    .stat-divider { display: none; }
    h1 { font-size: 3rem; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">🌺 Bloom<span>ing</span></div>
  <ul>
    <li><a href="#about">About</a></li>
    <li><a href="#menu">Menu</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#audience">Community</a></li>
    <li><a href="#marketing">Find Us</a></li>
    <li><a href="#cta" class="nav-cta">Order Now</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-bg"></div>
  <div class="blob blob-1"></div>
  <div class="blob blob-2"></div>
  <div class="blob blob-3"></div>

  <div class="hero-content">
    <div class="hero-badge">🌱 100% Eco-Friendly • Zero Plastic</div>
    <h1>
      <span class="accent">Bloom</span> into<br>
      <span class="accent2">Health.</span>
    </h1>
    <p class="hero-sub">
      Vibrant smoothies & wholesome snacks made with local ingredients — good for you, kind to the planet. No plastic. Just pure, blooming goodness.
    </p>
    <div class="hero-buttons">
      <a href="#menu" class="btn-primary">🥤 Explore Menu</a>
      <a href="#about" class="btn-secondary">Our Story →</a>
    </div>
  </div>

  <div class="hero-visual">
    <div class="hero-circle">
      <span class="hero-emoji-large">🥤</span>
      <div class="orbit-pill op-1">🌺 No Plastic!</div>
      <div class="orbit-pill op-2">🌿 100% Natural</div>
      <div class="orbit-pill op-3">⭐ From €4.99</div>
      <div class="orbit-pill op-4">🚀 We Deliver!</div>
    </div>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item">
    <span class="stat-num">100%</span>
    <span class="stat-label">Plastic Free</span>
  </div>
  <div class="stat-divider"></div>
  <div class="stat-item">
    <span class="stat-num">€4.99</span>
    <span class="stat-label">Starting Price</span>
  </div>
  <div class="stat-divider"></div>
  <div class="stat-item">
    <span class="stat-num">20+</span>
    <span class="stat-label">Smoothie Flavours</span>
  </div>
  <div class="stat-divider"></div>
  <div class="stat-item">
    <span class="stat-num">🌍</span>
    <span class="stat-label">Going Global</span>
  </div>
  <div class="stat-divider"></div>
  <div class="stat-item">
    <span class="stat-num">0🛒</span>
    <span class="stat-label">Competitors' Quality</span>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="about-grid">
    <div class="reveal">
      <span class="section-label">🌺 Who We Are</span>
      <h2 class="section-title">Born to Bloom,<br>Built to Thrive.</h2>
      <p class="section-subtitle">We're an eco-friendly smoothie & healthy food café on a mission to prove that nourishing your body and protecting the planet can taste absolutely amazing.</p>
      <br><br>
      <div class="about-cards">
        <div class="about-card">
          <div class="about-icon ai-green">🌿</div>
          <div>
            <h3>Zero Plastic Promise</h3>
            <p>Every cup, every lid, every straw — all glass. Walk into any Blooming Smoothies location and you won't find a single piece of plastic.</p>
          </div>
        </div>
        <div class="about-card">
          <div class="about-icon ai-pink">🍓</div>
          <div>
            <h3>Addictively Healthy</h3>
            <p>Our secret? Ingredients that nourish like superfoods but taste like your guilty pleasures. Healthy never felt this good.</p>
          </div>
        </div>
        <div class="about-card">
          <div class="about-icon ai-orange">🚗</div>
          <div>
            <h3>We Come To You</h3>
            <p>Book Blooming Smoothies for your gym, party, business opening, or sports centre. Our smoothies travel to where you need them!</p>
          </div>
        </div>
      </div>
    </div>
    <div class="about-visual reveal">
      <div class="about-badge ab-1">🏆 Best Value<br>in the Area</div>
      <div class="about-main-card">
        <span class="about-main-emoji">🌸</span>
        <h3>Blooming Smoothies</h3>
        <p>An eco-friendly café experience where every sip makes a difference — for you and for the planet.</p>
      </div>
      <div class="about-badge ab-2">🌍 Mission:<br>Zero Waste</div>
      <div class="about-badge ab-3">🥗 Local<br>Ingredients</div>
    </div>
  </div>
</section>

<!-- MENU -->
<section id="menu">
  <div class="menu-header reveal">
    <span class="section-label">🥤 What We Serve</span>
    <h2 class="section-title">Our Menu</h2>
    <p class="section-subtitle" style="margin:0 auto;">From power-packed protein smoothies to fresh snack platters — everything crafted with love and local ingredients.</p>
    <div class="menu-tabs">
      <button class="tab-btn active">All</button>
      <button class="tab-btn">Smoothies</button>
      <button class="tab-btn">Snacks</button>
      <button class="tab-btn">Protein</button>
    </div>
  </div>
  <div class="menu-grid">
    <div class="menu-card reveal">
      <div class="menu-card-img mc-pink">
        <span>🍓</span>
        <span class="menu-tag">Best Seller</span>
      </div>
      <div class="menu-body">
        <h3>Berry Bloom</h3>
        <p>Strawberry, raspberry, blueberry & banana with oat milk. A tropical burst of antioxidants.</p>
        <div class="menu-footer">
          <span class="price">€4.99</span>
          <button class="add-btn">+</button>
        </div>
      </div>
    </div>
    <div class="menu-card reveal">
      <div class="menu-card-img mc-green">
        <span>🥬</span>
        <span class="menu-tag vegan">Vegan</span>
      </div>
      <div class="menu-body">
        <h3>Green Queen</h3>
        <p>Spinach, kale, green apple, cucumber & ginger. Detox never tasted this refreshing.</p>
        <div class="menu-footer">
          <span class="price">€4.99</span>
          <button class="add-btn">+</button>
        </div>
      </div>
    </div>
    <div class="menu-card reveal">
      <div class="menu-card-img mc-orange">
        <span>🍊</span>
        <span class="menu-tag new">New</span>
      </div>
      <div class="menu-body">
        <h3>Citrus Sunrise</h3>
        <p>Orange, mango, turmeric & coconut water. Sunshine in a glass, packed with vitamin C.</p>
        <div class="menu-footer">
          <span class="price">€4.99</span>
          <button class="add-btn">+</button>
        </div>
      </div>
    </div>
    <div class="menu-card reveal">
      <div class="menu-card-img mc-purple">
        <span>💪</span>
        <span class="menu-tag">Protein</span>
      </div>
      <div class="menu-body">
        <h3>Power Bloom</h3>
        <p>Banana, peanut butter, oat milk & plant protein. The gym-goer's best friend.</p>
        <div class="menu-footer">
          <span class="price">€5.99</span>
          <button class="add-btn">+</button>
        </div>
      </div>
    </div>
    <div class="menu-card reveal">
      <div class="menu-card-img mc-yellow">
        <span>🥗</span>
        <span class="menu-tag vegan">Fresh</span>
      </div>
      <div class="menu-body">
        <h3>Garden Salad Toast</h3>
        <p>Sourdough, avocado, cherry tomatoes & micro-greens. A wholesome snack plate.</p>
        <div class="menu-footer">
          <span class="price">€6.99</span>
          <button class="add-btn">+</button>
        </div>
      </div>
    </div>
    <div class="menu-card reveal">
      <div class="menu-card-img mc-blue">
        <span>🍪</span>
        <span class="menu-tag">Snack</span>
      </div>
      <div class="menu-body">
        <h3>Bloom Biscuit Box</h3>
        <p>Assorted healthy oat & seed biscuits. Perfect pre or post-workout energy boost.</p>
        <div class="menu-footer">
          <span class="price">€2.99</span>
          <button class="add-btn">+</button>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- MISSION -->
<section id="mission">
  <div class="mission-content reveal">
    <span class="section-label">🌍 Our Purpose</span>
    <h2 class="section-title" style="color:white;margin-bottom:32px;">We're On a Mission<br>to Change the World</h2>
    <p class="mission-quote">
      Our mission is to <span>reduce plastic waste and unhealthy food all around the world.</span> That's why if you come to any of our locations, you won't see a single piece of plastic — everything is made of glass.
    </p>
    <div class="mission-pillars">
      <div class="pillar">
        <span class="pillar-icon">♻️</span>
        <h3>Zero Plastic</h3>
        <p>100% glass containers. Every single item in our café is plastic-free, always.</p>
      </div>
      <div class="pillar">
        <span class="pillar-icon">🌱</span>
        <h3>Local Sourcing</h3>
        <p>We partner with local farmers and suppliers to reduce our carbon footprint.</p>
      </div>
      <div class="pillar">
        <span class="pillar-icon">💚</span>
        <h3>Healthy Living</h3>
        <p>Combating unhealthy food culture one delicious smoothie at a time.</p>
      </div>
      <div class="pillar">
        <span class="pillar-icon">🌍</span>
        <h3>Global Vision</h3>
        <p>Starting local, dreaming global. Our mission doesn't stop at borders.</p>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section id="pricing">
  <div class="reveal" style="text-align:center;">
    <span class="section-label">💰 Transparent Pricing</span>
    <h2 class="section-title">Great Quality,<br>Fair Prices.</h2>
    <p class="section-subtitle" style="margin:0 auto;">We beat our competitors on both quality and price. No compromises — just pure value.</p>
  </div>
  <div class="pricing-grid">
    <div class="price-card pc-standard reveal">
      <span class="price-icon">🥤</span>
      <div class="price-category">Smoothies</div>
      <h3>Classic Smoothie</h3>
      <span class="price-amount" style="color:var(--pink);">€4.99</span>
      <p class="price-note">4-ingredient fruit blend • vs competitors €7.99</p>
      <ul class="price-features">
        <li>4 fresh fruit ingredients</li>
        <li>Choice of milk base</li>
        <li>Served in glass cup</li>
        <li>Customisable sweetness</li>
      </ul>
    </div>
    <div class="price-card pc-featured reveal">
      <span class="price-badge">Most Popular</span>
      <span class="price-icon">💪</span>
      <div class="price-category" style="color:rgba(255,255,255,0.6)">Protein Boost</div>
      <h3>Protein Smoothie</h3>
      <span class="price-amount">€5.99</span>
      <p class="price-note" style="color:rgba(255,255,255,0.6)">Extra protein • Perfect post-workout</p>
      <ul class="price-features">
        <li>Plant protein added</li>
        <li>Nut butter blend</li>
        <li>High-calorie option</li>
        <li>Gym-partner favourite</li>
      </ul>
    </div>
    <div class="price-card pc-eco reveal">
      <span class="price-icon">🥗</span>
      <div class="price-category" style="color:rgba(255,255,255,0.6)">Snacks</div>
      <h3>Snack Range</h3>
      <span class="price-amount">€2.99–15.99</span>
      <p class="price-note" style="color:rgba(255,255,255,0.6)">Biscuits to full salads & toast plates</p>
      <ul class="price-features">
        <li>Healthy biscuits</li>
        <li>Fresh salads</li>
        <li>Avocado toasts</li>
        <li>Snack platters</li>
      </ul>
    </div>
  </div>
</section>

<!-- AUDIENCE -->
<section id="audience">
  <div class="audience-grid">
    <div class="reveal">
      <span class="section-label">👥 Our Community</span>
      <h2 class="section-title">Made for Everyone<br>Who Moves.</h2>
      <p class="section-subtitle">From kids who love a fruity treat to elite athletes fuelling their performance — Blooming Smoothies is for every body.</p>
      <br>
      <div class="location-card">
        <h3><span class="location-flag">📍</span>Where We Are</h3>
        <p>Currently serving our local community with love. We also welcome holiday visitors who come back again and again. Our next step? Going national and international. The world needs more Blooming Smoothies! 🌍</p>
      </div>
    </div>
    <div class="audience-cards reveal">
      <div class="aud-card">
        <span class="aud-emoji">🧒</span>
        <h3>Kids</h3>
        <p>Fun fruity flavours that make healthy eating exciting for little ones.</p>
      </div>
      <div class="aud-card">
        <span class="aud-emoji">🧑‍🎓</span>
        <h3>Teens</h3>
        <p>Tasty, trendy smoothies that fit the active student lifestyle.</p>
      </div>
      <div class="aud-card">
        <span class="aud-emoji">🏋️</span>
        <h3>Athletes</h3>
        <p>High-protein blends and recovery snacks for peak performance.</p>
      </div>
      <div class="aud-card">
        <span class="aud-emoji">🏢</span>
        <h3>Businesses</h3>
        <p>Book us for your events, openings, and corporate wellness days.</p>
      </div>
    </div>
  </div>
</section>

<!-- MARKETING -->
<section id="marketing">
  <div class="marketing-flex">
    <div class="reveal">
      <span class="section-label">📣 Find Us Everywhere</span>
      <h2 class="section-title">Follow the<br>Bloom.</h2>
      <p class="section-subtitle">We're building a community of health-lovers. Find us on social, watch our ads, or spot our billboards around town.</p>
      <br>
      <div class="marketing-steps">
        <div class="mstep">
          <div class="mstep-num">1</div>
          <div class="mstep-text">
            <h4>Billboards Around Town</h4>
            <p>Look out for our vibrant posters across the local area — you can't miss them!</p>
          </div>
        </div>
        <div class="mstep">
          <div class="mstep-num">2</div>
          <div class="mstep-text">
            <h4>Our App & Online Ordering</h4>
            <p>Download the Blooming Smoothies app for exclusive deals and easy delivery ordering.</p>
          </div>
        </div>
        <div class="mstep">
          <div class="mstep-num">3</div>
          <div class="mstep-text">
            <h4>Influencer & TV Ads</h4>
            <p>We're working with local influencers and planning TV series sponsorships as we grow.</p>
          </div>
        </div>
        <div class="mstep">
          <div class="mstep-num">4</div>
          <div class="mstep-text">
            <h4>In-Game Mobile Ads</h4>
            <p>Reaching the next generation where they play — mobile games and apps.</p>
          </div>
        </div>
      </div>
    </div>
    <div class="social-grid reveal">
      <div class="social-card sc-ig">
        <span class="social-icon">📸</span>
        <h3>Instagram</h3>
        <p>Daily smoothie inspo, behind-the-scenes & giveaways</p>
      </div>
      <div class="social-card sc-tk">
        <span class="social-icon">🎵</span>
        <h3>TikTok</h3>
        <p>Fun recipe videos, challenges & viral content</p>
      </div>
      <div class="social-card sc-yt">
        <span class="social-icon">▶️</span>
        <h3>YouTube</h3>
        <p>Pre-roll ads & recipe tutorials for a wider reach</p>
      </div>
      <div class="social-card sc-bb">
        <span class="social-icon">📱</span>
        <h3>Mobile Games</h3>
        <p>In-game ads targeting the next generation of health fans</p>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section id="cta">
  <div class="cta-content reveal">
    <span class="section-label">🌺 Join the Movement</span>
    <h2>Ready to Bloom?</h2>
    <p>Sign up for exclusive offers, new flavour launches and eco tips delivered fresh to your inbox.</p>
    <div class="cta-form">
      <input type="email" class="cta-input" placeholder="your@email.com">
      <button class="cta-submit">🌸 Subscribe</button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-grid">
    <div class="footer-brand">
      <span class="nav-logo">🌺 Bloom<span>ing</span></span>
      <p>An eco-friendly smoothie & healthy food café on a mission to reduce plastic waste and unhealthy food, one bloom at a time.</p>
      <div class="footer-socials">
        <div class="fsoc">📸</div>
        <div class="fsoc">🎵</div>
        <div class="fsoc">▶️</div>
        <div class="fsoc">📱</div>
      </div>
    </div>
    <div class="footer-col">
      <h4>Menu</h4>
      <ul>
        <li><a href="#">Classic Smoothies</a></li>
        <li><a href="#">Protein Blends</a></li>
        <li><a href="#">Healthy Snacks</a></li>
        <li><a href="#">Salads & Toasts</a></li>
        <li><a href="#">Seasonal Specials</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Company</h4>
      <ul>
        <li><a href="#">Our Story</a></li>
        <li><a href="#">Mission</a></li>
        <li><a href="#">Eco Commitment</a></li>
        <li><a href="#">Careers</a></li>
        <li><a href="#">Press</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Services</h4>
      <ul>
        <li><a href="#">Book for Events</a></li>
        <li><a href="#">Gym Partnerships</a></li>
        <li><a href="#">Delivery App</a></li>
        <li><a href="#">Catering</a></li>
        <li><a href="#">Contact Us</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <p>© 2025 Blooming Smoothies. All rights reserved. Made with 💚 and zero plastic.</p>
    <div class="eco-badge">🌿 Certified Eco-Friendly Business</div>
  </div>
</footer>

<script>
  // CURSOR
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });
  function animRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();
  document.querySelectorAll('a, button, .menu-card, .aud-card, .social-card, .pillar, .about-card').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.width = '40px'; cursor.style.height = '40px'; cursor.style.background = 'var(--orange)'; });
    el.addEventListener('mouseleave', () => { cursor.style.width = '20px'; cursor.style.height = '20px'; cursor.style.background = 'var(--pink)'; });
  });

  // SCROLL REVEAL
  const revealEls = document.querySelectorAll('.reveal');
  const obs = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), 100);
      }
    });
  }, { threshold: 0.1 });
  revealEls.forEach(el => obs.observe(el));

  // TABS
  document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
    });
  });

  // ADD TO CART animation
  document.querySelectorAll('.add-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      btn.textContent = '✓';
      btn.style.background = 'var(--green)';
      setTimeout(() => { btn.textContent = '+'; btn.style.background = 'var(--pink)'; }, 1500);
    });
  });

  // NAV active state
  window.addEventListener('scroll', () => {
    const nav = document.querySelector('nav');
    nav.style.boxShadow = window.scrollY > 50 ? '0 4px 30px rgba(0,0,0,0.08)' : 'none';
  });
</script>
</body>
</html>
