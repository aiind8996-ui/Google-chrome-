GOOGLE 
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
<title>🌐 JACK WEBSITE</title>
<style>
  :root {
    --bg:#0f1724;
    --glass:rgba(255,255,255,0.05);
    --accent:#3b82f6;
    --text:#e6eef8;
    --muted:#a0aec0;
  }
  html,body{
    height:100%;
    width:100%;
    margin:0;
    padding:0;
    background:var(--bg);
    color:var(--text);
    font-family:"Segoe UI",Roboto,sans-serif;
    overflow:hidden;
  }
  .browser{
    display:flex;
    flex-direction:column;
    height:100vh;
    width:100vw;
    margin:0;
    padding:0;
  }
  .title-bar{
    text-align:center;
    font-weight:700;
    font-size:20px;
    background:var(--glass);
    color:var(--text);
    padding:12px 0;
    position:relative;
  }
  .btns{
    position:absolute;
    right:10px;
    top:6px;
    display:flex;
    gap:8px;
  }
  .icon-btn{
    background:transparent;
    border:none;
    color:var(--accent);
    font-size:22px;
    cursor:pointer;
  }
  .search-bar{
    display:flex;
    gap:6px;
    padding:8px;
  }
  input{
    flex:1;
    padding:10px 12px;
    border-radius:6px;
    border:none;
    outline:none;
    font-size:16px;
    background:rgba(255,255,255,0.1);
    color:var(--text);
  }
  input::placeholder{
    color:var(--muted);
  }
  button{
    background:var(--accent);
    color:white;
    border:none;
    border-radius:6px;
    padding:10px 16px;
    font-weight:600;
    cursor:pointer;
    transition:0.2s;
  }
  button:hover{
    opacity:0.9;
  }
  .iframe-wrap{
    flex:1;
    border:none;
    overflow:hidden;
  }
  iframe{
    width:100%;
    height:100%;
    border:0;
    display:block;
  }

  /* Settings panel styling */
  .settings-panel{
    position:fixed;
    top:0;left:0;
    width:100%;height:100%;
    background:rgba(0,0,0,0.6);
    display:none;
    align-items:center;
    justify-content:center;
    z-index:10;
  }
  .settings-box{
    background:var(--bg);
    border:1px solid var(--glass);
    border-radius:12px;
    padding:20px;
    width:85%;
    max-width:400px;
    box-shadow:0 0 20px rgba(0,0,0,0.4);
    text-align:left;
  }
  .settings-box h2{
    text-align:center;
    color:var(--accent);
    margin-top:0;
  }
  .settings-box label{
    display:block;
    margin-top:10px;
    font-weight:500;
    color:var(--text);
  }
  select,input[type="checkbox"]{
    margin-top:5px;
    width:100%;
    padding:8px;
    border-radius:6px;
    border:none;
    font-size:15px;
    background:rgba(255,255,255,0.1);
    color:var(--text);
  }
  .close-btn{
    background:var(--accent);
    color:white;
    border:none;
    padding:10px 20px;
    border-radius:6px;
    margin-top:20px;
    display:block;
    width:100%;
    cursor:pointer;
  }
</style>
</head>
<body>
<div class="browser">
  <div class="title-bar">
    🌐 JACK WEBSITE
    <div class="btns">
      <button class="icon-btn" id="settingsBtn" title="Settings">⚙️</button>
      <button class="icon-btn" id="fullBtn" title="Fullscreen">🔲</button>
    </div>
  </div>

  <div class="search-bar">
    <input id="query" placeholder="यहाँ खोजें या URL डालें..." />
    <button onclick="searchGoogle()">🔍</button>
  </div>

  <div class="iframe-wrap" id="view">
    <iframe id="frame" src="https://www.google.com/webhp?igu=1&hl=hi"></iframe>
  </div>
</div>

<!-- Settings Panel -->
<div class="settings-panel" id="settingsPanel">
  <div class="settings-box">
    <h2>⚙️ सेटिंग्स</h2>

    <label>🌐 भाषा चुनें:</label>
    <select id="langSelect">
      <option value="hi" selected>हिन्दी</option>
      <option value="en">English</option>
      <option value="bn">বাংলা</option>
      <option value="mr">मराठी</option>
      <option value="ta">தமிழ்</option>
    </select>

    <label>🎨 थीम:</label>
    <select id="themeSelect">
      <option value="dark" selected>Dark</option>
      <option value="light">Light</option>
    </select>

    <label>🏠 होमपेज:</label>
    <select id="homeSelect">
      <option value="https://www.google.com/webhp?igu=1&hl=hi">Google</option>
      <option value="https://www.bing.com">Bing</option>
      <option value="https://duckduckgo.com">DuckDuckGo</option>
    </select>

    <label>🔍 सर्च इंजन:</label>
    <select id="engineSelect">
      <option value="https://www.google.com/search?q=" selected>Google</option>
      <option value="https://www.bing.com/search?q=">Bing</option>
      <option value="https://duckduckgo.com/?q=">DuckDuckGo</option>
    </select>

    <button class="close-btn" onclick="closeSettings()">बंद करें</button>
  </div>
</div>

<script>
function searchGoogle(){
  let q=document.getElementById('query').value.trim();
  let frame=document.getElementById('frame');
  let lang=document.getElementById('langSelect').value;
  let engine=document.getElementById('engineSelect').value;

  if(q.startsWith("http")){
    frame.src=q;
  } else if(q.includes(".")){
    frame.src="https://"+q;
  } else {
    frame.src=engine+encodeURIComponent(q)+"&hl="+lang;
  }
}

// Fullscreen toggle
document.getElementById('fullBtn').addEventListener('click', function(){
  let iframe = document.getElementById('frame');
  if (!document.fullscreenElement) {
    iframe.requestFullscreen().catch(err => alert("Fullscreen error: "+err));
  } else {
    document.exitFullscreen();
  }
});

// Settings open & close
const settingsBtn=document.getElementById('settingsBtn');
const settingsPanel=document.getElementById('settingsPanel');
settingsBtn.onclick=()=>settingsPanel.style.display="flex";
function closeSettings(){settingsPanel.style.display="none";}

// Apply theme
document.getElementById('themeSelect').addEventListener('change', function(){
  if(this.value==="light"){
    document.documentElement.style.setProperty('--bg','#f5f5f5');
    document.documentElement.style.setProperty('--text','#111');
    document.documentElement.style.setProperty('--glass','rgba(0,0,0,0.05)');
  } else {
    document.documentElement.style.setProperty('--bg','#0f1724');
    document.documentElement.style.setProperty('--text','#e6eef8');
    document.documentElement.style.setProperty('--glass','rgba(255,255,255,0.05)');
  }
});
</script>
</body>
</html>
