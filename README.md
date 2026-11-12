# CB-s-unblocked-games-

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mac Desktop</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:radial-gradient(ellipse at 30% 20%,#241b43,#0d1220 55%,#050510);color:white;font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;height:100vh;overflow:hidden}
.menu{height:30px;background:#17171dcc;backdrop-filter:blur(20px);display:flex;justify-content:space-between;align-items:center;padding:0 15px;font-size:13px}
.desktop{height:calc(100vh - 30px);position:relative}
.stars{position:absolute;inset:0;pointer-events:none}
.icon{position:absolute;font-size:48px;cursor:pointer;filter:drop-shadow(0 5px 10px #0008)}
.icon:hover{transform:scale(1.15)}
.window{display:none;position:absolute;top:55px;left:50%;transform:translateX(-50%);width:min(650px,94vw);height:min(650px,80vh);background:#17171deF;border:1px solid #ffffff25;border-radius:14px;overflow:hidden;z-index:10;flex-direction:column;box-shadow:0 20px 60px #0009}
.window.active{display:flex}
.header{height:40px;display:flex;align-items:center;padding:0 12px;background:#ffffff0b;flex-shrink:0}
.dots{display:flex;gap:7px}
.dot{height:12px;width:12px;border-radius:50%;cursor:pointer}
.red{background:#ff5f57}.yellow{background:#febc2e}.green{background:#28c840}
.title{flex:1;text-align:center;font-size:13px;margin-right:38px}
.content{padding:14px;overflow:auto;display:flex;flex-direction:column;gap:10px;flex:1}
.card{display:flex;align-items:center;gap:13px;padding:13px;background:#ffffff0c;border:1px solid #ffffff15;border-radius:11px;color:white;text-decoration:none;cursor:pointer}
.card:hover{background:#ffffff20}
.card-icon{font-size:27px}
.card-title{font-weight:600;font-size:14px}
.card-desc{font-size:12px;color:#aaa;margin-top:3px}
.dock{position:absolute;bottom:12px;left:50%;transform:translateX(-50%);display:flex;gap:9px;padding:10px;background:#252530cc;backdrop-filter:blur(20px);border:1px solid #ffffff22;border-radius:17px;max-width:95vw;overflow-x:auto}
.dock button{font-size:27px;background:none;border:0;cursor:pointer}
.dock button:hover{transform:translateY(-6px)}
.browserbar{display:flex;gap:6px;padding:9px;background:#ffffff0b}
.browserbar input{flex:1;min-width:0;padding:9px;background:#0006;border:1px solid #ffffff30;border-radius:7px;color:white}
button{cursor:pointer;color:white}
.browserbar button,.action{border:0;border-radius:7px;padding:8px 12px;background:#ffffff20}
.primary{background:#087cff!important}
iframe{width:100%;flex:1;border:0;background:white;min-height:200px}
.note{font-size:11px;color:#aaa;padding:7px;text-align:center}
.game{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;width:220px;margin:auto}
.game button{height:68px;background:#ffffff15;border:1px solid #ffffff25;border-radius:9px;font-size:27px}
.status{text-align:center;color:#ccc;padding:8px}
.video{width:100%;aspect-ratio:16/9;border:0;background:black}
input,textarea{font-family:inherit}
@media(max-width:500px){.window{height:78vh;top:45px}.dock{gap:6px}.dock button{font-size:23px}}
</style>
</head>
<body>
<div class="menu">
  <span> &nbsp; Finder &nbsp; File &nbsp; Edit &nbsp; View</span>
  <span id="clock"></span>
</div>

<div class="desktop">
  <div class="icon" style="top:15%;left:8%" onclick="openApp('games')">🎮</div>
  <div class="icon" style="top:15%;right:8%" onclick="openApp('movies')">🎬</div>
  <div class="icon" style="top:42%;left:8%" onclick="openApp('music')">🎵</div>
  <div class="icon" style="top:42%;right:8%" onclick="openApp('social')">📱</div>
  <div class="icon" style="bottom:20%;left:45%" onclick="openApp('explore')">🌎</div>

  <!-- GAMES -->
  <section class="window" id="games">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('games')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title">Games</div></div>
    <div class="content">
      <h3>Play right here</h3>
      <div class="status" id="gameStatus">X's turn</div>
      <div class="game" id="gameBoard"></div>
      <button class="action primary" onclick="resetGame()">New game</button>
      <h3>More games</h3>
      <div id="gameLinks"></div>
    </div>
  </section>

  <!-- MOVIES -->
  <section class="window" id="movies">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('movies')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title">Movies & TV</div></div>
    <div class="content">
      <h3>Watch YouTube inside your desktop</h3>
      <input id="youtubeURL" placeholder="Paste a YouTube video link" style="padding:10px;border-radius:7px">
      <button class="action primary" onclick="playYouTube()">Play video</button>
      <iframe id="youtubePlayer" class="video" allowfullscreen allow="autoplay; encrypted-media; picture-in-picture"></iframe>
      <h3>Free streaming services</h3>
      <div id="movieLinks"></div>
    </div>
  </section>

  <!-- MUSIC -->
  <section class="window" id="music">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('music')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title">Music</div></div>
    <div class="content" id="musicLinks"></div>
  </section>

  <!-- SOCIAL -->
  <section class="window" id="social">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('social')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title">Social Media</div></div>
    <div class="content" id="socialLinks"></div>
  </section>

  <!-- EXPLORE -->
  <section class="window" id="explore">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('explore')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title">Explore</div></div>
    <div class="content" id="exploreLinks"></div>
  </section>

  <!-- INTERNAL BROWSER -->
  <section class="window" id="browser">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('browser')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title" id="browserTitle">Browser</div></div>
    <div class="browserbar">
      <button onclick="goBack()">‹</button>
      <button onclick="reloadPage()">↻</button>
      <input id="address" placeholder="Website address">
      <button class="primary" onclick="goToAddress()">Go</button>
      <button onclick="openExternal()">↗</button>
    </div>
    <iframe id="siteFrame" title="Website viewer"></iframe>
    <div class="note">Some websites block embedded browsing. Those sites cannot be forced to load inside this window.</div>
  </section>

  <!-- NOTES -->
  <section class="window" id="notes">
    <div class="header"><div class="dots"><span class="dot red" onclick="closeApp('notes')"></span><span class="dot yellow"></span><span class="dot green"></span></div><div class="title">Notes</div></div>
    <div class="content">
      <textarea id="noteText" placeholder="Write your notes..." style="flex:1;min-height:200px;background:#ffffff12;color:white;padding:12px;border-radius:9px"></textarea>
      <button class="action primary" onclick="saveNotes()">Save notes</button>
      <div id="noteStatus" class="status"></div>
    </div>
  </section>

  <div class="dock">
    <button onclick="openApp('games')">🎮</button>
    <button onclick="openApp('movies')">🎬</button>
    <button onclick="openApp('music')">🎵</button>
    <button onclick="openApp('social')">📱</button>
    <button onclick="openApp('explore')">🌎</button>
    <button onclick="openApp('notes')">📝</button>
  </div>
</div>

<script>
const websites={
 games:[
  ["Poki","🕹️","https://poki.com"],
  ["CrazyGames","🔥","https://www.crazygames.com"],
  ["itch.io","🎮","https://itch.io/games/free"],
  ["Coolmath Games","🧩","https://www.coolmathgames.com"]
 ],
 movies:[
  ["Tubi","📺","https://tubitv.com"],
  ["Pluto TV","📡","https://pluto.tv"],
  ["Plex","🎞️","https://watch.plex.tv"],
  ["Internet Archive","🏛️","https://archive.org/details/movies"],
  ["YouTube","▶️","https://youtube.com"]
 ],
 music:[
  ["SoundCloud","☁️","https://soundcloud.com"],
  ["Audiomack","🎧","https://audiomack.com"],
  ["Bandcamp","💿","https://bandcamp.com"],
  ["Radio Garden","🌍","https://radio.garden"]
 ],
 social:[
  ["TikTok","🎵","https://www.tiktok.com"],
  ["Reddit","👽","https://www.reddit.com"],
  ["Snapchat","👻","https://www.snapchat.com"],
  ["Pinterest","📌","https://www.pinterest.com"],
  ["Imgur","🖼️","https://imgur.com"],
  ["Tumblr","✒️","https://www.tumblr.com"]
 ],
 explore:[
  ["Neal.fun","🧪","https://neal.fun"],
  ["GeoGuessr","🧭","https://www.geoguessr.com"],
  ["Google Earth","🌎","https://earth.google.com/web/"],
  ["NASA","🚀","https://www.nasa.gov"],
  ["Wikipedia","📚","https://www.wikipedia.org"]
 ]
};

function makeCards(id){
 const el=document.getElementById(id+"Links");
 if(!el)return;
 el.innerHTML=websites[id].map(([name,emoji,url])=>
 `<a class="card" href="${url}" onclick="event.preventDefault();openSite('${url}','${name}')">
 <span class="card-icon">${emoji}</span>
 <span><div class="card-title">${name}</div><div class="card-desc">${url}</div></span>
 </a>`).join("");
}
["games","movies","music","social","explore"].forEach(makeCards);

function openApp(id){
 document.querySelectorAll(".window").forEach(w=>w.classList.remove("active"));
 document.getElementById(id).classList.add("active");
}
function closeApp(id){document.getElementById(id).classList.remove("active")}

let currentURL="",historyStack=[];
function openSite(url,title){
 currentURL=url;
 historyStack.push(url);
 document.getElementById("browserTitle").textContent=title;
 document.getElementById("address").value=url;
 document.getElementById("siteFrame").src=url;
 openApp("browser");
}
function goToAddress(){
 let url=document.getElementById("address").value.trim();
 if(!url)return;
 if(!/^https?:\/\//i.test(url))url="https://"+url;
 openSite(url,new URL(url).hostname);
}
function goBack(){
 if(historyStack.length>1){
  historyStack.pop();
  currentURL=historyStack[historyStack.length-1];
  document.getElementById("address").value=currentURL;
  document.getElementById("siteFrame").src=currentURL;
 }
}
function reloadPage(){
 document.getElementById("siteFrame").src=currentURL;
}
function openExternal(){
 if(currentURL)window.open(currentURL,"_blank","noopener");
}
function playYouTube(){
 const value=document.getElementById("youtubeURL").value.trim();
 try{
  const url=new URL(value);
  let id="";
  if(url.hostname.includes("youtu.be"))id=url.pathname.slice(1);
  else id=url.searchParams.get("v")||url.pathname.split("/").filter(Boolean).pop();
  if(!/^[A-Za-z0-9_-]{11}$/.test(id)){alert("Enter a valid YouTube video link.");return}
  document.getElementById("youtubePlayer").src="https://www.youtube-nocookie.com/embed/"+id;
 }catch(e){alert("Paste a full YouTube video URL.")}
}

// Tic-tac-toe
let board=Array(9).fill(""),turn="X",finished=false;
function drawBoard(){
 document.getElementById("gameBoard").innerHTML=board.map((v,i)=>
 `<button onclick="move(${i})">${v}</button>`).join("");
 document.getElementById("gameStatus").textContent=finished?"Game over":turn+"'s turn";
}
function move(i){
 if(finished||board[i])return;
 board[i]=turn;
 const wins=[[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,4,7],[0,4,8],[2,4,6]];
 if(wins.some(line=>line.every(n=>board[n]===turn))){
  finished=true;
  document.getElementById("gameStatus").textContent=turn+" wins!";
 }else if(board.every(Boolean)){
  finished=true;
  document.getElementById("gameStatus").textContent="Draw!";
 }else turn=turn==="X"?"O":"X";
 drawBoard();
}
function resetGame(){board=Array(9).fill("");turn="X";finished=false;drawBoard()}
drawBoard();

function saveNotes(){
 localStorage.setItem("mac-notes",document.getElementById("noteText").value);
 document.getElementById("noteStatus").textContent="Saved!";
}
document.getElementById("noteText").value=localStorage.getItem("mac-notes")||"";
setInterval(()=>document.getElementById("clock").textContent=new Date().toLocaleTimeString([],{hour:"2-digit",minute:"2-digit"}),1000);
</script>
</body>
</html>

