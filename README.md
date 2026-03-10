<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WORD CRUSH PRO: MEB 6. SINIF ELITE PROJECT</title>
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
        }

        body {
            background: radial-gradient(circle at top right, var(--bg-light) 0%, var(--bg-dark) 100%);
            color: var(--text-main); font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex; flex-direction: column; align-items: center;
            margin: 0; height: 100vh; overflow: hidden; transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* --- HATA & DOĞRU EFEKTLERİ --- */
        .wrong-flash { background: var(--danger) !important; animation: shake 0.3s; }
        .correct-flash { background: var(--success) !important; }
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(10px); }
            75% { transform: translateX(-10px); }
        }

        /* --- SCRIPTED MENU SYSTEM --- */
        #menu-screen {
            position: fixed; inset: 0; background: rgba(15, 23, 42, 0.98);
            display: flex; flex-direction: column; align-items: center; padding-top: 20px;
            z-index: 1000; backdrop-filter: blur(25px); overflow-y: auto;
        }
        
        .menu-header { text-align: center; margin-bottom: 30px; }
        .menu-title { font-size: 42px; color: var(--accent); letter-spacing: 5px; text-shadow: 0 0 20px var(--accent); margin: 0; }
        .menu-sub { color: var(--text-muted); font-size: 14px; text-transform: uppercase; letter-spacing: 2px; }

        .card-container { width: 100%; max-width: 700px; padding: 0 20px; box-sizing: border-box; }
        
        .unit-card {
            background: var(--panel-bg); border: 2px solid var(--accent); border-radius: 15px;
            padding: 20px; margin-bottom: 15px; cursor: pointer; transition: 0.3s ease;
            position: relative; overflow: hidden;
        }
        .unit-card:hover { transform: scale(1.02) translateY(-5px); box-shadow: 0 10px 30px rgba(0,0,0,0.5), 0 0 15px var(--accent); }
        .unit-card h2 { margin: 0 0 10px 0; font-size: 26px; color: #fff; }
        .unit-card hr { border: 0; height: 1px; background: var(--accent); opacity: 0.4; margin-bottom: 10px; }
        .unit-card p { margin: 0; color: var(--text-muted); font-size: 15px; }

        /* MODS CONTROL CENTER with EMOJIS */
        .mods-panel {
            width: 100%; max-width: 700px; background: rgba(0,0,0,0.4); 
            border: 2px dashed var(--accent); border-radius: 20px; padding: 20px;
            margin-bottom: 60px; box-sizing: border-box;
        }
        .mods-grid { display: grid; grid-template-columns: repeat(5, 1fr); gap: 12px; }
        .mod-btn {
            background: #1e293b; border: 1.5px solid var(--accent); border-radius: 10px;
            color: #fff; padding: 12px 5px; cursor: pointer; font-weight: 900; font-size: 12px;
            transition: 0.3s; text-transform: uppercase; display: flex; align-items: center; justify-content: center; gap: 5px;
        }
        .mod-btn:hover { background: var(--accent); color: #000; box-shadow: 0 0 15px var(--accent); }

        /* --- IN-GAME INTERFACE --- */
        #game-screen { display: none; width: 100%; height: 100%; flex-direction: column; align-items: center; padding-top: 20px; position: relative; }
        
        .ui-top { position: absolute; top: 25px; left: 25px; display: flex; gap: 15px; }
        .nav-btn { padding: 10px 20px; border-radius: 10px; border: none; font-weight: 900; cursor: pointer; transition: 0.2s; }
        .btn-exit { background: #475569; color: white; }
        .btn-finish { background: var(--danger); color: white; box-shadow: 0 0 15px rgba(239, 68, 68, 0.4); }

        #cheat-console {
            position: absolute; top: 25px; right: 25px; display: none;
            background: var(--panel-bg); padding: 10px; border-radius: 12px;
            border: 2px solid var(--accent); gap: 8px; align-items: center;
        }
        #cheat-input {
            background: #000; border: 1px solid #334155; color: var(--accent);
            padding: 8px; border-radius: 6px; text-align: center; font-weight: bold; outline: none;
        }

        .scoreboard {
            display: flex; justify-content: space-around; width: 85%; background: var(--panel-bg);
            padding: 15px; border-radius: 20px; border: 2px solid rgba(255,255,255,0.1); margin-bottom: 25px;
        }
        .stat-box { text-align: center; }
        .stat-val { display: block; font-size: 32px; font-weight: 900; color: var(--accent); }
        .stat-lbl { font-size: 12px; color: var(--text-muted); text-transform: uppercase; }

        /* --- GAME ENGINE GRIDS --- */
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
            box-shadow: 0 6px 0 rgba(0,0,0,0.4); text-transform: uppercase; padding: 5px; box-sizing: border-box;
        }
        .tile:hover { filter: brightness(1.2); transform: translateY(-5px); }
        .active-sel { border: 4px solid #fff !important; transform: scale(1.1) !important; z-index: 100; box-shadow: 0 0 25px #fff; }

        /* TILE ASSETS */
        .c-0 { background: linear-gradient(135deg, #f87171, #991b1b); }
        .c-1 { background: linear-gradient(135deg, #60a5fa, #1e40af); }
        .c-2 { background: linear-gradient(135deg, #4ade80, #14532d); }
        .c-3 { background: linear-gradient(135deg, #fbbf24, #b45309); color: #000; }
        .tr-tile { background: #1e293b; color: #94a3b8; border: 1px solid #334155; }

        /* ANIMATIONS & FIRE EFFECTS */
        @keyframes popOut { 0% { scale: 1; opacity: 1; } 50% { scale: 1.5; filter: brightness(2); } 100% { scale: 0; opacity: 0; } }
        @keyframes fire-glow { 0% { box-shadow: 0 0 10px #ff4500, 0 0 20px #ff0000; } 100% { box-shadow: 0 0 20px #ffd700, 0 0 40px #ff4500; } }
        @keyframes fallIn { from { transform: translateY(-300px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        
        .pop { animation: popOut 0.4s forwards; pointer-events: none; }
        .falling { animation: fallIn 0.5s ease-out forwards; }
        .fire-pop { animation: fire-glow 0.4s alternate infinite, popOut 0.4s forwards; border: 4px solid red; }

        #toast { position: fixed; top: 30%; font-size: 60px; font-weight: 900; color: gold; display: none; z-index: 5000; text-shadow: 0 0 20px #000; }

        /* END GAME MODALS */
        .end-screen {
            display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.98);
            z-index: 9999; flex-direction: column; align-items: center; justify-content: center;
            text-align: center; padding: 40px;
        }
        .end-title { font-size: 60px; color: var(--accent); margin-bottom: 20px; }
        .end-quote { font-size: 24px; color: #fff; font-style: italic; max-width: 800px; margin-bottom: 40px; }
    </style>
</head>
<body>

<div id="menu-screen">
    <div class="menu-header">
        <h1 class="menu-title">WORD CRUSH PRO</h1>
        <span class="menu-sub">MEB 6. Sınıf Spring English Project</span>
    </div>

    <div class="card-container" id="unit-root"></div>

    <div class="mods-panel">
        <h3 style="text-align:center; margin-top:0; color:var(--accent);">EXTENSIONS & THEMES</h3>
        <div class="mods-grid">
            <button class="mod-btn" onclick="applyTheme('classic')">🌑 Classic</button>
            <button class="mod-btn" onclick="applyTheme('subnautica')">🌊 Subnautica</button>
            <button class="mod-btn" onclick="applyTheme('cs2')">🔫 CS2 Global</button>
            <button class="mod-btn" onclick="applyTheme('alastor')" style="border-color: #ef4444; color: #ef4444;">📻 Alastor</button>
            <button class="mod-btn" onclick="applyTheme('vox')" style="border-color: #06b6d4; color: #06b6d4;">📺 VoxTek</button>
        </div>
    </div>
</div>

<div id="game-screen">
    <div class="ui-top">
        <button class="nav-btn btn-exit" onclick="location.reload()">MENU</button>
        <button class="nav-btn btn-finish" onclick="triggerFinal(true)">FINISH GAME</button>
    </div>

    <div id="cheat-console">
        <input type="password" id="cheat-input" placeholder="ACCESS CODE">
        <button onclick="execCheat()" style="cursor:pointer; font-weight:bold;">EXEC</button>
    </div>

    <div class="scoreboard">
        <div class="stat-box"><span class="stat-lbl">Active Unit</span><span id="ui-unit" class="stat-val">1</span></div>
        <div class="stat-box"><span class="stat-lbl">Total Score</span><span id="ui-score" class="stat-val">0</span></div>
        <div class="stat-box"><span class="stat-lbl">Tiles Left</span><span id="ui-tiles" class="stat-val">15</span></div>
    </div>

    <div class="game-world">
        <div class="grid-wrap">
            <h3>ENGLISH</h3>
            <div id="en-grid" class="game-grid"></div>
        </div>
        <div class="grid-wrap">
            <h3>TURKISH</h3>
            <div id="tr-grid" class="game-grid"></div>
        </div>
    </div>
</div>

<div id="toast">MATCH-3 BONUS!</div>

<div id="end-screen" class="end-screen">
    <h1 id="end-header" class="end-title">CONGRATULATIONS!</h1>
    <p id="end-quote" class="end-quote">"The future belongs to those who learn."</p>
    <div style="font-size: 40px; color: var(--accent); font-weight: 900; margin-bottom: 30px;">
        FINAL SCORE: <span id="end-score">0</span>
    </div>
    <button class="nav-btn" style="background:var(--accent); color:#000; padding:20px 50px; font-size:20px;" onclick="location.reload()">PLAY AGAIN</button>
</div>

<script>
    /* ========================================
       GAME ENGINE DATA & LOGIC
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
        score: 0,
        unit: 1,
        theme: 'classic',
        cheatUsed: false,
        activeCount: 15,
        selectedEN: null,
        selectedTR: null,
        bonusActive: false
    };

    let activeGamePool = []; 

    // Render 10 Units dynamic Menu
    const unitRoot = document.getElementById('unit-root');
    for (let i = 1; i <= 10; i++) {
        const data = MASTER_DICT[i];
        if(!data) continue;
        const card = document.createElement('div');
        card.className = 'unit-card';
        card.innerHTML = `<h2>Unit ${i}</h2><hr><p>${data.desc}</p>`;
        card.onclick = () => launchGame(i);
        unitRoot.appendChild(card);
    }

    function applyTheme(t) {
        GAME_STATE.theme = t;
        const style = document.documentElement.style;
        document.getElementById('cheat-console').style.display = (t==='alastor' || t==='vox') ? 'flex' : 'none';
        
        if(t==='subnautica') { style.setProperty('--accent', '#00ffff'); style.setProperty('--bg-dark', '#001a33'); style.setProperty('--panel-bg', 'rgba(0, 26, 51, 0.9)'); }
        else if(t==='cs2') { style.setProperty('--accent', '#fbbf24'); style.setProperty('--bg-dark', '#111'); style.setProperty('--panel-bg', 'rgba(20, 20, 20, 0.95)'); }
        else if(t==='alastor') { style.setProperty('--accent', '#ef4444'); style.setProperty('--bg-dark', '#2a0000'); style.setProperty('--panel-bg', 'rgba(40, 0, 0, 0.9)'); }
        else if(t==='vox') { style.setProperty('--accent', '#06b6d4'); style.setProperty('--bg-dark', '#081c24'); style.setProperty('--panel-bg', 'rgba(0, 30, 45, 0.9)'); }
        else { style.setProperty('--accent', '#38bdf8'); style.setProperty('--bg-dark', '#0f172a'); style.setProperty('--panel-bg', 'rgba(30, 41, 59, 0.98)'); }
    }

    function launchGame(unitId) {
        GAME_STATE.unit = unitId;
        GAME_STATE.score = 0;
        GAME_STATE.activeCount = 15;
        GAME_STATE.cheatUsed = false;
        GAME_STATE.bonusActive = false;
        
        let unitWords = MASTER_DICT[unitId].words;
        let allWords = [];
        Object.values(MASTER_DICT).forEach(u => allWords.push(...u.words));
        
        activeGamePool = [...unitWords];
        let attempts = 0;
        while(activeGamePool.length < 15 && attempts < 100) {
            let rand = allWords[Math.floor(Math.random()*allWords.length)];
            if(!activeGamePool.find(x => x.en === rand.en)) activeGamePool.push(rand);
            attempts++;
        }
        
        document.getElementById('menu-screen').style.display = 'none';
        document.getElementById('game-screen').style.display = 'flex';
        updateUI();
        buildGrids();
    }

    function buildGrids() {
        const enG = document.getElementById('en-grid');
        const trG = document.getElementById('tr-grid');
        enG.innerHTML = ''; trG.innerHTML = '';

        // --- THE SHUFFLE UPDATE: İki tarafı da birbirinden bağımsız karıştırıyoruz ---
        let enPool = [...activeGamePool].sort(() => Math.random() - 0.5);
        let trPool = [...activeGamePool].sort(() => Math.random() - 0.5);

        for(let i=0; i<15; i++) {
            let enWord = enPool[i];
            let trWord = trPool[i];
            
            let color = Math.floor(Math.random()*4);
            enG.appendChild(createTile(enWord.en, 'en', i, enWord.en, color));
            trG.appendChild(createTile(trWord.tr, 'tr', i, trWord.en, 'tr')); // Eşleşme data-pair ile sağlanıyor
        }
        setTimeout(scanForMatch3, 800);
    }

    function createTile(val, type, idx, pair, col) {
        const div = document.createElement('div');
        div.innerText = val;
        div.dataset.index = idx;
        div.dataset.type = type;
        div.dataset.pair = pair;
        div.dataset.color = col;
        div.onclick = () => onTileClick(div);
        div.className = `tile falling ${col === 'tr' ? 'tr-tile' : 'c-'+col}`;
        return div;
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
        // İki eşin data-pair değerine bakarak doğruluğunu kontrol et
        if(en.dataset.pair === tr.dataset.pair && en.dataset.pair !== "") {
            GAME_STATE.score += 100;
            updateUI();
            showFeedback("CORRECT!", "correct-flash");
            // Sadece EN gönderiyoruz, TR eşini data-pair'den bulup silecek
            removeTiles([en], false);
        } else {
            showFeedback("WRONG MATCH!", "wrong-flash");
            en.classList.remove('active-sel');
            tr.classList.remove('active-sel');
        }
        GAME_STATE.selectedEN = null;
        GAME_STATE.selectedTR = null;
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
        document.body.classList.add(cls);
        setTimeout(() => { p.style.display = 'none'; document.body.classList.remove(cls); }, 500);
    }

    // BONUS LOGIC: Match-3 trigger
    function scanForMatch3() {
        if(GAME_STATE.bonusActive) return;

        const tiles = Array.from(document.querySelectorAll('#en-grid .tile'));
        let matchSet = new Set();

        for(let r=0; r<5; r++) {
            let i1=r*3, i2=r*3+1, i3=r*3+2;
            let c1=tiles[i1]?.dataset.color, c2=tiles[i2]?.dataset.color, c3=tiles[i3]?.dataset.color;
            if(c1 && c1!=='tr' && c1===c2 && c2===c3 && tiles[i1].style.visibility!=='hidden') {
                matchSet.add(tiles[i1]); matchSet.add(tiles[i2]); matchSet.add(tiles[i3]);
            }
        }
        for(let c=0; c<3; c++) {
            for(let r=0; r<=2; r++) {
                let t1=tiles[r*3+c], t2=tiles[(r+1)*3+c], t3=tiles[(r+2)*3+c];
                let c1=t1?.dataset.color, c2=t2?.dataset.color, c3=t3?.dataset.color;
                if(c1 && c1!=='tr' && c1===c2 && c2===c3 && t1.style.visibility!=='hidden') {
                    matchSet.add(t1); matchSet.add(t2); matchSet.add(t3);
                }
            }
        }

        if(matchSet.size > 0) {
            GAME_STATE.score += 500;
            flashBonus();
            updateUI();
            GAME_STATE.bonusActive = true;
            removeTiles(Array.from(matchSet), true);
        }
    }

    function removeTiles(list, shouldRegen) {
        list.forEach(t => {
            // EŞLEŞTİRME MANTIĞI: data-pair özelliğini kullanarak eşini bul
            const pairTR = document.querySelector(`#tr-grid .tile[data-pair="${t.dataset.pair}"]`);
            
            t.className += (shouldRegen) ? ' fire-pop' : ' pop'; 
            if(pairTR) pairTR.className += (shouldRegen) ? ' fire-pop' : ' pop';
            
            setTimeout(() => {
                if(!shouldRegen) {
                    t.style.visibility = 'hidden'; 
                    t.dataset.color = 'none'; t.dataset.pair = ""; 
                    if(pairTR) { pairTR.style.visibility = 'hidden'; pairTR.dataset.pair = ""; }
                    
                    GAME_STATE.activeCount = document.querySelectorAll('#en-grid .tile:not([style*="visibility: hidden"])').length;
                    if(GAME_STATE.activeCount === 0) triggerFinal(false);
                } else {
                    const nw = activeGamePool[Math.floor(Math.random()*activeGamePool.length)];
                    const nc = Math.floor(Math.random()*4);
                    
                    t.innerText = nw.en; t.dataset.pair = nw.en; t.dataset.color = nc;
                    t.className = `tile falling c-${nc}`;
                    if(pairTR) { pairTR.innerText = nw.tr; pairTR.dataset.pair = nw.en; pairTR.className = `tile falling tr-tile`; }
                    setTimeout(()=> { t.classList.remove('falling'); if(pairTR) pairTR.classList.remove('falling'); }, 500);
                }
            }, 400);
        });

        if(shouldRegen) {
            setTimeout(() => { GAME_STATE.bonusActive = false; scanForMatch3(); }, 1200);
        }
    }

    function execCheat() {
        if(GAME_STATE.cheatUsed) return;
        const input = document.getElementById('cheat-input').value;
        if(input === 'LETSBEGİN_' && GAME_STATE.theme === 'alastor') { GAME_STATE.score += 4000; GAME_STATE.cheatUsed = true; }
        if(input === 'VOXTEK_' && GAME_STATE.theme === 'vox') { GAME_STATE.score += 1000; GAME_STATE.cheatUsed = true; }
        updateUI(); document.getElementById('cheat-input').value = '';
    }

    function updateUI() {
        document.getElementById('ui-unit').innerText = GAME_STATE.unit;
        document.getElementById('ui-score').innerText = GAME_STATE.score;
        document.getElementById('ui-tiles').innerText = document.querySelectorAll('#en-grid .tile:not([style*="visibility: hidden"])').length;
    }

    function flashBonus() {
        const t = document.getElementById('toast');
        t.style.display = 'block';
        setTimeout(()=> t.style.display = 'none', 1000);
    }

    function triggerFinal(isManualFinish) {
        const screen = document.getElementById('end-screen');
        const h = document.getElementById('end-header');
        const q = document.getElementById('end-quote');
        document.getElementById('end-score').innerText = GAME_STATE.score;
        
        if(GAME_STATE.theme === 'alastor') {
            h.innerText = "THE SHOW IS OVER! 📻";
            q.innerText = '"Smile, my dear! You know you are never fully dressed without one!"';
        } else if(GAME_STATE.theme === 'vox') {
            h.innerText = "VOXTEK SECURE! 📺";
            q.innerText = '"Trust us with your future! The technology of tomorrow, today."';
        } else if(GAME_STATE.theme === 'cs2') {
            const ct = Math.random() > 0.5;
            h.innerText = ct ? "COUNTER-TERRORISTS WIN 💣" : "TERRORISTS WIN 💥";
            q.innerText = ct ? "Bomb defused. Good work team." : "Hedef yok edildi. Teröristler kazandı.";
        } else if(GAME_STATE.theme === 'subnautica') {
            h.innerText = "FAREWELL... 🌊";
            q.innerText = '"We are different. But we go... together. To the stars."';
        }

        screen.style.display = 'flex';
    }
</script>
</body>
</html>
