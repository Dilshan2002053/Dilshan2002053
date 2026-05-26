<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Rohitha Dilshan | Advanced Portfolio</title>
  <!-- Google Fonts + Font Awesome + Skill Icons -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800;14..32,900&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Animate.css for smooth entrances -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      transition: background-color 0.3s cubic-bezier(0.2, 0.9, 0.4, 1.1), 
                  color 0.2s ease, 
                  border-color 0.2s ease,
                  box-shadow 0.2s ease,
                  transform 0.2s ease;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--bg-primary);
      color: var(--text-primary);
      line-height: 1.5;
      scroll-behavior: smooth;
      overflow-x: hidden;
    }

    /* ================= LIGHT & DARK THEMES (ADVANCED) ================= */
    :root {
      /* Light mode (elegant white/purple accents) */
      --bg-primary: #fef9ff;
      --bg-secondary: #ffffff;
      --bg-glass: rgba(255, 255, 255, 0.75);
      --card-bg: rgba(255, 255, 255, 0.9);
      --card-border: rgba(138, 43, 226, 0.15);
      --text-primary: #1a102f;
      --text-secondary: #4a3a6e;
      --accent-primary: #8A2BE2;
      --accent-soft: #c084fc;
      --accent-glow: rgba(138, 43, 226, 0.2);
      --badge-bg: #f2eaff;
      --badge-text: #4c1d95;
      --shadow-sm: 0 8px 20px rgba(0, 0, 0, 0.03), 0 2px 4px rgba(0, 0, 0, 0.05);
      --shadow-md: 0 20px 35px -10px rgba(138, 43, 226, 0.15);
      --shadow-glow: 0 0 15px rgba(138, 43, 226, 0.3);
      --gradient-bg: linear-gradient(135deg, #f8f3ff 0%, #ffffff 100%);
      --toggle-bg: #e9defa;
      --toggle-circle: #8A2BE2;
      --border-light: rgba(0, 0, 0, 0.05);
      --footer-border: #e9e2f5;
    }

    body.dark {
      /* Dark mode (deep space with vibrant purple) */
      --bg-primary: #0b081a;
      --bg-secondary: #13102b;
      --bg-glass: rgba(19, 16, 43, 0.8);
      --card-bg: rgba(20, 18, 40, 0.85);
      --card-border: rgba(138, 43, 226, 0.4);
      --text-primary: #f0eaff;
      --text-secondary: #c4b5fd;
      --accent-primary: #c77dff;
      --accent-soft: #b366ff;
      --accent-glow: rgba(199, 125, 255, 0.25);
      --badge-bg: #2a1e4a;
      --badge-text: #e2d9ff;
      --shadow-sm: 0 8px 20px rgba(0, 0, 0, 0.4);
      --shadow-md: 0 20px 35px -8px rgba(0, 0, 0, 0.6);
      --shadow-glow: 0 0 18px rgba(199, 125, 255, 0.4);
      --gradient-bg: linear-gradient(145deg, #0f0b24 0%, #181338 100%);
      --toggle-bg: #302a4e;
      --toggle-circle: #f0b27a;
      --border-light: rgba(255, 255, 255, 0.08);
      --footer-border: #25204a;
    }

    /* global glassmorphic cards */
    .glass-card {
      background: var(--card-bg);
      backdrop-filter: blur(10px);
      border: 1px solid var(--card-border);
      border-radius: 2rem;
      box-shadow: var(--shadow-sm);
      transition: all 0.3s ease;
    }

    .glass-card:hover {
      transform: translateY(-6px);
      box-shadow: var(--shadow-md);
      border-color: var(--accent-soft);
    }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 1.5rem 2rem;
    }

    /* Navigation & Theme Toggle (Advanced) */
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1.5rem;
      padding: 1rem 0;
    }
    .logo {
      font-weight: 800;
      font-size: 1.9rem;
      background: linear-gradient(135deg, var(--accent-primary), var(--accent-soft));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.02em;
    }
    .theme-switch-wrapper {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      background: var(--badge-bg);
      padding: 0.35rem 1rem;
      border-radius: 60px;
      backdrop-filter: blur(4px);
    }
    .theme-switch {
      position: relative;
      display: inline-block;
      width: 64px;
      height: 32px;
    }
    .theme-switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }
    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: var(--toggle-bg);
      transition: 0.4s;
      border-radius: 34px;
    }
    .slider:before {
      position: absolute;
      content: "";
      height: 25px;
      width: 25px;
      left: 4px;
      bottom: 3.5px;
      background-color: var(--toggle-circle);
      transition: 0.4s;
      border-radius: 50%;
      box-shadow: 0 1px 3px rgba(0,0,0,0.2);
    }
    input:checked + .slider:before {
      transform: translateX(31px);
    }

    /* Hero section */
    .hero {
      text-align: center;
      margin: 2rem 0 2.5rem;
    }
    .avatar-icon {
      font-size: 4rem;
      background: linear-gradient(145deg, var(--accent-primary), var(--accent-soft));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .typing-area {
      min-height: 90px;
      font-size: 1.8rem;
      font-weight: 700;
    }
    .badge-group {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin: 1.5rem 0;
    }
    .social-badge {
      background: var(--badge-bg);
      padding: 0.7rem 1.3rem;
      border-radius: 40px;
      display: inline-flex;
      align-items: center;
      gap: 10px;
      color: var(--badge-text);
      text-decoration: none;
      font-weight: 600;
      transition: all 0.2s;
      font-size: 0.95rem;
    }
    .social-badge:hover {
      background: var(--accent-primary);
      color: white;
      transform: scale(1.05);
      box-shadow: var(--shadow-glow);
    }

    /* section headings */
    .section-head {
      font-size: 2rem;
      font-weight: 800;
      margin: 2rem 0 1.2rem;
      display: inline-block;
      background: linear-gradient(120deg, var(--accent-primary), var(--accent-soft));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .skill-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem;
      margin: 1rem 0;
    }
    .skill-chip {
      background: var(--badge-bg);
      padding: 0.5rem 1.2rem;
      border-radius: 40px;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: var(--badge-text);
      backdrop-filter: blur(4px);
      transition: all 0.25s;
      font-size: 0.9rem;
    }
    .skill-chip i, .skill-chip img {
      font-size: 1.1rem;
    }
    .skill-chip:hover {
      background: var(--accent-primary);
      color: white;
      transform: translateY(-3px);
      box-shadow: var(--shadow-glow);
    }

    /* two column layout */
    .split-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 2rem;
      margin: 2rem 0;
    }

    .info-card-content {
      padding: 1.8rem;
    }
    .fact-list {
      list-style: none;
      margin-top: 0.8rem;
    }
    .fact-list li {
      margin: 1rem 0;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .streak-wrapper {
      text-align: center;
      margin-top: 1rem;
    }
    hr {
      margin: 2rem 0;
      border: none;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--accent-soft), transparent);
    }
    .project-table {
      width: 100%;
      border-collapse: separate;
      border-spacing: 0 0.8rem;
    }
    .project-table td {
      background: var(--bg-glass);
      padding: 1rem;
      border-radius: 20px;
      backdrop-filter: blur(4px);
    }
    footer {
      text-align: center;
      padding: 2rem;
      border-top: 1px solid var(--footer-border);
      margin-top: 3rem;
      font-size: 0.85rem;
    }
    .quote-block {
      margin: 2rem 0;
      padding: 2rem;
      text-align: center;
      border-radius: 2rem;
      background: var(--bg-glass);
      backdrop-filter: blur(8px);
    }

    /* responsiveness */
    @media (max-width: 700px) {
      .container {
        padding: 1rem;
      }
      .typing-area {
        font-size: 1.3rem;
      }
    }
    /* floating icons */
    @keyframes floatAnim {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-8px); }
      100% { transform: translateY(0px); }
    }
    .float-icon {
      animation: floatAnim 3s ease-in-out infinite;
    }
    .stats-img {
      border-radius: 1rem;
      transition: all 0.2s;
    }
  </style>
