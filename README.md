import os, zipfile, shutil

base = "/mnt/data/global_sports_center"
os.makedirs(base, exist_ok=True)

html = """<!doctype html>
<html lang="zh-Hant">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>全球体育中心</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>

<header class="header">
<div>
<h1>全球体育中心</h1>
<p>GLOBAL SPORTS CENTER</p>
</div>

<a class="tg-btn" href="https://t.me/JXC118" target="_blank">官方频道</a>
</header>

<section class="hero">
<div class="hero-content">

<span class="tag">官方入口 · 体育娱乐 · 充值福利</span>

<h2>吉祥坊 · 1win · 1xBet</h2>

<p>
官方体育娱乐平台入口，精选热门赛事、平台活动与充值福利。
</p>

<div class="hero-buttons">
<a href="#platforms" class="primary">查看平台</a>
<a href="https://t.me/JXC118" class="secondary" target="_blank">加入频道</a>
</div>

</div>
</section>

<section class="platforms" id="platforms">

<div class="card">
<div class="logo">吉祥坊</div>
<span class="label">老牌体育平台</span>
<p>稳定运营，适合体育与真人娱乐用户。</p>
<a href="https://www.astrowb888.com" target="_blank" class="enter">进入官网</a>
</div>

<div class="card">
<div class="logo">1win</div>
<span class="label">热门平台</span>
<p>注册快捷，适合手机端用户快速体验。</p>
<a href="https://lkmn.cc/77e5" target="_blank" class="enter">进入官网</a>
</div>

<div class="card">
<div class="logo">1xBet</div>
<span class="label">国际品牌</span>
<p>覆盖体育、电子、真人等多种玩法。</p>
<a href="https://reffpa.com/L?tag=d_5590520m_1260c_188bet&site=5590520&ad=1260" target="_blank" class="enter">进入官网</a>
</div>

</section>

<section class="advantages">

<div class="adv">
<h3>体育活动</h3>
<p>热门赛事、串关活动、VIP福利集中展示。</p>
</div>

<div class="adv">
<h3>充值优势</h3>
<p>充值流程简单、到账体验快、适合新用户。</p>
</div>

<div class="adv">
<h3>福利频道</h3>
<p>进入 Telegram 查看最新活动与客服说明。</p>
</div>

</section>

<footer>
<a href="https://t.me/JXC118" target="_blank">加入官方频道获取最新福利</a>
<p>仅限18+用户，活动规则以平台官方页面为准。</p>
</footer>

</body>
</html>
"""

css = """*{margin:0;padding:0;box-sizing:border-box}
body{
font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
background:#07111f;
color:#fff;
}
.header{
display:flex;
justify-content:space-between;
align-items:center;
padding:22px 28px;
background:rgba(5,10,18,.88);
border-bottom:1px solid rgba(255,255,255,.08);
position:sticky;
top:0;
}
.header h1{
font-size:30px;
font-weight:900;
}
.header p{
font-size:12px;
margin-top:4px;
color:#8fa2bf;
letter-spacing:.14em;
}
.tg-btn{
background:#1d8fff;
padding:12px 18px;
border-radius:14px;
color:#fff;
text-decoration:none;
font-weight:800;
}
.hero{
height:620px;
background:
linear-gradient(rgba(4,8,18,.55),rgba(4,8,18,.82)),
url('https://images.unsplash.com/photo-1547347298-4074fc3086f0?q=80&w=1600&auto=format&fit=crop') center/cover;
display:flex;
align-items:center;
padding:0 7%;
}
.hero-content{
max-width:700px;
}
.tag{
display:inline-block;
padding:10px 16px;
border-radius:999px;
background:rgba(255,215,100,.12);
border:1px solid rgba(255,215,100,.35);
color:#ffd56c;
font-weight:800;
margin-bottom:24px;
}
.hero h2{
font-size:72px;
line-height:1.05;
font-weight:900;
}
.hero p{
margin-top:22px;
font-size:20px;
line-height:1.8;
color:#c4d0e0;
}
.hero-buttons{
display:flex;
gap:14px;
margin-top:34px;
}
.primary,.secondary,.enter{
text-decoration:none;
}
.primary{
background:linear-gradient(135deg,#ffd56c,#d88f20);
color:#111;
padding:15px 28px;
border-radius:16px;
font-weight:900;
}
.secondary{
background:rgba(255,255,255,.08);
border:1px solid rgba(255,255,255,.12);
color:#fff;
padding:15px 28px;
border-radius:16px;
font-weight:900;
}
.platforms{
max-width:1200px;
margin:auto;
padding:70px 24px 30px;
display:grid;
grid-template-columns:repeat(3,1fr);
gap:20px;
}
.card{
background:#0d1b2f;
border:1px solid rgba(255,255,255,.08);
border-radius:26px;
padding:28px;
}
.logo{
font-size:34px;
font-weight:900;
}
.label{
display:inline-block;
margin-top:14px;
background:#ffd56c;
color:#111;
padding:6px 12px;
border-radius:999px;
font-size:13px;
font-weight:800;
}
.card p{
margin-top:18px;
line-height:1.8;
color:#b5c3d5;
min-height:70px;
}
.enter{
display:block;
margin-top:22px;
background:#1d8fff;
text-align:center;
padding:15px;
border-radius:16px;
font-weight:900;
color:#fff;
}
.advantages{
max-width:1200px;
margin:auto;
padding:20px 24px 80px;
display:grid;
grid-template-columns:repeat(3,1fr);
gap:20px;
}
.adv{
background:#0d1b2f;
border:1px solid rgba(255,255,255,.08);
padding:28px;
border-radius:24px;
}
.adv h3{
font-size:26px;
margin-bottom:14px;
}
.adv p{
line-height:1.8;
color:#b5c3d5;
}
footer{
padding:50px 24px 80px;
text-align:center;
border-top:1px solid rgba(255,255,255,.06);
}
footer a{
display:inline-block;
background:linear-gradient(135deg,#ffd56c,#d88f20);
color:#111;
padding:16px 30px;
border-radius:16px;
font-weight:900;
text-decoration:none;
}
footer p{
margin-top:24px;
color:#7f92ac;
}
@media(max-width:900px){
.hero{
height:auto;
padding:100px 24px;
}
.hero h2{
font-size:48px;
}
.platforms,.advantages{
grid-template-columns:1fr;
}
.hero-buttons{
display:grid;
}
.primary,.secondary{
text-align:center;
}
}
"""

with open(os.path.join(base, "index.html"), "w", encoding="utf-8") as f:
    f.write(html)

with open(os.path.join(base, "styles.css"), "w", encoding="utf-8") as f:
    f.write(css)

zip_path = "/mnt/data/global_sports_center.zip"

with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    z.write(os.path.join(base, "index.html"), "index.html")
    z.write(os.path.join(base, "styles.css"), "styles.css")

preview_dir = "/mnt/data/global_sports_center_preview"
if os.path.exists(preview_dir):
    shutil.rmtree(preview_dir)

shutil.copytree(base, preview_dir)

print("done")
