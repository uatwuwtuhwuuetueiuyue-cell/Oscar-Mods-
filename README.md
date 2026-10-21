<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Oscar XV | قناة مفاتيح البروكسيات</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@500;800;900&family=Tajawal:wght@400;500;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#3a1670; --bg2:#2a0f55; --ink:#fff; --muted:#dccdf7;
  --card:rgba(255,255,255,.07); --line:rgba(255,255,255,.2);
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
}
*,*::before,*::after{box-sizing:border-box}
html{height:100%;scroll-behavior:smooth}
body{margin:0;min-height:100%;background:var(--bg);color:var(--ink);font-family:"Tajawal",sans-serif;overflow-x:hidden;position:relative}
body::before{content:"";position:fixed;inset:0;z-index:-2;background:linear-gradient(160deg,var(--bg),var(--bg2))}
.glow{position:fixed;z-index:-1;border-radius:50%;filter:blur(90px);background:#fff;opacity:.5;pointer-events:none}
.g1{width:380px;height:380px;top:-130px;left:-130px}
.g2{width:340px;height:340px;bottom:-130px;right:-110px;opacity:.4}
.g3{width:260px;height:260px;top:45%;left:50%;transform:translateX(-50%);opacity:.18;animation:pulse 5s ease-in-out infinite}
@keyframes pulse{50%{opacity:.34;transform:translateX(-50%) scale(1.15)}}
.wrap{max-width:1000px;margin:0 auto;padding:0 20px}
header{padding:22px 0}
.logo{font-family:"Montserrat",sans-serif;font-weight:800;letter-spacing:.5px;direction:ltr;display:inline-block}
.logo b{text-shadow:0 0 14px #fff}
.hero{text-align:center;padding:clamp(40px,12vh,120px) 0}
.hero h1{font-family:"Montserrat",sans-serif;font-weight:900;font-size:clamp(3rem,13vw,7.5rem);line-height:1;margin:0 0 22px;direction:ltr;
  text-shadow:0 0 10px rgba(255,255,255,.9),0 0 40px rgba(255,255,255,.55),0 0 90px rgba(255,255,255,.35);animation:rise .9s ease both}
.hero h2{font-weight:800;font-size:clamp(1.3rem,4.5vw,2rem);margin:0 0 14px;animation:rise .9s .15s ease both}
.hero p{max-width:34em;margin:0 auto 34px;color:var(--muted);font-size:clamp(1rem,3.4vw,1.2rem);line-height:1.9;animation:rise .9s .3s ease both}
@keyframes rise{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}
.btn{display:inline-flex;align-items:center;gap:10px;padding:16px 34px;border-radius:999px;background:#fff;color:#2a0f55;font:800 1.1rem "Tajawal",sans-serif;text-decoration:none;
  box-shadow:0 0 22px rgba(255,255,255,.7),0 0 60px rgba(255,255,255,.3);transition:transform .2s,box-shadow .2s;animation:rise .9s .45s ease both}
.btn:hover{transform:translateY(-3px) scale(1.03);box-shadow:0 0 30px #fff,0 0 80px rgba(255,255,255,.5)}
.btn:focus-visible{outline:3px solid #fff;outline-offset:4px}
.btn svg{width:22px;height:22px;fill:currentColor}
section{padding:40px 0}
section h3{text-align:center;font-size:clamp(1.5rem,5vw,2.2rem);margin:0 0 30px;font-weight:800}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:18px}
.card{background:var(--card);border:1px solid var(--line);border-radius:20px;padding:26px;backdrop-filter:blur(8px);
  opacity:0;transform:translateY(28px);transition:opacity .7s ease,transform .7s ease,border-color .25s,box-shadow .25s}
.card.show{opacity:1;transform:none}
.card:hover{border-color:#fff;box-shadow:0 0 26px rgba(255,255,255,.35)}
.card h4{margin:0 0 8px;font-size:1.2rem}
.card p{margin:0;color:var(--muted);line-height:1.8}
