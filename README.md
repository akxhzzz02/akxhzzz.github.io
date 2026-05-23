<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Akash | Visual Editor & Content Creator</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #c9a84c;
    --gold-light: #e8d08a;
    --dark: #0a0a0a;
    --dark2: #111111;
    --dark3: #1a1a1a;
    --dark4: #222222;
    --light: #f5f0e8;
    --muted: #888880;
    --text: #e8e4dc;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 5%;
    background: rgba(10,10,10,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 0.5px solid rgba(201,168,76,0.2);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    color: var(--gold);
    letter-spacing: 2px;
    text-decoration: none;
  }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-size: 0.78rem;
    letter-spacing: 2.5px;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.3s;
  }

  .nav-links a:hover { color: var(--gold); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 0 5%;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute;
    inset: 0;
    background: 
      radial-gradient(ellipse 60% 60% at 80% 50%, rgba(201,168,76,0.06) 0%, transparent 70%),
      radial-gradient(ellipse 40% 40% at 10% 80%, rgba(201,168,76,0.04) 0%, transparent 70%);
  }

  .hero-grid {
    position: absolute;
    inset: 0;
    background-image: 
      linear-gradient(rgba(201,168,76,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
  }

  .hero-content {
    position: relative;
    max-width: 700px;
  }

  .hero-tag {
    font-size: 0.7rem;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .hero-tag::before {
    content: '';
    display: block;
    width: 40px;
    height: 1px;
    background: var(--gold);
  }

  .hero-name {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3.5rem, 8vw, 6rem);
    font-weight: 700;
    line-height: 1.05;
    margin-bottom: 1rem;
    color: var(--light);
  }

  .hero-name em {
    font-style: italic;
    color: var(--gold);
  }

  .hero-subtitle {
    font-size: 1rem;
    color: var(--muted);
    line-height: 1.7;
    max-width: 480px;
    margin-bottom: 3rem;
    font-weight: 300;
  }

  .hero-cta {
    display: flex;
    gap: 1.5rem;
    align-items: center;
    flex-wrap: wrap;
  }

  .btn-primary {
    padding: 0.9rem 2.5rem;
    background: var(--gold);
    color: var(--dark);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    font-weight: 500;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-decoration: none;
    border: none;
    cursor: pointer;
    transition: all 0.3s;
  }

  .btn-primary:hover {
    background: var(--gold-light);
    transform: translateY(-2px);
  }

  .btn-outline {
    padding: 0.9rem 2.5rem;
    background: transparent;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    font-weight: 400;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-decoration: none;
    border: 0.5px solid rgba(232,228,220,0.3);
    cursor: pointer;
    transition: all 0.3s;
  }

  .btn-outline:hover {
    border-color: var(--gold);
    color: var(--gold);
    transform: translateY(-2px);
  }

  .hero-scroll {
    position: absolute;
    bottom: 3rem;
    right: 5%;
    writing-mode: vertical-rl;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .hero-scroll::after {
    content: '';
    display: block;
    width: 1px;
    height: 60px;
    background: linear-gradient(to bottom, var(--muted), transparent);
  }

  /* SECTIONS */
  section {
    padding: 7rem 5%;
  }

  .section-label {
    font-size: 0.65rem;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label::before {
    content: '';
    display: block;
    width: 30px;
    height: 1px;
    background: var(--gold);
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.2rem, 4vw, 3.2rem);
    font-weight: 700;
    line-height: 1.15;
    margin-bottom: 1.5rem;
    color: var(--light);
  }

  /* ABOUT */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
    margin-top: 4rem;
  }

  .about-text p {
    color: var(--muted);
    line-height: 1.9;
    margin-bottom: 1.2rem;
    font-weight: 300;
  }

  .about-text p strong {
    color: var(--text);
    font-weight: 500;
  }

  .about-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-top: 3rem;
  }

  .stat-box {
    border: 0.5px solid rgba(201,168,76,0.2);
    padding: 1.5rem;
    background: var(--dark2);
  }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--gold);
    line-height: 1;
    margin-bottom: 0.4rem;
  }

  .stat-label {
    font-size: 0.72rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
  }

  .tools-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .tool-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.5rem;
    background: var(--dark2);
    border: 0.5px solid rgba(201,168,76,0.15);
    border-left: 2px solid var(--gold);
    transition: all 0.3s;
  }

  .tool-item:hover {
    background: var(--dark3);
    transform: translateX(4px);
  }

  .tool-name {
    font-size: 0.95rem;
    font-weight: 500;
    color: var(--text);
    flex: 1;
  }

  .tool-badge {
    font-size: 0.65rem;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--gold);
    border: 0.5px solid rgba(201,168,76,0.4);
    padding: 3px 10px;
  }

  /* SERVICES */
  .services-section {
    background: var(--dark2);
    border-top: 0.5px solid rgba(201,168,76,0.1);
    border-bottom: 0.5px solid rgba(201,168,76,0.1);
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5px;
    margin-top: 4rem;
    background: rgba(201,168,76,0.1);
  }

  .service-card {
    background: var(--dark2);
    padding: 2.5rem 2rem;
    position: relative;
    overflow: hidden;
    transition: all 0.4s;
  }

  .service-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    height: 2px;
    width: 0;
    background: var(--gold);
    transition: width 0.4s;
  }

  .service-card:hover::before { width: 100%; }
  .service-card:hover { background: var(--dark3); }

  .service-icon {
    font-size: 2.5rem;
    margin-bottom: 1.5rem;
    display: block;
  }

  .service-num {
    position: absolute;
    top: 1.5rem;
    right: 1.5rem;
    font-family: 'Playfair Display', serif;
    font-size: 3.5rem;
    font-weight: 700;
    color: rgba(201,168,76,0.06);
    line-height: 1;
    pointer-events: none;
  }

  .service-title {
    font-size: 1.1rem;
    font-weight: 500;
    color: var(--light);
    margin-bottom: 0.8rem;
    letter-spacing: 0.5px;
  }

  .service-desc {
    font-size: 0.85rem;
    color: var(--muted);
    line-height: 1.7;
  }

  /* PORTFOLIO */
  .portfolio-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    margin-bottom: 3rem;
  }

  .portfolio-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }

  .portfolio-item {
    position: relative;
    overflow: hidden;
    background: var(--dark3);
    border: 0.5px solid rgba(201,168,76,0.1);
    cursor: pointer;
  }

  .portfolio-item.wide {
    grid-column: span 2;
  }

  .portfolio-item img {
    width: 100%;
    height: 100%;
    min-height: 220px;
    object-fit: cover;
    display: block;
    transition: transform 0.6s ease;
    filter: brightness(0.85);
  }

  .portfolio-item:hover img {
    transform: scale(1.05);
    filter: brightness(0.6);
  }

  .portfolio-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(10,10,10,0.9) 0%, transparent 60%);
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: 1.5rem;
    opacity: 0;
    transition: opacity 0.4s;
  }

  .portfolio-item:hover .portfolio-overlay { opacity: 1; }

  .portfolio-cat {
    font-size: 0.62rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.4rem;
  }

  .portfolio-name {
    font-size: 1rem;
    font-weight: 500;
    color: var(--light);
  }

  .portfolio-tag {
    display: inline-block;
    font-size: 0.65rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    border: 0.5px solid rgba(201,168,76,0.2);
    padding: 4px 10px;
    margin-top: 0.6rem;
    background: rgba(201,168,76,0.05);
  }

  /* CONTACT */
  .contact-section {
    background: var(--dark2);
  }

  .contact-inner {
    max-width: 700px;
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-top: 3rem;
  }

  .contact-item {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    padding: 1.5rem;
    background: var(--dark3);
    border: 0.5px solid rgba(201,168,76,0.15);
    text-decoration: none;
    transition: all 0.3s;
    border-left: 2px solid transparent;
  }

  .contact-item:hover {
    border-left-color: var(--gold);
    transform: translateY(-2px);
  }

  .contact-icon {
    font-size: 1.4rem;
    color: var(--gold);
    margin-top: 2px;
  }

  .contact-label {
    font-size: 0.65rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 0.3rem;
  }

  .contact-value {
    font-size: 0.9rem;
    color: var(--text);
    font-weight: 400;
  }

  /* FOOTER */
  footer {
    padding: 2.5rem 5%;
    border-top: 0.5px solid rgba(201,168,76,0.15);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    color: var(--gold);
    letter-spacing: 2px;
  }

  .footer-copy {
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 1px;
  }

  .footer-tagline {
    font-size: 0.7rem;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    font-style: italic;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .hero-tag { animation: fadeUp 0.8s ease forwards; }
  .hero-name { animation: fadeUp 0.8s 0.2s ease forwards; opacity: 0; }
  .hero-subtitle { animation: fadeUp 0.8s 0.4s ease forwards; opacity: 0; }
  .hero-cta { animation: fadeUp 0.8s 0.6s ease forwards; opacity: 0; }

  .divider {
    width: 60px;
    height: 1px;
    background: linear-gradient(to right, var(--gold), transparent);
    margin: 2rem 0;
  }

  @media (max-width: 900px) {
    .about-grid { grid-template-columns: 1fr; gap: 3rem; }
    .portfolio-grid { grid-template-columns: 1fr 1fr; }
    .portfolio-item.wide { grid-column: span 2; }
    .contact-grid { grid-template-columns: 1fr; }
    .nav-links { display: none; }
    footer { flex-direction: column; gap: 1rem; text-align: center; }
  }

  @media (max-width: 600px) {
    .portfolio-grid { grid-template-columns: 1fr; }
    .portfolio-item.wide { grid-column: span 1; }
    .services-grid { grid-template-columns: 1fr; }
    .about-stats { grid-template-columns: 1fr 1fr; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">AK</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#work">Work</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-content">
    <div class="hero-tag">Visual Editor & Content Creator</div>
    <h1 class="hero-name">
      Turning Ideas<br>Into <em>Visual</em><br>Stories
    </h1>
    <p class="hero-subtitle">
      Photo & Video Editor. Photography enthusiast. Crafting cinematic visuals, reels, and aesthetic edits that connect with people on a deeper level.
    </p>
    <div class="hero-cta">
      <a href="#work" class="btn-primary">View My Work</a>
      <a href="#contact" class="btn-outline">Get In Touch</a>
    </div>
  </div>
  <div class="hero-scroll">Scroll</div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-label">About Me</div>
  <h2 class="section-title">Creativity, Consistency<br>& Passion</h2>
  <div class="about-grid">
    <div class="about-text">
      <p>Hi, I'm <strong>Akash</strong> — a passionate Photo & Video Editor and Photography enthusiast with a creative mindset and strong attention to detail. I enjoy turning simple moments into visually appealing stories.</p>
      <p>I love working on <strong>reels, aesthetic edits, fashion content, and emotional storytelling videos</strong> that create a strong connection with people. From color grading and transitions to capturing the perfect frame, I always focus on creating high-quality, engaging content.</p>
      <p>I'm constantly exploring new editing styles, trends, and creative ideas to improve my skills and bring fresh visuals to every project.</p>
      <div class="divider"></div>
      <div class="about-stats">
        <div class="stat-box">
          <div class="stat-num">3+</div>
          <div class="stat-label">Years Experience</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">50+</div>
          <div class="stat-label">Projects Done</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">4</div>
          <div class="stat-label">Core Services</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">∞</div>
          <div class="stat-label">Creative Ideas</div>
        </div>
      </div>
    </div>

    <div>
      <div class="section-label" style="margin-bottom: 1.5rem;">Design Tools</div>
      <div class="tools-list">
        <div class="tool-item">
          <span class="tool-name">Adobe Photoshop</span>
          <span class="tool-badge">Photo Editing</span>
        </div>
        <div class="tool-item">
          <span class="tool-name">CapCut</span>
          <span class="tool-badge">Video Editing</span>
        </div>
        <div class="tool-item">
          <span class="tool-name">Canva</span>
          <span class="tool-badge">Design & Branding</span>
        </div>
        <div class="tool-item">
          <span class="tool-name">AI Image Generation</span>
          <span class="tool-badge">Creative Assets</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services" class="services-section">
  <div class="section-label">What I Do</div>
  <h2 class="section-title">Services</h2>
  <div class="services-grid">
    <div class="service-card">
      <span class="service-num">01</span>
      <span class="service-icon">🎬</span>
      <div class="service-title">Video Editing</div>
      <div class="service-desc">Films, reels, shorts, and cinematic content with smooth transitions, color grading, and engaging visual storytelling.</div>
    </div>
    <div class="service-card">
      <span class="service-num">02</span>
      <span class="service-icon">📸</span>
      <div class="service-title">Photo Retouching</div>
      <div class="service-desc">Professional photo editing, skin retouching, color correction, and aesthetic enhancement for all types of photography.</div>
    </div>
    <div class="service-card">
      <span class="service-num">03</span>
      <span class="service-icon">✏️</span>
      <div class="service-title">Logo Design</div>
      <div class="service-desc">Clean, memorable logos and brand identities that reflect your vision and stand out across all platforms.</div>
    </div>
    <div class="service-card">
      <span class="service-num">04</span>
      <span class="service-icon">🎨</span>
      <div class="service-title">Graphics & Branding</div>
      <div class="service-desc">Social media posts, banners, posters, business cards, and complete branding packages tailored to your needs.</div>
    </div>
  </div>
</section>

<!-- PORTFOLIO -->
<section id="work">
  <div class="portfolio-header">
    <div>
      <div class="section-label">Selected Work</div>
      <h2 class="section-title">My Projects</h2>
    </div>
  </div>

  <div class="portfolio-grid">

    <div class="portfolio-item wide">
      <img src="https://images.unsplash.com/photo-1574717024653-61fd2cf4d44d?w=800&q=80" alt="Business Card Design">
      <div class="portfolio-overlay">
        <div class="portfolio-cat">Branding & Design</div>
        <div class="portfolio-name">AKXHZZZ_EDITZZ — Business Card</div>
        <span class="portfolio-tag">Gold & Black Edition</span>
      </div>
    </div>

    <div class="portfolio-item">
      <img src="https://images.unsplash.com/photo-1607082348824-0a96f2a4b9da?w=600&q=80" alt="New Year Design">
      <div class="portfolio-overlay">
        <div class="portfolio-cat">Social Media Design</div>
        <div class="portfolio-name">New Year 2026 Greeting</div>
        <span class="portfolio-tag">Festive Post</span>
      </div>
    </div>

    <div class="portfolio-item">
      <img src="https://images.unsplash.com/photo-1611532736597-de2d4265fba3?w=600&q=80" alt="Video Editing Work">
      <div class="portfolio-overlay">
        <div class="portfolio-cat">Video Editing</div>
        <div class="portfolio-name">Cinematic Reel Edit</div>
        <span class="portfolio-tag">Film / Reels</span>
      </div>
    </div>

    <div class="portfolio-item">
      <img src="https://images.unsplash.com/photo-1586953208448-b95a79798f07?w=600&q=80" alt="Product Photography">
      <div class="portfolio-overlay">
        <div class="portfolio-cat">Product Design</div>
        <div class="portfolio-name">Product Social Post</div>
        <span class="portfolio-tag">E-Commerce Content</span>
      </div>
    </div>

    <div class="portfolio-item">
      <img src="https://images.unsplash.com/photo-1561070791-2526d30994b5?w=600&q=80" alt="Logo Design">
      <div class="portfolio-overlay">
        <div class="portfolio-cat">Logo & Identity</div>
        <div class="portfolio-name">AE Brand Identity</div>
        <span class="portfolio-tag">Logo Design</span>
      </div>
    </div>

    <div class="portfolio-item wide">
      <img src="https://images.unsplash.com/photo-1542744094-24638eff58bb?w=800&q=80" alt="Social Media Design">
      <div class="portfolio-overlay">
        <div class="portfolio-cat">Social Media</div>
        <div class="portfolio-name">Festive & Seasonal Posts</div>
        <span class="portfolio-tag">Pongal • Christmas • Valentine's</span>
      </div>
    </div>

  </div>
</section>

<!-- CONTACT -->
<section id="contact" class="contact-section">
  <div class="contact-inner">
    <div class="section-label">Get In Touch</div>
    <h2 class="section-title">Let's Create Something<br><em style="font-style: italic; color: var(--gold);">Together</em></h2>
    <p style="color: var(--muted); line-height: 1.8; margin-top: 1rem; max-width: 500px;">
      Have a project in mind? Whether it's a reel, brand identity, or social campaign — I'd love to bring your vision to life.
    </p>
    <div class="contact-grid">
      <a href="tel:9043191722" class="contact-item">
        <span class="contact-icon">📞</span>
        <div>
          <div class="contact-label">Phone</div>
          <div class="contact-value">9043191722</div>
        </div>
      </a>
      <a href="mailto:crazyakash3853@gmail.com" class="contact-item">
        <span class="contact-icon">✉️</span>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-value">crazyakash3853@gmail.com</div>
        </div>
      </a>
      <a href="https://instagram.com/__.akxhzzz.__02" target="_blank" class="contact-item">
        <span class="contact-icon">📷</span>
        <div>
          <div class="contact-label">Instagram</div>
          <div class="contact-value">@__.akxhzzz.__02</div>
        </div>
      </a>
      <a href="https://instagram.com/achu.vijay.3152" target="_blank" class="contact-item">
        <span class="contact-icon">📱</span>
        <div>
          <div class="contact-label">Instagram (Alt)</div>
          <div class="contact-value">@achu.vijay.3152</div>
        </div>
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">AKASH</div>
  <div class="footer-tagline">Edit · Create · Inspire</div>
  <div class="footer-copy">© 2026 Akxhzzz_Editzz</div>
</footer>

</body>
</html>
