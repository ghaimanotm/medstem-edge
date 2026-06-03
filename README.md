<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MedSTEM Edge</title>
<style>
  :root {
    --navy: #1B3A6B;
    --gold: #C8922A;
    --teal: #1A7A6E;
    --ltgray: #F2F5F8;
    --dark: #1E1E1E;
    --white: #fff;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body { font-family: 'Segoe UI', Arial, sans-serif; color: var(--dark); background: #fff; }

  /* ── NAV ── */
  nav {
    position: sticky; top: 0; z-index: 100;
    background: var(--navy);
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 48px; height: 64px;
    box-shadow: 0 2px 12px rgba(0,0,0,.18);
  }
  .logo { display: flex; align-items: center; gap: 10px; text-decoration: none; }
  .logo-icon {
    width: 38px; height: 38px; border-radius: 8px;
    background: var(--gold); display: flex; align-items: center; justify-content: center;
    font-size: 15px; font-weight: 900; color: #fff; letter-spacing: -1px;
  }
  .logo-text { color: #fff; font-size: 17px; font-weight: 700; line-height: 1.2; }
  .logo-sub { color: var(--gold); font-size: 11px; font-weight: 400; letter-spacing: .5px; }
  .nav-links { display: flex; align-items: center; gap: 28px; }
  .nav-links a { color: rgba(255,255,255,.8); text-decoration: none; font-size: 14px; font-weight: 500; transition: color .15s; }
  .nav-links a:hover { color: var(--gold); }
  .lang-btn {
    background: rgba(255,255,255,.12); border: 1px solid rgba(255,255,255,.25);
    color: #fff; border-radius: 20px; padding: 5px 14px; font-size: 13px; cursor: pointer;
    transition: background .15s;
  }
  .lang-btn:hover { background: rgba(255,255,255,.22); }
  .nav-cta {
    background: var(--gold); color: #fff; border: none; border-radius: 8px;
    padding: 8px 18px; font-size: 14px; font-weight: 600; cursor: pointer;
    text-decoration: none; transition: opacity .15s;
  }
  .nav-cta:hover { opacity: .88; }

  /* ── HERO ── */
  .hero {
    background: linear-gradient(135deg, var(--navy) 0%, #0f2347 60%, #1a4a70 100%);
    padding: 90px 48px 80px;
    display: flex; align-items: center; gap: 64px;
    min-height: 560px; position: relative; overflow: hidden;
  }
  .hero::before {
    content: ''; position: absolute; right: -80px; top: -80px;
    width: 500px; height: 500px; border-radius: 50%;
    background: radial-gradient(circle, rgba(200,146,42,.12) 0%, transparent 70%);
  }
  .hero::after {
    content: 'ሃበሻ'; position: absolute; right: 80px; top: 50%;
    transform: translateY(-50%);
    font-size: 180px; font-weight: 900; color: rgba(255,255,255,.04);
    letter-spacing: -4px; pointer-events: none; user-select: none;
  }
  .hero-content { flex: 1; max-width: 600px; position: relative; z-index: 1; }
  .hero-badge {
    display: inline-block; background: rgba(200,146,42,.2); border: 1px solid rgba(200,146,42,.4);
    color: var(--gold); border-radius: 20px; padding: 5px 14px; font-size: 12px;
    font-weight: 600; letter-spacing: .5px; margin-bottom: 20px;
  }
  .hero h1 {
    color: #fff; font-size: 48px; font-weight: 800; line-height: 1.15;
    margin-bottom: 8px;
  }
  .hero h1 span { color: var(--gold); }
  .hero-am { color: rgba(255,255,255,.5); font-size: 20px; margin-bottom: 20px; font-style: italic; }
  .hero p {
    color: rgba(255,255,255,.75); font-size: 17px; line-height: 1.7;
    margin-bottom: 36px; max-width: 520px;
  }
  .hero-actions { display: flex; gap: 14px; align-items: center; flex-wrap: wrap; }
  .btn-primary {
    background: var(--gold); color: #fff; border: none; border-radius: 10px;
    padding: 14px 28px; font-size: 15px; font-weight: 700; cursor: pointer;
    text-decoration: none; transition: opacity .15s; display: inline-block;
  }
  .btn-primary:hover { opacity: .88; }
  .btn-outline {
    background: transparent; color: #fff;
    border: 1.5px solid rgba(255,255,255,.35); border-radius: 10px;
    padding: 13px 24px; font-size: 15px; font-weight: 600; cursor: pointer;
    text-decoration: none; transition: border-color .15s; display: inline-block;
  }
  .btn-outline:hover { border-color: var(--gold); color: var(--gold); }
  .hero-stats { display: flex; gap: 40px; margin-top: 48px; padding-top: 32px; border-top: 1px solid rgba(255,255,255,.1); }
  .stat-num { color: var(--gold); font-size: 28px; font-weight: 800; }
  .stat-label { color: rgba(255,255,255,.6); font-size: 12px; margin-top: 2px; }

  /* ── TRUST BAR ── */
  .trust-bar {
    background: var(--ltgray); padding: 18px 48px;
    display: flex; align-items: center; gap: 32px; flex-wrap: wrap;
  }
  .trust-label { color: #888; font-size: 12px; font-weight: 600; letter-spacing: .5px; text-transform: uppercase; white-space: nowrap; }
  .trust-items { display: flex; gap: 28px; flex-wrap: wrap; align-items: center; }
  .trust-item { display: flex; align-items: center; gap: 7px; color: var(--navy); font-size: 13px; font-weight: 600; }
  .trust-item::before { content: '✓'; color: var(--teal); font-weight: 800; }

  /* ── SECTION COMMONS ── */
  section { padding: 80px 48px; }
  .section-label { color: var(--teal); font-size: 12px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; margin-bottom: 10px; }
  .section-title { font-size: 34px; font-weight: 800; color: var(--navy); line-height: 1.2; margin-bottom: 14px; }
  .section-sub { font-size: 16px; color: #555; line-height: 1.7; max-width: 560px; }

  /* ── SERVICES ── */
  #services { background: #fff; }
  .services-header { text-align: center; margin-bottom: 56px; }
  .services-header .section-sub { margin: 0 auto; }
  .services-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px; max-width: 1000px; margin: 0 auto; }
  .service-card {
    border: 1.5px solid #E8EDF5; border-radius: 16px; padding: 32px;
    transition: box-shadow .2s, border-color .2s; cursor: default;
    position: relative; overflow: hidden;
  }
  .service-card::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0;
    height: 4px; background: var(--gold);
    transform: scaleX(0); transform-origin: left; transition: transform .3s;
  }
  .service-card:hover { box-shadow: 0 8px 32px rgba(27,58,107,.1); border-color: #c5d0e0; }
  .service-card:hover::before { transform: scaleX(1); }
  .service-icon {
    width: 52px; height: 52px; border-radius: 12px; margin-bottom: 18px;
    display: flex; align-items: center; justify-content: center; font-size: 24px;
  }
  .icon-navy { background: rgba(27,58,107,.1); }
  .icon-teal { background: rgba(26,122,110,.1); }
  .icon-gold { background: rgba(200,146,42,.1); }
  .service-card h3 { font-size: 18px; font-weight: 700; color: var(--navy); margin-bottom: 8px; }
  .service-card p { color: #555; font-size: 14px; line-height: 1.6; margin-bottom: 16px; }
  .service-tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    background: var(--ltgray); color: #555; border-radius: 6px;
    padding: 3px 10px; font-size: 12px; font-weight: 500;
  }
  .service-price { margin-top: 18px; padding-top: 16px; border-top: 1px solid #eee; font-size: 13px; color: #888; }
  .service-price strong { color: var(--teal); font-size: 15px; }

  /* ── HOW IT WORKS ── */
  #how { background: var(--ltgray); }
  .how-inner { max-width: 900px; margin: 0 auto; }
  .how-header { margin-bottom: 48px; }
  .steps { display: flex; gap: 0; position: relative; }
  .steps::before {
    content: ''; position: absolute; top: 28px; left: 40px; right: 40px;
    height: 2px; background: linear-gradient(90deg, var(--navy), var(--teal));
    z-index: 0;
  }
  .step { flex: 1; text-align: center; position: relative; z-index: 1; padding: 0 16px; }
  .step-circle {
    width: 56px; height: 56px; border-radius: 50%;
    background: var(--navy); color: #fff;
    font-size: 18px; font-weight: 800; display: flex; align-items: center; justify-content: center;
    margin: 0 auto 16px; border: 3px solid #fff; box-shadow: 0 0 0 3px var(--navy);
  }
  .step:nth-child(3) .step-circle { background: var(--teal); box-shadow: 0 0 0 3px var(--teal); }
  .step h4 { font-size: 15px; font-weight: 700; color: var(--navy); margin-bottom: 6px; }
  .step p { font-size: 13px; color: #555; line-height: 1.5; }

  /* ── TUTORS ── */
  #tutors { background: #fff; }
  .tutors-header { margin-bottom: 40px; }
  .tutor-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; max-width: 960px; }
  .tutor-card {
    border: 1.5px solid #E8EDF5; border-radius: 14px; padding: 24px;
    transition: box-shadow .2s;
  }
  .tutor-card:hover { box-shadow: 0 6px 24px rgba(27,58,107,.08); }
  .tutor-avatar {
    width: 60px; height: 60px; border-radius: 50%; margin-bottom: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px; font-weight: 800; color: #fff;
  }
  .av-navy { background: var(--navy); }
  .av-teal { background: var(--teal); }
  .av-gold { background: var(--gold); }
  .tutor-card h4 { font-size: 15px; font-weight: 700; color: var(--navy); margin-bottom: 2px; }
  .tutor-card .tutor-uni { font-size: 12px; color: var(--teal); font-weight: 600; margin-bottom: 10px; }
  .tutor-card .tutor-subjects { font-size: 12px; color: #555; line-height: 1.5; margin-bottom: 12px; }
  .stars { color: var(--gold); font-size: 13px; }
  .rating-text { color: #888; font-size: 12px; margin-left: 4px; }
  .tutor-rate { margin-top: 10px; font-size: 13px; color: #888; }
  .tutor-rate strong { color: var(--navy); font-size: 15px; }

  /* ── CTA BANNER ── */
  .cta-banner {
    background: linear-gradient(135deg, var(--navy), #0f2347);
    padding: 72px 48px; text-align: center;
  }
  .cta-banner h2 { color: #fff; font-size: 36px; font-weight: 800; margin-bottom: 12px; }
  .cta-banner h2 span { color: var(--gold); }
  .cta-banner p { color: rgba(255,255,255,.7); font-size: 17px; margin-bottom: 32px; }
  .cta-actions { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }
  .workshop-note { margin-top: 20px; color: rgba(255,255,255,.5); font-size: 13px; }
  .workshop-note strong { color: var(--gold); }

  /* ── TESTIMONIAL ── */
  #community { background: var(--ltgray); }
  .testimonials { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-top: 40px; }
  .testimonial {
    background: #fff; border-radius: 14px; padding: 24px;
    box-shadow: 0 2px 12px rgba(0,0,0,.04);
  }
  .testimonial p { font-size: 14px; color: #444; line-height: 1.65; font-style: italic; margin-bottom: 16px; }
  .testimonial-author { display: flex; align-items: center; gap: 10px; }
  .author-avatar {
    width: 36px; height: 36px; border-radius: 50%; background: var(--navy);
    color: #fff; font-size: 13px; font-weight: 700;
    display: flex; align-items: center; justify-content: center;
  }
  .author-name { font-size: 13px; font-weight: 700; color: var(--navy); }
  .author-detail { font-size: 11px; color: #888; }

  /* ── FOOTER ── */
  footer {
    background: var(--dark); color: rgba(255,255,255,.6);
    padding: 48px; display: flex; justify-content: space-between; align-items: flex-start;
    gap: 40px; flex-wrap: wrap;
  }
  .footer-brand .logo-text { color: #fff; }
  .footer-brand p { font-size: 13px; line-height: 1.6; margin-top: 10px; max-width: 260px; }
  .footer-links h5 { color: #fff; font-size: 13px; font-weight: 700; margin-bottom: 12px; }
  .footer-links a { display: block; color: rgba(255,255,255,.55); font-size: 13px; margin-bottom: 7px; text-decoration: none; }
  .footer-links a:hover { color: var(--gold); }
  .footer-bottom { border-top: 1px solid rgba(255,255,255,.08); margin-top: 32px; padding-top: 20px; font-size: 12px; text-align: center; width: 100%; }

  /* ── LANGUAGE TOGGLE ── */
  [data-lang="am"] { display: none; }
  body.am [data-lang="en"] { display: none; }
  body.am [data-lang="am"] { display: block; }
  body.am span[data-lang="am"] { display: inline; }
  body.am span[data-lang="en"] { display: none; }
  span[data-lang="am"] { display: none; }

  /* ── BOOKING MODAL ── */
  .modal-overlay {
    display: none; position: fixed; inset: 0; background: rgba(0,0,0,.5);
    z-index: 200; align-items: center; justify-content: center;
  }
  .modal-overlay.open { display: flex; }
  .modal {
    background: #fff; border-radius: 16px; padding: 36px; width: 100%; max-width: 480px;
    box-shadow: 0 20px 60px rgba(0,0,0,.2); position: relative;
  }
  .modal h3 { font-size: 22px; font-weight: 800; color: var(--navy); margin-bottom: 6px; }
  .modal p { color: #666; font-size: 14px; margin-bottom: 24px; }
  .form-group { margin-bottom: 16px; }
  .form-group label { display: block; font-size: 13px; font-weight: 600; color: var(--navy); margin-bottom: 5px; }
  .form-group input, .form-group select {
    width: 100%; border: 1.5px solid #D9DDE3; border-radius: 8px;
    padding: 10px 14px; font-size: 14px; outline: none; transition: border-color .15s;
  }
  .form-group input:focus, .form-group select:focus { border-color: var(--navy); }
  .modal-actions { display: flex; gap: 10px; margin-top: 24px; }
  .btn-cancel { flex: 1; background: var(--ltgray); color: #555; border: none; border-radius: 8px; padding: 12px; font-size: 14px; font-weight: 600; cursor: pointer; }
  .btn-submit { flex: 2; background: var(--gold); color: #fff; border: none; border-radius: 8px; padding: 12px; font-size: 14px; font-weight: 700; cursor: pointer; }
  .close-btn { position: absolute; top: 16px; right: 20px; background: none; border: none; font-size: 20px; color: #999; cursor: pointer; }

  @media (max-width: 768px) {
    nav { padding: 0 20px; }
    .nav-links { display: none; }
    .hero { padding: 60px 20px; flex-direction: column; }
    .hero h1 { font-size: 32px; }
    section { padding: 60px 20px; }
    .services-grid, .tutor-grid, .testimonials { grid-template-columns: 1fr; }
    .steps { flex-direction: column; gap: 24px; }
    .steps::before { display: none; }
    footer { flex-direction: column; padding: 32px 20px; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a class="logo" href="#">
    <div class="logo-icon">MS</div>
    <div>
      <div class="logo-text">MedSTEM Edge</div>
      <div class="logo-sub"><span data-lang="en">Empowering Families Through Education</span><span data-lang="am">ቤተሰቦችን በትምህርት ማብቃት</span></div>
    </div>
  </a>
  <div class="nav-links">
    <a href="#services"><span data-lang="en">Services</span><span data-lang="am">አገልግሎቶች</span></a>
    <a href="#tutors"><span data-lang="en">Tutors</span><span data-lang="am">አስተማሪዎች</span></a>
    <a href="#community"><span data-lang="en">Community</span><span data-lang="am">ማህበረሰብ</span></a>
    <a href="#how"><span data-lang="en">How It Works</span><span data-lang="am">እንዴት ይሰራል</span></a>
    <button class="lang-btn" onclick="toggleLang()">🇨🇦 EN / አማ</button>
    <a class="nav-cta" href="#" onclick="openModal(); return false;"><span data-lang="en">Book Free Session</span><span data-lang="am">ነፃ ክፍለ ጊዜ</span></a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-content">
    <div class="hero-badge">🇨🇦 Serving the Ethiopian-Canadian Community</div>
    <h1>
      <span data-lang="en">Your Child Deserves to <span style="color:var(--gold)">Thrive</span> in Canada</span>
      <span data-lang="am">ልጅዎ በካናዳ <span style="color:var(--gold)">ሊያብብ</span> ይገባዋል</span>
    </h1>
    <div class="hero-am">
      <span data-lang="en">ሜድስቴም ኤጅ</span>
      <span data-lang="am">MedSTEM Edge</span>
    </div>
    <p>
      <span data-lang="en">We help Ethiopian families navigate the Canadian school system, access affordable STEM tutoring, obtain professional certifications, and support homeschooling — in Amharic and English.</span>
      <span data-lang="am">ኢትዮጵያዊ ቤተሰቦች የካናዳ ትምህርት ስርዓት እንዲረዱ፣ ዋጋ ቅናሽ STEM ትምህርት እንዲያገኙ፣ ሙያዊ ምስክርነቶችን እንዲያገኙ እና ቤት ውስጥ ትምህርት እንዲደግፉ እናግዛለን።</span>
    </p>
    <div class="hero-actions">
      <a class="btn-primary" href="#" onclick="openModal(); return false;">
        <span data-lang="en">Book a Free Consultation</span>
        <span data-lang="am">ነፃ ምክክር ያዝ</span>
      </a>
      <a class="btn-outline" href="#services">
        <span data-lang="en">View Our Services</span>
        <span data-lang="am">አገልግሎቶቻችን</span>
      </a>
    </div>
    <div class="hero-stats">
      <div>
        <div class="stat-num">4</div>
        <div class="stat-label"><span data-lang="en">Service Pillars</span><span data-lang="am">የአገልግሎት ምሰሶዎች</span></div>
      </div>
      <div>
        <div class="stat-num">$30</div>
        <div class="stat-label"><span data-lang="en">Per hr tutoring</span><span data-lang="am">በሰዓት ትምህርት</span></div>
      </div>
      <div>
        <div class="stat-num">2</div>
        <div class="stat-label"><span data-lang="en">Languages</span><span data-lang="am">ቋንቋዎች</span></div>
      </div>
      <div>
        <div class="stat-num">🇨🇦</div>
        <div class="stat-label"><span data-lang="en">Waterloo Region</span><span data-lang="am">ዋተርሉ ክልል</span></div>
      </div>
    </div>
  </div>
</section>

<!-- TRUST BAR -->
<div class="trust-bar">
  <span class="trust-label"><span data-lang="en">Why Families Trust Us</span><span data-lang="am">ቤተሰቦች ለምን ይተማመኑብናል</span></span>
  <div class="trust-items">
    <span class="trust-item"><span data-lang="en">Ethiopian community members</span><span data-lang="am">ኢትዮጵያዊ ማህበረሰብ አባላት</span></span>
    <span class="trust-item"><span data-lang="en">Amharic & English support</span><span data-lang="am">አማርኛ እና እንግሊዝኛ ድጋፍ</span></span>
    <span class="trust-item"><span data-lang="en">University of Waterloo tutors</span><span data-lang="am">UWaterloo አስተማሪዎች</span></span>
    <span class="trust-item"><span data-lang="en">50–65% below agency rates</span><span data-lang="am">ከኤጀንሲ ዋጋ 50–65% ያነሰ</span></span>
    <span class="trust-item"><span data-lang="en">In-person & online</span><span data-lang="am">対面 እና ኦንላይን</span></span>
  </div>
</div>

<!-- SERVICES -->
<section id="services">
  <div class="services-header">
    <div class="section-label"><span data-lang="en">What We Offer</span><span data-lang="am">የምናቀርበው</span></div>
    <div class="section-title"><span data-lang="en">Four Services, One Community</span><span data-lang="am">አራት አገልግሎቶች፣ አንድ ማህበረሰብ</span></div>
    <div class="section-sub"><span data-lang="en">Every service is designed around the real challenges Ethiopian-Canadian families face in the education system.</span><span data-lang="am">እያንዳንዱ አገልግሎት ኢትዮጵያ-ካናዲያን ቤተሰቦች በትምህርት ስርዓቱ ውስጥ የሚያጋጥሟቸው ትክክለኛ ፈተናዎችን ሙሉ ቁጥቋጦ ዙሪያ ነው።</span></div>
  </div>
  <div class="services-grid">

    <div class="service-card">
      <div class="service-icon icon-navy">🧭</div>
      <h3><span data-lang="en">Student Navigation & Supervision</span><span data-lang="am">የተማሪ መምሪያ እና ክትትል</span></h3>
      <p><span data-lang="en">We help Ethiopian parents understand the Ontario school system — report cards, course selection, teacher communication, university pathways, and OSAP — in your language.</span><span data-lang="am">ኢትዮጵያዊ ወላጆች የኦንታሪዮ ትምህርት ቤት ስርዓትን — ሪፖርት ካርዶችን፣ ኮርስ ምርጫን፣ ከአስተማሪዎች ጋር ግንኙነትን — በቋንቋዎ እንዲረዱ እናግዛለን።</span></p>
      <div class="service-tags">
        <span class="tag"><span data-lang="en">Grade K–12</span><span data-lang="am">ክፍል K–12</span></span>
        <span class="tag"><span data-lang="en">University prep</span><span data-lang="am">ዩኒቨርሲቲ ዝግጅት</span></span>
        <span class="tag"><span data-lang="en">Parent coaching</span><span data-lang="am">ወላጅ ስልጠና</span></span>
      </div>
      <div class="service-price">
        <span data-lang="en">Starting at <strong>$80</strong> for initial assessment · <strong>$180/month</strong> package</span>
        <span data-lang="am">የመጀመሪያ ግምገማ <strong>$80</strong> · <strong>$180/ወር</strong> ጥቅል</span>
      </div>
    </div>

    <div class="service-card">
      <div class="service-icon icon-teal">📐</div>
      <h3><span data-lang="en">STEM & Coding Tutoring</span><span data-lang="am">STEM እና ኮዲንግ ትምህርት</span></h3>
      <p><span data-lang="en">Affordable 1-on-1 and group tutoring in Math, Physics, Chemistry, Computer Science, and coding — delivered by University of Waterloo students and alumni.</span><span data-lang="am">ዋጋ ቅናሽ 1-ለ-1 እና የቡድን ትምህርት ሂሳብ፣ ፊዚክስ፣ ኬሚስትሪ፣ ኮምፒውተር ሳይንስ — UWaterloo ተማሪዎች።</span></p>
      <div class="service-tags">
        <span class="tag">Math</span>
        <span class="tag">Physics</span>
        <span class="tag">CS</span>
        <span class="tag">Python</span>
        <span class="tag">Java</span>
        <span class="tag">Grade 4–University</span>
      </div>
      <div class="service-price">
        <span data-lang="en"><strong>$30/hr</strong> one-on-one · <strong>$15/session</strong> group</span>
        <span data-lang="am"><strong>$30/ሰዓት</strong> ግለሰባዊ · <strong>$15/ክፍለ ጊዜ</strong> ቡድን</span>
      </div>
    </div>

    <div class="service-card">
      <div class="service-icon icon-gold">🏥</div>
      <h3><span data-lang="en">Professional Certification Consulting</span><span data-lang="am">ሙያዊ ምስክርነት ምክር</span></h3>
      <p><span data-lang="en">Clear roadmaps and study support for internationally trained Ethiopians pursuing Canadian certification in nursing, physiotherapy, engineering, pharmacy, and more.</span><span data-lang="am">ዓለም አቀፍ ስልጠና ላላቸው ኢትዮጵያዊያን ለናርሲንግ፣ ፊዚዮቴራፒ፣ ምህንድስና ምስክርነት ግልጽ መንገድ እና ጥናት ድጋፍ።</span></p>
      <div class="service-tags">
        <span class="tag">Nursing</span>
        <span class="tag">Physiotherapy</span>
        <span class="tag">Engineering (P.Eng)</span>
        <span class="tag">Pharmacy</span>
      </div>
      <div class="service-price">
        <span data-lang="en"><strong>$120</strong> roadmap assessment · <strong>$80/month</strong> study group</span>
        <span data-lang="am"><strong>$120</strong> የመንገድ ካርታ · <strong>$80/ወር</strong> የጥናት ቡድን</span>
      </div>
    </div>

    <div class="service-card">
      <div class="service-icon icon-navy">🏠</div>
      <h3><span data-lang="en">Homeschooling Support</span><span data-lang="am">የቤት ትምህርት ድጋፍ</span></h3>
      <p><span data-lang="en">Curriculum planning, co-op group classes, parent coaching, and online courses for homeschooling families — with optional Amharic language and Ethiopian cultural integration.</span><span data-lang="am">የሥርዓተ-ትምህርት ዕቅድ፣ የቡድን ክፍሎች፣ የወላጅ ስልጠና እና ለቤት ትምህርት ቤተሰቦች ኦንላይን ኮርሶች — አማርኛ ቋንቋ ጨምሮ።</span></p>
      <div class="service-tags">
        <span class="tag">Grade 1–12</span>
        <span class="tag"><span data-lang="en">Co-op classes</span><span data-lang="am">የቡድን ክፍሎች</span></span>
        <span class="tag"><span data-lang="en">Amharic integration</span><span data-lang="am">አማርኛ ውህደት</span></span>
      </div>
      <div class="service-price">
        <span data-lang="en"><strong>$150/year</strong> curriculum plan · <strong>$60/month</strong> co-op classes</span>
        <span data-lang="am"><strong>$150/ዓመት</strong> ሥርዓተ-ትምህርት · <strong>$60/ወር</strong> ቡድን</span>
      </div>
    </div>

  </div>
</section>

<!-- HOW IT WORKS -->
<section id="how">
  <div class="how-inner">
    <div class="how-header">
      <div class="section-label"><span data-lang="en">Simple Process</span><span data-lang="am">ቀላል ሂደት</span></div>
      <div class="section-title"><span data-lang="en">Getting Started Is Easy</span><span data-lang="am">መጀመር ቀላል ነው</span></div>
    </div>
    <div class="steps">
      <div class="step">
        <div class="step-circle">1</div>
        <h4><span data-lang="en">Free Consultation</span><span data-lang="am">ነፃ ምክክር</span></h4>
        <p><span data-lang="en">We learn about your child's situation and goals — in Amharic or English, in person or online.</span><span data-lang="am">የልጅዎን ሁኔታ እና ዓላማ እንረዳለን — አማርኛ ወይም እንግሊዝኛ።</span></p>
      </div>
      <div class="step">
        <div class="step-circle">2</div>
        <h4><span data-lang="en">Custom Plan</span><span data-lang="am">ብጁ ዕቅድ</span></h4>
        <p><span data-lang="en">We match you with the right tutor or advisor and create a personalised roadmap.</span><span data-lang="am">ትክክለኛ አስተማሪ ወይም አማካሪ እናዛምዳለን እና ብጁ የመንገድ ካርታ ይሰራል።</span></p>
      </div>
      <div class="step">
        <div class="step-circle" style="background:var(--gold);box-shadow:0 0 0 3px var(--gold);">3</div>
        <h4><span data-lang="en">Book & Pay Online</span><span data-lang="am">ኦንላይን ያዝ እና ይክፈሉ</span></h4>
        <p><span data-lang="en">Sessions booked and paid securely through our platform. Automatic reminders sent to you.</span><span data-lang="am">ክፍለ ጊዜዎች ደህንነቱ በተጠበቀ ሁኔታ ቀጠሮ ይያዛሉ።</span></p>
      </div>
      <div class="step">
        <div class="step-circle">4</div>
        <h4><span data-lang="en">Your Child Thrives</span><span data-lang="am">ልጅዎ ያብባል</span></h4>
        <p><span data-lang="en">Progress tracked, feedback collected, and the plan adjusted as your child grows.</span><span data-lang="am">እድገት ይከታተላል፣ አስተያየት ይሰበሰባል፣ ዕቅዱ ይስተካከላል።</span></p>
      </div>
    </div>
  </div>
</section>

<!-- TUTORS -->
<section id="tutors">
  <div class="tutors-header">
    <div class="section-label"><span data-lang="en">Our Tutors</span><span data-lang="am">አስተማሪዎቻችን</span></div>
    <div class="section-title"><span data-lang="en">UWaterloo-Trained, Community-Rooted</span><span data-lang="am">UWaterloo ስልጠና፣ ማህበረሰብ ሥር</span></div>
    <div class="section-sub"><span data-lang="en">All our tutors are Ethiopian-Canadian university students or alumni who understand both the academic standard and the cultural context of our families.</span><span data-lang="am">ሁሉም አስተማሪዎቻችን ኢትዮጵያ-ካናዲያን ዩኒቨርሲቲ ተማሪዎች ወይም ምሩቃን ናቸው።</span></div>
  </div>
  <div class="tutor-grid">
    <div class="tutor-card">
      <div class="tutor-avatar av-navy">YA</div>
      <h4>Yonas Alemu</h4>
      <div class="tutor-uni">University of Waterloo — Computer Science</div>
      <div class="tutor-subjects">Math · CS · Python · Java · Grades 9–University</div>
      <div class="stars">★★★★★ <span class="rating-text">5.0 (12 sessions)</span></div>
      <div class="tutor-rate">
        <span data-lang="en">From <strong>$30/hr</strong></span>
        <span data-lang="am">ከ<strong>$30/ሰዓት</strong></span>
      </div>
    </div>
    <div class="tutor-card">
      <div class="tutor-avatar av-teal">ST</div>
      <h4>Sara Tesfaye</h4>
      <div class="tutor-uni">University of Waterloo — Mathematics</div>
      <div class="tutor-subjects">Advanced Functions · Calculus · STAT 230 · Grades 10–University</div>
      <div class="stars">★★★★★ <span class="rating-text">4.9 (8 sessions)</span></div>
      <div class="tutor-rate">
        <span data-lang="en">From <strong>$30/hr</strong></span>
        <span data-lang="am">ከ<strong>$30/ሰዓት</strong></span>
      </div>
    </div>
    <div class="tutor-card">
      <div class="tutor-avatar av-gold">DG</div>
      <h4>Daniel Girma</h4>
      <div class="tutor-uni">University of Waterloo — Engineering</div>
      <div class="tutor-subjects">Physics · Chemistry · Math · Grades 9–12</div>
      <div class="stars">★★★★★ <span class="rating-text">5.0 (6 sessions)</span></div>
      <div class="tutor-rate">
        <span data-lang="en">From <strong>$30/hr</strong></span>
        <span data-lang="am">ከ<strong>$30/ሰዓት</strong></span>
      </div>
    </div>
  </div>
  <div style="margin-top:28px;">
    <a class="btn-primary" href="#" onclick="openModal(); return false;" style="display:inline-block;">
      <span data-lang="en">→ View All Tutors & Book</span>
      <span data-lang="am">→ ሁሉንም አስተማሪዎች ይመልከቱ</span>
    </a>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="community">
  <div class="section-label"><span data-lang="en">Community Voice</span><span data-lang="am">የማህበረሰብ ድምፅ</span></div>
  <div class="section-title"><span data-lang="en">Families We've Helped</span><span data-lang="am">ያገዝናቸው ቤተሰቦች</span></div>
  <div class="testimonials">
    <div class="testimonial">
      <p><span data-lang="en">"I finally understood what courses my daughter needs for nursing school. No one had ever explained the Ontario system to me so clearly — in Amharic."</span><span data-lang="am">"ልጄ ለነርሲንግ ት/ቤት ምን ኮርሶች እንደሚያስፈልጓት በመጨረሻ ተረዳሁ። ማንም ኦንታሪዮ ስርዓቱን ለኔ በአማርኛ ያን ያህል በግልፅ አልተረጎመልኝም።"</span></p>
      <div class="testimonial-author">
        <div class="author-avatar">MT</div>
        <div>
          <div class="author-name">Mekdes T.</div>
          <div class="author-detail"><span data-lang="en">Parent, Waterloo</span><span data-lang="am">ወላጅ፣ ዋተርሉ</span></div>
        </div>
      </div>
    </div>
    <div class="testimonial">
      <p><span data-lang="en">"My son's math grade went from 62% to 84% in one semester. His tutor Yonas speaks Amharic and understands exactly where he gets stuck."</span><span data-lang="am">"የልጄ የሂሳብ ውጤት በአንድ ሴሜስተር ውስጥ ከ62% ወደ 84% ወጣ። አስተማሪው ዮናስ አማርኛ ይናገራል።"</span></p>
      <div class="testimonial-author">
        <div class="author-avatar">BH</div>
        <div>
          <div class="author-name">Biruk H.</div>
          <div class="author-detail"><span data-lang="en">Parent, Kitchener</span><span data-lang="am">ወላጅ፣ ኪችነር</span></div>
        </div>
      </div>
    </div>
    <div class="testimonial">
      <p><span data-lang="en">"I passed my NCLEX on the first attempt after doing the study group for 3 months. The roadmap they gave me saved me so much time and confusion."</span><span data-lang="am">"3 ወር የጥናት ቡድን ካደረኩ በኋላ NCLEX-ን በመጀመሪያ ሙከራ አለፍኩ። የሰጡኝ የመንገድ ካርታ ብዙ ጊዜ አስቀደመልኝ።"</span></p>
      <div class="testimonial-author">
        <div class="author-avatar">FD</div>
        <div>
          <div class="author-name">Fikirte D.</div>
          <div class="author-detail"><span data-lang="en">Registered Nurse, Cambridge</span><span data-lang="am">ነርስ፣ ካምብሪጅ</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA BANNER -->
<div class="cta-banner">
  <h2><span data-lang="en">Start With a <span>Free</span> Parent Workshop</span><span data-lang="am">ነፃ ወላጅ ወርክሾፕ</span></h2>
  <p>
    <span data-lang="en">"Understanding Your Child's Education in Canada" — a free 90-minute session in Amharic and English, open to all Ethiopian-Canadian families in Waterloo Region.</span>
    <span data-lang="am">"የልጅዎን ትምህርት በካናዳ መረዳት" — ነፃ 90 ደቂቃ ክፍለ ጊዜ በአማርኛ እና እንግሊዝኛ።</span>
  </p>
  <div class="cta-actions">
    <a class="btn-primary" href="#" onclick="openModal(); return false;">
      <span data-lang="en">Reserve My Free Spot</span>
      <span data-lang="am">ቦታዬን ይያዝ</span>
    </a>
    <a class="btn-outline" href="#services" style="color:#fff;border-color:rgba(255,255,255,.35);">
      <span data-lang="en">Learn About Services</span>
      <span data-lang="am">ስለ አገልግሎቶች</span>
    </a>
  </div>
  <div class="workshop-note">
    <span data-lang="en">📍 In-person in Waterloo Region + online via Zoom · <strong>Completely free, no commitment</strong></span>
    <span data-lang="am">📍 ዋተርሉ ክልል + ዙም · <strong>ሙሉ ለሙሉ ነፃ</strong></span>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-brand">
    <div class="logo">
      <div class="logo-icon">MS</div>
      <div>
        <div class="logo-text">MedSTEM Edge</div>
        <div class="logo-sub" style="color:var(--gold)">Waterloo Region, Ontario</div>
      </div>
    </div>
    <p style="color:rgba(255,255,255,.5);margin-top:14px;">
      <span data-lang="en">Serving the Ethiopian-Canadian community with education, tutoring, and professional support — in Amharic and English.</span>
      <span data-lang="am">ኢትዮጵያ-ካናዲያን ማህበረሰብን በትምህርት እና ሙያዊ ድጋፍ ማገልገል — በአማርኛ እና እንግሊዝኛ።</span>
    </p>
  </div>
  <div class="footer-links">
    <h5><span data-lang="en">Services</span><span data-lang="am">አገልግሎቶች</span></h5>
    <a href="#services"><span data-lang="en">Student Navigation</span><span data-lang="am">የተማሪ መምሪያ</span></a>
    <a href="#services"><span data-lang="en">STEM Tutoring</span><span data-lang="am">STEM ትምህርት</span></a>
    <a href="#services"><span data-lang="en">Certification Consulting</span><span data-lang="am">ምስክርነት ምክር</span></a>
    <a href="#services"><span data-lang="en">Homeschooling Support</span><span data-lang="am">የቤት ትምህርት</span></a>
  </div>
  <div class="footer-links">
    <h5><span data-lang="en">Contact</span><span data-lang="am">ያግኙን</span></h5>
    <a href="#">info@medstemedge.ca</a>
    <a href="#">+1 (519) 000-0000</a>
    <a href="#">Waterloo, Ontario</a>
    <a href="#"><span data-lang="en">Book a Free Consultation</span><span data-lang="am">ነፃ ምክክር ያዝ</span></a>
  </div>
  <div class="footer-bottom">
    <span data-lang="en">© 2026 MedSTEM Edge · Waterloo Region, Ontario · Serving the Ethiopian-Canadian Community</span>
    <span data-lang="am">© 2026 ሜድስቴም ኤጅ · ዋተርሉ ክልል · ኢትዮጵያ-ካናዲያን ማህበረሰብ ማገልገል</span>
  </div>
</footer>

<!-- BOOKING MODAL -->
<div class="modal-overlay" id="modal" onclick="if(event.target===this)closeModal()">
  <div class="modal">
    <button class="close-btn" onclick="closeModal()">✕</button>
    <h3><span data-lang="en">Book a Free Consultation</span><span data-lang="am">ነፃ ምክክር ያዝ</span></h3>
    <p><span data-lang="en">We'll reach out within 24 hours to confirm your session.</span><span data-lang="am">ክፍለ ጊዜዎን ለማረጋገጥ በ24 ሰዓት ውስጥ እናነጋግርዎታለን።</span></p>
    <div class="form-group">
      <label><span data-lang="en">Full Name</span><span data-lang="am">ሙሉ ስም</span></label>
      <input type="text" placeholder="Abebe Kebede">
    </div>
    <div class="form-group">
      <label><span data-lang="en">Phone or Email</span><span data-lang="am">ስልክ ወይም ኢሜይል</span></label>
      <input type="text" placeholder="abebe@email.com">
    </div>
    <div class="form-group">
      <label><span data-lang="en">I'm interested in</span><span data-lang="am">ፍላጎቴ ነው</span></label>
      <select>
        <option>Student Navigation &amp; Supervision</option>
        <option>STEM &amp; Coding Tutoring</option>
        <option>Professional Certification Consulting</option>
        <option>Homeschooling Support</option>
        <option>Free Parent Workshop</option>
      </select>
    </div>
    <div class="form-group">
      <label><span data-lang="en">Preferred language</span><span data-lang="am">የሚፈልጉት ቋንቋ</span></label>
      <select>
        <option>Amharic (አማርኛ)</option>
        <option>English</option>
        <option>Both / ሁለቱም</option>
      </select>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal()"><span data-lang="en">Cancel</span><span data-lang="am">ሰርዝ</span></button>
      <button class="btn-submit" onclick="submitForm()"><span data-lang="en">Send Request →</span><span data-lang="am">ጥያቄ ላክ →</span></button>
    </div>
  </div>
</div>

<script>
  function toggleLang() {
    document.body.classList.toggle('am');
  }
  function openModal() {
    document.getElementById('modal').classList.add('open');
  }
  function closeModal() {
    document.getElementById('modal').classList.remove('open');
  }
  function submitForm() {
    closeModal();
    const banner = document.createElement('div');
    banner.style.cssText = 'position:fixed;bottom:24px;right:24px;background:#1A7A6E;color:#fff;padding:16px 24px;border-radius:12px;font-size:14px;font-weight:600;box-shadow:0 4px 20px rgba(0,0,0,.2);z-index:300;';
    banner.textContent = '✓ Request sent! We\'ll contact you within 24 hours.';
    document.body.appendChild(banner);
    setTimeout(() => banner.remove(), 4000);
  }
</script>
</body>
</html>