</head>
<body>
<div class="container">
  <!-- navigation + themetoggle -->
  <div class="navbar animate__animated animate__fadeInDown">
    <div class="logo">
      <i class="fas fa-crown"></i> ROHITHA.D
    </div>
    <div class="theme-switch-wrapper">
      <i class="fas fa-sun" style="color: #f1c40f;"></i>
      <label class="theme-switch">
        <input type="checkbox" id="darkToggle">
        <span class="slider"></span>
      </label>
      <i class="fas fa-moon" style="color: #b794f4;"></i>
    </div>
  </div>

  <!-- Hero Section -->
  <div class="hero animate__animated animate__fadeInUp">
    <div class="avatar-icon"><i class="fas fa-code-branch"></i></div>
    <h1 style="font-size: 3rem; font-weight: 900; margin: 0.5rem 0;">👋 Hey, I'm Rohitha Dilshan</h1>
    <h3 style="font-weight: 600; color: var(--accent-primary);">🚀 Frontend Developer | UI/UX Enthusiast | Creative Tech Builder</h3>
    <div class="typing-area" id="typingAnimation"></div>
    <div class="badge-group">
      <a href="https://www.linkedin.com/in/rohitha-dilshan-dhananjaya-bandara-589051352/" target="_blank" class="social-badge"><i class="fab fa-linkedin"></i> LinkedIn</a>
      <a href="https://www.instagram.com/rohithadilshandhananjaya/" target="_blank" class="social-badge"><i class="fab fa-instagram"></i> Instagram</a>
      <a href="https://fb.com/rohitha.dilshan.dhananjaya" target="_blank" class="social-badge"><i class="fab fa-facebook"></i> Facebook</a>
      <a href="mailto:rddbandara53@gmail.com" class="social-badge"><i class="fas fa-envelope"></i> Email</a>
    </div>
    <div>
      <img src="https://komarev.com/ghpvc/?username=rohitha-dilshan&label=Profile+Views&color=8A2BE2&style=for-the-badge" alt="views" style="border-radius: 20px;">
    </div>
  </div>

  <!-- about + stats split -->
  <div class="split-grid">
    <div class="glass-card info-card-content animate__animated animate__fadeInLeft">
      <h2><i class="fas fa-user-astronaut" style="color: var(--accent-primary);"></i> 💫 About Me</h2>
      <ul class="fact-list">
        <li><i class="fas fa-gem" style="color: var(--accent-primary);"></i> 💎 Working on <strong>Modern Frontend Projects</strong></li>
        <li><i class="fas fa-seedling"></i> 🌱 Currently learning <strong>React, Node.js & MERN Stack</strong></li>
        <li><i class="fas fa-palette"></i> 🎨 Passionate about <strong>UI/UX Design</strong></li>
        <li><i class="fas fa-bolt"></i> ⚡ Love creating <strong>Creative Interfaces & Web Apps</strong></li>
        <li><i class="fas fa-at"></i> 📫 Reach me at <strong>rddbandara53@gmail.com</strong></li>
        <li><i class="fas fa-smile-wink"></i> ✨ Fun Fact: <strong>People call me Dila</strong></li>
      </ul>
      <img align="right" alt="Coding" width="120" src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" style="border-radius: 20px; margin-top: 0.5rem;" />
    </div>
    <div class="glass-card info-card-content animate__animated animate__fadeInRight">
      <h2><i class="fas fa-chart-line" style="color: var(--accent-primary);"></i> 📊 GitHub Stats</h2>
      <div class="streak-wrapper">
        <img class="stats-img" width="100%" src="https://github-readme-stats.vercel.app/api?username=rohitha-dilshan&show_icons=true&theme=tokyonight&hide_border=true&border_radius=15&bg_color=00000000" alt="stats"/>
      </div>
      <div class="streak-wrapper">
        <img class="stats-img" width="100%" src="https://github-readme-streak-stats.herokuapp.com/?user=rohitha-dilshan&theme=tokyonight&hide_border=true&border_radius=15" alt="streak"/>
      </div>
    </div>
  </div>

  <!-- Tech Stack (advanced icons) -->
  <h2 class="section-head"><i class="fas fa-code"></i> 🚀 Tech Stack</h2>
  <div class="skill-grid">
    <span class="skill-chip"><i class="fab fa-cuttlefish"></i> C++</span>
    <span class="skill-chip"><i class="fas fa-c"></i> C</span>
    <span class="skill-chip"><i class="fab fa-java"></i> Java</span>
    <span class="skill-chip"><i class="fab fa-js"></i> JavaScript</span>
    <span class="skill-chip"><i class="fab fa-php"></i> PHP</span>
    <span class="skill-chip"><i class="fab fa-html5"></i> HTML5</span>
    <span class="skill-chip"><i class="fab fa-css3-alt"></i> CSS3</span>
  </div>
  <h2 class="section-head"><i class="fas fa-paintbrush"></i> 🎨 Frontend</h2>
  <div class="skill-grid">
    <span class="skill-chip"><i class="fab fa-react"></i> React</span>
    <span class="skill-chip"><i class="fab fa-bootstrap"></i> Bootstrap</span>
    <span class="skill-chip"><i class="fab fa-tailwind"></i> TailwindCSS</span>
    <span class="skill-chip"><i class="fab fa-figma"></i> Figma</span>
  </div>
  <h2 class="section-head"><i class="fas fa-database"></i> ⚙️ Backend & DB</h2>
  <div class="skill-grid">
    <span class="skill-chip"><i class="fab fa-node-js"></i> NodeJS</span>
    <span class="skill-chip"><i class="fas fa-code"></i> Express.js</span>
    <span class="skill-chip"><i class="fas fa-database"></i> MongoDB</span>
    <span class="skill-chip"><i class="fas fa-database"></i> MySQL</span>
  </div>
  <h2 class="section-head"><i class="fas fa-tools"></i> 🛠 Tools & Platforms</h2>
  <div class="skill-grid">
    <span class="skill-chip"><i class="fab fa-git-alt"></i> Git</span>
    <span class="skill-chip"><i class="fab fa-github"></i> GitHub</span>
    <span class="skill-chip"><i class="fab fa-linux"></i> Linux</span>
    <span class="skill-chip"><i class="fab fa-windows"></i> Windows</span>
    <span class="skill-chip"><i class="fas fa-code"></i> VS Code</span>
  </div>

  <!-- Most used languages + Trophies -->
  <hr>
  <div class="split-grid">
    <div class="glass-card info-card-content" style="text-align: center;">
      <h3><i class="fas fa-chart-pie"></i> 📈 Most Used Languages</h3>
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=rohitha-dilshan&layout=compact&theme=tokyonight&hide_border=true&border_radius=15" width="100%" alt="top-langs">
    </div>
    <div class="glass-card info-card-content" style="text-align: center;">
      <h3><i class="fas fa-trophy"></i> 🏆 GitHub Trophies</h3>
      <img src="https://github-profile-trophy.vercel.app/?username=rohitha-dilshan&theme=tokyonight&no-frame=true&margin-w=15&margin-h=15" width="100%" alt="trophies">
    </div>
  </div>

  <!-- Contribution Graph -->
  <h2 class="section-head"><i class="fas fa-charging-station"></i> 🔥 Contribution Graph</h2>
  <div class="glass-card" style="padding: 1rem; margin-bottom: 1rem;">
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=rohitha-dilshan&theme=tokyo-night&hide_border=true&radius=20" width="100%" alt="activity-graph">
  </div>

  <!-- Featured Projects (elegant table) -->
  <h2 class="section-head"><i class="fas fa-rocket"></i> 🚀 Featured Projects</h2>
  <div class="glass-card" style="padding: 1rem;">
    <table class="project-table">
      <tr><td>🎯 QR Attendance System</td><td>Smart QR-based class attendance platform</td></tr>
      <tr><td>🛍 Clothing Store Website</td><td>Modern eCommerce frontend design</td></tr>
      <tr><td>🎨 UI/UX Wireframes</td><td>Figma-based creative interface designs</td></tr>
      <tr><td>🏢 Plant Management System</td><td>Operational workflow management system</td></tr>
      <tr><td>📚 School Library System</td><td>Digital library management platform</td></tr>
    </table>
  </div>

  <!-- Quote of the day with dynamic refresh -->
  <div class="quote-block glass-card" id="quoteBlock">
    <i class="fas fa-quote-left" style="font-size: 2rem; color: var(--accent-primary);"></i>
    <p id="quoteText" style="font-size: 1.3rem; margin: 0.8rem 0; font-weight: 500;">Loading wisdom...</p>
    <small><i class="fas fa-sync-alt"></i> Daily inspiration</small>
  </div>

  <!-- footer wave effect -->
  <footer>
    <p>© 2025 Rohitha Dilshan — Built with <i class="fas fa-heart" style="color: var(--accent-primary);"></i> + Advanced Light/Dark Magic ✨</p>
    <p><i class="fab fa-github"></i> github.com/rohitha-dilshan</p>
  </footer>
