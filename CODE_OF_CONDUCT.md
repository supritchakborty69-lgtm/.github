<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>The Little Bistro — Premium Menu</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500&family=Outfit:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#20201b;
  --layer:#2c2c24;
  --card:#323229;
  --amber:#f5a623;
  --amber2:#ffbe4d;
  --amber3:#ffe099;
  --cream:#fff8ee;
  --muted:rgba(255,248,238,0.5);
  --border:rgba(245,166,35,0.38);
  --glass:rgba(245,166,35,0.1);
  --glow:0 0 24px rgba(245,166,35,0.45);
  --shadow-card:0 6px 28px rgba(0,0,0,0.5),inset 0 1px 0 rgba(245,166,35,0.15);
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
html{scroll-behavior:smooth;}
body{background:var(--bg);color:var(--cream);font-family:'Outfit',sans-serif;min-height:100vh;overflow-x:hidden;}

body::after{content:'';position:fixed;inset:0;z-index:1;pointer-events:none;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.025'/%3E%3C/svg%3E");opacity:.3;}

#bg3d{position:fixed;inset:0;z-index:0;pointer-events:none;}

/* ONBOARDING */
#onboard{
  position:fixed;inset:0;z-index:800;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  padding:1.5rem;overflow-y:auto;
  background:radial-gradient(ellipse 150% 110% at 50% 20%,#3d2e08 0%,#20201b 60%);
}
.ob-logo{text-align:center;margin-bottom:2rem;animation:fadeUp .7s ease both;}
.ob-wordmark{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(2.8rem,12vw,5.2rem);font-weight:300;font-style:italic;
  background:linear-gradient(160deg,#f5a623 0%,#ffe099 50%,#f5a623 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  line-height:1;letter-spacing:0.02em;
  filter:drop-shadow(0 0 55px rgba(245,166,35,.75));
}
.ob-rule{display:flex;align-items:center;gap:.8rem;margin:.5rem 0 .3rem;justify-content:center;}
.ob-rule-line{width:45px;height:1px;background:rgba(245,166,35,.45);}
.ob-rule-dot{font-size:.62rem;letter-spacing:.32em;text-transform:uppercase;color:rgba(245,166,35,.75);}
.ob-sub{font-size:.65rem;letter-spacing:.32em;text-transform:uppercase;color:rgba(245,166,35,.55);}

.ob-card{
  background:rgba(50,50,38,0.65);border:1.5px solid rgba(245,166,35,.45);border-radius:26px;
  padding:2.2rem 1.8rem;width:100%;max-width:400px;
  backdrop-filter:blur(28px);
  box-shadow:0 32px 80px rgba(0,0,0,.7),0 0 50px rgba(245,166,35,.08),inset 0 1px 0 rgba(245,166,35,.2);
  animation:fadeUp .7s .1s ease both;
}
.ob-card-title{font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:400;color:#ffe099;text-align:center;margin-bottom:.3rem;}
.ob-card-sub{font-size:.72rem;color:var(--muted);text-align:center;letter-spacing:.05em;margin-bottom:1.8rem;}

.field-label{font-size:.65rem;letter-spacing:.18em;text-transform:uppercase;color:var(--amber);margin-bottom:.5rem;display:block;font-weight:500;}
.field-wrap{position:relative;margin-bottom:1.4rem;}
.field-wrap input{
  width:100%;padding:.85rem 1rem .85rem 2.8rem;
  background:rgba(245,166,35,.09);border:1.5px solid rgba(245,166,35,.32);border-radius:13px;
  font-family:'Outfit',sans-serif;font-size:.9rem;font-weight:300;
  color:var(--cream);letter-spacing:.04em;outline:none;transition:all .25s;caret-color:var(--amber);
}
.field-wrap input::placeholder{color:rgba(255,248,238,.22);}
.field-wrap input:focus{border-color:var(--amber);background:rgba(245,166,35,.13);box-shadow:0 0 0 4px rgba(245,166,35,.18),var(--glow);}
.field-icon{position:absolute;left:.9rem;top:50%;transform:translateY(-50%);font-size:1rem;pointer-events:none;color:var(--amber);}

.tbl-label{font-size:.65rem;letter-spacing:.18em;text-transform:uppercase;color:var(--amber);margin-bottom:.6rem;display:block;font-weight:500;}
.tbl-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:8px;margin-bottom:1.6rem;}
.t-btn{
  aspect-ratio:1;background:rgba(245,166,35,.09);border:1.5px solid rgba(245,166,35,.22);
  border-radius:11px;color:rgba(255,248,238,.6);
  font-family:'Cormorant Garamond',serif;font-size:1rem;font-weight:500;
  cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;
}
.t-btn:hover{background:rgba(245,166,35,.2);color:var(--cream);border-color:var(--amber);}
.t-btn.sel{
  background:var(--amber);border-color:var(--amber2);color:#20201b;font-weight:700;
  box-shadow:0 4px 22px rgba(245,166,35,.65),0 0 0 3px rgba(245,166,35,.22);transform:scale(1.1);
}

.enter-btn{
  width:100%;padding:1rem;background:var(--amber);border:none;border-radius:14px;
  font-family:'Outfit',sans-serif;font-size:.82rem;font-weight:600;letter-spacing:.18em;text-transform:uppercase;
  color:#20201b;cursor:pointer;transition:all .3s;opacity:.3;pointer-events:none;
}
.enter-btn.on{opacity:1;pointer-events:all;box-shadow:0 8px 34px rgba(245,166,35,.6);}
.enter-btn.on:hover{transform:translateY(-2px);background:var(--amber2);box-shadow:0 14px 42px rgba(245,166,35,.7);}

/* APP */
#app{display:none;position:relative;z-index:10;}

.hdr{
  position:sticky;top:0;z-index:300;padding:.8rem 1.2rem;
  display:flex;align-items:center;justify-content:space-between;
  background:rgba(32,32,27,.93);backdrop-filter:blur(22px);
  border-bottom:1.5px solid rgba(245,166,35,.35);
  box-shadow:0 4px 28px rgba(0,0,0,.45),0 1px 0 rgba(245,166,35,.15);
}
.hdr-logo{
  font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:400;font-style:italic;
  background:linear-gradient(135deg,var(--amber),var(--amber3));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  filter:drop-shadow(0 0 12px rgba(245,166,35,.45));
}
.hdr-logo small{
  display:block;font-style:normal;font-family:'Outfit',sans-serif;font-size:.52rem;
  letter-spacing:.25em;text-transform:uppercase;-webkit-text-fill-color:rgba(245,166,35,.65);margin-top:1px;
}
.hdr-right{display:flex;align-items:center;gap:.55rem;}
.info-chip{
  background:rgba(245,166,35,.13);border:1.5px solid rgba(245,166,35,.42);
  border-radius:8px;padding:.28rem .65rem;font-size:.66rem;letter-spacing:.06em;
  color:var(--amber2);white-space:nowrap;font-weight:500;
}
.cart-btn{
  position:relative;background:var(--amber);border:none;border-radius:11px;
  padding:.5rem .92rem;color:#20201b;font-family:'Outfit',sans-serif;
  font-size:.77rem;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:.35rem;
  transition:all .2s;box-shadow:0 4px 18px rgba(245,166,35,.55);
}
.cart-btn svg{width:14px;height:14px;}
.cart-btn:hover{transform:translateY(-1px);background:var(--amber2);box-shadow:0 8px 26px rgba(245,166,35,.65);}
.cdot{
  position:absolute;top:-5px;right:-5px;
  background:#ff4e3a;color:#fff;border-radius:50%;width:17px;height:17px;
  font-size:.6rem;font-weight:700;display:none;align-items:center;justify-content:center;
  box-shadow:0 2px 10px rgba(255,78,58,.7);
}
.cdot.on{display:flex;}

.cat-nav{
  display:flex;overflow-x:auto;gap:.45rem;padding:.8rem 1rem;
  background:rgba(32,32,27,.85);border-bottom:1px solid rgba(245,166,35,.18);
  scrollbar-width:none;backdrop-filter:blur(12px);
}
.cat-nav::-webkit-scrollbar{display:none;}
.cpill{
  flex-shrink:0;padding:.42rem .95rem;border-radius:30px;
  border:1.5px solid rgba(245,166,35,.22);background:transparent;
  font-family:'Outfit',sans-serif;font-size:.75rem;font-weight:400;
  color:rgba(255,248,238,.5);cursor:pointer;transition:all .22s;
  white-space:nowrap;display:flex;align-items:center;gap:.3rem;
}
.cpill:hover{border-color:var(--amber);color:var(--amber);background:rgba(245,166,35,.1);}
.cpill.on{background:var(--amber);border-color:var(--amber);color:#20201b;font-weight:600;box-shadow:0 3px 16px rgba(245,166,35,.5);}

/* HERO */
.hero{position:relative;overflow:hidden;height:260px;display:flex;align-items:center;justify-content:center;}
#hero-canvas{position:absolute;inset:0;pointer-events:none;}
.hero-bg{position:absolute;inset:0;background:url('https://images.unsplash.com/photo-1445116572660-236099ec97a0?w=900&q=80') center/cover;filter:brightness(0.22) saturate(0.6);}
.hero-gradient{position:absolute;inset:0;background:linear-gradient(to bottom,rgba(32,32,27,.2) 0%,rgba(32,32,27,0) 35%,rgba(32,32,27,.8) 80%,rgba(32,32,27,1) 100%);}
.hero-content{position:relative;z-index:2;text-align:center;padding:1rem;}
.hero-greet{font-size:.65rem;letter-spacing:.32em;text-transform:uppercase;color:var(--amber);margin-bottom:.5rem;font-weight:500;text-shadow:0 0 22px rgba(245,166,35,.9);}
.hero-name{font-family:'Cormorant Garamond',serif;font-size:clamp(1.8rem,7vw,2.8rem);font-weight:300;font-style:italic;color:var(--cream);line-height:1.1;margin-bottom:.4rem;text-shadow:0 2px 24px rgba(0,0,0,.65);}
.hero-tagline{font-size:.76rem;color:var(--muted);letter-spacing:.08em;font-weight:300;}
.gold-bar{width:60px;height:2px;background:linear-gradient(90deg,transparent,var(--amber),transparent);margin:.9rem auto 0;border-radius:1px;box-shadow:0 0 14px rgba(245,166,35,.7);}

/* MENU */
.menu-body{padding:1.2rem .9rem 9rem;}
.m-section{margin-bottom:2.8rem;}
.sec-hdr{display:flex;align-items:center;gap:.9rem;margin-bottom:1.1rem;padding:0 .2rem;}
.sec-icon{
  width:38px;height:38px;background:rgba(245,166,35,.16);border:1.5px solid rgba(245,166,35,.4);
  border-radius:11px;display:flex;align-items:center;justify-content:center;font-size:1.1rem;flex-shrink:0;
  box-shadow:0 0 16px rgba(245,166,35,.25);
}
.sec-name{font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:400;font-style:italic;color:var(--amber2);text-shadow:0 0 22px rgba(245,166,35,.35);}
.sec-line{flex:1;height:1.5px;background:linear-gradient(to right,rgba(245,166,35,.55),transparent);}

/* CARDS */
.items-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:.85rem;}
.items-grid .m-card:first-child{grid-column:1/-1;flex-direction:row;}
.items-grid .m-card:first-child .card-img-wrap{width:120px;padding-top:0;height:120px;flex-shrink:0;border-radius:14px 0 0 14px;}
.items-grid .m-card:first-child .card-img{position:relative;border-radius:14px 0 0 14px;}
.items-grid .m-card:first-child .card-body{padding:.9rem 1rem;display:flex;flex-direction:column;justify-content:space-between;flex:1;}

.m-card{
  background:var(--card);border:1.5px solid rgba(245,166,35,.2);border-radius:18px;
  overflow:hidden;display:flex;flex-direction:column;
  transition:all .3s cubic-bezier(.34,1.56,.64,1);
  box-shadow:var(--shadow-card);position:relative;cursor:default;
}
.m-card::before{content:'';position:absolute;inset:0;border-radius:18px;pointer-events:none;z-index:1;background:linear-gradient(135deg,rgba(245,166,35,.07) 0%,transparent 50%);}
.m-card:hover{
  transform:translateY(-5px) scale(1.018);
  border-color:rgba(245,166,35,.6);
  box-shadow:0 22px 55px rgba(0,0,0,.55),0 0 0 1px rgba(245,166,35,.4),0 0 35px rgba(245,166,35,.18),inset 0 1px 0 rgba(245,166,35,.22);
}

.card-img-wrap{position:relative;overflow:hidden;width:100%;padding-top:62%;}
.card-img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;transition:transform .5s ease;background:var(--layer);}
.m-card:hover .card-img{transform:scale(1.08);}
.img-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(32,32,27,.92) 0%,rgba(32,32,27,.05) 55%,transparent 100%);}
.img-badge{
  position:absolute;top:.6rem;right:.6rem;background:var(--amber);
  color:#20201b;border-radius:8px;padding:.24rem .62rem;font-size:.67rem;font-weight:700;
  letter-spacing:.04em;z-index:2;box-shadow:0 3px 14px rgba(245,166,35,.55);
}
.card-img-wrap::after{content:'';position:absolute;inset:0;background:linear-gradient(90deg,transparent 0%,rgba(245,166,35,.09) 50%,transparent 100%);background-size:200% 100%;animation:shimmer 1.8s infinite;}
@keyframes shimmer{0%{background-position:-200% 0}100%{background-position:200% 0}}

