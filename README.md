# 90s-Web-Simulator-
Simulates internet use in the 90s 
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>WELCOME TO MY 90s HOME PAGE!!!</title>
  <style>
    /* --- THEME TOKENS (switch with body[data-skin]) --- */
    :root{
      --bg:#0b114f; --ink:#ffffff; --accent:#00ffff; --chrome1:#efefef; --chrome2:#d7d7d7; --title1:#003399; --title2:#0066cc; --note:#111; --border:#b9b9b9;
    }
    body[data-skin="geocities"]{ --bg:#0b114f; --ink:#fff; --accent:#00ffff; --title1:#003399; --title2:#0066cc; }
    body[data-skin="angelfire"]{ --bg:#190018; --ink:#fff0f5; --accent:#ff66cc; --title1:#330033; --title2:#990066; }
    body[data-skin="corp98"]{ --bg:#1d2a30; --ink:#f2f2f2; --accent:#66ccff; --title1:#0f3b63; --title2:#2c6aa0; }/* --- 90s Aesthetic --- */
body {
  margin: 0; color: var(--ink);
  background: var(--bg) url('data:image/svg+xml;utf8,\
  <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64">\
    <rect width="64" height="64" fill="%23' + '0b114f' + '"/>\
    <circle cx="16" cy="16" r="2" fill="%23c6ff00" opacity="0.7"/>\
    <rect x="32" y="32" width="2" height="2" fill="%23ff00ff" opacity="0.7"/>\
    <circle cx="48" cy="12" r="2" fill="%2300ffff" opacity="0.7"/>\
    <rect x="8" y="40" width="2" height="2" fill="%23ff9900" opacity="0.7"/>\
  </svg>') repeat;
  font-family: "Comic Sans MS", "Trebuchet MS", Verdana, sans-serif;
  image-rendering: pixelated;
}
a { color: var(--accent); }
.container { max-width: 980px; margin: 0 auto; padding: 8px 10px 80px; }
.chrome { border: 3px ridge #c9c9c9; background: linear-gradient(var(--chrome1), var(--chrome2)); box-shadow: inset 0 0 0 2px #fff, 0 6px 24px rgba(0,0,0,0.5); color: #111; }
.titlebar { background: linear-gradient(var(--title1), var(--title2)); color:#fff; padding:6px 10px; font-weight:bold; text-shadow:0 1px 0 #000; display:flex; align-items:center; gap:8px; position:sticky; top:0; z-index:5; }
.btns{ margin-left:auto; display:flex; gap:6px; }
.btn{ width:14px; height:14px; border:2px outset #e2e2e2; background:#f3f3f3; }
.toolbar{ display:grid; grid-template-columns:auto 1fr auto auto; gap:8px; align-items:center; background:#ececec; padding:6px 8px; border-bottom:2px groove var(--border); color:#222; font-size:14px; }
.fake-url{ background:#fff; border:2px inset var(--border); padding:2px 6px; overflow:hidden; text-overflow:ellipsis; white-space:nowrap; }
.marquee{ background:#000; color:#0f0; border:2px inset #333; padding:4px 6px; margin:8px 8px 0; font-family:"Lucida Console", Monaco, monospace; }
.content{ padding:10px; }
.blink{ animation: blinky 1s steps(1) infinite; } @keyframes blinky{ 50%{opacity:0} }
.under-construction{ display:inline-flex; align-items:center; gap:8px; padding:6px 10px; background:#222; border:3px dashed #ff0; color:#ff0; }
.under-construction img{ width:24px; height:24px; image-rendering: pixelated; }
.window{ width:100%; max-width: 620px; margin:12px 8px; }
.window .body{ padding:10px; }
.progress-wrap{ background:#fff; border:2px inset var(--border); height:18px; position:relative; }
.progress{ position:absolute; left:0; top:0; bottom:0; width:0%; background: repeating-linear-gradient(45deg, #09f, #09f 10px, #7fd 10px, #7fd 20px); }
.progress-label{ font-family:"Lucida Console", monospace; font-size:12px; color:#111; padding-top:4px; }
.image-frame{ width:320px; height:240px; background:#000; border:4px groove var(--border); position:relative; overflow:hidden; }
.scanline{ position:absolute; left:0; right:0; height:0; background: linear-gradient(to bottom, rgba(0,255,0,0.25), rgba(0,0,0,0)); }
.image-final{ position:absolute; inset:0; display:none; object-fit: cover; }
.image-low{ position:absolute; inset:0; filter: blur(2px) contrast(120%); image-rendering: pixelated; }
.star{ position: fixed; width:6px; height:6px; pointer-events:none; background: radial-gradient(circle, #fff, rgba(255,255,255,0)); border-radius: 50%; opacity:0.9; }
.counter{ display:inline-block; padding:3px 6px; border:2px inset var(--border); background:#111; font-family:"Lucida Console", monospace; letter-spacing: 2px; color:#0f0; }
.row{ display:flex; flex-wrap:wrap; gap:12px; align-items:flex-start; }
.col{ flex:1 1 280px; }
.small{ font-size:12px; color:#222; }
.mono{ font-family:"Lucida Console", Monaco, monospace; }
.note{ background:#111; border-left: 4px solid var(--accent); padding: 8px; color:#ddd; }
.btn90{ border:3px outset #d6d6d6; background:#ececec; padding:6px 10px; cursor:pointer; font-weight:bold; }
.btn90:active{ border:3px inset #a9a9a9; }

/* FRAMES MODE */
#framesMode{ display:none; height:520px; border:4px ridge var(--border); background:#000; }
#framesNav{ width:180px; background:#111; color:#0f0; border-right:4px groove var(--border); overflow:auto; }
#framesMain{ flex:1; background:#001; color:#0f0; position:relative; }
#framesWrap{ display:flex; height:100%; }
.fake-iframe{ width:100%; height:100%; border:0; padding:12px; font-family:"Lucida Console", monospace; }

/* SPLASH */
#splash{ position:fixed; inset:0; background:radial-gradient(circle at 50% 40%, #111, #000 70%); display:flex; align-items:center; justify-content:center; z-index:99; color:#0f0; font-family:"Lucida Console", monospace; }
#splash .card{ border:4px ridge var(--border); background:#010; padding:18px; max-width: 560px; text-align:center; }

/* WEBRING */
.webring{ display:flex; gap:8px; align-items:center; padding:6px; background:#111; border:3px outset #333; font-family:"Lucida Console", monospace; color:#0f0; }
.webring button{ font-family:"Lucida Console", monospace; }

/* Download Manager */
#jobs{ display:grid; gap:10px; }
.job{ border:2px groove var(--border); padding:8px; background:#f6f6f6; color:#111; }

/* Guestbook */
#guestbook{ border:2px groove var(--border); padding:10px; background:#101; color:#0f0; font-family:"Lucida Console", monospace; }
.entry{ border-top:1px dashed #0f0; padding:6px 0; }

  </style>
</head>
<body data-skin="geocities">
  <!-- SPLASH PAGE -->
  <div id="splash">
    <div class="card">
      <h2>WELCOME TO ADRIAN'S HOME PAGE</h2>
      <p>Best viewed in <b>800x600</b> and <b>256 colors</b>. Do you agree?</p>
      <button class="btn90" onclick="dismissSplash()">YES, ENTER</button>
      <button class="btn90" onclick="alert('Please upgrade to 800x600 first.');">NO</button>
      <div style="margin-top:10px" class="webring">
        <span>◇ 90s WebRing ◇</span>
        <button onclick="ringPrev()">« Prev</button>
        <button onclick="ringRandom()">Random</button>
        <button onclick="ringNext()">Next »</button>
      </div>
      <div style="margin-top:10px">
        <label><input type="checkbox" id="autoplayMidi" checked> Enable background MIDI</label>
      </div>
    </div>
  </div>  <!-- AUDIO: MODEM + MIDI -->  <audio id="modem" preload="auto">
    <!-- super‑short 8kHz mono beep sweep approximating a screech; tiny placeholder -->
    <source src="data:audio/wav;base64,UklGRiQAAABXQVZFZm10IBAAAAABAAEAESsAACJWAAACABYAaW5mbyBoZXJl" type="audio/wav"/>
  </audio>
  <audio id="midi" loop>
    <!-- Browsers won't natively render .mid; we embed a tiny beep OGG as a nostalgic stand‑in -->
    <source src="data:audio/ogg;base64,T2dnUwACAAAAAAAAAABmZWFrbHkAAAAAABAAAAABAAACb2dnUwAAAA==" type="audio/ogg"/>
  </audio>  <div class="container chrome">
    <div class="titlebar">
      <span>✦ NetScape-ish Navigator 3.14</span>
      <div class="btns"><div class="btn" title="Minimize"></div><div class="btn" title="Maximize"></div><div class="btn" title="Close"></div></div>
    </div><div class="toolbar">
  <div>
    <button class="btn90" onclick="simulateDial()">Dial‑Up</button>
    <button class="btn90" onclick="simulatePageLoad()">Reload</button>
    <button class="btn90" onclick="toggleFrames()">Frames Mode</button>
    <button class="btn90" onclick="openGuestbook()">Guestbook</button>
  </div>
  <div class="fake-url mono" id="urlbar">http://www.geocities.com/~YourCoolPage/index.html</div>
  <div class="small mono">
    <label><input type="checkbox" id="modemFx" checked> Modem Screech</label>
  </div>
  <div>
    <select id="skin" onchange="setSkin(this.value)" class="btn90">
      <option value="geocities">GeoCities</option>
      <option value="angelfire">Angelfire</option>
      <option value="corp98">Corporate 98</option>
    </select>
  </div>
</div>

<div class="marquee"><marquee scrollamount="3">WELCOME TO MY HOME PAGE!!! Best viewed in 800x600 with 256 colors. Sign my guestbook!!! ✨</marquee></div>

<div class="content">
  <h1><span class="blink">★</span> Adrian's RAD 90s Page <span class="blink">★</span></h1>
  <p>Greetings, web traveler! Please be patient: our hamster‑powered servers are <i>very</i> busy.</p>

  <div class="row">
    <!-- Progressive image column -->
    <div class="col">
      <h3>Progressive Image Loading</h3>
      <div class="image-frame" id="imageFrame">
        <img class="image-low" id="imageLow" alt="Low‑res preview" src="data:image/svg+xml;utf8,\
          <svg xmlns='http://www.w3.org/2000/svg' width='160' height='120'>\
            <rect width='160' height='120' fill='%23002244'/>\
            <text x='50%' y='50%' dominant-baseline='middle' text-anchor='middle' fill='%23c6ff00' font-family='Verdana' font-size='12'>LO‑RES</text>\
          </svg>" />
        <img class="image-final" id="imageFinal" alt="Crisp final" src="data:image/svg+xml;utf8,\
          <svg xmlns='http://www.w3.org/2000/svg' width='640' height='480'>\
            <defs>\
              <linearGradient id='g' x1='0' x2='1'>\
                <stop offset='0' stop-color='%2300ffff'/>\
                <stop offset='1' stop-color='%23ff00ff'/>\
              </linearGradient>\
            </defs>\
            <rect width='640' height='480' fill='url(%23g)'/>\
            <circle cx='320' cy='240' r='160' fill='rgba(0,0,0,0.35)'/>\
            <text x='50%' y='50%' dominant-baseline='middle' text-anchor='middle' fill='white' font-family='Verdana' font-size='36'>SO CRISP</text>\
          </svg>" />
        <div class="scanline" id="scanline"></div>
      </div>
      <p class="small mono">Tip: Click <b>Reload</b> to watch it draw line‑by‑line again.</p>

      <div class="under-construction" style="margin-top:10px;">
        <img alt="Under Construction" src="data:image/gif;base64,R0lGODlhGQAZAPcAAAAAAP///wAAAP///wAAACH5BAEAAAEALAAAAAAZABkAAAj+APcJHEpZyR4AOQAA"/>
        <div><b>UNDER CONSTRUCTION!</b> Check back hourly for surprises.</div>
      </div>
    </div>

    <!-- Download manager column -->
    <div class="col">
      <h3>Download Manager (Parallel)</h3>
      <div class="window chrome">
        <div class="titlebar">File Downloads — Win98 Style<div class="btns"><div class="btn"></div><div class="btn"></div><div class="btn"></div></div></div>
        <div class="body">
          <div class="row" style="align-items:center">
            <label>Connection:&nbsp;
              <select id="globalSpeed">
                <option value="14400">14.4k</option>
                <option value="28800">28.8k</option>
                <option value="33600">33.6k</option>
                <option value="56000" selected>56k</option>
                <option value="64000">ISDN 64k</option>
                <option value="128000">ISDN 128k</option>
              </select>
            </label>
            <button class="btn90" onclick="addJob('MySong.mp3', 3584)">Add MP3 (3.5MB)</button>
            <button class="btn90" onclick="addJob('Wallpaper.jpg', 1024)">Add JPEG (1MB)</button>
            <button class="btn90" onclick="addJob('Shareware.zip', 5120)">Add ZIP (5MB)</button>
          </div>
          <div id="jobs"></div>
          <div class="note small">Parallel downloads share bandwidth like old browsers (roughly equal split).</div>
        </div>
      </div>

      <!-- WebRing -->
      <div class="webring" style="margin-top:10px">
        <span>◇ 90s WebRing ◇</span>
        <button onclick="ringPrev()">« Prev</button>
        <button onclick="ringRandom()">Random</button>
        <button onclick="ringNext()">Next »</button>
      </div>
    </div>
  </div>

  <h3>Frames Mode (Fake)</h3>
  <div id="framesMode" class="chrome">
    <div id="framesWrap">
      <div id="framesNav" class="fake-iframe">
        <b>Navigation</b><br>
        <a href="#" onclick="framesGoto('welcome')">Welcome</a><br>
        <a href="#" onclick="framesGoto('links')">Cool Links</a><br>
        <a href="#" onclick="framesGoto('pics')">PIX</a><br>
        <a href="#" onclick="framesGoto('music')">MP3z</a><br>
      </div>
      <div id="framesMain" class="fake-iframe">
        <div id="framesContent">[Click a link on the left. Loading will be… leisurely.]</div>
      </div>
    </div>
  </div>

  <h3>Guestbook (CGI‑style)</h3>
  <div id="guestbook">
    <form onsubmit="return submitGuestbook(event)">
      Name: <input id="gbName" required /> &nbsp; Message: <input id="gbMsg" required style="width:50%"/>
      <button class="btn90" type="submit">Sign</button>
    </form>
    <div id="gbStatus" style="margin:6px 0"></div>
    <div id="gbEntries"></div>
  </div>

  <h3>Site Map</h3>
  <ul>
    <li><a href="#" onclick="fakeNav('music.html')">My MP3z</a></li>
    <li><a href="#" onclick="fakeNav('pics.html')">PIX</a></li>
    <li><a href="#" onclick="fakeNav('links.html')">Cool Links</a></li>
  </ul>

  <div class="note">
    <b>Pro Tip:</b> Hit <em>Dial‑Up</em> first — you'll get a connection sequence, optional modem screech, and deliberate slowdown.
  </div>

  <hr/>
  <p class="mono small">Email: <a href="mailto:adrian_the_real_1997@aol.com">adrian_the_real_1997@aol.com</a></p>
</div>

<div class="titlebar" style="position: sticky; bottom: 0; top:auto;">
  <span>Visitor Counter:</span> <span class="counter" id="counter">0000420</span>
  <div class="btns" style="margin-left:auto">
    <div class="small mono">© 1997‑2001 Adrian's Page • Best viewed in Netscape 3.0 or IE4</div>
  </div>
</div>

  </div>  <script>
    // THEME
    function setSkin(val){ document.body.setAttribute('data-skin', val); }

    // SPLASH
    function dismissSplash(){
      document.getElementById('splash').style.display='none';
      if(document.getElementById('autoplayMidi').checked){
        const m=document.getElementById('midi'); m.volume=0.15; m.play().catch(()=>{});
      }
    }

    // Cursor sparkle
    (function(){ const stars=[]; window.addEventListener('mousemove',e=>{ const s=document.createElement('div'); s.className='star'; s.style.left=(e.clientX+(Math.random()*6-3))+'px'; s.style.top=(e.clientY+(Math.random()*6-3))+'px'; document.body.appendChild(s); stars.push({el:s,t:0}); }); function loop(){ for(let i=0;i<stars.length;i++){ stars[i].t+=0.03; stars[i].el.style.transform=`translateY(${stars[i].t*10}px) scale(${1-stars[i].t/2})`; stars[i].el.style.opacity=String(0.9-stars[i].t); if(stars[i].t>0.9){ stars[i].el.remove(); stars.splice(i,1); i--; } } requestAnimationFrame(loop);} loop(); })();

    // Dial-up
    let dialed=false;
    function simulateDial(){
      if(dialed){ alert('Already connected at blistering 56k!'); return; }
      const steps=['Initializing modem…','Dialing: 555‑CONNECT…','Negotiating… (v.90)','Authenticating…','Assigning IP (10.0.0.199)…','Connected at 49,333 bps.'];
      let i=0; const itv=setInterval(()=>{ document.getElementById('urlbar').textContent='dialup:// '+steps[i]; i++; if(i>=steps.length){ clearInterval(itv); dialed=true; document.getElementById('urlbar').textContent='http://www.geocities.com/~YourCoolPage/index.html — CONNECTED'; simulatePageLoad(); } },900);
      if(document.getElementById('modemFx').checked){ const a=document.getElementById('modem'); a.volume=0.5; a.currentTime=0; a.play().catch(()=>{}); }
    }

    // Progressive image draw
    function simulatePageLoad(){ const frame=document.getElementById('imageFrame'), scan=document.getElementById('scanline'), low=document.getElementById('imageLow'), hi=document.getElementById('imageFinal'); scan.style.height='0px'; hi.style.display='none'; low.style.display='block'; const total=frame.clientHeight; let h=0; const base=dialed?14:6; const timer=setInterval(()=>{ h+=4; scan.style.height=h+'px'; if(h>=total){ clearInterval(timer); low.style.display='none'; hi.style.display='block'; } }, base); }

    // Fake navigation delays
    function fakeNav(path){ document.getElementById('urlbar').textContent='Loading '+path+'…'; setTimeout(()=>{ alert(`${path} could not be displayed because your plugin is out of date. Please install Shockwave.`); document.getElementById('urlbar').textContent='http://www.geocities.com/~YourCoolPage/index.html'; }, dialed?3000:1200); }

    // Visitor counter
    (function(){ const el=document.getElementById('counter'); let n=parseInt(el.textContent,10)||123; setInterval(()=>{ n++; el.textContent=(''+n).padStart(7,'0'); },4000); })();

    // Frames mode
    function toggleFrames(){ const fm=document.getElementById('framesMode'); fm.style.display = fm.style.display==='none' || fm.style.display==='' ? 'block':'none'; }
    function framesGoto(id){ const c=document.getElementById('framesContent'); c.textContent='Loading '+id+'…'; const delay=dialed?2400:900; setTimeout(()=>{ if(id==='links'){ c.innerHTML='<b>Cool Links</b><br>1) <i>Under Construction</i><br>2) Best Free Cursor Trails<br>3) The MIDI Hall of Fame'; } else if(id==='pics'){ c.innerHTML='<b>PIX</b><br>[Progressive JPEGs arriving…]'; } else if(id==='music'){ c.innerHTML='<b>MP3z</b><br>Winamp skins and tracker tunes ahead.'; } else { c.innerHTML='<b>Welcome</b><br>“Frames!” because we could.'; } }, delay); }

    // Guestbook with CGI-ish delay
    function submitGuestbook(e){ e.preventDefault(); const name=document.getElementById('gbName').value.trim(); const msg=document.getElementById('gbMsg').value.trim(); if(!name||!msg) return false; const s=document.getElementById('gbStatus'); s.textContent='Submitting to /cgi-bin/guestbook.pl …'; setTimeout(()=>{ const arr=JSON.parse(localStorage.getItem('gbEntries')||'[]'); const now=new Date(); arr.unshift({name, msg, t: now.toISOString()}); localStorage.setItem('gbEntries', JSON.stringify(arr)); s.textContent='Thanks! Your entry will appear after moderator review (jk, it is live).'; renderGuestbook(); }, dialed?2200:800); return false; }
    function renderGuestbook(){ const box=document.getElementById('gbEntries'); const arr=JSON.parse(localStorage.getItem('gbEntries')||'[]'); box.innerHTML=arr.map(e=>`<div class="entry"><b>${escapeHtml(e.name)}</b> — <i>${new Date(e.t).toLocaleString()}</i><br>${escapeHtml(e.msg)}</div>`).join('') || '<div class="entry">(No entries yet. Be the first!)</div>'; }
    function escapeHtml(s){ return s.replace(/[&<>"']/g, m=>({"&":"&amp;","<":"&lt;",">":"&gt;","\"":"&quot;","'":"&#39;"}[m])); }

    // WebRing actions
    function ringPrev(){ alert('Taking you to: http://members.aol.com/~someone/prev.html'); }
    function ringNext(){ alert('Taking you to: http://members.aol.com/~someone/next.html'); }
    function ringRandom(){ alert('Teleporting to: http://geocities.com/Area51/Random.html'); }

    // DOWNLOAD MANAGER (parallel bandwidth share)
    const jobs=[]; let jobTimer=null;
    function addJob(filename, sizeKB){ const id=Math.random().toString(36).slice(2,7); const el=document.createElement('div'); el.className='job'; el.innerHTML=`<div><b>${filename}</b> — <span id="st_${id}">Queued</span></div>
      <div class="progress-wrap"><div class="progress" id="pr_${id}"></div></div>
      <div class="small mono">Size: ${(sizeKB/1024).toFixed(2)} MB</div>
      <button class="btn90" onclick="cancelJob('${id}')">Cancel</button>`; document.getElementById('jobs').appendChild(el); const job={id, el, name:filename, size:sizeKB*1024, got:0}; jobs.push(job); startJobs(); }
    function startJobs(){ if(jobTimer) return; const status=(id)=>document.getElementById('st_'+id); const bar=(id)=>document.getElementById('pr_'+id); jobTimer=setInterval(()=>{
        // compute shared bandwidth
        const speed=parseInt(document.getElementById('globalSpeed').value,10); // bps
        const eff=0.85; let active=jobs.filter(j=>j.got<j.size);
        if(active.length===0){ clearInterval(jobTimer); jobTimer=null; return; }
        const bytesPerSec=(speed/8)*eff; const each=bytesPerSec/active.length; const tick= dialed? 500:200; const jitter=()=>0.7+Math.random()*0.6;
        active.forEach(j=>{ const delta=each*(tick/1000)*jitter(); j.got=Math.min(j.got+delta, j.size); const pct=(j.got/j.size)*100; bar(j.id).style.width=pct+'%'; const remain=(j.size-j.got)/each; status(j.id).textContent = `${(j.got/1024).toFixed(0)} KB of ${(j.size/1024).toFixed(0)} KB @ ${(each/1024).toFixed(1)} KB/s — ${fmtTime(remain)} left`; if(j.got>=j.size){ status(j.id).textContent='Complete. Opening in Winamp…'; }
        });
      }, dialed?500:200);
    }
    function cancelJob(id){ const i=jobs.findIndex(j=>j.id===id); if(i>=0){ jobs[i].el.remove(); jobs.splice(i,1); if(jobs.every(j=>j.got>=j.size)){ clearInterval(jobTimer); jobTimer=null; } } }
    function fmtTime(s){ if(!isFinite(s)) return '∞'; const m=Math.floor(s/60); const sec=Math.ceil(s%60); return (m>0? m+'m ': '') + sec + 's'; }

    // Init
    window.addEventListener('load', ()=>{ simulatePageLoad(); renderGuestbook(); });
  </script></body>
</html>
