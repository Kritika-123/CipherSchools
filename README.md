<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>CipherStudio — Browser React IDE</title>
  <style>
    :root{
      --bg:#0f1724; --card:#0b1220; --muted:#98a0b3; --accent:#7c3aed; --glass: rgba(255,255,255,0.03);
      --light-bg: #f7f9fc; --light-card:#ffffff; --light-text:#0b1220; --light-muted:#51607a;
    }
    html,body{height:100%;margin:0;font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,'Helvetica Neue',Arial}
    body{background:linear-gradient(180deg,#071029 0%, #081226 60%);color:#e6eef8;line-height:1.5}
    .container{max-width:1100px;margin:32px auto;padding:24px}

    header{display:flex;align-items:center;gap:16px}
    .logo{width:56px;height:56px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#4f46e5);display:flex;align-items:center;justify-content:center;font-weight:700;font-size:20px;box-shadow:0 6px 18px rgba(31,41,55,0.45)}
    h1{margin:0;font-size:22px}
    p.lead{margin:6px 0 0;color:var(--muted);font-size:14px}

    .hero{display:grid;grid-template-columns:1fr 320px;gap:20px;margin-top:18px}
    .card{background:var(--card);border-radius:12px;padding:18px;box-shadow:0 6px 30px rgba(4,6,15,0.6)}
    .meta{display:flex;justify-content:space-between;align-items:center}
    .meta .links a{color:var(--accent);text-decoration:none;margin-left:10px;font-weight:600}

    .features{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-top:14px}
    .feature{background:var(--glass);padding:12px;border-radius:10px}
    .feature h4{margin:0 0 6px;font-size:15px}
    .feature p{margin:0;color:var(--muted);font-size:13px}

    .sidebar{display:flex;flex-direction:column;gap:12px}
    .btn{display:inline-block;padding:10px 12px;border-radius:8px;background:linear-gradient(90deg,var(--accent),#4f46e5);color:white;text-decoration:none;font-weight:600}
    .muted{color:var(--muted);font-size:13px}

    pre{background:#071224;padding:12px;border-radius:8px;overflow:auto;font-family:ui-monospace,SFMono-Regular,Menlo,monospace;font-size:13px;color:#dbeafe}
    code.inline{background:rgba(255,255,255,0.03);padding:4px 6px;border-radius:6px}

    footer{margin-top:22px;color:var(--muted);font-size:13px}

    /* Responsive */
    @media (max-width:880px){
      .hero{grid-template-columns:1fr}
      .features{grid-template-columns:1fr}
    }

    /* Light mode */
    .light{background:linear-gradient(180deg,var(--light-bg),#eaf0fb);color:var(--light-text)}
    .light .card{background:var(--light-card);box-shadow:0 6px 18px rgba(13,20,40,0.06)}
    .light .feature{background:#f3f6fb}
    .light .muted{color:var(--light-muted)}
    .light pre{background:#f3f6fb;color:#0b1220}
  </style>
</head>
<body>
  <div class="container" id="app">
    <header>
      <div class="logo">CS</div>
      <div>
        <h1>CipherStudio — Browser-Based React IDE</h1>
        <p class="lead">Create, edit, and preview React projects right in the browser. Zero local setup.</p>
      </div>
      <div style="margin-left:auto;display:flex;gap:10px;align-items:center">
        <button id="themeToggle" class="btn" style="background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--accent)">Toggle Theme</button>
        <a href="#" class="btn">Live Demo</a>
      </div>
    </header>

    <section class="hero">
      <div class="card">
        <div class="meta">
          <div>
            <strong>Overview</strong>
            <div class="muted">Next.js + Monaco + Sandpack · Express + MongoDB</div>
          </div>
          <div class="links">
            <a href="#">Docs</a>
            <a href="#">Quick Start</a>
          </div>
        </div>

        <div class="features" style="margin-top:16px">
          <div class="feature">
            <h4>File Management</h4>
            <p>Create, delete and organise files & folders.</p>
          </div>
          <div class="feature">
            <h4>Live Preview</h4>
            <p>Instant Sandpack preview of your React app while you type.</p>
          </div>
          <div class="feature">
            <h4>Monaco Editor</h4>
            <p>Powerful code editing with syntax highlighting and autocompletion.</p>
          </div>
          <div class="feature">
            <h4>Save & Load</h4>
            <p>Persist projects to MongoDB or fallback to localStorage.</p>
          </div>
        </div>

        <h3 style="margin-top:18px">Quick Start</h3>
        <p class="muted">Run backend and frontend locally. Frontend uses port <code class="inline">3000</code>, backend <code class="inline">5000</code>.</p>

        <pre><code>// Clone & install
 git clone &lt;repo&gt;
 cd CipherStudio
 cd backend && npm install
 cd ../frontend && npm install

 // start
 cd backend && npm run dev
 cd frontend && npm run dev
</code></pre>

        <h3 style="margin-top:12px">API Endpoints</h3>
        <pre><code>POST   /api/projects   # create
GET    /api/projects   # list
GET    /api/projects/:id
PUT    /api/projects/:id
DELETE /api/projects/:id
</code></pre>
      </div>

      <aside class="sidebar">
        <div class="card">
          <strong>Project Stats</strong>
          <div class="muted" style="margin-top:8px">Frontend: ~2000 LOC · Backend: ~500 LOC</div>

          <div style="margin-top:12px">
            <a class="btn" href="#">Export Project</a>
          </div>
        </div>

        <div class="card">
          <strong>Roadmap</strong>
          <ul class="muted" style="padding-left:16px;margin:8px 0 0">
            <li>User authentication</li>
            <li>Real-time collaboration</li>
            <li>Version control integration</li>
          </ul>
        </div>

        <div class="card">
          <strong>Tech Stack</strong>
          <div class="muted" style="margin-top:8px">Next.js · React · Monaco · Sandpack · Express · MongoDB · Zustand</div>
        </div>
      </aside>
    </section>

    <section style="margin-top:18px;display:grid;grid-template-columns:1fr 1fr;gap:12px">
      <div class="card">
        <h3>Project Structure</h3>
        <pre><code>CipherStudio/
├─ frontend/ (Next.js)
├─ backend/  (Express + MongoDB)
└─ README.md
</code></pre>
      </div>

      <div class="card">
        <h3>Contribute</h3>
        <p class="muted">Fork the repository, create a feature branch, and open a pull request. See CONTRIBUTING.md for rules.</p>
        <div style="margin-top:10px"><a class="btn" href="#">Create Issue</a></div>
      </div>
    </section>

    <footer>
      <div class="muted">MIT · Built with ❤️ by the CipherStudio team</div>
    </footer>
  </div>

  <script>
    const root = document.documentElement;
    const app = document.getElementById('app');
    const themeBtn = document.getElementById('themeToggle');
    let light = false;
    themeBtn.addEventListener('click',()=>{
      light = !light;
      document.body.classList.toggle('light', light);
    });
  </script>
</body>
</html>
