Here is an advanced, animated HTML/CSS interface that provides both light and dark themes, based on your GitHub profile content.
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Rohitha Dilshan | Advanced Dev Portfolio</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Animate.css (subtle) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      transition: background-color 0.3s ease, color 0.2s ease, border-color 0.2s ease, box-shadow 0.2s ease;
    }

    body {
      font-family: 'Inter', sans-serif;
      scroll-behavior: smooth;
      background: var(--bg-gradient);
      color: var(--text-primary);
      line-height: 1.5;
      overflow-x: hidden;
    }

    /* ========== LIGHT & DARK THEME VARIABLES ========== */
    :root {
      /* Light Mode (default) */
      --bg-gradient: linear-gradient(135deg, #f8faff 0%, #fff4f0 100%);
      --card-bg: rgba(255, 255, 255, 0.85);
      --card-border: rgba(0, 0, 0, 0.05);
      --text-primary: #1e1b2c;
      --text-secondary: #4a4a6a;
      --accent: #851c73;
      --accent-glow: rgba(133, 28, 115, 0.2);
      --badge-bg: #f0f0fa;
      --badge-text: #2d2f3e;
      --shadow-sm: 0 10px 30px -10px rgba(0, 0, 0, 0.1);
      --shadow-md: 0 20px 35px -12px rgba(0, 0, 0, 0.15);
      --toggle-bg: #e2e8f0;
      --toggle-circle: #ffffff;
      --code-bg: #f1f5f9;
      --footer-border: rgba(0,0,0,0.05);
    }

    body.dark {
      /* Dark Mode */
      --bg-gradient: linear-gradient(145deg, #0b0c15 0%, #1a142d 100%);
      --card-bg: rgba(18, 18, 30, 0.75);
      --card-border: rgba(255, 255, 255, 0.08);
      --text-primary: #f0eefc;
      --text-secondary: #b9b9e0;
      --accent: #d26bc2;
      --accent-glow: rgba(210, 107, 194, 0.25);
      --badge-bg: #25253f;
      --badge-text: #e0ddfc;
      --shadow-sm: 0 10px 30px -8px rgba(0, 0, 0, 0.5);
      --shadow-md: 0 20px 40px -12px rgba(0, 0, 0, 0.6);
      --toggle-bg: #3b2b4a;
      --toggle-circle: #ffdd99;
      --code-bg: #13112b;
      --footer-border: rgba(255,255,255,0.08);
    }

    /* GLASS MORPHISM + BLUR */
    .glass-card {
      background: var(--card-bg);
      backdrop-filter: blur(12px);
      border: 1px solid var(--card-border);
      border-radius: 2rem;
      box-shadow: var(--shadow-sm);
      transition: transform 0.25s ease, box-shadow 0.3s ease;
    }

    .glass-card:hover {
      transform: translateY(-4px);
      box-shadow: var(--shadow-md);
    }

    /* container */
    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 1.5rem 2rem;
    }

    /* header / navbar */
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
      padding: 1rem 0;
    }

    .logo-area {
      font-weight: 800;
      font-size: 1.8rem;
      background: linear-gradient(135deg, var(--accent), #b44a9e);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.5px;
    }

    /* Theme Toggle switch (modern) */
    .theme-switch-wrapper {
      display: flex;
      align-items: center;
      gap: 0.6rem;
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
      height: 26px;
      width: 26px;
      left: 3px;
      bottom: 3px;
      background-color: var(--toggle-circle);
      transition: 0.4s;
      border-radius: 50%;
      box-shadow: 0 1px 3px rgba(0,0,0,0.2);
    }

    input:checked + .slider:before {
      transform: translateX(32px);
    }

    .theme-icon {
      font-size: 1.2rem;
    }

    /* profile header animation */
    .hero {
      text-align: center;
      margin: 2rem 0 3rem;
    }

    .typing-wrapper {
      margin: 1rem 0;
    }

    .badge-group {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .social-btn {
      background: var(--badge-bg);
      padding: 0.6rem 1.2rem;
      border-radius: 40px;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: var(--text-secondary);
      text-decoration: none;
      font-weight: 500;
      transition: all 0.2s;
    }

    .social-btn:hover {
      transform: scale(1.05);
      background: var(--accent);
      color: white;
      box-shadow: 0 5px 12px var(--accent-glow);
    }

    /* section titles */
    .section-title {
      font-size: 2rem;
      font-weight: 700;
      margin: 2rem 0 1.5rem;
      position: relative;
      display: inline-block;
    }
    .section-title:after {
      content: '';
      position: absolute;
      bottom: -8px;
      left: 0;
      width: 60%;
      height: 3px;
      background: var(--accent);
      border-radius: 4px;
    }

    /* tech grid */
    .tech-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem 1.2rem;
      margin-top: 1rem;
    }
    .tech-item {
      background: var(--badge-bg);
      padding: 0.5rem 1rem;
      border-radius: 2rem;
      font-size: 0.9rem;
      font-weight: 500;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: var(--badge-text);
      backdrop-filter: blur(4px);
      transition: all 0.2s;
    }
    .tech-item i, .tech-item svg {
      font-size: 1.1rem;
    }
    .tech-item:hover {
      background: var(--accent);
      color: white;
      transform: translateY(-2px);
    }

    /* row layout */
    .two-columns {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 2rem;
      margin: 2rem 0;
    }

    .info-card {
      padding: 1.5rem;
    }

    .contact-line {
      display: flex;
      align-items: center;
      gap: 12px;
      margin: 1rem 0;
      flex-wrap: wrap;
    }

    hr {
      margin: 2rem 0;
      border: none;
      height: 1px;
      background: var(--card-border);
    }

    .streak-container {
      display: flex;
      justify-content: center;
      margin: 2rem 0;
    }

    footer {
      text-align: center;
      padding: 2rem 0;
      border-top: 1px solid var(--footer-border);
      margin-top: 3rem;
      font-size: 0.85rem;
    }

    /* animated underline and floating */
    @keyframes float {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-6px); }
      100% { transform: translateY(0px); }
    }
    .float-icon {
      animation: float 3s ease-in-out infinite;
    }

    /* responsive */
    @media (max-width: 700px) {
      .container {
        padding: 1rem;
      }
      .section-title {
        font-size: 1.7rem;
      }
    }
    /* custom glow text */
    .glow-text {
      text-shadow: 0 0 4px var(--accent-glow);
    }
  </style>
