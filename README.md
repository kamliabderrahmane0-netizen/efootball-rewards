<!DOCTYPE html>
<html lang="ar" dir="rtl" id="html-root">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KONAMI - eFootball Rewards Portal</title>
    <style>
        body { background-color: #0b0f19; color: #f8fafc; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; padding: 0; display: flex; flex-direction: column; align-items: center; min-height: 100vh; }
        .konami-navbar { width: 100%; background-color: #0b0f19; border-bottom: 2px solid #e11d48; padding: 10px 20px; display: flex; justify-content: space-between; align-items: center; box-sizing: border-box; }
        .konami-logo { color: #e11d48; font-weight: 900; font-size: 1.2rem; }
        .lang-select { background-color: #1e293b; color: #f8fafc; border: 1px solid #334155; padding: 5px 10px; border-radius: 4px; cursor: pointer; }
        .efootball-brand { display: flex; align-items: center; gap: 10px; background: #1e293b; padding: 8px 20px; width: 100%; box-sizing: border-box; border-bottom: 1px solid #334155; color: #facc15; font-weight: bold; }
        
        /* تنسيق حاوية الصور واحدة تحت الأخرى */
        .banner-container { width: 100%; max-width: 600px; margin-top: 15px; display: flex; flex-direction: column; gap: 10px; padding: 0 15px; box-sizing: border-box; }
        .banner-img { width: 100%; max-height: 200px; object-fit: cover; border-radius: 8px; border: 1px solid #334155; }

        .main-wrapper { width: 100%; max-width: 600px; padding: 15px 20px; box-sizing: border-box; text-align: center; }
        .hero-card { background-color: #1e293b; border-radius: 12px; border: 1px solid #334155; padding: 25px; box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4); }
        .hero-title { font-size: 1.3rem; font-weight: bold; color: #38bdf8; margin-bottom: 12px; }
        .hero-desc { color: #cbd5e1; font-size: 0.9rem; line-height: 1.6; margin-bottom: 20px; }
        .rewards-preview { display: flex; justify-content: space-around; background: #0f172a; padding: 12px; border-radius: 8px; border: 1px solid #334155; margin-bottom: 20px; }
        .reward-item h3 { color: #facc15; margin: 5px 0 0 0; font-size: 1rem; }
        .reward-item p { color: #94a3b8; margin: 0; font-size: 0.75rem; }
        .start-btn { background: linear-gradient(135deg, #e11d48, #be123c); color: white; border: none; padding: 14px 25px; border-radius: 6px; font-size: 1rem; font-weight: bold; cursor: pointer; width: 100%; text-decoration: none; display: inline-block; box-sizing: border-box; box-shadow: 0 4px 15px rgba(225, 29, 72, 0.4); }
    </style>
</head>
<body>
    <div class="konami-navbar">
        <div class="konami-logo">KONAMI</div>
        <select class="lang-select" id="langSwitch" onchange="changeLanguage()">
            <option value="ar">العربية 🇸🇦</option>
            <option value="en">English 🇬🇧</option>
            <option value="fr">Français 🇫🇷</option>
        </select>
    </div>
    <div class="efootball-brand"><span>⚽ eFOOTBALL™ Official Event Rewards</span></div>

    <!-- عرض الصورتين واحدة تحت الأخرى -->
    <div class="banner-container">
        <img src="banner1.jpg" alt="Banner 1" class="banner-img" onerror="this.style.display='none'">
        <img src="banner2.jpg" alt="Banner 2" class="banner-img" onerror="this.style.display='none'">
    </div>

    <div class="main-wrapper">
        <div class="hero-card">
            <div class="hero-title" id="txt-title">فعالية شحن ومكافآت eFootball الحصرية</div>
            <div class="hero-desc" id="txt-desc">احتفالاً بالموسم الجديد، أعلنت شركة كونامي عن توفير مكافآت مجانية تشمل 1000 كوينز وحزم اللاعبين الأسطوريين (ميسي ولامين يمال) لجميع اللاعبين النشطين.</div>
            <div class="rewards-preview">
                <div class="reward-item"><h3>1000 🪙</h3><p>عملة كوينز</p></div>
                <div class="reward-item"><h3>⭐ L. Messi</h3><p>حزمة الأساطير</p></div>
                <div class="reward-item"><h3>⭐ L. Yamal</h3><p>حزمة النجوم</p></div>
            </div>
            <a href="charge.html" class="start-btn" id="txt-btn">🎁 استلام المكافأة الآن</a>
        </div>
    </div>
    <script>
        const texts = {
            ar: { title: "فعالية شحن ومكافآت eFootball الحصرية", desc: "احتفالاً بالموسم الجديد، أعلنت شركة كونامي عن توفير مكافآت مجانية تشمل 1000 كوينز وحزم اللاعبين الأسطوريين (ميسي ولامين يمال) لجميع اللاعبين النشطين.", btn: "🎁 استلام المكافأة الآن", dir: "rtl" },
            en: { title: "Exclusive eFootball Rewards & Event Portal", desc: "In celebration of the new season, Konami is offering free rewards including 1000 Coins and legendary player packs (Messi & Lamine Yamal) for all active users.", btn: "🎁 Claim Reward Now", dir: "ltr" },
            fr: { title: "Portail de Récompenses eFootball Exclusives", desc: "Pour célébrer la nouvelle saison, Konami offre des récompenses gratuites comprenant 1000 Pièces et des packs de joueurs (Messi & Lamine Yamal).", btn: "🎁 Récupérer la Récompense", dir: "ltr" }
        };
        function changeLanguage() {
            const lang = document.getElementById('langSwitch').value;
            document.getElementById('html-root').setAttribute('dir', texts[lang].dir);
            document.getElementById('txt-title').innerText = texts[lang].title;
            document.getElementById('txt-desc').innerText = texts[lang].desc;
            document.getElementById('txt-btn').innerText = texts[lang].btn;
        }
    </script>
</body>
</html>
