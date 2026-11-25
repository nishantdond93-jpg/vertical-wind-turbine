<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#07111f">
<title>VERTEX | Vertical Axis Wind Turbine</title>
<style>
:root{
  --bg:#07111f;--panel:#0d1b2e;--panel2:#10243a;--text:#eef6ff;
  --muted:#a8bbcf;--cyan:#53e0d0;--line:rgba(130,190,220,.22);
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:Inter,Segoe UI,Arial,sans-serif;background:var(--bg);color:var(--text);line-height:1.65}
a{color:inherit;text-decoration:none}
.wrap{width:min(1120px,90%);margin:auto}
header{position:sticky;top:0;z-index:10;background:rgba(7,17,31,.88);backdrop-filter:blur(14px);border-bottom:1px solid var(--line)}
.nav{min-height:76px;display:flex;align-items:center;justify-content:space-between;gap:20px}
.logo{font-weight:900;letter-spacing:2px;font-size:1.35rem;color:var(--cyan)}
nav{display:flex;gap:24px;flex-wrap:wrap}
nav a{font-size:.92rem;color:var(--muted)}
nav a:hover{color:var(--cyan)}
.hero{position:relative;overflow:hidden;padding:105px 0 95px;background:radial-gradient(ellipse at 80% 40%,rgba(20,125,150,.30),transparent 42%),linear-gradient(130deg,#07111f,#0b2135 58%,#092b37)}
.hero-grid{display:grid;grid-template-columns:1.15fr .85fr;align-items:center;gap:50px}
.eyebrow{display:inline-block;color:var(--cyan);border:1px solid rgba(83,224,208,.35);border-radius:30px;padding:7px 13px;font-size:.78rem;letter-spacing:1.4px;text-transform:uppercase;margin-bottom:22px}
h1{font-size:clamp(2.7rem,6vw,5rem);line-height:1.04;letter-spacing:-2px;margin-bottom:22px}
h1 span{color:var(--cyan)}
.hero p{max-width:650px;color:#c2d2e2;font-size:1.08rem}
.actions{display:flex;gap:14px;flex-wrap:wrap;margin-top:30px}
.btn{display:inline-flex;align-items:center;justify-content:center;padding:13px 21px;border-radius:30px;font-weight:750;background:var(--cyan);color:#06202a}
.btn.secondary{background:transparent;border:1px solid var(--line);color:var(--text)}
.visual{min-height:340px;border:1px solid var(--line);border-radius:28px;background:linear-gradient(145deg,rgba(20,65,87,.7),rgba(8,22,38,.65));display:grid;place-items:center;position:relative;overflow:hidden}
.visual:before,.visual:after{content:"";position:absolute;border:1px solid rgba(83,224,208,.18);border-radius:50%;width:300px;height:300px}
.visual:after{width:220px;height:220px}
.turbine{position:relative;width:150px;height:250px;z-index:1}
.turbine .mast{position:absolute;left:73px;top:10px;width:5px;height:225px;background:linear-gradient(#d7f8f3,#4baeb4);border-radius:5px}
.blade{position:absolute;width:52px;height:105px;border:3px solid var(--cyan);background:linear-gradient(145deg,rgba(83,224,208,.25),rgba(83,224,208,.03));border-radius:50% 50% 12px 12px}
.blade.one{left:49px;top:5px;transform:rotate(0deg)}
.blade.two{left:5px;top:85px;transform:rotate(-120deg)}
.blade.three{left:93px;top:85px;transform:rotate(120deg)}
.hub{position:absolute;left:65px;top:116px;width:22px;height:22px;border-radius:50%;background:var(--cyan);box-shadow:0 0 25px var(--cyan)}
.visual-label{position:absolute;bottom:18px;color:#b6d2df;font-size:.8rem;letter-spacing:1.5px}
section{padding:82px 0}
.section-tag{color:var(--cyan);font-size:.78rem;letter-spacing:1.5px;text-transform:uppercase;font-weight:800}
h2{font-size:clamp(2rem,4vw,3rem);line-height:1.15;margin:10px 0 18px}
.lead{max-width:760px;color:var(--muted)}
.two-col{display:grid;grid-template-columns:1fr 1fr;gap:36px;align-items:center}
.panel{background:linear-gradient(145deg,var(--panel2),var(--panel));border:1px solid var(--line);border-radius:22px;padding:28px}
.steps{display:grid;grid-template-columns:repeat(2,1fr);gap:16px;margin-top:30px}
.step,.spec{background:var(--panel);border:1px solid var(--line);border-radius:17px;padding:21px}
.num{color:var(--cyan);font-size:.8rem;font-weight:900;letter-spacing:1px}
.step h3{margin:8px 0;color:var(--text);font-size:1.05rem}
.step p{color:var(--muted);font-size:.94rem}
.specs{display:grid;grid-template-columns:repeat(2,1fr);gap:14px;margin-top:25px}
.spec span{display:block;color:var(--muted);font-size:.75rem;text-transform:uppercase;letter-spacing:1px;margin-bottom:6px}
.spec strong{font-size:1rem}
.note{margin-top:18px;color:var(--muted);font-size:.88rem}
.gallery{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin-top:28px}
.gallery-card{border:1px solid var(--line);background:var(--panel);border-radius:20px;padding:15px}
.gallery-card img{width:100%;height:280px;object-fit:contain;background:#f3f6f8;border-radius:13px;display:block}
.gallery-card h3{margin:14px 4px 4px}
.gallery-card p{margin:0 4px 8px;color:var(--muted);font-size:.9rem}
.file-link{display:inline-block;color:var(--cyan);font-weight:750;margin:10px 4px}
.future{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;margin-top:26px}
.future .panel{padding:23px}
footer{border-top:1px solid var(--line);padding:28px 0;color:var(--muted);text-align:center;font-size:.9rem}
@media(max-width:760px){
 .nav{padding:14px 0;align-items:flex-start;flex-direction:column}
 nav{gap:14px}
 .hero{padding:75px 0}
 .hero-grid,.two-col{grid-template-columns:1fr}
 .visual{min-height:290px}
 .steps,.specs,.gallery,.future{grid-template-columns:1fr}
 section{padding:62px 0}
 .gallery-card img{height:230px}
}
</style>
</head>
<body>
<header>
  <div class="wrap nav">
    <a class="logo" href="#home">VERTEX</a>
    <nav>
      <a href="#overview">Overview</a>
      <a href="#working">How it works</a>
      <a href="#design">Design</a>
      <a href="#gallery">Gallery</a>
      <a href="#future">Future scope</a>
    </nav>
  </div>
</header>

<main>
<section class="hero" id="home">
  <div class="wrap hero-grid">
    <div>
      <div class="eyebrow">Mechanical Engineering Project</div>
      <h1>Engineering a<br><span>Cleaner Tomorrow.</span></h1>
      <p>A student project exploring how a Vertical Axis Wind Turbine can convert wind energy into electrical energy through practical mechanical design and engineering.</p>
      <div class="actions">
        <a class="btn" href="#overview">Explore project ↗</a>
        <a class="btn secondary" href="#gallery">View project files</a>
      </div>
    </div>
    <div class="visual" aria-label="Decorative vertical-axis turbine illustration">
      <div class="turbine">
        <div class="mast"></div><div class="blade one"></div><div class="blade two"></div><div class="blade three"></div><div class="hub"></div>
      </div>
      <div class="visual-label">VERTICAL AXIS WIND TURBINE</div>
    </div>
  </div>
</section>

<section id="overview">
  <div class="wrap two-col">
    <div>
      <div class="section-tag">01 / Overview</div>
      <h2>Turning moving air into useful energy.</h2>
      <p class="lead">VERTEX is a vertical-axis wind turbine project designed to demonstrate the conversion of wind energy into mechanical rotation and then electrical energy. The vertical rotor is arranged around a central shaft and is intended to accept wind from different directions.</p>
    </div>
    <div class="panel">
      <div class="section-tag">Project focus</div>
      <h3 style="font-size:1.35rem;margin:10px 0">Learn by designing and building</h3>
      <p class="lead">The project brings together rotor design, shaft support, bearings, a generator and an electrical output circuit. Performance values should be added after testing the completed prototype.</p>
    </div>
  </div>
</section>

<section id="working" style="background:linear-gradient(180deg,rgba(15,39,59,.35),transparent)">
  <div class="wrap">
    <div class="section-tag">02 / Working principle</div>
    <h2>How the system works</h2>
    <p class="lead">The energy conversion takes place in a sequence of connected stages.</p>
    <div class="steps">
      <article class="step"><div class="num">STEP 01</div><h3>Wind reaches the rotor</h3><p>Moving air applies force to the turbine blades and creates rotor motion.</p></article>
      <article class="step"><div class="num">STEP 02</div><h3>The shaft rotates</h3><p>The rotor transfers its motion to the central shaft, supported by bearings.</p></article>
      <article class="step"><div class="num">STEP 03</div><h3>The generator converts energy</h3><p>The rotating shaft drives the generator, which converts mechanical energy into electrical energy.</p></article>
      <article class="step"><div class="num">STEP 04</div><h3>Electrical output is checked</h3><p>Voltage and current can be measured, then compared under different test conditions.</p></article>
    </div>
  </div>
</section>

<section id="design">
  <div class="wrap">
    <div class="section-tag">03 / Design & components</div>
    <h2>Built around practical engineering.</h2>
    <p class="lead">These are the main system elements. Add exact material names, model numbers and ratings after checking the parts fitted to your prototype.</p>
    <div class="specs">
      <div class="spec"><span>Turbine type</span><strong>Vertical Axis Wind Turbine (VAWT)</strong></div>
      <div class="spec"><span>Rotor / blade material</span><strong>To be confirmed from prototype</strong></div>
      <div class="spec"><span>Shaft & support</span><strong>Rotating shaft with bearing support</strong></div>
      <div class="spec"><span>Generator</span><strong>DC Motor Used as Generator</strong></div>
      <div class="spec"><span>Electrical circuit</span><strong>Output / charging circuit (verify fitted components)</strong></div>
      <div class="spec"><span>Test load</span><strong>Record actual load and measured output</strong></div>
    </div>
    <p class="note">Note: No voltage, power, efficiency or charging-performance figures are claimed here. Add only values measured during your project testing.</p>
  </div>
</section>

<section id="gallery" style="background:linear-gradient(180deg,rgba(15,39,59,.35),transparent)">
  <div class="wrap">
    <div class="section-tag">04 / Project gallery</div>
    <h2>The work behind the idea.</h2>
    <p class="lead">The repository includes your prototype photograph and SolidWorks assembly file.</p>
    <div class="gallery">
      <article class="gallery-card">
        <img src="WhatsApp%20Image%202026-11-25%20at%208.01.38%20PM.jpeg" alt="Vertical wind turbine prototype photograph" onerror="this.style.display='none';this.insertAdjacentHTML('afterend','<div style=&quot;padding:45px 15px;text-align:center;color:#536579;background:#eef3f6;border-radius:13px&quot;>Prototype image not found. Check the exact image filename in GitHub.</div>')">
        <h3>Prototype photograph</h3>
        <p>Photograph of the physical vertical wind turbine prototype.</p>
      </article>
      <article class="gallery-card">
        <div style="height:280px;background:#eef3f6;color:#183044;border-radius:13px;display:grid;place-items:center;text-align:center;padding:25px">
          <div><div style="font-size:2.5rem">⚙</div><strong>SolidWorks assembly file</strong><br><small>Download the model to open it in SolidWorks.</small></div>
        </div>
        <h3>CAD / assembly model</h3>
        <p>SolidWorks assembly supplied with the project repository.</p>
        <a class="file-link" href="VERTICAL%20WIND%20TURBINE.SLDASM" download>Download SolidWorks assembly ↗</a>
      </article>
    </div>
  </div>
</section>

<section id="future">
  <div class="wrap">
    <div class="section-tag">05 / Future scope</div>
    <h2>Where the project can go next.</h2>
    <div class="future">
      <div class="panel"><h3>Improve rotor design</h3><p class="lead">Study blade shape, material and arrangement to improve starting and rotation.</p></div>
      <div class="panel"><h3>Monitor performance</h3><p class="lead">Add suitable sensors to record rotor speed, voltage and current during testing.</p></div>
      <div class="panel"><h3>Improve power storage</h3><p class="lead">Evaluate a suitable charging and storage arrangement after measuring generator output.</p></div>
    </div>
  </div>
</section>
</main>

<footer>
  <div class="wrap">VERTEX · Vertical Axis Wind Turbine Project · Mechanical Engineering</div>
</footer>
</body>
</html>