</head>
<body>
  <div class="container">
    <!-- NAVBAR with theme toggle -->
    <div class="navbar animate__animated animate__fadeInDown">
      <div class="logo-area">
        <i class="fas fa-code"></i> ROHITHA.dev
      </div>
      <div class="theme-switch-wrapper">
        <i class="fas fa-sun theme-icon" style="color: #f39c12;"></i>
        <label class="theme-switch">
          <input type="checkbox" id="darkmode-toggle">
          <span class="slider"></span>
        </label>
        <i class="fas fa-moon theme-icon" style="color: #9b59b6;"></i>
      </div>
    </div>

    <!-- HERO SECTION with Typing SVG style (but animated) -->
    <div class="hero animate__animated animate__fadeInUp">
      <h1 style="font-size: 2.8rem; font-weight: 800; background: linear-gradient(135deg, var(--accent), #b96aae); -webkit-background-clip: text; background-clip: text; color: transparent;">
        Hi 👋, I'm Rohitha Dilshan
      </h1>
      <div class="typing-wrapper" style="margin-top: 0.5rem;">
        <span id="dynamic-role" style="font-size: 1.6rem; font-weight: 500; color: var(--accent); border-right: 2px solid var(--accent); padding-right: 5px;"></span>
      </div>
      <p style="font-size: 1.2rem; max-width: 700px; margin: 1rem auto; color: var(--text-secondary);">
        A passionate frontend developer from Sri Lanka <i class="fas fa-map-marker-alt" style="color: var(--accent);"></i>
      </p>
      
      <!-- badges group -->
      <div class="badge-group">
        <a href="https://www.linkedin.com/in/rohitha-dilshan-dhananjaya-bandara-589051352/" target="_blank" class="social-btn"><i class="fab fa-linkedin"></i> LinkedIn</a>
        <a href="https://www.instagram.com/rohithadilshandhananjaya/" target="_blank" class="social-btn"><i class="fab fa-instagram"></i> Instagram</a>
        <a href="https://fb.com/rohitha.dilshan.dhananjaya" target="_blank" class="social-btn"><i class="fab fa-facebook"></i> Facebook</a>
        <a href="mailto:rddbandara53@gmail.com" class="social-btn"><i class="fas fa-envelope"></i> Email</a>
      </div>
    </div>

    <!-- ABOUT + STATS two column -->
    <div class="two-columns">
      <!-- left: about / facts -->
      <div class="glass-card info-card animate__animated animate__fadeInLeft">
        <h3 style="font-size: 1.8rem; margin-bottom: 1rem;"><i class="fas fa-user-astronaut"></i> About Me</h3>
        <ul style="list-style: none;">
          <li style="margin-bottom: 0.8rem;">💎 <strong>Working on:</strong> Frontend Projects & React apps</li>
          <li style="margin-bottom: 0.8rem;">📝 <strong>Exploring:</strong> React & JavaScript ecosystem</li>
          <li style="margin-bottom: 0.8rem;">📞 <strong>Contact:</strong> rddbandara53@gmail.com</li>
          <li style="margin-bottom: 0.8rem;">✨ <strong>Fun fact:</strong> Call me as <span style="background: var(--accent-glow); padding: 0.1rem 0.4rem; border-radius: 20px;">Dila</span> 🎉</li>
        </ul>
        <div class="contact-line">
          <i class="fas fa-robot"></i> <span>Always building creative UI experiences</span>
        </div>
      </div>

      <!-- right: GitHub streak stats (modern embed) -->
      <div class="glass-card info-card animate__animated animate__fadeInRight" style="text-align: center;">
        <h3 style="margin-bottom: 1rem;"><i class="fas fa-fire"></i> Dev Streak</h3>
        <div class="streak-container">
          <a href="https://git.io/streak-stats" target="_blank">
            <img src="https://github-readme-streak-stats.herokuapp.com?user=rohitha-dilshan&theme=midnight-purple&date_format=j%20M%5B%20Y%5D&card_width=450&card_height=180&fire=EB6D00" alt="GitHub Streak" style="border-radius: 24px; max-width: 100%;">
          </a>
        </div>
        <p style="margin-top: 0.5rem;"><i class="fas fa-chart-line"></i> Consistent coding journey</p>
      </div>
    </div>

    <!-- LANGUAGES & TOOLS SECTION -->
    <h3 class="section-title"><i class="fas fa-code"></i> Languages & Core</h3>
    <div class="tech-grid">
      <span class="tech-item"><i class="fab fa-cuttlefish"></i> C++</span>
      <span class="tech-item"><i class="fas fa-c"></i> C</span>
      <span class="tech-item"><i class="fab fa-html5"></i> HTML5</span>
      <span class="tech-item"><i class="fab fa-css3-alt"></i> CSS3</span>
      <span class="tech-item"><i class="fab fa-js"></i> JavaScript</span>
      <span class="tech-item"><i class="fab fa-java"></i> Java</span>
      <span class="tech-item"><i class="fab fa-php"></i> PHP</span>
    </div>

    <h3 class="section-title"><i class="fas fa-laptop-code"></i> Frontend Development</h3>
    <div class="tech-grid">
      <span class="tech-item"><i class="fab fa-react"></i> React</span>
      <span class="tech-item"><i class="fab fa-bootstrap"></i> Bootstrap</span>
      <span class="tech-item"><i class="fab fa-tailwind"></i> TailwindCSS</span>
    </div>

    <h3 class="section-title"><i class="fas fa-server"></i> Backend & DB</h3>
    <div class="tech-grid">
      <span class="tech-item"><i class="fas fa-database"></i> MySQL</span>
      <span class="tech-item"><i class="fas fa-leaf"></i> MongoDB</span>
      <span class="tech-item"><i class="fas fa-code"></i> Express.js</span>
    </div>

    <h3 class="section-title"><i class="fas fa-tools"></i> Version Control & Tools</h3>
    <div class="tech-grid">
      <span class="tech-item"><i class="fab fa-git-alt"></i> Git</span>
      <span class="tech-item"><i class="fab fa-github"></i> GitHub</span>
      <span class="tech-item"><i class="fab fa-figma"></i> Figma</span>
      <span class="tech-item"><i class="fab fa-linux"></i> Linux</span>
      <span class="tech-item"><i class="fab fa-windows"></i> Windows</span>
    </div>

    <h3 class="section-title"><i class="fas fa-graduation-cap"></i> Currently Learning & Future Plans</h3>
    <div class="tech-grid">
      <span class="tech-item"><i class="fab fa-react"></i> React Advanced</span>
      <span class="tech-item"><i class="fab fa-node-js"></i> NodeJS</span>
      <span class="tech-item"><i class="fab fa-docker"></i> Docker (future)</span>
      <span class="tech-item"><i class="fas fa-fire"></i> Firebase (future)</span>
      <span class="tech-item"><i class="fas fa-chart-line"></i> GraphQL (future)</span>
    </div>

    <!-- PROJECTS / MOTTO animated card -->
    <hr>
    <div class="glass-card" style="padding: 2rem; text-align: center; margin: 2rem 0;">
      <i class="fas fa-quote-left" style="font-size: 2rem; color: var(--accent); opacity: 0.6;"></i>
      <p style="font-size: 1.4rem; font-weight: 500; margin: 1rem 0;">"Code with passion, design with purpose"</p>
      <div class="tech-item" style="display: inline-flex; background: var(--accent); color: white;">
        <i class="fas fa-gem"></i> Available for collaboration
      </div>
    </div>

    <!-- SKILLS in advanced grid (animated on scroll) -->
    <div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 1rem; margin-top: 1rem;">
      <div class="glass-card" style="flex:1; min-width: 200px; padding: 1rem;">
        <i class="fas fa-layer-group float-icon" style="font-size: 2rem; color: var(--accent);"></i>
        <h4>UI/UX Passion</h4>
        <p style="font-size: 0.9rem;">Crafting responsive & interactive experiences.</p>
      </div>
      <div class="glass-card" style="flex:1; min-width: 200px; padding: 1rem;">
        <i class="fas fa-rocket float-icon" style="font-size: 2rem; color: var(--accent);"></i>
        <h4>Performance</h4>
        <p style="font-size: 0.9rem;">Clean code, modern stacks, blazing fast apps.</p>
      </div>
      <div class="glass-card" style="flex:1; min-width: 200px; padding: 1rem;">
        <i class="fas fa-brain float-icon" style="font-size: 2rem; color: var(--accent);"></i>
        <h4>Problem Solver</h4>
        <p style="font-size: 0.9rem;">Creative solutions for real-world challenges.</p>
      </div>
    </div>

    <footer>
      <p>© 2025 Rohitha Dilshan — built with <i class="fas fa-heart" style="color: var(--accent);"></i> & advanced interface | Light/Dark magic ✨</p>
      <p style="margin-top: 8px;"><i class="fab fa-github"></i> github.com/rohitha-dilshan</p>
    </footer>
  </div>

  <script>
    // ------------------------- THEME TOGGLE (DARK / LIGHT) -------------------------
    const toggleCheckbox = document.getElementById('darkmode-toggle');
    // Check local storage for theme preference
    const currentTheme = localStorage.getItem('theme');
    if (currentTheme === 'dark') {
      document.body.classList.add('dark');
      toggleCheckbox.checked = true;
    } else {
      document.body.classList.remove('dark');
      toggleCheckbox.checked = false;
    }

    toggleCheckbox.addEventListener('change', function(e) {
      if (this.checked) {
        document.body.classList.add('dark');
        localStorage.setItem('theme', 'dark');
      } else {
        document.body.classList.remove('dark');
        localStorage.setItem('theme', 'light');
      }
    });

    // ------------------------- ADVANCED TYPING ANIMATION (multiple roles) -------------------------
    const roles = [
      "Frontend Developer 💻",
      "React Enthusiast ⚛️",
      "UI/UX Craftsman 🎨",
      "Open Source Learner 🚀",
      "Problem Solver 🧠"
    ];
    let roleIndex = 0;
    let charIndex = 0;
    let isDeleting = false;
    const dynamicElement = document.getElementById("dynamic-role");
    
    function typeEffect() {
      const currentRole = roles[roleIndex];
      if (isDeleting) {
        // Deleting text
        dynamicElement.textContent = currentRole.substring(0, charIndex - 1);
        charIndex--;
        if (charIndex === 0) {
          isDeleting = false;
          roleIndex = (roleIndex + 1) % roles.length;
          setTimeout(typeEffect, 300);
          return;
        }
        setTimeout(typeEffect, 60);
      } else {
        // Typing text
        dynamicElement.textContent = currentRole.substring(0, charIndex + 1);
        charIndex++;
        if (charIndex === currentRole.length) {
          isDeleting = true;
          setTimeout(typeEffect, 1800);
          return;
        }
        setTimeout(typeEffect, 100);
      }
    }
    // start the typing animation after page loads
    window.addEventListener('load', () => {
      typeEffect();
    });

    // ---------- Intersection Observer for subtle scroll animations (additional) ----------
    const animatedElements = document.querySelectorAll('.glass-card, .tech-item, .section-title');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.style.opacity = '1';
          entry.target.style.transform = 'translateY(0)';
        } else {
          // optional: reset? but keep smoothness
        }
      });
    }, { threshold: 0.05, rootMargin: "0px 0px -20px 0px" });
    
    animatedElements.forEach(el => {
      el.style.opacity = '0';
      el.style.transform = 'translateY(12px)';
      el.style.transition = 'opacity 0.5s ease, transform 0.4s ease';
      observer.observe(el);
    });
    
    // Force immediate rendering for already visible items on load
    setTimeout(() => {
      animatedElements.forEach(el => {
        const rect = el.getBoundingClientRect();
        if (rect.top < window.innerHeight - 80) {
          el.style.opacity = '1';
          el.style.transform = 'translateY(0)';
        }
      });
    }, 100);
    
    // manual background smoothness for external image (streak SVG might glitch with dark mode, but it's externally light)
    // To improve the embed, we let it stay independent. additional dark mode adaptation for img border
    const streakImg = document.querySelector('.streak-container img');
    if (streakImg) {
      streakImg.style.transition = 'all 0.2s';
      streakImg.style.borderRadius = '20px';
      streakImg.style.boxShadow = 'var(--shadow-sm)';
    }

    // Refresh for some social links icons: ensure all external links have rel
    document.querySelectorAll('.social-btn').forEach(link => {
      link.setAttribute('target', '_blank');
      link.setAttribute('rel', 'noopener noreferrer');
    });
    
    // live date/time footer greeting (optional)
    const footerP = document.querySelector('footer p:first-child');
    if (footerP) {
      const hour = new Date().getHours();
      let greeting = "";
      if (hour < 12) greeting = "Good morning 🌤️";
      else if (hour < 18) greeting = "Good afternoon ☀️";
      else greeting = "Good evening 🌙";
      footerP.innerHTML = `© 2025 Rohitha Dilshan — ${greeting} &nbsp;| built with <i class="fas fa-heart" style="color: var(--accent);"></i> & advanced interface | Light/Dark magic ✨`;
    }
  </script>
</body>
</html>
```
