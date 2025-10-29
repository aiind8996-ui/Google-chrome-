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
    <iframe id="frame" src="https://www.google.com/webhp?igu=1&hl=hi"></iframe>
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
