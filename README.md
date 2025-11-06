<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>No siempre que llueve es un desastre natural 💌</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Baloo+2:wght@400;700;800&display=swap" rel="stylesheet">

<style>
:root{
  --rose:#ff69b4; --lav:#ab49cc; --sig:#7f00b2; --gold:#f7c56b;
  --ink:#2a0f28; --panel:rgba(255,255,255,.86);
}
*{box-sizing:border-box;margin:0;padding:0}
html,body{height:100%}
body{font-family:"Baloo 2",system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Cantarell,sans-serif;background:#0b0810;color:#fff;overflow:hidden}

.bg{position:fixed;inset:0;z-index:0;pointer-events:none}
.bg::before{content:"";position:absolute;inset:0;
  background:url('photo_4900317553574480829_y.jpg') center/cover no-repeat;
  filter:blur(8px) brightness(1.04) saturate(1.05)}

.rain{position:fixed;inset:0;z-index:1;pointer-events:none}
.drop{position:fixed;top:-40px;left:0;opacity:0;transform:translate3d(var(--x),-40px,0) rotate(var(--r)) scale(var(--s,1));
  animation:fall var(--dur) linear forwards;font-size:var(--fs);
  filter:drop-shadow(0 6px 12px rgba(0,0,0,.18))}
@keyframes fall{0%{opacity:0}10%{opacity:1}80%{opacity:1}100%{transform:translate3d(var(--x),calc(100vh + 68px),0) rotate(var(--r)) scale(var(--s,1));opacity:0}}

.stage{position:relative;z-index:2;min-height:100vh;width:100vw;display:flex;flex-direction:column;justify-content:center;align-items:center;}

.banner{position:relative;top:0;left:50%;transform:translateX(-50%);
  font-weight:900;color:#fff;font-size:clamp(1rem,3.6vw,1.3rem);
  text-shadow:0 2px 8px rgba(0,0,0,.35),0 0 14px rgba(255,105,180,.55)}

.heart-wrap{display:flex;flex-direction:column;align-items:center;gap:14px;justify-content:center;}
.heart{position:relative;width:min(78vw,62vh);max-width:760px;aspect-ratio:1;
  filter:drop-shadow(0 10px 20px rgba(255,105,180,.40));margin:0 auto;transition:filter .3s;}
svg{display:block}
.outline{fill:none;stroke:var(--rose);stroke-width:3}
.level{fill:#ffc1dd;opacity:.58}
.base{fill:#ffd1e8;opacity:.16}
.bloom{opacity:0;animation:bl .28s ease forwards}
@keyframes bl{to{opacity:1}}
.progress{font-weight:900;font-size:clamp(1rem,3.6vw,1.05rem);color:#ffe8f3;
  text-shadow:0 0 10px rgba(255,105,180,.6),0 2px 6px rgba(0,0,0,.35)}

.controls{position:relative;left:50%;bottom:0;transform:translateX(-50%);display:flex;gap:12px;z-index:60}
.btn{
  position:relative; display:inline-flex; align-items:center; justify-content:center;
  min-width:min(280px,86vw); padding:14px 22px; border:none; border-radius:999px;
  font-weight:900; font-size:clamp(.95rem,4vw,1.05rem); color:#7a2c56;
  background:linear-gradient(180deg,#ffd7ec,#ffc3e3); box-shadow:0 8px 18px rgba(0,0,0,.20);
  cursor:pointer; user-select:none; touch-action:manipulation; outline:none;
  transition:transform .08s ease, box-shadow .2s ease, filter .2s ease;
}
.btn:hover{filter:brightness(1.04); box-shadow:0 12px 32px rgba(255,105,180,.25);}
.btn:active{transform:scale(.98)}
.btn:disabled{opacity:.55;cursor:not-allowed}
.btn .ink{position:absolute; width:0;height:0; border-radius:50%; pointer-events:none;
  background:rgba(255,255,255,.7); transform:translate(-50%,-50%);
  animation:ripple .6s ease-out forwards}
@keyframes ripple{0%{width:0;height:0;opacity:.6}100%{width:520px;height:520px;opacity:0}}
.pop-burst{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);
  width:0;height:0;border-radius:999px;pointer-events:none;opacity:.75;
  background:radial-gradient(circle,#fff 0 20%, rgba(255,105,180,.55) 21% 60%, transparent 61%);
  animation:burst .4s ease-out forwards}
@keyframes burst{from{width:0;height:0;opacity:.9}to{width:46%;height:46%;opacity:0}}
.msg4s{position:fixed;left:50%;top:50%;transform:translate(-50%,-50%);z-index:55;
  font-weight:900;font-size:clamp(1.2rem,6vw,2.2rem);text-align:center;color:#fff;
  text-shadow:0 3px 22px rgba(255,105,180,.9),0 2px 10px rgba(0,0,0,.45);opacity:0;transition:opacity .3s ease}
.msg4s.show{opacity:1}
.pulse{animation:pulse 1.1s cubic-bezier(.22,1,.36,1);filter:drop-shadow(0 0 32px #ff69b4);}
@keyframes pulse{0%{transform:scale(1)}30%{transform:scale(1.11)}50%{transform:scale(.95)}85%{transform:scale(1.08)}100%{transform:scale(1)}}

/* SOBRE + Carta + Destello igual que antes, para evitar repetidos, se mantiene igual que tu archivo */

// ... (mantén el resto del CSS igual que el original para .env-wrap, .envelope, .flapT, .letter, .letter-panel, etc.)

.flash{position:fixed;inset:0;pointer-events:none;z-index:40;opacity:0}
.flash.show{animation:flashIn 1.7s ease forwards}
@keyframes flashIn{0%{opacity:0}12%{opacity:1;background:radial-gradient(60% 60% at 50% 50%, rgba(255,105,180,.55), rgba(255,105,180,.22) 45%, rgba(255,105,180,0) 70%)}100%{opacity:0}

.audio-info{position:fixed;left:50%;bottom:56px;transform:translateX(-50%);
  width:300px;max-width:90vw;padding:10px 16px;border-radius:16px;
  font-weight:700;font-size:1.05rem;color:#fff;background:#7a2c567c;
  text-align:center;box-shadow:0 6px 20px rgba(255,105,180,.22);z-index:80;
  transition:opacity .2s;}
#playToggle{position:fixed;bottom:26px;right:24px;z-index:70;width:70px;height:70px;border-radius:50%;
  border:none;cursor:pointer;font-size:28px;background:radial-gradient(circle at 30% 30%, #ffbde3 0%, #ff69b4 60%, #ff2aa7 100%);
  color:white;box-shadow:0 0 20px rgba(255,105,180,.6);transition:transform .3s ease, box-shadow .3s ease}
#playToggle:hover{transform:scale(1.10); box-shadow:0 0 40px rgba(255,235,245,.9);}
#playToggle.anim{animation:btBlink 1.15s infinite;}
@keyframes btBlink{0%,100%{filter:none}50%{filter:brightness(1.18) drop-shadow(0 0 16px #fff)}}

@media (max-width:480px){
  .audio-info{ bottom:44px;}
  #playToggle{width:60px;height:60px;font-size:24px;bottom:18px;right:16px}
}
@media (max-width:360px){
  .controls{bottom:6vh}
  .title{letter-spacing:.2px}
  .sign img{width:70px;height:70px}
}
</style>
</head>
<body>
<div class="bg"></div>
<div class="rain" id="rain"></div>

<div class="stage">
  <div class="heart-wrap" id="heartStage">
    <div class="banner" id="banner">🌸 El primero floreció.</div>
    <div class="heart" id="heart">
      <svg viewBox="0 0 100 100" aria-hidden="true">
        <defs>
          <clipPath id="clipH"><path d="M50 86C50 86 9 61 9 36C9 23 20 12 33 12C41 12 47 16 50 22C53 16 59 12 67 12C80 12 91 23 91 36C91 61 50 86 50 86Z"/></clipPath>
        </defs>
        <g clip-path="url(#clipH)">
          <rect id="level" class="level" x="10" y="86" width="80" height="0"/>
          <rect id="base" class="base" x="10" y="12" width="80" height="74"/>
          <g id="rise"></g>
          <g id="fill"></g>
        </g>
        <path class="outline" d="M50 86C50 86 9 61 9 36C9 23 20 12 33 12C41 12 47 16 50 22C53 16 59 12 67 12C80 12 91 23 91 36C91 61 50 86 50 86Z"/>
      </svg>
      <div id="popBox"></div>
    </div>
    <div class="progress" id="progress">Tulipanes: 0/18</div>
    <div class="controls">
      <button class="btn" id="btnTulip" aria-label="Añadir tulipán" type="button">🌷 Haz florecer otro tulipán</button>
    </div>
  </div>
  <div class="msg4s" id="msg4s">Desde que llegaste, ya no hay espacio para nadie más.</div>
  <div class="env-wrap" id="envWrap" aria-hidden="true">
    <div class="envelope" id="env">
      <div class="env-body"></div>
      <div class="flapT" id="flapT"></div>
      <div class="ribbon" id="ribbon"></div>
      <div class="sheet" id="sheet"></div>
    </div>
  </div>
  <article class="letter" id="letter" aria-live="polite">
    <div class="letter-panel">
      <h2 class="title">No siempre que llueve es un desastre natural</h2>
      <p class="p" style="--d:.08s"><b>He pensado mucho en nosotras, en las veces que peleamos y en todo lo que pasa después. Sé que muchas veces eres tú quien da el primer paso, quien busca arreglar las cosas, y eso es algo que valoro mucho.</b></p>
      <p class="p" style="--d:.22s"><b>A veces necesito quedarme callada, pensar, ordenar todo lo que siento antes de hablar. No porque quiera alejarme, sino porque tengo miedo de decir algo sin pensarlo. Quiero que sepas que incluso en esos silencios te sigo queriendo igual.</b></p>
      <p class="p" style="--d:.36s"><b>No sabes cuántas veces me he quedado con las ganas de escribirte, de correr detrás de ti, pero termino frenándome porque no quiero que mis palabras salgan desordenadas.</b></p>
      <p class="p" style="--d:.50s"><b>Porque incluso en esos momentos donde parece que todo se rompe, yo sigo pensando en ti, sigo queriendo que estés bien, sigo queriéndote. Y aunque a veces no lo demuestre, eres la persona más importante para mí.</b></p>
      <div class="sign" id="sign">
        <span>te quiere con todo su corazón M</span>
        <img src="photo_4900317553574480831_y.jpg" alt="Nosotras">
      </div>
    </div>
  </article>
</div>
<div class="flash" id="flash"></div>
<!-- AUTO PLAY INFO & AUDIO CONTROLS -->
<div class="audio-info" id="audioInfo" style="opacity:0;pointer-events:none;">
  Toca el botón <b>▶️</b> para activar la música 🎶<br>
  Si no suena, asegúrate que el dispositivo tiene audio encendido y prueba de nuevo.
</div>
<audio id="song" preload="auto" loop>
  <source src="ssstik.io_1762269203857.mp3" type="audio/mpeg">
</audio>
<button id="playToggle" title="Reproducir/Pausar música">▶️</button>

<script>
/* ===== Lluvia ===== */
const rain=document.getElementById('rain');const EM=['🌷','🍦','💖','💗'];
function drop(){
  const d=document.createElement('div');
  d.className='drop';
  d.textContent=EM[Math.floor(Math.random()*EM.length)];
  d.style.setProperty('--x',Math.random()*innerWidth+'px');
  d.style.setProperty('--r',(Math.random()-0.5)*100+'deg'); // más rotación
  d.style.setProperty('--dur',(Math.random()*3+4).toFixed(2)+'s'); // velocidad variada
  d.style.setProperty('--fs',(Math.random()*10+18|0)+'px'); // tamaño más variado
  d.style.setProperty('--s',(0.7+Math.random()*1.2).toFixed(1)); // escala variada
  rain.appendChild(d);
  d.addEventListener('animationend',()=>d.remove())
}
setInterval(drop,280);for(let i=0;i<14;i++)drop();

/* ===== Corazón 18 clics ===== */
const btn=document.getElementById('btnTulip'),progress=document.getElementById('progress'),
      banner=document.getElementById('banner'),msg4s=document.getElementById('msg4s'),
      heart=document.getElementById('heart');
const level=document.getElementById('level'),base=document.getElementById('base'),
      rise=document.getElementById('rise'),fill=document.getElementById('fill'),
      popBox=document.getElementById('popBox');
let clicks=0,total=18,busy=false,done=false;
const msgs=["🌸 El primero floreció.","🌷 Otro más, por ti.","💞 Late más fuerte.","✨ Ya se siente el amor.","🌷 Cada clic es cariño.","💗 Qué bonito va quedando.","🌸 Se llena de tulipanes.","💖 Siempre crecen más por ti.",
"🪄 El corazón se alegra.","🌹 Esto es magia.","💫 ¡Increíble!","💗 ¿Notas el cambio?","🌷 Ya casi.","🌷 Últimos tulipanes.","❤️ Esto es por ti.","💞 Completo de amor.","🌸 Ya floreció todo.","🌷 ¡Completaste los 18!"];

function popSound(){try{const ac=new (window.AudioContext||window.webkitAudioContext)();
  const o=ac.createOscillator(),g=ac.createGain();
  o.type='sine';o.frequency.setValueAtTime(700,ac.currentTime);
  o.frequency.exponentialRampToValueAtTime(260,ac.currentTime+0.1);
  g.gain.setValueAtTime(0.016,ac.currentTime);
  g.gain.exponentialRampToValueAtTime(0.00002,ac.currentTime+0.14);
  o.connect(g).connect(ac.destination);o.start();o.stop(ac.currentTime+0.16);}catch(e){}}
function popVisual(){const b=document.createElement('div');b.className='pop-burst';popBox.appendChild(b);b.addEventListener('animationend',()=>b.remove())}

const placed=[];function d2(a,b){const dx=a.x-b.x,dy=a.y-b.y;return dx*dx+dy*dy}
function addTulip(x,y,s){const t=document.createElementNS('http://www.w3.org/2000/svg','text');t.setAttribute('x',x.toFixed(2));t.setAttribute('y',y.toFixed(2));t.setAttribute('font-size',s);t.textContent='🌷';t.setAttribute('class','bloom');fill.appendChild(t);}
function pack(n,minD=26){let tries=0,add=0;while(add<n&&tries<600){tries++;const x=12+Math.random()*76,y=16+Math.random()*64,p={x,y};let ok=true;for(const q of placed){if(d2(p,q)<minD){ok=false;break}}if(ok){placed.push(p);addTulip(x,y,(4.8+Math.random()*2));add++;}}}
function updateLevel(){const r=Math.min(clicks/total,1),H=74,h=H*r,y=86-h;level.setAttribute('y',y.toFixed(2));level.setAttribute('height',h.toFixed(2));base.setAttribute('opacity',(0.16+r*0.30).toFixed(2));}

function riser(){const x=18+Math.random()*64,y=70+Math.random()*4,s=5.4+Math.random()*2.2;const t=document.createElementNS('http://www.w3.org/2000/svg','text');t.setAttribute('x',x.toFixed(2));t.setAttribute('y',y.toFixed(2));t.setAttribute('font-size',s);t.textContent='🌷';t.setAttribute('class','bloom');rise.appendChild(t);}
function fillAll(){for(let gx=14;gx<=86;gx+=6){for(let gy=16;gy<=76;gy+=6){const dx=gx-50,dy=gy-56;if(dy<22||(dy*0.9+Math.abs(dx)*0.55)<38){placed.push({x:gx,y:gy});addTulip(gx,gy,5+Math.random()*2)}}}}

function advance(){
  if(busy||done)return; busy=true;
  clicks++; popSound(); popVisual();
  pack(5,26); for(let i=0;i<3;i++)riser(); updateLevel();
  progress.textContent=`Tulipanes: ${clicks}/${total}`;
  banner.textContent=msgs[Math.min(clicks-1,msgs.length-1)];
  heart.classList.add('pulse');
  setTimeout(()=>heart.classList.remove('pulse'),950);
  if(clicks===total){
    fillAll(); heart.classList.add('pulse'); btn.disabled=true; done=true;
    msg4s.classList.add('show'); setTimeout(()=>{msg4s.classList.remove('show'); showEnvelope();},4100);
  }
  setTimeout(()=>busy=false,130);
}

function ripple(e){
  const r=document.createElement('span');r.className='ink';
  const rect=btn.getBoundingClientRect();
  const cx=(e.clientX||(e.touches&&e.touches[0].clientX)||rect.left+rect.width/2)-rect.left;
  const cy=(e.clientY||(e.touches&&e.touches[0].clientY)||rect.top+rect.height/2)-rect.top;
  r.style.left=cx+'px'; r.style.top=cy+'px'; btn.appendChild(r);
  r.addEventListener('animationend',()=>r.remove());
}
function press(e){ if(btn.disabled||busy) return; ripple(e); advance(); }
btn.addEventListener('click',press);
btn.addEventListener('pointerdown',press);
btn.addEventListener('touchend',press,{passive:true});
btn.addEventListener('keydown',e=>{if(e.key==='Enter'||e.key===' '){e.preventDefault();press(e)}});

/* ===== SOBRE (épico) + explosiones + CARTA persistente ===== */
const envWrap=document.getElementById('envWrap'),env=document.getElementById('env'),
      flapT=document.getElementById('flapT'),ribbon=document.getElementById('ribbon'),
      sheet=document.getElementById('sheet'),flash=document.getElementById('flash'),
      letter=document.getElementById('letter'),heartStage=document.getElementById('heartStage');

function showEnvelope(){
  heartStage.style.display='none';
  envWrap.style.display='grid';
  requestAnimationFrame(()=>env.classList.add('show'));
  setTimeout(()=>ribbon.classList.add('draw'), 700);
  setTimeout(()=>{ribbon.classList.remove('draw'); explodeAt(innerWidth/2,innerHeight/2,140);}, 2000);
  setTimeout(()=>{env.animate([{transform:'translateY(0)'},{transform:'translateY(-6px)'},{transform:'translateY(0)'}],
                {duration:350,easing:'ease-in-out'});}, 2400);
  setTimeout(()=>{flapT.style.transform='rotateX(-178deg)';
    env.animate([{transform:'rotateZ(0deg)'},{transform:'rotateZ(-2deg)'},{transform:'rotateZ(0deg)'}],
                {duration:800,easing:'ease-in-out'});}, 2700);
  setTimeout(()=>{sheet.classList.add('show');}, 3400);
  setTimeout(()=>{envWrap.style.display='none'; showLetter();}, 4600);
  setTimeout(autoPlaySong, 1800); // Reproduce la música tras abrir el sobre
}

function explodeAt(cx,cy,count=90){
  flash.classList.add('show'); setTimeout(()=>flash.classList.remove('show'),1300);
  const sy=['🌷','💗','🍦','💖'];
  for(let i=0;i<count;i++){
    const s=document.createElement('div'); s.textContent=sy[i%sy.length];
    Object.assign(s.style,{position:'fixed',left:cx+'px',top:cy+'px',zIndex:45,
      fontSize:(18+Math.random()*16)+'px',opacity:1,
      transition:'transform 1.9s cubic-bezier(.22,1,.36,1), opacity 2s ease',
      filter:'drop-shadow(0 0 12px rgba(255,105,180,.85))'});
    document.body.appendChild(s);
    const a=Math.random()*2*Math.PI, d=124+Math.random()*260, r=(Math.random()*720-360);
    requestAnimationFrame(()=>{s.style.transform=`translate(${Math.cos(a)*d}px,${Math.sin(a)*d}px) rotate(${r}deg)`; s.style.opacity=0;});
    setTimeout(()=>s.remove(),1920);
  }
}

function showLetter(){
  letter.classList.add('show');
  document.querySelectorAll('.p').forEach(p=>p.classList.add('reveal'));
  document.getElementById('sign').classList.add('reveal');

  // Animación extra al aparecer la carta
  letter.animate([
    {transform:'translate(-50%,-50%) scale(.90) rotateX(14deg)', opacity:0},
    {transform:'translate(-50%,-50%) scale(1.06) rotateX(1deg)', opacity:1},
    {transform:'translate(-50%,-50%) scale(1) rotateX(0)', opacity:1}
  ], {
    duration: 1600,
    easing: 'cubic-bezier(.22,1,.36,1)',
    fill: 'forwards'
  });
  setTimeout(()=>{letter.style.opacity='1';letter.style.visibility='visible';letter.style.transform='translate(-50%,-50%) scale(1) rotateX(0)'},1500);
}

/* ===== Audio ===== */
const song=document.getElementById('song'),
      playToggle=document.getElementById('playToggle'),
      audioInfo=document.getElementById('audioInfo');
let playing=false;

// Parpadeo botón audio
playToggle.classList.add('anim');

// Mensaje inicial para activar el audio
window.addEventListener('DOMContentLoaded',()=>{
  audioInfo.innerHTML = 'Toca el botón <b>▶️</b> para activar la música 🎶<br>Si no suena, activa el audio en tu dispositivo y prueba de nuevo.';
  audioInfo.style.opacity = 1;
  audioInfo.style.pointerEvents = 'auto';
});

// Botón clásico
playToggle.addEventListener('click',()=>{
  if(!playing){
    song.play().then(()=>{
      playing=true;
      playToggle.textContent='⏸️';
      playToggle.style.boxShadow='0 0 34px rgba(255,255,255,.8),0 0 68px rgba(255,105,180,.8)';
      audioInfo.style.opacity=0;
      audioInfo.style.pointerEvents='none';
      playToggle.classList.remove('anim');
    }).catch((err)=>{
      audioInfo.innerHTML='Toca de nuevo o activa el sonido en tu navegador/dispositivo 🎶';
      audioInfo.style.opacity=1;
      audioInfo.style.pointerEvents='auto';
    });
  } else {
    song.pause();
    playing=false;
    playToggle.textContent='▶️';
    playToggle.style.boxShadow='0 0 20px rgba(255,105,180,.6)';
    audioInfo.innerHTML='Música pausada ⏸️';
    audioInfo.style.opacity=1;
    audioInfo.style.pointerEvents='auto';
    setTimeout(()=>audioInfo.style.opacity=0,1900);
    playToggle.classList.add('anim');
  }
});

song.addEventListener('pause', ()=>{
  playing=false;
  playToggle.textContent='▶️';
  playToggle.classList.add('anim');
});
song.addEventListener('play', ()=>{
  playing=true;
  playToggle.textContent='⏸️';
  playToggle.classList.remove('anim');
});

/* Intenta reproducir cuando se abra el sobre */
function autoPlaySong() {
  song.play().then(()=>{
    playing=true;
    playToggle.textContent='⏸️';
    playToggle.style.boxShadow='0 0 34px rgba(255,255,255,.8),0 0 68px rgba(255,105,180,.8)';
    audioInfo.style.opacity=0;
    audioInfo.style.pointerEvents='none';
    playToggle.classList.remove('anim');
  }).catch((err)=>{
    audioInfo.innerHTML='Toca el botón <b>▶️</b> arriba para activar la música 🎶<br>Si no suena, activa el audio en tu dispositivo y prueba de nuevo.';
    audioInfo.style.opacity=1;
    audioInfo.style.pointerEvents='auto';
    playToggle.classList.add('anim');
  });
}

/* ===== lluvia inicial extra ===== */
(function seedRain(){for(let i=0;i<13;i++)drop()})();
</script>
</body>
</html>
