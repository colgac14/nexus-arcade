<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NEXUS ARCADE</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&display=swap" rel="stylesheet">
<style>
:root{--bg:#04050f;--panel:#0d1128;--accent:#00f5ff;--accent2:#ff006e;--accent3:#a855f7;--gold:#ffd700;--text:#c8d8f0;--dim:#4a5a7a;--border:#1a2a4a;--card:#0a0f22;}
*{margin:0;padding:0;box-sizing:border-box;}
body{background:var(--bg);color:var(--text);font-family:'Rajdhani',sans-serif;min-height:100vh;overflow-x:hidden;}
body::before{content:'';position:fixed;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,0,0,0.07) 2px,rgba(0,0,0,0.07) 4px);pointer-events:none;z-index:9999;}
.gbg{position:fixed;inset:0;background-image:linear-gradient(rgba(0,245,255,0.03) 1px,transparent 1px),linear-gradient(90deg,rgba(0,245,255,0.03) 1px,transparent 1px);background-size:40px 40px;animation:gs 20s linear infinite;pointer-events:none;z-index:0;}
@keyframes gs{to{background-position:40px 40px;}}
header{position:sticky;top:0;z-index:100;background:rgba(4,5,15,0.95);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);}
.hi{max-width:1400px;margin:0 auto;display:flex;align-items:center;gap:1.5rem;height:65px;padding:0 2rem;}
.logo{font-family:'Orbitron',monospace;font-weight:900;font-size:1.3rem;letter-spacing:0.15em;color:var(--accent);text-shadow:0 0 30px rgba(0,245,255,0.5);white-space:nowrap;}
.logo span{color:var(--accent2);}
.sw{flex:1;max-width:500px;position:relative;}
.sw input{width:100%;background:var(--panel);border:1px solid var(--border);border-radius:4px;padding:0.55rem 1rem 0.55rem 2.4rem;color:var(--text);font-family:'Share Tech Mono',monospace;font-size:0.85rem;outline:none;transition:border-color 0.2s,box-shadow 0.2s;}
.sw input:focus{border-color:var(--accent);box-shadow:0 0 15px rgba(0,245,255,0.2);}
.sw input::placeholder{color:var(--dim);}
.si{position:absolute;left:0.7rem;top:50%;transform:translateY(-50%);color:var(--dim);}
.hr{margin-left:auto;font-family:'Share Tech Mono',monospace;font-size:0.75rem;color:var(--dim);}
.hr span{color:var(--accent);}
.hero{position:relative;z-index:1;text-align:center;padding:2.5rem 2rem 2rem;border-bottom:1px solid var(--border);background:linear-gradient(180deg,rgba(0,245,255,0.03) 0%,transparent 100%);}
.hero h1{font-family:'Orbitron',monospace;font-size:clamp(1.6rem,4vw,3rem);font-weight:900;color:var(--accent);text-shadow:0 0 40px rgba(0,245,255,0.4);margin-bottom:0.4rem;}
.hero p{color:var(--dim);font-size:1rem;}
.filters{position:relative;z-index:1;display:flex;flex-wrap:wrap;gap:0.4rem;padding:0.8rem 2rem;max-width:1400px;margin:0 auto;align-items:center;border-bottom:1px solid var(--border);}
.fl{font-family:'Share Tech Mono',monospace;font-size:0.7rem;color:var(--dim);letter-spacing:0.1em;margin-right:0.3rem;}
.fb{background:var(--panel);border:1px solid var(--border);color:var(--dim);font-family:'Rajdhani',sans-serif;font-weight:600;font-size:0.8rem;padding:0.3rem 0.9rem;border-radius:3px;cursor:pointer;transition:all 0.15s;}
.fb:hover,.fb.active{border-color:var(--accent);color:var(--accent);background:rgba(0,245,255,0.07);}
.main{position:relative;z-index:1;max-width:1400px;margin:0 auto;padding:1.5rem 2rem 4rem;}
.rbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:1.2rem;font-family:'Share Tech Mono',monospace;font-size:0.75rem;color:var(--dim);}
.rbar span{color:var(--accent);}
.gg{display:grid;grid-template-columns:repeat(auto-fill,minmax(190px,1fr));gap:0.9rem;}
.gc{background:var(--card);border:1px solid var(--border);border-radius:6px;overflow:hidden;cursor:pointer;transition:transform 0.2s,border-color 0.2s,box-shadow 0.2s;position:relative;}
.gc:hover{transform:translateY(-4px);border-color:var(--accent);box-shadow:0 8px 25px rgba(0,245,255,0.12);}
.gc:hover .ov{opacity:1;}
.gt{width:100%;aspect-ratio:16/10;display:flex;align-items:center;justify-content:center;font-size:2.8rem;position:relative;}
.ov{position:absolute;inset:0;background:rgba(0,245,255,0.1);display:flex;align-items:center;justify-content:center;opacity:0;transition:opacity 0.2s;}
.pnow{background:var(--accent);color:var(--bg);font-family:'Orbitron',monospace;font-size:0.6rem;font-weight:700;letter-spacing:0.1em;padding:0.45rem 1.1rem;border-radius:3px;border:none;cursor:pointer;}
.gi{padding:0.65rem;}
.gtitle{font-size:0.85rem;font-weight:700;color:#ddeeff;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;margin-bottom:0.25rem;}
.gm{display:flex;justify-content:space-between;align-items:center;}
.ggenre{font-family:'Share Tech Mono',monospace;font-size:0.6rem;color:var(--accent3);text-transform:uppercase;}
.grat{font-family:'Share Tech Mono',monospace;font-size:0.65rem;color:var(--gold);}
.gtag{position:absolute;top:0.35rem;right:0.35rem;font-family:'Orbitron',monospace;font-size:0.45rem;font-weight:700;letter-spacing:0.1em;padding:0.15rem 0.4rem;border-radius:2px;text-transform:uppercase;}
.tag-hot{background:var(--accent2);color:#fff;}
.tag-new{background:var(--accent);color:var(--bg);}
.tag-top{background:var(--gold);color:var(--bg);}
.pb{position:absolute;bottom:0.35rem;left:0.35rem;background:rgba(0,245,255,0.15);border:1px solid rgba(0,245,255,0.3);color:var(--accent);font-family:'Share Tech Mono',monospace;font-size:0.5rem;padding:0.1rem 0.4rem;border-radius:2px;}
.mbg{display:none;position:fixed;inset:0;background:rgba(2,3,12,0.97);z-index:500;align-items:center;justify-content:center;padding:1rem;}
.mbg.open{display:flex;}
.mbox{background:var(--panel);border:1px solid var(--accent);border-radius:8px;width:100%;max-width:860px;max-height:92vh;overflow:hidden;display:flex;flex-direction:column;box-shadow:0 0 60px rgba(0,245,255,0.15);animation:mIn 0.2s ease-out;}
@keyframes mIn{from{opacity:0;transform:scale(0.97)}to{opacity:1;transform:scale(1)}}
.mhdr{display:flex;align-items:center;padding:0.8rem 1.2rem;border-bottom:1px solid var(--border);flex-shrink:0;gap:0.8rem;}
.mtitle{font-family:'Orbitron',monospace;font-size:1rem;font-weight:700;color:var(--accent);}
.mgtag{font-family:'Share Tech Mono',monospace;font-size:0.7rem;color:var(--accent3);}
.mcls{background:none;border:1px solid var(--border);color:var(--dim);font-size:1.1rem;width:2rem;height:2rem;border-radius:3px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all 0.15s;margin-left:auto;}
.mcls:hover{border-color:var(--accent2);color:var(--accent2);}
.gframe{flex:1;background:#020510;min-height:420px;overflow-y:auto;display:flex;align-items:flex-start;justify-content:center;}
#gcon{width:100%;}
.pag{display:flex;justify-content:center;gap:0.4rem;margin-top:2.5rem;flex-wrap:wrap;}
.pgb{background:var(--panel);border:1px solid var(--border);color:var(--dim);font-family:'Share Tech Mono',monospace;font-size:0.8rem;padding:0.45rem 0.85rem;border-radius:3px;cursor:pointer;transition:all 0.15s;}
.pgb:hover,.pgb.active{border-color:var(--accent);color:var(--accent);background:rgba(0,245,255,0.07);}
.pgb:disabled{opacity:0.3;cursor:not-allowed;}
@media(max-width:700px){.hi{gap:0.8rem;padding:0 1rem;}.logo{font-size:1rem;}.hr{display:none;}.main{padding:1rem 1rem 3rem;}.gg{grid-template-columns:repeat(auto-fill,minmax(145px,1fr));gap:0.6rem;}.filters{padding:0.8rem 1rem;}}
</style>
</head>
<body>
<div class="gbg"></div>
<header>
  <div class="hi">
    <div class="logo">NEXUS<span>ARCADE</span></div>
    <div class="sw"><span class="si">⌕</span><input type="text" id="searchInput" placeholder="Search games..."></div>
    <div class="hr"><span id="hCount">2000</span> GAMES</div>
  </div>
</header>
<div class="hero">
  <h1>🎮 NEXUS ARCADE</h1>
  <p>12 real playable games + 1988 more coming soon — click any <span style="color:var(--accent)">▶ PLAYABLE</span> card to play instantly!</p>
</div>
<div class="filters">
  <span class="fl">GENRE:</span>
  <button class="fb active" data-genre="all">ALL</button>
  <button class="fb" data-genre="Arcade">Arcade</button>
  <button class="fb" data-genre="Puzzle">Puzzle</button>
  <button class="fb" data-genre="Action">Action</button>
  <button class="fb" data-genre="Strategy">Strategy</button>
  <button class="fb" data-genre="RPG">RPG</button>
  <button class="fb" data-genre="Racing">Racing</button>
  <button class="fb" data-genre="Horror">Horror</button>
</div>
<div class="main">
  <div class="rbar">
    <div>Showing <span id="showCount">0</span> games &nbsp;·&nbsp; <span style="color:var(--accent2)">▶ PLAYABLE</span> = real game inside</div>
    <div id="pageInfo">Page 1</div>
  </div>
  <div class="gg" id="gameGrid"></div>
  <div class="pag" id="pagination"></div>
</div>
<div class="mbg" id="modalBg">
  <div class="mbox">
    <div class="mhdr">
      <div class="mtitle" id="mTitle">Game</div>
      <span class="mgtag" id="mGenre"></span>
      <button class="mcls" id="modalClose">✕</button>
    </div>
    <div class="gframe"><div id="gcon"></div></div>
  </div>
</div>
<script>
// ─────────────────────────────────────────────
// REAL PLAYABLE GAMES
// ─────────────────────────────────────────────
const REAL=[
  {id:1,title:'Snake Neon',genre:'Arcade',emoji:'🐍',rating:4.8,year:2024,tag:'top',playable:true,hue:140,play:playSnake},
  {id:2,title:'Breakout X',genre:'Arcade',emoji:'🧱',rating:4.6,year:2024,tag:'hot',playable:true,hue:200,play:playBreakout},
  {id:3,title:'Tetris Zero',genre:'Puzzle',emoji:'🟦',rating:4.9,year:2024,tag:'top',playable:true,hue:220,play:playTetris},
  {id:4,title:'Space Invaders FX',genre:'Action',emoji:'👾',rating:4.7,year:2024,tag:'new',playable:true,hue:280,play:playSpaceInvaders},
  {id:5,title:'Pong Duel',genre:'Arcade',emoji:'🏓',rating:4.3,year:2024,tag:null,playable:true,hue:50,play:playPong},
  {id:6,title:'Flappy Neon',genre:'Arcade',emoji:'🐦',rating:4.5,year:2024,tag:'hot',playable:true,hue:170,play:playFlappy},
  {id:7,title:'Minesweeper Pro',genre:'Puzzle',emoji:'💣',rating:4.4,year:2024,tag:null,playable:true,hue:30,play:playMinesweeper},
  {id:8,title:'2048 Surge',genre:'Puzzle',emoji:'🔢',rating:4.7,year:2024,tag:'top',playable:true,hue:40,play:play2048},
  {id:9,title:'Asteroid Storm',genre:'Action',emoji:'🌠',rating:4.6,year:2024,tag:'new',playable:true,hue:260,play:playAsteroids},
  {id:10,title:'Memory Match',genre:'Puzzle',emoji:'🃏',rating:4.2,year:2024,tag:null,playable:true,hue:320,play:playMemory},
  {id:11,title:'Tower Stack',genre:'Arcade',emoji:'🏗️',rating:4.4,year:2024,tag:null,playable:true,hue:90,play:playTowerStack},
  {id:12,title:'Dino Run',genre:'Action',emoji:'🦕',rating:4.5,year:2024,tag:'hot',playable:true,hue:60,play:playDino},
];
 
// ─────────────────────────────────────────────
// GENERATE 1988 FAKE GAMES
// ─────────────────────────────────────────────
const GNS=['Action','Adventure','Puzzle','RPG','Racing','Sports','Strategy','Shooter','Horror','Arcade','Simulation','Fighting'];
const ADJ=['Epic','Legendary','Dark','Neon','Turbo','Shadow','Cyber','Blazing','Thunder','Steel','Cosmic','Phantom','Iron','Golden','Void','Storm','Crystal','Savage','Pixel','Quantum','Hyper','Ultra','Ancient','Silent','Mystic'];
const NON=['Quest','Wars','Arena','Runner','Strike','Blast','Clash','Force','Realm','Empire','Saga','Legends','Odyssey','Rising','Assault','Escape','Fury','Impact','Zone','Legacy','Rift','Nexus','Core','Surge','Drift'];
const DVS=['PixelForge','NeonStudio','ArcadeLab','ByteWorks','GridPunk','VoxelCraft','BitShift','CodeNova','HexForge','ZeroGravity'];
const EMO={Action:'⚔️',Adventure:'🗺️',Puzzle:'🧩',RPG:'🧙',Racing:'🏎️',Sports:'⚽',Strategy:'♟️',Shooter:'🔫',Horror:'👻',Arcade:'👾',Simulation:'🏙️',Fighting:'🥋'};
const TAGP=['hot','new','top',null,null,null,null];
function genFake(){
  const out=[];
  for(let i=0;i<1988;i++){
    const g=GNS[i%GNS.length];
    out.push({
      id:i+100,
      title:ADJ[(i*7)%ADJ.length]+' '+NON[(i*3)%NON.length],
      genre:g,emoji:EMO[g]||'🎮',
      rating:parseFloat((3+Math.random()*2).toFixed(1)),
      year:2015+i%10,tag:TAGP[i%TAGP.length],
      hue:i*18%360,playable:false,
      dev:DVS[i%DVS.length],play:null
    });
  }
  return out;
}
const ALL=[...REAL,...genFake()];
 
// ─────────────────────────────────────────────
// RENDER
// ─────────────────────────────────────────────
const PGS=40;
let filtered=[...ALL],page=1,genre='all',search='';
 
function bg(h){return`linear-gradient(135deg,hsl(${h},60%,7%),hsl(${(h+60)%360},50%,12%))`;}
 
function renderGrid(){
  const grid=document.getElementById('gameGrid');
  const s=(page-1)*PGS,items=filtered.slice(s,s+PGS),tp=Math.ceil(filtered.length/PGS);
  document.getElementById('showCount').textContent=filtered.length;
  document.getElementById('hCount').textContent=ALL.length;
  document.getElementById('pageInfo').textContent='Page '+page+' of '+tp;
  grid.innerHTML=items.map(g=>`
    <div class="gc" data-id="${g.id}">
      <div class="gt" style="background:${bg(g.hue)}">${g.emoji}
        <div class="ov"><button class="pnow">${g.playable?'▶ PLAY':'🔒 SOON'}</button></div>
        ${g.tag?`<div class="gtag tag-${g.tag}">${g.tag}</div>`:''}
        ${g.playable?'<div class="pb">▶ PLAYABLE</div>':''}
      </div>
      <div class="gi">
        <div class="gtitle" title="${g.title}">${g.title}</div>
        <div class="gm"><div class="ggenre">${g.genre}</div><div class="grat">★${g.rating.toFixed(1)}</div></div>
      </div>
    </div>`).join('');
  grid.querySelectorAll('.gc').forEach(card=>{
    card.addEventListener('click',()=>{
      const g=ALL.find(x=>x.id===+card.dataset.id);
      if(!g)return;
      g.playable&&g.play?openGame(g):showSoon(g);
    });
  });
  renderPag(tp);
}
 
function renderPag(tp){
  const p=document.getElementById('pagination');
  if(tp<=1){p.innerHTML='';return;}
  let h=`<button class="pgb" id="pP" ${page===1?'disabled':''}>‹ PREV</button>`;
  const r=[];
  if(tp<=7)for(let i=1;i<=tp;i++)r.push(i);
  else{r.push(1);if(page>3)r.push('…');for(let i=Math.max(2,page-1);i<=Math.min(tp-1,page+1);i++)r.push(i);if(page<tp-2)r.push('…');r.push(tp);}
  r.forEach(x=>{if(x==='…')h+=`<span style="color:var(--dim);padding:0 .3rem;font-family:monospace">…</span>`;else h+=`<button class="pgb ${x===page?'active':''}" data-p="${x}">${x}</button>`;});
  h+=`<button class="pgb" id="pN" ${page===tp?'disabled':''}>NEXT ›</button>`;
  p.innerHTML=h;
  p.querySelectorAll('[data-p]').forEach(b=>b.addEventListener('click',()=>{page=+b.dataset.p;renderGrid();scrollTo({top:0,behavior:'smooth'});}));
  document.getElementById('pP')?.addEventListener('click',()=>{if(page>1){page--;renderGrid();scrollTo({top:0,behavior:'smooth'});}});
  document.getElementById('pN')?.addEventListener('click',()=>{if(page<tp){page++;renderGrid();scrollTo({top:0,behavior:'smooth'});}});
}
 
function applyFilter(){
  let g=[...ALL];
  if(genre!=='all')g=g.filter(x=>x.genre===genre);
  if(search){const q=search.toLowerCase();g=g.filter(x=>x.title.toLowerCase().includes(q)||x.genre.toLowerCase().includes(q));}
  filtered=g;page=1;renderGrid();
}
 
document.getElementById('searchInput').addEventListener('input',e=>{search=e.target.value.trim();applyFilter();});
document.querySelectorAll('.fb').forEach(b=>b.addEventListener('click',()=>{document.querySelectorAll('.fb').forEach(x=>x.classList.remove('active'));b.classList.add('active');genre=b.dataset.genre;applyFilter();}));
 
// ─────────────────────────────────────────────
// MODAL
// ─────────────────────────────────────────────
function openGame(g){
  document.getElementById('mTitle').textContent=g.title;
  document.getElementById('mGenre').textContent=g.genre;
  document.getElementById('gcon').innerHTML='';
  document.getElementById('modalBg').classList.add('open');
  document.body.style.overflow='hidden';
  g.play(document.getElementById('gcon'));
}
function showSoon(g){
  document.getElementById('mTitle').textContent=g.title;
  document.getElementById('mGenre').textContent=g.genre;
  document.getElementById('gcon').innerHTML=`<div style="text-align:center;padding:4rem 2rem;font-family:'Share Tech Mono',monospace;color:var(--dim)"><div style="font-size:5rem;margin-bottom:1.2rem">${g.emoji}</div><div style="color:var(--accent);font-size:1.1rem;margin-bottom:.6rem">${g.title}</div><div style="font-size:.8rem;letter-spacing:.12em">COMING SOON — IN DEVELOPMENT</div></div>`;
  document.getElementById('modalBg').classList.add('open');
  document.body.style.overflow='hidden';
}
function closeModal(){document.getElementById('modalBg').classList.remove('open');document.body.style.overflow='';document.getElementById('gcon').innerHTML='';}
document.getElementById('modalClose').addEventListener('click',closeModal);
document.getElementById('modalBg').addEventListener('click',e=>{if(e.target===document.getElementById('modalBg'))closeModal();});
document.addEventListener('keydown',e=>{if(e.key==='Escape')closeModal();});
 
// ═══════════════════════════════════════════════════════════
// GAME 1 — SNAKE
// ═══════════════════════════════════════════════════════════
function playSnake(con){
  const W=400,H=400,SZ=20,COLS=W/SZ,ROWS=H/SZ;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="snkS">0</span> &nbsp;|&nbsp; BEST: <span id="snkB">0</span></div>
    <canvas id="snkC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Arrow keys / WASD to move &nbsp;·&nbsp; SPACE to restart</div>
  </div>`;
  const cv=document.getElementById('snkC'),ctx=cv.getContext('2d');
  let snake=[{x:10,y:10},{x:9,y:10},{x:8,y:10}];
  let dir={x:1,y:0},nd={x:1,y:0},food=newFood(),score=0,best=0,dead=false;
  function newFood(){for(;;){const f={x:~~(Math.random()*COLS),y:~~(Math.random()*ROWS)};if(!snake.some(s=>s.x===f.x&&s.y===f.y))return f;}}
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    ctx.strokeStyle='rgba(0,245,255,.04)';
    for(let i=0;i<=COLS;i++){ctx.beginPath();ctx.moveTo(i*SZ,0);ctx.lineTo(i*SZ,H);ctx.stroke();}
    for(let i=0;i<=ROWS;i++){ctx.beginPath();ctx.moveTo(0,i*SZ);ctx.lineTo(W,i*SZ);ctx.stroke();}
    ctx.fillStyle='#ff006e';ctx.shadowColor='#ff006e';ctx.shadowBlur=14;
    ctx.fillRect(food.x*SZ+2,food.y*SZ+2,SZ-4,SZ-4);
    snake.forEach((s,i)=>{const t=1-i/snake.length;ctx.fillStyle=`hsl(185,100%,${28+t*38}%)`;ctx.shadowColor='rgba(0,245,255,.5)';ctx.shadowBlur=i===0?12:3;ctx.fillRect(s.x*SZ+1,s.y*SZ+1,SZ-2,SZ-2);});
    ctx.shadowBlur=0;
    if(dead){
      ctx.fillStyle='rgba(4,5,15,.78)';ctx.fillRect(0,0,W,H);
      ctx.fillStyle='#ff006e';ctx.font='bold 28px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',W/2,H/2-18);
      ctx.fillStyle='#00f5ff';ctx.font='14px Share Tech Mono,monospace';ctx.fillText('Score: '+score,W/2,H/2+10);
      ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('SPACE to restart',W/2,H/2+34);
    }
  }
  function step(){
    if(dead)return;
    dir=nd;
    const h={x:(snake[0].x+dir.x+COLS)%COLS,y:(snake[0].y+dir.y+ROWS)%ROWS};
    if(snake.some(s=>s.x===h.x&&s.y===h.y)){dead=true;best=Math.max(best,score);document.getElementById('snkB').textContent=best;draw();return;}
    snake.unshift(h);
    if(h.x===food.x&&h.y===food.y){score++;document.getElementById('snkS').textContent=score;food=newFood();}else snake.pop();
    draw();
    setTimeout(step,Math.max(72,140-score*3));
  }
  const KM={'ArrowUp':{x:0,y:-1},'ArrowDown':{x:0,y:1},'ArrowLeft':{x:-1,y:0},'ArrowRight':{x:1,y:0},w:{x:0,y:-1},s:{x:0,y:1},a:{x:-1,y:0},d:{x:1,y:0}};
  function kh(e){
    if(e.key===' '&&dead){snake=[{x:10,y:10},{x:9,y:10},{x:8,y:10}];dir={x:1,y:0};nd={x:1,y:0};score=0;food=newFood();dead=false;document.getElementById('snkS').textContent=0;step();e.preventDefault();return;}
    const d=KM[e.key];
    if(d&&!(d.x===-dir.x&&d.y===0)&&!(d.y===-dir.y&&d.x===0)){nd=d;e.preventDefault();}
  }
  document.addEventListener('keydown',kh);cv.focus();draw();step();
}
 
// ═══════════════════════════════════════════════════════════
// GAME 2 — BREAKOUT
// ═══════════════════════════════════════════════════════════
function playBreakout(con){
  const W=480,H=360;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="brkS">0</span> &nbsp;|&nbsp; LIVES: <span id="brkL">3</span></div>
    <canvas id="brkC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block;cursor:none" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Move mouse or ← → to move paddle &nbsp;·&nbsp; SPACE to restart</div>
  </div>`;
  const cv=document.getElementById('brkC'),ctx=cv.getContext('2d');
  const PW=80,PH=10,BR=7;
  let px=(W-PW)/2,bx=W/2,by=H-60,bdx=3.8,bdy=-3.8;
  let lives=3,score=0,over=false,won=false,lK=false,rK=false;
  const BC=['#ff006e','#ff5500','#ffd700','#00f5ff','#a855f7'];
  let bricks=[];
  function mk(){bricks=[];for(let r=0;r<5;r++)for(let c=0;c<10;c++)bricks.push({x:8+c*46,y:28+r*22,a:true,col:BC[r]});}
  mk();
  cv.addEventListener('mousemove',e=>{const r=cv.getBoundingClientRect();px=Math.min(W-PW,Math.max(0,e.clientX-r.left-PW/2));});
  function kh(e){
    if(e.key==='ArrowLeft')lK=e.type==='keydown';
    if(e.key==='ArrowRight')rK=e.type==='keydown';
    if(e.key===' '&&over){mk();px=(W-PW)/2;bx=W/2;by=H-60;bdx=3.8;bdy=-3.8;lives=3;score=0;over=false;won=false;document.getElementById('brkS').textContent=0;document.getElementById('brkL').textContent=3;}
    e.preventDefault();
  }
  document.addEventListener('keydown',kh);document.addEventListener('keyup',kh);
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    bricks.forEach(b=>{if(!b.a)return;ctx.fillStyle=b.col;ctx.shadowColor=b.col;ctx.shadowBlur=6;ctx.fillRect(b.x,b.y,44,18);ctx.shadowBlur=0;ctx.fillStyle='rgba(255,255,255,.18)';ctx.fillRect(b.x,b.y,44,5);});
    ctx.fillStyle='#00f5ff';ctx.shadowColor='#00f5ff';ctx.shadowBlur=14;ctx.fillRect(px,H-22,PW,PH);ctx.shadowBlur=0;
    ctx.fillStyle='#fff';ctx.shadowColor='#00f5ff';ctx.shadowBlur=16;ctx.beginPath();ctx.arc(bx,by,BR,0,Math.PI*2);ctx.fill();ctx.shadowBlur=0;
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle=won?'#00f5ff':'#ff006e';ctx.font='bold 26px Orbitron,monospace';ctx.textAlign='center';ctx.fillText(won?'YOU WIN!':'GAME OVER',W/2,H/2-15);ctx.fillStyle='#00f5ff';ctx.font='13px Share Tech Mono,monospace';ctx.fillText('Score: '+score,W/2,H/2+10);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('SPACE to restart',W/2,H/2+34);}
  }
  function update(){
    if(over)return;
    if(lK)px=Math.max(0,px-6);if(rK)px=Math.min(W-PW,px+6);
    bx+=bdx;by+=bdy;
    if(bx-BR<0||bx+BR>W)bdx=-bdx;
    if(by-BR<0)bdy=Math.abs(bdy);
    if(by+BR>H-22&&bdy>0&&bx>px&&bx<px+PW){bdy=-Math.abs(bdy);bdx=(bx-(px+PW/2))/(PW/2)*5;}
    if(by+BR>H){lives--;document.getElementById('brkL').textContent=lives;if(lives<=0)over=true;else{by=H-60;bx=W/2;bdx=3.8;bdy=-3.8;}}
    bricks.forEach(b=>{if(!b.a)return;if(bx+BR>b.x&&bx-BR<b.x+44&&by+BR>b.y&&by-BR<b.y+18){b.a=false;bdy=-bdy;score+=10;document.getElementById('brkS').textContent=score;}});
    if(bricks.every(b=>!b.a)){won=true;over=true;}
    draw();
  }
  cv.focus();setInterval(update,16);
}
 
// ═══════════════════════════════════════════════════════════
// GAME 3 — TETRIS
// ═══════════════════════════════════════════════════════════
function playTetris(con){
  const W=200,H=400,BS=20,C=10,R=20;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="tetS">0</span> &nbsp;|&nbsp; LINES: <span id="tetL">0</span></div>
    <canvas id="tetC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">← → move &nbsp; ↑ rotate &nbsp; ↓ drop &nbsp; SPACE restart</div>
  </div>`;
  const cv=document.getElementById('tetC'),ctx=cv.getContext('2d');
  const PS=[{s:[[1,1,1,1]],c:'#00f5ff'},{s:[[1,0],[1,0],[1,1]],c:'#ff7700'},{s:[[0,1],[0,1],[1,1]],c:'#0055ff'},{s:[[1,1],[1,1]],c:'#ffd700'},{s:[[0,1,1],[1,1,0]],c:'#00ff55'},{s:[[1,1,0],[0,1,1]],c:'#ff006e'},{s:[[0,1,0],[1,1,1]],c:'#a855f7'}];
  let board=Array.from({length:R},()=>Array(C).fill(0)),sc=0,li=0,over=false,cur,cx,cy;
  function rp(){const p=PS[~~(Math.random()*PS.length)];cur={s:JSON.parse(JSON.stringify(p.s)),c:p.c};cx=~~((C-p.s[0].length)/2);cy=0;}
  function rot(s){return s[0].map((_,i)=>s.map(r=>r[i]).reverse());}
  function ok(s,ox,oy){return s.every((row,r)=>row.every((v,cl)=>!v||(oy+r>=0&&oy+r<R&&ox+cl>=0&&ox+cl<C&&!board[oy+r][ox+cl])));}
  function place(){
    cur.s.forEach((row,r)=>row.forEach((v,cl)=>{if(v)board[cy+r][cx+cl]=cur.c;}));
    let cl=0;board=board.filter(row=>{if(row.every(x=>x)){cl++;return false;}return true;});
    while(board.length<R)board.unshift(Array(C).fill(0));
    li+=cl;sc+=cl*100+cl*cl*50;
    document.getElementById('tetS').textContent=sc;document.getElementById('tetL').textContent=li;
    rp();if(!ok(cur.s,cx,cy))over=true;
  }
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    ctx.strokeStyle='rgba(0,245,255,.05)';
    for(let i=0;i<=C;i++){ctx.beginPath();ctx.moveTo(i*BS,0);ctx.lineTo(i*BS,H);ctx.stroke();}
    for(let i=0;i<=R;i++){ctx.beginPath();ctx.moveTo(0,i*BS);ctx.lineTo(W,i*BS);ctx.stroke();}
    board.forEach((row,r)=>row.forEach((cl,c)=>{if(cl){ctx.fillStyle=cl;ctx.shadowColor=cl;ctx.shadowBlur=5;ctx.fillRect(c*BS+1,r*BS+1,BS-2,BS-2);ctx.shadowBlur=0;}}));
    cur.s.forEach((row,r)=>row.forEach((v,cl)=>{if(v){ctx.fillStyle=cur.c;ctx.shadowColor=cur.c;ctx.shadowBlur=8;ctx.fillRect((cx+cl)*BS+1,(cy+r)*BS+1,BS-2,BS-2);ctx.shadowBlur=0;}}));
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle='#ff006e';ctx.font='bold 22px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',W/2,H/2-10);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('SPACE to restart',W/2,H/2+22);}
  }
  function kh(e){
    if(e.key===' '&&over){board=Array.from({length:R},()=>Array(C).fill(0));sc=0;li=0;over=false;document.getElementById('tetS').textContent=0;document.getElementById('tetL').textContent=0;rp();e.preventDefault();return;}
    if(over)return;
    if(e.key==='ArrowLeft'&&ok(cur.s,cx-1,cy))cx--;
    if(e.key==='ArrowRight'&&ok(cur.s,cx+1,cy))cx++;
    if(e.key==='ArrowDown'&&ok(cur.s,cx,cy+1))cy++;
    if(e.key==='ArrowUp'){const nr=rot(cur.s);if(ok(nr,cx,cy))cur.s=nr;}
    e.preventDefault();draw();
  }
  document.addEventListener('keydown',kh);
  rp();cv.focus();
  setInterval(()=>{if(over)return;if(ok(cur.s,cx,cy+1))cy++;else place();draw();},500);
  draw();
}
 
// ═══════════════════════════════════════════════════════════
// GAME 4 — SPACE INVADERS
// ═══════════════════════════════════════════════════════════
function playSpaceInvaders(con){
  const W=480,H=380;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="siS">0</span> &nbsp;|&nbsp; LIVES: <span id="siL">3</span></div>
    <canvas id="siC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">← → move &nbsp; SPACE shoot &nbsp; SPACE restart after death</div>
  </div>`;
  const cv=document.getElementById('siC'),ctx=cv.getContext('2d');
  let px=W/2-20,pw=40,ph=12,py=H-38;
  let bullets=[],eb=[],sc=0,lives=3,over=false,won=false,lK=false,rK=false,spK=false,lastShot=0,inv=0;
  function mkA(){return Array.from({length:40},(_,i)=>({x:28+(i%10)*42,y:28+~~(i/10)*35,a:true,row:~~(i/10)}));}
  let aliens=mkA(),aDir=1,aTick=0,aDrop=false,aSpd=0.8;
  function restart(){aliens=mkA();px=W/2-20;bullets=[];eb=[];sc=0;lives=3;over=false;won=false;aDir=1;aTick=0;aDrop=false;aSpd=0.8;inv=0;document.getElementById('siS').textContent=0;document.getElementById('siL').textContent=3;}
  function kh(e){
    if(e.key==='ArrowLeft')lK=e.type==='keydown';
    if(e.key==='ArrowRight')rK=e.type==='keydown';
    if(e.key===' '){spK=e.type==='keydown';e.preventDefault();}
    if(e.key===' '&&over&&e.type==='keydown')restart();
  }
  document.addEventListener('keydown',kh);document.addEventListener('keyup',kh);
  const ACOLS=['#ff006e','#ff5500','#ffd700','#a855f7'];
  function update(){
    if(over)return;
    if(lK)px=Math.max(0,px-5);if(rK)px=Math.min(W-pw,px+5);
    const now=Date.now();
    if(spK&&now-lastShot>300){bullets.push({x:px+pw/2,y:py-5});lastShot=now;}
    bullets=bullets.filter(b=>{b.y-=9;return b.y>0;});
    eb=eb.filter(b=>{b.y+=4;return b.y<H;});
    aTick++;
    if(aTick>~~(55/aSpd)){
      aTick=0;
      const alive=aliens.filter(a=>a.a);
      if(!alive.length){won=true;over=true;return;}
      if(aDrop){aliens.forEach(a=>a.y+=16);aDir=-aDir;aDrop=false;}
      else{
        aliens.forEach(a=>a.x+=aDir*16);
        const mx=Math.max(...alive.map(a=>a.x)),mn=Math.min(...alive.map(a=>a.x));
        if(mx>W-28||mn<8)aDrop=true;
      }
      if(Math.random()<0.15&&alive.length){const a=alive[~~(Math.random()*alive.length)];eb.push({x:a.x+13,y:a.y+24});}
    }
    const alive=aliens.filter(a=>a.a);
    aSpd=Math.min(5,0.8+(40-alive.length)/12);
    bullets.forEach(b=>{aliens.forEach(a=>{if(!a.a)return;if(b.x>a.x&&b.x<a.x+26&&b.y>a.y&&b.y<a.y+24){a.a=false;b.y=-999;sc+=(4-a.row)*10;document.getElementById('siS').textContent=sc;}});});
    if(inv>0)inv--;
    if(!inv){
      eb.forEach(b=>{if(b.x>px&&b.x<px+pw&&b.y>py&&b.y<py+ph){b.y=-999;lives--;document.getElementById('siL').textContent=lives;inv=90;if(lives<=0)over=true;}});
      aliens.forEach(a=>{if(a.a&&a.y+24>py)over=true;});
    }
  }
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    [[50,18],[130,55],[220,28],[340,42],[430,18],[470,65],[90,90],[260,78]].forEach(([x,y])=>{ctx.fillStyle='rgba(255,255,255,.4)';ctx.fillRect(x,y,1,1);});
    aliens.forEach(a=>{if(!a.a)return;ctx.fillStyle=ACOLS[a.row%4];ctx.shadowColor=ACOLS[a.row%4];ctx.shadowBlur=8;ctx.font='20px monospace';ctx.textAlign='center';ctx.fillText('👾',a.x+13,a.y+22);ctx.shadowBlur=0;});
    if(!(inv>0&&~~(inv/5)%2)){
      ctx.fillStyle='#00f5ff';ctx.shadowColor='#00f5ff';ctx.shadowBlur=12;
      ctx.fillRect(px,py,pw,ph);ctx.fillRect(px+pw/2-4,py-8,8,10);ctx.shadowBlur=0;
    }
    ctx.fillStyle='#fff';ctx.shadowColor='#fff';ctx.shadowBlur=8;
    bullets.forEach(b=>ctx.fillRect(b.x-2,b.y,4,10));
    ctx.fillStyle='#ff006e';ctx.shadowColor='#ff006e';
    eb.forEach(b=>ctx.fillRect(b.x-2,b.y,4,10));
    ctx.shadowBlur=0;
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle=won?'#00f5ff':'#ff006e';ctx.font='bold 26px Orbitron,monospace';ctx.textAlign='center';ctx.fillText(won?'YOU WIN!':'GAME OVER',W/2,H/2-15);ctx.fillStyle='#00f5ff';ctx.font='13px Share Tech Mono,monospace';ctx.fillText('Score: '+sc,W/2,H/2+10);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('SPACE to restart',W/2,H/2+34);}
  }
  cv.focus();setInterval(()=>{update();draw();},1000/60);
}
 
