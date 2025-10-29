GOOGLE 
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no" />
<title>🌐 AI Web Browser</title>
<style>
  :root {
    --bg:#0f1724;
    --glass:rgba(255,255,255,0.05);
    --accent:#3b82f6;
    --text:#e6eef8;
    --muted:#a0aec0;
  }
  html,body {
    width:100%;
    height:100%;
    margin:0;
    padding:0;
    background:var(--bg);
    color:var(--text);
    font-family:"Segoe UI",Roboto,sans-serif;
    overflow:hidden;
  }
  .browser {
    display:flex;
    flex-direction:column;
    height:100vh;
    width:100vw;
    padding:10px;
    box-sizing:border-box;
    background:var(--bg);
  }
  .title-bar {
    text-align:center;
    font-weight:700;
    font-size:18px;
    background:var(--glass);
    padding:10px;
    border-radius:8px;
    margin-bottom:8px;
  }
  .search-bar {
    display:flex;
    gap:6px;
    margin-bottom:8px;
  }
  input {
    flex:1;
    padding:8px 10px;
    border-radius:6px;
    border:none;
    outline:none;
    font-size:16px;
  }
  button {
    background:var(--accent);
    color:white;
    border:none;
    border-radius:6px;
    padding:8px 14px;
    font-weight:600;
    cursor:pointer;
  }
  .iframe-wrap {
    flex:1;
    border:none;
    border-radius:0;
    overflow:hidden;
    background:#000; /* match google dark mode background */
  }
  iframe {
    width:100%;
    height:100%;
    border:none;
    display:block;
    background:#000; /* removes visible black border */
    transform:scale(1.05); /* slight zoom to remove side gaps */
    transform-origin:center center;
  }
</style>
</head>
<body>
<div class="browser">
  <div class="title-bar">🌐 AI Web Browser</div>
  <div class="search-bar">
    <input id="query" placeholder="यहाँ खोजें या URL डालें..." />
    <button onclick="searchGoogle()">🔍</button>
  </div>
  <div class="iframe-wrap" id="view">
    <iframe id="frame" src="https://www.google.com/webhp?igu=1"></iframe>
  </div>
</div>

<script>
function searchGoogle(){
  let q=document.getElementById('query').value.trim();
  let frame=document.getElementById('frame');
  if(q.startsWith("http")){
    frame.src=q;
  } else if(q.includes(".")){
    frame.src="https://"+q;
  } else {
    frame.src="https://www.google.com/search?q="+encodeURIComponent(q)+"&hl=hi";
  }
}
</script>
</body>
</html>