.card-body{padding:.8rem .85rem .85rem;flex:1;display:flex;flex-direction:column;gap:.35rem;}
.card-name{font-family:'Cormorant Garamond',serif;font-size:.98rem;font-weight:600;color:var(--cream);line-height:1.2;}
.card-desc{font-size:.68rem;color:rgba(255,248,238,.42);line-height:1.45;flex:1;}
.card-foot{display:flex;align-items:center;justify-content:space-between;margin-top:.3rem;}
.card-price{font-size:.9rem;font-weight:700;color:var(--amber2);text-shadow:0 0 14px rgba(245,166,35,.45);}
.add-btn{
  width:34px;height:34px;background:var(--amber);border:none;border-radius:10px;
  color:#20201b;font-size:1.35rem;cursor:pointer;display:flex;align-items:center;justify-content:center;
  transition:all .25s cubic-bezier(.34,1.56,.64,1);
  box-shadow:0 3px 14px rgba(245,166,35,.55),inset 0 1px 0 rgba(255,255,255,.15);line-height:1;font-weight:300;
}
.add-btn:hover{transform:scale(1.22);background:var(--amber2);box-shadow:0 6px 24px rgba(245,166,35,.7);}

.qty-row{display:flex;align-items:center;gap:.4rem;}
.qb{
  width:30px;height:30px;background:rgba(245,166,35,.13);border:1.5px solid rgba(245,166,35,.38);
  border-radius:8px;color:var(--amber2);font-size:.95rem;cursor:pointer;
  display:flex;align-items:center;justify-content:center;transition:all .15s;
}
.qb:hover{background:rgba(245,166,35,.28);color:var(--cream);}
.qn{font-size:.88rem;font-weight:700;color:var(--amber);min-width:14px;text-align:center;}