// ═══════════════════════════════════════════════════════════
// GAME 5 — PONG
// ═══════════════════════════════════════════════════════════
function playPong(con){
  const W=480,H=320,PH=70,PW=10;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">YOU: <span id="pgY">0</span> &nbsp;|&nbsp; CPU: <span id="pgC">0</span></div>
    <canvas id="pgC2" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">W / S or ↑ / ↓ to move your paddle (left side)</div>
  </div>`;
  const cv=document.getElementById('pgC2'),ctx=cv.getContext('2d');
  let py=H/2-PH/2,cy=H/2-PH/2,bx=W/2,by=H/2,bdx=4,bdy=3,pSc=0,cSc=0,uK=false,dK=false;
  function kh(e){if(e.key==='ArrowUp'||e.key==='w')uK=e.type==='keydown';if(e.key==='ArrowDown'||e.key==='s')dK=e.type==='keydown';e.preventDefault();}
  document.addEventListener('keydown',kh);document.addEventListener('keyup',kh);
  function reset(){bx=W/2;by=H/2;bdx=(Math.random()>0.5?1:-1)*4;bdy=(Math.random()-.5)*6;}
  function update(){
    if(uK)py=Math.max(0,py-6);if(dK)py=Math.min(H-PH,py+6);
    const spd=Math.min(6,Math.abs(bdy)+0.3);
    if(cy+PH/2<by+8)cy=Math.min(H-PH,cy+spd);else cy=Math.max(0,cy-spd);
    bx+=bdx;by+=bdy;
    if(by-6<0||by+6>H)bdy=-bdy;
    if(bx-6<PW+5&&bdy,by>py&&by<py+PH&&bdx<0){bdx=Math.abs(bdx);bdy=(by-(py+PH/2))/12*5;}
    if(bx+6>W-PW-5&&by>cy&&by<cy+PH&&bdx>0){bdx=-Math.abs(bdx);bdy=(by-(cy+PH/2))/12*5;}
    if(bx<0){cSc++;document.getElementById('pgC').textContent=cSc;reset();}
    if(bx>W){pSc++;document.getElementById('pgY').textContent=pSc;reset();}
  }
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    ctx.setLineDash([8,8]);ctx.strokeStyle='rgba(0,245,255,.12)';ctx.beginPath();ctx.moveTo(W/2,0);ctx.lineTo(W/2,H);ctx.stroke();ctx.setLineDash([]);
    ctx.fillStyle='#00f5ff';ctx.shadowColor='#00f5ff';ctx.shadowBlur=12;
    ctx.fillRect(5,py,PW,PH);ctx.fillRect(W-PW-5,cy,PW,PH);ctx.shadowBlur=0;
    ctx.fillStyle='#fff';ctx.shadowColor='#fff';ctx.shadowBlur=16;
    ctx.beginPath();ctx.arc(bx,by,6,0,Math.PI*2);ctx.fill();ctx.shadowBlur=0;
  }
  cv.focus();setInterval(()=>{update();draw();},1000/60);
}
 
// ═══════════════════════════════════════════════════════════
// GAME 6 — FLAPPY BIRD
// ═══════════════════════════════════════════════════════════
function playFlappy(con){
  const W=360,H=420,bx=80,br=13,gap=130,PW=52;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="flS">0</span> &nbsp;|&nbsp; BEST: <span id="flB">0</span></div>
    <canvas id="flC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block;cursor:pointer" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Click or SPACE to flap</div>
  </div>`;
  const cv=document.getElementById('flC'),ctx=cv.getContext('2d');
  let by2=H/2,bv=0,sc=0,best=0,pipes=[],over=false,started=false;
  function addPipe(){const top=Math.random()*(H-gap-100)+50;pipes.push({x:W,top,bot:top+gap,passed:false});}
  function flap(){if(over){restart();return;}if(!started)started=true;bv=-8;}
  function restart(){by2=H/2;bv=0;sc=0;pipes=[];over=false;started=false;document.getElementById('flS').textContent=0;}
  cv.addEventListener('click',flap);
  function kh(e){if(e.key===' '){flap();e.preventDefault();}}
  document.addEventListener('keydown',kh);
  function update(){
    if(!started||over)return;
    bv+=0.42;by2+=bv;
    if(by2-br<0||by2+br>H){over=true;best=Math.max(best,sc);document.getElementById('flB').textContent=best;return;}
    pipes.forEach(p=>p.x-=2.8);
    if(!pipes.length||pipes[pipes.length-1].x<W-190)addPipe();
    pipes=pipes.filter(p=>p.x>-PW);
    pipes.forEach(p=>{
      if(bx+br>p.x&&bx-br<p.x+PW&&(by2-br<p.top||by2+br>p.bot)){over=true;best=Math.max(best,sc);document.getElementById('flB').textContent=best;}
      if(!p.passed&&p.x+PW<bx){p.passed=true;sc++;document.getElementById('flS').textContent=sc;}
    });
  }
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    pipes.forEach(p=>{
      ctx.fillStyle='#00aa44';ctx.shadowColor='#00cc55';ctx.shadowBlur=8;
      ctx.fillRect(p.x,0,PW,p.top);ctx.fillRect(p.x,p.bot,PW,H-p.bot);
      ctx.fillStyle='#00cc55';ctx.fillRect(p.x-4,p.top-22,PW+8,22);ctx.fillRect(p.x-4,p.bot,PW+8,22);
      ctx.shadowBlur=0;
    });
    ctx.save();ctx.translate(bx,by2);ctx.rotate(Math.min(Math.max(bv*0.07,-0.5),0.85));
    ctx.fillStyle='#ffd700';ctx.shadowColor='#ffd700';ctx.shadowBlur=10;
    ctx.beginPath();ctx.ellipse(0,0,br,br-2,0,0,Math.PI*2);ctx.fill();
    ctx.fillStyle='#ff6600';ctx.shadowBlur=0;ctx.fillRect(br-3,-3,7,6);
    ctx.fillStyle='#111';ctx.beginPath();ctx.arc(br-1,-4,3,0,Math.PI*2);ctx.fill();
    ctx.restore();
    if(!started){ctx.fillStyle='rgba(0,245,255,.8)';ctx.font='14px Share Tech Mono,monospace';ctx.textAlign='center';ctx.fillText('CLICK OR SPACE TO START',W/2,H/2+55);}
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle='#ff006e';ctx.font='bold 26px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',W/2,H/2-10);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='12px Share Tech Mono,monospace';ctx.fillText('Click to restart',W/2,H/2+28);}
  }
  cv.focus();setInterval(()=>{update();draw();},1000/60);
}
 
