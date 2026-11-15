<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#000000">
<title>Halo Flight Deck</title>
<meta name="description" content="An interim head coach and a full offensive staff for your business.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&family=Instrument+Serif:ital@0;1&family=Inter+Tight:wght@400;500;600&display=swap">
<style>
@font-face{font-family:"IS Fallback";src:local("Times New Roman"),local("TimesNewRomanPSMT"),local("Georgia");size-adjust:88%;ascent-override:104%;descent-override:28%;line-gap-override:0%}
@font-face{font-family:"IT Fallback";src:local("Arial"),local("Helvetica Neue"),local("Helvetica");size-adjust:94%;ascent-override:98%;descent-override:24%;line-gap-override:0%}
@font-face{font-family:"PM Fallback";src:local("Courier New"),local("Menlo");size-adjust:100%;ascent-override:102%;descent-override:27%;line-gap-override:0%}
:root{
  --bg:#000;--fg:#fff;--g1:#1C1C1E;--g2:#2C2C2E;--g3:#636366;--g4:#8E8E93;--ember:#E83214;
  --serif:"Instrument Serif","IS Fallback",Georgia,serif;
  --mono:"IBM Plex Mono","PM Fallback",ui-monospace,Menlo,monospace;
  --sans:"Inter Tight","Inter","IT Fallback",system-ui,-apple-system,Arial,sans-serif;
  --gut:16px;--rail:34px;--ease:cubic-bezier(.16,1,.3,1);
  --sat:env(safe-area-inset-top,0px);--sab:env(safe-area-inset-bottom,0px);
  color-scheme:dark;
}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#000;--fg:#fff}}
:root[data-theme="dark"]{--bg:#000;--fg:#fff}
*{box-sizing:border-box;margin:0;padding:0}
html{background:#000;-webkit-text-size-adjust:100%;overflow-x:hidden}
body{background:var(--bg);color:var(--fg);font-family:var(--sans);font-size:16px;line-height:1.5;overflow-x:hidden;-webkit-font-smoothing:antialiased;-webkit-tap-highlight-color:transparent;user-select:none;-webkit-user-select:none;-webkit-touch-callout:none}
button{font:inherit;color:inherit;background:none;border:0;cursor:pointer}
a{color:inherit}
:focus-visible{outline:1px solid var(--fg);outline-offset:3px}
.e{color:#fff}

/* ---------- fixed layers ---------- */
#gl{position:fixed;inset:0;width:100%;height:100%;display:block;z-index:0;background:#000}
#dims{position:fixed;inset:0;width:100%;height:100%;z-index:1;pointer-events:none;overflow:visible}
#dims text{font-family:var(--mono);font-size:10px;letter-spacing:.12em;fill:#8E8E93}
#dims .dl{stroke:#8E8E93;stroke-width:1;fill:none}
#dims .cl{stroke:#636366;stroke-width:1;stroke-dasharray:14 4 2 4;fill:none}
#dims .draw{stroke-dasharray:600;stroke-dashoffset:600;animation:draw 1.6s var(--ease) .5s forwards}
@keyframes draw{to{stroke-dashoffset:0}}
#scan{animation:scan 6s linear infinite}
@keyframes scan{0%{transform:translateY(0);opacity:0}8%{opacity:.5}92%{opacity:.5}100%{transform:translateY(var(--scanH,400px));opacity:0}}
#scrim{position:fixed;inset:0;z-index:2;pointer-events:none;background:linear-gradient(to top,rgba(0,0,0,.94) 0%,rgba(0,0,0,.82) 30%,rgba(0,0,0,0) 56%)}
#scrim2{position:fixed;inset:0;z-index:2;pointer-events:none;background:linear-gradient(to top,rgba(0,0,0,.9) 0%,rgba(0,0,0,.86) 58%,rgba(0,0,0,0) 82%);opacity:0}
#labels{position:fixed;inset:0;z-index:3;pointer-events:none;overflow:hidden}

/* falling cash rail */
#cash{position:fixed;top:0;right:0;bottom:0;width:var(--rail);z-index:4;pointer-events:none;overflow:hidden;-webkit-mask-image:linear-gradient(to bottom,transparent 0,#000 120px,#000 calc(100% - 110px),transparent 100%);mask-image:linear-gradient(to bottom,transparent 0,#000 120px,#000 calc(100% - 110px),transparent 100%)}
#cash i{position:absolute;top:0;left:var(--x);width:var(--w);height:auto;display:block;animation:fall var(--d) linear var(--dl) infinite;will-change:transform;opacity:var(--o)}
#cash svg{display:block;width:100%;height:auto}
@keyframes fall{from{transform:translate3d(0,-60px,0) rotate(var(--r0))}to{transform:translate3d(0,calc(100vh + 60px),0) rotate(var(--r1))}}

/* projected labels */
.pl{position:absolute;left:0;top:0;will-change:transform,opacity;opacity:0;pointer-events:none;transition:opacity .25s}
.pl.on{pointer-events:auto}
.pl.yr,.pl.yr.on,.pl.gate,.pl.gate.on{pointer-events:none}
.gate{font-family:var(--mono);font-size:11px;letter-spacing:.12em;text-transform:uppercase;padding:9px 11px;border:1px solid rgba(255,255,255,.55);background:rgba(0,0,0,.6);white-space:nowrap}
.gate b{font-weight:500;color:#8E8E93;margin-right:8px}
.gate:hover,.gate.hot{border-color:#fff;background:#000}
.yr{font-family:var(--mono);font-size:10px;letter-spacing:.16em;color:#fff;padding:3px 6px;border-left:1px solid #fff;background:rgba(0,0,0,.45);white-space:nowrap;font-variant-numeric:tabular-nums}
.dest{font-family:var(--mono);font-size:10.5px;letter-spacing:.1em;text-transform:uppercase;color:#8E8E93;padding:6px 8px;border:1px solid rgba(255,255,255,.25);background:rgba(0,0,0,.55);white-space:nowrap;min-height:30px}
.dest.hot{color:#fff;border-color:#fff}
.lock{width:var(--s,72px);height:var(--s,72px);transition:width .7s var(--ease),height .7s var(--ease),opacity .25s}
.lock i{position:absolute;width:12px;height:12px;border-color:rgba(255,255,255,.75);border-style:solid;border-width:0}
.lock i:nth-child(1){left:0;top:0;border-left-width:1px;border-top-width:1px}
.lock i:nth-child(2){right:0;top:0;border-right-width:1px;border-top-width:1px}
.lock i:nth-child(3){left:0;bottom:0;border-left-width:1px;border-bottom-width:1px}
.lock i:nth-child(4){right:0;bottom:0;border-right-width:1px;border-bottom-width:1px}
.lock span{position:absolute;left:calc(100% + 8px);top:50%;transform:translateY(-50%);font-family:var(--mono);font-size:10px;letter-spacing:.12em;text-transform:uppercase;white-space:nowrap;color:#8E8E93;transition:color .3s}
.lock em{position:absolute;left:calc(100% + 8px);top:calc(50% + 10px);font-style:normal;font-family:var(--mono);font-size:9px;letter-spacing:.14em;color:#fff;opacity:0;transition:opacity .3s}
.lock.locked{--s:30px}
.lock.locked i{border-color:#fff}
.lock.locked span{color:#fff}
.lock.locked em{opacity:1}
.lock.left span,.lock.left em{left:auto;right:calc(100% + 8px)}
.pyl{font-family:var(--mono);font-size:10px;letter-spacing:.12em;color:#8E8E93;padding:4px 6px;border:1px solid transparent;min-width:30px;min-height:26px}
.pyl.hot{color:#fff;border-color:#fff}

/* ---------- chrome ---------- */
#top{position:fixed;left:0;right:0;top:0;z-index:20;display:flex;align-items:flex-start;justify-content:space-between;gap:10px;padding:calc(12px + var(--sat)) var(--gut) 10px;pointer-events:none;background:linear-gradient(to bottom,rgba(0,0,0,.7),rgba(0,0,0,0))}
#top>*{pointer-events:auto}
.wm{font-family:var(--mono);font-size:12px;letter-spacing:.18em;font-weight:500;white-space:nowrap;text-decoration:none;display:block}
.wm b{color:#8E8E93;font-weight:500}
.btn{display:inline-flex;align-items:center;justify-content:center;gap:10px;min-height:44px;padding:0 18px;font-family:var(--mono);font-size:12px;letter-spacing:.12em;text-transform:uppercase;border:1px solid #fff;color:#fff;background:#000;text-decoration:none;transition:background .2s,color .2s,border-color .2s;white-space:nowrap}
.btn:hover{background:#fff;color:#000}
.btn.solid{background:#fff;color:#000}
.btn.solid:hover{background:#fff;color:#000}
.btn.sm{min-height:40px;padding:0 12px;font-size:10.5px;letter-spacing:.1em}
#hud{position:fixed;left:0;right:0;bottom:0;z-index:20;display:flex;align-items:flex-end;justify-content:space-between;gap:12px;padding:26px var(--gut) calc(12px + var(--sab));pointer-events:none;background:linear-gradient(to top,rgba(0,0,0,.92) 0%,rgba(0,0,0,.7) 55%,rgba(0,0,0,0))}
#hud>*{pointer-events:auto}
.ro{display:flex;gap:14px;font-family:var(--mono);font-variant-numeric:tabular-nums;pointer-events:none!important}
.ro div{line-height:1.25}
.ro small{display:block;font-size:9px;letter-spacing:.16em;color:#636366}
.ro span{font-size:11.5px;letter-spacing:.06em;color:#8E8E93}
.ctl{display:flex;gap:6px}
.tg{min-height:40px;min-width:44px;padding:0 10px;border:1px solid rgba(255,255,255,.4);font-family:var(--mono);font-size:10.5px;letter-spacing:.12em;background:rgba(0,0,0,.6)}
.tg[aria-pressed="true"]{border-color:#fff;color:#fff;background:#000}
.tg[aria-pressed="true"]::before{content:"";display:inline-block;width:8px;height:8px;background:var(--ember);margin-right:8px;vertical-align:0}
#hint{position:fixed;left:50%;bottom:calc(70px + var(--sab));transform:translateX(-50%);z-index:19;font-family:var(--mono);font-size:10px;letter-spacing:.14em;text-transform:uppercase;color:#8E8E93;white-space:nowrap;pointer-events:none;transition:opacity .4s;opacity:0}

/* warnings + vr hud */
#warn{position:fixed;z-index:4;right:calc(var(--rail) + 6px);top:calc(96px + var(--sat));pointer-events:none;opacity:0;transition:opacity .4s;display:flex;flex-direction:column;align-items:flex-end;gap:10px}
.stall{font-family:var(--mono);font-size:11px;letter-spacing:.2em;color:#fff;border:1px solid #fff;padding:5px 9px;animation:blink 1.1s steps(1) infinite}
@keyframes blink{50%{opacity:.25}}
.fuel{display:flex;align-items:flex-end;gap:8px;font-family:var(--mono);font-size:9.5px;letter-spacing:.14em;color:#8E8E93}
.fuel .bar{width:8px;height:110px;border:1px solid rgba(255,255,255,.6);position:relative}
.fuel .bar i{position:absolute;left:1px;right:1px;bottom:1px;background:#fff;height:calc((100% - 2px) * var(--f,1))}
.fuel .bar.low i{background:#8E8E93}
.fuel .ticks{display:flex;flex-direction:column;justify-content:space-between;height:110px;text-align:right}
#vr{position:fixed;inset:0;z-index:4;pointer-events:none;opacity:0;transition:opacity .5s}
#vr svg{position:absolute;inset:0;width:100%;height:100%}
#vr text{font-family:var(--mono);font-size:9px;letter-spacing:.08em;fill:#8E8E93;font-variant-numeric:tabular-nums}
#vr .v{fill:#fff;font-size:11px}
#hold{position:fixed;left:50%;top:50%;transform:translate(-50%,-50%);z-index:5;font-family:var(--mono);font-size:10px;letter-spacing:.2em;color:#fff;border:1px solid rgba(255,255,255,.5);padding:6px 10px;opacity:0;transition:opacity .3s;pointer-events:none;background:rgba(0,0,0,.4)}

/* ---------- content ---------- */
main{position:relative;z-index:10;pointer-events:none}
main a,main button,main [data-int]{pointer-events:auto}
.panel{min-height:100vh;min-height:100svh;display:flex;align-items:flex-end;padding:120px calc(var(--gut) + var(--rail) - 8px) calc(96px + var(--sab)) var(--gut);position:relative}
.panel.tall{min-height:135vh;min-height:135svh;padding-bottom:calc(96px + 35vh + var(--sab))}
.panel.c{align-items:center;justify-content:center;text-align:center}
.txt{width:100%;max-width:560px}
.k{font-family:var(--mono);font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:#8E8E93;margin-bottom:16px;display:flex;gap:8px;align-items:center}
.k::before{content:"";width:8px;height:8px;background:var(--ember);flex:none}
h1,h2,.big,.hl{font-family:var(--serif);font-weight:400;letter-spacing:-.01em;line-height:.98}
h1{font-size:clamp(58px,15.4vw,136px)}
h2{font-size:clamp(42px,11vw,84px)}
.hl{font-size:clamp(40px,10.4vw,76px);line-height:1}
.big{font-size:clamp(30px,7.8vw,54px);line-height:1.05}
.big+.big{margin-top:16px}
.lede{font-size:18px;line-height:1.45;color:#fff;margin:16px 0 24px;max-width:30ch}
.src{font-family:var(--mono);font-size:11px;letter-spacing:.05em;color:#8E8E93;margin-top:16px;line-height:1.5}
.stat{margin-top:24px;padding-top:16px;border-top:1px solid var(--g2)}
.row{display:flex;flex-wrap:wrap;gap:10px;align-items:center}
.help{font-family:var(--mono);font-size:10.5px;letter-spacing:.12em;text-transform:uppercase;color:#8E8E93;margin-top:16px}
.years{display:flex;gap:6px;margin-top:20px;flex-wrap:wrap}
.years span{font-family:var(--mono);font-size:12px;letter-spacing:.1em;padding:7px 9px;border:1px solid var(--g2);color:#fff;font-variant-numeric:tabular-nums}
.years span:first-child{border-color:#fff}
.list{list-style:none;margin-top:18px;border-top:1px solid var(--g2)}
.list li{border-bottom:1px solid var(--g2)}
.list li>button,.list li>span{display:flex;width:100%;align-items:center;gap:14px;padding:13px 0;text-align:left;font-size:16px;line-height:1.35}
.list .n{font-family:var(--mono);font-size:11px;color:#8E8E93;letter-spacing:.1em;min-width:22px}
.list .go{margin-left:auto;font-family:var(--mono);font-size:10.5px;letter-spacing:.12em;text-transform:uppercase;color:#8E8E93}
.list li>button:hover .go{color:#fff}
.why li>span{font-family:var(--serif);font-size:clamp(24px,6.4vw,34px);line-height:1.1;padding:14px 0}
.gnum{font-family:var(--mono);font-size:12px;letter-spacing:.14em;color:#8E8E93;margin-bottom:8px;font-variant-numeric:tabular-nums}
.tag{font-size:18px;line-height:1.4;margin:16px 0 0;color:#fff;max-width:32ch}
.steps{list-style:none;display:grid;grid-template-columns:repeat(5,1fr);gap:6px;margin-top:18px}
.steps button{display:flex;flex-direction:column;gap:10px;align-items:flex-start;width:100%;min-height:96px;padding:10px 8px;border:1px solid var(--g2);text-align:left;font-size:13px;line-height:1.25;transition:border-color .25s,background .25s;background:rgba(0,0,0,.4)}
.steps button .n{font-family:var(--mono);font-size:11px;color:#8E8E93}
.steps button[aria-pressed="true"]{border-color:#fff;background:#000}
.steps button[aria-pressed="true"] .n{color:#fff}
.roles{font-size:17px;color:#fff;margin:4px 0 4px;line-height:1.4}
.chk li>button{gap:14px}
.box{width:18px;height:18px;border:1px solid rgba(255,255,255,.6);flex:none;position:relative}
[aria-pressed="true"] .box{border-color:#fff}
[aria-pressed="true"] .box::after{content:"";position:absolute;left:5px;top:1px;width:5px;height:10px;border:solid #fff;border-width:0 1.5px 1.5px 0;transform:rotate(45deg)}
.mets{list-style:none;display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-top:18px}
.mets button{width:100%;min-height:46px;padding:0 12px;border:1px solid var(--g2);text-align:left;font-family:var(--mono);font-size:11px;letter-spacing:.08em;text-transform:uppercase;color:#8E8E93;transition:border-color .25s,color .25s;background:rgba(0,0,0,.4)}
.mets button[aria-pressed="true"]{border-color:#fff;color:#fff}
.chips{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin:20px 0 16px}
.chips button{min-height:46px;padding:0 12px;border:1px solid var(--g2);font-size:14px;text-align:left;transition:border-color .25s,background .25s;background:rgba(0,0,0,.4);display:flex;align-items:center;gap:10px}
.chips button .n{font-family:var(--mono);font-size:10px;color:#636366}
.chips button[aria-pressed="true"]{border-color:#fff;background:#000}
.chips button[aria-pressed="true"] .n{color:#fff}
.spanro{font-family:var(--mono);font-size:12px;letter-spacing:.12em;color:#8E8E93;margin-top:18px;font-variant-numeric:tabular-nums}
.spanro b{color:#fff;font-weight:500}
.spanbar{display:flex;gap:4px;margin-top:10px}
.spanbar i{height:3px;flex:1;background:var(--g2);transition:background .3s}
.spanbar i.on{background:#fff}
.urg{font-family:var(--serif);font-size:clamp(28px,7.2vw,46px);line-height:1.08;max-width:18ch}
.tnum{font-family:var(--mono);font-variant-numeric:tabular-nums;font-size:clamp(46px,14vw,112px);letter-spacing:-.03em;line-height:1;margin-top:22px;white-space:nowrap}
.tnum i{font-style:normal;color:#fff}
.tmeta{display:flex;gap:26px;margin-top:16px;font-family:var(--mono);font-variant-numeric:tabular-nums}
.tmeta small{display:block;font-size:9.5px;letter-spacing:.14em;color:#8E8E93;text-transform:uppercase}
.tmeta span{font-size:16px;letter-spacing:.06em}
.mail{font-family:var(--mono);font-size:clamp(15px,4.3vw,20px);letter-spacing:.02em;user-select:text;-webkit-user-select:text;-webkit-touch-callout:default;word-break:break-all;padding:16px 0;border-top:1px solid var(--g2);border-bottom:1px solid var(--g2);margin:20px 0 14px}
.sub{font-family:var(--serif);font-size:clamp(26px,6.6vw,40px);line-height:1.05;margin-top:16px}
.brick{font-family:var(--mono);font-size:12px;letter-spacing:.18em;text-transform:uppercase;color:#fff;margin-top:22px}
footer{position:relative;z-index:10;padding:30vh calc(var(--gut) + var(--rail) - 8px) calc(96px + var(--sab)) var(--gut);display:flex;justify-content:space-between;align-items:center;gap:16px;pointer-events:none}
footer>*{pointer-events:auto}
.flink{font-family:var(--mono);font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:#8E8E93;min-height:44px;padding:0 4px;text-decoration:underline;text-underline-offset:4px}
.flink:hover{color:#fff}
.reveal{opacity:0;transform:translateY(14px);transition:opacity .9s var(--ease),transform .9s var(--ease)}
.reveal.in{opacity:1;transform:none}
#heroIn{will-change:opacity,transform}


/* orbit pad */
#pad{position:fixed;inset:0;z-index:15;touch-action:none;cursor:grab;display:none}
#pad.on{display:block}
#pad:active{cursor:grabbing}

/* fallback */
#fb{display:none;position:fixed;inset:0;z-index:0;align-items:flex-start;justify-content:center;padding:96px var(--gut) 0}
#fb svg{width:min(88vw,640px);height:auto;opacity:.75}
.nogl #fb{display:flex}
.nogl #gl,.nogl #dims,.nogl #labels,.nogl .ctl,.nogl .ro{display:none}

@media (max-width:859px){
  .lock span,.lock.left span{left:50%;right:auto;top:calc(100% + 6px);transform:translateX(-50%)}
  .lock em,.lock.left em{display:none}
  .lock{--s:50px}
  .lock.locked{--s:28px}
}
@media (min-width:860px){
  :root{--gut:28px;--rail:72px}
  #scrim{background:linear-gradient(to right,rgba(0,0,0,.92) 0%,rgba(0,0,0,.74) 32%,rgba(0,0,0,0) 56%)}
  #scrim2{background:linear-gradient(to right,rgba(0,0,0,.9) 0%,rgba(0,0,0,.8) 40%,rgba(0,0,0,0) 62%)}
  .panel{align-items:center;padding:120px 0 110px 7vw}
  .panel.c{padding:120px 7vw}
  .panel.tall{padding-bottom:110px}
  .txt{max-width:540px}
  .lede{font-size:20px}
  h1{font-size:clamp(84px,8.4vw,140px)}
  #hint{left:auto;right:calc(var(--rail) + 8px);transform:none;bottom:84px}
  .steps button{min-height:110px;font-size:14px}
  .btn.sm{padding:0 16px;font-size:11px}
  .fuel .bar,.fuel .ticks{height:150px}
  footer{padding-left:7vw}
}
@media (max-width:370px){.steps{grid-template-columns:repeat(3,1fr)}h1{font-size:52px}.btn.sm{padding:0 9px;font-size:9.5px;letter-spacing:.06em}.wm{font-size:11px;letter-spacing:.14em}.ro{gap:10px}}
@media (prefers-reduced-motion:reduce){
  .reveal{opacity:1;transform:none;transition:none}
  #scan{display:none}
  #dims .draw{animation:none;stroke-dashoffset:0}
  .stall{animation:none}
  #cash i{animation:none;transform:translate3d(0,var(--ry),0) rotate(var(--r0))}
  *{scroll-behavior:auto!important}
}

/* ---------- v8 additions ---------- */
h1,h2,.big,.hl,.cl1{text-wrap:balance}
p{text-wrap:pretty}
.pre{font-family:var(--mono);font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:#8E8E93;margin-bottom:8px}
.mets button{white-space:normal;line-height:1.3;padding:8px 12px}
.chips button{line-height:1.3;padding:8px 12px;min-height:56px}
.stepline{font-size:18px;line-height:1.4;margin-top:16px;min-height:1.4em;color:#fff}
.ln{display:block}.nw{white-space:nowrap}#close{max-width:720px}
.cl1{font-family:var(--serif);font-weight:400;font-size:clamp(32px,8.4vw,64px);line-height:1;color:#8E8E93;letter-spacing:-.01em}
.cl1 em{color:#fff;font-style:italic;display:block}
.cl2{font-size:18px;line-height:1.4;color:#fff;margin:48px 0 16px}
.pill{display:inline-grid;grid-template-columns:auto 18px;align-items:center;gap:12px;min-height:56px;padding:0 24px;border-radius:999px;background:var(--ember);color:#000;font-family:var(--mono);font-size:16px;font-weight:500;letter-spacing:.01em;border:0;cursor:pointer;max-width:100%;user-select:none;-webkit-user-select:none}
.pill .pt{display:grid}
.pill .pt>span{grid-area:1/1;transition:opacity .2s;white-space:nowrap}
.pill .pt .b{opacity:0}
.pill.done .pt .a{opacity:0}
.pill.done .pt .b{opacity:1}
.pill svg{width:18px;height:18px;display:block}
.pill:focus-visible{outline:2px solid #fff;outline-offset:4px}
.sr{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap;border:0}
.floc{font-family:var(--mono);font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:#8E8E93}
@media (max-width:370px){.pill{padding:0 16px;font-size:14px;gap:8px}}
@media (prefers-reduced-motion:reduce){.pill .pt>span{transition:none}}
</style>
</head>
<body>
<canvas id="gl" aria-hidden="true"></canvas>
<div id="fb" aria-hidden="true"></div>
<svg id="dims" aria-hidden="true"></svg>
<div id="scrim" aria-hidden="true"></div>
<div id="scrim2" aria-hidden="true"></div>
<div id="labels"></div>
<div id="cash" aria-hidden="true"></div>
<div id="warn" aria-hidden="true">
  <div class="stall">STALL</div>
  <div class="fuel"><div class="ticks"><span>F</span><span>½</span><span>E</span></div><div class="bar" id="fuelBar"><i></i></div><span style="writing-mode:vertical-rl;transform:rotate(180deg)">FUEL</span></div>
</div>
<div id="vr" aria-hidden="true"><svg id="vrsvg"></svg></div>
<div id="hold">STILL</div>
<div id="pad" aria-hidden="true"></div>

<header id="top">
  <a class="wm" href="#p0" aria-label="HALO // VENTURES, back to top">HALO <b>//</b> VENTURES</a>
  <a class="btn sm" href="#close">Contact</a>
</header>

<main id="main">
  <section class="panel" id="p0">
    <div class="txt reveal"><div id="heroIn">
      <h1>Five seats. One staff.</h1>
      <p class="lede">An interim head coach and a full offensive staff for your business.</p>
      <p class="help">Scroll to fly</p>
    </div></div>
  </section>

  <section class="panel" id="p1">
    <div class="txt reveal">
      <div class="k">Off course</div>
      <p class="big">Weak sales wastes demand.</p>
    </div>
  </section>

  <section class="panel" id="p2">
    <div class="txt reveal"><h2>Broken operations burn cash.</h2></div>
  </section>

  <section class="panel" id="p3">
    <div class="txt reveal"><p class="hl">Bad positioning loses customers.</p></div>
  </section>

  <section class="panel" id="p4">
    <div class="txt reveal">
      <div class="k">The stakes</div>
      <p class="big">43% of failed VC‑backed startups cited no product-market fit.</p>
      <p class="big">70% ran out of capital.</p>
      <p class="src">Source: VCBacked, The Startup Graveyard, 2026</p>
    </div>
  </section>

  <section class="panel tall" id="p5">
    <div class="txt reveal">
      <h2>Wrong hires compound it all.</h2>
      <div class="stat"><p class="big">A wrong sales hire costs <span class="nw">1.5–3×</span> the role’s annual pay.</p><p class="src">Source: U.S. Dept. of Labor, SHRM, HBR</p></div>
    </div>
  </section>

  <section class="panel" id="p6">
    <div class="txt reveal">
      <p class="big">New account executives take <span class="nw">4.5–6 months</span> to ramp.</p>
      <p class="src">Source: Bridge Group</p>
      <p class="tag">It can take two quarters to learn it was the hire, not the product.</p>
    </div>
  </section>

  <section class="panel gp" id="p7" data-g="0"><div class="txt reveal"></div></section>
  <section class="panel gp" id="p8" data-g="1"><div class="txt reveal"></div></section>
  <section class="panel gp" id="p9" data-g="2"><div class="txt reveal"></div></section>
  <section class="panel gp" id="p10" data-g="3"><div class="txt reveal"></div></section>
  <section class="panel gp" id="p11" data-g="4"><div class="txt reveal"></div></section>

  <section class="panel tall" id="p12">
    <div class="txt reveal">
      <div class="k">The shift</div>
      <p class="big">From founder-led to system-driven.</p>
      <p class="spanro" aria-hidden="true"><b id="spanN">00</b> / 08</p>
      <div class="spanbar" id="spanBar" aria-hidden="true"><i></i><i></i><i></i><i></i><i></i><i></i><i></i><i></i></div>
    </div>
  </section>

  <section class="panel" id="p13" data-dense="1">
    <div class="txt reveal">
      <div class="k">The method</div>
      <ol class="steps" id="steps" aria-label="Five steps"></ol>
      <p class="stepline" id="stepLine" aria-live="polite"></p>
    </div>
  </section>

  <section class="panel" id="p14">
    <div class="txt reveal"><h2>Potential is nothing without performance.</h2></div>
  </section>

  <section class="panel" id="p15">
    <div class="txt reveal">
      <p class="big">We don’t advise from the sidelines.</p>
      <p class="big">We get in the building and take the field.</p>
    </div>
  </section>

  <section class="panel" id="p16">
    <div class="txt reveal"><h2><span class="ln">Prove the play.</span> <span class="ln">Then recruit the player.</span></h2></div>
  </section>

  <section class="panel" id="p17" data-dense="1">
    <div class="txt reveal">
      <div class="k">How we hire</div>
      <ul class="mets" id="mets"></ul>
    </div>
  </section>

  <section class="panel" id="p18" data-dense="1">
    <div class="txt reveal">
      <div class="k">The outcome</div>
      <p class="big">Make growth repeatable.</p>
      <div class="chips" id="chips"></div>
    </div>
  </section>

  <section class="panel tall" id="p19" data-dense="1">
    <div class="txt reveal">
      <h2><span class="ln">Build the system.</span> <span class="ln">Prove the model.</span> <span class="ln">Scale the people.</span></h2>
      <p class="brick">Brick by brick.</p>
    </div>
  </section>

  <section class="panel" id="p20" data-dense="1">
    <div class="txt reveal" id="close">
      <p class="cl1">Change is inevitable. <em>Growth is optional.</em></p>
      <p class="cl2">Ready to grow?</p>
      <button class="pill" id="pill" type="button" aria-label="Copy email address chris@halovpartners.com"><span class="pt"><span class="a">chris@halovpartners.com</span><span class="b" aria-hidden="true">Copied ✓</span></span><svg viewBox="0 0 18 18" aria-hidden="true" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="6" y="6" width="9" height="9" rx="1.5"/><path d="M12 3.5V3a1 1 0 0 0-1-1H4a1 1 0 0 0-1 1v7a1 1 0 0 0 1 1h.5"/></svg></button>
      <p class="sr" id="live" role="status" aria-live="polite"></p>
    </div>
  </section>
</main>
<footer>
  <span class="wm">HALO <b>//</b> VENTURES</span>
  <span class="floc">Portland, Oregon</span>
</footer>

<div id="hud">
  <div class="ro" aria-hidden="true"><div><small>ALT</small><span id="roA">00000</span></div><div><small>SPD</small><span id="roS">0000</span></div><div><small>HDG</small><span id="roH">000°</span></div></div>
  <div class="ctl">
    <button class="tg" id="tgVR" aria-pressed="false" aria-label="VR mode, cockpit view">VR</button>
    <button class="tg" id="tgOrb" aria-pressed="false" aria-label="Pause and orbit">ORBIT</button>
  </div>
</div>
<div id="hint" aria-hidden="true"></div>

<script>
(function(){
'use strict';
/* =========================== content =========================== */
const PARTS=[
 {n:'01',l:'Growth',pre:'Fractional',t:'Chief Growth Officer',s:'Strategy, priorities, the biggest opportunities.'},
 {n:'02',l:'Revenue',pre:'Fractional',t:'Chief Revenue Officer',s:'Sales, client acquisition, pipeline, conversion.'},
 {n:'03',l:'Operations',pre:'Fractional',t:'Chief Operating Officer',s:'Systems, process, accountability.'},
 {n:'04',l:'Talent',pre:'',t:'Talent and recruiting',s:'Scout and hire the people who run it.'},
 {n:'05',l:'Partnerships',pre:'',t:'Partnerships and business development',s:'Channels and distribution.'}];
const STEPS=[{t:'Diagnose',d:'Find the biggest constraint.'},{t:'Design',d:'The strategy and playbooks.'},{t:'Build',d:'Embed leadership and execute.'},{t:'Prove',d:'Measure and refine.'},{t:'Scale',d:'Recruit and repeat.'}];
const METS=['Define what winning looks like','Build scorecards','Recruit to proven requirements','Onboard into working systems'];
const METL=['Winning','Scorecards','Recruit','Onboard'];
const SECT=['Customers','Accountability','Partnerships','People'];
const OUTC=['A reliable way to win customers','Clear accountability','Partnerships that create leverage','The right people in the right seats'];
const EMAIL='chris@halovpartners.com';
const $=s=>document.querySelector(s), $$=s=>[...document.querySelectorAll(s)];
const RM=matchMedia('(prefers-reduced-motion: reduce)').matches;

/* build DOM lists */
$$('.gp').forEach(sec=>{const p=PARTS[+sec.dataset.g];sec.querySelector('.txt').innerHTML=`<div class="k">The seats we fill</div><div class="gnum">${p.n} / 05</div>${p.pre?`<p class="pre">${p.pre}</p>`:''}<h2>${p.t}</h2><p class="tag">${p.s}</p>`;});
$('#steps').innerHTML=STEPS.map((s,k)=>`<li><button aria-pressed="${k===0}" data-step="${k}"><span class="n">0${k+1}</span>${s.t}</button></li>`).join('');$('#stepLine').textContent=STEPS[0].d;
$('#mets').innerHTML=METS.map((s,k)=>`<li><button aria-pressed="false" data-met="${k}">${s}</button></li>`).join('');
$('#chips').innerHTML=OUTC.map((s,k)=>`<button aria-pressed="false" data-sec="${k}"><span class="n">0${k+1}</span>${s}</button>`).join('');

/* falling cash rail (compositor-only CSS animation) */
(function(){const STK='<svg viewBox="0 0 40 26" aria-hidden="true"><g fill="#000" stroke="#fff" stroke-opacity=".6" stroke-width=".8" stroke-linejoin="round"><path d="M2 9L20 2L38 9L20 16Z"/><path d="M2 9V17L20 24V16Z"/><path d="M38 9V17L20 24V16Z"/></g><g stroke="#fff" stroke-opacity=".28" stroke-width=".5" fill="none"><path d="M2 11.7L20 18.7L38 11.7M2 14.3L20 21.3L38 14.3"/></g><path d="M9.6 6.1L12.4 4.9L30.4 11.9V19.9L27.6 21.1V13.1Z" fill="#636366"/></svg>';
  const n=matchMedia('(min-width:860px)').matches?11:8,el=$('#cash');let h='';
  for(let i=0;i<n;i++){const d=11+((i*7919)%9)+(i%3)*1.7,dl=-(i/n)*d-((i*31)%7);const w=matchMedia('(min-width:860px)').matches?34+(i%3)*8:22+(i%3)*4;
    h+=`<i style="--x:${(i*37)%Math.max(4,(matchMedia('(min-width:860px)').matches?72:34)-w)}px;--w:${w}px;--d:${d.toFixed(1)}s;--dl:${dl.toFixed(1)}s;--r0:${((i*53)%30)-15}deg;--r1:${((i*71)%60)-30}deg;--o:${(.45+(i%4)*.12).toFixed(2)};--ry:${(120+i*((innerHeight-240)/n)).toFixed(0)}px">${STK}</i>`;}
  el.innerHTML=h;})();

const T0=performance.now();

/* =========================== copy email =========================== */
(function(){const pill=$('#pill'),live=$('#live');
  const fallbackCopy=()=>{try{const t=document.createElement('textarea');t.value=EMAIL;t.setAttribute('readonly','');t.style.cssText='position:fixed;top:0;left:0;opacity:0';document.body.appendChild(t);t.select();const ok=document.execCommand('copy');t.remove();return ok;}catch(e){return false;}};
  const done=ok=>{pill.classList.toggle('done',ok);live.textContent=ok?'Email address copied':'Copy failed. The address is '+EMAIL;clearTimeout(pill._t);pill._t=setTimeout(()=>{pill.classList.remove('done');live.textContent='';},2400);};
  pill.addEventListener('click',()=>{if(navigator.clipboard&&navigator.clipboard.writeText){navigator.clipboard.writeText(EMAIL).then(()=>done(true),()=>done(fallbackCopy()));}else done(fallbackCopy());});
})();
document.addEventListener('click',e=>{
  const t=e.target;
  const st=t.closest('[data-step]'); if(st){setStep(+st.dataset.step);return;}
  const mt=t.closest('[data-met]'); if(mt){toggleLock(+mt.dataset.met);return;}
  const sc=t.closest('[data-sec]'); if(sc){setSector(+sc.dataset.sec);return;}
});
document.addEventListener('keydown',e=>{if(e.key==='Escape'&&G.orbit)setOrbit(false);});
const locks=new Array(METS.length).fill(false);let lockEls=[],pylEls=[],destEls=[];
function toggleLock(k,v){locks[k]=v===undefined?!locks[k]:v;$$('[data-met]').forEach(b=>b.setAttribute('aria-pressed',locks[+b.dataset.met]));const el=lockEls[k];if(el)el.classList.toggle('locked',locks[k]);need=true;}
function setStep(k){G.step=k;$('#stepLine').textContent=STEPS[k].d;$$('[data-step]').forEach(b=>b.setAttribute('aria-pressed',+b.dataset.step===k));pylEls.forEach((el,i)=>el.classList.toggle('hot',i===k));need=true;}
function setSector(k){G.sector=G.sector===k?-1:k;$$('[data-sec]').forEach(b=>b.setAttribute('aria-pressed',+b.dataset.sec===G.sector));destEls.forEach((el,i)=>el.classList.toggle('hot',i===G.sector));need=true;}

/* reveal */
const io='IntersectionObserver' in window?new IntersectionObserver(es=>es.forEach(en=>{if(en.isIntersecting){en.target.classList.add('in');}}),{threshold:.12}):null;
$$('.reveal').forEach(el=>io?io.observe(el):el.classList.add('in'));
setTimeout(()=>$$('.reveal').forEach(el=>{const r=el.getBoundingClientRect();if(r.top<innerHeight&&r.bottom>0)el.classList.add('in');}),1200);

/* =========================== state =========================== */
const G={p:0,pT:0,step:0,sector:-1,hotGate:-1,orbit:false,vr:false,firePulse:null};
window.__fd=G;
let need=true;

/* =========================== math =========================== */
const D2R=Math.PI/180, cl=(x,a,b)=>x<a?a:x>b?b:x, lerp=(a,b,t)=>a+(b-a)*t;
const ss=(a,b,x)=>{const t=cl((x-a)/(b-a),0,1);return t*t*(3-2*t);};
const range=(p,a,b,f)=>ss(a-f,a,p)*(1-ss(b,b+f,p));
const v3={add:(a,b)=>[a[0]+b[0],a[1]+b[1],a[2]+b[2]],sub:(a,b)=>[a[0]-b[0],a[1]-b[1],a[2]-b[2]],sc:(a,s)=>[a[0]*s,a[1]*s,a[2]*s],cross:(a,b)=>[a[1]*b[2]-a[2]*b[1],a[2]*b[0]-a[0]*b[2],a[0]*b[1]-a[1]*b[0]],norm:a=>{const l=Math.hypot(a[0],a[1],a[2])||1;return [a[0]/l,a[1]/l,a[2]/l];},lerp:(a,b,t)=>[lerp(a[0],b[0],t),lerp(a[1],b[1],t),lerp(a[2],b[2],t)]};
const Q={
  ax:(x,y,z,a)=>{const s=Math.sin(a/2);return [x*s,y*s,z*s,Math.cos(a/2)];},
  mul:(a,b)=>[a[3]*b[0]+a[0]*b[3]+a[1]*b[2]-a[2]*b[1],a[3]*b[1]-a[0]*b[2]+a[1]*b[3]+a[2]*b[0],a[3]*b[2]+a[0]*b[1]-a[1]*b[0]+a[2]*b[3],a[3]*b[3]-a[0]*b[0]-a[1]*b[1]-a[2]*b[2]],
  conj:q=>[-q[0],-q[1],-q[2],q[3]],
  rot:(q,v)=>{const u=[q[0],q[1],q[2]],s=q[3];const t=v3.sc(v3.cross(u,v),2);return v3.add(v3.add(v,v3.sc(t,s)),v3.cross(u,t));},
  slerp:(a,b,t)=>{let c=a[0]*b[0]+a[1]*b[1]+a[2]*b[2]+a[3]*b[3];let bb=b;if(c<0){c=-c;bb=[-b[0],-b[1],-b[2],-b[3]];}if(c>.9995){const r=[lerp(a[0],bb[0],t),lerp(a[1],bb[1],t),lerp(a[2],bb[2],t),lerp(a[3],bb[3],t)];const l=Math.hypot(...r);return r.map(x=>x/l);}const th=Math.acos(c),s=Math.sin(th),wa=Math.sin((1-t)*th)/s,wb=Math.sin(t*th)/s;return [a[0]*wa+bb[0]*wb,a[1]*wa+bb[1]*wb,a[2]*wa+bb[2]*wb,a[3]*wa+bb[3]*wb];},
  euler:(yaw,pitch,roll)=>Q.mul(Q.mul(Q.ax(0,1,0,yaw),Q.ax(1,0,0,pitch)),Q.ax(0,0,1,roll)),
  fromBasis:(x,y,z)=>{const m00=x[0],m11=y[1],m22=z[2],tr=m00+m11+m22;let q;
    if(tr>0){const s=Math.sqrt(tr+1)*2;q=[(y[2]-z[1])/s,(z[0]-x[2])/s,(x[1]-y[0])/s,.25*s];}
    else if(m00>m11&&m00>m22){const s=Math.sqrt(1+m00-m11-m22)*2;q=[.25*s,(y[0]+x[1])/s,(z[0]+x[2])/s,(y[2]-z[1])/s];}
    else if(m11>m22){const s=Math.sqrt(1+m11-m00-m22)*2;q=[(y[0]+x[1])/s,.25*s,(z[1]+y[2])/s,(z[0]-x[2])/s];}
    else{const s=Math.sqrt(1+m22-m00-m11)*2;q=[(z[0]+x[2])/s,(z[1]+y[2])/s,.25*s,(x[1]-y[0])/s];}
    const l=Math.hypot(...q);return q.map(v=>v/l);},
  look:(eye,tgt,up=[0,1,0])=>{const z=v3.norm(v3.sub(eye,tgt)),x=v3.norm(v3.cross(up,z)),y=v3.cross(z,x);return Q.fromBasis(x,y,z);}
};
const M4={
  qt(q,t,s=1,o=new Float32Array(16)){const [x,y,z,w]=q,x2=x+x,y2=y+y,z2=z+z,xx=x*x2,xy=x*y2,xz=x*z2,yy=y*y2,yz=y*z2,zz=z*z2,wx=w*x2,wy=w*y2,wz=w*z2;
    o[0]=(1-(yy+zz))*s;o[1]=(xy+wz)*s;o[2]=(xz-wy)*s;o[3]=0;o[4]=(xy-wz)*s;o[5]=(1-(xx+zz))*s;o[6]=(yz+wx)*s;o[7]=0;o[8]=(xz+wy)*s;o[9]=(yz-wx)*s;o[10]=(1-(xx+yy))*s;o[11]=0;o[12]=t[0];o[13]=t[1];o[14]=t[2];o[15]=1;return o;},
  view(q,e,o=new Float32Array(16)){const c=Q.conj(q);M4.qt(c,[0,0,0],1,o);const t=Q.rot(c,e);o[12]=-t[0];o[13]=-t[1];o[14]=-t[2];return o;},
  persp(fy,a,n,f,sx,sy,o=new Float32Array(16)){const t=1/Math.tan(fy/2),nf=1/(n-f);o.fill(0);o[0]=t/a;o[5]=t;o[8]=sx;o[9]=sy;o[10]=(f+n)*nf;o[11]=-1;o[14]=2*f*n*nf;return o;},
  mul(a,b,o=new Float32Array(16)){for(let c=0;c<4;c++)for(let r=0;r<4;r++)o[c*4+r]=a[r]*b[c*4]+a[4+r]*b[c*4+1]+a[8+r]*b[c*4+2]+a[12+r]*b[c*4+3];return o;},
  I:new Float32Array([1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1])
};
let seed=7;const rnd=()=>{seed=(seed*16807)%2147483647;return (seed-1)/2147483646;};

/* =========================== geometry =========================== */
/* layout per vertex: pos3 n3 c4 b1 = 11 floats */
function Geo(){this.a=[];}
Geo.prototype.v=function(p,n,c,b){this.a.push(p[0],p[1],p[2],n?n[0]:0,n?n[1]:0,n?n[2]:0,c?c[0]:0,c?c[1]:0,c?c[2]:0,c?c[3]:0,b===undefined?1:b);};
Geo.prototype.tri=function(a,b,c,C,nUp){let n=v3.norm(v3.cross(v3.sub(b,a),v3.sub(c,a)));if(nUp!==undefined&&n[1]*nUp<0)n=v3.sc(n,-1);this.v(a,n,C);this.v(b,n,C);this.v(c,n,C);};
Geo.prototype.seg=function(a,b,C,br){this.v(a,null,C,br);this.v(b,null,C,br);};
Geo.prototype.count=function(){return this.a.length/11;};

/* --- the craft --- */
const OUT=[[0,-2.2],[6.0,1.55],[5.55,2.05],[3.7,1.0],[2.3,2.05],[1.0,1.25],[0,1.75]];
const TOPP={T0:[0,.32,-.9],T1:[0,.48,0],T2:[0,.30,1.2],B1:[1.25,.24,.1],B2:[1.3,.16,.8],W:[3.4,.07,.6]};
const BOTP={T0:[0,-.12,-.9],T1:[0,-.16,0],T2:[0,-.12,1.2],B1:[1.25,-.12,.1],B2:[1.3,-.08,.8],W:[3.4,-.03,.6]};
const TRIS=[['O0','T0','B1'],['T0','T1','B1'],['T1','B2','B1'],['T1','T2','B2'],['T2','O6','O5'],['T2','O5','B2'],['B2','O5','O4'],['B2','O4','O3'],['O0','B1','W'],['B1','B2','W'],['B2','O3','W'],['O0','W','O1'],['W','O3','O2'],['W','O2','O1']];
function pt(name,surf,m){let p;if(name[0]==='O'){const o=OUT[+name[1]];p=[o[0],0,o[1]];}else p=(surf>0?TOPP:BOTP)[name].slice();if(m)p[0]=-p[0];return p;}
const topTris=[];
TRIS.forEach(t=>[false,true].forEach(m=>topTris.push(t.map(n=>pt(n,1,m)))));
function topY(x,z){for(const t of topTris){const [a,b,c]=t;const d=(b[2]-c[2])*(a[0]-c[0])+(c[0]-b[0])*(a[2]-c[2]);if(Math.abs(d)<1e-9)continue;const l1=((b[2]-c[2])*(x-c[0])+(c[0]-b[0])*(z-c[2]))/d,l2=((c[2]-a[2])*(x-c[0])+(a[0]-c[0])*(z-c[2]))/d,l3=1-l1-l2;if(l1>=-1e-6&&l2>=-1e-6&&l3>=-1e-6)return l1*a[1]+l2*b[1]+l3*c[1];}return 0;}
function buildCraft(){
  const F=new Geo(), L=new Geo(), E=new Geo(), EL=new Geo();
  const edges=new Map();
  const key=p=>p.map(v=>v.toFixed(3)).join(',');
  const addE=(a,b)=>{const ka=key(a),kb=key(b),k=ka<kb?ka+'|'+kb:kb+'|'+ka;if(!edges.has(k))edges.set(k,[a,b]);};
  [1,-1].forEach(s=>TRIS.forEach(t=>[false,true].forEach(m=>{const P=t.map(n=>pt(n,s,m));F.tri(P[0],P[1],P[2],null,s);addE(P[0],P[1]);addE(P[1],P[2]);addE(P[2],P[0]);})));
  const segs=[...edges.values()];
  const up=(x,z,o=.014)=>[x,topY(x,z)+o,z];
  const det=[];
  const poly=(pts,closed)=>{for(let i=0;i<pts.length-(closed?0:1);i++){const a=pts[i],b=pts[(i+1)%pts.length];const n=6;for(let k=0;k<n;k++){const t0=k/n,t1=(k+1)/n;det.push([up(lerp(a[0],b[0],t0),lerp(a[1],b[1],t0)),up(lerp(a[0],b[0],t1),lerp(a[1],b[1],t1))]);}}};
  [1,-1].forEach(sg=>{
    [[2,3],[3,4],[4,5],[5,6]].forEach(([i,j])=>{const A=OUT[i],B=OUT[j];const a=[lerp(A[0],B[0],.1),lerp(A[1],B[1],.1)],b=[lerp(A[0],B[0],.9),lerp(A[1],B[1],.9)];const ins=.3;
      poly([[a[0]*sg,a[1]-.02],[a[0]*sg,a[1]-ins],[b[0]*sg,b[1]-ins],[b[0]*sg,b[1]-.02]],false);});
    poly([[.42*sg,-.42],[.95*sg,-.22],[.95*sg,.12],[.42*sg,.18]],true);
    poly([[.1*sg,-.82],[.42*sg,-.62],[.4*sg,-.4],[.1*sg,-.46]],true);
    poly([[2.0*sg,.35],[2.9*sg,.55],[2.7*sg,.95]],false);
    /* leading-edge panel line + wingtip lamp housing */
    poly([[.6*sg,-1.3],[4.6*sg,.82]],false);
    poly([[5.2*sg,1.42],[5.75*sg,1.62]],false);
  });
  const ex=[[-.55,1.29],[.55,1.29],[.55,1.39],[-.55,1.39]].map(q=>up(q[0],q[1],.02));
  E.tri(ex[0],ex[1],ex[2],null,1);E.tri(ex[0],ex[2],ex[3],null,1);
  for(let i=0;i<4;i++)EL.seg(ex[i],ex[(i+1)%4],null,1);
  const onOut=q=>Math.abs(q[1])<1e-6;const all=segs.map(s=>({s,b:onOut(s[0])&&onOut(s[1])?1:.62})).concat(det.map(s=>({s,b:.55})));
  all.forEach(o=>{o.z=Math.min(o.s[0][2],o.s[1][2]);});
  all.forEach(o=>{const ord=(o.z+2.2)/4.3*.85+rnd()*.15;L.seg(o.s[0],o.s[1],[ord,0,0,0],o.b);});
  return {F,L,E,EL,segs:all.map(o=>o.s)};
}
const CRAFT=buildCraft();

/* --- flight plan --- */
const D=180, NWP=21;
/*          0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 */
const ALT=[28,30,26, 9,24,46,30,10,10,10,10,10,30,22,20,14,16,22,34,12,1.05];
const altAt=p=>{const i=cl(Math.floor(p),0,NWP-2),f=ss(0,1,p-i);return lerp(ALT[i],ALT[i+1],f);};
const xPath=p=>9*Math.sin(p*.85);
const zAt=p=>-p*D;
const posAt=p=>[xPath(p),altAt(p),zAt(p)];
/* camera offsets: [right, up, back] in heading frame */
const CK=[[5,3.2,12],[-7,4,17],[5,2.4,12],[-6,2.6,11],[8,5,17],[0,28,34],[-4,2.8,11],[0,2.4,14],[0,2.4,14],[0,2.4,14],[0,2.4,14],[0,2.4,14],[14,12,24],[11,10,18],[-8,3,13],[6,1.6,12],[0,6,20],[0,2.6,13],[0,16,22],[6,9,16],[0,24,15]];
const camOff=p=>{const i=cl(Math.floor(p),0,NWP-2),f=ss(0,1,p-i);return v3.lerp(CK[i],CK[i+1],f);};

/* fault line (mirrored in the vertex shader) */
const FX=z=>9*Math.sin(-z/D*.85)-4+22*Math.sin(z/90)+4*Math.sin(z/13);
const ZF0=-306,ZF1=-1160;

/* --- swarm (money in the air) --- */
function dart(G_,home,b,trail){const n=[0,0,-1.6],l=[-1.4,0,.9],r=[1.4,0,.9],k=[0,0,.4],t=[0,.25,-.1];
  if(G_.F){G_.F.tri(n,l,t,home,1);G_.F.tri(n,t,r,home,1);G_.F.tri(l,k,t,home,1);G_.F.tri(k,r,t,home,1);}
  [[n,l],[l,k],[k,r],[r,n],[n,t],[t,k],[l,t],[r,t]].forEach(([a,c])=>G_.L.seg(a,c,home,b));
  if(trail){const N=6;for(let i=0;i<N;i++){G_.L.v([0,0,.4+i*2.2],null,home,.55*(1-i/N));G_.L.v([0,0,.4+(i+1)*2.2],null,home,.55*(1-(i+1)/N));}}}
function buildSwarm(){const F=new Geo(),L=new Geo();for(let i=0;i<130;i++){let x=(rnd()*2-1)*110;if(Math.abs(x)<12)x+=x<0?-12:12;const home=[x,(rnd()*2-1)*30+6,(rnd()*2-1)*420,rnd()];dart({F,L},home,.95);}return {F,L};}
/* falling craft, five funding years + one early cluster */
const YEARS=[];
const CLUS=[{p:4.3,dx:20},{p:5.056,dx:-22},{p:5.122,dx:24},{p:5.189,dx:-26},{p:5.256,dx:26},{p:5.322,dx:-18}].map(c=>({c:[xPath(c.p)+c.dx,0,zAt(c.p)],p:c.p}));
function buildFall(){const F=new Geo(),L=new Geo();CLUS.forEach((cc,ci)=>{const n=ci===0?6:12;for(let i=0;i<n;i++){const home=[cc.c[0]+(rnd()*2-1)*13,0,cc.c[2]+(rnd()*2-1)*13,rnd()];dart({F,L},home,.9,true);}});return {F,L};}
function buildPoints(n){const a=new Float32Array(n*4);for(let i=0;i<n;i++){a[i*4]=(rnd()*2-1)*620;a[i*4+1]=12+Math.pow(rnd(),.7)*170;a[i*4+2]=(rnd()*2-1)*720;a[i*4+3]=rnd();}return a;}
function buildDebris(){const F=new Geo(),L=new Geo();for(let i=0;i<120;i++){let x=(rnd()*2-1)*70;if(Math.abs(x)<9)x+=x<0?-9:9;const C=[x,(rnd()*2-1)*26,(rnd()*2-1)*240,rnd()];const s=.3+Math.pow(rnd(),2)*1.6;
  const P=[[0,s*.2,0],[s*(rnd()+.3),0,s*(rnd()-.5)],[-s*(rnd()+.2),s*(rnd()-.5)*.5,s*(rnd()-.5)],[s*(rnd()-.5),-s*.25,s*(rnd()+.4)]];
  [[0,1,2],[0,2,3],[0,3,1],[1,3,2]].forEach(t=>F.tri(P[t[0]],P[t[1]],P[t[2]],C));[[0,1],[1,2],[2,0],[0,3],[1,3],[2,3]].forEach(e=>L.seg(P[e[0]],P[e[1]],C,.8));}return {F,L};}
function buildStreaks(){const L=new Geo();for(let i=0;i<240;i++){let x=(rnd()*2-1)*40,y=(rnd()*2-1)*22;if(Math.abs(x)<4&&Math.abs(y)<3)x+=x<0?-5:5;const len=3+rnd()*14;L.seg([0,0,0],[0,0,len],[x,y,rnd()*320,rnd()],.25+rnd()*.5);}return L;}
function buildRain(){const L=new Geo();for(let i=0;i<1400;i++){let x=(rnd()*2-1)*70,z=rnd()*300;if(Math.abs(x)<5)x+=x<0?-6:6;const len=1+rnd()*1.6;L.seg([0,0,0],[.06,len,.35*len],[x,rnd()*50,z,rnd()],.25+rnd()*.4);}return L;}

/* --- cracked runway (the problem) --- */
function buildCracked(){const L=new Geo(),C=new Geo();const z0=zAt(2.3),z1=zAt(3.95),hw=7,SL=10;
  for(let z=z0;z>z1;z-=SL){const p0=-z/D,p1=-(z-SL)/D;const xa=xPath(p0),xb=xPath(p1);
    [[-hw,0],[0,hw]].forEach(([u0,u1])=>{const sink=rnd()<.42?-(.2+rnd()*.9):0,tilt=sink?(rnd()-.5)*.8:0;
      const Y=(u,t)=>sink+tilt*(u-(u0+u1)/2)/hw*(t?1:-1)*.6;
      const P=[[xa+u0,Y(u0,0),z],[xa+u1,Y(u1,0),z],[xb+u1,Y(u1,1),z-SL],[xb+u0,Y(u0,1),z-SL]];
      for(let i=0;i<4;i++)L.seg(P[i],P[(i+1)%4],null,sink?.6:.85);
      /* cracks: random walks inside the slab */
      const nc=1+Math.floor(rnd()*3);for(let c=0;c<nc;c++){let u=lerp(u0,u1,rnd()),t=rnd()*.2,ang=rnd()*Math.PI;let prev=null;
        for(let s=0;s<9;s++){ang+=(rnd()-.5)*1.4;u=cl(u+Math.cos(ang)*1.3,u0+.1,u1-.1);t=cl(t+Math.abs(Math.sin(ang))*.12+.03,0,1);
          const q=[lerp(xa,xb,t)+u,Y(u,t>.5?1:0)+.02,z-SL*t];if(prev)C.seg(prev,q,null,.9-s*.06);prev=q;}}
      /* broken edge light */
      if(rnd()<.5){const ux=u0===-hw?-hw-.6:hw+.6;const q=[xa+ux,.05,z-SL*.5];L.seg([q[0]-.4,q[1],q[2]],[q[0]+.4,q[1],q[2]],null,.8);L.seg([q[0],q[1],q[2]-.4],[q[0],q[1],q[2]+.4],null,.8);}
    });
    if(rnd()<.6){const q0=[lerp(xa,xb,.2),.03,z-SL*.2],q1=[lerp(xa,xb,.6),.03,z-SL*.6];L.seg(q0,q1,null,.55);}
  }
  /* fault line with branches */
  let prev=null;for(let z=ZF0;z>=ZF1;z-=2.5){const q=[FX(z)-.02,.06,z];if(prev)C.seg(prev,q,null,1);prev=q;
    if(rnd()<.09){let b=q.slice(),a=rnd()*Math.PI*2;const sd=rnd()<.5?-1:1;for(let s=0;s<6;s++){a+=(rnd()-.5)*1;const nq=[b[0]+sd*Math.abs(Math.cos(a))*1.6,.06,b[2]+Math.sin(a)*1.6];C.seg(b,nq,null,.7-s*.1);b=nq;}}}
  return {L,C};}

/* --- the cleared runway with a deep foundation --- */
const RZ0=zAt(6.5),RZ1=zAt(12.6),RHW=7;
function buildRunway(){const L=new Geo(),F=new Geo(),Lt=new Geo();const len=RZ0-RZ1;
  const X=z=>xPath(-z/D);const K=z=>[(RZ0-z)/len,0,0,0];
  for(let z=RZ0;z>RZ1;z-=4){const z2=z-4,a=X(z),b=X(z2);
    L.seg([a-RHW,0,z],[b-RHW,0,z2],K(z),.8);L.seg([a+RHW,0,z],[b+RHW,0,z2],K(z),.8);
    if(Math.round((RZ0-z)/4)%3===0)L.seg([a,.02,z],[b,.02,z2],K(z),.65);
  }
  /* threshold bars + touchdown marks */
  for(let i=-5;i<=5;i++){if(!i)continue;const x=X(RZ0)+i*1.1;L.seg([x,.02,RZ0-2],[x,.02,RZ0-12],K(RZ0),.8);}
  [30,60,90].forEach(d=>{const z=RZ0-d,x=X(z);[-1,1].forEach(s=>{for(let j=0;j<3;j++){const xx=x+s*(2.2+j*.8);L.seg([xx,.02,z],[xx,.02,z-9],K(z),.6);}});});
  /* edge lights */
  for(let z=RZ0;z>RZ1;z-=6){const x=X(z);[-1,1].forEach(s=>{const c=[x+s*(RHW+.7),.05,z];Lt.seg([c[0]-.45,c[1],c[2]],[c[0]+.45,c[1],c[2]],K(z),1);Lt.seg([c[0],c[1],c[2]-.45],[c[0],c[1],c[2]+.45],K(z),1);});}
  /* approach light bars */
  for(let r=1;r<=6;r++){const z=RZ0+r*8,x=X(RZ0);const w=r===3?5:1.6;Lt.seg([x-w,.05,z],[x+w,.05,z],[0,0,0,0],1);}
  /* deep foundation: piers, decks and bracing below grade */
  const depths=[-1.6,-4,-8,-13];
  for(let z=RZ0;z>RZ1;z-=8){const z2=z-8,a=X(z),b=X(z2);depths.forEach((d,j)=>{const br=.42-j*.07;[-1,1].forEach(s=>F.seg([a+s*(RHW+.4),d,z],[b+s*(RHW+.4),d,z2],K(z),br));});
    if(Math.round((RZ0-z)/8)%2===0)F.seg([a-RHW,-1.6,z],[a+RHW,-1.6,z],K(z),.28);}
  for(let z=RZ0;z>RZ1;z-=24){const z2=z-24,a=X(z),b=X(z2);[-1,1].forEach(s=>{const x0=a+s*(RHW+.4),x1=b+s*(RHW+.4);
      F.seg([x0,0,z],[x0,-13,z],K(z),.55);F.seg([x0-.8*s,-13,z],[x0+.8*s,-13,z],K(z),.5);
      F.seg([x0,-1.6,z],[x1,-8,z2],K(z),.22);F.seg([x0,-8,z],[x1,-1.6,z2],K(z),.22);});
    F.seg([a-RHW-.4,-13,z],[a+RHW+.4,-13,z],K(z),.3);}
  return {L,F,Lt};}
/* --- five seats: pillar gates on the runway --- */
const GATES=[0,1,2,3,4].map(k=>{const p=7.22+k;return {p,pos:posAt(p)};});
function buildPillars(){const L=new Geo();GATES.forEach((g,k)=>{const c=g.pos,C=[k,0,0,0],top=c[1]+5.6,px=9.6,hw=1.05;
  const box=(cx,y0,y1,cz,hx,hz,b)=>{const P=y=>[[cx-hx,y,cz-hz],[cx+hx,y,cz-hz],[cx+hx,y,cz+hz],[cx-hx,y,cz+hz]];const A=P(y0),B=P(y1);for(let i=0;i<4;i++){L.seg(A[i],A[(i+1)%4],C,b);L.seg(B[i],B[(i+1)%4],C,b);L.seg(A[i],B[i],C,b);}};
  [-1,1].forEach(s=>{const x=c[0]+s*px;box(x,-7,top,c[2],hw,hw,.85);
    for(let y=1.2;y<top-1;y+=1.2){const P=[[x-hw,y,c[2]-hw],[x+hw,y,c[2]-hw],[x+hw,y,c[2]+hw],[x-hw,y,c[2]+hw]];for(let i=0;i<4;i++)L.seg(P[i],P[(i+1)%4],C,y%6<1.2?.45:.16);}
    box(x,-7.6,-7,c[2],2.8,2.8,.5);
    /* precision ticks on the inner face */
    for(let y=1;y<top;y+=.6){const t=Math.round(y/.6)%5===0?.7:.35;L.seg([x-s*hw,y,c[2]-hw],[x-s*(hw+t),y,c[2]-hw],C,.55);}
  });
  box(c[0],top-1.4,top,c[2],px+hw+1.2,hw*.9,.9);box(c[0],c[1]-5.6,c[1]-4.8,c[2],px+hw,hw*.7,.6);
  for(let i=-4;i<4;i++){const x0=c[0]+i*2.4,x1=x0+2.4;L.seg([x0,top-1.4,c[2]-hw*.9],[x1,top,c[2]-hw*.9],C,.35);}
 });return L;}
/* --- spans of runway lights multiplying --- */
const SPN=8,SPR=.7,SPX=xPath(12.3),SZ0=zAt(11.6),SZ1=zAt(13.6);
const SPF=[...Array(SPN+1)].map((_,k)=>(1-Math.pow(SPR,k))/(1-Math.pow(SPR,SPN)));
function spanReveal(q){for(let k=0;k<SPN;k++)if(q<SPF[k+1])return k+(q-SPF[k])/(SPF[k+1]-SPF[k]);return SPN+.001;}
function buildSpans(){const L=new Geo();const len=SZ0-SZ1;for(let k=0;k<SPN;k++){const sd=k%2?1:-1,x=SPX+sd*(26+Math.floor(k/2)*24);
  const K=z=>[k+cl((SZ0-z)/len,0,.999),0,0,0];
  for(let z=SZ0;z>SZ1;z-=8){[-1,1].forEach(s=>{const c=[x+s*5.2,.05,z];L.seg([c[0]-.4,c[1],c[2]],[c[0]+.4,c[1],c[2]],K(z),1);L.seg([c[0],c[1],c[2]-.4],[c[0],c[1],c[2]+.4],K(z),1);});
    L.seg([x-4.6,0,z],[x-4.6,0,z-8],K(z),.22);L.seg([x+4.6,0,z],[x+4.6,0,z-8],K(z),.22);
    if(Math.round((SZ0-z)/8)%2===0)L.seg([x,.02,z],[x,.02,z-4],K(z),.4);}
  for(let r=1;r<=4;r++){const z=SZ0+r*7;L.seg([x-1.4,.05,z],[x+1.4,.05,z],[k,0,0,0],.9);}
  for(let i=-3;i<=3;i++)L.seg([x+i*1.1,.02,SZ0-1],[x+i*1.1,.02,SZ0-8],[k,0,0,0],.55);
 }return L;}
/* --- pylons (how we work) --- */
const PYL=[0,1,2,3,4].map(k=>{const c=posAt(13);return [c[0]-17+k*2.2,0,c[2]-30-k*13];});
function buildPylons(){const L=new Geo();PYL.forEach((c,k)=>{const h=altAt(13)-5;const C=[k,0,0,0];L.seg(c,[c[0],h,c[2]],C,.55);const t=[c[0],h,c[2]],s=.9;
  const d=[[s,0,0],[0,s,0],[-s,0,0],[0,-s,0]].map(o=>v3.add(t,o));for(let i=0;i<4;i++)L.seg(d[i],d[(i+1)%4],C,1);
  for(let r=0;r<3;r++){const R=2+r*2.2;for(let i=0;i<24;i++){const a0=i/24*Math.PI*2,a1=(i+1)/24*Math.PI*2;L.seg([c[0]+Math.cos(a0)*R,.05,c[2]+Math.sin(a0)*R],[c[0]+Math.cos(a1)*R,.05,c[2]+Math.sin(a1)*R],C,.5-r*.12);}}});return L;}
/* --- beacons (data we track) --- */
const BP=17.08;
const BEAC=METS.map((m,k)=>{const c=posAt(BP);const col=k%2?1:-1,row=k>>1;const pt_=innerWidth<860;return [c[0]+col*(pt_?5.4:6.2),c[1]+(pt_?1.4:2.4)+row*(pt_?4.3:3.4),c[2]-6];});
function buildBeacons(){const L=new Geo();BEAC.forEach((c,k)=>{const s=.7,C=[k,0,0,0];const V=[[s,0,0],[-s,0,0],[0,s,0],[0,-s,0],[0,0,s],[0,0,-s]].map(o=>v3.add(c,o));[[0,2],[0,3],[0,4],[0,5],[1,2],[1,3],[1,4],[1,5],[2,4],[4,3],[3,5],[5,2]].forEach(e=>L.seg(V[e[0]],V[e[1]],C,.9));});return L;}
/* --- four destinations --- */
const DEST=[[-24,-28],[26,-36],[-18,-70],[22,-78]].map(o=>{const c=posAt(18);return [c[0]+o[0],0,c[2]+o[1]];});
function buildDest(){const L=new Geo();DEST.forEach((c,k)=>{const C=[k,0,0,0];const ring=(R,b,n=64)=>{for(let i=0;i<n;i++){const a0=i/n*Math.PI*2,a1=(i+1)/n*Math.PI*2;L.seg([c[0]+Math.cos(a0)*R,.05,c[2]+Math.sin(a0)*R],[c[0]+Math.cos(a1)*R,.05,c[2]+Math.sin(a1)*R],C,b);}};
  ring(9,.7);ring(9.6,.3);ring(14,.16,96);
  const ang=k*.6+.3;[[ang,7.5],[ang+1.2,6]].forEach(([a,l])=>{const dx=Math.cos(a),dz=Math.sin(a),nx=-dz,nz=dx;[-1,1].forEach(s=>L.seg([c[0]-dx*l+nx*s*.9,.05,c[2]-dz*l+nz*s*.9],[c[0]+dx*l+nx*s*.9,.05,c[2]+dz*l+nz*s*.9],C,.6));});
  for(let i=0;i<36;i++){const a=i/36*Math.PI*2,r1=i%9===0?12:10.6;L.seg([c[0]+Math.cos(a)*9.6,.05,c[2]+Math.sin(a)*9.6],[c[0]+Math.cos(a)*r1,.05,c[2]+Math.sin(a)*r1],C,.4);}
  L.seg([c[0],.05,c[2]],[c[0],9,c[2]],C,.5);
 });return L;}
/* --- the halo --- */
const HALO=[xPath(20),0,zAt(20)];
function buildHalo(){const L=new Geo();const ring=(R,b,n=160,y=.06)=>{for(let i=0;i<n;i++){const a0=i/n*Math.PI*2,a1=(i+1)/n*Math.PI*2;L.seg([HALO[0]+Math.cos(a0)*R,y,HALO[2]+Math.sin(a0)*R],[HALO[0]+Math.cos(a1)*R,y,HALO[2]+Math.sin(a1)*R],null,b);}};
  ring(9,1);ring(9.35,.8);ring(9.8,.45);ring(10.4,.25);ring(13,.3);ring(24,.18,220);
  for(let i=0;i<72;i++){const a=i/72*Math.PI*2,r0=9.8,r1=i%6===0?12:10.9;L.seg([HALO[0]+Math.cos(a)*r0,.06,HALO[2]+Math.sin(a)*r0],[HALO[0]+Math.cos(a)*r1,.06,HALO[2]+Math.sin(a)*r1],null,i%6===0?.8:.4);}
  [[1,0],[0,1]].forEach(([a,b])=>{L.seg([HALO[0]-a*20,.06,HALO[2]-b*20],[HALO[0]-a*14,.06,HALO[2]-b*14],null,.5);L.seg([HALO[0]+a*14,.06,HALO[2]+b*14],[HALO[0]+a*20,.06,HALO[2]+b*20],null,.5);});
  return L;}
/* --- the cash pile --- */
const NST=1600;
function buildStacks(){const F=new Geo(),L=new Geo(),Bd=new Geo();const c0=posAt(19);const list=[];
  for(let gx=-34;gx<=34;gx++)for(let gz=-60;gz<=26;gz++){if(rnd()<.45)continue;const x=c0[0]+gx*4.0+(rnd()-.5)*.6,z=c0[2]+gz*2.6+(rnd()-.5)*.6;const d=Math.abs(gx)*1.0+Math.abs(gz+10)*.45+rnd()*9;list.push({x,z,d});}
  list.sort((a,b)=>a.d-b.d);list.length=Math.min(list.length,NST);
  list.forEach((s,i)=>{const w=.8,dp=.34,LH=.3,layers=1+Math.floor(rnd()*3+Math.pow(rnd(),3)*6);const h=layers*LH;const ang=(rnd()<.5?0:Math.PI/2)+(rnd()-.5)*.2;const ca=Math.cos(ang),sa=Math.sin(ang);
    const P=(x,y,z)=>[s.x+x*ca-z*sa,y,s.z+x*sa+z*ca];const C=[i,0,0,0];
    const q=(a,b_,c,d)=>{F.tri(a,b_,c,C);F.tri(a,c,d,C);};
    [[-.82,0],[.82,0]].forEach(([ox])=>{const X=x=>x+ox;
      const b=[P(X(-w),0,-dp),P(X(w),0,-dp),P(X(w),0,dp),P(X(-w),0,dp)],t=[P(X(-w),h,-dp),P(X(w),h,-dp),P(X(w),h,dp),P(X(-w),h,dp)];
      q(t[0],t[1],t[2],t[3]);q(b[0],b[1],t[1],t[0]);q(b[1],b[2],t[2],t[1]);q(b[2],b[3],t[3],t[2]);q(b[3],b[0],t[0],t[3]);
      for(let k=0;k<4;k++){L.seg(t[k],t[(k+1)%4],C,.7);L.seg(b[k],t[k],C,.4);}
      for(let l=1;l<layers;l++){const y=l*LH;L.seg(P(X(-w),y,-dp),P(X(w),y,-dp),C,.07);L.seg(P(X(w),y,-dp),P(X(w),y,dp),C,.07);L.seg(P(X(w),y,dp),P(X(-w),y,dp),C,.07);L.seg(P(X(-w),y,dp),P(X(-w),y,-dp),C,.07);}
      [-.12,.12].forEach(bx=>{Bd.seg(P(X(bx),h+.01,-dp),P(X(bx),h+.01,dp),C,.9);Bd.seg(P(X(bx),0,-dp-.01),P(X(bx),h,-dp-.01),C,.6);Bd.seg(P(X(bx),0,dp+.01),P(X(bx),h,dp+.01),C,.6);});
    });
  });return {F,L,Bd,n:list.length};}

/* --- ground: an abstract fine-line street map, cleared along the runway --- */
const RIVER=z=>-150+130*Math.sin(z/520+.6)+60*Math.sin(z/190);
function buildGround(){const L=new Geo();const X0=-860,X1=860,Z0=420,Z1=-4000,B=140;
  const clip=(p,d,R,rx0,rz0,rx1,rz1)=>{let t0=-R,t1=R;const P=[[d[0],p[0],rx0,rx1],[d[1],p[1],rz0,rz1]];for(const [dd,pp,lo,hi] of P){if(Math.abs(dd)<1e-9){if(pp<lo||pp>hi)return null;continue;}let a=(lo-pp)/dd,b=(hi-pp)/dd;if(a>b)[a,b]=[b,a];t0=Math.max(t0,a);t1=Math.min(t1,b);if(t0>=t1)return null;}return [[p[0]+d[0]*t0,p[1]+d[1]*t0],[p[0]+d[0]*t1,p[1]+d[1]*t1]];};
  const seg2=(a,b,br)=>L.seg([a[0],0,a[1]],[b[0],0,b[1]],null,br);
  const cleared=(x,z)=>{const p=-z/D;if(p>6.2&&p<12.9&&Math.abs(x-xPath(p))<90)return true;if(p>11.4&&p<13.9&&Math.abs(x-SPX)<150)return true;return false;};
  for(let bx=X0;bx<X1;bx+=B)for(let bz=Z0;bz>Z1;bz-=B){
    const cx=bx+B/2,cz=bz-B/2;
    if(Math.hypot(cx-HALO[0],cz-HALO[2])<70)continue;
    if(Math.abs(cx-RIVER(cz))<62)continue;
    const clr=cleared(cx,cz);
    const r=rnd();
    const rx0=bx+2.2,rx1=bx+B-2.2,rz0=bz-B+2.2,rz1=bz-2.2;
    seg2([bx,bz],[bx+B,bz],clr?.16:.36);seg2([bx,bz],[bx,bz-B],clr?.16:.36);
    if(clr){/* survey grid only: the cleared ground */for(let i=1;i<7;i++){const x=bx+i*B/7;seg2([x,bz-B/2-1],[x,bz-B/2+1],.25);}continue;}
    if(r<.1)continue;
    if(r<.26){
      const n=4+Math.floor(rnd()*5);for(let k=0;k<n;k++){const R=12+k*7+rnd()*4,ph=rnd()*6,amp=2+rnd()*5;let prev=null;for(let i=0;i<=48;i++){const a=i/48*Math.PI*2,rr=R+amp*Math.sin(a*3+ph);const q=[cx+Math.cos(a)*rr*1.1,cz+Math.sin(a)*rr*.9];if(q[0]<rx0||q[0]>rx1||q[1]<rz0||q[1]>rz1){prev=null;continue;}if(prev&&rnd()>.04)seg2(prev,q,.28);prev=q;}}
      continue;}
    const ang=[0,0,0,.26,-.35,.78,.12][Math.floor(rnd()*7)];const sp=6+rnd()*6,sp2=sp*(1+rnd()*1.6);
    const d1=[Math.cos(ang),Math.sin(ang)],d2=[-d1[1],d1[0]];const R=B;
    for(let i=-Math.ceil(B/sp);i<=Math.ceil(B/sp);i++){const s=clip([cx+d2[0]*i*sp,cz+d2[1]*i*sp],d1,R,rx0,rz0,rx1,rz1);if(s)seg2(s[0],s[1],.26+rnd()*.08);}
    for(let i=-Math.ceil(B/sp2);i<=Math.ceil(B/sp2);i++){const s=clip([cx+d1[0]*i*sp2,cz+d1[1]*i*sp2],d2,R,rx0,rz0,rx1,rz1);if(s)seg2(s[0],s[1],.22+rnd()*.08);}
  }
  for(let z=Z0;z>Z1;z-=6){const a=RIVER(z),b=RIVER(z-6),w0=20+8*Math.sin(z/300),w1=20+8*Math.sin((z-6)/300);seg2([a-w0,z],[b-w1,z-6],.5);seg2([a+w0,z],[b+w1,z-6],.5);}
  const hw=[z=>220+90*Math.sin(z/700),z=>-420+140*Math.sin(z/900+1.3)];
  hw.forEach(f=>{for(let z=Z0;z>Z1;z-=8){const a=f(z),b=f(z-8);seg2([a-1.4,z],[b-1.4,z-8],.62);seg2([a+1.4,z],[b+1.4,z-8],.62);}});
  return L;}

/* =========================== WebGL =========================== */
const cv=$('#gl');
let gl=null;
try{gl=cv.getContext('webgl',{antialias:true,alpha:false,powerPreference:'high-performance',preserveDrawingBuffer:false})||cv.getContext('experimental-webgl');}catch(e){gl=null;}
if(!gl){fallback();return;}

const VS=`precision highp float;
attribute vec3 aP;attribute vec3 aN;attribute vec4 aC;attribute float aB;
uniform mat4 uVP,uM;uniform float uAnim,uT,uCount,uSpd,uShift;uniform vec3 uAnchor;
varying vec3 vW;varying vec3 vN;varying float vB;varying vec4 vC;
mat3 rotm(vec3 a,float g){a=normalize(a);float s=sin(g),c=cos(g),o=1.-c;return mat3(o*a.x*a.x+c,o*a.x*a.y+a.z*s,o*a.z*a.x-a.y*s,o*a.x*a.y-a.z*s,o*a.y*a.y+c,o*a.y*a.z+a.x*s,o*a.z*a.x+a.y*s,o*a.y*a.z-a.x*s,o*a.z*a.z+c);}
float fx(float z){return 9.*sin(-z/180.*.85)-4.+22.*sin(z/90.)+4.*sin(z/13.);}
void main(){vec3 p=aP;vec3 n=aN;vB=aB;vC=aC;
 if(uAnim==1.){
  float s=aC.w;mat3 R=rotm(vec3(sin(s*12.),cos(s*7.),sin(s*3.)+.3),uT*(.5+s*1.6)+s*20.);p=R*p;n=R*n;
  vec3 c=aC.xyz;c.z=mod(c.z+uT*(26.+s*30.)+240.,480.)-300.;c.y+=sin(uT*.7+s*9.)*1.5;p+=c+uAnchor;
 }else if(uAnim==2.){
  float g=clamp(uCount-aC.x,0.,1.);g=g*g*(3.-2.*g);p.y*=g;vB*=step(.001,g);
 }else if(uAnim==3.){
  float s=aC.w;float roll=sin(uT*.6+s*20.)*.35;mat3 R=rotm(vec3(0.,0.,1.),roll);p=R*p*(1.3+s*2.);n=R*n;
  vec3 c=aC.xyz;c.z=mod(c.z-uT*(14.+s*34.)+420.,840.)-420.;c.y+=sin(uT*.4+s*30.)*2.;p+=c+uAnchor;
 }else if(uAnim==4.){
  vec3 c=aC.xyz;c.z=mod(c.z+uT*uSpd,320.)-240.;p+=c+uAnchor;
 }else if(uAnim==5.){
  float m=(1.-smoothstep(-346.,-306.,p.z))*smoothstep(-1160.,-1110.,p.z)*uShift;
  float sd=step(fx(p.z),p.x);p.y+=-sd*m*6.+(1.-sd)*m*.6;p.x+=sd*m*3.6;p.z+=sd*m*.9;
 }else if(uAnim==6.){
  float s=aC.w;float ph=fract(s*7.31+uT*(.03+s*.025));float y=56.-ph*48.;
  mat3 R=rotm(vec3(0.,1.,0.),s*20.+uT*(.3+s*.4))*rotm(vec3(1.,0.,0.),-1.0-s*.3);p=R*(p*1.5);n=R*n;
  p+=vec3(aC.x,y,aC.z);vB*=smoothstep(8.,15.,y)*(1.-smoothstep(49.,56.,y));
 }else if(uAnim==7.){
  vec3 c=aC.xyz;c.y=mod(c.y-uT*34.,50.)-24.;c.z=mod(c.z+uT*uSpd,300.)-210.;p+=c+uAnchor;
 }
 vec4 w=uM*vec4(p,1.);vW=w.xyz;vN=mat3(uM)*n;gl_Position=uVP*w;}`;
const FS=`precision highp float;
uniform vec3 uColor,uCam;uniform float uCut,uAlpha,uLine,uReveal,uEmit,uHot,uCold,uHotK,uShade;uniform vec2 uFog;uniform vec4 uPulse,uHi;
varying vec3 vW;varying vec3 vN;varying float vB;varying vec4 vC;
void main(){float d=distance(vW,uCam);float fog=1.-smoothstep(uFog.x,uFog.y,d);
 float pd=distance(vW,uPulse.xyz);float R=uPulse.w;
 if(uLine>.5){float a=uAlpha*vB*fog;vec3 col=uColor;
  a*=step(vC.x,uReveal);
  if(uHotK>-.5){a*=abs(vC.x-uHotK)<.5?uHot:uCold;}
  if(R>0.){float band=exp(-pow((pd-R)/2.6,2.));float inside=step(pd,R)*exp(-(R-pd)/30.);a+=(band*.9+inside*.12)*fog*uAlpha*step(.001,vB);col=mix(col,vec3(1.),band);}
  if(uHi.w>0.){float h=1.-smoothstep(uHi.w*.55,uHi.w,distance(vW.xz,uHi.xz));a+=h*.5*fog*vB*uAlpha;}
  gl_FragColor=vec4(col,clamp(a,0.,1.));
 }else{
  if(vB<.001||d<uCut)discard;
  if(R>0.&&pd<R&&pd>R-46.)discard;
  vec3 n=normalize(vN);if(!gl_FrontFacing)n=-n;
  vec3 L=normalize(vec3(.4,.85,.3));float df=max(dot(n,L),0.);float hemi=n.y*.5+.5;
  vec3 c=uEmit>.5?uColor:uColor*(.30+.55*df+.25*hemi)*uShade;
  gl_FragColor=vec4(c*mix(1.,fog,uEmit>.5?.4:1.),uAlpha);}}`;
const PVS=`precision highp float;attribute vec4 aC;uniform mat4 uVP;uniform vec3 uAnchor,uCam;uniform float uT,uDpr;varying float vF;
void main(){vec3 c=aC.xyz;c.x+=uAnchor.x;c.z=mod(c.z-uT*(20.+aC.w*46.)-uAnchor.z+720.,1440.)-720.+uAnchor.z;float d=distance(c,uCam);vF=1.-smoothstep(120.,620.,d);gl_PointSize=clamp(420./d,1.2,3.4)*uDpr;gl_Position=uVP*vec4(c,1.);}`;
const PFS=`precision highp float;uniform float uA;varying float vF;void main(){gl_FragColor=vec4(1.,1.,1.,uA*vF);}`;
function sh(type,src){const s=gl.createShader(type);gl.shaderSource(s,src);gl.compileShader(s);if(!gl.getShaderParameter(s,gl.COMPILE_STATUS))throw new Error(gl.getShaderInfoLog(s));return s;}
function prog(vs,fs){const p=gl.createProgram();gl.attachShader(p,sh(gl.VERTEX_SHADER,vs));gl.attachShader(p,sh(gl.FRAGMENT_SHADER,fs));gl.linkProgram(p);if(!gl.getProgramParameter(p,gl.LINK_STATUS))throw new Error(gl.getProgramInfoLog(p));const u={},a={};
  for(let i=0;i<gl.getProgramParameter(p,gl.ACTIVE_UNIFORMS);i++){const n=gl.getActiveUniform(p,i).name;u[n]=gl.getUniformLocation(p,n);}
  for(let i=0;i<gl.getProgramParameter(p,gl.ACTIVE_ATTRIBUTES);i++){const n=gl.getActiveAttrib(p,i).name;a[n]=gl.getAttribLocation(p,n);}return {p,u,a};}
let PR,PP;
try{PR=prog(VS,FS);PP=prog(PVS,PFS);}catch(e){console.warn(e);fallback();return;}
function buf(g){const b=gl.createBuffer();gl.bindBuffer(gl.ARRAY_BUFFER,b);gl.bufferData(gl.ARRAY_BUFFER,new Float32Array(g.a),gl.STATIC_DRAW);const n=g.count();g.a=null;return {b,n};}

const swarm=buildSwarm(), debris=buildDebris(), stacks=buildStacks(), fall=buildFall(), crk=buildCracked(), rwy=buildRunway();
const B={
  craftF:buf(CRAFT.F),craftL:buf(CRAFT.L),lampF:buf(CRAFT.E),lampL:buf(CRAFT.EL),
  ground:buf(buildGround()),swarmF:buf(swarm.F),swarmL:buf(swarm.L),debF:buf(debris.F),debL:buf(debris.L),streak:buf(buildStreaks()),rain:buf(buildRain()),
  fallF:buf(fall.F),fallL:buf(fall.L),crkL:buf(crk.L),crkC:buf(crk.C),rwyL:buf(rwy.L),rwyF:buf(rwy.F),rwyLt:buf(rwy.Lt),
  pil:buf(buildPillars()),spans:buf(buildSpans()),pyl:buf(buildPylons()),beac:buf(buildBeacons()),dest:buf(buildDest()),halo:buf(buildHalo()),stF:buf(stacks.F),stL:buf(stacks.L),stB:buf(stacks.Bd)
};
const ring=(()=>{const g=new Geo();for(let i=0;i<128;i++){const a0=i/128*Math.PI*2,a1=(i+1)/128*Math.PI*2;g.seg([Math.cos(a0),0,Math.sin(a0)],[Math.cos(a1),0,Math.sin(a1)],null,1);}return buf(g);})();
const NPTS=22000;const ptsBuf=gl.createBuffer();gl.bindBuffer(gl.ARRAY_BUFFER,ptsBuf);gl.bufferData(gl.ARRAY_BUFFER,buildPoints(NPTS),gl.STATIC_DRAW);

/* =========================== sizing =========================== */
const isTouch=matchMedia('(pointer:coarse)').matches;
let W=0,H=0,dpr=1,qLevel=0,P=new Float32Array(16),VP=new Float32Array(16),V=new Float32Array(16);
let portrait=true,vfov=60*D2R;
const dprSteps=[1.5,1.25,1,.85];
let RAIL=34;
function resize(){RAIL=parseFloat(getComputedStyle(document.documentElement).getPropertyValue('--rail'))||34;W=innerWidth;H=innerHeight;portrait=W<860;dpr=Math.min(window.devicePixelRatio||1,dprSteps[qLevel]);
  cv.width=Math.round(W*dpr);cv.height=Math.round(H*dpr);gl.viewport(0,0,cv.width,cv.height);
  vfov=(W/H<1?64:44)*D2R;measure();layoutDims();buildVR();for(const el of [...gateEls,...lockEls,...pylEls,...destEls,...yrEls])el._hw=undefined;need=true;}
/* =========================== scroll -> progress =========================== */
let centers=[],dense=[];
const heroIn=$('#heroIn');
function measure(){const ps=$$('.panel');centers=ps.map(el=>el.offsetTop+el.offsetHeight/2);dense=ps.map(el=>el.dataset.dense?1:0);}
function readScroll(){const c=scrollY+innerHeight/2;let p=0;if(c<=centers[0])p=0;else if(c>=centers[centers.length-1])p=centers.length-1;else{for(let i=0;i<centers.length-1;i++){if(c<centers[i+1]){p=i+(c-centers[i])/(centers[i+1]-centers[i]);break;}}}
  const atEnd=scrollY+innerHeight>=document.documentElement.scrollHeight-4;if(atEnd)p=NWP-1;G.pT=p;lastInput=performance.now();need=true;
  /* hero copy clears out before the drawing folds (no overlap) */
  const ho=1-ss(.02,.24,p);heroIn.style.opacity=ho.toFixed(3);heroIn.style.transform=ho>0?`translate3d(0,${(Math.min(scrollY,innerHeight)*.5).toFixed(1)}px,0)`:'';heroIn.style.visibility=ho<.01?'hidden':'';}
addEventListener('scroll',readScroll,{passive:true});
addEventListener('resize',()=>{resize();readScroll();});

/* =========================== input =========================== */
let steerT=[0,0],steer=[0,0],steerV=0,lastInput=performance.now();
let timeScale=1,tsT=1,holding=false,holdTimer=0,down=null;
const isInt=t=>t.closest&&t.closest('button,a,input,[data-int],.pl.on,#hud,#top');
addEventListener('pointermove',e=>{if(e.pointerType==='mouse'&&!isTouch&&!G.orbit&&(e.clientX||e.clientY)){steerT=[cl((e.clientX/W-.5)*2.2,-1,1),cl(-(e.clientY/H-.5)*2.2,-1,1)];lastInput=performance.now();}
  if(down&&Math.hypot(e.clientX-down.x,e.clientY-down.y)>10){clearTimeout(holdTimer);if(!holding)down.moved=true;}},{passive:true});
addEventListener('pointerdown',e=>{if(G.orbit||isInt(e.target))return;down={x:e.clientX,y:e.clientY,t:performance.now(),moved:false};clearTimeout(holdTimer);holdTimer=setTimeout(()=>{if(down&&!down.moved){holding=true;tsT=0;$('#hold').style.opacity=1;}},380);},{passive:true});
function endPress(e,cancel){clearTimeout(holdTimer);if(holding){holding=false;tsT=1;$('#hold').style.opacity=0;down=null;return;}
  if(!cancel&&down&&!down.moved&&performance.now()-down.t<320)firePulse();down=null;}
addEventListener('pointerup',e=>endPress(e,false),{passive:true});
addEventListener('pointercancel',e=>endPress(e,true),{passive:true});
addEventListener('touchstart',e=>{const t=e.touches[0];if(t){steerT[0]=cl((t.clientX/W-.5)*2.2,-1,1);lastInput=performance.now();}},{passive:true});
addEventListener('touchmove',e=>{const t=e.touches[0];if(t){steerT[0]=cl((t.clientX/W-.5)*2.2,-1,1);lastInput=performance.now();}if(down&&t&&Math.hypot(t.clientX-down.x,t.clientY-down.y)>10){down.moved=true;clearTimeout(holdTimer);}},{passive:true});
addEventListener('touchend',()=>{steerT=[0,0];},{passive:true});
document.addEventListener('mouseleave',()=>{steerT=[0,0];});
addEventListener('contextmenu',e=>{if(holding)e.preventDefault();});
let pulse={o:[0,0,0],t:-1e9};
function firePulse(){if(RM)return;pulse={o:craftPos.slice(),t:performance.now()};need=true;}
G.firePulse=firePulse;

/* toggles */
const tgVR=$('#tgVR'),tgOrb=$('#tgOrb'),pad=$('#pad');
tgVR.addEventListener('click',()=>{G.vr=!G.vr;tgVR.setAttribute('aria-pressed',G.vr);if(G.vr&&G.p<.6){const el=$('#p1');scrollTo({top:el.offsetTop+el.offsetHeight/2-innerHeight/2,behavior:RM?'auto':'smooth'});}need=true;});
let orbit=[0,0],orbitT=[0,0],od=null;
function setOrbit(on){G.orbit=on;tgOrb.setAttribute('aria-pressed',on);tgOrb.textContent=on?'RESUME':'ORBIT';pad.classList.toggle('on',on);document.documentElement.style.overflow=on?'hidden':'';tsT=on?0:1;if(!on)orbitT=[0,0];showHint(on?'Drag to orbit':null);need=true;}
tgOrb.addEventListener('click',()=>setOrbit(!G.orbit));
pad.addEventListener('pointerdown',e=>{od={x:e.clientX,y:e.clientY,o:orbitT.slice()};try{pad.setPointerCapture(e.pointerId);}catch(_){}});
pad.addEventListener('pointermove',e=>{if(!od)return;orbitT=[od.o[0]-(e.clientX-od.x)*.008,cl(od.o[1]+(e.clientY-od.y)*.006,-.9,1.1)];need=true;});
pad.addEventListener('pointerup',()=>{od=null;});pad.addEventListener('pointercancel',()=>{od=null;});
const hintEl=$('#hint');let hintLock=null;
function showHint(s){hintLock=s;hintEl.textContent=s||'';hintEl.style.opacity=s?1:0;hintEl._t=s;}

/* =========================== projected labels =========================== */
const LB=$('#labels');
const mk=(cls,html,suf,aria,fn,tag='button')=>{const b=document.createElement(tag);b.className='pl '+cls;b._suf=suf;b.innerHTML=html;if(aria)b.setAttribute('aria-label',aria);if(tag==='button')b.tabIndex=-1;if(fn)b.addEventListener('click',fn);LB.appendChild(b);return b;};
const gateEls=PARTS.map((p,k)=>mk('gate',`<b>${p.n}</b>${p.l}`,' translate(-50%,-100%)',null,null,'span'));
lockEls=METS.map((m,k)=>mk('lock'+(BEAC[k][0]<posAt(BP)[0]?' left':''),`<i></i><i></i><i></i><i></i><span>${METL[k]}</span><em>LOCK</em>`,' translate(-50%,-50%)',`Lock ${m}`,()=>toggleLock(k)));
pylEls=PYL.map((c,k)=>mk('pyl'+(k===0?' hot':''),'0'+(k+1),' translate(-50%,-140%)',STEPS[k].t,()=>setStep(k)));
destEls=SECT.map((s,k)=>mk('dest',s,' translate(-50%,-130%)',s,()=>setSector(k)));
const yrEls=YEARS.map(y=>mk('yr',y,' translate(-50%,-50%)',null,null,'span'));
function project(p){const x=VP[0]*p[0]+VP[4]*p[1]+VP[8]*p[2]+VP[12],y=VP[1]*p[0]+VP[5]*p[1]+VP[9]*p[2]+VP[13],w=VP[3]*p[0]+VP[7]*p[1]+VP[11]*p[2]+VP[15];if(w<.1)return null;return [(x/w*.5+.5)*W,(1-(y/w*.5+.5))*H,w];}
const hideL=el=>{if(el._on){el.style.opacity=0;el.classList.remove('on');el._on=false;}};
function placeLabel(el,p,a,maxY){const s=a>.02?project(p):null;if(!s||s[0]<-40||s[0]>W+40||s[1]<84||s[1]>(maxY||H-70)){hideL(el);return;}
  let x=s[0];if(el._hw===undefined&&el.offsetWidth)el._hw=el.offsetWidth/2*(el.classList.contains('lock')?0:1);if(el._hw)x=cl(x,16+el._hw,W-RAIL-el._hw);
  el.style.transform=`translate3d(${x.toFixed(1)}px,${s[1].toFixed(1)}px,0)${el._suf||''}`;if(!el._on||Math.abs(el._a-a)>.05){el.style.opacity=a.toFixed(2);el._a=a;}if(!el._on){el.classList.add('on');el._on=true;}}

/* =========================== 3-view drawing poses =========================== */
const QTOP=Q.ax(1,0,0,Math.PI/2),QFRONT=Q.ax(0,1,0,Math.PI),QSIDE=Q.ax(0,1,0,Math.PI/2);
let DRAW=[];
const ZD=320;
function pxToView(px,py,depth){const nx=px/W*2-1,ny=1-py/H*2;return [(nx+P[8])*depth/P[0],(ny+P[9])*depth/P[5],-depth];}
function drawLayout(){
  if(portrait){const top=96,bot=H*.5;const wpx=Math.min(W*.76,420);const rh=bot-top;
    return {wpx,front:[W/2-6,top+rh*.07],top:[W/2-6,top+rh*.47],side:[W/2-6,top+rh*.9]};}
  const wpx=Math.min(W*.4,620),cx=W*.68;const top=130,bot=H-130,rh=bot-top;return {wpx,front:[cx,top+rh*.06],top:[cx,top+rh*.5],side:[cx,top+rh*.95]};}
let LAY=null;
function layoutDims(){
  buildProj(0);LAY=drawLayout();
  const unit=(2*ZD*Math.tan(vfov/2))/H;const s=LAY.wpx/12*unit;
  DRAW=[{q:QTOP,t:pxToView(LAY.top[0],LAY.top[1]-.075*LAY.wpx/12,ZD),s},{q:QFRONT,t:pxToView(LAY.front[0],LAY.front[1],ZD),s},{q:QSIDE,t:pxToView(LAY.side[0]-0.1*LAY.wpx/12,LAY.side[1],ZD),s}];
  buildDimsSVG();
}
const dimsSvg=$('#dims');
function buildDimsSVG(){
  if(!LAY)return;const k=LAY.wpx/12;const T=LAY.top,F=LAY.front,S=LAY.side;
  const tY=z=>T[1]-.075*k+z*k;
  const L=[],tx=[];
  const line=(a,b,c='dl draw')=>L.push(`<path class="${c}" d="M${a[0].toFixed(1)} ${a[1].toFixed(1)}L${b[0].toFixed(1)} ${b[1].toFixed(1)}"/>`);
  const tick=p=>L.push(`<path class="dl" d="M${(p[0]-4).toFixed(1)} ${(p[1]+4).toFixed(1)}L${(p[0]+4).toFixed(1)} ${(p[1]-4).toFixed(1)}"/>`);
  const text=(p,s,anchor='middle',rot=0)=>tx.push(`<text x="${p[0].toFixed(1)}" y="${p[1].toFixed(1)}" text-anchor="${anchor}" ${rot?`transform="rotate(${rot} ${p[0].toFixed(1)} ${p[1].toFixed(1)})"`:''}>${s}</text>`);
  const yS=tY(2.05)+18;line([T[0]-6*k,tY(1.6)+6],[T[0]-6*k,yS+6]);line([T[0]+6*k,tY(1.6)+6],[T[0]+6*k,yS+6]);line([T[0]-6*k,yS],[T[0]-.9*k,yS]);line([T[0]+.9*k,yS],[T[0]+6*k,yS]);tick([T[0]-6*k,yS]);tick([T[0]+6*k,yS]);text([T[0],yS+4],'12.00');
  if(!portrait){const xL=T[0]+6*k+22;line([T[0]+8,tY(-2.2)],[xL+6,tY(-2.2)]);line([T[0]+5.6*k+6,tY(2.05)],[xL+6,tY(2.05)]);line([xL,tY(-2.2)],[xL,tY(2.05)]);tick([xL,tY(-2.2)]);tick([xL,tY(2.05)]);text([xL+14,(tY(-2.2)+tY(2.05))/2],'4.25','middle',90);
    text([T[0]-6*k,tY(-2.2)-6],'SWEEP 32°','start');}
  line([T[0],tY(-2.2)-16],[T[0],tY(1.75)+10],'cl');line([F[0],F[1]-16],[F[0],F[1]+12],'cl');line([T[0]-5.2*k,tY(.2)],[T[0]+5.2*k,tY(.2)],'cl');
  const fx=F[0]+6*k+(portrait?6:14);line([F[0]+.5*k,F[1]-.48*k],[fx+6,F[1]-.48*k]);line([F[0]+6*k+4,F[1]],[fx+6,F[1]]);line([fx,F[1]-.48*k-14],[fx,F[1]+.16*k+10]);text([fx-4,F[1]-.48*k-18],'0.64','end');
  const sy=S[1]+.16*k+16;line([S[0]-2.3*k,sy-10],[S[0]-2.3*k,sy+4]);line([S[0]+1.95*k,sy-10],[S[0]+1.95*k,sy+4]);line([S[0]-2.3*k,sy],[S[0]+1.95*k,sy]);text([S[0],sy+14],'4.25');
  const lx=portrait?16:LAY.top[0]-LAY.wpx/2-6;const ly=portrait?-14:3;
  text([lx,F[1]+ly],'FRONT','start');text([lx,T[1]+ly],'TOP','start');text([lx,S[1]+ly],'SIDE','start');
  const scanTop=F[1]-24,scanH=S[1]+30-scanTop;
  dimsSvg.innerHTML=`<g id="dg">${L.join('')}${tx.join('')}<line id="scan" x1="${(T[0]-LAY.wpx/2-10).toFixed(1)}" x2="${(T[0]+LAY.wpx/2+10).toFixed(1)}" y1="${scanTop}" y2="${scanTop}" stroke="#fff" stroke-opacity=".35" style="--scanH:${scanH}px"/></g>`;
}

/* =========================== VR cockpit HUD (built once, updated by transforms) =========================== */
const vrsvg=$('#vrsvg');let VRX=null;
function buildVR(){
  const cx=W/2,cy=H/2,hw=portrait?Math.min(W/2-74,260):Math.min(W*.36,300),Lx=cx-hw,Rx=cx+hw,th=Math.min(H*.38,300),Ty=cy-th/2,hy=cy-Math.min(H*.33,290);
  const tw=Math.min(W*.56,420);let s='';
  s+=`<defs><clipPath id="cH"><rect x="${cx-tw/2}" y="${hy-22}" width="${tw}" height="34"/></clipPath><clipPath id="cS"><rect x="${Lx-64}" y="${Ty}" width="64" height="${th}"/></clipPath><clipPath id="cA"><rect x="${Rx}" y="${Ty}" width="70" height="${th}"/></clipPath><clipPath id="cL"><rect x="${cx-hw+10}" y="${Ty-10}" width="${hw*2-20}" height="${th+20}"/></clipPath></defs>`;
  /* ladder */
  let lad='';for(let i=-12;i<=12;i++){const y=cy-i*52.4;if(!i){lad+=`<path d="M${cx-hw+14} ${y}H${cx-46}M${cx+46} ${y}H${cx+hw-14}"/>`;continue;}
    lad+=`<path d="M${cx-86} ${y+(i>0?6:-6)}V${y}H${cx-36}M${cx+36} ${y}H${cx+86}V${y+(i>0?6:-6)}" ${i<0?'stroke-dasharray="6 5"':''}/><text x="${cx+92}" y="${y+3}" stroke="none">${Math.abs(i*5)}</text><text x="${cx-92}" y="${y+3}" text-anchor="end" stroke="none">${Math.abs(i*5)}</text>`;}
  s+=`<g clip-path="url(#cL)"><g id="vLad" stroke="#fff" stroke-opacity=".55" fill="none">${lad}</g></g>`;
  /* boresight + flight path marker */
  s+=`<g stroke="#fff" fill="none" stroke-opacity=".9"><path d="M${cx-30} ${cy}h14l6 7 6-7 6 7 6-7h14"/><g id="vFpm"><circle cx="${cx}" cy="${cy}" r="5"/><path d="M${cx-13} ${cy}h8M${cx+5} ${cy}h8M${cx} ${cy-5}v-6"/></g></g>`;
  /* bank scale */
  const br=Math.min(hw*.62,150);let bk='';[-60,-45,-30,-20,-10,0,10,20,30,45,60].forEach(a=>{const r0=br,r1=br+(a%30===0?10:6),t=(a-90)*D2R;bk+=`<path d="M${(cx+Math.cos(t)*r0).toFixed(1)} ${(cy+Math.sin(t)*r0).toFixed(1)}L${(cx+Math.cos(t)*r1).toFixed(1)} ${(cy+Math.sin(t)*r1).toFixed(1)}"/>`;});
  s+=`<g stroke="#fff" stroke-opacity=".5" fill="none">${bk}<path d="M${(cx+Math.cos(-150*D2R)*br).toFixed(1)} ${(cy+Math.sin(-150*D2R)*br).toFixed(1)}A${br} ${br} 0 0 1 ${(cx+Math.cos(-30*D2R)*br).toFixed(1)} ${(cy+Math.sin(-30*D2R)*br).toFixed(1)}" stroke-opacity=".25"/></g><path id="vBank" d="M${cx} ${cy-br+1}l-5 9h10z" fill="#fff"/>`;
  /* heading tape */
  let hd='';for(let a=-180;a<=540;a+=5){const x=cx+a*4;const m=a%30===0;hd+=`<path d="M${x} ${hy}v${m?-9:-5}"/>`;if(m)hd+=`<text x="${x}" y="${hy-12}" text-anchor="middle" stroke="none">${String(((a%360)+360)%360).padStart(3,'0')}</text>`;}
  s+=`<g clip-path="url(#cH)"><g id="vHdg" stroke="#fff" stroke-opacity=".6" fill="none">${hd}</g></g><path d="M${cx-tw/2} ${hy}H${cx+tw/2}" stroke="#fff" stroke-opacity=".25"/><path d="M${cx} ${hy+2}l-5 8h10z" fill="#fff"/><rect x="${cx-24}" y="${hy+12}" width="48" height="18" fill="#000" stroke="#fff" stroke-opacity=".7"/><text id="vHv" class="v" x="${cx}" y="${hy+25}" text-anchor="middle">000</text>`;
  /* speed tape (left) */
  let sp='';for(let v=0;v<=1000;v+=10){const y=cy-v*2;const m=v%50===0;sp+=`<path d="M${Lx} ${y}h${m?-9:-5}"/>`;if(m)sp+=`<text x="${Lx-13}" y="${y+3}" text-anchor="end" stroke="none">${v}</text>`;}
  s+=`<g clip-path="url(#cS)"><g id="vSpd" stroke="#fff" stroke-opacity=".6" fill="none">${sp}</g></g><path d="M${Lx} ${Ty}V${Ty+th}" stroke="#fff" stroke-opacity=".3"/><rect x="${Lx-58}" y="${cy-10}" width="50" height="20" fill="#000" stroke="#fff" stroke-opacity=".8"/><text id="vSv" class="v" x="${Lx-12}" y="${cy+4}" text-anchor="end">000</text><text x="${Lx-58}" y="${Ty-8}" stroke="none">KT</text>`;
  /* altitude tape (right) */
  let al='';for(let v=0;v<=6000;v+=100){const y=cy-v*.4;const m=v%500===0;al+=`<path d="M${Rx} ${y}h${m?9:5}"/>`;if(m)al+=`<text x="${Rx+13}" y="${y+3}" stroke="none">${v}</text>`;}
  s+=`<g clip-path="url(#cA)"><g id="vAlt" stroke="#fff" stroke-opacity=".6" fill="none">${al}</g></g><path d="M${Rx} ${Ty}V${Ty+th}" stroke="#fff" stroke-opacity=".3"/><rect x="${Rx+8}" y="${cy-10}" width="58" height="20" fill="#000" stroke="#fff" stroke-opacity=".8"/><text id="vAv" class="v" x="${Rx+12}" y="${cy+4}">00000</text><text x="${Rx+8}" y="${Ty-8}" stroke="none">FT</text>`;
  /* corner brackets + precision */
  const by=Ty+th+14,ry=Ty-40;s+=`<g stroke="#fff" stroke-opacity=".3" fill="none"><path d="M${Lx-60} ${by}v12h12M${Rx+66} ${by}v12h-12"/></g><text x="${Lx-58}" y="${ry}" stroke="none">PREC</text><text id="vPv" class="v" x="${Lx-58}" y="${ry+14}">±0.0°</text><text x="${Rx+64}" y="${ry}" text-anchor="end" stroke="none">G</text><text id="vGv" class="v" x="${Rx+64}" y="${ry+14}" text-anchor="end">1.0</text>`;
  vrsvg.innerHTML=s;
  VRX={cx,cy,lad:$('#vLad'),hdg:$('#vHdg'),spd:$('#vSpd'),alt:$('#vAlt'),bank:$('#vBank'),fpm:$('#vFpm'),hv:$('#vHv'),sv:$('#vSv'),av:$('#vAv'),pv:$('#vPv'),gv:$('#vGv')};
}

/* =========================== frame =========================== */
let craftPos=[0,0,0],craftQ=[0,0,0,1],camPos=[0,0,0],camQ=[0,0,0,1];
let tm=0,lastT=performance.now(),vrB=0,pPrev=0,spdS=380,fpsAcc=[],idleSkip=false,frameN=0,dens=0,FLY={alt:0,spd:0,hdg:0,prec:0,g:1};
const Mm=new Float32Array(16),Mloc=new Float32Array(16),Mcam=new Float32Array(16),Mw=new Float32Array(16);
const fuelBar=$('#fuelBar'),warn=$('#warn'),vrEl=$('#vr'),stallEl=$('.stall'),scrim2=$('#scrim2');
const roA=$('#roA'),roS=$('#roS'),roH=$('#roH'),spanN=$('#spanN'),spanBar=$$('#spanBar i');
let revealT0=performance.now(),spanShown=-1;
function buildProj(vr){const sy=portrait?-.36:0,sx=portrait?0:-.36;M4.persp(lerp(vfov,(portrait?78:62)*D2R,vr),W/H,lerp(.1,.04,vr),1100,lerp(sx,0,vr),lerp(sy,0,vr),P);}
function bindGeo(g){gl.bindBuffer(gl.ARRAY_BUFFER,g.b);const a=PR.a,st=44;
  gl.enableVertexAttribArray(a.aP);gl.vertexAttribPointer(a.aP,3,gl.FLOAT,false,st,0);
  if(a.aN>=0){gl.enableVertexAttribArray(a.aN);gl.vertexAttribPointer(a.aN,3,gl.FLOAT,false,st,12);}
  if(a.aC>=0){gl.enableVertexAttribArray(a.aC);gl.vertexAttribPointer(a.aC,4,gl.FLOAT,false,st,24);}
  if(a.aB>=0){gl.enableVertexAttribArray(a.aB);gl.vertexAttribPointer(a.aB,1,gl.FLOAT,false,st,40);}}
const U=PR.u;
const uf=(n,v)=>{if(U[n])gl.uniform1f(U[n],v);};
function drawG(g,{line=true,M=M4.I,color=[1,1,1],alpha=1,anim=0,reveal=1e5,emit=0,shade=1,hotK=-1,hot=1,cold=1,count=0,cut=0,shift=0}={}){
  if(alpha<=.003)return;bindGeo(g);uf('uCut',cut);gl.uniformMatrix4fv(U.uM,false,M);gl.uniform3fv(U.uColor,color);uf('uAlpha',alpha);uf('uLine',line?1:0);uf('uAnim',anim);uf('uReveal',reveal);uf('uEmit',emit);uf('uShade',shade);uf('uHotK',hotK);uf('uHot',hot);uf('uCold',cold);uf('uCount',count);uf('uShift',shift);
  if(line){gl.enable(gl.BLEND);gl.blendFunc(gl.SRC_ALPHA,gl.ONE);gl.depthMask(false);gl.disable(gl.POLYGON_OFFSET_FILL);}
  else{if(alpha<1){gl.enable(gl.BLEND);gl.blendFunc(gl.SRC_ALPHA,gl.ONE_MINUS_SRC_ALPHA);}else gl.disable(gl.BLEND);gl.depthMask(true);gl.enable(gl.POLYGON_OFFSET_FILL);gl.polygonOffset(1,2);}
  gl.drawArrays(line?gl.LINES:gl.TRIANGLES,0,g.n);}

const LAMP=[.92,.92,.94];
function frame(now){
  requestAnimationFrame(frame);const _t0=performance.now();
  try{frameBody(now);}catch(err){if(!frame._e){frame._e=1;console.warn(err);}}
  finally{const d=performance.now()-_t0;(G.cpu||(G.cpu=[])).push(d);if(G.cpu.length>4000)G.cpu.shift();}
}
function frameBody(now){
  if(document.hidden)return;
  let dt=Math.min(.05,(now-lastT)/1000);
  const idle=now-lastInput>7000&&Math.abs(G.pT-G.p)<.001;
  if(RM&&!need){lastT=now;return;}
  if(idle&&!RM){idleSkip=!idleSkip;if(idleSkip)return;}
  lastT=now;frameN++;
  if(!RM){fpsAcc.push(dt);if(fpsAcc.length>=50){const avg=fpsAcc.reduce((a,b)=>a+b,0)/fpsAcc.length;fpsAcc=[];if(avg>.026&&qLevel<dprSteps.length-1&&!idle){qLevel++;resize();}}}
  /* damped values: critically damped feel, no overshoot */
  const k=RM?1:1-Math.exp(-dt*4.4);
  G.p+=(G.pT-G.p)*k; if(Math.abs(G.pT-G.p)<1e-4)G.p=G.pT;
  const p=G.p;
  timeScale+=(tsT-timeScale)*(1-Math.exp(-dt*3));
  if(!RM)tm+=dt*timeScale;
  const ks=RM?1:1-Math.exp(-dt*2.6);
  const sPrev=steer[0];steer[0]+=(steerT[0]-steer[0])*ks;steer[1]+=(steerT[1]-steer[1])*ks;
  const sv=(steer[0]-sPrev)/Math.max(dt,1e-3);steerV+=(sv-steerV)*(1-Math.exp(-dt*5));
  vrB+=((G.vr?1:0)-vrB)*(RM?1:1-Math.exp(-dt*3.2));
  orbit[0]+=(orbitT[0]-orbit[0])*(1-Math.exp(-dt*6));orbit[1]+=(orbitT[1]-orbit[1])*(1-Math.exp(-dt*6));
  const fold=ss(.2,.86,p);
  /* section weights */
  const wSit=range(p,.7,1.4,.6), wShift=ss(1.4,2.5,p), wTurb=range(p,1.75,2.4,.55), wCrack=range(p,2.6,3.4,.6), wFall=range(p,3.8,5.6,.7), wYear=range(p,4.75,5.35,.4), wStall=range(p,5.7,6.3,.4),
        wGate=range(p,6.7,11.6,.5), wSpan=range(p,11.5,12.6,.6), wPyl=range(p,12.6,13.4,.5), wRain=range(p,14.6,15.4,.6), wWing=range(p,15.5,16.5,.6), wBeac=range(p,16.6,17.5,.55), wWho=range(p,17.6,18.4,.5), wHalo=ss(18,20,p);
  /* craft pose */
  const base=posAt(p);const steerK=1-ss(19.3,19.9,p);
  const lat=steer[0]*7*steerK, ver=steer[1]*2.4*steerK;
  const tb=(wTurb*.8+wCrack*.25)*(RM?0:1);
  const turbR=tb*(Math.sin(tm*1.4)*.07+Math.sin(tm*2.9+1)*.03), turbP=tb*(Math.sin(tm*1.7+2)*.025);
  const stallP=wStall*(.26+(RM?0:Math.sin(tm*1.1)*.03));
  craftPos=[base[0]+lat,base[1]+ver+tb*Math.sin(tm*1.1)*.4-wStall*1.2,base[2]];
  const yawPath=-Math.atan2(9*.85*Math.cos(p*.85),D);
  const roll=cl(-steerV*.11*steerK,-.6,.6)-steer[0]*.18*steerK+turbR;
  const pitch=steer[1]*.08*steerK+turbP+stallP+ss(19.4,20,p)*.06;
  craftQ=Q.euler(yawPath-steer[0]*.06*steerK,pitch,roll);
  /* chase camera (never shaken: follows the path, not the turbulence) */
  const off=camOff(p),kk=portrait?2.25:1.35;
  const qh=Q.euler(yawPath+orbit[0],0,0);
  let o=[off[0]*kk,off[1]*kk,off[2]*kk];
  if(orbit[1]){const r=Math.hypot(o[1],o[2]),a=Math.atan2(o[1],o[2])+orbit[1];o=[o[0],Math.sin(a)*r,Math.cos(a)*r];}
  const wingK=wWing*(fold>=1?1:0);const follow=v3.add([base[0]+lat*.55,base[1]+ver*.5-wStall*.6,base[2]],Q.rot(Q.euler(yawPath,0,0),[5*wingK,0,-1.5*wingK]));
  let ce=v3.add(follow,Q.rot(qh,o));
  if(ce[1]<1.5)ce[1]=1.5;
  let cq=Q.look(ce,follow);
  if(vrB>.001){const vf=vrB*fold;const eye=v3.add(craftPos,Q.rot(craftQ,[0,.62,-.55]));const cockQ=Q.mul(craftQ,Q.euler(orbit[0],-.06+orbit[1]*.5,-roll*.35));
    ce=v3.lerp(ce,eye,vf);cq=Q.slerp(cq,cockQ,vf);}
  camPos=ce;camQ=cq;
  buildProj(vrB*fold);
  M4.view(camQ,camPos,V);M4.mul(P,V,VP);
  /* ---- draw ---- */
  gl.clearColor(0,0,0,1);gl.clear(gl.COLOR_BUFFER_BIT|gl.DEPTH_BUFFER_BIT);gl.enable(gl.DEPTH_TEST);gl.depthFunc(gl.LEQUAL);
  gl.useProgram(PR.p);
  gl.uniformMatrix4fv(U.uVP,false,VP);gl.uniform3fv(U.uCam,camPos);uf('uT',tm);gl.uniform3fv(U.uAnchor,craftPos);uf('uSpd',lerp(70,190,wTurb)*timeScale);
  const pa=(now-pulse.t)/1000*95;gl.uniform4f(U.uPulse,pulse.o[0],pulse.o[1],pulse.o[2],pa<320?pa:-1);
  if(pa<320)need=true;
  const hi=G.sector>=0&&wWho>.01?DEST[G.sector]:null;
  gl.uniform4f(U.uHi,hi?hi[0]:0,0,hi?hi[2]:0,hi?40:0);
  /* craft: three drawing copies merge into one */
  const flightT=Q.rot(Q.conj(camQ),v3.sub(craftPos,camPos)),flightQ=Q.mul(Q.conj(camQ),craftQ);
  const reveal=RM?1:cl((now-revealT0)/1700,0,1);
  const copies=fold<1?[0,1,2]:[0];M4.qt(camQ,camPos,1,Mcam);
  const faceShade=ss(.15,.85,fold);
  gl.uniform2f(U.uFog,1e5,2e5);
  for(const c of copies){
    const d=DRAW[c]||DRAW[0];const f=c===0?fold:ss(0,.7,fold);
    const qv=Q.slerp(d.q,flightQ,f),tv=v3.lerp(d.t,flightT,f),sv_=lerp(d.s,1,f);
    M4.qt(qv,tv,sv_,Mloc);const eps=lerp(.015,1,ss(0,.6,f));Mloc[2]*=eps;Mloc[6]*=eps;Mloc[10]*=eps;M4.mul(Mcam,Mloc,Mm);
    const la=c===0?1:1-ss(.25,.7,fold);
    if(c===0){drawG(B.craftF,{line:false,M:Mm,color:[.13,.13,.14],shade:faceShade});drawG(B.lampF,{line:false,M:Mm,color:LAMP,emit:1});}
    drawG(B.craftL,{M:Mm,alpha:la*lerp(.8,.95,fold)*(1-vrB*fold*.7),reveal:c===0&&fold>.05?1e5:reveal});
    drawG(B.lampL,{M:Mm,color:LAMP,alpha:la*reveal});
  }
  /* wingman: in the work with you */
  if(wWing>.01&&fold>=1){const wp=v3.add(craftPos,Q.rot(craftQ,[10,.4,2.5]));M4.qt(craftQ,wp,1,Mw);
    drawG(B.craftF,{line:false,M:Mw,color:[.13,.13,.14],alpha:wWing>.98?1:wWing});drawG(B.craftL,{M:Mw,alpha:wWing*.9});drawG(B.lampL,{M:Mw,color:LAMP,alpha:wWing});}
  gl.uniform2f(U.uFog,portrait?60:70,portrait?560:600);
  if(fold>.01){
    const gA=ss(.1,.9,fold);
    /* opaque solids first */
    if(wSit>.01)drawG(B.swarmF,{line:false,anim:3,color:[.12,.12,.13],cut:6});
    if(wTurb>.01)drawG(B.debF,{line:false,anim:1,color:[.16,.16,.17],cut:6});
    if(p>3.3&&p<7)drawG(B.fallF,{line:false,anim:6,color:[.12,.12,.13]});
    const stCount=stacks.n?Math.min(stacks.n,70+(now-T0)/1000*7):0;
    if(p>17.5)drawG(B.stF,{line:false,anim:2,color:[.11,.11,.12],count:stCount});
    /* lines */
    drawG(B.ground,{alpha:gA,anim:5,shift:wShift});
    if(p>1.2&&p<7.4){const ca=(1-ss(6.6,7.4,p));drawG(B.crkL,{anim:5,shift:wShift,alpha:ca*.9});drawG(B.crkC,{anim:5,shift:wShift,color:LAMP,alpha:ca*wShift*(.55+.45*wCrack)});}
    if(wSit>.01)drawG(B.swarmL,{anim:3,alpha:wSit});
    if(wTurb>.01)drawG(B.debL,{anim:1,alpha:wTurb});
    if(p>3.3&&p<7)drawG(B.fallL,{anim:6,alpha:.25+wFall*.75});
    const stA=(.16+wTurb*.6)*gA*(1-ss(13.4,14.4,p))*(1-wRain)*(RM?0:1)*Math.max(.15,timeScale);
    drawG(B.streak,{anim:4,alpha:stA});
    if(wRain>.01&&!RM)drawG(B.rain,{anim:7,alpha:wRain*.75});
    if(p>5.6&&p<13.8){const rr=ss(6.15,7.3,p)*1.001;drawG(B.rwyL,{alpha:.95,reveal:rr});drawG(B.rwyF,{alpha:.95,reveal:rr});drawG(B.rwyLt,{alpha:1,reveal:rr});
      const raise=ss(6.2,7.0,p)*5;drawG(B.pil,{anim:2,count:raise,alpha:.95,hotK:G.hotGate,hot:1.7,cold:G.hotGate>=0?.7:1});}
    if(p>10.8&&p<14.6){const q=RM?(p>11.8?1:ss(11.2,12,p)):ss(11.2,12,p);const sr=spanReveal(q);drawG(B.spans,{alpha:.95,reveal:sr});
      const sn=Math.min(8,Math.floor(sr));if(sn!==spanShown){spanShown=sn;spanN.textContent=String(sn).padStart(2,'0');spanBar.forEach((el,i)=>el.classList.toggle('on',i<sn));}}
    if(p>11.8&&p<14.8)drawG(B.pyl,{alpha:Math.max(wPyl,.3),hotK:G.step,hot:1.5,cold:.45});
    if(p>15.6&&p<18.4)drawG(B.beac,{alpha:Math.max(wBeac,.35)});
    if(p>16.6&&p<19.4)drawG(B.dest,{alpha:Math.max(wWho,.3),hotK:G.sector,hot:1.7,cold:G.sector>=0?.5:1});
    if(hi){const pr=RM?0:(tm*.5)%1;M4.qt([0,0,0,1],[hi[0],.12,hi[2]],11+pr*8,Mm);drawG(ring,{M:Mm,color:LAMP,alpha:wWho*(1-pr)});M4.qt([0,0,0,1],[hi[0],.12,hi[2]],9,Mm);drawG(ring,{M:Mm,color:LAMP,alpha:wWho});}
    if(p>17.5){drawG(B.stL,{anim:2,alpha:.85,color:[.92,.92,.94],count:stCount});drawG(B.stB,{anim:2,alpha:.75,color:LAMP,count:stCount});}
    if(p>17.5){const pul=RM?1:.8+.2*Math.sin(tm*2);drawG(B.halo,{color:LAMP,alpha:pul*(.5+wHalo*.5)});}
    if(pa>0&&pa<320){const r=pa;M4.qt([0,0,0,1],[pulse.o[0],.15,pulse.o[2]],r,Mm);drawG(ring,{M:Mm,alpha:(1-r/320)*.9});M4.qt([0,0,0,1],pulse.o,r,Mm);drawG(ring,{M:Mm,alpha:(1-r/320)*.5});}
    if(wSit>.01){gl.useProgram(PP.p);gl.uniformMatrix4fv(PP.u.uVP,false,VP);gl.uniform3fv(PP.u.uAnchor,craftPos);gl.uniform3fv(PP.u.uCam,camPos);gl.uniform1f(PP.u.uT,tm);gl.uniform1f(PP.u.uDpr,dpr);gl.uniform1f(PP.u.uA,wSit*.85);
      gl.bindBuffer(gl.ARRAY_BUFFER,ptsBuf);for(const n in PR.a)gl.disableVertexAttribArray(PR.a[n]);gl.enableVertexAttribArray(PP.a.aC);gl.vertexAttribPointer(PP.a.aC,4,gl.FLOAT,false,16,0);
      gl.enable(gl.BLEND);gl.blendFunc(gl.SRC_ALPHA,gl.ONE);gl.depthMask(false);gl.drawArrays(gl.POINTS,0,qLevel>1?NPTS/2:NPTS);gl.disableVertexAttribArray(PP.a.aC);}
  }
  /* ---- overlays ---- */
  const dgo=1-ss(.0,.2,p);const g_=document.getElementById('dg');if(g_){g_.style.opacity=dgo.toFixed(3);dimsSvg.style.display=dgo<.005?'none':'';}
  placeAll(p,wGate,wPyl,wBeac,wWho,wYear);
  /* warnings: turbulence = fuel, stall = STALL */
  const wW=Math.max(wTurb,wStall);warn.style.opacity=(wW>.02?Math.min(1,wW*1.3):0).toFixed(2);
  if(wW>.02){stallEl.style.display=wStall>.05?'':'none';const fuel=lerp(1,.2,ss(1.8,6,p));fuelBar.style.setProperty('--f',fuel.toFixed(3));fuelBar.classList.toggle('low',fuel<.3);}
  /* scrim density follows the panel */
  const di=Math.round(cl(p,0,dense.length-1));dens+=((dense[di]||0)-dens)*(RM?1:1-Math.exp(-dt*5));scrim2.style.opacity=dens.toFixed(3);
  /* flight data (shared by mini readout + cockpit) */
  const v=(p-pPrev)/Math.max(dt,1e-3);pPrev=p;const landing=1-ss(19.2,20,p);
  spdS+=((360+Math.min(280,Math.abs(v)*D*.9))*landing+(1-landing)*14-spdS)*(1-Math.exp(-dt*3));
  FLY.alt=craftPos[1]*100;FLY.spd=spdS;FLY.hdg=((-(yawPath-steer[0]*.06)*180/Math.PI)%360+360)%360;FLY.prec=Math.max(.1,.1+Math.abs(roll)*4+wTurb*3*(.6+.4*Math.abs(Math.sin(tm*2)))+wStall*2-wGate*.05);FLY.g=1+Math.abs(steerV)*.08+wTurb*.25*Math.abs(Math.sin(tm*2.3));
  if(frameN%6===0&&fold>.5){roA.textContent=String(Math.round(FLY.alt)).padStart(5,'0');roS.textContent=String(Math.round(FLY.spd)).padStart(4,'0');roH.textContent=String(Math.round(FLY.hdg)%360).padStart(3,'0')+'°';}
  const vo=vrB*fold;vrEl.style.opacity=vo.toFixed(2);
  if(vo>.01&&VRX)updateVR(roll,pitch);
    if(!hintLock){const h=(p>.6&&p<1.5)?(isTouch?'Tap to scan':'Move to steer · click to scan'):(p>1.7&&p<2.4?'Hold to still':'');if(hintEl._t!==h){hintEl._t=h;hintEl.textContent=h;hintEl.style.opacity=h?1:0;}}
  if(wBeac>.6&&!RM){const n=Math.floor(cl((p-16.7)/.45,0,1)*(METS.length-.01));for(let i=0;i<n;i++)if(!lockTouched[i]){lockTouched[i]=true;toggleLock(i,true);}}
  need=false;
}
const lockTouched=new Array(METS.length).fill(false);
function placeAll(p,wGate,wPyl,wBeac,wWho,wYear){
  const lim=portrait?H*.56:H-70;
  GATES.forEach((g,k)=>{const a=wGate*ss(g.p-1.2,g.p-.85,p)*(p<g.p+.05?1:0);placeLabel(gateEls[k],[g.pos[0],g.pos[1]+7.6,g.pos[2]],a,lim);});
  PYL.forEach((c,k)=>placeLabel(pylEls[k],[c[0],altAt(13)-4,c[2]],wPyl,lim));
  BEAC.forEach((c,k)=>placeLabel(lockEls[k],c,wBeac,lim));
  DEST.forEach((c,k)=>placeLabel(destEls[k],[c[0],9.5,c[2]],wWho,lim));
  YEARS.forEach((y,k)=>{const cc=CLUS[k+1].c;placeLabel(yrEls[k],[cc[0],26,cc[2]],wYear,lim);});
}
function updateVR(roll,pitch){const X=VRX,cx=X.cx,cy=X.cy;
  const rd=(-roll*180/Math.PI).toFixed(2),py=(pitch*600).toFixed(1);
  X.lad.setAttribute('transform',`rotate(${rd} ${cx} ${cy}) translate(0 ${py})`);
  X.bank.setAttribute('transform',`rotate(${rd} ${cx} ${cy})`);
  X.fpm.setAttribute('transform',`translate(${(steer[0]*14).toFixed(1)} ${(-steer[1]*10).toFixed(1)})`);
  let hd=FLY.hdg;if(hd>180)hd-=360;X.hdg.setAttribute('transform',`translate(${(-hd*4).toFixed(1)} 0)`);
  X.spd.setAttribute('transform',`translate(0 ${(FLY.spd*2).toFixed(1)})`);X.alt.setAttribute('transform',`translate(0 ${(FLY.alt*.4).toFixed(1)})`);
  if(frameN%3===0){X.hv.textContent=String(Math.round(FLY.hdg)%360).padStart(3,'0');X.sv.textContent=String(Math.round(FLY.spd)).padStart(3,'0');X.av.textContent=String(Math.round(FLY.alt)).padStart(5,'0');X.pv.textContent='±'+FLY.prec.toFixed(1)+'°';X.gv.textContent=FLY.g.toFixed(1);}
}

/* =========================== fallback =========================== */
function fallback(){
  document.documentElement.classList.add('nogl');document.body.classList.add('nogl');
  const segs=CRAFT.segs;const views=[{f:p=>[p[0],-p[1]],oy:-30},{f:p=>[p[0],p[2]],oy:40},{f:p=>[p[2]-.1,-p[1]],oy:105}];
  let s='<svg viewBox="-70 -40 140 160" xmlns="http://www.w3.org/2000/svg"><g stroke="#fff" stroke-width=".18" fill="none">';
  const k=10;views.forEach(v=>{segs.forEach(([a,b])=>{const A=v.f(a),B_=v.f(b);s+=`<path d="M${(A[0]*k).toFixed(2)} ${(A[1]*k+v.oy).toFixed(2)}L${(B_[0]*k).toFixed(2)} ${(B_[1]*k+v.oy).toFixed(2)}"/>`;});});
  s+='</g></svg>';$('#fb').innerHTML=s;
  $('#scrim2').style.opacity=.6;spanBarAll();
  addEventListener('scroll',()=>{const ho=1-Math.min(1,scrollY/(innerHeight*.4));const h=document.getElementById('heroIn');if(h)h.style.opacity=ho;},{passive:true});
}
function spanBarAll(){$$('#spanBar i').forEach(el=>el.classList.add('on'));const n=$('#spanN');if(n)n.textContent='08';}

/* =========================== start =========================== */
cv.addEventListener('webglcontextlost',e=>{e.preventDefault();fallback();});
resize();readScroll();G.p=G.pT;
if(document.fonts&&document.fonts.ready)document.fonts.ready.then(()=>{measure();readScroll();for(const el of [...gateEls,...lockEls,...pylEls,...destEls,...yrEls])el._hw=undefined;});
setTimeout(()=>{measure();readScroll();},600);
document.addEventListener('visibilitychange',()=>{lastT=performance.now();need=true;});
requestAnimationFrame(frame);
})();
</script>
</body>
</html>
