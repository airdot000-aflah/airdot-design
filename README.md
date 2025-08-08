<!DOCTYPE html>
<html lang="ml">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Airdot — Minimal Portfolio</title>
<style>
  :root{
    --bg:#0f1724;
    --card:#0b1220;
    --muted:#94a3b8;
    --accent:#00c2a8;
    --glass: rgba(156, 77, 77, 0.04);
    --radius:14px;
    --maxw:1100px;
    font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
  }
  *{box-sizing:border-box}
  body{
    margin:0;
    background: linear-gradient(180deg,#071025 0%, #071424 100%);
    color:#e6eef6;
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    line-height:1.5;
  }
  .container{max-width:var(--maxw);margin:0 auto;padding:28px;}
  header{display:flex;align-items:center;justify-content:space-between;padding:10px 0}
  .brand{display:flex;gap:12px;align-items:center}
  .logo{
    width:46px;height:46px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#00a6d6);
    display:flex;align-items:center;justify-content:center;font-weight:700;color:#02111b;font-size:18px;
    box-shadow:0 6px 20px rgba(2,18,26,0.45);
  }
  nav ul{display:flex;gap:18px;list-style:none;margin:0;padding:0}
  nav a{color:var(--muted);text-decoration:none;font-weight:600}
  .cta{background:var(--accent);color:#012026;padding:10px 14px;border-radius:10px;text-decoration:none;font-weight:700}
  /* hero */
  .hero{display:grid;grid-template-columns:1fr 420px;gap:28px;align-items:center;padding:36px 0}
  .eyebrow{color:var(--muted);font-weight:600;margin-bottom:8px}
  h1{font-size:36px;margin:0 0 12px 0;line-height:1.05}
  p.lead{color:var(--muted);margin:0 0 20px 0;max-width:56ch}
  .hero-actions{display:flex;gap:12px;align-items:center}
  .btn-outline{border:1px solid rgba(255,255,255,0.08);padding:10px 12px;border-radius:10px;color:var(--muted);text-decoration:none;font-weight:600}
  /* hero right card */
  .card{background:var(--card);border-radius:18px;padding:18px;box-shadow:0 8px 30px rgba(2,12,20,0.6);backdrop-filter:blur(6px)}
  .stats{display:flex;gap:12px;flex-wrap:wrap}
  .stat{flex:1;min-width:120px;padding:12px;background:var(--glass);border-radius:12px;text-align:center}
  .stat h3{margin:0;font-size:20px}
  .stat p{margin:6px 0 0 0;color:var(--muted);font-size:13px}
  /* services */
  .services{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin:28px 0}
  .service{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:18px;border-radius:12px}
  .service h4{margin:0 0 8px 0}
  .service p{margin:0;color:var(--muted);font-size:14px}
  /* portfolio */
  .portfolio{margin:28px 0}
  .grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
  .tile{position:relative;border-radius:12px;overflow:hidden;cursor:pointer;background:#111827}
  .tile img{width:100%;height:220px;object-fit:cover;display:block;transition:transform .35s ease}
  .tile .meta{
    position:absolute;left:0;right:0;bottom:0;padding:12px;background:linear-gradient(180deg, transparent, rgba(2,6,10,0.7));
    color:#fff;font-weight:700;
  }
  .tile:hover img{transform:scale(1.06)}
  .tile .tag{position:absolute;top:10px;left:10px;background:rgba(0,0,0,0.45);padding:6px 8px;border-radius:8px;font-size:12px}
  /* testimonial */
  .testimonials{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:28px 0}
  .tcard{background:var(--card);padding:16px;border-radius:12px}
  .avatar{width:48px;height:48px;border-radius:10px;object-fit:cover}
  .stars{color:#ffd166;margin-top:6px}
  /* footer */
  footer{margin-top:40px;padding:20px 0;border-top:1px solid rgba(255,255,255,0.03)}
  .footer-grid{display:flex;justify-content:space-between;gap:18px;flex-wrap:wrap}
  .contact{min-width:220px}
  /* modal */
  .modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(2,6,10,0.6);padding:18px;z-index:60}
  .modal.show{display:flex}
  .modal .modal-content{max-width:900px;width:100%;background:#021423;padding:12px;border-radius:12px}
  .close-btn{background:transparent;border:0;color:var(--muted);font-size:18px;cursor:pointer}
  /* responsive */
  @media (max-width:980px){
    .hero{grid-template-columns:1fr;gap:18px}
    .services{grid-template-columns:repeat(2,1fr)}
    .grid{grid-template-columns:repeat(2,1fr)}
    .testimonials{grid-template-columns:1fr}
  }
  @media (max-width:560px){
    nav ul{display:none}
    .mobile-toggle{display:block}
    .services{grid-template-columns:1fr}
    .grid{grid-template-columns:1fr}
  }
  .mobile-toggle{display:none;background:transparent;border:1px solid rgba(255,255,255,0.06);padding:8px 10px;border-radius:10px;color:var(--muted);cursor:pointer}
  .nav-open{position:fixed;top:0;left:0;right:0;background:linear-gradient(180deg, rgba(1,8,12,0.98), rgba(1,8,12,0.98));padding:18px;z-index:80}
  .nav-open ul{display:flex;flex-direction:column;gap:12px}
  .small{font-size:13px;color:var(--muted)}
  .pill{display:inline-block;padding:6px 10px;background:rgba(255,255,255,0.02);border-radius:999px;font-weight:600}
</style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">AD</div>
        <div>
          <div style="font-weight:800;font-size:16px">Airdot</div>
          <div class="small">Wireless — Creative — Minimal</div>
        </div>
      </div>

      <nav>
        <ul>
          <li><a href="#services">Services</a></li>
          <li><a href="#portfolio">Portfolio</a></li>
          <li><a href="#testimonials">Testimonials</a></li>
          <li><a href="#contact" class="cta">Contact</a></li>
        </ul>
      </nav>

      <button class="mobile-toggle" id="mobileToggle">☰</button>
    </header>

    <!-- HERO -->
    <section class="hero" id="home">
      <div>
        <div class="eyebrow pill">Experience Wireless Like Never Before</div>
        <h1>Design & Production for modern digital brands</h1>
        <p class="lead">Airdot crafts sleek visuals, videos and campaigns — from model direction and posters to full production videography. Clean minimalism that converts.</p>
        <div class="hero-actions">
          <a href="#contact" class="cta">Get a Quote</a>
          <a href="#portfolio" class="btn-outline">See Works</a>
        </div>

        <!-- quick features -->
        <div style="display:flex;gap:12px;margin-top:18px;flex-wrap:wrap">
          <div style="background:var(--glass);padding:10px 12px;border-radius:10px"><strong>Fast Turnaround</strong><div class="small">48–72h drafts</div></div>
          <div style="background:var(--glass);padding:10px 12px;border-radius:10px"><strong>Studio-grade</strong><div class="small">AI & Live Audio</div></div>
          <div style="background:var(--glass);padding:10px 12px;border-radius:10px"><strong>Responsive</strong><div class="small">Mobile-first designs</div></div>
        </div>
      </div>

      <aside>
        <div class="card">
          <div style="display:flex;justify-content:space-between;align-items:center">
            <strong>Quick Stats</strong>
            <span class="small">Updated Recently</span>
          </div>
          <div style="height:12px"></div>
          <div class="stats">
            <div class="stat">
              <h3>120+</h3>
              <p>Projects</p>
            </div>
            <div class="stat">
              <h3>85%</h3>
              <p>Repeat Clients</p>
            </div>
            <div class="stat">
              <h3>5+</h3>
              <p>Years Experience</p>
            </div>
          </div>
          <div style="height:12px"></div>
          <div style="display:flex;gap:8px;align-items:center;justify-content:space-between">
            <div>
              <div class="small">Top services</div>
              <div style="font-weight:800">Poster · Video · Photography</div>
            </div>
            <div>
              <a class="btn-outline" href="#contact">Book a Call</a>
            </div>
          </div>
        </div>
      </aside>
    </section>

    <!-- services -->
    <section id="services">
      <h2 style="margin-bottom:12px">Services</h2>
      <div class="services">
        <div class="service">
          <h4>MODELS</h4>
          <p>Model direction, casting support, on-set styling and full shoot coordination.</p>
        </div>
        <div class="service">
          <h4>POSTER</h4>
          <p>Bold poster designs for print & socials — prepared with print-safe colours and bleed.</p>
        </div>
        <div class="service">
          <h4>VIDEO</h4>
          <p>Short-form ads, product videos, and social content — from script to final edit.</p>
        </div>
        <div class="service">
          <h4>PHOTOGRAPHY</h4>
          <p>Product, lifestyle and studio photography with professional retouching.</p>
        </div>
        <div class="service">
          <h4>VIDEOGRAPHY</h4>
          <p>Full production videography — multi-camera, drone-ready, colour grading included.</p>
        </div>
        <div class="service">
          <h4>BRANDING</h4>
          <p>Logo, visual systems and brand assets to keep your identity consistent.</p>
        </div>
      </div>
    </section>

    <!-- portfolio -->
    <section id="portfolio" class="portfolio">
      <h2 style="margin-bottom:12px">Portfolio</h2>
      <div class="grid">
        <!-- tile 1 -->
        <div class="tile" data-type="Poster" data-title="Airdot Launch Poster" data-desc="High-contrast poster for new product launch" onclick="openModal(this)">
          <div class="tag">POSTER</div>
          <img src="https://images.unsplash.com/photo-1503602642458-232111445657?w=1200&q=60" alt="poster sample" />
          <div class="meta">
            Airdot Launch Poster
          </div>
        </div>
        <!-- tile 2 -->
        <div class="tile" data-type="Video" data-title="Product Film" data-desc="30s product highlight" onclick="openModal(this)">
          <div class="tag">VIDEO</div>
          <img src="https://images.unsplash.com/photo-1515378791036-0648a3ef77b2?w=1200&q=60" alt="video sample" />
          <div class="meta">Product Film — 30s</div>
        </div>
        <!-- tile 3 -->
        <div class="tile" data-type="Photography" data-title="Lifestyle Shoot" data-desc="Lifestyle images for social" onclick="openModal(this)">
          <div class="tag">PHOTOGRAPHY</div>
          <img src="https://images.unsplash.com/photo-1507120410856-1f35574c3b45?w=1200&q=60" alt="photography sample" />
          <div class="meta">Lifestyle Shoot</div>
        </div>
        <!-- tile 4 -->
        <div class="tile" data-type="Models" data-title="Model Portfolio" data-desc="Lookbook and portfolio" onclick="openModal(this)">
          <div class="tag">MODELS</div>
          <img src="https://images.unsplash.com/photo-1520975924231-41a7c68a1b99?w=1200&q=60" alt="models" />
          <div class="meta">Model Lookbook</div>
        </div>
        <!-- tile 5 -->
        <div class="tile" data-type="Videography" data-title="Drone Capture" data-desc="Aerial drone shots" onclick="openModal(this)">
          <div class="tag">VIDEOGRAPHY</div>
          <img src="https://images.unsplash.com/photo-1504198453319-5ce911bafcde?w=1200&q=60" alt="drone" />
          <div class="meta">Drone Capture</div>
        </div>
        <!-- tile 6 -->
        <div class="tile" data-type="Poster" data-title="Event Poster" data-desc="Poster for campus event" onclick="openModal(this)">
          <div class="tag">POSTER</div>
          <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?w=1200&q=60" alt="event poster" />
          <div class="meta">Event Poster</div>
        </div>
      </div>
    </section>

    <!-- testimonials -->
    <section id="testimonials">
      <h2 style="margin-bottom:12px">What clients say</h2>
      <div class="testimonials">
        <div class="tcard">
          <div style="display:flex;gap:12px;align-items:center">
            <img class="avatar" src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=200&q=60" alt="client" />
            <div>
              <strong>Riya K.</strong>
              <div class="small">Marketing Lead</div>
            </div>
          </div>
          <div style="margin-top:12px">Airdot's video cut our conversion cost by 30% — fast, clean and very collaborative.</div>
          <div class="stars">★★★★★</div>
        </div>

        <div class="tcard">
          <div style="display:flex;gap:12px;align-items:center">
            <img class="avatar" src="https://images.unsplash.com/photo-1545996124-1bbd3f6c2a7a?w=200&q=60" alt="client2" />
            <div>
              <strong>Sameer P.</strong>
              <div class="small">Founder</div>
            </div>
          </div>
          <div style="margin-top:12px">Poster design was print-ready and the team handled everything end-to-end.</div>
          <div class="stars">★★★★☆</div>
        </div>

        <div class="tcard">
          <div style="display:flex;gap:12px;align-items:center">
            <img class="avatar" src="https://images.unsplash.com/photo-1545996124-60b2ef6b87aa?w=200&q=60" alt="client3" />
            <div>
              <strong>Annie G.</strong>
              <div class="small">Creative Director</div>
            </div>
          </div>
          <div style="margin-top:12px">Excellent photography and retouching. Highly recommend for product shoots.</div>
          <div class="stars">★★★★★</div>
        </div>
      </div>
    </section>

    <!-- contact -->
    <section id="contact" style="margin-top:28px">
      <h2>Contact</h2>
      <div style="display:grid;grid-template-columns:1fr 360px;gap:18px;align-items:start;margin-top:12px">
        <div>
          <p class="small">Interested in a project? Tell us briefly about your idea and we'll get back within 24 hours.</p>
          <form onsubmit="submitForm(event)" style="display:flex;flex-direction:column;gap:10px">
            <input required name="name" placeholder="Your name" style="padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit" />
            <input required name="email" type="email" placeholder="Email" style="padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit" />
            <textarea required name="message" placeholder="Project brief" rows="4" style="padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:inherit"></textarea>
            <div style="display:flex;gap:10px">
              <button class="cta" type="submit">Send</button>
              <button type="button" class="btn-outline" onclick="openEmail()">Email Us</button>
            </div>
          </form>
        </div>

        <aside class="card contact">
          <div style="font-weight:800">Airdot design</div>
          <div class="small" style="margin-top:8px">Email: <strong>airdot000@gmail.com</strong></div>
          <div class="small">Phone: <strong>+91 8714559096</strong></div>
          <div style="height:12px"></div>
          <div class="small">Follow airdot_design</div>
          <div style="display:flex;gap:8px;margin-top:8px">
            <div class="pill">Instagram</div>
          </div>
        </aside>
      </div>
    </section>

    <footer>
      <div style="display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap">
        <div class="small">© <strong>Airdot</strong> — Designed by you &amp; this template</div>
        <div class="small">Made with ♥ for minimal brands</div>
      </div>
    </footer>
  </div>

  <!-- modal -->
  <div id="modal" class="modal" onclick="closeModal(event)">
    <div class="modal-content" onclick="event.stopPropagation()">
      <div style="display:flex;justify-content:space-between;align-items:center">
        <div>
          <strong id="mTitle">Title</strong>
          <div id="mType" class="small" style="margin-top:4px"></div>
        </div>
        <button class="close-btn" onclick="closeModal(event)">✕ Close</button>
      </div>
      <div style="height:12px"></div>
      <div style="display:flex;gap:12px;align-items:flex-start;flex-wrap:wrap">
        <img id="mImg" src="" style="width:320px;height:220px;object-fit:cover;border-radius:8px" alt="preview" />
        <div style="flex:1">
          <p id="mDesc" class="small"></p>
          <div style="height:8px"></div>
          <div style="display:flex;gap:8px">
            <a class="cta" id="viewBtn" href="#" target="_blank">Open</a>
            <button class="btn-outline" onclick="downloadSample()">Download</button>
          </div>
        </div>
      </div>
    </div>
  </div>

<script>
  // mobile nav toggle (very simple)
  const mobileToggle = document.getElementById('mobileToggle');
  mobileToggle && mobileToggle.addEventListener('click', ()=> {
    const nav = document.querySelector('nav');
    const open = document.createElement('div');
    open.className = 'nav-open';
    open.innerHTML = '<ul><li><a href=\"#services\">Services</a></li><li><a href=\"#portfolio\">Portfolio</a></li><li><a href=\"#testimonials\">Testimonials</a></li><li><a href=\"#contact\">Contact</a></li></ul><div style=\"height:12px\"></div><button onclick=\"document.querySelector(\\'.nav-open\\').remove()\" class=\"btn-outline\">Close</button>';
    document.body.appendChild(open);
  });

  // modal functions
  function openModal(el){
    const modal = document.getElementById('modal');
    const title = el.getAttribute('data-title') || 'Project';
    const type = el.getAttribute('data-type') || '';
    const desc = el.getAttribute('data-desc') || '';
    const img = el.querySelector('img')?.src || '';

    document.getElementById('mTitle').innerText = title;
    document.getElementById('mType').innerText = type;
    document.getElementById('mDesc').innerText = desc;
    document.getElementById('mImg').src = img;
    document.getElementById('viewBtn').href = img;

    modal.classList.add('show');
    document.body.style.overflow = 'hidden';
  }
  function closeModal(ev){
    ev && ev.stopPropagation && ev.stopPropagation();
    const modal = document.getElementById('modal');
    modal.classList.remove('show');
    document.body.style.overflow = '';
  }

  // contact form (demo)
  function submitForm(e){
    e.preventDefault();
    const f = e.target;
    // simple client-side "thank you" experience
    alert('Thanks — message received! We will reach out soon.');
    f.reset();
  }
  function openEmail(){
    window.location.href = 'mailto:hello@airdot.example?subject=Project%20Inquiry';
  }
  function downloadSample(){
    alert('Sample download action (replace with real file link).');
  }
</script>
</body>
</html>
