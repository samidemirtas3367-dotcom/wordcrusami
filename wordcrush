<!DOCTYPE html> 
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ENG GAME (BİG UPDATE)</title>
    <style>
        /* ========================================
           CORE UI DESIGN & THEME ENGINE
           ========================================
        */
        :root {
            --bg-dark: #0f172a;
            --bg-light: #1e293b;
            --accent: #38bdf8;
            --panel-bg: rgba(30, 41, 59, 0.98);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --danger: #ef4444;
            --success: #22c55e;
            --gold: #fbbf24;
            --p1-color: #f87171;
            --p2-color: #60a5fa;
        }

        body {
            background: radial-gradient(circle at top right, var(--bg-light) 0%, var(--bg-dark) 100%);
            color: var(--text-main); font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex; flex-direction: column; align-items: center; justify-content: flex-start;
            margin: 0; height: 100vh; overflow: hidden; transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* --- MENÜ SİSTEMİ EKRANLARI --- */
        .screen {
            display: none; width: 100%; height: 100%; flex-direction: column; 
            align-items: center; padding-top: 40px; position: absolute; inset: 0;
            background: rgba(15, 23, 42, 0.95); backdrop-filter: blur(25px); overflow-y: auto; z-index: 10;
        }
        #main-menu { display: flex; z-index: 20; }
        #game-screen, #quiz-screen { background: transparent; backdrop-filter: none; z-index: 5; }

        .menu-header { text-align: center; margin-bottom: 40px; }
        .menu-title { font-size: 50px; color: var(--accent); letter-spacing: 5px; text-shadow: 0 0 20px var(--accent); margin: 0; }
        .menu-sub { color: var(--text-muted); font-size: 16px; text-transform: uppercase; letter-spacing: 3px; }

        /* BUTONLAR */
        .big-btn {
            background: var(--panel-bg); border: 2px solid var(--accent); border-radius: 15px;
            color: #fff; padding: 20px 40px; font-size: 24px; font-weight: 900; letter-spacing: 2px;
            cursor: pointer; transition: 0.3s; width: 300px; margin-bottom: 20px; text-transform: uppercase;
        }
        .big-btn:hover { background: var(--accent); color: #000; box-shadow: 0 0 25px var(--accent); transform: scale(1.05); }
        
        .back-btn { background: transparent; border: 2px solid #64748b; color: #94a3b8; margin-top: 20px; }
        .back-btn:hover { background: #64748b; color: #fff; box-shadow: 0 0 15px #64748b; }

        .nav-btn { padding: 10px 20px; border-radius: 10px; border: none; font-weight: 900; cursor: pointer; transition: 0.2s; }
        .btn-exit { background: #475569; color: white; }
        .btn-finish { background: var(--danger); color: white; box-shadow: 0 0 15px rgba(239, 68, 68, 0.4); }

        /* ÜNİTE KARTLARI */
        .card-container { width: 100%; max-width: 700px; padding: 0 20px; box-sizing: border-box; }
        .unit-card {
            background: var(--panel-bg); border: 2px solid var(--accent); border-radius: 15px;
            padding: 20px; margin-bottom: 15px; cursor: pointer; transition: 0.3s ease; position: relative; overflow: hidden;
        }
        .unit-card:hover { transform: scale(1.02) translateY(-5px); box-shadow: 0 10px 30px rgba(0,0,0,0.5), 0 0 15px var(--accent); }
        .unit-card h2 { margin: 0 0 10px 0; font-size: 26px; color: #fff; }
        .unit-card hr { border: 0; height: 1px; background: var(--accent); opacity: 0.4; margin-bottom: 10px; }
        .unit-card p { margin: 0; color: var(--text-muted); font-size: 15px; }

        /* MODLAR VE AYARLAR */
        .mods-grid, .settings-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; max-width: 600px; width: 100%; }
        .mod-btn {
            background: #1e293b; border: 2px solid var(--accent); border-radius: 15px;
            color: #fff; padding: 20px; cursor: pointer; font-weight: 900; font-size: 18px;
            transition: 0.3s; text-transform: uppercase; display: flex; align-items: center; justify-content: center; gap: 10px;
        }
        .mod-btn:hover, .mod-btn.active { background: var(--accent); color: #000; box-shadow: 0 0 20px var(--accent); }

        .info-box {
            background: rgba(0,0,0,0.5); border: 1px solid var(--accent); border-radius: 10px;
            padding: 20px; margin-top: 30px; max-width: 600px; text-align: center; color: var(--gold); font-size: 18px;
        }

        /* --- IN-GAME INTERFACE (WordMatch & Quiz) --- */
        .ui-top { position: absolute; top: 25px; left: 25px; display: flex; gap: 15px; z-index: 100; }
        
        .scoreboard {
            display: flex; justify-content: space-around; width: 85%; background: var(--panel-bg);
            padding: 15px; border-radius: 20px; border: 2px solid rgba(255,255,255,0.1); margin-bottom: 25px; margin-top: 60px;
        }
        .stat-box { text-align: center; }
        .stat-val { display: block; font-size: 32px; font-weight: 900; color: var(--accent); }
        .stat-lbl { font-size: 12px; color: var(--text-muted); text-transform: uppercase; }

        /* QUIZ UI */
        .quiz-container { width: 90%; max-width: 800px; margin-top: 20px; }
        .quiz-question { background: var(--panel-bg); border: 3px solid var(--accent); border-radius: 20px; padding: 40px; font-size: 32px; text-align: center; margin-bottom: 30px; box-shadow: 0 0 20px rgba(0,0,0,0.5); }
        .quiz-options { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
        .quiz-opt-btn {
            background: #1e293b; border: 2px solid #475569; border-radius: 15px; padding: 25px;
            font-size: 24px; color: #fff; cursor: pointer; transition: 0.2s; font-weight: bold;
        }
        .quiz-opt-btn:hover { background: var(--accent); color: #000; border-color: var(--accent); transform: translateY(-5px); }
        
        /* --- BATTLE MODE UI --- */
        #battle-screen { flex-direction: row; padding: 0; background: #000; overflow: hidden; }
        .battle-side { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; position: relative; transition: 0.3s; height: 100%; }
        .p1-side { border-right: 4px solid #334155; background: linear-gradient(to right, #1a0505, #000); }
        .p2-side { background: linear-gradient(to left, #050a1a, #000); }
        
        .vs-divider { position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%); font-size: 80px; font-weight: 900; color: #fff; text-shadow: 0 0 30px var(--accent); z-index: 100; pointer-events: none; font-style: italic; }
        .battle-q-zone { position: absolute; top: 30px; width: 70%; background: var(--panel-bg); padding: 20px; border-radius: 20px; border: 2px solid var(--accent); text-align: center; font-size: 32px; font-weight: bold; z-index: 50; left: 15%; }
        
        .battle-options { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; width: 85%; max-width: 500px; }
        .battle-btn { padding: 30px 10px; font-size: 22px; font-weight: bold; border-radius: 15px; border: 3px solid rgba(255,255,255,0.1); cursor: pointer; color: white; transition: 0.2s; background: rgba(255,255,255,0.05); }
        .p1-btn:hover { background: var(--p1-color); color: #000; transform: scale(1.05); }
        .p2-btn:hover { background: var(--p2-color); color: #000; transform: scale(1.05); }
        
        .battle-score { font-size: 80px; font-weight: 900; margin-bottom: 30px; }
        .p1-text { color: var(--p1-color); }
        .p2-text { color: var(--p2-color); }
        
        .win-flash { animation: winGlow 0.5s infinite alternate; }
        @keyframes winGlow { from { box-shadow: inset 0 0 50px rgba(34, 197, 94, 0.5); } to { box-shadow: inset 0 0 100px var(--success); } }

        /* HATA & DOĞRU EFEKTLERİ */
        .wrong-flash { background: var(--danger) !important; animation: shake 0.3s; border-color: #fff !important; }
        .correct-flash { background: var(--success) !important; border-color: #fff !important; color: #000 !important; }
        @keyframes shake { 0%, 100% { transform: translateX(0); } 25% { transform: translateX(10px); } 75% { transform: translateX(-10px); } }

        /* GAME ENGINE GRIDS (WordMatch) */
        .game-world { display: flex; gap: 50px; }
        .grid-wrap h3 { text-align: center; color: var(--accent); letter-spacing: 4px; margin-bottom: 10px; }
        .game-grid {
            display: grid; grid-template-columns: repeat(3, 115px); grid-template-rows: repeat(5, 80px);
            gap: 12px; background: rgba(0,0,0,0.5); padding: 18px; border-radius: 25px;
            border: 4px solid #334155; position: relative;
        }
        .tile {
            width: 115px; height: 80px; display: flex; align-items: center; justify-content: center;
            border-radius: 14px; cursor: pointer; font-size: 13px; font-weight: 900;
            transition: 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275); text-align: center;
            box-shadow: 0 6px 0 rgba(0,0,0,0.4); text-transform: uppercase; padding: 5px; box-sizing: border-box; position: absolute;
        }
        .tile:hover { filter: brightness(1.2); transform: translateY(-5px); }
        .active-sel { border: 4px solid #fff !important; transform: scale(1.1) !important; z-index: 100; box-shadow: 0 0 25px #fff; }

        .c-0 { background: linear-gradient(135deg, #f87171, #991b1b); }
        .c-1 { background: linear-gradient(135deg, #60a5fa, #1e40af); }
        .c-2 { background: linear-gradient(135deg, #4ade80, #14532d); }
        .c-3 { background: linear-gradient(135deg, #fbbf24, #b45309); color: #000; }
        .tr-tile { background: #1e293b; color: #94a3b8; border: 1px solid #334155; }

        @keyframes popOut { 0% { scale: 1; opacity: 1; } 50% { scale: 1.5; filter: brightness(2); } 100% { scale: 0; opacity: 0; } }
        @keyframes fire-glow { 0% { box-shadow: 0 0 10px #ff4500, 0 0 20px #ff0000; } 100% { box-shadow: 0 0 20px #ffd700, 0 0 40px #ff4500; } }
        @keyframes gravityDrop { 0% { transform: translateY(-92px); } 100% { transform: translateY(0); } }
        
        .gravity-fall { animation: gravityDrop 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; }
        .pop { animation: popOut 0.4s forwards; pointer-events: none; }
        .fire-pop { animation: fire-glow 0.4s alternate infinite, popOut 0.4s forwards; border: 4px solid red; }

        #toast, #msg-popup { position: fixed; top: 30%; font-weight: 900; display: none; z-index: 5000; text-shadow: 0 0 20px #000; text-align: center; }
        #toast { font-size: 60px; color: gold; }
        #msg-popup { font-size: 45px; }

        /* END GAME MODALS */
        .end-screen {
            display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.98);
            z-index: 9999; flex-direction: column; align-items: center; justify-content: center; text-align: center; padding: 40px;
        }
        .end-title { font-size: 60px; color: var(--accent); margin-bottom: 20px; }
        .end-quote { font-size: 24px; color: #fff; font-style: italic; max-width: 800px; margin-bottom: 40px; }
    </style>
</head>
<body>

<div id="main-menu" class="screen">
    <div class="menu-header">
        <h1 class="menu-title">ENG GAME</h1>
        <span class="menu-sub">(BİG UPDATE)</span>
    </div>
    <button class="big-btn" onclick="showScreen('mode-menu')">▶ BAŞLA</button>
    <button class="big-btn" onclick="showScreen('mods-menu')">🎨 MODLAR</button>
    <button class="big-btn" onclick="showScreen('settings-menu')">⚙️ AYARLAR</button>
</div>

<div id="mode-menu" class="screen">
    <div class="menu-header">
        <h1 class="menu-title">MOD SEÇİMİ</h1>
        <span class="menu-sub">Nasıl Oynamak İstiyorsun?</span>
    </div>
    <button class="big-btn" onclick="selectMode('wordmatch')">🧩 WORD MATCH</button>
    <button class="big-btn" onclick="selectMode('quiz')" style="border-color: #fbbf24; color: #fbbf24;">📝 QUICK QUIZ</button>
    <button class="big-btn" onclick="selectMode('battle')" style="border-color: #ef4444; color: #ef4444;">⚔️ BATTLE MODE (2P)</button>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<div id="unit-menu" class="screen">
    <div class="menu-header">
        <h1 class="menu-title">ÜNİTE SEÇİMİ</h1>
        <span class="menu-sub">Test edilecek konuyu seç</span>
    </div>
    <div class="card-container" id="unit-root"></div>
    <button class="big-btn back-btn" onclick="showScreen('mode-menu')">GERİ DÖN</button>
</div>

<div id="mods-menu" class="screen">
    <div class="menu-header">
        <h1 class="menu-title">MODLAR</h1>
        <span class="menu-sub">Oyun Görünümünü Değiştir</span>
    </div>
    <div class="mods-grid">
        <button class="mod-btn" id="btn-theme-classic" onclick="applyTheme('classic')">🌑 Classic</button>
        <button class="mod-btn" id="btn-theme-subnautica" onclick="applyTheme('subnautica')">🌊 Subnautica</button>
        <button class="mod-btn" id="btn-theme-cs2" onclick="applyTheme('cs2')">🔫 CS2 Global</button>
        <button class="mod-btn" id="btn-theme-alastor" onclick="applyTheme('alastor')" style="border-color: #ef4444; color: #ef4444;">📻 Alastor</button>
        <button class="mod-btn" id="btn-theme-vox" onclick="applyTheme('vox')" style="border-color: #06b6d4; color: #06b6d4;">📺 VoxTek</button>
    </div>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<div id="settings-menu" class="screen">
    <div class="menu-header">
        <h1 class="menu-title">AYARLAR</h1>
        <span class="menu-sub">Cihaz Optimizasyonu</span>
    </div>
    <div class="settings-grid">
        <button class="mod-btn" id="btn-dev-pc" onclick="setDevice('pc')">💻 PC</button>
        <button class="mod-btn" id="btn-dev-tahta" onclick="setDevice('tahta')">🏫 Akıllı Tahta</button>
    </div>
    <div id="device-info" class="info-box">
        Klavye ve fare kullanımı için optimize edildi. Hover (üzerine gelme) efektleri aktiftir.
    </div>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<div id="game-screen" class="screen">
    <div class="ui-top">
        <button class="nav-btn btn-exit" onclick="resetGame()">ANA MENÜ</button>
        <button class="nav-btn btn-finish" onclick="triggerFinal(true)">BİTİR</button>
    </div>
    <div class="scoreboard">
        <div class="stat-box"><span class="stat-lbl">Ünite</span><span id="wm-unit" class="stat-val">1</span></div>
        <div class="stat-box"><span class="stat-lbl">Skor</span><span id="wm-score" class="stat-val">0</span></div>
        <div class="stat-box"><span class="stat-lbl">Kalan</span><span id="wm-tiles" class="stat-val">15</span></div>
    </div>
    <div class="game-world">
        <div class="grid-wrap"><h3>İNGİLİZCE</h3><div id="en-grid" class="game-grid"></div></div>
        <div class="grid-wrap"><h3>TÜRKÇE</h3><div id="tr-grid" class="game-grid"></div></div>
    </div>
</div>

<div id="quiz-screen" class="screen">
    <div class="ui-top">
        <button class="nav-btn btn-exit" onclick="resetGame()">ANA MENÜ</button>
    </div>
    <div class="scoreboard">
        <div class="stat-box"><span class="stat-lbl">Ünite</span><span id="qz-unit" class="stat-val">1</span></div>
        <div class="stat-box"><span class="stat-lbl">Soru</span><span id="qz-progress" class="stat-val">1/10</span></div>
        <div class="stat-box"><span class="stat-lbl">Skor</span><span id="qz-score" class="stat-val">0</span></div>
    </div>
    <div class="quiz-container">
        <div id="quiz-q-text" class="quiz-question">Yükleniyor...</div>
        <div id="quiz-options-container" class="quiz-options">
            <button class="quiz-opt-btn" onclick="checkQuizAnswer(0)" id="q-opt-0">Seçenek 1</button>
            <button class="quiz-opt-btn" onclick="checkQuizAnswer(1)" id="q-opt-1">Seçenek 2</button>
            <button class="quiz-opt-btn" onclick="checkQuizAnswer(2)" id="q-opt-2">Seçenek 3</button>
            <button class="quiz-opt-btn" onclick="checkQuizAnswer(3)" id="q-opt-3">Seçenek 4</button>
        </div>
    </div>
</div>

<div id="battle-screen" class="screen">
    <div class="ui-top" style="top: 25px; left: 25px; z-index: 200;">
        <button class="nav-btn btn-exit" onclick="resetGame()">ANA MENÜ</button>
    </div>
    <div class="vs-divider">VS</div>
    
    <div id="battle-q-box" class="battle-q-zone">SORU YÜKLENİYOR...</div>

    <div class="battle-side p1-side" id="p1-side">
        <div class="battle-score p1-text" id="p1-score-ui">0</div>
        <div class="battle-options">
            <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 0)" id="p1-opt-0">A</button>
            <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 1)" id="p1-opt-1">B</button>
            <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 2)" id="p1-opt-2">C</button>
            <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 3)" id="p1-opt-3">D</button>
        </div>
        <h2 class="p1-text" style="margin-top:20px; font-size: 30px;">PLAYER 1</h2>
    </div>

    <div class="battle-side p2-side" id="p2-side">
        <div class="battle-score p2-text" id="p2-score-ui">0</div>
        <div class="battle-options">
            <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 0)" id="p2-opt-0">A</button>
            <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 1)" id="p2-opt-1">B</button>
            <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 2)" id="p2-opt-2">C</button>
            <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 3)" id="p2-opt-3">D</button>
        </div>
        <h2 class="p2-text" style="margin-top:20px; font-size: 30px;">PLAYER 2</h2>
    </div>
</div>

<div id="toast">MATCH-3 BONUS!</div>
<div id="end-screen" class="end-screen">
    <h1 id="end-header" class="end-title">TEBRİKLER!</h1>
    <p id="end-quote" class="end-quote">"Öğrenenlerin geleceği parlaktır."</p>
    <div style="font-size: 40px; color: var(--accent); font-weight: 900; margin-bottom: 30px;">FİNAL SKOR: <span id="end-score">0</span></div>
    <button class="nav-btn" style="background:var(--accent); color:#000; padding:20px 50px; font-size:20px;" onclick="resetGame()">ANA MENÜYE DÖN</button>
</div>

<script>
    /* ========================================
       SİSTEM DEĞİŞKENLERİ VE VERİTABANI
       ========================================
    */
    const MASTER_DICT = {
        1: { desc: "Daily routines and breakfast habits.", words: [{en:"Routine", tr:"Rutin"}, {en:"Nap", tr:"Kestirmek"}, {en:"Diary", tr:"Günlük"}, {en:"Visit", tr:"Ziyaret"}, {en:"Wake up", tr:"Uyanmak"}, {en:"Arrive", tr:"Varmak"}, {en:"Course", tr:"Kurs"}, {en:"Rest", tr:"Dinlenmek"}] },
        2: { desc: "Food, drinks and healthy life.", words: [{en:"Yummy", tr:"Lezzetli"}, {en:"Healthy", tr:"Sağlıklı"}, {en:"Cheese", tr:"Peynir"}, {en:"Butter", tr:"Tereyağı"}, {en:"Honey", tr:"Bal"}, {en:"Bagel", tr:"Simit"}, {en:"Beverage", tr:"İçecek"}, {en:"Jam", tr:"Reçel"}] },
        3: { desc: "Downtown life, streets and busy cities.", words: [{en:" Downtown", tr:"Şehir Merkezi"}, {en:"Street", tr:"Sokak"}, {en:"Skyscraper", tr:"Gökdelen"}, {en:"Crowded", tr:"Kalabalık"}, {en:"Kiosk", tr:"Büfe"}, {en:"Neighborhood", tr:"Mahalle"}, {en:"Pavement", tr:"Kaldırım"}] },
        4: { desc: "Weather conditions and moods.", words: [{en:"Weather", tr:"Hava Durumu"}, {en:"Stormy", tr:"Fırtınalı"}, {en:"Freezing", tr:"Dondurucu"}, {en:"Lightning", tr:"Şimşek"}, {en:" Mood", tr:"Ruh Hali"}, {en:"Anxious", tr:"Endişeli"}, {en:"Frightened", tr:"Korkmuş"}] },
        5: { desc: "Funfairs, bumper cars and thrill.", words: [{en:"Funfair", tr:"Lunapark"}, {en:"Ferris Wheel", tr:"Dönme Dolap"}, {en:"Bumper cars", tr:"Çarpışan araba"}, {en:"Carousel", tr:"Atlı Karınca"}, {en:"Ticket", tr:"Bilet"}, {en:"Thrilling", tr:"Heyecan verici"}, {en:"Amazing", tr:"Şaşırtıcı"}] },
        6: { desc: "Occupations and working places.", words: [{en:"Mechanic", tr:"Tamirci"}, {en:"Vet", tr:"Veteriner"}, {en:"Tailor", tr:"Terzi"}, {en:"Driver", tr:"Şoför"}, {en:"Architect", tr:"Mimar"}, {en:"Engineer", tr:"Mühendis"}, {en:"Dentist", tr:"Diş Hekimi"}] },
        7: { desc: "Vacation, seaside and sightseeing.", words: [{en:"Vacation", tr:"Tatil"}, {en:"Sightseeing", tr:"Şehir Gezisi"}, {en:" Seaside", tr:"Deniz Kenarı"}, {en:" Forest", tr:"Orman"}, {en:" Tent", tr:"Çadır"}, {en:" Skiing", tr:"Kayak yapmak"}, {en:" Hiking", tr:"Doğa yürüyüşü"}] },
        8: { desc: "Bookworms and library rules.", words: [{en:"Bookworm", tr:"Kitap Kurdu"}, {en:"Novel", tr:"Roman"}, {en:"Poetry", tr:"Şiir"}, {en:"Library", tr:"Kütüphane"}, {en:"Shelf", tr:"Raf"}, {en:"Borrow", tr:"Ödünç almak"}, {en:"Dictionary", tr:"Sözlük"}] },
        9: { desc: "Environment, saving the planet.", words: [{en:"Environment", tr:"Çevre"}, {en:"Recycle", tr:"Geri Dönüşüm"}, {en:" Pollution", tr:"Kirlilik"}, {en:"Save", tr:"Korumak"}, {en:" Litter", tr:"Çöp atmak"}, {en:" Waste", tr:"Atık"}] },
        10:{ desc: "Democracy, elections and voting process.", words: [{en:"Election", tr:"Seçim"}, {en:"Vote", tr:"Oy Vermek"}, {en:"Candidate", tr:"Aday"}, {en:"Ballot box", tr:"Sandık"}, {en:" Democracy", tr:"Demokrasi"}, {en:" Presidential", tr:"Başkanlık"}] }
    };

    let GAME_STATE = {
        mode: '', // 'wordmatch', 'quiz', veya 'battle'
        unit: 1,
        theme: 'classic',
        device: 'pc',
        score: 0,
        scoreP1: 0,
        scoreP2: 0,
        isBattleLocked: false,
        activeCount: 15,
        selectedEN: null,
        selectedTR: null,
        bonusActive: false,
        enData: null,
        trData: null
    };

    let activeGamePool = [];
    let QUIZ_STATE = { questions: [], currentIdx: 0 };
    let BATTLE_Q = null;

    /* ========================================
       SES MOTORU
       ========================================
    */
    const AUDIO_FILES = {
        classic: { correct: 'https://actions.google.com/sounds/v1/water/splash.ogg', wrong: 'https://actions.google.com/sounds/v1/alarms/beep_short.ogg', win: 'https://actions.google.com/sounds/v1/human_voices/applause.ogg' },
        cs2: { correct: 'https://actions.google.com/sounds/v1/weapons/firework_rocket_launch.ogg', wrong: 'https://actions.google.com/sounds/v1/alarms/digital_alarm_clock.ogg', win: 'https://actions.google.com/sounds/v1/science_fiction/low_fuzz_explosion.ogg' },
        subnautica: { correct: 'https://actions.google.com/sounds/v1/water/bubbles_liquid.ogg', wrong: 'https://actions.google.com/sounds/v1/alarms/sonar_ping.ogg', win: 'https://actions.google.com/sounds/v1/ambient/ocean_surf.ogg' }
    };

    function playSound(actionType) {
        let theme = GAME_STATE.theme;
        let soundSrc = (AUDIO_FILES[theme] || AUDIO_FILES['classic'])[actionType];
        if (soundSrc) {
            let sfx = new Audio(soundSrc);
            sfx.volume = 0.5;
            let p = sfx.play();
            if(p !== undefined) p.catch(() => {});
        }
    }

    /* ========================================
       MENÜ NAVİGASYON VE AYARLAR
       ========================================
    */
    function showScreen(screenId) {
        document.querySelectorAll('.screen').forEach(el => el.style.display = 'none');
        document.getElementById(screenId).style.display = 'flex';
    }

    function selectMode(mode) {
        GAME_STATE.mode = mode;
        showScreen('unit-menu');
    }

    function resetGame() {
        document.getElementById('end-screen').style.display = 'none';
        showScreen('main-menu');
    }

    // Üniteleri Render Et
    const unitRoot = document.getElementById('unit-root');
    for (let i = 1; i <= 10; i++) {
        if(!MASTER_DICT[i]) continue;
        const card = document.createElement('div');
        card.className = 'unit-card';
        card.innerHTML = `<h2>Ünite ${i}</h2><hr><p>${MASTER_DICT[i].desc}</p>`;
        card.onclick = () => startGame(i);
        unitRoot.appendChild(card);
    }

    function applyTheme(t) {
        GAME_STATE.theme = t;
        const style = document.documentElement.style;
        
        if(t==='subnautica') { style.setProperty('--accent', '#00ffff'); style.setProperty('--bg-dark', '#001a33'); style.setProperty('--panel-bg', 'rgba(0, 26, 51, 0.9)'); }
        else if(t==='cs2') { style.setProperty('--accent', '#fbbf24'); style.setProperty('--bg-dark', '#111'); style.setProperty('--panel-bg', 'rgba(20, 20, 20, 0.95)'); }
        else if(t==='alastor') { style.setProperty('--accent', '#ef4444'); style.setProperty('--bg-dark', '#2a0000'); style.setProperty('--panel-bg', 'rgba(40, 0, 0, 0.9)'); }
        else if(t==='vox') { style.setProperty('--accent', '#06b6d4'); style.setProperty('--bg-dark', '#081c24'); style.setProperty('--panel-bg', 'rgba(0, 30, 45, 0.9)'); }
        else { style.setProperty('--accent', '#38bdf8'); style.setProperty('--bg-dark', '#0f172a'); style.setProperty('--panel-bg', 'rgba(30, 41, 59, 0.98)'); }

        document.querySelectorAll('.mod-btn').forEach(btn => btn.classList.remove('active'));
        document.getElementById('btn-theme-' + t).classList.add('active');
    }

    function setDevice(type) {
        GAME_STATE.device = type;
        const info = document.getElementById('device-info');
        document.getElementById('btn-dev-pc').classList.remove('active');
        document.getElementById('btn-dev-tahta').classList.remove('active');
        document.getElementById('btn-dev-' + type).classList.add('active');

        if(type === 'tahta') {
            info.innerHTML = "🏫 <b>Akıllı Tahta Modu:</b> Dokunmatik ekranlar için optimize edildi. Hedef alanlar büyütüldü ve vurgular belirginleştirildi.";
        } else {
            info.innerHTML = "💻 <b>PC Modu:</b> Klavye ve fare kullanımı için optimize edildi. Hover (üzerine gelme) efektleri aktiftir.";
        }
    }

    applyTheme('classic');
    setDevice('pc');

    /* ========================================
       OYUN BAŞLATMA MANTIĞI
       ========================================
    */
    function startGame(unitId) {
        GAME_STATE.unit = unitId;
        GAME_STATE.score = 0;
        
        let allWords = [];
        Object.values(MASTER_DICT).forEach(u => allWords.push(...u.words));
        
        if (GAME_STATE.mode === 'wordmatch') {
            GAME_STATE.activeCount = 15;
            GAME_STATE.enData = null;
            GAME_STATE.trData = null;
            activeGamePool = [];
            let attempts = 0;
            while(activeGamePool.length < 15 && attempts < 100) {
                let rand = allWords[Math.floor(Math.random()*allWords.length)];
                if(!activeGamePool.find(x => x.en === rand.en)) activeGamePool.push(rand);
                attempts++;
            }
            showScreen('game-screen');
            updateWMUI();
            buildGrids();
        } 
        else if (GAME_STATE.mode === 'quiz') {
            let unitWords = MASTER_DICT[unitId].words;
            let selectedWords = [...unitWords].sort(()=>Math.random()-0.5).slice(0, 10);
            
            QUIZ_STATE.questions = selectedWords.map(w => {
                let options = [w.tr];
                while(options.length < 4) {
                    let randTR = allWords[Math.floor(Math.random()*allWords.length)].tr;
                    if(!options.includes(randTR)) options.push(randTR);
                }
                return { en: w.en, correct: w.tr, options: options.sort(()=>Math.random()-0.5) };
            });
            QUIZ_STATE.currentIdx = 0;
            
            showScreen('quiz-screen');
            loadQuizQuestion();
            updateQuizUI();
        }
        else if (GAME_STATE.mode === 'battle') {
            GAME_STATE.scoreP1 = 0;
            GAME_STATE.scoreP2 = 0;
            document.getElementById('p1-score-ui').innerText = "0";
            document.getElementById('p2-score-ui').innerText = "0";
            showScreen('battle-screen');
            nextBattleQuestion();
        }
    }

    /* ========================================
       BATTLE MOTORU (2 KİŞİLİK KAPIŞMA)
       ========================================
    */
    function nextBattleQuestion() {
        GAME_STATE.isBattleLocked = false;
        document.getElementById('p1-side').classList.remove('win-flash');
        document.getElementById('p2-side').classList.remove('win-flash');
        
        let unitWords = MASTER_DICT[GAME_STATE.unit].words;
        let allWords = [];
        Object.values(MASTER_DICT).forEach(u => allWords.push(...u.words));
        
        let correctObj = unitWords[Math.floor(Math.random() * unitWords.length)];
        
        let opts = [correctObj.tr];
        while(opts.length < 4) {
            let r = allWords[Math.floor(Math.random() * allWords.length)].tr;
            if(!opts.includes(r)) opts.push(r);
        }
        opts.sort(() => Math.random() - 0.5);

        BATTLE_Q = { en: correctObj.en, tr: correctObj.tr, options: opts };
        
        document.getElementById('battle-q-box').innerText = `"${BATTLE_Q.en}"`;
        
        for(let i=0; i<4; i++) {
            let btn1 = document.getElementById(`p1-opt-${i}`);
            let btn2 = document.getElementById(`p2-opt-${i}`);
            btn1.innerText = opts[i];
            btn2.innerText = opts[i];
            btn1.style.background = "";
            btn2.style.background = "";
        }
    }

    function handleBattlePress(player, optIdx) {
        if(GAME_STATE.isBattleLocked) return;
        
        let selected = BATTLE_Q.options[optIdx];
        let isCorrect = (selected === BATTLE_Q.tr);
        
        if(isCorrect) {
            GAME_STATE.isBattleLocked = true;
            playSound('correct');
            if(player === 1) {
                GAME_STATE.scoreP1 += 10;
                document.getElementById('p1-score-ui').innerText = GAME_STATE.scoreP1;
                document.getElementById('p1-side').classList.add('win-flash');
            } else {
                GAME_STATE.scoreP2 += 10;
                document.getElementById('p2-score-ui').innerText = GAME_STATE.scoreP2;
                document.getElementById('p2-side').classList.add('win-flash');
            }
            setTimeout(nextBattleQuestion, 1500);
        } else {
            playSound('wrong');
            document.getElementById(`p${player}-opt-${optIdx}`).style.background = "var(--danger)";
        }
    }

    /* ========================================
       QUICK QUIZ MOTORU
       ========================================
    */
    function loadQuizQuestion() {
        if(QUIZ_STATE.currentIdx >= QUIZ_STATE.questions.length) {
            triggerFinal(true);
            return;
        }
        let q = QUIZ_STATE.questions[QUIZ_STATE.currentIdx];
        document.getElementById('quiz-q-text').innerText = `"${q.en}" kelimesinin Türkçe anlamı nedir?`;
        for(let i=0; i<4; i++) {
            let btn = document.getElementById('q-opt-'+i);
            btn.innerText = q.options[i];
            btn.className = 'quiz-opt-btn';
            btn.disabled = false;
        }
    }

    function checkQuizAnswer(optIndex) {
        let q = QUIZ_STATE.questions[QUIZ_STATE.currentIdx];
        let btn = document.getElementById('q-opt-'+optIndex);
        let selected = btn.innerText;

        for(let i=0; i<4; i++) document.getElementById('q-opt-'+i).disabled = true;

        if (selected === q.correct) {
            btn.classList.add('correct-flash');
            GAME_STATE.score += 100;
            playSound('correct');
        } else {
            btn.classList.add('wrong-flash');
            playSound('wrong');
            for(let i=0; i<4; i++) {
                let b = document.getElementById('q-opt-'+i);
                if(b.innerText === q.correct) b.classList.add('correct-flash');
            }
        }
        updateQuizUI();
        setTimeout(() => {
            QUIZ_STATE.currentIdx++;
            loadQuizQuestion();
            updateQuizUI();
        }, 1500);
    }

    function updateQuizUI() {
        document.getElementById('qz-unit').innerText = GAME_STATE.unit;
        document.getElementById('qz-score').innerText = GAME_STATE.score;
        let progressText = (QUIZ_STATE.currentIdx + 1 > 10) ? "10/10" : `${QUIZ_STATE.currentIdx + 1}/10`;
        document.getElementById('qz-progress').innerText = progressText;
    }

    /* ========================================
       WORD MATCH MOTORU (YERÇEKİMİ İLE BİRLİKTE)
       ========================================
    */
    function buildGrids() {
        renderGrid('en-grid', 'en');
        renderGrid('tr-grid', 'tr');
    }

    function renderGrid(containerId, type) {
        const container = document.getElementById(containerId);
        container.innerHTML = '';
        
        if (!GAME_STATE[type + 'Data']) {
            let pool = [...activeGamePool].sort(() => Math.random() - 0.5);
            GAME_STATE[type + 'Data'] = [];
            for(let i=0; i<15; i++) GAME_STATE[type + 'Data'].push(pool[i]);
        }

        GAME_STATE[type + 'Data'].forEach((word, i) => {
            if (!word) return;
            const row = Math.floor(i / 3);
            const col = i % 3;
            
            const color = word.color !== undefined ? word.color : Math.floor(Math.random()*4);
            word.color = color;

            const div = document.createElement('div');
            div.innerText = type === 'en' ? word.en : word.tr;
            div.dataset.index = i;
            div.dataset.type = type;
            div.dataset.pair = word.en;
            div.dataset.color = type === 'tr' ? 'tr' : color;
            div.onclick = () => onTileClick(div);
            div.className = `tile ${type === 'tr' ? 'tr-tile' : 'c-'+color}`;
            
            div.style.left = (col * (115 + 12) + 18) + "px";
            div.style.top = (row * (80 + 12) + 18) + "px";
            
            container.appendChild(div);
        });
    }

    function onTileClick(tile) {
        if(tile.style.visibility === 'hidden') return;
        if(tile.dataset.type === 'en') {
            if(GAME_STATE.selectedEN) GAME_STATE.selectedEN.classList.remove('active-sel');
            GAME_STATE.selectedEN = tile;
        } else {
            if(GAME_STATE.selectedTR) GAME_STATE.selectedTR.classList.remove('active-sel');
            GAME_STATE.selectedTR = tile;
        }
        tile.classList.add('active-sel');
        if(GAME_STATE.selectedEN && GAME_STATE.selectedTR) checkPair();
    }

    function checkPair() {
        const en = GAME_STATE.selectedEN;
        const tr = GAME_STATE.selectedTR;
        if(en.dataset.pair === tr.dataset.pair && en.dataset.pair !== "") {
            GAME_STATE.score += 100;
            playSound('correct');
            showFeedback("DOĞRU!", "correct-flash");
            removeTilesWM(en, tr);
        } else {
            playSound('wrong');
            showFeedback("YANLIŞ!", "wrong-flash");
            en.classList.remove('active-sel');
            tr.classList.remove('active-sel');
        }
        GAME_STATE.selectedEN = null;
        GAME_STATE.selectedTR = null;
        updateWMUI();
    }

    function removeTilesWM(en, tr) {
        const enIdx = parseInt(en.dataset.index);
        const trIdx = parseInt(tr.dataset.index);

        en.classList.add('pop');
        tr.classList.add('pop');

        setTimeout(() => {
            GAME_STATE.enData[enIdx] = null;
            GAME_STATE.trData[trIdx] = null;
            applyGravity('en');
            applyGravity('tr');
            
            GAME_STATE.activeCount--;
            updateWMUI();
            if(GAME_STATE.activeCount <= 0) triggerFinal(false);
        }, 400);
    }

    function applyGravity(type) {
        let data = GAME_STATE[type + 'Data'];
        for (let col = 0; col < 3; col++) {
            let emptySpots = [];
            for (let row = 4; row >= 0; row--) {
                let i = row * 3 + col;
                if (data[i] === null) {
                    emptySpots.push(i);
                } else if (emptySpots.length > 0) {
                    let nextEmpty = emptySpots.shift();
                    data[nextEmpty] = data[i];
                    data[i] = null;
                    emptySpots.push(i);
                }
            }
        }
        renderGrid(type + '-grid', type);
        const container = document.getElementById(type + '-grid');
        Array.from(container.children).forEach(child => {
            child.classList.remove('gravity-fall');
            void child.offsetWidth;
            child.classList.add('gravity-fall');
        });
    }

    function updateWMUI() {
        document.getElementById('wm-unit').innerText = GAME_STATE.unit;
        document.getElementById('wm-score').innerText = GAME_STATE.score;
        document.getElementById('wm-tiles').innerText = GAME_STATE.activeCount;
    }

    function showFeedback(txt, cls) {
        let p = document.getElementById('msg-popup');
        if (!p) {
            p = document.createElement('div');
            p.id = 'msg-popup';
            p.style.cssText = "position:fixed; top:50%; left:50%; transform:translate(-50%, -50%); font-size:45px; font-weight:900; z-index:9000; text-shadow:0 5px 15px #000; background:rgba(0,0,0,0.8); padding:15px 40px; border-radius:50px;";
            document.body.appendChild(p);
        }
        p.innerText = txt; p.style.display = 'block'; p.style.color = (cls==="correct-flash") ? "#22c55e" : "#ef4444";
        setTimeout(() => p.style.display = 'none', 500);
    }

    function triggerFinal(isManualFinish) {
        playSound('win');
        const screen = document.getElementById('end-screen');
        document.getElementById('end-score').innerText = GAME_STATE.score;
        screen.style.display = 'flex';
    }
</script>
</body>
</html>
