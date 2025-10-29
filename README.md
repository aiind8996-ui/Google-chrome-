GOOGLE 
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>🌐 JACK WEBSITE</title>
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
  .browser {
    display:flex;flex-direction:column;height:100vh;
    padding:10px;
  }
  .title-bar {
    text-align:center;font-weight:700;
    font-size:18px;background:var(--glass);
    padding:10px;border-radius:8px;margin-bottom:8px;
  }
  .search-bar {
    display:flex;gap:6px;margin-bottom:8px;
  }
  input {
    flex:1;padding:8px 10px;border-radius:6px;
    border:none;outline:none;font-size:16px;
  }
  button {
    background:var(--accent);color:white;
    border:none;border-radius:6px;padding:8px 14px;
    font-weight:600;cursor:pointer;
  }
  .iframe-wrap {
    flex:1;border-radius:10px;overflow:hidden;
    border:1px solid rgba(255,255,255,0.05);
  }
  iframe {width:100%;height:100%;border:0;}
</style>
</head>
<body>
<div class="browser">
  <div class="title-bar">🌐 JACK WEBSITE</div>
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
