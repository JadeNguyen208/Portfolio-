# Portfolio-
<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jade Nguyen – Portfolio 2026</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,400;1,600;1,700&family=Cormorant+SC:wght@400;500;600;700&family=Jost:wght@300;400;500;600;700;800&display=swap');
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{font-family:'Jost',sans-serif;background:#000;color:#fff;overflow-x:hidden}
:root{--gold:#f7d44c;--gold-dim:rgba(247,212,76,0.7);--gold-line:rgba(247,212,76,0.18);--white:#fff;--wb:rgba(255,255,255,0.88);--ws:rgba(255,255,255,0.65)}
.label{font-family:'Cormorant SC',serif;font-size:11px;letter-spacing:6px;text-transform:uppercase;color:var(--gold-dim);margin-bottom:14px;font-weight:700}
.divider{width:100%;height:1px;background:linear-gradient(90deg,transparent,var(--gold-line),transparent)}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:16px 52px;display:flex;justify-content:space-between;align-items:center;background:rgba(0,0,0,0.9);backdrop-filter:blur(18px);border-bottom:1px solid rgba(247,212,76,0.1)}
.nav-logo{font-family:‘Cormorant SC’,serif;font-size:13px;letter-spacing:5px;color:var(–gold);font-weight:700;line-height:1.5;border:1px solid rgba(247,212,76,0.3);padding:5px 14px;margin-right:20px}
.nav-links{display:flex;gap:28px;align-items:center}
.nav-links a{font-size:10px;letter-spacing:4px;text-transform:uppercase;color:rgba(255,255,255,0.6);text-decoration:none;transition:color .2s;font-weight:500}
.nav-links a:hover{color:var(–gold)}
.nav-pdf{font-size:10px;letter-spacing:3px;text-transform:uppercase;color:var(–gold);border:1px solid rgba(247,212,76,0.45);padding:7px 18px;background:none;font-family:‘Jost’,sans-serif;font-weight:700;cursor:pointer;transition:all .2s}
.nav-pdf:hover{background:rgba(247,212,76,0.1)}

/* HERO */
#hero{position:relative;height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;overflow:hidden;background:#000}
#c1{position:absolute;inset:0;width:100%;height:100%}
.hero-inner{position:relative;z-index:2;display:flex;flex-direction:column;align-items:center}
.hero-badge{display:inline-block;font-family:‘Cormorant SC’,serif;font-size:13px;letter-spacing:6px;color:rgba(247,212,76,0.95);border:1px solid rgba(247,212,76,0.5);padding:9px 28px;margin-bottom:40px;font-weight:700;background:rgba(247,212,76,0.05)}
.hero-j1{font-family:‘Cormorant Garamond’,serif;font-size:clamp(46px,7.5vw,90px);font-weight:700;letter-spacing:4px;color:var(–white);line-height:1;white-space:nowrap;display:block}
.hero-j2{font-family:‘Cormorant Garamond’,serif;font-size:clamp(36px,5.8vw,68px);font-weight:400;font-style:italic;letter-spacing:3px;color:var(–gold);line-height:1.15;margin-top:8px;white-space:nowrap;display:block}
.hero-line{width:60px;height:1px;background:linear-gradient(90deg,transparent,rgba(247,212,76,0.7),transparent);margin:28px auto}
.hero-name{font-family:‘Cormorant SC’,serif;font-size:28px;letter-spacing:10px;color:rgba(255,255,255,0.92);font-weight:600;display:block}
.scroll-hint{position:absolute;bottom:40px;left:50%;transform:translateX(-50%);font-family:‘Cormorant SC’,serif;font-size:9px;letter-spacing:4px;color:rgba(247,212,76,0.3);display:flex;flex-direction:column;align-items:center;gap:10px;font-weight:600;z-index:2}
.scroll-hint::after{content:’’;width:1px;height:36px;background:linear-gradient(180deg,rgba(247,212,76,0.5),transparent)}

section{padding:110px 0}
.container{max-width:1020px;margin:0 auto;padding:0 52px}

/* ABOUT */
#about{background:#000;position:relative;overflow:hidden}
#about::before{content:’’;position:absolute;top:-10%;right:-5%;width:700px;height:700px;background:radial-gradient(circle,rgba(247,212,76,0.04),transparent 65%);pointer-events:none}

/* heading row: h2 left + snippet right */
.about-head{display:grid;grid-template-columns:1fr auto;gap:40px;align-items:center;margin-bottom:32px}
.about-head h2{font-family:‘Cormorant Garamond’,serif;font-size:clamp(44px,5vw,66px);font-weight:700;line-height:1.1;color:var(–white);white-space:nowrap}
.about-head h2 em{color:var(–gold);font-style:italic}
.about-snippet{font-family:‘Courier New’,monospace;font-size:13px;line-height:2;background:#0d0d0d;border:1px solid rgba(247,212,76,0.15);border-left:2px solid var(–gold);padding:18px 22px;white-space:nowrap}
.sn-cm{color:rgba(247,212,76,0.45);display:block}
.sn-k{color:#c792ea}.sn-v{color:#f7d44c}.sn-s{color:#c3e88d}.sn-d{color:rgba(255,255,255,0.3)}.sn-w{color:rgba(255,255,255,0.8)}

/* typewriter window */
.code-window{background:#0d0d0d;border:1px solid rgba(247,212,76,0.15);border-radius:10px;overflow:hidden;box-shadow:0 24px 80px rgba(0,0,0,0.7);margin-bottom:32px}
.code-titlebar{background:#181818;padding:10px 16px;display:flex;align-items:center;gap:8px;border-bottom:1px solid rgba(255,255,255,0.05)}
.code-dot{width:10px;height:10px;border-radius:50%}
.code-dot.r{background:#ff5f57}.code-dot.y{background:#febc2e}.code-dot.g{background:#28c840}
.code-filename{font-size:11px;color:rgba(255,255,255,0.3);margin-left:8px;letter-spacing:1px;font-family:‘Jost’,sans-serif}
.code-body{padding:20px 24px;font-family:‘Courier New’,monospace;font-size:13px;line-height:1.85;min-height:160px}
.cursor{display:inline-block;width:2px;height:14px;background:var(–gold);vertical-align:middle;margin-left:1px;animation:blink .9s step-end infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}

/* 2x2 cards */
.acards{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:0}
.acard{padding:20px 24px;border:1px solid rgba(247,212,76,0.1);border-left:2px solid rgba(247,212,76,0.65);background:rgba(247,212,76,0.02)}
.acard h4{font-family:‘Cormorant SC’,serif;font-size:11px;letter-spacing:4px;color:var(–gold);margin-bottom:8px;font-weight:700}
.acard p{font-size:14px;color:var(–wb);line-height:1.75;font-weight:400}
.acard ul{list-style:none;display:flex;flex-direction:column;gap:5px}
.acard ul li{font-size:13px;color:var(–wb);padding-left:16px;position:relative;line-height:1.6}
.acard ul li::before{content:’·’;position:absolute;left:4px;color:var(–gold);font-size:16px;top:-2px}

/* numbers */
.about-nums{display:flex;gap:52px;padding-top:32px;border-top:1px solid rgba(247,212,76,0.08)}
.num-item .v{font-family:‘Cormorant Garamond’,serif;font-size:52px;font-weight:700;line-height:1;color:#fff}
.num-item .l{font-size:10px;letter-spacing:4px;text-transform:uppercase;color:var(–ws);margin-top:5px;font-weight:500}

/* OFFER */
#offer{background:#000}
#offer h2{font-family:‘Cormorant Garamond’,serif;font-size:54px;font-weight:700;margin-bottom:40px;color:var(–white);letter-spacing:1px}
#offer h2 em{color:var(–gold);font-style:italic}
.offer-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:rgba(247,212,76,0.08)}
.ocard{background:#000;padding:28px 24px;position:relative;overflow:hidden;transition:background .3s}
.ocard:hover{background:rgba(247,212,76,0.03)}
.ocard::after{content:’’;position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,var(–gold),rgba(247,212,76,0.15),transparent)}
.ocard .ico{font-size:24px;margin-bottom:14px}
.ocard h4{font-family:‘Cormorant SC’,serif;font-size:13px;letter-spacing:2px;color:var(–gold);margin-bottom:10px;font-weight:700}
.ocard p{font-size:13px;color:var(–wb);line-height:1.75}
.ocard ul{list-style:none;margin-top:14px;display:flex;flex-direction:column;gap:7px}
.ocard ul li{font-size:13px;color:rgba(255,255,255,0.7);padding-left:14px;position:relative;line-height:1.5}
.ocard ul li::before{content:’—’;position:absolute;left:0;color:rgba(247,212,76,0.6);font-size:9px;top:3px}

/* PROJECT */
#project{background:#000}
.project-grid{display:grid;grid-template-columns:1fr 1fr;gap:64px;align-items:center}
.project-left h2{font-family:‘Cormorant Garamond’,serif;font-size:72px;font-weight:700;line-height:.92;margin-bottom:10px;color:var(–white);letter-spacing:2px}
.project-left h2 span{display:block;font-style:italic;color:var(–gold)}
.project-url{font-size:11px;color:var(–ws);margin-bottom:32px;letter-spacing:2px}
.ux-pts{display:flex;flex-direction:column;gap:16px}
.ux-pt{display:flex;gap:16px;align-items:flex-start}
.ux-n{font-family:‘Cormorant Garamond’,serif;font-size:12px;font-weight:700;color:rgba(247,212,76,0.65);min-width:22px;padding-top:1px;letter-spacing:1px}
.ux-t h4{font-size:15px;font-weight:700;color:var(–white);margin-bottom:3px}
.ux-t p{font-size:13px;color:var(–ws);line-height:1.65}
.phone{width:210px;margin:0 auto}
.pframe{background:#050500;border:1px solid rgba(247,212,76,0.18);border-radius:28px;overflow:hidden;box-shadow:0 40px 120px rgba(0,0,0,.95)}
.pnotch{height:22px;background:#000;display:flex;align-items:center;justify-content:center}
.pnotch-pill{width:60px;height:5px;background:#0a0a00;border-radius:3px}
.pscreen{background:radial-gradient(ellipse at 40% 90%,#2d1400,#060400 55%,#000);position:relative;overflow:hidden;padding-bottom:14px}
.pscreen canvas{position:absolute;inset:0}
.pui{position:relative;z-index:2;padding:10px 10px 0}
.pnav{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px}
.plogo{font-family:‘Cormorant SC’,serif;font-size:11px;font-weight:700;color:var(–gold);letter-spacing:3px}
.ppro{font-size:7px;padding:2px 7px;background:var(–gold);color:#000;font-weight:800;letter-spacing:1px}
.pmodes{display:flex;gap:3px;margin-bottom:8px;flex-wrap:wrap}
.pmode{font-size:7px;padding:3px 7px;border:1px solid rgba(247,212,76,0.12);color:rgba(247,212,76,0.45)}
.pmode.on{background:rgba(247,212,76,0.12);border-color:rgba(247,212,76,0.55);color:var(–gold);font-weight:700}
.pgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:4px}
.pcard{background:rgba(15,10,0,0.8);border:1px solid rgba(247,212,76,0.07);padding:9px 3px;text-align:center}
.pcard.glow{border-color:rgba(247,212,76,0.5);background:rgba(247,212,76,0.08);box-shadow:0 0 14px rgba(247,212,76,0.14)}
.pcard .e{font-size:17px;margin-bottom:3px}
.pcard .n{font-size:7px;color:rgba(255,255,255,0.6)}
.pcard.glow .n{color:var(–gold)}
.pbar{margin:8px 10px 0;background:rgba(247,212,76,0.06);border:1px solid rgba(247,212,76,0.18);padding:5px;text-align:center;font-size:7px;color:rgba(247,212,76,0.85);letter-spacing:.5px}

/* UX */
#ux{background:#000}
#ux h2{font-family:‘Cormorant Garamond’,serif;font-size:52px;font-weight:700;margin-bottom:36px;color:var(–white)}
#ux h2 em{color:var(–gold);font-style:italic}
.ux-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:rgba(247,212,76,0.08)}
.ux-card{background:#000;padding:28px 24px;position:relative;transition:background .3s}
.ux-card:hover{background:rgba(247,212,76,0.025)}
.ux-card::before{content:’’;position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,var(–gold),transparent)}
.ux-card .ico{font-size:22px;margin-bottom:14px}
.ux-card h4{font-family:‘Cormorant SC’,serif;font-size:13px;letter-spacing:2px;color:var(–gold);margin-bottom:8px;font-weight:700}
.ux-card p{font-size:13px;color:var(–wb);line-height:1.75}
.tags{display:flex;flex-wrap:wrap;gap:5px;margin-top:10px}
.tag{font-size:9px;padding:3px 9px;border:1px solid rgba(247,212,76,0.3);color:rgba(247,212,76,0.75);letter-spacing:1px;font-weight:500}

/* SKILLS */
#skills{background:#000}
.skills-layout{display:grid;grid-template-columns:1fr 1fr;gap:64px;align-items:start}
.skills-left h2{font-family:‘Cormorant Garamond’,serif;font-size:52px;font-weight:700;line-height:1.05;margin-bottom:10px;color:var(–white)}
.skills-left h2 em{color:var(–gold);font-style:italic}
.skills-left .sub{font-size:14px;color:var(–wb);margin-bottom:32px;line-height:1.8}
.media-list{display:flex;flex-direction:column;gap:1px;background:rgba(247,212,76,0.08)}
.mitem{display:flex;gap:16px;align-items:flex-start;padding:16px 18px;background:#000;transition:background .3s}
.mitem:hover{background:rgba(247,212,76,0.025)}
.mitem .mi{font-size:20px;min-width:28px}
.mitem h4{font-family:‘Cormorant SC’,serif;font-size:12px;letter-spacing:2px;color:var(–gold);margin-bottom:5px;font-weight:700}
.mitem p{font-size:13px;color:var(–wb);line-height:1.65}
.skills-right{display:flex;flex-direction:column;gap:24px}
.sg h4{font-family:‘Cormorant SC’,serif;font-size:10px;letter-spacing:4px;color:var(–gold-dim);margin-bottom:12px;font-weight:700}
.chips{display:flex;flex-wrap:wrap;gap:6px}
.chip{font-size:11px;padding:5px 14px;border:1px solid rgba(247,212,76,0.35);color:var(–gold);background:rgba(247,212,76,0.04);font-weight:500;letter-spacing:0.8px}
.chip.g{border-color:rgba(247,212,76,0.65);background:rgba(247,212,76,0.1);font-weight:700}

/* CTA */
#cta{position:relative;overflow:hidden;min-height:65vh;display:flex;align-items:center;justify-content:center;text-align:center;background:#000;padding:80px 0}
#c7{position:absolute;inset:0;width:100%;height:100%}
.cta-inner{position:relative;z-index:2}
.cta-inner h2{font-family:‘Cormorant Garamond’,serif;font-size:96px;font-weight:700;line-height:.9;margin-bottom:28px;color:var(–white);letter-spacing:3px}
.cta-inner h2 span{display:block;font-style:italic;color:var(–gold)}
.cta-line{width:80px;height:1px;background:linear-gradient(90deg,transparent,rgba(247,212,76,0.75),transparent);margin:0 auto 28px}
.cta-sub{font-size:10px;letter-spacing:6px;text-transform:uppercase;color:var(–ws);margin-bottom:48px;font-weight:500}
.cta-row{display:flex;gap:1px;justify-content:center;flex-wrap:wrap;background:rgba(247,212,76,0.09)}
.cta-card{padding:22px 32px;background:#000;min-width:170px;transition:background .3s}
.cta-card:hover{background:rgba(247,212,76,0.03)}
.cta-card .cl{font-family:‘Cormorant SC’,serif;font-size:9px;letter-spacing:4px;color:var(–gold-dim);margin-bottom:8px;font-weight:700}
.cta-card .cv{font-size:14px;color:var(–white);font-weight:500}

.reveal{opacity:0;transform:translateY(30px);transition:opacity .8s cubic-bezier(.22,1,.36,1),transform .8s cubic-bezier(.22,1,.36,1)}
.reveal.visible{opacity:1;transform:none}
.reveal-slow{opacity:0;transform:translateY(20px);transition:opacity 1.1s cubic-bezier(.22,1,.36,1) .15s,transform 1.1s cubic-bezier(.22,1,.36,1) .15s}
.reveal-slow.visible{opacity:1;transform:none}

@media print{
nav,.scroll-hint,#c1,#c7,#bokeh{display:none!important}
*{-webkit-print-color-adjust:exact!important;print-color-adjust:exact!important}
body{background:#000!important}
section{padding:40px 0;break-inside:avoid}
.container{padding:0 32px}
.reveal,.reveal-slow{opacity:1!important;transform:none!important}
#hero{height:auto;padding:60px 0 40px;display:block;text-align:center}
.offer-grid,.ux-grid,.acards{grid-template-columns:repeat(2,1fr)!important}
canvas{display:none!important}
}
</style>

</head>
<body>

<nav>
  <div class="nav-logo">Jade<br>Nguyen</div>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#offer">Services</a>
    <a href="#project">Project</a>
    <a href="#skills">Skills</a>
    <a href="#cta">Contact</a>
    <button class="nav-pdf" onclick="window.print()">↓ Save PDF</button>
  </div>
</nav>

<!-- HERO -->

<section id="hero">
  <canvas id="c1"></canvas>
  <div class="hero-inner">
    <div class="hero-badge">Portfolio &nbsp;·&nbsp; 2026</div>
    <span class="hero-j1">Digital Designer</span>
    <span class="hero-j2">Frontend Web Developer</span>
    <div class="hero-line"></div>
    <span class="hero-name">Jade Nguyen</span>
  </div>
  <div class="scroll-hint">scroll</div>
</section>

<div class="divider"></div>

<!-- ABOUT -->

<section id="about">
  <div class="container">
    <div class="label reveal">About</div>

```
<!-- heading + snippet side by side -->
<div class="about-head reveal">
  <h2>Design that <em>works.</em><br>Code that <em>ships.</em></h2>
  <div class="about-snippet">
    <span class="sn-cm">// what I build</span>
    <span><span class="sn-k">const</span> <span class="sn-w">output</span> <span class="sn-d">=</span> <span class="sn-d">{</span></span>
    <span>&nbsp;&nbsp;<span class="sn-v">design</span><span class="sn-d">:</span> <span class="sn-s">"pixel-perfect"</span><span class="sn-d">,</span></span>
    <span>&nbsp;&nbsp;<span class="sn-v">code</span><span class="sn-d">:</span> <span class="sn-s">"ships on time"</span><span class="sn-d">,</span></span>
    <span>&nbsp;&nbsp;<span class="sn-v">deploy</span><span class="sn-d">:</span> <span class="sn-k">() =&gt;</span> <span class="sn-s">"live"</span></span>
    <span><span class="sn-d">};</span></span>
  </div>
</div>

<!-- typewriter code window -->
<div class="code-window reveal">
  <div class="code-titlebar">
    <div class="code-dot r"></div><div class="code-dot y"></div><div class="code-dot g"></div>
    <span class="code-filename">jade-nguyen.js</span>
  </div>
  <div class="code-body" id="codeBody"></div>
</div>

<!-- 2x2 cards -->
<div class="acards reveal-slow">
  <div class="acard">
    <h4>Background</h4>
    <ul>
      <li>BSc Digital Marketing Management</li>
      <li>Cardiff Metropolitan University, Cardiff, Wales, UK</li>
      <li>CS50x Computer Science — Harvard University (edX)</li>
    </ul>
  </div>
  <div class="acard"><h4>What I Do</h4><p>Layout, visual design, HTML/CSS/JS, WordPress, and digital content — concept to launch, independently.</p></div>
  <div class="acard"><h4>How I Work</h4><p>Comfortable solo or coordinating design and media teams. I manage timelines, align visuals with brand, and deliver on time.</p></div>
  <div class="acard"><h4>Open To</h4><p>Open for remote working. Flexible with time zones. Available for full-time roles in web design &amp; frontend dev.</p></div>
</div>

<!-- numbers -->
<div class="about-nums reveal">
  <div class="num-item"><div class="v">3<span style="font-weight:300">+</span></div><div class="l">Years</div></div>
  <div class="num-item"><div class="v">40<span style="font-weight:300">+</span></div><div class="l">Sounds Built</div></div>
  <div class="num-item"><div class="v">5</div><div class="l">Languages</div></div>
</div>
```

  </div>
</section>

<div class="divider"></div>

<!-- OFFER -->

<section id="offer">
  <div class="container">
    <div class="label reveal">Services</div>
    <h2 class="reveal">What I can do <em>for you</em></h2>
    <div class="offer-grid reveal">
      <div class="ocard"><div class="ico">🌐</div><h4>Web Design &amp; Build</h4><p>From landing pages to full web apps — responsive, fast, and on-brand.</p><ul><li>HTML/CSS/JS from scratch</li><li>WordPress design &amp; setup</li><li>Webflow &amp; Framer sites</li><li>Cross-browser compatible</li></ul></div>
      <div class="ocard"><div class="ico">🎨</div><h4>Visual &amp; Digital Design</h4><p>Graphic assets, social media visuals, ads, and brand-consistent UI.</p><ul><li>Social media graphics</li><li>Digital ad creatives</li><li>Landing page layouts</li><li>UI components &amp; icons</li></ul></div>
      <div class="ocard"><div class="ico">🎬</div><h4>Motion &amp; Video Content</h4><p>Promotional video, motion graphics, and short-form content for social.</p><ul><li>After Effects animations</li><li>CapCut video editing</li><li>AI-generated video (Veo 3, Kling)</li><li>Product launch content</li></ul></div>
      <div class="ocard"><div class="ico">⚡</div><h4>Interactive UX</h4><p>Engaging web experiences with animation, sound, and real-time effects.</p><ul><li>Canvas API animations</li><li>Web Audio integration</li><li>Smooth micro-interactions</li><li>Multi-language support</li></ul></div>
      <div class="ocard"><div class="ico">🤖</div><h4>AI-Powered Workflows</h4><p>Using AI tools to produce more, faster — without losing creative direction.</p><ul><li>AI image gen (Nano Banana Pro)</li><li>AI video (Veo 3, Kling, Whisk)</li><li>Rapid prototyping &amp; ideation</li><li>AI-assisted copywriting</li></ul></div>
      <div class="ocard"><div class="ico">📊</div><h4>Digital Marketing</h4><p>BSc-level background in marketing — aligning content with business goals.</p><ul><li>On-page SEO basics</li><li>Product Hunt launches</li><li>Social media strategy</li><li>Content planning</li></ul></div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- PROJECT -->

<section id="project">
  <div class="container">
    <div class="label reveal">Featured Project</div>
    <div class="project-grid">
      <div class="reveal">
        <h2>Sleep<br>Sound<br><span>Mixer</span></h2>
        <div class="project-url">jadenguyen208.github.io/SleepSoundMixer</div>
        <div class="ux-pts">
          <div class="ux-pt"><div class="ux-n">01</div><div class="ux-t"><h4>Full UX Ownership</h4><p>Every screen, flow &amp; interaction designed from scratch</p></div></div>
          <div class="ux-pt"><div class="ux-n">02</div><div class="ux-t"><h4>Real-time 3D Animations</h4><p>Rain, fire, aurora &amp; fog — HTML5 Canvas, no library</p></div></div>
          <div class="ux-pt"><div class="ux-n">03</div><div class="ux-t"><h4>5-language UI</h4><p>EN/VI/ZH/FR/DE — seamless switching from scratch</p></div></div>
          <div class="ux-pt"><div class="ux-n">04</div><div class="ux-t"><h4>Shipped to Real Users</h4><p>Launched on Product Hunt with social &amp; promo content</p></div></div>
          <div class="ux-pt"><div class="ux-n">05</div><div class="ux-t"><h4>Monetised</h4><p>3-tier commercial licensing, PayPal integration</p></div></div>
        </div>
      </div>
      <div class="reveal-slow">
        <div class="phone">
          <div class="pframe">
            <div class="pnotch"><div class="pnotch-pill"></div></div>
            <div class="pscreen">
              <canvas id="bokeh"></canvas>
              <div class="pui">
                <div class="pnav"><span class="plogo">SSM</span><span class="ppro">PRO</span></div>
                <div class="pmodes">
                  <div class="pmode on">😴 Sleep</div><div class="pmode">🧘 Meditate</div><div class="pmode">📚 Focus</div><div class="pmode">✨ AI</div>
                </div>
                <div class="pgrid">
                  <div class="pcard glow"><div class="e">🔥</div><div class="n">Fireplace</div></div>
                  <div class="pcard"><div class="e">🌧</div><div class="n">Rain</div></div>
                  <div class="pcard"><div class="e">🌊</div><div class="n">Ocean</div></div>
                  <div class="pcard"><div class="e">🌲</div><div class="n">Forest</div></div>
                  <div class="pcard glow"><div class="e">🌬</div><div class="n">Wind</div></div>
                  <div class="pcard"><div class="e">☕</div><div class="n">Café</div></div>
                  <div class="pcard"><div class="e">〰️</div><div class="n">White</div></div>
                  <div class="pcard"><div class="e">🟤</div><div class="n">Brown</div></div>
                  <div class="pcard"><div class="e">⛈</div><div class="n">Thunder</div></div>
                </div>
                <div class="pbar">● 1 hour free daily · No sign-up</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- UX -->

<section id="ux">
  <div class="container">
    <div class="label reveal">UX Deep Dive</div>
    <h2 class="reveal">SleepSoundMixer — <em>UX breakdown</em></h2>
    <div class="ux-grid reveal">
      <div class="ux-card"><div class="ico">🎨</div><h4>Design System</h4><p>Dark luxury aesthetic, gold accent (#c9a84c), consistent type &amp; spacing across all 4 modes.</p><div class="tags"><span class="tag">CSS3</span><span class="tag">Custom tokens</span></div></div>
      <div class="ux-card"><div class="ico">✨</div><h4>3D Canvas FX</h4><p>Aurora, fog, rain, fire — all real-time on HTML5 Canvas. Zero libraries. Mode-specific.</p><div class="tags"><span class="tag">Canvas API</span><span class="tag">Vanilla JS</span></div></div>
      <div class="ux-card"><div class="ico">📱</div><h4>Responsive</h4><p>Mobile-first, fully responsive. Optimised touch interactions and accessible controls.</p><div class="tags"><span class="tag">Mobile-first</span><span class="tag">CSS Grid</span></div></div>
      <div class="ux-card"><div class="ico">🧘</div><h4>Wellness UX</h4><p>4-7-8 breathing, Pomodoro timer, sleep fade-out. Calm, distraction-free interactions.</p><div class="tags"><span class="tag">Interaction design</span></div></div>
      <div class="ux-card"><div class="ico">🌍</div><h4>i18n — 5 Languages</h4><p>EN/VI/ZH/FR/DE with seamless switching. No library — built from scratch in Vanilla JS.</p><div class="tags"><span class="tag">i18n</span><span class="tag">Vanilla JS</span></div></div>
      <div class="ux-card"><div class="ico">💰</div><h4>Conversion Design</h4><p>Landing page, 3-tier pricing, stats, social proof, PayPal integration — free-to-paid flow.</p><div class="tags"><span class="tag">Landing page</span><span class="tag">PayPal API</span></div></div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- SKILLS -->

<section id="skills">
  <div class="container">
    <div class="label reveal">Tools &amp; Media</div>
    <div class="skills-layout">
      <div>
        <h2 class="reveal">Motion &amp;<br><em>Visual Work</em></h2>
        <p class="sub reveal">Creating content that moves — for social, product, and brand</p>
        <div class="media-list reveal">
          <div class="mitem"><div class="mi">🎬</div><div><h4>Promotional Video</h4><p>CapCut — short-form product videos and social ads, editing, pacing, captions, music sync</p></div></div>
          <div class="mitem"><div class="mi">✨</div><div><h4>Motion Graphics</h4><p>After Effects — animated intros, transitions, and visual effects for digital campaigns</p></div></div>
          <div class="mitem"><div class="mi">🤖</div><div><h4>AI Video Generation</h4><p>Veo 3, Kling, Whisk — producing cinematic visuals fast for content pipelines</p></div></div>
          <div class="mitem"><div class="mi">🍌</div><div><h4>AI Image Editing</h4><p>Nano Banana Pro — conversational image editing, character consistency, campaign visuals at speed</p></div></div>
          <div class="mitem"><div class="mi">🎨</div><div><h4>Graphic Design</h4><p>Canva Advanced — social posts, ad banners, thumbnails, brand-consistent and production-ready</p></div></div>
        </div>
      </div>
      <div class="skills-right reveal-slow">
        <div class="sg"><h4>Development</h4><div class="chips"><span class="chip g">HTML5</span><span class="chip g">CSS3</span><span class="chip g">JavaScript</span><span class="chip g">WordPress</span><span class="chip">Canvas API</span><span class="chip">Web Audio API</span><span class="chip">Git</span><span class="chip">Vercel</span></div></div>
        <div class="sg"><h4>Design &amp; Motion</h4><div class="chips"><span class="chip g">Canva</span><span class="chip g">After Effects</span><span class="chip g">CapCut</span><span class="chip">Figma</span><span class="chip">Framer</span><span class="chip">Webflow</span></div></div>
        <div class="sg"><h4>AI Tools</h4><div class="chips"><span class="chip g">Nano Banana Pro</span><span class="chip">Veo 3</span><span class="chip">Whisk</span><span class="chip">Kling</span><span class="chip">Claude</span><span class="chip">ChatGPT</span></div></div>
        <div class="sg"><h4>Languages</h4><div class="chips"><span class="chip g">Vietnamese</span><span class="chip g">English</span><span class="chip">German A1</span><span class="chip">French</span><span class="chip">Mandarin</span></div></div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- CTA -->

<section id="cta">
  <canvas id="c7"></canvas>
  <div class="cta-inner">
    <div class="label" style="text-align:center;margin-bottom:24px">Let's work together</div>
    <h2>Ready to<span>contribute.</span></h2>
    <div class="cta-line"></div>
    <div class="cta-sub">Remote &nbsp;·&nbsp; Full-time &nbsp;·&nbsp; Vietnam UTC+7</div>
    <div class="cta-row">
      <div class="cta-card"><div class="cl">Live Portfolio</div><div class="cv">jadenguyen208.github.io</div></div>
      <div class="cta-card"><div class="cl">Education</div><div class="cv">Cardiff, Wales, UK</div></div>
      <div class="cta-card"><div class="cl">English</div><div class="cv">Professional Level</div></div>
      <div class="cta-card"><div class="cl">Availability</div><div class="cv">Full-time Remote</div></div>
    </div>
  </div>
</section>

<script>
// scroll reveal
var revEls = document.querySelectorAll('.reveal,.reveal-slow');
var revObs = new IntersectionObserver(function(entries){
  entries.forEach(function(e){
    if(e.isIntersecting){ e.target.classList.add('visible'); revObs.unobserve(e.target); }
  });
},{threshold:0.1});
revEls.forEach(function(el){ revObs.observe(el); });

// particles
function particles(canvas, n, opts){
  opts = opts || {};
  var ctx = canvas.getContext('2d');
  function resize(){ canvas.width = canvas.offsetWidth || window.innerWidth; canvas.height = canvas.offsetHeight || window.innerHeight; }
  resize();
  window.addEventListener('resize', resize);
  var pts = [];
  for(var i=0;i<n;i++) pts.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*(opts.mr||1.3)+.3,vx:(Math.random()-.5)*(opts.sp||.3),vy:(Math.random()-.5)*(opts.sp||.3)});
  function draw(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    pts.forEach(function(p){
      p.x+=p.vx; p.y+=p.vy;
      if(p.x<0||p.x>canvas.width) p.vx*=-1;
      if(p.y<0||p.y>canvas.height) p.vy*=-1;
      ctx.beginPath(); ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle='rgba(247,212,76,0.65)'; ctx.fill();
    });
    if(opts.lines) pts.forEach(function(a,ai){ pts.forEach(function(b,bi){ if(bi<=ai) return; var d=Math.hypot(a.x-b.x,a.y-b.y); if(d<140){ ctx.beginPath(); ctx.moveTo(a.x,a.y); ctx.lineTo(b.x,b.y); ctx.strokeStyle='rgba(247,212,76,'+(0.1*(1-d/140))+')'; ctx.lineWidth=.5; ctx.stroke(); }}); });
    requestAnimationFrame(draw);
  }
  draw();
}
setTimeout(function(){
  particles(document.getElementById('c1'),70,{lines:true,sp:.28});
  particles(document.getElementById('c7'),55,{lines:true,sp:.22});
},100);

// bokeh
var bk = document.getElementById('bokeh');
if(bk){
  var bc = bk.getContext('2d'); bk.width=210; bk.height=320;
  var orbs=[];
  for(var i=0;i<14;i++) orbs.push({x:Math.random()*210,y:Math.random()*320,r:Math.random()*26+6,ox:Math.random()*Math.PI*2,oy:Math.random()*Math.PI*2,sp:Math.random()*.005+.002,warm:Math.random()>.4});
  function db(){
    bc.clearRect(0,0,210,320);
    orbs.forEach(function(o){
      o.ox+=o.sp; o.oy+=o.sp*.65;
      var x=o.x+Math.sin(o.ox)*20, y=o.y+Math.cos(o.oy)*15;
      var g=bc.createRadialGradient(x,y,0,x,y,o.r);
      var c=o.warm?'rgba(200,100,10,':'rgba(247,212,76,';
      g.addColorStop(0,c+'0.28)'); g.addColorStop(1,c+'0)');
      bc.beginPath(); bc.arc(x,y,o.r,0,Math.PI*2); bc.fillStyle=g; bc.fill();
    });
    requestAnimationFrame(db);
  }
  db();
}

// typewriter
var codeLines = [
  '<span style="color:rgba(247,212,76,0.5)">// jade-nguyen · creative developer</span>',
  '<span style="color:#c792ea">const</span> <span style="color:rgba(255,255,255,0.85)">jade</span> <span style="color:rgba(255,255,255,0.3)">=</span> <span style="color:rgba(255,255,255,0.3)">{</span>',
  '&nbsp;&nbsp;<span style="color:#f7d44c">role</span><span style="color:rgba(255,255,255,0.3)">:</span> <span style="color:#c3e88d">"Digital Designer &amp; Frontend Dev"</span><span style="color:rgba(255,255,255,0.3)">,</span>',
  '&nbsp;&nbsp;<span style="color:#f7d44c">based</span><span style="color:rgba(255,255,255,0.3)">:</span> <span style="color:#c3e88d">"Cardiff, Wales, UK"</span><span style="color:rgba(255,255,255,0.3)">,</span>',
  '&nbsp;&nbsp;<span style="color:#f7d44c">skills</span><span style="color:rgba(255,255,255,0.3)">:</span> <span style="color:rgba(255,255,255,0.3)">[</span><span style="color:#c3e88d">"HTML/CSS/JS"</span><span style="color:rgba(255,255,255,0.3)">,</span> <span style="color:#c3e88d">"Canvas API"</span><span style="color:rgba(255,255,255,0.3)">,</span> <span style="color:#c3e88d">"Web Audio"</span><span style="color:rgba(255,255,255,0.3)">],</span>',
  '&nbsp;&nbsp;<span style="color:#f7d44c">available</span><span style="color:rgba(255,255,255,0.3)">:</span> <span style="color:#c792ea">true</span><span style="color:rgba(255,255,255,0.3)">,</span>',
  '&nbsp;&nbsp;<span style="color:#f7d44c">ship</span><span style="color:rgba(255,255,255,0.3)">:</span> <span style="color:rgba(255,255,255,0.3)">() =&gt;</span> <span style="color:#c3e88d">"concept to live product"</span>',
  '<span style="color:rgba(255,255,255,0.3)">};</span>'
];
var cb = document.getElementById('codeBody');
var twStarted = false;
function typeLine(i){
  if(!cb || i >= codeLines.length) return;
  var d = document.createElement('div');
  d.innerHTML = codeLines[i];
  cb.appendChild(d);
  setTimeout(function(){ typeLine(i+1); }, 300);
}
var cw = document.querySelector('.code-window');
if(cw){
  var twObs = new IntersectionObserver(function(entries){
    if(entries[0].isIntersecting && !twStarted){
      twStarted = true;
      setTimeout(function(){ typeLine(0); }, 400);
      twObs.disconnect();
    }
  },{threshold:0.2});
  twObs.observe(cw);
}
</script>

</body>
</html>