// ═══════════════════════════════════════════════════════════
// GAME 7 — MINESWEEPER
// ═══════════════════════════════════════════════════════════
function playMinesweeper(con){
  const C=12,R=10,MINES=18,CS=34;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">FLAGS: <span id="msF">0</span>/${MINES} &nbsp;|&nbsp; <span id="msSt">Click to start</span></div>
    <canvas id="msC" width="${C*CS}" height="${R*CS}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;cursor:pointer;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Left click = reveal &nbsp; Right click = flag</div>
  </div>`;
  const cv=document.getElementById('msC'),ctx=cv.getContext('2d');
  let board,rev,flagged,over,won,first;
  function init(){board=Array.from({length:R},()=>Array(C).fill(0));rev=Array.from({length:R},()=>Array(C).fill(false));flagged=Array.from({length:R},()=>Array(C).fill(false));over=false;won=false;first=true;document.getElementById('msF').textContent=0;document.getElementById('msSt').textContent='Click to start';draw();}
  function plant(sr,sc2){let n=0;while(n<MINES){const r=~~(Math.random()*R),c=~~(Math.random()*C);if(!board[r][c]&&!(r===sr&&c===sc2)){board[r][c]=-1;n++;}}for(let r=0;r<R;r++)for(let c=0;c<C;c++){if(board[r][c]===-1)continue;let cnt=0;for(let dr=-1;dr<=1;dr++)for(let dc=-1;dc<=1;dc++){const nr=r+dr,nc=c+dc;if(nr>=0&&nr<R&&nc>=0&&nc<C&&board[nr][nc]===-1)cnt++;}board[r][c]=cnt;}}
  function reveal(r,c){if(r<0||r>=R||c<0||c>=C||rev[r][c]||flagged[r][c])return;rev[r][c]=true;if(board[r][c]===0)for(let dr=-1;dr<=1;dr++)for(let dc=-1;dc<=1;dc++)reveal(r+dr,c+dc);}
  const NC=['','#00f5ff','#00dd44','#ff006e','#0044ff','#ff4400','#00ccaa','#ffffff','#888'];
  function draw(){
    for(let r=0;r<R;r++)for(let c=0;c<C;c++){
      const x=c*CS,y=r*CS;
      if(rev[r][c]){
        ctx.fillStyle=(r+c)%2===0?'#0d1a0d':'#0a1508';ctx.fillRect(x,y,CS,CS);
        if(board[r][c]===-1){ctx.fillStyle='#ff006e';ctx.fillRect(x,y,CS,CS);ctx.font='20px monospace';ctx.textAlign='center';ctx.fillText('💣',x+CS/2,y+CS/2+7);}
        else if(board[r][c]>0){ctx.fillStyle=NC[board[r][c]];ctx.font='bold 15px Share Tech Mono,monospace';ctx.textAlign='center';ctx.fillText(board[r][c],x+CS/2,y+CS/2+6);}
      } else {
        ctx.fillStyle=(r+c)%2===0?'#1a2a3a':'#152230';ctx.fillRect(x,y,CS,CS);
        ctx.strokeStyle='rgba(0,245,255,.1)';ctx.strokeRect(x+.5,y+.5,CS-1,CS-1);
        if(flagged[r][c]){ctx.font='18px monospace';ctx.textAlign='center';ctx.fillText('🚩',x+CS/2,y+CS/2+7);}
      }
    }
  }
  cv.addEventListener('click',e=>{
    if(over)return;
    const rect=cv.getBoundingClientRect();
    const c=~~((e.clientX-rect.left)/CS),r=~~((e.clientY-rect.top)/CS);
    if(r<0||r>=R||c<0||c>=C||rev[r][c]||flagged[r][c])return;
    if(first){plant(r,c);first=false;}
    if(board[r][c]===-1){rev[r][c]=true;over=true;document.getElementById('msSt').textContent='💥 BOOM! Right-click = New Game';}
    else{reveal(r,c);const left=rev.flat().filter(v=>!v).length;if(left===MINES){won=true;over=true;document.getElementById('msSt').textContent='🏆 YOU WIN!';}}
    draw();
  });
  cv.addEventListener('contextmenu',e=>{
    e.preventDefault();
    if(over){init();return;}
    const rect=cv.getBoundingClientRect();
    const c=~~((e.clientX-rect.left)/CS),r=~~((e.clientY-rect.top)/CS);
    if(r<0||r>=R||c<0||c>=C||rev[r][c])return;
    flagged[r][c]=!flagged[r][c];document.getElementById('msF').textContent=flagged.flat().filter(v=>v).length;draw();
  });
  init();cv.focus();
}
 
// ═══════════════════════════════════════════════════════════
// GAME 8 — 2048
// ═══════════════════════════════════════════════════════════
function play2048(con){
  const N=4,CS=92;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="t8S">0</span> &nbsp;|&nbsp; BEST: <span id="t8B">0</span></div>
    <canvas id="t8C" width="${N*CS+8}" height="${N*CS+8}" style="border:1px solid rgba(0,245,255,.3);border-radius:6px;background:#0a0a1a;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Arrow keys to merge tiles &nbsp; R to restart</div>
  </div>`;
  const cv=document.getElementById('t8C'),ctx=cv.getContext('2d');
  const TC={0:'#1a1a2e',2:'#162032',4:'#1a2a3a',8:'#0d4a4a',16:'#0d5a3a',32:'#1a4a0d',64:'#4a2a0d',128:'#4a3a0d',256:'#4a0d2a',512:'#2a0d4a',1024:'#0d2a4a',2048:'#0d0d4a'};
  const TC2={0:'#334',2:'#8af',4:'#6cf',8:'#0ef',16:'#0fa',32:'#8f2',64:'#fa2',128:'#f82',256:'#f2a',512:'#a2f',1024:'#2af',2048:'#fff'};
  let board,sc,best=0,over;
  function init(){board=Array.from({length:N},()=>Array(N).fill(0));sc=0;over=false;add();add();draw();}
  function add(){const e=[];for(let r=0;r<N;r++)for(let c=0;c<N;c++)if(!board[r][c])e.push([r,c]);if(!e.length)return;const[r,c]=e[~~(Math.random()*e.length)];board[r][c]=Math.random()<0.9?2:4;}
  function slide(row){const f=row.filter(v=>v);const m=[];let i=0;while(i<f.length){if(i+1<f.length&&f[i]===f[i+1]){m.push(f[i]*2);sc+=f[i]*2;i+=2;}else{m.push(f[i]);i++;}}while(m.length<N)m.push(0);return m;}
  function move(d){
    const prev=JSON.stringify(board);
    if(d==='left')board=board.map(r=>slide(r));
    else if(d==='right')board=board.map(r=>slide([...r].reverse()).reverse());
    else if(d==='up'){for(let c=0;c<N;c++){const col=board.map(r=>r[c]);const s=slide(col);s.forEach((v,r)=>board[r][c]=v);}}
    else if(d==='down'){for(let c=0;c<N;c++){const col=board.map(r=>r[c]).reverse();const s=slide(col).reverse();s.forEach((v,r)=>board[r][c]=v);}}
    if(JSON.stringify(board)!==prev){add();best=Math.max(best,sc);document.getElementById('t8S').textContent=sc;document.getElementById('t8B').textContent=best;}
    let can=false;for(let r=0;r<N;r++)for(let c=0;c<N;c++){if(!board[r][c])can=true;if(c<N-1&&board[r][c]===board[r][c+1])can=true;if(r<N-1&&board[r][c]===board[r+1][c])can=true;}
    if(!can)over=true;draw();
  }
  function draw(){
    const TW=N*CS+8;ctx.fillStyle='#0a0a1a';ctx.fillRect(0,0,TW,TW);
    for(let r=0;r<N;r++)for(let c=0;c<N;c++){
      const v=board[r][c],x=4+c*CS,y=4+r*CS,k=Math.min(v,2048);
      ctx.fillStyle=TC[k]||'#060030';ctx.beginPath();ctx.roundRect?ctx.roundRect(x,y,CS-4,CS-4,6):null;ctx.fill();
      if(!ctx.roundRect)ctx.fillRect(x,y,CS-4,CS-4);
      if(v){const fs=v<100?26:v<1000?20:15;ctx.fillStyle=TC2[k]||'#fff';ctx.font=`bold ${fs}px Orbitron,monospace`;ctx.textAlign='center';ctx.fillText(v,x+(CS-4)/2,y+(CS-4)/2+fs/3);}
    }
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,TW,TW);ctx.fillStyle='#ff006e';ctx.font='bold 22px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',TW/2,TW/2-8);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('R to restart',TW/2,TW/2+24);}
  }
  function kh(e){
    if((e.key==='r'||e.key==='R')){init();return;}
    if(over)return;
    const m={ArrowLeft:'left',ArrowRight:'right',ArrowUp:'up',ArrowDown:'down'};
    if(m[e.key]){move(m[e.key]);e.preventDefault();}
  }
  document.addEventListener('keydown',kh);init();cv.focus();
}
 
