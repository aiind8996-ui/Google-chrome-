FIR
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>AI Web Browser</title>
<style>
  :root {
    --bg:#0f1724; --glass:rgba(255,255,255,0.05);
    --accent:#3b82f6; --text:#e6eef8; --muted:#a0aec0;
  }
  html,body {
    height:100%;margin:0;
    background:var(--bg);color:var(--text);
    font-family:"Segoe UI",Roboto,sans-serif;
  }
  .browser {display:flex;flex-direction:column;height:100vh;padding:10px;}
  .title-bar {
    width:100%;text-align:center;font-weight:700;
    font-size:18px;background:var(--glass);
    padding:10px;border-radius:8px;margin-bottom:8px;
  }
  /* बाकी सब चीजें छिपा दी गई हैं */
  .top, .tabs, .bottom {display:none !important;}
  .iframe-wrap {
    flex:1;border-radius:10px;overflow:hidden;
    border:1px solid rgba(255,255,255,0.05);
  }
  iframe {width:100%;height:100%;border:0;}
</style>
</head>
<body>
<div class="browser">
  <div class="title-bar">🌐 AI Web Browser</div>
  <div class="iframe-wrap">
    <!-- केवल Google दिखेगा -->
    <iframe src="https://www.google.com/webhp?igu=1"
            sandbox="allow-same-origin allow-forms allow-scripts allow-popups">
    </iframe>
  </div>
</div>
</body>
</html>
