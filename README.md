<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<title>RTUT — สมาพันธ์นิสิตนักศึกษารังสีเทคนิคแห่งประเทศไทย</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&family=Sarabun:wght@300;400;500;600;700&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
<style>
  :root{
    --navy:#003366;
    --navy-deep:#00203f;
    --sky:#3399FF;
    --gold:#FFCC00;
    --bg:#F5F8FC;
    --paper:#FFFFFF;
    --ink:#12233d;
    --ink-soft:#5b7092;
    --line:#e1e9f4;
    --ok:#1f9d55;
    --warn:#c0392b;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;overflow-x:hidden;}
  body{
    font-family:'Sarabun',sans-serif;
    background:var(--bg);
    color:var(--ink);
    line-height:1.6;
    position:relative;
  }
  body::before,
  body::after{
    content:"";
    position:fixed;
    border-radius:50%;
    z-index:0;
    pointer-events:none;
    filter:blur(70px);
  }
  body::before{
    top:-12%; left:-10%; width:52vw; height:52vw; max-width:640px; max-height:640px;
    background:radial-gradient(circle, rgba(51,153,255,0.32), transparent 70%);
  }
  body::after{
    bottom:-16%; right:-12%; width:56vw; height:56vw; max-width:680px; max-height:680px;
    background:radial-gradient(circle, rgba(255,204,0,0.28), transparent 70%);
  }
  h1,h2,h3,.brand,.nav-tab,.stat-num,.btn{font-family:'Kanit',sans-serif;}

  /* ---- liquid glass effect (adapted from Velorah) ---- */
  .liquid-glass{
    background: rgba(255,255,255,0.06);
    background-blend-mode: luminosity;
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border: none;
    box-shadow: inset 0 1px 1px rgba(255,255,255,0.14);
    position: relative;
    overflow: hidden;
  }
  .liquid-glass::before{
    content:"";
    position:absolute; inset:0; border-radius:inherit; padding:1.4px;
    background: linear-gradient(180deg,
      rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%,
      rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%,
      rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%);
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor; mask-composite: exclude;
    pointer-events:none;
  }

  /* ---- fade-rise entrance animation ---- */
  @keyframes fade-rise{ from{opacity:0; transform:translateY(24px);} to{opacity:1; transform:translateY(0);} }
  .animate-fade-rise{ animation: fade-rise .8s ease-out both; }
  .animate-fade-rise-delay{ animation: fade-rise .8s ease-out .2s both; }
  .animate-fade-rise-delay-2{ animation: fade-rise .8s ease-out .4s both; }
  @media (prefers-reduced-motion: reduce){
    .animate-fade-rise, .animate-fade-rise-delay, .animate-fade-rise-delay-2{ animation:none; opacity:1; transform:none; }
  }

  /* ---- hero background: fallback gradient (shown while video loads) ---- */
  .scanfield{
    position:relative;
    overflow:hidden;
    background:
      radial-gradient(circle at 85% -10%, rgba(51,153,255,0.35), transparent 45%),
      linear-gradient(180deg, var(--navy-deep) 0%, var(--navy) 100%);
  }
  .hero-video{
    position:absolute; inset:0; width:100%; height:100%;
    object-fit:cover; z-index:0;
  }
  .hero-video-overlay{
    position:absolute; inset:0; z-index:1; pointer-events:none;
    background:linear-gradient(180deg, rgba(0,32,63,0.55) 0%, rgba(0,20,40,0.72) 100%);
  }

  /* ---- top nav ---- */
  header{
    color:#fff;
    position:sticky; top:0; z-index:50;
    border-bottom:1px solid rgba(255,255,255,0.08);
    box-shadow:0 2px 14px rgba(0,20,50,0.25);
    isolation:isolate;
  }
  header::before{
    content:"";
    position:absolute; inset:0; z-index:-1;
    background:rgba(0,32,63,0.55);
    backdrop-filter:blur(14px);
    -webkit-backdrop-filter:blur(14px);
  }
  .nav-wrap{
    max-width:1120px; margin:0 auto;
    display:flex; align-items:center; justify-content:space-between;
    padding:14px 20px;
  }
  .brand{
    display:flex; align-items:center; gap:10px;
    font-weight:600; font-size:1.05rem; letter-spacing:.3px;
    color:#fff; text-decoration:none;
  }
  .brand-mark{
    width:40px;height:40px;
    display:flex; align-items:center; justify-content:center;
    flex-shrink:0;
  }
  .brand-mark svg{width:100%;height:100%;display:block;}
  .brand-text{display:flex; flex-direction:column; line-height:1.15; justify-content:center;}
  .brand-title{
    font-size:1.15rem; font-weight:700; color:#fff;
    padding-bottom:3px; border-bottom:2.5px solid #fff; letter-spacing:.5px;
    display:inline-block;
  }
  .brand-title .bl{
    display:inline-block;
    animation: letterIn .6s ease-out backwards,
               letterBounce 2.4s ease-in-out infinite 1.4s;
  }
  .brand-sub{
    font-size:0.62rem; color:#cfe0f7; font-weight:400; margin-top:3px;
    white-space:nowrap; letter-spacing:.2px;
  }
  @media (max-width:640px){
    .brand-sub{display:none;}
  }
  .footer-inner{
    display:flex; align-items:center; justify-content:center; gap:10px; flex-wrap:wrap;
  }
  .footer-mark{width:26px;height:26px; opacity:0.85; flex-shrink:0;}
  .footer-mark svg{width:100%;height:100%;display:block;}
  nav.tabs{display:flex; gap:4px;}
  .nav-tab{
    background:none; border:none; color:#cfe0f7; cursor:pointer;
    font-size:0.92rem; padding:9px 14px; border-radius:8px;
    transition:transform .15s ease, background .15s ease, color .15s ease; font-weight:500;
    position:relative; overflow:hidden;
  }
  .nav-tab:hover{background:rgba(255,255,255,0.08); color:#fff;}
  .nav-tab:active{transform:scale(.92);}
  .nav-tab.active{background:var(--gold); color:var(--navy-deep); animation: tabPop .35s cubic-bezier(.34,1.56,.64,1);}
  @keyframes tabPop{ from{ transform:scale(.85); } to{ transform:scale(1); } }
  .auth-actions{display:flex; align-items:center; gap:10px;}
  .btn-header{
    font-family:'Kanit',sans-serif; font-size:0.85rem; font-weight:500;
    padding:8px 16px; border-radius:8px; cursor:pointer; transition:transform .15s ease, background .15s ease, border-color .15s ease; white-space:nowrap;
    position:relative; overflow:hidden;
  }
  .btn-header:active{ transform:scale(.94); }
  .btn-header-ghost{background:transparent; border:1.5px solid rgba(255,255,255,0.35); color:#fff;}
  .btn-header-ghost:hover{border-color:var(--sky); background:rgba(255,255,255,0.08);}
  .btn-header-primary{background:var(--gold); border:1.5px solid var(--gold); color:var(--navy-deep); font-weight:600;}
  .btn-header-primary:hover{background:#ffd633;}
  .auth-hello{color:#e4edfa; font-size:0.85rem; font-weight:500;}
  @media (max-width:900px){
    .auth-hello{display:none;}
    .btn-header{padding:7px 12px; font-size:0.78rem;}
  }
  @media (max-width:560px){
    .nav-wrap{flex-wrap:wrap; gap:8px;}
    .auth-actions{width:100%; justify-content:flex-end;}
  }
  @media (max-width:720px){
    nav.tabs{position:fixed; bottom:0; left:0; right:0; background:var(--navy); justify-content:space-around; padding:6px 4px; box-shadow:0 -4px 14px rgba(0,0,0,.25);}
    .nav-tab{padding:8px 6px; font-size:0.78rem;}
    body{padding-bottom:58px;}
  }

  /* ---- hero ---- */
  .hero{color:#fff; padding:64px 20px 76px;}
  .hero-inner{max-width:1120px; margin:0 auto; position:relative; z-index:2;}
  .hero-grid{display:grid; grid-template-columns:1.25fr 1fr; gap:44px; align-items:center;}
  @media (max-width:900px){
    .hero-grid{grid-template-columns:1fr;}
  }
  .pill-badge{
    display:inline-flex; align-items:center; gap:8px;
    font-size:0.8rem; font-weight:500; color:#fff;
    padding:8px 16px; border-radius:30px; margin-bottom:22px;
  }
  .pill-badge svg{width:15px;height:15px; color:var(--gold); flex-shrink:0;}
  .eyebrow{
    display:inline-flex; align-items:center; gap:8px;
    font-size:0.78rem; letter-spacing:2px; text-transform:uppercase;
    color:var(--gold); font-weight:600; margin-bottom:16px;
  }
  .eyebrow::before{content:"";width:22px;height:1px;background:var(--gold);}
  .hero h1{
    font-family:'Kanit', sans-serif;
    font-size:clamp(2.2rem, 5vw, 3.4rem);
    font-weight:700; margin:0 0 16px; max-width:620px; line-height:1.15; letter-spacing:-0.5px;
  }
  .hero h1 .accent{color:var(--gold);}
  .hero p.lead{max-width:560px; color:#d9e6f8; font-size:1.05rem; margin:0 0 30px;}
  .hero-cta{display:flex; gap:14px; flex-wrap:wrap;}
  .hero-social-row{ display:flex; gap:10px; margin-top:24px; }
  .hero-social-row a{
    width:38px; height:38px; border-radius:50%;
    display:flex; align-items:center; justify-content:center;
    color:#fff; text-decoration:none; transition:.15s;
  }
  .hero-social-row a svg{ width:17px; height:17px; }
  .hero-social-row a:hover{ transform:translateY(-2px); color:var(--gold); }

  .btn-outline-light{
    background:transparent; color:#fff; border:1.5px solid rgba(255,255,255,0.4);
    font-family:'Kanit',sans-serif; font-weight:600; font-size:0.95rem;
    padding:12px 22px; border-radius:10px; cursor:pointer; transition:.15s;
  }
  .btn-outline-light:hover{border-color:var(--sky); color:var(--sky);}
  .hero-stat-grid{display:grid; grid-template-columns:1fr 1fr; gap:16px;}
  @media (max-width:480px){
    .hero-stat-grid{grid-template-columns:1fr 1fr;}
  }
  .stat-card{
    border-radius:16px; padding:22px 20px;
  }
  .stat-icon{width:26px;height:26px; color:var(--gold); margin-bottom:14px;}
  .stat-num{font-size:1.7rem; font-weight:600; color:#fff; font-family:'Kanit',sans-serif;}
  .stat-label{font-size:0.8rem; color:#b9cde8; margin-top:2px;}

  /* ---- layout shell ---- */
  main{max-width:1120px; margin:-40px auto 80px; padding:0 20px; position:relative; z-index:5;}
  .panel{
    background:rgba(255,255,255,0.55);
    border:1px solid rgba(255,255,255,0.6);
    border-radius:16px;
    padding:28px; margin-bottom:24px;
    backdrop-filter:blur(20px);
    -webkit-backdrop-filter:blur(20px);
    box-shadow:0 8px 30px rgba(10,40,90,0.08), inset 0 1px 1px rgba(255,255,255,0.7);
    position:relative;
  }
  .panel h2{margin:0 0 4px; font-size:1.35rem; color:var(--navy); font-weight:600;}
  .panel .sub{color:var(--ink-soft); font-size:0.9rem; margin:0 0 22px;}
  .view{display:none;}
  .view.active{display:block; animation: viewEnter .55s cubic-bezier(.16,.8,.32,1) both;}
  @keyframes viewEnter{
    from{ opacity:0; transform:translateX(-40px); }
    to{ opacity:1; transform:translateX(0); }
  }
  .panel{ }
  .scroll-reveal{
    opacity:0; transform:translateX(-46px);
    transition: opacity .7s cubic-bezier(.16,.8,.32,1), transform .7s cubic-bezier(.16,.8,.32,1);
  }
  .scroll-reveal.revealed{ opacity:1; transform:translateX(0); }
  .scroll-reveal-toggle{
    transform:translateY(20px);
    transition: opacity .5s cubic-bezier(.16,.8,.32,1), transform .5s cubic-bezier(.16,.8,.32,1);
  }
  .scroll-reveal-toggle.revealed{ transform:translateY(0); }
  @media (prefers-reduced-motion: reduce){
    .view.active{ animation:none; }
    .scroll-reveal{ opacity:1; transform:none; transition:none; }
  }

  /* ---- form ---- */
  .grid{display:grid; grid-template-columns:1fr 1fr; gap:16px;}
  @media (max-width:640px){.grid{grid-template-columns:1fr;}}
  label{display:block; font-size:0.85rem; font-weight:500; color:var(--ink); margin-bottom:6px;}
  input,select,textarea{
    width:100%; padding:11px 13px; border:1.5px solid rgba(255,255,255,0.55); border-radius:9px;
    font-family:'Sarabun',sans-serif; font-size:0.95rem; color:var(--ink);
    background:rgba(255,255,255,0.4);
    backdrop-filter:blur(10px); -webkit-backdrop-filter:blur(10px);
    transition:.15s;
  }
  input:focus,select:focus,textarea:focus{
    outline:none; border-color:var(--sky); box-shadow:0 0 0 3px rgba(51,153,255,0.15);
  }
  .field{margin-bottom:16px;}
  .btn{
    display:inline-flex; align-items:center; gap:8px; justify-content:center;
    border:none; border-radius:10px; padding:12px 22px; font-size:0.95rem;
    font-weight:600; cursor:pointer; transition:transform .15s ease, background .15s ease, box-shadow .15s ease;
    position:relative; overflow:hidden;
  }
  .btn:active{ transform:scale(.96); }
  .ripple{
    position:absolute; border-radius:50%; pointer-events:none;
    background:rgba(255,255,255,0.55); transform:scale(0);
    animation: rippleOut .55s ease-out forwards;
  }
  @keyframes rippleOut{ to{ transform:scale(2.6); opacity:0; } }
  .btn-primary{background:var(--gold); color:var(--navy-deep);}
  .btn-glass-gold{
    background:rgba(255,204,0,0.16); color:var(--gold); font-weight:600;
  }
  .btn-glass-gold:hover{background:rgba(255,204,0,0.26); transform:translateY(-1px);}
  .btn-primary:hover{background:#ffd633; transform:translateY(-1px);}
  .btn-ghost{background:transparent; color:var(--navy); border:1.5px solid var(--line);}
  .btn-ghost:hover{border-color:var(--sky); color:var(--sky);}
  .btn-danger{background:#fdecea; color:var(--warn);}
  .btn-danger:hover{background:#fadbd8;}
  .btn:disabled{opacity:.5; cursor:not-allowed;}
  .row-actions{display:flex; gap:10px; flex-wrap:wrap; margin-top:22px;}

  .badge{
    display:inline-flex; align-items:center; gap:6px;
    font-size:0.75rem; font-weight:600; padding:4px 10px; border-radius:20px;
  }
  .badge.active{background:#e7f7ee; color:var(--ok);}
  .badge.alumnus{background:#eef2fb; color:var(--navy);}
  .badge.pending{background:#fff6e0; color:#a67c00;}
  .badge.rejected{background:#fdecea; color:var(--warn);}

  .empty{
    text-align:center; padding:40px 20px; color:var(--ink-soft);
  }
  .empty svg{opacity:.5; margin-bottom:12px;}

  .toast{
    position:fixed; bottom:24px; left:50%; transform:translateX(-50%) translateY(20px);
    background:var(--navy-deep); color:#fff; padding:13px 22px; border-radius:10px;
    font-size:0.9rem; opacity:0; pointer-events:none; transition:.25s;
    box-shadow:0 10px 30px rgba(0,0,0,0.25); z-index:200; display:flex; align-items:center; gap:8px;
  }
  .toast.show{opacity:1; transform:translateX(-50%) translateY(0);}
  .toast.err{background:var(--warn);}
  .toast.success{background:var(--ok);}

  .id-card{
    border:1.5px solid rgba(255,255,255,0.6); border-radius:14px; padding:20px;
    display:flex; gap:16px; align-items:center;
    background:linear-gradient(135deg, rgba(255,255,255,0.6), rgba(242,247,255,0.45));
    backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);
    margin-bottom:22px;
  }
  .id-avatar{
    width:56px;height:56px;border-radius:50%; flex-shrink:0;
    background:var(--navy); color:#fff; display:flex; align-items:center; justify-content:center;
    font-weight:600; font-size:1.2rem; font-family:'Kanit',sans-serif;
    overflow:hidden;
  }
  .id-avatar img{ width:100%; height:100%; object-fit:cover; display:block; }
  .id-name{font-weight:600; font-size:1.05rem; color:var(--navy);}
  .id-meta{font-size:0.85rem; color:var(--ink-soft); margin-top:2px;}

  .photo-upload-row{ display:flex; align-items:center; gap:16px; margin-bottom:20px; }
  .photo-preview{
    width:84px; height:84px; border-radius:50%; flex-shrink:0; overflow:hidden;
    background:var(--navy); color:#fff; display:flex; align-items:center; justify-content:center;
    font-weight:600; font-size:1.6rem; font-family:'Kanit',sans-serif;
    border:2px solid rgba(255,255,255,0.6);
  }
  .photo-preview img{ width:100%; height:100%; object-fit:cover; display:block; }
  .photo-upload-actions{ display:flex; gap:10px; flex-wrap:wrap; align-items:center; }
  .photo-upload-actions input[type="file"]{ display:none; }
  .photo-hint{ font-size:0.78rem; color:var(--ink-soft); margin-top:4px; }

  .proj-card{
    border:1.5px solid rgba(255,255,255,0.55); border-radius:14px; padding:20px; margin-bottom:16px;
    background:rgba(255,255,255,0.42);
    backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);
    transition:.15s;
  }
  .proj-card:hover{border-color:var(--sky); box-shadow:0 6px 20px rgba(51,153,255,0.12);}
  .proj-head{display:flex; justify-content:space-between; align-items:flex-start; gap:12px; flex-wrap:wrap;}
  .proj-title{font-family:'Kanit',sans-serif; font-weight:600; font-size:1.1rem; color:var(--navy);}
  .proj-tag{font-size:0.75rem; color:var(--sky); font-weight:600; text-transform:uppercase; letter-spacing:.5px;}
  .proj-desc{color:var(--ink-soft); font-size:0.92rem; margin:8px 0 14px;}
  .dept-pills{display:flex; gap:8px; flex-wrap:wrap; margin:10px 0;}
  .pill{
    font-size:0.8rem; padding:6px 12px; border-radius:20px; border:1.5px solid rgba(255,255,255,0.55);
    cursor:pointer; background:rgba(255,255,255,0.4);
    backdrop-filter:blur(10px); -webkit-backdrop-filter:blur(10px);
    transition:.15s; color:var(--ink);
  }
  .pill:hover{border-color:var(--sky);}
  .pill.sel{
    background:rgba(0,51,102,0.75); color:#fff; border-color:rgba(0,51,102,0.85);
    backdrop-filter:blur(10px); -webkit-backdrop-filter:blur(10px);
  }

  table{width:100%; border-collapse:collapse; font-size:0.9rem;}
  th{text-align:left; color:var(--ink-soft); font-weight:600; font-size:0.78rem; text-transform:uppercase; letter-spacing:.4px; padding:10px 12px; border-bottom:2px solid var(--line);}
  td{padding:12px; border-bottom:1px solid var(--line);}
  tr:last-child td{border-bottom:none;}
  .table-wrap{overflow-x:auto;}

  .note{
    font-size:0.82rem; color:var(--ink-soft); background:#f3f7fd; border-radius:8px; padding:10px 12px;
    border-left:3px solid var(--sky); margin-top:14px;
  }
  footer{
    background:var(--navy-deep); color:#b9cde8; text-align:center; padding:28px 20px; font-size:0.85rem;
  }

  /* ---------------- animated RTUT mark ---------------- */
  .rtut-mark{ overflow:visible; }
  .rtut-mark .ring{ transform-origin:150px 150px; animation:ringPulse 2.4s ease-in-out infinite; }
  .rtut-mark .ring1{ animation-delay:0s; }
  .rtut-mark .ring2{ animation-delay:0.2s; }
  .rtut-mark .ring3{ animation-delay:0.4s; }
  .rtut-mark .center-ring{ transform-origin:150px 150px; animation:ringPulseCenter 2.4s ease-in-out infinite; }
  .rtut-mark .chevron{ transform-origin:45px 255px; animation:ringSway 2.4s ease-in-out infinite; }

  @keyframes ringPulse{
    0%   { opacity:1;   transform:scale(1); }
    50%  { opacity:0.55;transform:scale(1.06); }
    100% { opacity:1;   transform:scale(1); }
  }
  @keyframes ringPulseCenter{
    0%   { transform:scale(1); }
    50%  { transform:scale(0.94); }
    100% { transform:scale(1); }
  }
  @keyframes ringSway{
    0%   { transform:rotate(0deg); }
    50%  { transform:rotate(-8deg); }
    100% { transform:rotate(0deg); }
  }
  @keyframes letterIn{
    0%   { opacity:0; transform:translateY(40px) scale(0.7) rotate(-8deg); }
    70%  { opacity:1; transform:translateY(-6px) scale(1.05) rotate(2deg); }
    100% { opacity:1; transform:translateY(0) scale(1) rotate(0deg); }
  }
  @keyframes letterBounce{
    0%   { transform:translateY(0); }
    15%  { transform:translateY(-6px); }
    30%  { transform:translateY(0); }
    100% { transform:translateY(0); }
  }
  .footer-mark .ring,
  .footer-mark .center-ring,
  .footer-mark .chevron{ animation:none; } /* keep footer mark static, small & subtle */

  /* ---------------- scrolling university network banner (as hero background) ---------------- */
  :root{ --uni-banner-speed: 28s; }
  .hero-bg-banner{
    position:absolute; inset:0; overflow:hidden; z-index:0; pointer-events:none;
  }
  .hero-bg-banner-track{
    display:flex;
    width:max-content;
    height:100%;
    animation: uniBannerScroll var(--uni-banner-speed) linear infinite reverse;
    will-change:transform;
  }
  .hero-bg-banner-track img{
    height:100%;
    width:auto;
    display:block;
    flex-shrink:0;
    object-fit:cover;
    filter:brightness(0.5) saturate(1.05);
  }
  @keyframes uniBannerScroll{
    from{ transform:translateX(0); }
    to  { transform:translateX(-50%); }
  }
  @media (prefers-reduced-motion: reduce){
    .hero-bg-banner-track{ animation:none; }
  }

  /* ---------------- intro splash screen ---------------- */
  #site-splash{
    position:fixed; inset:0; z-index:9999;
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    gap:20px; text-align:center; padding:20px;
    overflow:hidden;
    background:
      radial-gradient(circle at 85% -10%, rgba(51,153,255,0.35), transparent 45%),
      radial-gradient(circle at 10% 110%, rgba(255,204,0,0.16), transparent 50%),
      linear-gradient(180deg, var(--navy-deep) 0%, var(--navy) 100%);
    cursor:pointer;
    transition:opacity 1.4s ease, visibility 1.4s ease;
  }
  #site-splash.splash-hide{ opacity:0; visibility:hidden; pointer-events:none; }
  #site-splash::before,
  #site-splash::after{
    content:""; position:absolute; border-radius:50%; pointer-events:none; filter:blur(60px); z-index:0;
  }
  #site-splash::before{
    top:-15%; left:-12%; width:46vw; height:46vw; max-width:520px; max-height:520px;
    background:radial-gradient(circle, rgba(51,153,255,0.28), transparent 70%);
  }
  #site-splash::after{
    bottom:-18%; right:-12%; width:50vw; height:50vw; max-width:560px; max-height:560px;
    background:radial-gradient(circle, rgba(255,204,0,0.22), transparent 70%);
  }
  .splash-logo-wrap{
    position:relative; width:96px; height:96px; margin-bottom:4px; z-index:1;
    opacity:0; animation: splashPopIn .7s cubic-bezier(0.22,1,0.36,1) forwards;
  }
  .splash-logo-wrap::before{
    content:""; position:absolute; inset:-26px; border-radius:50%;
    background:radial-gradient(circle, rgba(255,204,0,0.35), transparent 70%);
    filter:blur(14px); z-index:-1;
  }
  .splash-logo-wrap svg{ width:100%; height:100%; display:block; }
  .splash-icons{ display:flex; gap:16px; z-index:1; }
  .splash-icon-circle{
    width:44px; height:44px; border-radius:50%;
    display:flex; align-items:center; justify-content:center;
    color:var(--gold);
    opacity:0; animation: splashPopIn .6s cubic-bezier(0.22,1,0.36,1) forwards;
  }
  .splash-icon-circle svg{ width:18px; height:18px; }
  @keyframes splashPopIn{
    from{ opacity:0; transform:translateY(14px) scale(0.7); }
    to  { opacity:1; transform:translateY(0) scale(1); }
  }
  .splash-welcome{
    font-family:'Kanit',sans-serif; font-weight:500; font-size:1.05rem;
    color:#cfe0f7; opacity:0; animation: splashFadeUp .7s ease-out .8s forwards; z-index:1;
  }
  .splash-title{
    font-family:'Kanit',sans-serif; font-weight:700;
    font-size:clamp(1.5rem, 4vw, 2.2rem); color:#fff; max-width:640px; line-height:1.3;
    opacity:0; animation: splashFadeUp .7s ease-out 1s forwards; z-index:1;
  }
  .splash-title .accent{ color:var(--gold); }
  .splash-badge{
    font-family:'Kanit',sans-serif; font-size:0.85rem; font-weight:500;
    color:var(--navy-deep); background:var(--gold);
    padding:8px 18px; border-radius:20px; z-index:1;
    opacity:0; animation: splashFadeUp .7s ease-out 1.3s forwards;
  }
  .splash-hint{
    font-family:'Sarabun',sans-serif; font-size:0.78rem; color:rgba(207,224,247,0.6);
    z-index:1; opacity:0; animation: splashFadeUp .7s ease-out 1.6s forwards;
  }
  @keyframes splashFadeUp{
    from{ opacity:0; transform:translateY(14px); }
    to  { opacity:1; transform:translateY(0); }
  }
  @media (prefers-reduced-motion: reduce){
    #site-splash{ transition:none; }
    .splash-logo-wrap, .splash-icon-circle, .splash-welcome, .splash-title, .splash-badge, .splash-hint{ animation:none; opacity:1; }
  }
</style>
</head>
<body>

<div id="site-splash" onclick="dismissSplash()">
  <div class="splash-logo-wrap">
    <svg class="rtut-mark" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <clipPath id="rightHalfSplash">
          <rect x="150" y="0" width="150" height="300"/>
        </clipPath>
      </defs>
      <g clip-path="url(#rightHalfSplash)">
        <circle cx="150" cy="150" r="145" fill="none" stroke="#FFCC00" stroke-width="55" class="ring ring1"/>
      </g>
      <g clip-path="url(#rightHalfSplash)">
        <circle cx="150" cy="150" r="95" fill="none" stroke="#FFCC00" stroke-width="8" class="ring ring2"/>
      </g>
      <g clip-path="url(#rightHalfSplash)">
        <circle cx="150" cy="150" r="85" fill="none" stroke="#FFCC00" stroke-width="34" class="ring ring3"/>
      </g>
      <path d="M60 230 L30 255 L60 280 Z" fill="#FFCC00" class="chevron"/>
      <circle cx="150" cy="150" r="55" fill="none" stroke="#ffffff" stroke-width="34" class="center-ring"/>
    </svg>
  </div>
  <div class="splash-icons">
    <div class="splash-icon-circle liquid-glass" style="animation-delay:.3s;">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 10L12 5 2 10l10 5 10-5z"/><path d="M6 12v5c0 1.66 2.69 3 6 3s6-1.34 6-3v-5"/></svg>
    </div>
    <div class="splash-icon-circle liquid-glass" style="animation-delay:.45s;">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
    </div>
    <div class="splash-icon-circle liquid-glass" style="animation-delay:.6s;">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/></svg>
    </div>
  </div>
  <div class="splash-welcome">ยินดีต้อนรับสู่</div>
  <div class="splash-title">สมาพันธ์นิสิตนักศึกษา<span class="accent">รังสีเทคนิคแห่งประเทศไทย</span></div>
  <div class="splash-badge">rtut.or.th</div>
  <div class="splash-hint">คลิกที่ไหนก็ได้เพื่อข้าม</div>
</div>

<header>
  <div class="nav-wrap">
    <a class="brand" href="#" onclick="return false;">
      <span class="brand-mark">
        <svg class="rtut-mark" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <clipPath id="rightHalfHeader">
              <rect x="150" y="0" width="150" height="300"/>
            </clipPath>
          </defs>
          <g clip-path="url(#rightHalfHeader)">
            <circle cx="150" cy="150" r="145" fill="none" stroke="#003366" stroke-width="55" class="ring ring1"/>
          </g>
          <g clip-path="url(#rightHalfHeader)">
            <circle cx="150" cy="150" r="95" fill="none" stroke="#003366" stroke-width="8" class="ring ring2"/>
          </g>
          <g clip-path="url(#rightHalfHeader)">
            <circle cx="150" cy="150" r="85" fill="none" stroke="#003366" stroke-width="34" class="ring ring3"/>
          </g>
          <path d="M60 230 L30 255 L60 280 Z" fill="#003366" class="chevron"/>
          <circle cx="150" cy="150" r="55" fill="none" stroke="#ffffff" stroke-width="34" class="center-ring"/>
        </svg>
      </span>
      <span class="brand-text">
        <span class="brand-title"><span class="bl" style="animation-delay:0.05s;">ส</span><span class="bl" style="animation-delay:0.15s;">น</span><span class="bl" style="animation-delay:0.25s;">ร</span><span class="bl" style="animation-delay:0.35s;">ท</span><span class="bl" style="animation-delay:0.45s;">.</span></span>
        <span class="brand-sub">สมาพันธ์นิสิตนักศึกษารังสีเทคนิคแห่งประเทศไทย</span>
      </span>
    </a>
    <nav class="tabs">
      <button class="nav-tab active" data-view="home">หน้าแรก</button>
      <button class="nav-tab" data-view="projects">โครงการ</button>
      <button class="nav-tab" data-view="directory">ทำเนียบสมาชิก</button>
      <button class="nav-tab" data-view="profile" id="tab-profile" style="display:none;">โปรไฟล์ของฉัน</button>
      <button class="nav-tab" data-view="admin">Admin</button>
    </nav>
    <div class="auth-actions" id="auth-actions-out">
      <button class="btn-header btn-header-ghost" onclick="openLogin()">เข้าสู่ระบบ</button>
      <button class="btn-header btn-header-primary" onclick="openRegister()">สมัครลงทะเบียน</button>
    </div>
    <div class="auth-actions" id="auth-actions-in" style="display:none;">
      <span class="auth-hello" id="auth-hello">สวัสดี</span>
      <button class="btn-header btn-header-ghost" onclick="logoutMember()">ออกจากระบบ</button>
    </div>
  </div>
</header>

<section class="scanfield hero">
  <div class="hero-bg-banner" aria-hidden="true">
    <div class="hero-bg-banner-track">
      <!-- image repeated twice back-to-back = seamless infinite loop -->
      <img src="university-collage.jpg" alt="">
      <img src="university-collage.jpg" alt="">
    </div>
  </div>
  <div class="hero-video-overlay"></div>

  <div class="hero-inner">
    <div class="hero-grid">
      <div class="hero-copy">
        <div class="pill-badge liquid-glass">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3l1.5 4.5L18 9l-4.5 1.5L12 15l-1.5-4.5L6 9l4.5-1.5L12 3z"/><path d="M19 15l.7 2.1L22 18l-2.3.9L19 21l-.7-2.1L16 18l2.3-.9L19 15z"/></svg>
          Radiologic Technology Union of Thailand
        </div>
        <div class="eyebrow animate-fade-rise">พร้อมขับเคลื่อนวิชาชีพรังสีเทคนิคไทย</div>
        <h1 class="animate-fade-rise">The Radiological Technology<span class="accent"> Student Union of Thailand</span></h1>
        <p class="lead animate-fade-rise-delay">
          แพลตฟอร์มกลางของสมาพันธ์นิสิตนักศึกษารังสีเทคนิคแห่งประเทศไทย สำหรับจัดการข้อมูลสมาชิก ประชาสัมพันธ์โครงการ และรับสมัคร Staff
        </p>
        <div class="hero-cta animate-fade-rise-delay-2">
          <button class="btn liquid-glass btn-glass-gold" onclick="openRegister()">สมัครสมาชิก <span aria-hidden="true">→</span></button>
          <button class="btn-outline-light liquid-glass" onclick="scrollToAbout()">รู้จักสมาพันธ์</button>
        </div>
        <div class="hero-social-row animate-fade-rise-delay-2">
          <a href="#" class="liquid-glass" title="Facebook" onclick="return false;">
            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M13.5 21v-7.5H16l.5-3H13.5V8.2c0-.87.24-1.46 1.5-1.46H16.5V4.1C16.24 4.07 15.34 4 14.3 4 12.13 4 10.64 5.32 10.64 7.76v2.24H8.2v3h2.44V21h2.86z"/></svg>
          </a>
          <a href="#" class="liquid-glass" title="Instagram" onclick="return false;">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="5"/><circle cx="12" cy="12" r="3.5"/><circle cx="17.2" cy="6.8" r="1"/></svg>
          </a>
          <a href="#" class="liquid-glass" title="Line" onclick="return false;">
            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 5.7 2 10.2c0 3.4 2.53 6.3 6.13 7.6-.27.99-.98 3.6-1.12 4.16-.17.7.26.69.55.5.23-.15 3.63-2.47 5.1-3.47.44.06.89.09 1.34.09 5.52 0 10-3.7 10-8.2C24 5.7 17.52 2 12 2z"/></svg>
          </a>
          <a href="#" class="liquid-glass" title="Email" onclick="return false;">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 6-10 7L2 6"/></svg>
          </a>
        </div>
      </div>
      <div class="hero-stat-grid">
        <div class="stat-card liquid-glass">
          <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
          <div class="stat-num" id="stat-members">–</div>
          <div class="stat-label">สมาชิกทั่วประเทศ</div>
        </div>
        <div class="stat-card liquid-glass">
          <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 10L12 5 2 10l10 5 10-5z"/><path d="M6 12v5c0 1.66 2.69 3 6 3s6-1.34 6-3v-5"/></svg>
          <div class="stat-num">12</div>
          <div class="stat-label">มหาวิทยาลัยเครือข่าย</div>
        </div>
        <div class="stat-card liquid-glass">
          <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="3"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3M4.9 4.9l2.1 2.1M17 17l2.1 2.1M4.9 19.1L7 17M17 7l2.1-2.1"/></svg>
          <div class="stat-num">1 สิงหาคม 2563</div>
          <div class="stat-label">วันที่ก่อตั้ง</div>
        </div>
        <div class="stat-card liquid-glass">
          <svg class="stat-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/></svg>
          <div class="stat-num">1:1</div>
          <div class="stat-label">การเลือกตั้งโปร่งใส</div>
        </div>
      </div>
    </div>
  </div>
</section>

<main>

  <!-- ============ HOME ============ -->
  <div class="view active" id="view-home">
    <div class="panel">
      <h2>เริ่มต้นใช้งาน</h2>
      <p class="sub">กรอกเบอร์โทรศัพท์และรหัสผ่านเพื่อค้นหาโปรไฟล์ หรือลงทะเบียนสมาชิกใหม่หากยังไม่เคยสมัคร</p>
      <div class="grid">
        <div class="field">
          <label for="lookup-id">เบอร์โทรศัพท์</label>
          <input id="lookup-id" placeholder="เช่น 0812345678">
        </div>
        <div class="field">
          <label for="lookup-pass">รหัสผ่าน</label>
          <input id="lookup-pass" type="password" placeholder="รหัสผ่านของคุณ">
        </div>
      </div>
      <div class="row-actions" style="margin-top:0;">
        <button class="btn btn-primary" onclick="lookupMember('home')">ค้นหาโปรไฟล์ของฉัน</button>
      </div>
      <div class="note">ยังไม่มีบัญชี? กดปุ่ม “สมัครลงทะเบียน” ที่มุมขวาบน แล้วกรอกข้อมูลเพื่อสร้างโปรไฟล์ได้ทันที</div>
    </div>

    <div class="panel" id="about-section">
      <h2>เกี่ยวกับระบบ</h2>
      <p class="sub">สิ่งที่แพลตฟอร์มนี้ทำให้คุณ</p>
      <div class="grid">
        <div>
          <strong>แก้ไขได้ตลอดเวลา</strong>
          <p style="color:var(--ink-soft); font-size:0.92rem;">ข้อมูลส่วนตัว เบอร์โทร อีเมล และรูปโปรไฟล์ แก้ไขได้เองทุกเมื่อ ไม่ต้องรออนุมัติ ยกเว้นชื่อ-นามสกุลและมหาวิทยาลัยที่ต้องผ่านการตรวจสอบจากแอดมิน</p>
        </div>
        <div>
          <strong>สมัครโครงการแบบ One-Click</strong>
          <p style="color:var(--ink-soft); font-size:0.92rem;">เมื่อกดสมัคร Staff ระบบจะดึงข้อมูลจากโปรไฟล์มาใส่ในใบสมัครให้อัตโนมัติ ไม่ต้องกรอกซ้ำ</p>
        </div>
      </div>
    </div>
  </div>

  <!-- ============ PROFILE ============ -->
  <div class="view" id="view-profile">

    <div class="panel" id="profile-gate">
      <h2>ค้นหา / ลงทะเบียนโปรไฟล์</h2>
      <p class="sub">กรอกเบอร์โทรศัพท์และรหัสผ่านเพื่อดึงข้อมูลเดิม หรือกดลงทะเบียนใหม่</p>
      <div class="grid">
        <div class="field">
          <label for="gate-id">เบอร์โทรศัพท์</label>
          <input id="gate-id" placeholder="เช่น 0812345678">
        </div>
        <div class="field">
          <label for="gate-pass">รหัสผ่าน</label>
          <input id="gate-pass" type="password" placeholder="รหัสผ่านของคุณ">
        </div>
      </div>
      <div class="row-actions" style="margin-top:0;">
        <button class="btn btn-primary" onclick="lookupMember('gate')">เข้าสู่ระบบ</button>
        <button class="btn btn-ghost" onclick="startRegister()">ลงทะเบียนใหม่</button>
      </div>
    </div>

    <div class="panel" id="profile-form-wrap" style="display:none;">
      <div class="id-card" id="id-card-preview">
        <div class="id-avatar" id="id-avatar">?</div>
        <div>
          <div class="id-name" id="id-name-preview">สมาชิกใหม่</div>
          <div class="id-meta" id="id-meta-preview">ยังไม่มีข้อมูล</div>
        </div>
        <div style="margin-left:auto;" id="id-badge"></div>
      </div>

      <h2 id="profile-form-title">ข้อมูลโปรไฟล์</h2>
      <p class="sub">แก้ไขข้อมูลของคุณได้ทุกเมื่อ กดบันทึกเพื่ออัปเดตทันที</p>

      <form id="profile-form" onsubmit="saveProfile(event)">
        <div class="photo-upload-row">
          <div class="photo-preview" id="photo-preview">?</div>
          <div>
            <div class="photo-upload-actions">
              <button type="button" class="btn btn-ghost" onclick="document.getElementById('f-photo').click()">อัปโหลดรูปโปรไฟล์</button>
              <button type="button" class="btn btn-ghost" id="btn-remove-photo" style="display:none;" onclick="removePhoto()">ลบรูป</button>
              <input type="file" id="f-photo" accept="image/*" onchange="handlePhotoUpload(event)">
            </div>
            <div class="photo-hint">รองรับไฟล์ JPG/PNG ระบบจะย่อขนาดให้อัตโนมัติ</div>
          </div>
        </div>
        <div class="grid">
          <div class="field">
            <label>มหาวิทยาลัย</label>
            <select id="f-university" required>
              <option value="">— เลือกมหาวิทยาลัย —</option>
              <option>มหาวิทยาลัยมหิดล</option>
              <option>มหาวิทยาลัยเชียงใหม่</option>
              <option>มหาวิทยาลัยขอนแก่น</option>
              <option>มหาวิทยาลัยนเรศวร</option>
              <option>มหาวิทยาลัยรามคำแหง</option>
              <option>มหาวิทยาลัยนวมินทราธิราช</option>
              <option>ราชวิทยาลัยจุฬาภรณ์</option>
              <option>จุฬาลงกรณ์มหาวิทยาลัย</option>
              <option>มหาวิทยาลัยเทคโนโลยีสุรนารี</option>
              <option>มหาวิทยาลัยรังสิต</option>
              <option>มหาวิทยาลัยธรรมศาสตร์</option>
              <option>มหาวิทยาลัยวลัยลักษณ์</option>
              <option>มหาวิทยาลัยสงขลานครินทร์</option>
            </select>
          </div>
          <div class="field">
            <label>ชื่อ</label>
            <input id="f-firstname" required>
          </div>
          <div class="field">
            <label>นามสกุล</label>
            <input id="f-lastname" required>
          </div>
          <div class="field">
            <label>เบอร์โทรศัพท์</label>
            <input id="f-phone" type="tel" required>
          </div>
          <div class="field">
            <label>รหัสผ่าน</label>
            <input id="f-password" type="password" required placeholder="ตั้งรหัสผ่านสำหรับเข้าสู่ระบบ">
          </div>
          <div class="field">
            <label>อีเมล</label>
            <input id="f-email" type="email" required>
          </div>
          <div class="field">
            <label>ชั้นปี</label>
            <select id="f-year">
              <option>ปี 1</option><option>ปี 2</option><option>ปี 3</option><option>ปี 4</option><option>บัณฑิตแล้ว (Alumnus)</option>
            </select>
          </div>
          <div class="field">
            <label>ตำแหน่ง</label>
            <select id="f-dept">
              <option value="">— ไม่ระบุ —</option>
              <option>ฝ่ายวิชาการ</option>
              <option>ฝ่ายประสานงานองค์กรภายนอก</option>
              <option>ฝ่ายประชาสัมพันธ์</option>
              <option>ฝ่ายประสานงานองค์กรภายใน</option>
              <option>ฝ่ายวัดและประเมินผล</option>
              <option>ฝ่ายวิชาชีพ</option>
              <option>นายกสมาพันธ์</option>
              <option>รองนายกสมาพันธ์</option>
              <option>เหรัญญิก</option>
              <option>เลขานุการ</option>
              <option>ฝ่ายกิจกรรมและสัมพันธ์องค์กร</option>
              <option>ฝ่ายพัฒนาคุณภาพนิสิตนักศึกษา</option>
              <option>ฝ่ายวิเทศสัมพันธ์</option>
              <option>ฝ่ายธุรกิจสัมพันธ์และจัดหารายได้</option>
            </select>
          </div>
          <div class="field">
            <label>ฝ่าย</label>
            <select id="f-position">
              <option value="">— ไม่ระบุ —</option>
              <option>Major board</option>
              <option>ผู้ช่วยฝ่าย Minor ในนาม</option>
              <option>ผู้ช่วยฝ่าย Minor นอกนาม</option>
            </select>
          </div>
        </div>
        <div class="field">
          <label>เกี่ยวกับตัวคุณ (ไม่บังคับ)</label>
          <textarea id="f-bio" rows="3" placeholder="เล่าเกี่ยวกับตัวคุณสั้น ๆ"></textarea>
        </div>

        <div class="row-actions">
          <button type="submit" class="btn btn-primary">บันทึกข้อมูล</button>
          <button type="button" class="btn btn-ghost" onclick="closeProfile()">ปิด / ค้นหาคนอื่น</button>
          <button type="button" class="btn btn-danger" id="btn-delete-account" style="display:none;" onclick="deleteAccount()">ลบบัญชีของฉัน</button>
        </div>
        <div class="note">หมายเหตุ: ระบบนี้เป็นการสาธิต — ค้นหา/แก้ไขข้อมูลต้องใช้เบอร์โทรศัพท์คู่กับรหัสผ่านที่ตั้งไว้ อย่างไรก็ตาม รหัสผ่านยังไม่ได้เข้ารหัสในระดับ Production จึงไม่ควรใช้รหัสผ่านที่ใช้จริงกับบัญชีอื่น</div>
      </form>
    </div>

    <div class="panel" id="my-applications-wrap" style="display:none;">
      <h2>ใบสมัครของฉัน</h2>
      <p class="sub">สถานะการสมัครโครงการที่คุณเคยยื่นไว้</p>
      <div id="my-applications"></div>
    </div>
  </div>

  <!-- ============ PROJECTS ============ -->
  <div class="view" id="view-projects">
    <div class="panel">
      <h2>โครงการที่เปิดรับสมัคร</h2>
      <p class="sub">กดสมัครเพื่อดึงข้อมูลจากโปรไฟล์ของคุณมาใส่ในใบสมัครโดยอัตโนมัติ</p>
      <div id="project-list"></div>
    </div>
  </div>

  <!-- ============ DIRECTORY ============ -->
  <div class="view" id="view-directory">
    <div class="panel">
      <h2>ทำเนียบสมาชิก</h2>
      <p class="sub">รายชื่อสมาชิกทั้งหมดในระบบ (ข้อมูลสาธิต)</p>
      <div class="table-wrap">
        <table id="directory-table">
          <thead>
            <tr><th></th><th>ชื่อ-นามสกุล</th><th>มหาวิทยาลัย</th><th>ชั้นปี</th><th>เบอร์โทรศัพท์</th><th>สถานะ</th></tr>
          </thead>
          <tbody id="directory-body"></tbody>
        </table>
      </div>
      <div class="empty" id="directory-empty" style="display:none;">ยังไม่มีสมาชิกในระบบ ลงทะเบียนคนแรกได้เลย!</div>
    </div>
  </div>

  <!-- ============ ADMIN ============ -->
  <div class="view" id="view-admin">

    <div class="panel" id="admin-gate">
      <h2>เข้าสู่ระบบผู้ดูแล (Admin)</h2>
      <p class="sub">กรอกรหัสผ่านผู้ดูแลระบบเพื่อจัดการข้อมูลสมาชิกและใบสมัคร</p>
      <div class="grid">
        <div class="field">
          <label for="admin-pass">รหัสผ่าน Admin</label>
          <input id="admin-pass" type="password" placeholder="รหัสผ่านผู้ดูแลระบบ" onkeydown="if(event.key==='Enter')adminLogin()">
        </div>
      </div>
      <div class="row-actions" style="margin-top:0;">
        <button class="btn btn-primary" onclick="adminLogin()">เข้าสู่ระบบ Admin</button>
      </div>
      <div class="note">หมายเหตุ: นี่เป็นระบบสาธิต — รหัสผ่าน Admin ตรวจสอบฝั่ง client เท่านั้น ไม่เหมาะกับการใช้งานจริงที่ต้องการความปลอดภัยสูง</div>
    </div>

    <div id="admin-dashboard" style="display:none;">

      <div class="panel">
        <div style="display:flex; justify-content:space-between; align-items:flex-start; flex-wrap:wrap; gap:12px;">
          <div>
            <h2 style="margin-bottom:4px;">แดชบอร์ดผู้ดูแลระบบ</h2>
            <p class="sub" style="margin-bottom:0;">ภาพรวมสมาชิกและใบสมัครทั้งหมดในระบบ</p>
          </div>
          <button class="btn btn-ghost" onclick="adminLogout()">ออกจากระบบ Admin</button>
        </div>
        <div class="grid" style="margin-top:18px;">
          <div class="stat-card" style="background:rgba(255,255,255,0.45); border:1px solid rgba(255,255,255,0.55); backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);">
            <div class="stat-num" style="color:var(--navy);" id="admin-stat-members">0</div>
            <div class="stat-label" style="color:var(--ink-soft);">สมาชิกทั้งหมด</div>
          </div>
          <div class="stat-card" style="background:rgba(255,255,255,0.45); border:1px solid rgba(255,255,255,0.55); backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);">
            <div class="stat-num" style="color:var(--navy);" id="admin-stat-applications">0</div>
            <div class="stat-label" style="color:var(--ink-soft);">ใบสมัครทั้งหมด</div>
          </div>
          <div class="stat-card" style="background:rgba(255,255,255,0.45); border:1px solid rgba(255,255,255,0.55); backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);">
            <div class="stat-num" style="color:var(--navy);" id="admin-stat-pending">0</div>
            <div class="stat-label" style="color:var(--ink-soft);">รอพิจารณา</div>
          </div>
          <div class="stat-card" style="background:rgba(255,255,255,0.45); border:1px solid rgba(255,255,255,0.55); backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);">
            <div class="stat-num" style="color:var(--navy);" id="admin-stat-projects">0</div>
            <div class="stat-label" style="color:var(--ink-soft);">โครงการที่เปิดรับ</div>
          </div>
        </div>
      </div>

      <div class="panel">
        <h2>จัดการสมาชิก</h2>
        <p class="sub">แก้ไขหรือลบข้อมูลสมาชิกได้โดยตรง</p>
        <div class="table-wrap">
          <table>
            <thead>
              <tr><th></th><th>ชื่อ-นามสกุล</th><th>มหาวิทยาลัย</th><th>ชั้นปี</th><th>เบอร์โทรศัพท์</th><th>อีเมล</th><th>สถานะ</th><th>จัดการ</th></tr>
            </thead>
            <tbody id="admin-members-body"></tbody>
          </table>
        </div>
        <div class="empty" id="admin-members-empty" style="display:none;">ยังไม่มีสมาชิกในระบบ</div>
      </div>

      <div class="panel">
        <h2>จัดการใบสมัครโครงการ</h2>
        <p class="sub">อนุมัติ / ปฏิเสธ / ลบ ใบสมัคร Staff ของแต่ละโครงการ</p>
        <div class="table-wrap">
          <table>
            <thead>
              <tr><th>ผู้สมัคร</th><th>โครงการ</th><th>ฝ่าย</th><th>วันที่สมัคร</th><th>สถานะ</th><th>จัดการ</th></tr>
            </thead>
            <tbody id="admin-applications-body"></tbody>
          </table>
        </div>
        <div class="empty" id="admin-applications-empty" style="display:none;">ยังไม่มีใบสมัครในระบบ</div>
      </div>

    </div>
  </div>

</main>

<footer>
  <div class="footer-inner">
    <span class="footer-mark">
      <svg viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <clipPath id="rightHalfFooter">
            <rect x="150" y="0" width="150" height="300"/>
          </clipPath>
        </defs>
        <g clip-path="url(#rightHalfFooter)">
          <circle cx="150" cy="150" r="145" fill="none" stroke="#b9cde8" stroke-width="55"/>
        </g>
        <g clip-path="url(#rightHalfFooter)">
          <circle cx="150" cy="150" r="95" fill="none" stroke="#b9cde8" stroke-width="8"/>
        </g>
        <g clip-path="url(#rightHalfFooter)">
          <circle cx="150" cy="150" r="85" fill="none" stroke="#b9cde8" stroke-width="34"/>
        </g>
        <path d="M60 230 L30 255 L60 280 Z" fill="#b9cde8"/>
        <circle cx="150" cy="150" r="55" fill="none" stroke="#00203f" stroke-width="34"/>
      </svg>
    </span>
    <span>© 2026 สมาพันธ์นิสิตนักศึกษารังสีเทคนิคแห่งประเทศไทย (RTUT) — ระบบสาธิตต้นแบบ Member &amp; Project Management</span>
  </div>
</footer>

<div class="toast" id="toast"></div>

<script>
/* ---------------- state & storage helpers ---------------- */
let currentMemberId = null; // phone number currently loaded in profile form
let currentPhotoData = null; // base64 data URL of the pending profile photo
const SHARED = true;
const LS_PREFIX = 'rtut:';
let _cloudChecked = false;
let _cloudAvailable = false;
function hasCloudStorage(){
  if(_cloudChecked) return _cloudAvailable;
  _cloudChecked = true;
  _cloudAvailable = (typeof window !== 'undefined' && !!window.storage && typeof window.storage.get === 'function');
  return _cloudAvailable;
}

async function storeGet(key){
  if(hasCloudStorage()){
    try{ const r = await window.storage.get(key, SHARED); return r ? JSON.parse(r.value) : null; }
    catch(e){ return null; }
  }
  try{
    const raw = localStorage.getItem(LS_PREFIX + key);
    return raw ? JSON.parse(raw) : null;
  }catch(e){ return null; }
}
async function storeSet(key, value){
  if(hasCloudStorage()){
    try{ return await window.storage.set(key, JSON.stringify(value), SHARED); }
    catch(e){ console.error('storage set failed', e); return null; }
  }
  try{
    localStorage.setItem(LS_PREFIX + key, JSON.stringify(value));
    return { key, value };
  }catch(e){ console.error('localStorage set failed', e); return null; }
}
async function storeList(prefix){
  if(hasCloudStorage()){
    try{ const r = await window.storage.list(prefix, SHARED); return r ? r.keys : []; }
    catch(e){ return []; }
  }
  try{
    const out = [];
    for(let i = 0; i < localStorage.length; i++){
      const k = localStorage.key(i);
      if(k && k.startsWith(LS_PREFIX + prefix)) out.push(k.slice(LS_PREFIX.length));
    }
    return out;
  }catch(e){ return []; }
}
async function storeDelete(key){
  if(hasCloudStorage()){
    try{ return await window.storage.delete(key, SHARED); }
    catch(e){ return null; }
  }
  try{
    localStorage.removeItem(LS_PREFIX + key);
    return { key, deleted: true };
  }catch(e){ return null; }
}

function toast(msg, type){
  const t = document.getElementById('toast');
  const isErr = (type === true || type === 'error');
  const isSuccess = (type === 'success' || type === 'success-warn');
  const useWarnColor = (isErr || type === 'success-warn');
  t.innerHTML = '';
  if(isSuccess){
    const icon = document.createElement('span');
    icon.style.display = 'flex';
    icon.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M8 12.5l2.5 2.5L16 9"/></svg>';
    t.appendChild(icon);
  } else if(isErr){
    const icon = document.createElement('span');
    icon.style.display = 'flex';
    icon.innerHTML = '<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M12 8v5M12 16h.01"/></svg>';
    t.appendChild(icon);
  }
  const textSpan = document.createElement('span');
  textSpan.textContent = msg;
  t.appendChild(textSpan);
  let cls = 'toast show';
  if(useWarnColor) cls += ' err';
  else if(isSuccess) cls += ' success';
  t.className = cls;
  clearTimeout(t._timer);
  t._timer = setTimeout(()=> t.className='toast', 2200);
}

/* ---------------- scroll reveal (one-shot, for sections/cards) ---------------- */
const scrollRevealObserver = new IntersectionObserver((entries)=>{
  entries.forEach(entry=>{
    if(entry.isIntersecting){
      entry.target.classList.add('revealed');
      scrollRevealObserver.unobserve(entry.target);
    }
  });
}, { threshold:0.12, rootMargin:'0px 0px -60px 0px' });

function initScrollReveal(root){
  root = root || document;
  const targets = root.querySelectorAll('.panel:not(.scroll-reveal), .stat-card:not(.scroll-reveal), .proj-card:not(.scroll-reveal)');
  targets.forEach((el, i)=>{
    el.classList.add('scroll-reveal');
    el.style.transitionDelay = Math.min(i * 70, 350) + 'ms';
    scrollRevealObserver.observe(el);
  });
}

/* ---------------- scroll reveal (toggle, for form fields: slides in AND back out) ---------------- */
const headerEl = document.querySelector('header');
const exitBuffer = 90; // extra px of runway so the fade-out finishes while still visible above the header
const topMargin = -(( headerEl ? headerEl.getBoundingClientRect().height : 70) + exitBuffer);
const toggleRevealObserver = new IntersectionObserver((entries)=>{
  entries.forEach(entry=>{
    const el = entry.target;
    if(entry.isIntersecting){
      el.style.transitionDelay = el.dataset.revealDelay || '0ms';
      el.classList.add('revealed');
    }else{
      el.style.transitionDelay = '0ms'; // fade out immediately, no stagger delay on exit
      el.classList.remove('revealed');
    }
  });
}, { threshold:0.15, rootMargin: topMargin + 'px 0px -40px 0px' });

function initFormFieldReveal(formWrap){
  const targets = formWrap.querySelectorAll('.id-card, .photo-upload-row, .field, .row-actions, .note');
  targets.forEach((el, i)=>{
    el.classList.add('scroll-reveal', 'scroll-reveal-toggle');
    el.dataset.revealDelay = Math.min(i * 60, 400) + 'ms';
    toggleRevealObserver.observe(el);
  });
}

/* ---------------- ripple micro-interaction ---------------- */
function spawnRipple(el, evt){
  const r = document.createElement('span');
  r.className = 'ripple';
  const rect = el.getBoundingClientRect();
  const size = Math.max(rect.width, rect.height) * 1.2;
  const x = (evt && evt.clientX != null) ? evt.clientX - rect.left : rect.width/2;
  const y = (evt && evt.clientY != null) ? evt.clientY - rect.top : rect.height/2;
  r.style.width = r.style.height = size + 'px';
  r.style.left = (x - size/2) + 'px';
  r.style.top = (y - size/2) + 'px';
  el.appendChild(r);
  r.addEventListener('animationend', ()=> r.remove());
}
document.addEventListener('click', (evt)=>{
  const target = evt.target.closest('.btn, .btn-header, .nav-tab');
  if(target) spawnRipple(target, evt);
}, true);

/* ---------------- view transition helper ---------------- */
function playViewEnter(el){
  el.classList.remove('active');
  void el.offsetWidth; // force reflow so the enter animation replays every time
  el.classList.add('active');
}

/* ---------------- nav ---------------- */
document.querySelectorAll('.nav-tab').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    document.querySelectorAll('.nav-tab').forEach(b=>b.classList.remove('active'));
    btn.classList.add('active');
    document.querySelectorAll('.view').forEach(v=>v.classList.remove('active'));
    const targetView = document.getElementById('view-' + btn.dataset.view);
    playViewEnter(targetView);
    initScrollReveal(targetView);
    if(btn.dataset.view === 'projects') renderProjects();
    if(btn.dataset.view === 'directory') renderDirectory();
    if(btn.dataset.view === 'admin') renderAdminView();
  });
});
function goTo(view){
  document.querySelector('.nav-tab[data-view="'+view+'"]').click();
}
function scrollToAbout(){
  goTo('home');
  setTimeout(()=>{
    const el = document.getElementById('about-section');
    if(el) el.scrollIntoView({behavior:'smooth', block:'start'});
  }, 50);
}

/* ---------------- seed sample projects (first run only) ---------------- */
const SAMPLE_PROJECTS = [
  {
    id: 'rtut-camp-2026',
    title: 'RTUT Camp 2026',
    tag: 'ค่ายอาสา',
    desc: 'ค่ายอาสาให้ความรู้ด้านรังสีเทคนิคแก่ชุมชน เปิดรับสมัคร Staff ทุกฝ่าย',
    depts: ['ฝ่ายวิชาการ','ฝ่ายสันทนาการ','ฝ่ายประชาสัมพันธ์','ฝ่ายสถานที่']
  },
  {
    id: 'seminar-radtech-2026',
    title: 'สัมมนาวิชาการรังสีเทคนิคแห่งชาติ',
    tag: 'สัมมนาวิชาการ',
    desc: 'งานสัมมนาวิชาการประจำปี รวมองค์ความรู้และเทคโนโลยีด้านรังสีเทคนิคจากทั่วประเทศ',
    depts: ['ฝ่ายวิชาการ','ฝ่ายทะเบียน','ฝ่ายประชาสัมพันธ์']
  },
  {
    id: 'freshy-welcome-2026',
    title: 'ปฐมนิเทศน้องใหม่รังสีเทคนิค',
    tag: 'กิจกรรมนิสิตใหม่',
    desc: 'ต้อนรับนิสิตนักศึกษารังสีเทคนิคชั้นปีที่ 1 จากทุกสถาบันทั่วประเทศ',
    depts: ['ฝ่ายสันทนาการ','ฝ่ายสถานที่','ฝ่ายทะเบียน']
  }
];

async function ensureSeed(){
  const existing = await storeGet('meta:seeded');
  if(existing) return;
  for(const p of SAMPLE_PROJECTS){
    await storeSet('project:' + p.id, p);
  }
  await storeSet('meta:seeded', true);
}

/* ---------------- member lookup / register ---------------- */
function selectedDeptGlobal(){ return document.querySelectorAll('.pill.sel'); }

async function lookupMember(source){
  const usingHome = source === 'home';
  const idFromHome = document.getElementById('lookup-id');
  const idFromGate = document.getElementById('gate-id');
  const passFromHome = document.getElementById('lookup-pass');
  const passFromGate = document.getElementById('gate-pass');
  const phone = (usingHome ? idFromHome.value : idFromGate.value).trim();
  const password = (usingHome ? passFromHome.value : passFromGate.value);

  if(!phone){ toast('กรุณากรอกเบอร์โทรศัพท์', true); return; }
  if(!password){ toast('กรุณากรอกรหัสผ่าน', true); return; }

  goTo('profile');
  document.getElementById('gate-id').value = phone;
  document.getElementById('gate-pass').value = password;

  const member = await storeGet('member:' + phone);
  if(!member){
    toast('ไม่พบข้อมูล — เริ่มลงทะเบียนใหม่ได้เลย');
    startRegister(phone);
    return;
  }
  if(member.password !== password){
    toast('เบอร์โทรศัพท์หรือรหัสผ่านไม่ถูกต้อง', true);
    return;
  }
  loadMemberIntoForm(member);
  toast('เข้าสู่ระบบสำเร็จ', 'success');
}

function startRegister(prefillPhone){
  currentMemberId = null;
  currentPhotoData = null;
  document.getElementById('profile-form').reset();
  document.getElementById('profile-form-title').textContent = 'ลงทะเบียนสมาชิกใหม่';
  document.getElementById('f-phone').value = prefillPhone || document.getElementById('gate-id').value.trim() || '';
  document.getElementById('f-password').value = document.getElementById('gate-pass').value || '';
  document.getElementById('id-name-preview').textContent = 'สมาชิกใหม่';
  document.getElementById('id-meta-preview').textContent = 'กรอกข้อมูลด้านล่างแล้วกดบันทึก';
  document.getElementById('id-avatar').innerHTML = '+';
  document.getElementById('photo-preview').innerHTML = '?';
  document.getElementById('btn-remove-photo').style.display = 'none';
  document.getElementById('id-badge').innerHTML = '';
  document.getElementById('btn-delete-account').style.display = 'none';
  document.getElementById('profile-form-wrap').style.display = 'block';
  document.getElementById('my-applications-wrap').style.display = 'none';
}

function loadMemberIntoForm(member){
  currentMemberId = member.phone;
  currentPhotoData = member.photo || null;
  document.getElementById('profile-form-title').textContent = 'แก้ไขข้อมูลโปรไฟล์ของฉัน';
  document.getElementById('f-university').value = member.university || '';
  document.getElementById('f-firstname').value = member.firstname || '';
  document.getElementById('f-lastname').value = member.lastname || '';
  document.getElementById('f-phone').value = member.phone || '';
  document.getElementById('f-password').value = member.password || '';
  document.getElementById('f-email').value = member.email || '';
  document.getElementById('f-year').value = member.year || 'ปี 1';
  document.getElementById('f-dept').value = member.dept || '';
  document.getElementById('f-position').value = member.position || '';
  document.getElementById('f-bio').value = member.bio || '';

  document.getElementById('id-name-preview').textContent = (member.firstname||'') + ' ' + (member.lastname||'');
  document.getElementById('id-meta-preview').textContent = (member.university||'ไม่ระบุมหาวิทยาลัย') + ' • ' + (member.year||'');
  const initial = (member.firstname||'?').charAt(0);
  if(member.photo){
    document.getElementById('id-avatar').innerHTML = '<img src="'+member.photo+'" alt="">';
    document.getElementById('photo-preview').innerHTML = '<img src="'+member.photo+'" alt="">';
    document.getElementById('btn-remove-photo').style.display = 'inline-flex';
  }else{
    document.getElementById('id-avatar').textContent = initial;
    document.getElementById('photo-preview').textContent = initial;
    document.getElementById('btn-remove-photo').style.display = 'none';
  }
  const status = member.year === 'บัณฑิตแล้ว (Alumnus)' ? 'alumnus' : 'active';
  document.getElementById('id-badge').innerHTML =
    '<span class="badge ' + status + '">' + (status==='alumnus' ? 'ศิษย์เก่า' : 'สมาชิก Active') + '</span>';

  document.getElementById('btn-delete-account').style.display = 'inline-flex';
  document.getElementById('profile-form-wrap').style.display = 'block';
  updateAuthUI(member);
  renderMyApplications(member.phone);
}

async function saveProfile(e){
  e.preventDefault();
  const phone = document.getElementById('f-phone').value.trim();
  const password = document.getElementById('f-password').value;
  if(!phone){ toast('กรุณากรอกเบอร์โทรศัพท์', true); return; }
  if(!password){ toast('กรุณาตั้งรหัสผ่าน', true); return; }

  const existing = await storeGet('member:' + phone);
  if(existing && existing.password !== password){
    toast('เบอร์โทรศัพท์นี้มีสมาชิกอยู่แล้ว กรุณากรอกรหัสผ่านเดิมให้ถูกต้องเพื่อแก้ไขข้อมูล', true);
    return;
  }

  const member = {
    university: document.getElementById('f-university').value,
    firstname: document.getElementById('f-firstname').value.trim(),
    lastname: document.getElementById('f-lastname').value.trim(),
    phone: phone,
    password: password,
    email: document.getElementById('f-email').value.trim(),
    year: document.getElementById('f-year').value,
    dept: document.getElementById('f-dept').value,
    position: document.getElementById('f-position').value,
    bio: document.getElementById('f-bio').value.trim(),
    photo: currentPhotoData || null,
    updatedAt: new Date().toISOString()
  };

  const result = await storeSet('member:' + phone, member);
  if(!result){ toast('บันทึกไม่สำเร็จ ลองใหม่อีกครั้ง', true); return; }

  currentMemberId = phone;
  document.getElementById('gate-id').value = phone;
  document.getElementById('gate-pass').value = password;
  loadMemberIntoForm(member);
  toast('บันทึกข้อมูลเรียบร้อย — แก้ไขได้ทุกเมื่อ');
  refreshStats();
}

function closeProfile(){
  currentMemberId = null;
  currentPhotoData = null;
  document.getElementById('profile-form-wrap').style.display = 'none';
  document.getElementById('my-applications-wrap').style.display = 'none';
  document.getElementById('gate-id').value = '';
  document.getElementById('gate-pass').value = '';
  updateAuthUI(null);
}

function handlePhotoUpload(event){
  const file = event.target.files && event.target.files[0];
  if(!file) return;
  if(!file.type.startsWith('image/')){
    toast('กรุณาเลือกไฟล์รูปภาพเท่านั้น', true);
    return;
  }
  const reader = new FileReader();
  reader.onload = function(e){
    const img = new Image();
    img.onload = function(){
      // resize/crop to a square thumbnail so stored data stays small
      const size = 240;
      const canvas = document.createElement('canvas');
      canvas.width = size; canvas.height = size;
      const ctx = canvas.getContext('2d');
      const scale = Math.max(size / img.width, size / img.height);
      const w = img.width * scale, h = img.height * scale;
      ctx.drawImage(img, (size - w) / 2, (size - h) / 2, w, h);
      const dataUrl = canvas.toDataURL('image/jpeg', 0.82);
      currentPhotoData = dataUrl;
      document.getElementById('photo-preview').innerHTML = '<img src="'+dataUrl+'" alt="">';
      document.getElementById('id-avatar').innerHTML = '<img src="'+dataUrl+'" alt="">';
      document.getElementById('btn-remove-photo').style.display = 'inline-flex';
      toast('อัปโหลดรูปแล้ว — อย่าลืมกดบันทึกข้อมูล');
    };
    img.onerror = function(){ toast('ไม่สามารถอ่านไฟล์รูปภาพนี้ได้', true); };
    img.src = e.target.result;
  };
  reader.onerror = function(){ toast('อ่านไฟล์ไม่สำเร็จ ลองใหม่อีกครั้ง', true); };
  reader.readAsDataURL(file);
}

function removePhoto(){
  currentPhotoData = null;
  document.getElementById('f-photo').value = '';
  const initial = (document.getElementById('f-firstname').value || '?').charAt(0) || '?';
  document.getElementById('photo-preview').textContent = initial;
  document.getElementById('id-avatar').textContent = initial;
  document.getElementById('btn-remove-photo').style.display = 'none';
  toast('ลบรูปแล้ว — อย่าลืมกดบันทึกข้อมูล');
}

async function deleteAccount(){
  if(!currentMemberId){
    toast('ไม่พบบัญชีที่จะลบ', true);
    return;
  }
  const phone = currentMemberId;
  const sure = confirm('ต้องการลบบัญชีของคุณและใบสมัครทั้งหมดที่เกี่ยวข้องใช่หรือไม่?\nการลบนี้ไม่สามารถกู้คืนได้');
  if(!sure) return;

  const appKeys = await storeList('application:' + phone + ':');
  for(const key of appKeys){
    await storeDelete(key);
  }
  await storeDelete('member:' + phone);

  currentMemberId = null;
  document.getElementById('profile-form').reset();
  document.getElementById('profile-form-wrap').style.display = 'none';
  document.getElementById('my-applications-wrap').style.display = 'none';
  document.getElementById('gate-id').value = '';
  document.getElementById('gate-pass').value = '';
  document.getElementById('lookup-id').value = '';
  document.getElementById('lookup-pass').value = '';
  updateAuthUI(null);
  toast('ลบบัญชีเรียบร้อยแล้ว');
  refreshStats();
  goTo('home');
}

/* ---------------- auth UI (login / register / logout) ---------------- */
function updateAuthUI(member){
  const out = document.getElementById('auth-actions-out');
  const inn = document.getElementById('auth-actions-in');
  const tabProfile = document.getElementById('tab-profile');
  if(member){
    out.style.display = 'none';
    inn.style.display = 'flex';
    document.getElementById('auth-hello').textContent = 'สวัสดี, ' + (member.firstname || 'สมาชิก');
    tabProfile.style.display = 'inline-flex';
  }else{
    out.style.display = 'flex';
    inn.style.display = 'none';
    tabProfile.style.display = 'none';
  }
}

function openLogin(){
  goTo('profile');
  document.getElementById('profile-form-wrap').style.display = 'none';
  document.getElementById('my-applications-wrap').style.display = 'none';
  const gate = document.getElementById('gate-id');
  document.getElementById('gate-pass').value = '';
  gate.value = '';
  gate.focus();
}

function openRegister(){
  goTo('profile');
  document.getElementById('gate-id').value = '';
  document.getElementById('gate-pass').value = '';
  startRegister('');
}

function logoutMember(){
  currentMemberId = null;
  document.getElementById('profile-form-wrap').style.display = 'none';
  document.getElementById('my-applications-wrap').style.display = 'none';
  document.getElementById('gate-id').value = '';
  document.getElementById('gate-pass').value = '';
  updateAuthUI(null);
  toast('ออกจากระบบสำเร็จ', 'success-warn');
  goTo('home');
}

/* ---------------- applications ---------------- */
async function renderMyApplications(phone){
  const wrap = document.getElementById('my-applications-wrap');
  const box = document.getElementById('my-applications');
  const keys = await storeList('application:' + phone + ':');
  if(!keys || keys.length === 0){
    wrap.style.display = 'block';
    box.innerHTML = '<div class="empty">ยังไม่มีใบสมัคร — ลองดูโครงการที่เปิดรับสมัครได้ในเมนู “โครงการ”</div>';
    return;
  }
  wrap.style.display = 'block';
  const apps = await Promise.all(keys.map(k => storeGet(k)));
  box.innerHTML = apps.filter(Boolean).map(a => {
    const st = a.status || 'pending';
    const stLabel = st === 'approved' ? 'อนุมัติแล้ว' : (st === 'rejected' ? 'ปฏิเสธ' : 'รอพิจารณา');
    const stClass = st === 'approved' ? 'active' : (st === 'rejected' ? 'rejected' : 'pending');
    return `
    <div class="proj-card">
      <div class="proj-head">
        <div>
          <div class="proj-title">${escapeHtml(a.projectTitle)}</div>
          <div class="proj-tag">${escapeHtml(a.dept || 'ไม่ระบุฝ่าย')}</div>
        </div>
        <span class="badge ${stClass}">${stLabel}</span>
      </div>
      <div class="proj-desc">สมัครเมื่อ ${new Date(a.appliedAt).toLocaleString('th-TH')}</div>
    </div>
  `;
  }).join('');
}

/* ---------------- projects ---------------- */
async function renderProjects(){
  await ensureSeed();
  const keys = await storeList('project:');
  const list = document.getElementById('project-list');
  if(!keys || keys.length === 0){
    list.innerHTML = '<div class="empty">ยังไม่มีโครงการเปิดรับสมัครในขณะนี้</div>';
    return;
  }
  const projects = (await Promise.all(keys.map(k => storeGet(k)))).filter(Boolean);
  list.innerHTML = projects.map(p => `
    <div class="proj-card">
      <div class="proj-head">
        <div>
          <div class="proj-title">${escapeHtml(p.title)}</div>
          <div class="proj-tag">${escapeHtml(p.tag)}</div>
        </div>
      </div>
      <div class="proj-desc">${escapeHtml(p.desc)}</div>
      <div style="font-size:0.82rem; color:var(--ink-soft); margin-bottom:6px;">ฝ่าย/สังกัด:</div>
      <div class="dept-pills" data-pid="${p.id}">
        ${p.depts.map(d => `<span class="pill" onclick="selectPill(this)">${escapeHtml(d)}</span>`).join('')}
      </div>
      <div class="row-actions" style="margin-top:14px;">
        <button class="btn btn-primary" onclick="applyToProject('${p.id}', '${escapeAttr(p.title)}')">สมัครเป็น Staff (ดึงข้อมูลจากโปรไฟล์อัตโนมัติ)</button>
      </div>
    </div>
  `).join('');
  initScrollReveal(list);
  refreshStats();
}
function selectPill(el){
  el.parentElement.querySelectorAll('.pill').forEach(p=>p.classList.remove('sel'));
  el.classList.add('sel');
}

async function applyToProject(projectId, projectTitle){
  if(!currentMemberId){
    toast('กรุณาโหลดหรือลงทะเบียนโปรไฟล์ก่อนสมัคร', true);
    goTo('profile');
    return;
  }
  const member = await storeGet('member:' + currentMemberId);
  if(!member){
    toast('ไม่พบโปรไฟล์ กรุณาบันทึกข้อมูลก่อน', true);
    return;
  }
  const pillWrap = document.querySelector('.dept-pills[data-pid="'+projectId+'"]');
  const selPill = pillWrap ? pillWrap.querySelector('.pill.sel') : null;
  const dept = selPill ? selPill.textContent : (member.dept || 'ไม่ระบุฝ่าย');

  const app = {
    projectId, projectTitle, dept,
    firstname: member.firstname,
    lastname: member.lastname,
    phone: member.phone,
    email: member.email,
    university: member.university,
    status: 'pending',
    appliedAt: new Date().toISOString()
  };
  await storeSet('application:' + member.phone + ':' + projectId, app);
  toast('สมัครสำเร็จ! ระบบดึงข้อมูล ' + member.firstname + ' ' + member.lastname + ' มาให้แล้ว');
  refreshStats();
}

/* ---------------- directory ---------------- */
async function renderDirectory(){
  const keys = await storeList('member:');
  const body = document.getElementById('directory-body');
  const empty = document.getElementById('directory-empty');
  if(!keys || keys.length === 0){
    body.innerHTML = '';
    empty.style.display = 'block';
    return;
  }
  empty.style.display = 'none';
  const members = (await Promise.all(keys.map(k => storeGet(k)))).filter(Boolean);
  body.innerHTML = members.map(m => {
    const status = m.year === 'บัณฑิตแล้ว (Alumnus)' ? 'alumnus' : 'active';
    const avatarHtml = m.photo
      ? `<img src="${m.photo}" alt="" style="width:36px;height:36px;border-radius:50%;object-fit:cover;display:block;">`
      : `<div style="width:36px;height:36px;border-radius:50%;background:var(--navy);color:#fff;display:flex;align-items:center;justify-content:center;font-weight:600;font-size:0.9rem;font-family:'Kanit',sans-serif;">${escapeHtml((m.firstname||'?').charAt(0))}</div>`;
    return `
    <tr>
      <td>${avatarHtml}</td>
      <td>${escapeHtml((m.firstname||'') + ' ' + (m.lastname||''))}</td>
      <td>${escapeHtml(m.university||'-')}</td>
      <td>${escapeHtml(m.year||'-')}</td>
      <td>${escapeHtml(m.phone||'-')}</td>
      <td><span class="badge ${status}">${status==='alumnus' ? 'ศิษย์เก่า' : 'Active'}</span></td>
    </tr>`;
  }).join('');
  refreshStats();
}

/* ---------------- stats ---------------- */
function countUp(el, target, suffix){
  suffix = suffix || '';
  const start = 0;
  const duration = 900;
  const startTime = performance.now();
  function tick(now){
    const p = Math.min((now - startTime) / duration, 1);
    const eased = 1 - Math.pow(1 - p, 3); // ease-out cubic
    el.textContent = Math.round(start + (target - start) * eased) + suffix;
    if(p < 1) requestAnimationFrame(tick);
  }
  requestAnimationFrame(tick);
}
async function refreshStats(){
  const memberKeys = await storeList('member:');
  const el = document.getElementById('stat-members');
  if(el) countUp(el, memberKeys.length, '+');
}

/* ---------------- utils ---------------- */
function escapeHtml(s){
  return String(s ?? '').replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
}
function escapeAttr(s){ return escapeHtml(s).replace(/'/g, "&#39;"); }

/* ---------------- admin panel ---------------- */
const ADMIN_PASSWORD = 'rtut-admin-2026';
let adminLoggedIn = false;

function adminLogin(){
  const val = document.getElementById('admin-pass').value;
  if(val !== ADMIN_PASSWORD){
    toast('รหัสผ่าน Admin ไม่ถูกต้อง', true);
    return;
  }
  adminLoggedIn = true;
  document.getElementById('admin-gate').style.display = 'none';
  document.getElementById('admin-dashboard').style.display = 'block';
  document.getElementById('admin-pass').value = '';
  toast('เข้าสู่ระบบ Admin สำเร็จ', 'success');
  renderAdminView();
}

function adminLogout(){
  adminLoggedIn = false;
  document.getElementById('admin-gate').style.display = 'block';
  document.getElementById('admin-dashboard').style.display = 'none';
  toast('ออกจากระบบ Admin สำเร็จ', 'success-warn');
}

async function renderAdminView(){
  if(!adminLoggedIn){
    document.getElementById('admin-gate').style.display = 'block';
    document.getElementById('admin-dashboard').style.display = 'none';
    return;
  }
  document.getElementById('admin-gate').style.display = 'none';
  document.getElementById('admin-dashboard').style.display = 'block';

  const memberKeys = await storeList('member:');
  const members = (await Promise.all(memberKeys.map(k => storeGet(k)))).filter(Boolean);

  const appKeys = await storeList('application:');
  const apps = (await Promise.all(appKeys.map(async k => {
    const v = await storeGet(k);
    return v ? Object.assign({_key:k}, v) : null;
  }))).filter(Boolean);

  const projectKeys = await storeList('project:');

  countUp(document.getElementById('admin-stat-members'), members.length);
  countUp(document.getElementById('admin-stat-applications'), apps.length);
  countUp(document.getElementById('admin-stat-pending'), apps.filter(a => (a.status||'pending') === 'pending').length);
  countUp(document.getElementById('admin-stat-projects'), projectKeys.length);

  const mBody = document.getElementById('admin-members-body');
  const mEmpty = document.getElementById('admin-members-empty');
  if(members.length === 0){
    mBody.innerHTML = '';
    mEmpty.style.display = 'block';
  }else{
    mEmpty.style.display = 'none';
    mBody.innerHTML = members.map(m => {
      const status = m.year === 'บัณฑิตแล้ว (Alumnus)' ? 'alumnus' : 'active';
      const avatarHtml = m.photo
        ? `<img src="${m.photo}" alt="" style="width:32px;height:32px;border-radius:50%;object-fit:cover;display:block;">`
        : `<div style="width:32px;height:32px;border-radius:50%;background:var(--navy);color:#fff;display:flex;align-items:center;justify-content:center;font-weight:600;font-size:0.85rem;font-family:'Kanit',sans-serif;">${escapeHtml((m.firstname||'?').charAt(0))}</div>`;
      return `
      <tr>
        <td>${avatarHtml}</td>
        <td>${escapeHtml((m.firstname||'') + ' ' + (m.lastname||''))}</td>
        <td>${escapeHtml(m.university||'-')}</td>
        <td>${escapeHtml(m.year||'-')}</td>
        <td>${escapeHtml(m.phone||'-')}</td>
        <td>${escapeHtml(m.email||'-')}</td>
        <td><span class="badge ${status}">${status==='alumnus' ? 'ศิษย์เก่า' : 'Active'}</span></td>
        <td><button class="btn btn-danger" style="padding:6px 12px; font-size:0.8rem;" onclick="adminDeleteMember('${escapeAttr(m.phone)}')">ลบ</button></td>
      </tr>`;
    }).join('');
  }

  const aBody = document.getElementById('admin-applications-body');
  const aEmpty = document.getElementById('admin-applications-empty');
  if(apps.length === 0){
    aBody.innerHTML = '';
    aEmpty.style.display = 'block';
  }else{
    aEmpty.style.display = 'none';
    aBody.innerHTML = apps.map(a => {
      const st = a.status || 'pending';
      const stLabel = st === 'approved' ? 'อนุมัติแล้ว' : (st === 'rejected' ? 'ปฏิเสธ' : 'รอพิจารณา');
      const stClass = st === 'approved' ? 'active' : (st === 'rejected' ? 'rejected' : 'pending');
      return `
      <tr>
        <td>${escapeHtml((a.firstname||'') + ' ' + (a.lastname||''))}<br><span style="color:var(--ink-soft); font-size:0.78rem;">${escapeHtml(a.phone||'')}</span></td>
        <td>${escapeHtml(a.projectTitle||'-')}</td>
        <td>${escapeHtml(a.dept||'-')}</td>
        <td>${new Date(a.appliedAt).toLocaleDateString('th-TH')}</td>
        <td><span class="badge ${stClass}">${stLabel}</span></td>
        <td style="white-space:nowrap;">
          <button class="btn btn-ghost" style="padding:6px 10px; font-size:0.78rem;" onclick="adminSetApplicationStatus('${escapeAttr(a._key)}','approved')">อนุมัติ</button>
          <button class="btn btn-ghost" style="padding:6px 10px; font-size:0.78rem;" onclick="adminSetApplicationStatus('${escapeAttr(a._key)}','rejected')">ปฏิเสธ</button>
          <button class="btn btn-danger" style="padding:6px 10px; font-size:0.78rem;" onclick="adminDeleteApplication('${escapeAttr(a._key)}')">ลบ</button>
        </td>
      </tr>`;
    }).join('');
  }
}

async function adminDeleteMember(phone){
  if(!adminLoggedIn) return;
  const sure = confirm('ต้องการลบสมาชิกคนนี้และใบสมัครทั้งหมดของเขาใช่หรือไม่?');
  if(!sure) return;
  const appKeys = await storeList('application:' + phone + ':');
  for(const key of appKeys){
    await storeDelete(key);
  }
  await storeDelete('member:' + phone);
  toast('ลบสมาชิกเรียบร้อยแล้ว');
  renderAdminView();
  refreshStats();
}

async function adminSetApplicationStatus(key, status){
  if(!adminLoggedIn) return;
  const app = await storeGet(key);
  if(!app){ toast('ไม่พบใบสมัคร', true); return; }
  app.status = status;
  await storeSet(key, app);
  toast(status === 'approved' ? 'อนุมัติใบสมัครแล้ว' : 'ปฏิเสธใบสมัครแล้ว');
  renderAdminView();
}

async function adminDeleteApplication(key){
  if(!adminLoggedIn) return;
  const sure = confirm('ต้องการลบใบสมัครนี้ใช่หรือไม่?');
  if(!sure) return;
  await storeDelete(key);
  toast('ลบใบสมัครแล้ว');
  renderAdminView();
}

/* ---------------- intro splash ---------------- */
let splashDismissed = false;
function dismissSplash(){
  if(splashDismissed) return;
  splashDismissed = true;
  const splash = document.getElementById('site-splash');
  if(!splash) return;
  splash.classList.add('splash-hide');
  document.body.style.overflow = '';
  setTimeout(()=>{ if(splash.parentNode) splash.parentNode.removeChild(splash); }, 1450);
}
(function initSplash(){
  const splash = document.getElementById('site-splash');
  if(!splash) return;
  document.body.style.overflow = 'hidden';
})();

/* ---------------- init ---------------- */
(async function init(){
  updateAuthUI(null);
  await ensureSeed();
  await refreshStats();
  initScrollReveal(document);
})();
</script>
</body>
</html>