// ═══════════════════════════════════════════════════════════
// GAME 9 — ASTEROIDS
// ═══════════════════════════════════════════════════════════
function playAsteroids(con){
  const W=500,H=380;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="astS">0</span> &nbsp;|&nbsp; LIVES: <span id="astL">3</span></div>
    <canvas id="astC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">← → turn &nbsp; ↑ thrust &nbsp; SPACE shoot &nbsp; SPACE restart</div>
  </div>`;
  const cv=document.getElementById('astC'),ctx=cv.getContext('2d');
  let ship,bullets,asteroids,sc,lives,over,keys={},lastShot=0,inv=0;
  function mkAst(n){return Array.from({length:n},()=>{const a=Math.random()*Math.PI*2,r=Math.random()*22+18;const side=Math.floor(Math.random()*4);let x,y;if(side===0)x=Math.random()*W,y=0;else if(side===1)x=W,y=Math.random()*H;else if(side===2)x=Math.random()*W,y=H;else x=0,y=Math.random()*H;return{x,y,vx:Math.cos(a)*1.4,vy:Math.sin(a)*1.4,r,pts:~~(Math.random()*6)+5};});}
  function init(){ship={x:W/2,y:H/2,a:-Math.PI/2,vx:0,vy:0};bullets=[];asteroids=mkAst(5);sc=0;lives=3;over=false;inv=0;}
  function kh(e){keys[e.key]=e.type==='keydown';if(e.key===' ')e.preventDefault();if(e.key===' '&&over&&e.type==='keydown')init();}
  document.addEventListener('keydown',kh);document.addEventListener('keyup',kh);
  function update(){
    if(over)return;
    if(keys['ArrowLeft'])ship.a-=0.07;if(keys['ArrowRight'])ship.a+=0.07;
    if(keys['ArrowUp']){ship.vx+=Math.cos(ship.a)*0.22;ship.vy+=Math.sin(ship.a)*0.22;}
    ship.vx*=0.985;ship.vy*=0.985;ship.x=(ship.x+ship.vx+W)%W;ship.y=(ship.y+ship.vy+H)%H;
    const now=Date.now();
    if(keys[' ']&&now-lastShot>240){bullets.push({x:ship.x+Math.cos(ship.a)*16,y:ship.y+Math.sin(ship.a)*16,vx:Math.cos(ship.a)*9,vy:Math.sin(ship.a)*9,life:52});lastShot=now;}
    bullets=bullets.filter(b=>{b.x=(b.x+b.vx+W)%W;b.y=(b.y+b.vy+H)%H;return --b.life>0;});
    asteroids.forEach(a=>{a.x=(a.x+a.vx+W)%W;a.y=(a.y+a.vy+H)%H;});
    if(inv>0)inv--;
    if(!inv){asteroids.forEach(a=>{const dx=ship.x-a.x,dy=ship.y-a.y;if(Math.sqrt(dx*dx+dy*dy)<a.r+10){lives--;document.getElementById('astL').textContent=lives;if(lives<=0){over=true;}else{ship.x=W/2;ship.y=H/2;ship.vx=0;ship.vy=0;inv=110;}}});}
    const newA=[];
    bullets.forEach(b=>{asteroids.forEach(a=>{if(a.r<1)return;const dx=b.x-a.x,dy=b.y-a.y;if(Math.sqrt(dx*dx+dy*dy)<a.r){b.life=0;sc+=~~(100/a.r);document.getElementById('astS').textContent=sc;if(a.r>14){for(let i=0;i<2;i++){const ag=Math.random()*Math.PI*2;newA.push({x:a.x,y:a.y,vx:Math.cos(ag)*2,vy:Math.sin(ag)*2,r:a.r*.55,pts:a.pts});}}a.r=0;}});});
    asteroids=[...asteroids.filter(a=>a.r>4),...newA];
    if(!asteroids.length)asteroids=mkAst(6);
  }
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    [[45,18],[110,52],[205,28],[325,55],[425,16],[475,72],[155,88],[265,75]].forEach(([x,y])=>{ctx.fillStyle='rgba(255,255,255,.45)';ctx.fillRect(x,y,1,1);});
    asteroids.forEach(a=>{if(a.r<1)return;ctx.strokeStyle='rgba(0,245,255,.7)';ctx.lineWidth=1.5;ctx.shadowColor='rgba(0,245,255,.35)';ctx.shadowBlur=5;ctx.beginPath();for(let i=0;i<a.pts;i++){const ag=i/a.pts*Math.PI*2,r2=a.r*(0.78+Math.sin(i*2.3)*0.22);i===0?ctx.moveTo(a.x+Math.cos(ag)*r2,a.y+Math.sin(ag)*r2):ctx.lineTo(a.x+Math.cos(ag)*r2,a.y+Math.sin(ag)*r2);}ctx.closePath();ctx.stroke();ctx.shadowBlur=0;});
    bullets.forEach(b=>{ctx.fillStyle='#fff';ctx.shadowColor='#fff';ctx.shadowBlur=8;ctx.beginPath();ctx.arc(b.x,b.y,2,0,Math.PI*2);ctx.fill();ctx.shadowBlur=0;});
    if(!(inv>0&&~~(inv/5)%2)){
      ctx.save();ctx.translate(ship.x,ship.y);ctx.rotate(ship.a);
      ctx.strokeStyle='#00f5ff';ctx.lineWidth=2;ctx.shadowColor='#00f5ff';ctx.shadowBlur=10;
      ctx.beginPath();ctx.moveTo(16,0);ctx.lineTo(-10,8);ctx.lineTo(-6,0);ctx.lineTo(-10,-8);ctx.closePath();ctx.stroke();
      if(keys['ArrowUp']){ctx.fillStyle='#ff4400';ctx.beginPath();ctx.moveTo(-6,0);ctx.lineTo(-15,4);ctx.lineTo(-15,-4);ctx.fill();}
      ctx.shadowBlur=0;ctx.restore();
    }
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle='#ff006e';ctx.font='bold 26px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',W/2,H/2-15);ctx.fillStyle='#00f5ff';ctx.font='13px Share Tech Mono,monospace';ctx.fillText('Score: '+sc,W/2,H/2+10);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('SPACE to restart',W/2,H/2+34);}
  }
  init();cv.focus();setInterval(()=>{update();draw();},1000/60);
}
 
// ═══════════════════════════════════════════════════════════
// GAME 10 — MEMORY MATCH
// ═══════════════════════════════════════════════════════════
function playMemory(con){
  const EM=['🎮','⚡','🔥','💎','🚀','🌟','🎯','💣','🏆','🎲','🧩','💀'];
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">PAIRS: <span id="mmP">0</span>/12 &nbsp;|&nbsp; MOVES: <span id="mmM">0</span></div>
    <div id="mmG" style="display:grid;grid-template-columns:repeat(6,58px);gap:6px;"></div>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Click cards to find matching pairs</div>
  </div>`;
  let cards=[...EM,...EM].sort(()=>Math.random()-.5);
  let flipped=[],matched=new Set(),moves=0,locked=false;
  function render(){
    const g=document.getElementById('mmG');if(!g)return;
    g.innerHTML=cards.map((e,i)=>`<div onclick="window._mm(${i})" style="width:58px;height:58px;background:${matched.has(i)||flipped.includes(i)?'#0d2a3a':'#0d1128'};border:1px solid ${matched.has(i)?'rgba(0,245,255,.6)':flipped.includes(i)?'rgba(0,245,255,.35)':'rgba(0,245,255,.12)'};border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:1.5rem;cursor:pointer;transition:all .15s;box-shadow:${matched.has(i)?'0 0 12px rgba(0,245,255,.3)':'none'}">${matched.has(i)||flipped.includes(i)?e:''}</div>`).join('');
  }
  window._mm=function(i){
    if(locked||flipped.includes(i)||matched.has(i))return;
    flipped.push(i);render();
    if(flipped.length===2){
      moves++;document.getElementById('mmM').textContent=moves;locked=true;
      if(cards[flipped[0]]===cards[flipped[1]]){matched.add(flipped[0]);matched.add(flipped[1]);document.getElementById('mmP').textContent=matched.size/2;flipped=[];locked=false;render();}
      else setTimeout(()=>{flipped=[];locked=false;render();},850);
    }
  };
  render();
}
 