/* FLOAT BAR */
.float-bar{
  position:fixed;bottom:1.1rem;left:.9rem;right:.9rem;z-index:400;
  background:rgba(32,32,27,.97);border:1.5px solid rgba(245,166,35,.5);
  border-radius:20px;padding:.9rem 1.2rem;
  display:none;align-items:center;justify-content:space-between;
  backdrop-filter:blur(22px);
  box-shadow:0 16px 52px rgba(0,0,0,.65),0 0 36px rgba(245,166,35,.25),inset 0 1px 0 rgba(245,166,35,.18);
  cursor:pointer;transition:transform .2s;
}
.float-bar.on{display:flex;}
.float-bar:hover{transform:translateY(-3px);}
.fb-l{display:flex;align-items:center;gap:.6rem;}
.fb-badge{background:var(--amber);color:#20201b;border-radius:7px;padding:.2rem .6rem;font-size:.75rem;font-weight:700;box-shadow:0 2px 12px rgba(245,166,35,.55);}
.fb-txt{font-size:.78rem;color:var(--muted);font-weight:300;}
.fb-price{font-size:.96rem;font-weight:700;color:var(--amber2);}

/* CART */
#cOverlay{position:fixed;inset:0;z-index:500;background:rgba(0,0,0,.82);backdrop-filter:blur(12px);display:none;}
#cOverlay.on{display:block;}
.cart-sheet{
  position:fixed;bottom:0;left:0;right:0;z-index:501;
  background:linear-gradient(180deg,#2e2e24 0%,#24241c 100%);
  border-radius:26px 26px 0 0;
  border-top:2px solid rgba(245,166,35,.55);
  border-left:1px solid rgba(245,166,35,.18);border-right:1px solid rgba(245,166,35,.18);
  padding:1.4rem 1.1rem 2.5rem;max-height:90vh;overflow-y:auto;
  transform:translateY(100%);transition:transform .4s cubic-bezier(.32,.72,0,1);
  box-shadow:0 -30px 72px rgba(0,0,0,.8),0 -2px 0 rgba(245,166,35,.35);
}
.cart-sheet.on{transform:translateY(0);}
.cart-sheet::-webkit-scrollbar{width:2px;}
.cart-sheet::-webkit-scrollbar-thumb{background:rgba(245,166,35,.45);border-radius:1px;}

.cs-handle{width:36px;height:4px;background:rgba(245,166,35,.55);border-radius:2px;margin:0 auto 1.4rem;box-shadow:0 0 12px rgba(245,166,35,.45);}
.cs-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.3rem;}
.cs-title{font-family:'Cormorant Garamond',serif;font-size:1.45rem;font-weight:400;font-style:italic;color:var(--amber3);text-shadow:0 0 22px rgba(245,166,35,.35);}
.cs-close{
  width:30px;height:30px;background:rgba(245,166,35,.12);border:1.5px solid rgba(245,166,35,.35);
  border-radius:7px;color:var(--amber);cursor:pointer;
  display:flex;align-items:center;justify-content:center;font-size:.95rem;transition:all .2s;
}
.cs-close:hover{background:rgba(245,166,35,.22);color:var(--cream);}

.cs-empty{text-align:center;padding:2.5rem 1rem;color:var(--muted);}
.cs-empty .ei{font-size:2.8rem;margin-bottom:.7rem;}
.cs-empty p{font-size:.8rem;letter-spacing:.04em;}

.cs-list{display:flex;flex-direction:column;gap:.7rem;margin-bottom:1.1rem;}
.cs-item{background:rgba(245,166,35,.08);border:1px solid rgba(245,166,35,.22);border-radius:15px;padding:.8rem;display:flex;align-items:center;gap:.75rem;}
.cs-img{width:48px;height:48px;border-radius:10px;object-fit:cover;flex-shrink:0;background:var(--layer);border:1px solid rgba(245,166,35,.25);}
.cs-inf{flex:1;}
.cs-n{font-size:.87rem;color:var(--cream);margin-bottom:.12rem;font-weight:400;}
.cs-p{font-size:.72rem;color:var(--amber);font-weight:500;}
.cs-ctl{display:flex;align-items:center;gap:.35rem;}
.csb{width:26px;height:26px;background:rgba(245,166,35,.12);border:1.5px solid rgba(245,166,35,.32);border-radius:6px;color:var(--amber2);font-size:.88rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .15s;}
.csb:hover{background:rgba(245,166,35,.28);color:var(--cream);}
.csq{font-size:.85rem;font-weight:700;color:var(--amber);min-width:13px;text-align:center;}

.cs-rule{height:1px;background:rgba(245,166,35,.2);margin:.9rem 0;}
.cs-sum{margin-bottom:1.1rem;}
.sum-row{display:flex;justify-content:space-between;font-size:.79rem;color:var(--muted);margin-bottom:.35rem;}
.sum-row.tot{font-size:1rem;font-weight:700;color:var(--amber2);padding-top:.3rem;}

.tbl-strip{
  background:rgba(245,166,35,.12);border:1.5px solid rgba(245,166,35,.38);
  border-radius:11px;padding:.65rem .9rem;font-size:.78rem;color:var(--amber2);
  text-align:center;letter-spacing:.05em;margin-bottom:1rem;font-weight:600;
  box-shadow:0 0 18px rgba(245,166,35,.12);
}

.wa-btn{
  width:100%;padding:1.05rem;
  background:linear-gradient(135deg,#22c55e,#15803d);
  border:none;border-radius:15px;
  font-family:'Outfit',sans-serif;font-size:.88rem;font-weight:700;
  letter-spacing:.08em;color:#fff;cursor:pointer;
  display:flex;align-items:center;justify-content:center;gap:.55rem;
  transition:all .22s;
  box-shadow:0 8px 30px rgba(34,197,94,.45),inset 0 1px 0 rgba(255,255,255,.14);
}
.wa-btn svg{width:20px;height:20px;}
.wa-btn:hover{transform:translateY(-2px);box-shadow:0 14px 40px rgba(34,197,94,.55);}

/* ANIMATIONS */
@keyframes fadeUp{from{opacity:0;transform:translateY(22px);}to{opacity:1;transform:translateY(0);}}
.m-section{animation:fadeUp .5s ease both;}
.m-section:nth-child(1){animation-delay:.04s}.m-section:nth-child(2){animation-delay:.09s}
.m-section:nth-child(3){animation-delay:.14s}.m-section:nth-child(4){animation-delay:.19s}
.m-section:nth-child(5){animation-delay:.24s}.m-section:nth-child(6){animation-delay:.29s}
.m-section:nth-child(7){animation-delay:.34s}

@keyframes tiltPop{0%{transform:scale(1);}40%{transform:scale(1.3) rotate(-6deg);}70%{transform:scale(.92) rotate(4deg);}100%{transform:scale(1);}}
.tilt-pop{animation:tiltPop .32s cubic-bezier(.34,1.56,.64,1);}
</style>
</head>
<body>
<canvas id="bg3d"></canvas>

<!-- ══════ ONBOARDING ══════ -->
<div id="onboard">
  <div class="ob-logo">
    <div class="ob-wordmark">The Little Bistro</div>
    <div class="ob-rule">
      <div class="ob-rule-line"></div>
      <div class="ob-rule-dot">✦ Fine Café · Est. 2018 ✦</div>
      <div class="ob-rule-line"></div>
    </div>
    <div class="ob-sub">Kolkata's most loved café experience</div>
  </div>

  <div class="ob-card">
    <div class="ob-card-title">Welcome, Guest</div>
    <div class="ob-card-sub">Tell us who you are and where you're seated</div>

    <label class="field-label">Your Name</label>
    <div class="field-wrap">
      <span class="field-icon">✦</span>
      <input type="text" id="nameInput" placeholder="e.g. Arjun Das" autocomplete="off" maxlength="40">
    </div>

    <label class="tbl-label">Your Table Number</labe