</div>

<script>
  // =============== DARK / LIGHT MODE toggling ===============
  const toggleBtn = document.getElementById('darkToggle');
  const currentSaved = localStorage.getItem('theme_pref');
  if (currentSaved === 'dark') {
    document.body.classList.add('dark');
    toggleBtn.checked = true;
  } else {
    document.body.classList.remove('dark');
    toggleBtn.checked = false;
  }
  toggleBtn.addEventListener('change', () => {
    if (toggleBtn.checked) {
      document.body.classList.add('dark');
      localStorage.setItem('theme_pref', 'dark');
    } else {
      document.body.classList.remove('dark');
      localStorage.setItem('theme_pref', 'light');
    }
  });

  // =============== Advanced Typing Animation ===============
  const roles = [
    "Frontend Developer 💻",
    "React & JavaScript Explorer ⚛️",
    "UI/UX Designer 🎨",
    "Building Creative Digital Experiences 🚀",
    "MERN Stack Learner 🌟"
  ];
  let idx = 0, charIdx = 0, isDeletingFlag = false;
  const typingEl = document.getElementById("typingAnimation");
  function typeLoop() {
    const fullText = roles[idx];
    if (isDeletingFlag) {
      typingEl.textContent = fullText.substring(0, charIdx - 1);
      charIdx--;
      if (charIdx === 0) {
        isDeletingFlag = false;
        idx = (idx + 1) % roles.length;
        setTimeout(typeLoop, 400);
      } else {
        setTimeout(typeLoop, 55);
      }
    } else {
      typingEl.textContent = fullText.substring(0, charIdx + 1);
      charIdx++;
      if (charIdx === fullText.length) {
        isDeletingFlag = true;
        setTimeout(typeLoop, 1800);
      } else {
        setTimeout(typeLoop, 85);
      }
    }
  }
  typeLoop();

  // =============== Dynamic Quote of the Day (GitHub style but fetch free API) ===============
  async function fetchQuote() {
    const quoteElement = document.getElementById('quoteText');
    try {
      const response = await fetch('https://api.quotable.io/random');
      const data = await response.json();
      quoteElement.innerHTML = `“${data.content}” — <strong>${data.author}</strong>`;
    } catch (error) {
      quoteElement.innerHTML = `“Code is like humor. When you have to explain it, it’s bad.” — Cory House`;
    }
  }
  fetchQuote();

  // =============== Intersection Observer for Scroll Reveal (subtle) ===============
  const fadeElements = document.querySelectorAll('.glass-card, .skill-chip, .section-head, .project-table tr');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0px)';
      }
    });
  }, { threshold: 0.05, rootMargin: "0px 0px -10px 0px" });
  fadeElements.forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(15px)';
    el.style.transition = 'opacity 0.4s ease, transform 0.3s ease';
    observer.observe(el);
  });
  // immediate reveal for visible items
  setTimeout(() => {
    fadeElements.forEach(el => {
      const rect = el.getBoundingClientRect();
      if (rect.top < window.innerHeight - 70) {
        el.style.opacity = '1';
        el.style.transform = 'translateY(0)';
      }
    });
  }, 100);
  
  // extra effect: tooltips for skill icons?
  // fix for external images (adjust if needed)
  const allImgs = document.querySelectorAll('img');
  allImgs.forEach(img => {
    if (img.src.includes('github-readme')) {
      img.setAttribute('loading', 'lazy');
    }
  });
</script>
</body>
</html>