// ═══════════════════════════════════════════════════════════
// GAME 11 — TOWER STACK
// ═══════════════════════════════════════════════════════════
function playTowerStack(con){
  const W=320,H=440,BH=22;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="tsS">0</span> &nbsp;|&nbsp; BEST: <span id="tsB">0</span></div>
    <canvas id="tsC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block;cursor:pointer" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">Click or SPACE to place block &nbsp; Click after death to restart</div>
  </div>`;
  const cv=document.getElementById('tsC'),ctx=cv.getContext('2d');
  let stack,mov,sc,best=0,over,spd;
  function init(){stack=[{x:W/2-60,w:120,y:H-BH}];mov={x:-10,w:120,dir:1};sc=0;over=false;spd=3;draw();}
  function place(){
    if(over){init();return;}
    const top=stack[stack.length-1];
    const left=Math.max(mov.x,top.x),right=Math.min(mov.x+mov.w,top.x+top.w),ov=right-left;
    if(ov<=4){over=true;best=Math.max(best,sc);document.getElementById('tsB').textContent=best;draw();return;}
    stack.push({x:left,w:ov,y:top.y-BH});
    sc++;spd=Math.min(9,3+sc*.18);document.getElementById('tsS').textContent=sc;
    mov={x:Math.random()>.5?-130:W+10,w:ov,dir:Math.random()>.5?1:-1};
    if(stack[stack.length-1].y<H*.38)stack.forEach(s=>s.y+=BH*3);
    draw();
  }
  cv.addEventListener('click',place);
  function kh(e){if(e.key===' '){place();e.preventDefault();}}
  document.addEventListener('keydown',kh);
  const HS=[185,160,140,100,60,40,20,340,300];
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    stack.forEach((b,i)=>{const h=HS[i%HS.length];ctx.fillStyle=`hsl(${h},80%,33%)`;ctx.shadowColor=`hsl(${h},100%,58%)`;ctx.shadowBlur=8;ctx.fillRect(b.x,b.y,b.w,BH-2);ctx.fillStyle=`hsl(${h},80%,52%)`;ctx.fillRect(b.x,b.y,b.w,4);ctx.shadowBlur=0;});
    if(!over){ctx.fillStyle='rgba(0,245,255,.85)';ctx.shadowColor='#00f5ff';ctx.shadowBlur=10;ctx.fillRect(mov.x,35,mov.w,BH-2);ctx.shadowBlur=0;mov.x+=spd*mov.dir;if(mov.x+mov.w>W+10||mov.x<-10)mov.dir=-mov.dir;}
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle='#ff006e';ctx.font='bold 22px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',W/2,H/2-10);ctx.fillStyle='#00f5ff';ctx.font='13px Share Tech Mono,monospace';ctx.fillText('Score: '+sc,W/2,H/2+14);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('Click to restart',W/2,H/2+38);}
  }
  init();cv.focus();setInterval(()=>{if(!over)draw();},1000/60);
}
 
// ═══════════════════════════════════════════════════════════
// GAME 12 — DINO RUN
// ═══════════════════════════════════════════════════════════
function playDino(con){
  const W=500,H=220,GY=168,DX=60;
  con.innerHTML=`<div style="display:flex;flex-direction:column;align-items:center;gap:.6rem;padding:1.2rem 1rem">
    <div style="font-family:'Share Tech Mono',monospace;color:var(--accent);font-size:.8rem;letter-spacing:.1em">SCORE: <span id="dnS">0</span> &nbsp;|&nbsp; BEST: <span id="dnB">0</span></div>
    <canvas id="dnC" width="${W}" height="${H}" style="border:1px solid rgba(0,245,255,.3);border-radius:4px;background:#020510;display:block;cursor:pointer" tabindex="0"></canvas>
    <div style="font-family:'Share Tech Mono',monospace;color:var(--dim);font-size:.68rem">SPACE or Click to jump · Double jump allowed!</div>
  </div>`;
  const cv=document.getElementById('dnC'),ctx=cv.getContext('2d');
  let dy=0,dinoY=GY,sc=0,best=0,obs=[],frame=0,spd=3.5,over=false,started=false,jumps=0,leg=0;
  function jump(){if(!started)started=true;if(jumps<2){dy=-10;jumps++;}}
  function restart(){dinoY=GY;dy=0;obs=[];sc=0;frame=0;spd=3.5;over=false;started=false;jumps=0;document.getElementById('dnS').textContent=0;}
  cv.addEventListener('click',()=>over?restart():jump());
  function kh(e){if(e.key===' '){over?restart():jump();e.preventDefault();}}
  document.addEventListener('keydown',kh);
  function update(){
    if(!started||over)return;
    dy+=0.6;dinoY=Math.min(GY,dinoY+dy);
    if(dinoY>=GY)jumps=0;
    frame++;leg=~~(frame/8)%2;spd=3.5+sc/600;
    if(frame%~~(60/spd)===0)obs.push({x:W,h:Math.random()>.5?28:48,w:20});
    obs.forEach(o=>o.x-=spd);obs=obs.filter(o=>o.x>-30);
    sc++;best=Math.max(best,~~(sc/10));document.getElementById('dnS').textContent=~~(sc/10);document.getElementById('dnB').textContent=best;
    obs.forEach(o=>{if(DX+26>o.x&&DX<o.x+o.w&&dinoY+36>GY+5-o.h)over=true;});
  }
  function draw(){
    ctx.fillStyle='#020510';ctx.fillRect(0,0,W,H);
    ctx.fillStyle='rgba(0,245,255,.25)';ctx.fillRect(0,GY+36,W,2);
    // dino body
    ctx.fillStyle='#00f5ff';ctx.shadowColor='#00f5ff';ctx.shadowBlur=8;
    ctx.fillRect(DX,dinoY,26,34);ctx.fillRect(DX+10,dinoY-13,18,15);
    ctx.fillStyle='#111';ctx.fillRect(DX+22,dinoY-9,5,5);
    ctx.fillStyle='#ff6600';ctx.fillRect(DX+25,dinoY-6,6,5);
    if(dinoY>=GY-2){ctx.fillStyle='#00f5ff';if(leg===0){ctx.fillRect(DX+4,dinoY+34,8,12);ctx.fillRect(DX+15,dinoY+34,8,7);}else{ctx.fillRect(DX+4,dinoY+34,8,7);ctx.fillRect(DX+15,dinoY+34,8,12);}}
    ctx.shadowBlur=0;
    obs.forEach(o=>{ctx.fillStyle='#ff006e';ctx.shadowColor='#ff006e';ctx.shadowBlur=8;ctx.fillRect(o.x,GY+36-o.h,o.w,o.h);ctx.shadowBlur=0;});
    if(!started){ctx.fillStyle='rgba(0,245,255,.75)';ctx.font='13px Share Tech Mono,monospace';ctx.textAlign='center';ctx.fillText('SPACE OR CLICK TO START',W/2,H/2+40);}
    if(over){ctx.fillStyle='rgba(4,5,15,.82)';ctx.fillRect(0,0,W,H);ctx.fillStyle='#ff006e';ctx.font='bold 24px Orbitron,monospace';ctx.textAlign='center';ctx.fillText('GAME OVER',W/2,H/2-10);ctx.fillStyle='rgba(0,245,255,.5)';ctx.font='11px Share Tech Mono,monospace';ctx.fillText('Click or SPACE to restart',W/2,H/2+22);}
  }
  cv.focus();setInterval(()=>{update();draw();},1000/60);
}
 
// ─────────────────────────────────────────────
// BOOT
// ─────────────────────────────────────────────
renderGrid();
</script>
</body>
</html>
