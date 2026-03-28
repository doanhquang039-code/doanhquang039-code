<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Doanhnocode – GitHub Profile Preview</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0e17;
    --surface: #111827;
    --surface2: #1a2236;
    --border: #1e2d45;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #10b981;
    --text: #e2e8f0;
    --muted: #64748b;
    --warm: #f59e0b;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 860px;
    margin: 0 auto;
    padding: 48px 24px;
    position: relative;
    z-index: 1;
  }

  /* HERO */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -40px; left: 50%;
    transform: translateX(-50%);
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(124,58,237,0.15) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-tag {
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    border: 1px solid rgba(0,212,255,0.3);
    padding: 4px 14px;
    border-radius: 100px;
    margin-bottom: 20px;
    animation: fadeInDown 0.6s ease both;
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(36px, 6vw, 64px);
    font-weight: 800;
    line-height: 1.1;
    animation: fadeInUp 0.7s 0.1s ease both;
  }

  .hero h1 .name {
    background: linear-gradient(135deg, #00d4ff 0%, #7c3aed 50%, #10b981 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    margin-top: 16px;
    color: var(--muted);
    font-size: 16px;
    font-weight: 300;
    animation: fadeInUp 0.7s 0.2s ease both;
  }

  .hero-badges {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 28px;
    animation: fadeInUp 0.7s 0.3s ease both;
  }

  .badge {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 6px 14px;
    border-radius: 6px;
    border: 1px solid;
  }
  .badge-blue { color: var(--accent); border-color: rgba(0,212,255,0.3); background: rgba(0,212,255,0.05); }
  .badge-purple { color: #a78bfa; border-color: rgba(124,58,237,0.3); background: rgba(124,58,237,0.05); }
  .badge-green { color: var(--accent3); border-color: rgba(16,185,129,0.3); background: rgba(16,185,129,0.05); }
  .badge-yellow { color: var(--warm); border-color: rgba(245,158,11,0.3); background: rgba(245,158,11,0.05); }

  /* DIVIDER */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 40px 0;
  }

  /* SECTION LABEL */
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ABOUT */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  @media (max-width: 600px) { .about-grid { grid-template-columns: 1fr; } }

  .about-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px;
    transition: border-color 0.2s, transform 0.2s;
  }
  .about-item:hover {
    border-color: rgba(0,212,255,0.3);
    transform: translateY(-2px);
  }
  .about-icon { font-size: 18px; flex-shrink: 0; margin-top: 2px; }
  .about-text { font-size: 14px; color: var(--muted); line-height: 1.5; }
  .about-text strong { color: var(--text); }

  /* TECH STACK */
  .tech-group { margin-bottom: 24px; }

  .tech-group-title {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 10px;
  }

  .tech-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .chip {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 12px;
    font-weight: 500;
    padding: 6px 12px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text);
    transition: all 0.2s;
    cursor: default;
  }
  .chip:hover {
    border-color: rgba(0,212,255,0.4);
    background: var(--surface2);
    transform: translateY(-1px);
  }
  .chip .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  /* PROJECTS */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
  }
  @media (max-width: 600px) { .projects-grid { grid-template-columns: 1fr; } }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px;
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
    text-decoration: none;
    display: block;
    color: inherit;
  }
  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity 0.25s;
  }
  .project-card:hover {
    border-color: rgba(0,212,255,0.25);
    transform: translateY(-3px);
    box-shadow: 0 12px 40px rgba(0,0,0,0.4);
  }
  .project-card:hover::before { opacity: 1; }

  .project-emoji { font-size: 28px; margin-bottom: 10px; }
  .project-name {
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 600;
    margin-bottom: 6px;
  }
  .project-desc {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.5;
    margin-bottom: 12px;
  }
  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .project-tag {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    padding: 2px 8px;
    border-radius: 4px;
    background: rgba(0,212,255,0.08);
    color: var(--accent);
    border: 1px solid rgba(0,212,255,0.15);
  }

  /* STATS */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 12px;
  }
  @media (max-width: 600px) { .stats-row { grid-template-columns: 1fr; } }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    text-align: center;
  }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 28px;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .stat-label {
    font-size: 11px;
    color: var(--muted);
    margin-top: 4px;
  }

  /* CONTACT */
  .contact-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    justify-content: center;
  }
  .contact-btn {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 12px 20px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--text);
    text-decoration: none;
    font-size: 13px;
    font-weight: 500;
    transition: all 0.2s;
  }
  .contact-btn:hover {
    border-color: rgba(0,212,255,0.4);
    background: var(--surface2);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
  }
  .contact-btn svg { flex-shrink: 0; }

  /* STATS CARDS */
  .stats-cards-row {
    width: 100%;
    max-width: 640px;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .stats-bottom-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  @media (max-width: 500px) { .stats-bottom-row { grid-template-columns: 1fr; } }

  .stat-img-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 14px;
    overflow: hidden;
  }
  .stat-img-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 10px;
  }
  .stat-fallback {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 80px;
  }
  .stat-link {
    color: var(--accent);
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    text-decoration: none;
    border: 1px solid rgba(0,212,255,0.3);
    padding: 8px 16px;
    border-radius: 8px;
    transition: all 0.2s;
  }
  .stat-link:hover { background: rgba(0,212,255,0.1); }

  /* FOOTER */
  .footer {
    text-align: center;
    padding: 40px 0 20px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
  }
  .footer span { color: var(--accent); }

  /* ANIMATIONS */
  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeInDown {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  section { animation: fadeInUp 0.6s ease both; }
</style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-tag">// open to work · vietnam 🇻🇳</div>
    <h1>Hi, I'm <span class="name">Doanhnocode</span> 👋</h1>
    <p class="hero-sub">Software Developer · Building things that matter · Lifelong Learner</p>
    <div class="hero-badges">
      <span class="badge badge-blue">Spring Boot</span>
      <span class="badge badge-purple">Flutter</span>
      <span class="badge badge-green">Node.js</span>
      <span class="badge badge-yellow">Aspiring DevOps</span>
    </div>
  </div>

  <div class="divider"></div>

  <!-- ABOUT -->
  <section>
    <div class="section-label">About Me</div>
    <div class="about-grid">
      <div class="about-item">
        <span class="about-icon">🎓</span>
        <div class="about-text"><strong>CS Student</strong> passionate about building real-world software</div>
      </div>
      <div class="about-item">
        <span class="about-icon">🌱</span>
        <div class="about-text">Currently leveling up in <strong>Spring Boot, Node.js & Flutter</strong></div>
      </div>
      <div class="about-item">
        <span class="about-icon">☁️</span>
        <div class="about-text">Aspiring <strong>DevOps & Cloud Engineer</strong> — big goals, steady steps</div>
      </div>
      <div class="about-item">
        <span class="about-icon">🚀</span>
        <div class="about-text">Dream: <strong>Build products</strong> that solve real-world problems</div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- TECH STACK -->
  <section>
    <div class="section-label">Tech Stack</div>

    <div class="tech-group">
      <div class="tech-group-title">Backend</div>
      <div class="tech-chips">
        <div class="chip"><span class="dot" style="background:#ED8B00"></span>Java</div>
        <div class="chip"><span class="dot" style="background:#6DB33F"></span>Spring Boot</div>
        <div class="chip"><span class="dot" style="background:#339933"></span>Node.js</div>
        <div class="chip"><span class="dot" style="background:#ffffff"></span>Express.js</div>
        <div class="chip"><span class="dot" style="background:#239120"></span>C#</div>
        <div class="chip"><span class="dot" style="background:#512BD4"></span>.NET</div>
        <div class="chip"><span class="dot" style="background:#3DDC84"></span>Android</div>
      </div>
    </div>

    <div class="tech-group">
      <div class="tech-group-title">Frontend & Mobile</div>
      <div class="tech-chips">
        <div class="chip"><span class="dot" style="background:#F7DF1E"></span>JavaScript</div>
        <div class="chip"><span class="dot" style="background:#3178C6"></span>TypeScript</div>
        <div class="chip"><span class="dot" style="background:#E34F26"></span>HTML5</div>
        <div class="chip"><span class="dot" style="background:#1572B6"></span>CSS3</div>
        <div class="chip"><span class="dot" style="background:#02569B"></span>Flutter</div>
      </div>
    </div>

    <div class="tech-group">
      <div class="tech-group-title">Database & Tools</div>
      <div class="tech-chips">
        <div class="chip"><span class="dot" style="background:#4479A1"></span>MySQL</div>
        <div class="chip"><span class="dot" style="background:#47A248"></span>MongoDB</div>
        <div class="chip"><span class="dot" style="background:#CC2927"></span>SQL Server</div>
        <div class="chip"><span class="dot" style="background:#2496ED"></span>Docker</div>
        <div class="chip"><span class="dot" style="background:#F05032"></span>Git</div>
        <div class="chip"><span class="dot" style="background:#007ACC"></span>VS Code</div>
        <div class="chip"><span class="dot" style="background:#181717"></span>GitHub</div>
        <div class="chip"><span class="dot" style="background:#FF6C37"></span>Postman</div>
        <div class="chip"><span class="dot" style="background:#3448C5"></span>Cloudinary</div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- PROJECTS -->
  <section>
    <div class="section-label">Projects</div>
    <div class="projects-grid">

      <a class="project-card" href="https://github.com/doanhquang039-code/hr-managerment-system" target="_blank">
        <div class="project-emoji">🏢</div>
        <div class="project-name">HR Management System</div>
        <div class="project-desc">Human resource management with Spring Security & Spring Cloud microservices</div>
        <div class="project-tags">
          <span class="project-tag">Spring Boot</span>
          <span class="project-tag">MySQL</span>
          <span class="project-tag">Docker</span>
          <span class="project-tag">Cloudinary</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/doanhquang039-code/app" target="_blank">
        <div class="project-emoji">📱</div>
        <div class="project-name">Flutter App</div>
        <div class="project-desc">Cross-platform mobile application built with Flutter & SQL Server backend</div>
        <div class="project-tags">
          <span class="project-tag">Flutter</span>
          <span class="project-tag">TypeScript</span>
          <span class="project-tag">SQL Server</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/doanhquang039-code/node-my-blog" target="_blank">
        <div class="project-emoji">🌐</div>
        <div class="project-name">NodeJS Blog</div>
        <div class="project-desc">Personal blog platform built with Node.js, EJS templating & Cloudinary</div>
        <div class="project-tags">
          <span class="project-tag">Node.js</span>
          <span class="project-tag">EJS</span>
          <span class="project-tag">MySQL</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/doanhquang039-code/TourHotel" target="_blank">
        <div class="project-emoji">🏨</div>
        <div class="project-name">Tour Hotel Booking</div>
        <div class="project-desc">Hotel & tour booking website using Java Servlet JSP architecture</div>
        <div class="project-tags">
          <span class="project-tag">Java</span>
          <span class="project-tag">JSP/Servlet</span>
          <span class="project-tag">MySQL</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/doanhquang039-code/libraliry" target="_blank">
        <div class="project-emoji">📚</div>
        <div class="project-name">Library System</div>
        <div class="project-desc">Desktop app for book borrowing & management with SQL Server</div>
        <div class="project-tags">
          <span class="project-tag">Java</span>
          <span class="project-tag">SQL Server</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/doanhquang039-code/C-ADCSoftWare" target="_blank">
        <div class="project-emoji">🖥️</div>
        <div class="project-name">ADC Software</div>
        <div class="project-desc">Desktop software built with C# and .NET framework</div>
        <div class="project-tags">
          <span class="project-tag">C#</span>
          <span class="project-tag">.NET</span>
        </div>
      </a>

    </div>
  </section>

  <div class="divider"></div>

  <!-- STATS -->
  <section>
    <div class="section-label">GitHub Stats</div>
    <div style="text-align:center; display:flex; flex-direction:column; gap:16px; align-items:center;">

      <!-- Stats cards using object tags as fallback for blocked images -->
      <div class="stats-cards-row">
        <div class="stat-img-card">
          <div class="stat-img-label">📊 General Stats</div>
          <object
            data="https://github-readme-stats.vercel.app/api?username=doanhquang039-code&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=00d4ff&icon_color=7c3aed&text_color=e2e8f0&border_radius=12"
            type="image/svg+xml"
            style="width:100%; height:180px; border-radius:12px; display:block;">
            <div class="stat-fallback">
              <a href="https://github.com/doanhquang039-code" target="_blank" class="stat-link">
                🔗 View GitHub Profile Stats
              </a>
            </div>
          </object>
        </div>

        <div class="stats-bottom-row">
          <div class="stat-img-card">
            <div class="stat-img-label">💻 Top Languages</div>
            <object
              data="https://github-readme-stats.vercel.app/api/top-langs/?username=doanhquang039-code&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=00d4ff&text_color=e2e8f0&border_radius=12"
              type="image/svg+xml"
              style="width:100%; height:150px; border-radius:12px; display:block;">
              <div class="stat-fallback">
                <a href="https://github.com/doanhquang039-code" target="_blank" class="stat-link">🔗 Top Languages</a>
              </div>
            </object>
          </div>

          <div class="stat-img-card">
            <div class="stat-img-label">🔥 Streak Stats</div>
            <object
              data="https://streak-stats.demolab.com/?user=doanhquang039-code&theme=tokyonight&hide_border=true&background=0d1117&ring=00d4ff&fire=7c3aed&currStreakLabel=00d4ff&border_radius=12"
              type="image/svg+xml"
              style="width:100%; height:150px; border-radius:12px; display:block;">
              <div class="stat-fallback">
                <a href="https://github.com/doanhquang039-code" target="_blank" class="stat-link">🔗 Streak Stats</a>
              </div>
            </object>
          </div>
        </div>
      </div>

      <!-- Quick stat numbers -->
      <div class="stats-row" style="width:100%; max-width:600px;">
        <div class="stat-card">
          <div class="stat-num">6+</div>
          <div class="stat-label">Projects</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">8+</div>
          <div class="stat-label">Technologies</div>
        </div>
        <div class="stat-card">
          <div class="stat-num">🇻🇳</div>
          <div class="stat-label">Based in Vietnam</div>
        </div>
      </div>

      <a href="https://github.com/doanhquang039-code" target="_blank" class="contact-btn" style="margin-top:4px;">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="#e2e8f0"><path d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.166 6.839 9.489.5.092.682-.217.682-.483 0-.237-.009-.868-.013-1.703-2.782.605-3.369-1.342-3.369-1.342-.454-1.155-1.11-1.463-1.11-1.463-.908-.62.069-.608.069-.608 1.004.07 1.532 1.032 1.532 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .269.18.58.688.482A10.001 10.001 0 0022 12c0-5.523-4.477-10-10-10z"/></svg>
        View Full GitHub Profile →
      </a>
    </div>
  </section>

  <div class="divider"></div>

  <!-- CONTACT -->
  <section>
    <div class="section-label">Contact Me</div>
    <div class="contact-row">
      <a href="/cdn-cgi/l/email-protection#0b6f646a65637a7e6a656c3b38324b6c666a626725686466" class="contact-btn">
        <svg width="16" height="16" fill="none" viewBox="0 0 24 24" stroke="#00d4ff" stroke-width="2"><path d="M4 4h16v16H4z" rx="2"/><path d="M22 7l-10 7L2 7"/></svg>
        <span class="__cf_email__" data-cfemail="8de9e2ece3e5fcf8ece3eabdbeb4cdeae0ece4e1a3eee2e0">[email&#160;protected]</span>
      </a>
      <a href="https://zalo.me/0373542982" class="contact-btn">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="#0068FF"><rect width="24" height="24" rx="6" fill="#0068FF"/><text x="4" y="17" font-size="10" fill="white" font-weight="bold">Za</text></svg>
        0373542982
      </a>
      <a href="https://github.com/doanhquang039-code" class="contact-btn">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="#e2e8f0"><path d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.166 6.839 9.489.5.092.682-.217.682-.483 0-.237-.009-.868-.013-1.703-2.782.605-3.369-1.342-3.369-1.342-.454-1.155-1.11-1.463-1.11-1.463-.908-.62.069-.608.069-.608 1.004.07 1.532 1.032 1.532 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .269.18.58.688.482A10.001 10.001 0 0022 12c0-5.523-4.477-10-10-10z"/></svg>
        doanhquang039-code
      </a>
    </div>
  </section>

  <div class="footer">
    <p>⭐ <span>Feel free to explore</span> my repos and leave a star if you find something us
