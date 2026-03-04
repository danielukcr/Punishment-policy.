<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Punishment Policy</title>
  <style>
    :root{
      --bg:#0b0f14;
      --card:#121824;
      --text:#e8eef7;
      --muted:#b8c3d6;
      --accent:#6aa9ff;
      --border:rgba(255,255,255,.10);
      --shadow:0 10px 30px rgba(0,0,0,.35);
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, "Noto Sans", "Liberation Sans", sans-serif;
      background: radial-gradient(1200px 600px at 20% 0%, rgba(106,169,255,.18), transparent 55%),
                  radial-gradient(900px 500px at 90% 10%, rgba(140,92,246,.14), transparent 55%),
                  var(--bg);
      color:var(--text);
      line-height:1.55;
      padding:24px;
    }
    .wrap{max-width:900px;margin:0 auto;}
    header{
      margin: 6px 0 18px;
      display:flex;
      gap:12px;
      align-items:flex-start;
      justify-content:space-between;
      flex-wrap:wrap;
    }
    h1{
      margin:0;
      font-size:clamp(1.5rem, 3vw, 2.1rem);
      letter-spacing:.2px;
    }
    .meta{
      color:var(--muted);
      font-size:.95rem;
      margin-top:4px;
    }
    .card{
      background: linear-gradient(180deg, rgba(255,255,255,.03), transparent 45%),
                  var(--card);
      border:1px solid var(--border);
      border-radius:16px;
      box-shadow:var(--shadow);
      overflow:hidden;
    }
    .card-inner{padding:18px 18px 10px;}
    .rule{
      border-left:4px solid var(--accent);
      padding:12px 14px;
      margin:14px 0;
      background: rgba(106,169,255,.08);
      border-radius:12px;
    }
    .rule h2{
      margin:0 0 8px;
      font-size:1.05rem;
    }
    .rule p{margin:0;color:var(--text)}
    .notice{
      margin-top:16px;
      padding:12px 14px;
      border:1px dashed rgba(255,255,255,.18);
      border-radius:12px;
      color:var(--muted);
      background: rgba(255,255,255,.02);
      font-style:italic;
    }
    .actions{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      padding:0 18px 18px;
      border-top:1px solid var(--border);
      margin-top:10px;
    }
    button{
      appearance:none;
      border:1px solid var(--border);
      background: rgba(255,255,255,.04);
      color:var(--text);
      padding:10px 12px;
      border-radius:12px;
      cursor:pointer;
      font-weight:600;
      transition:transform .06s ease, background .2s ease, border-color .2s ease;
    }
    button:hover{
      background: rgba(255,255,255,.07);
      border-color: rgba(255,255,255,.18);
    }
    button:active{transform:translateY(1px)}
    .small{
      font-size:.9rem;
      color:var(--muted);
      margin:10px 0 0;
    }
    footer{
      margin-top:14px;
      color:var(--muted);
      font-size:.9rem;
      text-align:center;
    }
    @media (prefers-color-scheme: light){
      :root{
        --bg:#f6f8fc;
        --card:#ffffff;
        --text:#101828;
        --muted:#475467;
        --border:rgba(16,24,40,.12);
        --shadow:0 10px 30px rgba(16,24,40,.10);
      }
      body{
        background: radial-gradient(1200px 600px at 20% 0%, rgba(106,169,255,.20), transparent 55%),
                    radial-gradient(900px 500px at 90% 10%, rgba(140,92,246,.12), transparent 55%),
                    var(--bg);
      }
      .rule{background: rgba(106,169,255,.10);}
    }
  </style>
</head>
<body>
  <main class="wrap">
    <header>
      <div>
        <h1>Punishment Policy</h1>
        <div class="meta" id="effectiveText">Effective immediately</div>
      </div>
      <div class="meta" aria-label="Policy timing note">
        All time references use local server/client time.
      </div>
    </header>

    <section class="card" aria-labelledby="policyTitle">
      <div class="card-inner">
        <div class="rule" role="note" aria-label="Rule 1">
          <h2>1) Time limit on sanctions</h2>
          <p>
            If more than <strong>4 hours</strong> have passed since an incident occurred,
            action can only be taken if there is an <strong>official investigation</strong>
            supported by <strong>sufficient evidence</strong>.
          </p>
        </div>

        <div class="rule" role="note" aria-label="Rule 2">
          <h2>2) Evidence sharing requirement</h2>
          <p>
            If a member or staff is placed under investigation, evidence must be shared with them
            within <strong>30 minutes</strong>. Failure to provide evidence within that time will
            <strong>void the investigation</strong> due to insufficient proof.
          </p>
        </div>

        <p class="notice">
          This policy is in place to support the well-being of both the community and its staff.
        </p>

        <p class="small" id="lastUpdated"></p>
      </div>

      <div class="actions" aria-label="Page actions">
        <button type="button" id="copyBtn">Copy policy text</button>
        <button type="button" id="printBtn">Print</button>
      </div>
    </section>

    <footer>
      <span id="footerStamp"></span>
    </footer>
  </main>

  <script>
    (function () {
      // Optional: set a "Last updated" stamp. Change the date string if you want it fixed.
      const now = new Date();
      const fmt = new Intl.DateTimeFormat(undefined, { year: "numeric", month: "long", day: "2-digit" });
      const updatedLine = document.getElementById("lastUpdated");
      updatedLine.textContent = "Last updated: " + fmt.format(now);

      const footerStamp = document.getElementById("footerStamp");
      footerStamp.textContent = "© " + now.getFullYear() + " — Policy Document";

      const policyText =
`Punishment Policy

1) Time limit on sanctions
If more than 4 hours have passed since an incident occurred, action can only be taken if there is an official investigation supported by sufficient evidence.

2) Evidence sharing requirement
If a member or staff is placed under investigation, evidence must be shared with them within 30 minutes. Failure to provide evidence within that time will void the investigation due to insufficient proof.

This policy is in place to support the well-being of both the community and its staff.`;

      document.getElementById("copyBtn").addEventListener("click", async () => {
        try {
          await navigator.clipboard.writeText(policyText);
          const btn = document.getElementById("copyBtn");
          const old = btn.textContent;
          btn.textContent = "Copied!";
          setTimeout(() => (btn.textContent = old), 1200);
        } catch (e) {
          alert("Copy failed. You can manually select and copy the policy text.");
        }
      });

      document.getElementById("printBtn").addEventListener("click", () => window.print());
    })();
  </script>
</body>
</html>
