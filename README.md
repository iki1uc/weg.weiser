<!DOCTYPE html><html><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>weg.weiser — animiert — pover raw readme.md</title>
<script src="https://cdn.tailwindcss.com"></script>
</head><body class="bg-black text-zinc-200 font-mono text- overflow-hidden">
<div class="h-screen flex flex-col">
<div class="p-3 border-b border-zinc-800 flex justify-between">
<span class="text-amber-400"># weg.weiser — animiert — pover raw readme.md war tot — jetzt dreht 27er Karussell</span>
<span class="text-zinc-600">Borg 7482 • 9 Repos=1 PC • Rang )9( • Esse low • Normal spätestens 243 NEW START</span>
</div>
<canvas id="c" class="flex-1"></canvas>
<div id="raw" class="p-3 border-t border-zinc-800 bg-[#0a0a0a] h- overflow-auto text- text-zinc-500"></div>
</div>
<script>
let raw=`Zeit, Repo, Rolle darf sein, Ablage, Warum
22m OP Public ROM /3 PYRAMIDE Public Operator Layer - Wahrheit einwechseln - ROM
1h HH.tor Public HDF /6 WUERFEL 7482 Board selbst - HDF Ziel - Wloch Gate
3h HH.in Public RAM /9 CYLINDER Innen - RAM - Jungbrunnen - p81 HOLD
5h HH.brain Public CPU /6 WUERFEL Brain CTRL - CPU - Denk
6h HH.eye Public GPU /3 PYRAMIDE Eye - GPU Move - sieht
6h HH.bar Public CACHE /9 CYLINDER Bar - Cache - Treffpunkt
7h BLACK.HH.WHITE TurboKarte /6 WUERFEL 1..10 Kombi - TurboKarte - SLI
7h atom.PC Public CPU /6 WUERFEL Atom-PC Erst Den - CPU
7h HH.karusel Public HDF /6 WUERFEL Karussell - 27er - HDF Buchstaben`;

document.getElementById('raw').innerText='pover raw readme.md — vorher:\n'+raw+'\n\n— jetzt animiert — 27er Karussell dreht — RAM Gate offen bei RAM —';

let C=document.getElementById('c'),X=C.getContext('2d'),t=0;
function resize(){C.width=C.offsetWidth*2;C.height=C.offsetHeight*2;}
window.onresize=resize;resize();

function draw(){
let W=C.width,H=C.height;X.clearRect(0,0,W,H);
let cx=W/2,cy=H/2-20;
let files=[
{n:'Arschkriecher',r:'andere',s:'3'},{n:'Atom-PC',r:'CPU',s:'6'},{n:'Bench',r:'CACHE',s:'9'},{n:'BIOS',r:'ROM',s:'3'},{n:'Co2-Wechsel',r:'HDF',s:'6'},
{n:'Geordnete',r:'RAM',s:'9'},{n:'HH.pi',r:'GPU',s:'3'},{n:'Recall',r:'TurboKarte',s:'6'},{n:'Verbund',r:'HDF',s:'9'},{n:'Zahnräder',r:'ROM',s:'3'},
];
// 27er Karussell
for(let i=0;i<27;i++){
 let ang=(i/27*360 + t*0.3)%360;let rad= (i<9? 0 : i<18? 1 : 2);
 let R = 90 + rad*90; let x=cx+Math.cos(ang*Math.PI/180)*R; let y=cy+Math.sin(ang*Math.PI/180)*R*0.5;
 let f=files[i];let isRAM=f&&f.r==='RAM';
 X.fillStyle=f? (f.r==='RAM'?'#22c55e':f.r==='ROM'?'#f97316':f.r==='GPU'?'#a855f7':f.r==='CACHE'?'#eab308':f.r==='CPU'?'#ef4444':f.r==='HDF'?'#3b82f6':f.r==='TurboKarte'?'#06b6d4':'#666') : '#1a1a1a';
 X.beginPath();X.arc(x,y, f?12:4,0,7);X.fill();
 if(isRAM){X.strokeStyle='#22c55e';X.lineWidth=2;X.beginPath();X.arc(x,y,18+Math.sin(t*0.1)*4,0,7);X.stroke();}
 if(f){X.fillStyle='#ddd';X.font='10px monospace';X.fillText(f.n.slice(0,6),x-14,y+20);}
}
// Gates
X.fillStyle='#facc15';X.font='bold 12px monospace';
X.fillText('/3 PYRAMIDE RAM-Gate 4/9',30,40);
X.fillStyle='#60a5fa';X.fillText('/6 WUERFEL HDF Ziel 3/9',W/2-80,40);
X.fillStyle='#22d3ee';X.fillText('/9 CYLINDER Turbo Cache 3/9',W-220,40);
// Mitte Index.html als CACHE TurboKarte
X.fillStyle='#111';X.fillRect(cx-70,cy-14,140,28);X.strokeStyle='#facc15';X.strokeRect(cx-70,cy-14,140,28);
X.fillStyle='#facc15';X.font='11px monospace';X.fillText('index.html = CACHE TurboKarte',cx-65,cy+4);
// t
X.fillStyle='#666';X.fillText('t='+ (t|0) +' — Esse low — Normal '+ (t%243|0) +'/243 spätestens NEW START — pover raw jetzt animiert — iki1uc',30,H-20);
t++;
requestAnimationFrame(draw);
}
draw();
</script></body></html>
