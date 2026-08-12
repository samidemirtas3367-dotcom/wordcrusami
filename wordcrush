<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ENG GAME (MEGA ULTIMATE EDITION - DOMAIN EXPANSION)</title>
    <style>
        /* ========================================
           CORE UI DESIGN & NEON THEME ENGINE
           ======================================== */
        :root {
            --bg-dark: #050b14; 
            --bg-light: #0f172a; 
            --accent: #00f3ff; 
            --panel-bg: rgba(15, 23, 42, 0.85); 
            --text-main: #f8fafc;
            --text-muted: #94a3b8; 
            --danger: #ff0055; 
            --success: #00ff66; 
            --gold: #ffea00; 
            --p1-color: #ff0055; 
            --p2-color: #00f3ff;
            --minigame-accent: #bc13fe; 
            --wheel-accent: #ff0055;
            --term-green: #00ff41; 
            --term-bg: rgba(0, 5, 10, 0.95);
        }

        body {
            background: radial-gradient(circle at 50% 50%, var(--bg-light) 0%, var(--bg-dark) 100%);
            background-size: 200% 200%;
            animation: bgShift 15s ease infinite;
            color: var(--text-main); 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex; 
            flex-direction: column; 
            align-items: center; 
            justify-content: flex-start;
            margin: 0; 
            height: 100vh; 
            overflow: hidden; 
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        @keyframes bgShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* --- MATRIX INTRO & HACKER CONSOLE --- */
        #intro-screen {
            position: fixed; 
            inset: 0; 
            background: #000; 
            z-index: 99999;
            display: flex; 
            flex-direction: column; 
            align-items: flex-start; 
            justify-content: flex-end;
            padding: 40px; 
            font-family: 'Courier New', Courier, monospace; 
            color: var(--term-green);
        }

        .intro-log { 
            font-size: 22px; 
            margin-bottom: 10px; 
            text-shadow: 0 0 10px var(--term-green), 0 0 20px var(--term-green); 
        }

        #dev-console {
            position: fixed; 
            top: -100%; 
            left: 0; 
            width: 100%; 
            height: 50vh;
            background: var(--term-bg); 
            border-bottom: 4px solid var(--term-green);
            z-index: 50000; 
            transition: top 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            display: flex; 
            flex-direction: column; 
            font-family: 'Courier New', Courier, monospace;
            box-shadow: 0 20px 50px rgba(0,255,65,0.2), 0 0 30px rgba(0,255,65,0.4);
        }

        #console-output {
            flex: 1; 
            padding: 20px; 
            overflow-y: auto; 
            color: var(--term-green);
            font-size: 18px; 
            text-shadow: 0 0 5px var(--term-green); 
            display: flex; 
            flex-direction: column; 
            gap: 5px;
        }

        .console-input-line { 
            display: flex; 
            padding: 10px 20px; 
            background: rgba(0,255,65,0.1); 
            border-top: 1px solid var(--term-green); 
        }

        .console-prefix { 
            color: #fff; 
            margin-right: 10px; 
            font-size: 20px; 
            font-weight: bold; 
        }

        #console-input { 
            background: transparent; 
            border: none; 
            color: #fff; 
            font-size: 20px; 
            width: 100%; 
            outline: none; 
            font-family: 'Courier New', Courier, monospace; 
        }

        .sys-msg { color: var(--accent); text-shadow: 0 0 8px var(--accent); } 
        .err-msg { color: var(--danger); text-shadow: 0 0 8px var(--danger); } 
        .success-msg { color: var(--gold); text-shadow: 0 0 8px var(--gold); }
        
        .dev-trigger { 
            position: fixed; 
            bottom: 10px; 
            right: 10px; 
            color: rgba(255,255,255,0.2); 
            font-size: 14px; 
            cursor: pointer; 
            z-index: 10000; 
            font-family: monospace; 
            font-weight: bold; 
        }
        .dev-trigger:hover { 
            color: var(--term-green); 
            text-shadow: 0 0 10px var(--term-green); 
        }

        /* --- RANK UI (3D & NEON) --- */
        .rank-container {
            background: linear-gradient(135deg, rgba(15, 23, 42, 0.9), rgba(2, 6, 23, 0.9));
            border: 2px solid var(--accent); 
            padding: 15px 40px; 
            border-radius: 20px; 
            text-align: center; 
            box-shadow: 0 0 20px rgba(0, 243, 255, 0.3), inset 0 0 15px rgba(0, 243, 255, 0.1); 
            width: 350px; 
            position: relative; 
            overflow: hidden;
        }

        .rank-container::before {
            content: ''; 
            position: absolute; 
            top: -50%; 
            left: -50%; 
            width: 200%; 
            height: 200%;
            background: conic-gradient(transparent, var(--accent), transparent 30%);
            animation: rotateBorder 4s linear infinite; 
            z-index: -1; 
            opacity: 0.2;
        }

        @keyframes rotateBorder { 
            100% { transform: rotate(360deg); } 
        }

        .rank-title { 
            color: var(--accent); 
            font-size: 14px; 
            font-weight: bold; 
            letter-spacing: 4px; 
            margin-bottom: 5px; 
            text-transform: uppercase; 
            text-shadow: 0 0 10px var(--accent); 
        }

        #rank-name-ui { 
            font-size: 32px; 
            font-weight: 900; 
            color: #fff; 
            text-shadow: 0 0 15px #fff, 0 0 30px var(--gold); 
            margin-bottom: 10px; 
            letter-spacing: 2px;
        }

        .xp-bar-bg { 
            width: 100%; 
            height: 16px; 
            background: #0f172a; 
            border-radius: 8px; 
            overflow: hidden; 
            border: 2px solid #334155; 
            box-shadow: inset 0 0 10px #000; 
        }

        #xp-bar-fill { 
            width: 0%; 
            height: 100%; 
            background: linear-gradient(90deg, #ca8a04, var(--gold), #fff); 
            transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1); 
            box-shadow: 0 0 20px var(--gold); 
        }

        #xp-text-ui { 
            font-size: 14px; 
            color: var(--accent); 
            margin-top: 8px; 
            font-weight: bold; 
            text-shadow: 0 0 5px var(--accent); 
        }

        /* --- MENÜ SİSTEMİ EKRANLARI --- */
        .screen { 
            display: none; 
            width: 100%; 
            height: 100%; 
            flex-direction: column; 
            align-items: center; 
            padding-top: 40px; 
            position: absolute; 
            inset: 0; 
            background: rgba(5, 11, 20, 0.85); 
            backdrop-filter: blur(20px); 
            overflow-y: auto; 
            z-index: 10; 
        }

        #main-menu { display: flex; z-index: 20; }
        #game-screen, #quiz-screen, #battle-screen, #bomb-screen, #memory-screen, #rain-screen, #wheel-screen, #voltage-screen, #crate-screen { 
            background: transparent; 
            backdrop-filter: none; 
            z-index: 5; 
        }

        .menu-header { 
            text-align: center; 
            margin-bottom: 30px; 
            animation: slideDown 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275); 
        }

        @keyframes slideDown { 
            from { transform: translateY(-50px) scale(0.9); opacity: 0; } 
            to { transform: translateY(0) scale(1); opacity: 1; } 
        }

        .menu-title { 
            font-size: 65px; 
            color: #fff; 
            letter-spacing: 6px; 
            text-shadow: 0 0 10px var(--accent), 0 0 20px var(--accent), 0 0 40px var(--accent), 0 0 80px var(--accent); 
            margin: 0; 
            font-weight: 900; 
        }

        .menu-sub { 
            color: var(--accent); 
            font-size: 20px; 
            text-transform: uppercase; 
            letter-spacing: 8px; 
            font-weight: bold; 
            text-shadow: 0 0 10px var(--accent); 
        }

        /* BUTONLAR (3D ARCADE STİLİ) */
        .big-btn { 
            background: linear-gradient(145deg, var(--panel-bg), #020617); 
            border: 2px solid var(--accent); 
            border-radius: 15px; 
            color: #fff; 
            padding: 20px 40px; 
            font-size: 24px; 
            font-weight: 900; 
            letter-spacing: 3px; 
            cursor: pointer; 
            width: 400px; 
            margin-bottom: 20px; 
            text-transform: uppercase; 
            box-shadow: 0 8px 0 rgba(0, 243, 255, 0.4), 0 15px 20px rgba(0,0,0,0.6), inset 0 0 15px rgba(0, 243, 255, 0.2); 
            transition: all 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            text-shadow: 0 0 8px rgba(255,255,255,0.5);
            position: relative; 
            overflow: hidden;
        }

        .big-btn::after {
            content: ''; 
            position: absolute; 
            top: -50%; 
            left: -50%; 
            width: 20px; 
            height: 200%;
            background: rgba(255,255,255,0.2); 
            transform: rotate(45deg); 
            filter: blur(5px);
            transition: all 0.5s ease; 
            opacity: 0;
        }

        .big-btn:hover { 
            background: var(--accent); 
            color: #000; 
            text-shadow: none;
            box-shadow: 0 8px 0 #008b91, 0 15px 30px rgba(0, 243, 255, 0.6), inset 0 0 20px rgba(255, 255, 255, 0.5); 
            transform: translateY(-4px); 
        }

        .big-btn:hover::after { 
            left: 120%; 
            opacity: 1; 
            transition: all 0.6s ease; 
        }

        .big-btn:active { 
            transform: translateY(6px); 
            box-shadow: 0 2px 0 #008b91, 0 5px 10px rgba(0, 243, 255, 0.4), inset 0 0 10px rgba(255, 255, 255, 0.5); 
        }
        
        .back-btn { 
            border-color: #64748b; 
            box-shadow: 0 8px 0 #334155, 0 15px 20px rgba(0,0,0,0.6); 
            color: #94a3b8; 
            margin-top: 20px; 
            width: 300px; 
        }

        .back-btn:hover { 
            background: #64748b; 
            color: #fff; 
            box-shadow: 0 8px 0 #334155, 0 15px 30px rgba(100, 116, 139, 0.6); 
            transform: translateY(-4px); 
        }

        .back-btn:active { 
            box-shadow: 0 2px 0 #334155; 
            transform: translateY(6px); 
        }

        .nav-btn { 
            padding: 12px 25px; 
            border-radius: 12px; 
            border: none; 
            font-weight: 900; 
            cursor: pointer; 
            transition: 0.2s; 
            z-index: 1000; 
            letter-spacing: 1px; 
            box-shadow: 0 5px 0 rgba(0,0,0,0.5);
        }

        .nav-btn:active { 
            transform: translateY(3px); 
            box-shadow: 0 2px 0 rgba(0,0,0,0.5); 
        }

        .btn-exit { 
            background: #475569; 
            color: white; 
            border: 2px solid #94a3b8; 
        } 

        .btn-exit:hover { 
            background: #94a3b8; 
            color: #000; 
            box-shadow: 0 5px 0 #475569, 0 0 20px #94a3b8;
        }

        .btn-finish { 
            background: var(--danger); 
            color: white; 
            border: 2px solid #ff4d88; 
        }

        .btn-finish:hover { 
            background: #ff4d88; 
            color: #000; 
            box-shadow: 0 5px 0 #990033, 0 0 20px var(--danger);
        }

        .minigame-grid { 
            display: grid; 
            grid-template-columns: 1fr 1fr; 
            gap: 20px; 
            max-width: 950px; 
        }

        /* ÜNİTE KARTLARI & MODLAR (NEON HOVER EFEKTLİ) */
        .card-container { 
            width: 100%; 
            max-width: 900px; 
            padding: 0 20px; 
            box-sizing: border-box; 
            display: grid; 
            grid-template-columns: 1fr 1fr; 
            gap: 20px; 
            perspective: 1000px; 
        }

        .unit-card { 
            background: linear-gradient(145deg, rgba(30,41,59,0.9), rgba(15,23,42,0.95)); 
            border: 2px solid var(--accent); 
            border-radius: 15px; 
            padding: 25px; 
            cursor: pointer; 
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); 
            position: relative; 
            overflow: hidden;
            box-shadow: 0 10px 15px rgba(0,0,0,0.5), inset 0 0 10px rgba(0,243,255,0.1);
            transform-style: preserve-3d;
        }

        .unit-card::before {
            content: ''; 
            position: absolute; 
            inset: 0;
            box-shadow: inset 0 0 20px var(--accent); 
            opacity: 0; 
            transition: 0.4s;
        }

        .unit-card:hover { 
            transform: translateY(-10px) rotateX(5deg) scale(1.05); 
            border-color: #fff;
            box-shadow: 0 20px 30px rgba(0,0,0,0.8), 0 0 30px var(--accent); 
        }

        .unit-card:hover::before { 
            opacity: 1; 
        }

        .unit-card h2 { 
            margin: 0 0 10px 0; 
            font-size: 28px; 
            color: #fff; 
            text-shadow: 0 0 10px var(--accent); 
            transition: 0.3s; 
        }

        .unit-card:hover h2 { 
            color: var(--accent); 
            text-shadow: 0 0 20px var(--accent), 0 0 40px #fff; 
        }

        .unit-card hr { 
            border: 0; 
            height: 2px; 
            background: linear-gradient(90deg, transparent, var(--accent), transparent); 
            margin-bottom: 15px; 
        }

        .unit-card p { 
            margin: 0; 
            color: var(--text-muted); 
            font-size: 16px; 
            font-weight: bold; 
        }

        .mods-grid, .settings-grid { 
            display: grid; 
            grid-template-columns: repeat(2, 1fr); 
            gap: 25px; 
            max-width: 650px; 
            width: 100%; 
        }

        .mod-btn { 
            background: #0f172a; 
            border: 2px solid var(--accent); 
            border-radius: 15px; 
            color: #fff; 
            padding: 20px; 
            cursor: pointer; 
            font-weight: 900; 
            font-size: 18px; 
            transition: 0.3s; 
            text-transform: uppercase; 
            box-shadow: 0 6px 0 rgba(0,243,255,0.3);
        }

        .mod-btn:hover, .mod-btn.active { 
            background: var(--accent); 
            color: #000; 
            box-shadow: 0 6px 0 #008b91, 0 0 30px var(--accent); 
            transform: translateY(-3px);
        }

        .mod-btn:active { 
            box-shadow: 0 0 0; 
            transform: translateY(3px); 
        }

        .info-box { 
            background: rgba(0,0,0,0.7); 
            border: 2px dashed var(--success); 
            border-radius: 15px; 
            padding: 20px; 
            margin-top: 30px; 
            max-width: 600px; 
            text-align: center; 
            color: var(--success); 
            font-size: 18px; 
            text-shadow: 0 0 10px var(--success);
            font-weight: bold;
        }

        /* --- SCOREBOARDS --- */
        .ui-top { 
            position: absolute; 
            top: 25px; 
            left: 25px; 
            display: flex; 
            gap: 15px; 
            z-index: 2000; 
        }

        .scoreboard { 
            display: flex; 
            justify-content: space-around; 
            width: 85%; 
            background: rgba(15, 23, 42, 0.85); 
            padding: 15px; 
            border-radius: 20px; 
            border: 2px solid var(--accent); 
            margin-bottom: 25px; 
            margin-top: 60px; 
            z-index: 100; 
            box-shadow: 0 10px 30px rgba(0,0,0,0.5), inset 0 0 20px rgba(0,243,255,0.2); 
            backdrop-filter: blur(10px);
        }

        .stat-box { 
            text-align: center; 
        } 
        
        .stat-val { 
            display: block; 
            font-size: 40px; 
            font-weight: 900; 
            color: #fff; 
            text-shadow: 0 0 15px var(--accent), 0 0 30px var(--accent); 
        } 
        
        .stat-lbl { 
            font-size: 15px; 
            color: var(--accent); 
            text-transform: uppercase; 
            font-weight: bold; 
            letter-spacing: 2px; 
        }

        /* --- QUIZ & BATTLE --- */
        .quiz-container { 
            width: 90%; 
            max-width: 900px; 
            margin-top: 20px; 
            perspective: 1000px;
        }

        .quiz-question { 
            background: linear-gradient(145deg, #0f172a, #020617); 
            border: 4px solid var(--accent); 
            border-radius: 20px; 
            padding: 50px; 
            font-size: 40px; 
            font-weight: 900; 
            text-align: center; 
            margin-bottom: 40px; 
            box-shadow: 0 20px 40px rgba(0,0,0,0.8), inset 0 0 30px rgba(0,243,255,0.2); 
            text-shadow: 0 0 10px #fff, 0 0 20px var(--accent);
        }

        .quiz-options { 
            display: grid; 
            grid-template-columns: 1fr 1fr; 
            gap: 25px; 
        }

        .quiz-opt-btn { 
            background: #1e293b; 
            border: 3px solid var(--accent); 
            border-radius: 15px; 
            padding: 30px; 
            font-size: 28px; 
            color: #fff; 
            cursor: pointer; 
            transition: 0.2s; 
            font-weight: bold; 
            box-shadow: 0 10px 0 rgba(0,243,255,0.4), 0 15px 20px rgba(0,0,0,0.5);
            text-shadow: 0 0 5px rgba(255,255,255,0.5);
        }

        .quiz-opt-btn:hover { 
            background: var(--accent); 
            color: #000; 
            border-color: #fff; 
            transform: translateY(-6px); 
            box-shadow: 0 10px 0 #008b91, 0 20px 30px rgba(0,243,255,0.5);
            text-shadow: none;
        }

        .quiz-opt-btn:active { 
            transform: translateY(4px); 
            box-shadow: 0 0 0 #008b91; 
        }

        #battle-screen { 
            flex-direction: row; 
            padding: 0; 
            background: #000; 
            overflow: hidden; 
        }

        .battle-side { 
            flex: 1; 
            display: flex; 
            flex-direction: column; 
            align-items: center; 
            justify-content: center; 
            position: relative; 
            transition: 0.3s; 
            height: 100%; 
        }

        .p1-side { 
            border-right: 5px solid #334155; 
            background: radial-gradient(circle at left, #3a0011, #000); 
            box-shadow: inset -20px 0 50px rgba(255,0,85,0.1); 
        } 
        
        .p2-side { 
            background: radial-gradient(circle at right, #001a33, #000); 
            box-shadow: inset 20px 0 50px rgba(0,243,255,0.1); 
        }

        .vs-divider { 
            position: absolute; 
            left: 50%; 
            top: 50%; 
            transform: translate(-50%, -50%); 
            font-size: 120px; 
            font-weight: 900; 
            color: #fff; 
            text-shadow: 0 0 20px var(--accent), 0 0 40px var(--danger); 
            z-index: 100; 
            font-style: italic; 
        }

        .battle-q-zone { 
            position: absolute; 
            top: 40px; 
            width: 70%; 
            background: rgba(15, 23, 42, 0.95); 
            padding: 30px; 
            border-radius: 20px; 
            border: 3px solid var(--accent); 
            text-align: center; 
            font-size: 40px; 
            font-weight: 900; 
            z-index: 50; 
            left: 15%; 
            box-shadow: 0 15px 40px #000, 0 0 30px var(--accent); 
            text-shadow: 0 0 10px #fff; 
        }

        .battle-options { 
            display: grid; 
            grid-template-columns: 1fr 1fr; 
            gap: 20px; 
            width: 85%; 
            max-width: 600px; 
        }

        .battle-btn { 
            padding: 40px 10px; 
            font-size: 28px; 
            font-weight: 900; 
            border-radius: 15px; 
            border: 4px solid rgba(255,255,255,0.2); 
            cursor: pointer; 
            color: white; 
            transition: 0.2s; 
            background: rgba(255,255,255,0.05); 
            box-shadow: 0 8px 0 rgba(0,0,0,0.5);
        }

        .p1-btn:hover { 
            background: var(--p1-color); 
            color: #000; 
            transform: translateY(-5px) scale(1.05); 
            box-shadow: 0 8px 0 #990033, 0 0 30px var(--p1-color); 
            border-color:#fff;
        } 
        
        .p2-btn:hover { 
            background: var(--p2-color); 
            color: #000; 
            transform: translateY(-5px) scale(1.05); 
            box-shadow: 0 8px 0 #008b91, 0 0 30px var(--p2-color); 
            border-color:#fff;
        }
        
        .p1-btn:active, .p2-btn:active { 
            transform: translateY(3px) scale(1); 
            box-shadow: 0 0 0;
        }

        .battle-score { 
            font-size: 120px; 
            font-weight: 900; 
            margin-bottom: 20px; 
            text-shadow: 0 0 30px; 
        } 

        .p1-text { color: var(--p1-color); text-shadow: 0 0 20px var(--p1-color); } 
        .p2-text { color: var(--p2-color); text-shadow: 0 0 20px var(--p2-color); }

        /* --- WORD MATCH (3D TILES) --- */
        .game-world { 
            display: flex; 
            gap: 60px; 
            margin-top: 10px; 
        }

        .grid-wrap h3 { 
            text-align: center; 
            color: #fff; 
            font-size: 24px; 
            letter-spacing: 6px; 
            margin-bottom: 15px; 
            text-shadow: 0 0 15px var(--accent), 0 0 30px var(--accent); 
        }

        .game-grid { 
            display: grid; 
            grid-template-columns: repeat(3, 120px); 
            grid-template-rows: repeat(5, 85px); 
            gap: 15px; 
            background: rgba(0,0,0,0.8); 
            padding: 25px; 
            border-radius: 30px; 
            border: 4px solid var(--accent); 
            position: relative; 
            box-shadow: inset 0 0 50px #000, 0 0 30px rgba(0,243,255,0.2); 
        }

        .tile { 
            width: 120px; 
            height: 85px; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            border-radius: 12px; 
            cursor: pointer; 
            font-size: 15px; 
            font-weight: 900; 
            transition: 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275); 
            text-align: center; 
            text-transform: uppercase; 
            padding: 5px; 
            box-sizing: border-box; 
            position: absolute; 
            z-index: 10;
            border: 2px solid rgba(255,255,255,0.3);
            box-shadow: 0 8px 0 rgba(0,0,0,0.6), 0 10px 15px rgba(0,0,0,0.4), inset 0 2px 5px rgba(255,255,255,0.5);
        }

        .tile:hover { 
            filter: brightness(1.3); 
            transform: translateY(-6px) scale(1.05); 
            box-shadow: 0 14px 0 rgba(0,0,0,0.6), 0 20px 20px rgba(0,0,0,0.5), inset 0 2px 5px rgba(255,255,255,0.8); 
        }

        .active-sel { 
            border: 4px solid #fff !important; 
            transform: scale(1.15) translateY(-5px) !important; 
            z-index: 100; 
            box-shadow: 0 15px 0 rgba(0,0,0,0.5), 0 0 40px #fff, inset 0 0 20px rgba(255,255,255,0.8) !important; 
            color: #fff !important;
        }

        .c-0 { background: linear-gradient(135deg, #ff4d4d, #990000); text-shadow: 0 1px 2px #000;} 
        .c-1 { background: linear-gradient(135deg, #33ccff, #003399); text-shadow: 0 1px 2px #000;} 
        .c-2 { background: linear-gradient(135deg, #33ff77, #006622); color:#000;} 
        .c-3 { background: linear-gradient(135deg, #ffcc00, #996600); color: #000; } 
        .tr-tile { background: linear-gradient(135deg, #334155, #0f172a); color: #e2e8f0; border-color: #64748b; }

        @keyframes popOut { 
            0% { transform: scale(1); opacity: 1; } 
            50% { transform: scale(1.5); filter: brightness(2); box-shadow: 0 0 50px #fff; } 
            100% { transform: scale(0); opacity: 0; } 
        }

        @keyframes fire-glow { 
            0% { box-shadow: 0 0 15px #ff0055, 0 0 30px #ff0055, inset 0 0 20px #ff0055; border-color:#ff0055;} 
            100% { box-shadow: 0 0 30px #ffea00, 0 0 60px #ff0055, inset 0 0 30px #ffea00; border-color:#ffea00;} 
        }

        @keyframes gravityDrop { 
            0% { transform: translateY(-100px); opacity: 0; } 
            100% { transform: translateY(0); opacity: 1; } 
        }

        .gravity-fall { animation: gravityDrop 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; }
        .pop { animation: popOut 0.4s forwards; pointer-events: none; }
        .fire-pop { animation: fire-glow 0.4s alternate infinite, popOut 0.4s forwards; border: 4px solid red; z-index: 200; color:#fff !important;}

        /* ========================================
           DOMAIN EXPANSION SİSTEMİ EFEKTLERİ
           ======================================== */
        @keyframes domainExpandFlash {
            0% { opacity: 0; transform: scale(1.2); }
            10% { opacity: 1; transform: scale(1); box-shadow: inset 0 0 200px var(--accent); background: rgba(0,0,0,0.95); }
            90% { opacity: 1; transform: scale(1); box-shadow: inset 0 0 50px var(--accent); background: rgba(0,0,0,0.85); }
            100% { opacity: 0; transform: scale(0.9); }
        }

        .domain-overlay { 
            display: none; 
            position: fixed; 
            inset: 0; 
            z-index: 999999; 
            flex-direction: column; 
            justify-content: center; 
            align-items: center; 
            pointer-events: none; 
        }

        .domain-active { 
            display: flex !important; 
            animation: domainExpandFlash 3s cubic-bezier(0.1, 0.8, 0.2, 1) forwards; 
        }

        .domain-text { 
            font-size: 110px; 
            color: #fff; 
            font-weight: 900; 
            letter-spacing: 15px; 
            text-shadow: 0 0 50px var(--accent), 0 0 100px var(--accent); 
            text-align: center; 
            margin: 0;
        }

        .domain-sub { 
            font-size: 40px; 
            color: var(--accent); 
            margin-top: 20px; 
            font-weight: bold; 
            letter-spacing: 5px; 
            text-shadow: 0 0 20px var(--accent); 
        }

        /* DOMAIN PARLAK KELİMELER (Renk Kombinasyonu) */
        @keyframes intense-glow-1 { 0% { box-shadow: 0 0 20px #00ff66, inset 0 0 10px #00ff66; } 100% { box-shadow: 0 0 60px #00ff66, inset 0 0 30px #00ff66; } }
        @keyframes intense-glow-2 { 0% { box-shadow: 0 0 20px #ffea00, inset 0 0 10px #ffea00; } 100% { box-shadow: 0 0 60px #ffea00, inset 0 0 30px #ffea00; } }
        @keyframes intense-glow-3 { 0% { box-shadow: 0 0 20px #ff0055, inset 0 0 10px #ff0055; } 100% { box-shadow: 0 0 60px #ff0055, inset 0 0 30px #ff0055; } }

        .glow-pair-1 { 
            border: 4px solid #00ff66 !important; 
            color: #fff !important; 
            text-shadow: 0 0 10px #000 !important; 
            animation: intense-glow-1 0.5s alternate infinite;
            z-index: 50;
        }
        
        .glow-pair-2 { 
            border: 4px solid #ffea00 !important; 
            color: #fff !important; 
            text-shadow: 0 0 10px #000 !important; 
            animation: intense-glow-2 0.5s alternate infinite;
            z-index: 50;
        }
        
        .glow-pair-3 { 
            border: 4px solid #ff0055 !important; 
            color: #fff !important; 
            text-shadow: 0 0 10px #000 !important; 
            animation: intense-glow-3 0.5s alternate infinite;
            z-index: 50;
        }

        /* --- MINIGAMES: WHEEL OF FORTUNE --- */
        .wheel-box { position: relative; width: 550px; height: 550px; margin-top: 20px; display: flex; align-items: center; justify-content: center; }
        #wheel-canvas { border-radius: 50%; border: 12px solid #0f172a; box-shadow: 0 0 60px rgba(0,0,0,0.8), 0 0 40px var(--wheel-accent), inset 0 0 30px #000; transition: transform 4s cubic-bezier(0.1, 0.8, 0.25, 1); }
        .wheel-pointer { position: absolute; top: -35px; left: 50%; transform: translateX(-50%); width: 0; height: 0; border-left: 40px solid transparent; border-right: 40px solid transparent; border-top: 70px solid #fff; z-index: 100; filter: drop-shadow(0 10px 15px rgba(0,0,0,0.9)); }
        #wheel-result-modal { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.95); z-index: 9000; flex-direction: column; align-items: center; justify-content: center; text-align: center; padding: 50px; animation: modalIn 0.5s ease; backdrop-filter: blur(10px);}
        @keyframes modalIn { from { transform: scale(0.5); opacity: 0; } to { transform: scale(1); opacity: 1; } }
        .wheel-task-number { font-size: 45px; color: var(--wheel-accent); letter-spacing: 5px; font-weight: bold; margin-bottom: 25px; text-shadow: 0 0 20px var(--wheel-accent); }
        .wheel-task-text { font-size: 65px; color: #fff; font-weight: 900; max-width: 1000px; line-height: 1.3; text-shadow: 0 5px 30px var(--accent); margin-bottom: 50px; }

        /* --- MINIGAMES: BOMB DEFUSE --- */
        #bomb-screen { background: radial-gradient(circle, #310a0a 0%, #000 100%); }
        .bomb-container { background: #111; border: 10px solid #333; border-radius: 30px; padding: 40px; display: flex; flex-direction: column; align-items: center; box-shadow: inset 0 0 60px #000, 0 20px 60px rgba(0,0,0,0.9), 0 0 40px rgba(255,0,0,0.3); width: 85%; max-width: 800px; margin-top: 50px; border-style: double; }
        .digital-timer { font-family: 'Courier New', Courier, monospace; font-size: 110px; color: #ef4444; background: #050000; padding: 15px 50px; border-radius: 20px; border: 5px solid #222; text-shadow: 0 0 30px #ef4444, 0 0 50px #ef4444; margin-bottom: 30px; letter-spacing: 8px; box-shadow: inset 0 0 20px #f00; }
        .bomb-question { font-size: 38px; color: #fff; margin-bottom: 25px; text-align: center; font-weight: bold; background: rgba(255,255,255,0.05); padding: 15px 40px; border-radius: 15px; border: 2px solid #333; text-shadow: 0 0 10px #fff; }
        .wires-container { display: flex; flex-direction: column; gap: 25px; width: 100%; }
        .wire { background: linear-gradient(90deg, #444 0%, #888 50%, #444 100%); height: 75px; border-radius: 35px; display: flex; align-items: center; justify-content: center; font-size: 26px; font-weight: 900; color: white; cursor: pointer; text-shadow: 1px 1px 3px #000; transition: 0.2s; position: relative; overflow: hidden; border: 3px solid #222; box-shadow: 0 10px 15px rgba(0,0,0,0.8), inset 0 5px 10px rgba(255,255,255,0.3); }
        .wire:hover { filter: brightness(1.3); transform: scale(1.03); box-shadow: 0 0 20px #fff; }
        .wire.cut::after { content: ''; position: absolute; left: 50%; top: -15px; bottom: -15px; width: 20px; background: #000; transform: skewX(-20deg); box-shadow: inset 0 0 20px #000, 0 0 10px rgba(255,255,255,0.5); }
        .wire.cut-wrong { background: #ef4444 !important; animation: shake 0.3s; box-shadow: 0 0 30px #ef4444 !important;}
        .w-red { background: linear-gradient(90deg, #990000, #ff3333, #990000); } .w-blue { background: linear-gradient(90deg, #003399, #3366ff, #003399); } .w-green { background: linear-gradient(90deg, #006622, #33cc33, #006622); } .w-yellow { background: linear-gradient(90deg, #996600, #ffcc00, #996600); }
        @keyframes massiveExplosion { 0% { background: #fff; transform: scale(1); } 50% { background: #ff0055; transform: scale(1.1); } 100% { background: #000; transform: scale(1); opacity: 0; } }
        .exploded-bg { animation: massiveExplosion 1s forwards; pointer-events: none; }

        /* --- MINIGAMES: MEMORY CARDS (3D) --- */
        .memory-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 25px; max-width: 950px; margin-top: 20px; perspective: 1200px; }
        .mem-card { width: 160px; height: 160px; background: transparent; cursor: pointer; perspective: 1200px; }
        .mem-inner { position: relative; width: 100%; height: 100%; text-align: center; transition: transform 0.6s cubic-bezier(0.4, 0.2, 0.2, 1); transform-style: preserve-3d; border-radius: 20px; box-shadow: 0 15px 25px rgba(0,0,0,0.6); }
        .mem-card.flipped .mem-inner, .mem-card.matched .mem-inner { transform: rotateY(180deg); box-shadow: 0 0 30px var(--accent); }
        .mem-front, .mem-back { position: absolute; width: 100%; height: 100%; backface-visibility: hidden; border-radius: 20px; display: flex; align-items: center; justify-content: center; font-size: 22px; font-weight: 900; padding: 15px; box-sizing: border-box; }
        .mem-front { background: linear-gradient(135deg, #020617, #0f172a); color: var(--accent); border: 4px solid var(--accent); font-size: 70px; box-shadow: inset 0 0 30px rgba(0,243,255,0.2); text-shadow: 0 0 20px var(--accent);}
        .mem-back { background: var(--panel-bg); color: #fff; transform: rotateY(180deg); border: 4px solid var(--gold); box-shadow: inset 0 0 30px rgba(255,234,0,0.3); text-shadow: 0 0 10px #fff;}
        .mem-card.matched .mem-inner { animation: popOut 0.5s 0.3s forwards; }

        /* --- MINIGAMES: WORD RAIN --- */
        #rain-screen { overflow: hidden; position: relative; }
        .rain-catcher { position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); background: var(--panel-bg); border: 4px solid var(--accent); padding: 25px 60px; border-radius: 30px; font-size: 36px; font-weight: 900; z-index: 100; text-align: center; box-shadow: 0 -15px 40px rgba(0,243,255,0.4), inset 0 0 20px rgba(0,243,255,0.2); width: 70%; backdrop-filter: blur(10px);}
        .rain-target-word { color: var(--gold); display: block; font-size: 60px; margin-top: 15px; text-shadow: 0 0 20px var(--gold), 0 0 40px var(--gold); }
        .raindrop { position: absolute; top: -120px; background: linear-gradient(135deg, #1e293b, #0f172a); border: 3px solid #fff; border-radius: 15px; padding: 25px 35px; font-size: 28px; font-weight: 900; cursor: pointer; transition: background 0.2s, transform 0.2s; box-shadow: 0 20px 40px rgba(0,0,0,0.8), inset 0 0 15px rgba(255,255,255,0.2); text-align: center; z-index: 50; text-shadow: 0 0 10px #fff;}
        .raindrop:hover { background: var(--accent); color: #000; transform: scale(1.2); box-shadow: 0 0 40px var(--accent); text-shadow: none; border-color: #000;}
        @keyframes rainFall { to { top: 110vh; } }
        .rain-explode { animation: fire-glow 0.3s alternate infinite, popOut 0.3s forwards; pointer-events: none; border-color: var(--success) !important; background: var(--success) !important; color: #000 !important; box-shadow: 0 0 50px var(--success) !important;}

        /* --- MINIGAMES: VOLTAGE CUT --- */
        #voltage-screen { background: radial-gradient(circle, #001a33 0%, #000 100%); }
        .voltage-area { width: 85%; height: 60vh; background: #020617; border: 6px solid #334155; border-radius: 30px; position: relative; margin-top: 30px; box-shadow: inset 0 0 80px #000, 0 0 40px rgba(0,243,255,0.2); overflow: hidden; touch-action: none; background-image: radial-gradient(rgba(0, 243, 255, 0.1) 2px, transparent 2px); background-size: 40px 40px;}
        .voltage-node { position: absolute; width: 110px; height: 110px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 900; font-size: 18px; text-align: center; padding: 10px; cursor: pointer; z-index: 10; border: 4px solid #fff; box-shadow: 0 0 30px rgba(255,255,255,0.5), inset 0 0 15px #000; text-shadow: 0 0 5px #000;}
        .v-start { background: var(--p2-color); color: #fff; left: 40px; top: 40%; box-shadow: 0 0 40px var(--p2-color); border-color: #fff;}
        .v-end { background: var(--success); color: #fff; right: 40px; top: 40%; transition: top 0.5s; box-shadow: 0 0 40px var(--success); border-color: #fff;}
        .v-wire { position: absolute; background: #334155; height: 24px; border-radius: 12px; transform-origin: left center; z-index: 5; pointer-events: none; box-shadow: 0 10px 20px #000, inset 0 0 10px #000; border: 2px solid #000;}
        .v-active-wire { background: #00ffff !important; box-shadow: 0 0 30px #00ffff, 0 0 60px #00ffff, inset 0 0 15px #fff !important; border-color: #fff !important;}
        .zap-effect { animation: zapFlash 0.3s; }
        @keyframes zapFlash { 0%, 100% { background: #020617; } 50% { background: #00ffff; } }

        /* --- MINIGAMES: CRATE BREAKER --- */
        #crate-screen { background: url('https://www.transparenttextures.com/patterns/dark-matter.png'), #111; }
        .crates-container { display: flex; gap: 60px; margin-top: 60px; perspective: 1000px;}
        .crate { width: 240px; height: 240px; background: url('https://www.transparenttextures.com/patterns/wood-pattern.png'), #8b4513; border: 12px solid #3e1f08; border-radius: 15px; cursor: pointer; position: relative; display: flex; align-items: center; justify-content: center; font-size: 36px; font-weight: 900; color: #fff; text-shadow: 2px 2px 10px #000; box-shadow: 0 30px 60px rgba(0,0,0,0.9), inset 0 0 80px rgba(0,0,0,0.7); transition: transform 0.1s, filter 0.2s; transform-style: preserve-3d;}
        .crate:hover { filter: brightness(1.2); box-shadow: 0 0 40px #d97706;}
        .crate:active { transform: scale(0.9) translateZ(-50px); box-shadow: 0 10px 20px rgba(0,0,0,0.9);}
        .crate-cracked-1 { background: url('https://www.transparenttextures.com/patterns/wood-pattern.png'), #70360e; border-color: #2e1605; }
        .crate-cracked-2 { background: url('https://www.transparenttextures.com/patterns/wood-pattern.png'), #542809; border-color: #1a0c03; }
        .crate-broken { background: transparent !important; border: none !important; box-shadow: none !important; pointer-events: none; animation: popOut 0.5s forwards; color: var(--gold); font-size: 60px; text-shadow: 0 0 40px var(--gold); }
        .crate-q { position: absolute; top: -110px; width: 100%; text-align: center; font-size: 50px; color: var(--gold); font-weight: 900; text-shadow: 0 0 30px #000, 0 0 20px var(--gold); background: rgba(0,0,0,0.7); padding: 10px; border-radius: 15px; border: 2px solid var(--gold);}

        /* --- EFFECTS & MODALS --- */
        .win-flash { animation: winGlow 0.5s infinite alternate; } 
        @keyframes winGlow { from { box-shadow: inset 0 0 50px rgba(0, 255, 102, 0.5); } to { box-shadow: inset 0 0 100px var(--success), 0 0 50px var(--success); } }
        .wrong-flash { background: var(--danger) !important; animation: shake 0.3s; border-color: #fff !important; box-shadow: 0 0 40px var(--danger) !important;}
        .correct-flash { background: var(--success) !important; border-color: #fff !important; color: #000 !important; box-shadow: 0 0 40px var(--success) !important; text-shadow: none !important;}
        @keyframes shake { 0%, 100% { transform: translateX(0); } 25% { transform: translateX(15px); } 75% { transform: translateX(-15px); } }

        #toast, #msg-popup { position: fixed; top: 30%; font-weight: 900; display: none; z-index: 9999; text-shadow: 0 0 30px #000, 0 0 50px #fff; text-align: center; }
        #toast { font-size: 80px; color: var(--gold); } 
        #msg-popup { font-size: 60px; top: 50%; left: 50%; transform: translate(-50%,-50%); background: rgba(0,0,0,0.9); padding: 30px 60px; border-radius: 50px; border: 4px solid #fff; box-shadow: 0 0 50px rgba(255,255,255,0.3); }

        .end-screen { display: none; position: fixed; inset: 0; background: rgba(5,11,20,0.98); z-index: 9999; flex-direction: column; align-items: center; justify-content: center; text-align: center; padding: 50px; backdrop-filter: blur(20px);}
        .end-title { font-size: 80px; color: #fff; margin-bottom: 25px; text-shadow: 0 0 20px var(--accent), 0 0 40px var(--accent), 0 0 80px var(--accent); }
        .end-quote { font-size: 32px; color: #fff; font-style: italic; max-width: 900px; margin-bottom: 50px; text-shadow: 0 0 15px rgba(255,255,255,0.5);}
    </style>
</head>
<body>

<div id="intro-screen">
    <div id="intro-container"></div>
</div>

<div id="dev-console">
    <div id="console-output"></div>
    <div class="console-input-line" id="console-line">
        <span class="console-prefix">root@smartboard:~#</span>
        <input type="password" id="console-input" autocomplete="off" spellcheck="false" autofocus>
    </div>
</div>

<div class="dev-trigger" onclick="toggleConsole()">v3.5.0_domain_destan_build(1400)</div>

<div id="main-menu" class="screen">
    <div class="menu-header">
        <h1 class="menu-title">ENG GAME</h1>
        <span class="menu-sub">DOMAIN EXPANSION EDITION</span>
    </div>
    
    <div class="rank-container" style="margin-bottom: 40px;">
        <div class="rank-title">CS2 RANK SYSTEM</div>
        <div id="rank-name-ui">🥈 SILVER I</div>
        <div class="xp-bar-bg">
            <div id="xp-bar-fill"></div>
        </div>
        <div id="xp-text-ui">0 / 400 XP</div>
    </div>

    <button class="big-btn" onclick="showScreen('mode-menu')">▶ KLASİK MODLAR</button>
    <button class="big-btn" onclick="showScreen('minigames-menu')" style="border-color: var(--minigame-accent); color: var(--minigame-accent); box-shadow: 0 8px 0 #5b0a8a, 0 15px 20px rgba(0,0,0,0.6), inset 0 0 15px rgba(188, 19, 254, 0.3);">🎮 MİNİGAMES (6)</button>
    <button class="big-btn" onclick="showScreen('mods-menu')">🎨 TEMALAR & DOMAIN</button>
    <button class="big-btn" onclick="showScreen('settings-menu')">⚙️ AYARLAR</button>
</div>

<div id="mode-menu" class="screen">
    <div class="menu-header"><h1 class="menu-title">MOD SEÇİMİ</h1></div>
    <button class="big-btn" onclick="selectMode('wordmatch')">🧩 WORD MATCH (Domainli)</button>
    <button class="big-btn" onclick="selectMode('quiz')" style="border-color: #fbbf24; color: #fbbf24; box-shadow: 0 8px 0 #b48600, 0 15px 20px rgba(0,0,0,0.6), inset 0 0 15px rgba(251, 191, 36, 0.3);">📝 QUICK QUIZ</button>
    <button class="big-btn" onclick="selectMode('battle')" style="border-color: #ff0055; color: #ff0055; box-shadow: 0 8px 0 #990033, 0 15px 20px rgba(0,0,0,0.6), inset 0 0 15px rgba(255, 0, 85, 0.3);">⚔️ BATTLE MODE (2P)</button>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<div id="minigames-menu" class="screen">
    <div class="menu-header" style="margin-bottom: 30px;"><h1 class="menu-title" style="color:var(--minigame-accent); text-shadow:0 0 30px var(--minigame-accent), 0 0 60px var(--minigame-accent);">MİNİGAMES</h1><span class="menu-sub" style="color:var(--minigame-accent);">Aksiyon ve Hız</span></div>
    <div class="minigame-grid">
        <button class="big-btn" style="width:100%; font-size: 20px; border-color: var(--wheel-accent); color: var(--wheel-accent); box-shadow: 0 6px 0 #990033, inset 0 0 10px rgba(255,0,85,0.2);" onclick="selectMinigame('wheel')">🎡 GÖREV ÇARKI (34)</button>
        <button class="big-btn" style="width:100%; font-size: 20px; border-color: #ef4444; color: #ef4444; box-shadow: 0 6px 0 #990000, inset 0 0 10px rgba(239,68,68,0.2);" onclick="selectMinigame('bomb')">💣 BOMB DEFUSE</button>
        <button class="big-btn" style="width:100%; font-size: 20px; border-color: #38bdf8; color: #38bdf8; box-shadow: 0 6px 0 #0284c7, inset 0 0 10px rgba(56,189,248,0.2);" onclick="selectMinigame('memory')">🎴 MEMORY CARDS</button>
        <button class="big-btn" style="width:100%; font-size: 20px; border-color: #22c55e; color: #22c55e; box-shadow: 0 6px 0 #009933, inset 0 0 10px rgba(34,197,94,0.2);" onclick="selectMinigame('rain')">🌧️ WORD RAIN</button>
        <button class="big-btn" style="width:100%; font-size: 20px; border-color: #00ffff; color: #00ffff; box-shadow: 0 6px 0 #008b91, inset 0 0 10px rgba(0,255,255,0.2);" onclick="selectMinigame('voltage')">⚡ VOLTAGE CUT</button>
        <button class="big-btn" style="width:100%; font-size: 20px; border-color: #d97706; color: #d97706; box-shadow: 0 6px 0 #994d00, inset 0 0 10px rgba(217,119,6,0.2);" onclick="selectMinigame('crate')">📦 CRATE BREAKER</button>
    </div>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')" style="grid-column: span 2; margin-top: 30px;">GERİ DÖN</button>
</div>

<div id="bomb-settings-menu" class="screen">
    <div class="menu-header"><h1 class="menu-title" style="color:#ef4444; text-shadow: 0 0 30px #ef4444;">BOMBA SÜRESİ</h1></div>
    <button class="big-btn" onclick="setBombSettings(10, 2)" style="font-size: 22px;">10 SANİYE (2 SORU)</button>
    <button class="big-btn" onclick="setBombSettings(20, 4)" style="font-size: 22px;">20 SANİYE (4 SORU)</button>
    <button class="big-btn" onclick="setBombSettings(40, 6)" style="font-size: 22px;">40 SANİYE (6 SORU)</button>
    <button class="big-btn" onclick="setBombSettings(50, 10)" style="border-color:#ef4444; color:#ef4444; font-size: 22px; box-shadow: 0 8px 0 #990000, 0 0 30px rgba(239,68,68,0.6);">50 SANİYE (10 SORU) 🔥</button>
    <button class="big-btn back-btn" onclick="showScreen('minigames-menu')">GERİ DÖN</button>
</div>

<div id="unit-menu" class="screen">
    <div class="menu-header"><h1 class="menu-title">ÜNİTE SEÇİMİ</h1></div>
    <div class="card-container" id="unit-root"></div>
    <button class="big-btn back-btn" style="grid-column: span 2; margin: 30px auto;" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<div id="mods-menu" class="screen">
    <div class="menu-header"><h1 class="menu-title">TEMALAR & DOMAIN</h1></div>
    <div class="mods-grid">
        <button class="mod-btn" id="btn-theme-classic" onclick="applyTheme('classic')">🌑 Classic (Domain Yok)</button>
        <button class="mod-btn" id="btn-theme-cs2" onclick="applyTheme('cs2')">🔫 CS2 Global</button>
        <button class="mod-btn" id="btn-theme-Vessel" onclick="applyTheme('Vessel')" style="border-color: #ef4444; color: #ef4444;">⛩️ Vessel (Sukuna)</button>
        <button class="mod-btn" id="btn-theme-Honored" onclick="applyTheme('Honored')" style="border-color: #a855f7; color: #a855f7;">🤞 Honored one (Gojo)</button>
        <button class="mod-btn" id="btn-theme-Gambler" onclick="applyTheme('Gambler')" style="border-color: #f59e0b; color: #f59e0b; grid-column: span 2;">🎰 Restless Gambler (Hakari)</button>
    </div>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<div id="settings-menu" class="screen">
    <div class="menu-header"><h1 class="menu-title">AYARLAR</h1></div>
    <div class="settings-grid">
        <button class="mod-btn" id="btn-dev-pc" onclick="setDevice('pc')">💻 PC</button>
        <button class="mod-btn" id="btn-dev-tahta" onclick="setDevice('tahta')">🏫 Akıllı Tahta</button>
    </div>
    <div id="device-info" class="info-box">MEGA UPDATE V3.5: KLASİK MODDAKİ EŞLEŞMEYEN KELİME BUG'I %100 FİXLENDİ! DOMAIN EXPANSION SİSTEMİ AKTİF! 5 COMBO YAP VE ŞOVU İZLE!</div>
    <button class="big-btn back-btn" onclick="showScreen('main-menu')">GERİ DÖN</button>
</div>

<!-- ================= OYUN EKRANLARI ================= -->

<div id="game-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button><button class="nav-btn btn-finish" onclick="triggerFinal(true)">BİTİR</button></div>
    <div class="scoreboard">
        <div class="stat-box"><span class="stat-lbl">Ünite</span><span id="wm-unit" class="stat-val">1</span></div>
        <div class="stat-box"><span class="stat-lbl">Skor</span><span id="wm-score" class="stat-val">0</span></div>
        <div class="stat-box"><span class="stat-lbl">Kalan Eş</span><span id="wm-tiles" class="stat-val">15</span></div>
    </div>
    <div class="game-world"><div class="grid-wrap"><h3>İNGİLİZCE</h3><div id="en-grid" class="game-grid"></div></div><div class="grid-wrap"><h3>TÜRKÇE</h3><div id="tr-grid" class="game-grid"></div></div></div>
</div>

<div id="quiz-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="scoreboard">
        <div class="stat-box"><span class="stat-lbl">Ünite</span><span id="qz-unit" class="stat-val">1</span></div>
        <div class="stat-box"><span class="stat-lbl">Soru</span><span id="qz-progress" class="stat-val">1/10</span></div>
        <div class="stat-box"><span class="stat-lbl">Skor</span><span id="qz-score" class="stat-val">0</span></div>
    </div>
    <div class="quiz-container">
        <div id="quiz-q-text" class="quiz-question">Yükleniyor...</div>
        <div id="quiz-options-container" class="quiz-options">
            <button class="quiz-opt-btn" onclick="checkQuizAnswer(0)" id="q-opt-0">A</button> <button class="quiz-opt-btn" onclick="checkQuizAnswer(1)" id="q-opt-1">B</button>
            <button class="quiz-opt-btn" onclick="checkQuizAnswer(2)" id="q-opt-2">C</button> <button class="quiz-opt-btn" onclick="checkQuizAnswer(3)" id="q-opt-3">D</button>
        </div>
    </div>
</div>

<div id="battle-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="vs-divider">VS</div>
    <div id="battle-q-box" class="battle-q-zone">SORU YÜKLENİYOR...</div>
    <div class="battle-side p1-side" id="p1-side">
        <div class="battle-score p1-text" id="p1-score-ui">0</div>
        <div class="battle-options"><button class="battle-btn p1-btn" onclick="handleBattlePress(1, 0)" id="p1-opt-0">A</button> <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 1)" id="p1-opt-1">B</button> <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 2)" id="p1-opt-2">C</button> <button class="battle-btn p1-btn" onclick="handleBattlePress(1, 3)" id="p1-opt-3">D</button></div>
        <h2 class="p1-text" style="margin-top:30px; font-size: 35px; font-weight: 900;">PLAYER 1</h2>
    </div>
    <div class="battle-side p2-side" id="p2-side">
        <div class="battle-score p2-text" id="p2-score-ui">0</div>
        <div class="battle-options"><button class="battle-btn p2-btn" onclick="handleBattlePress(2, 0)" id="p2-opt-0">A</button> <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 1)" id="p2-opt-1">B</button> <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 2)" id="p2-opt-2">C</button> <button class="battle-btn p2-btn" onclick="handleBattlePress(2, 3)" id="p2-opt-3">D</button></div>
        <h2 class="p2-text" style="margin-top:30px; font-size: 35px; font-weight: 900;">PLAYER 2</h2>
    </div>
</div>

<div id="wheel-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="menu-header" style="margin-bottom: 0;">
        <h1 class="menu-title" style="color:var(--wheel-accent); text-shadow:0 0 30px var(--wheel-accent), 0 0 60px var(--wheel-accent);">GÖREV ÇARKI</h1>
    </div>
    <div class="wheel-box">
        <div class="wheel-pointer"></div>
        <canvas id="wheel-canvas" width="550" height="550"></canvas>
    </div>
    <button class="big-btn" onclick="spinWheel()" id="spin-btn" style="border-color:var(--wheel-accent); color:var(--wheel-accent); margin-top: 50px; width: 450px; font-size: 36px; box-shadow: 0 8px 0 #990033, 0 15px 20px rgba(0,0,0,0.6);">ÇEVİR!</button>
</div>

<div id="wheel-result-modal">
    <div class="wheel-task-number" id="wheel-task-num">GÖREV #1</div>
    <div class="wheel-task-text" id="wheel-task-text">Bunu Yap!</div>
    <button class="big-btn" onclick="document.getElementById('wheel-result-modal').style.display='none'" style="border-color:var(--success); color:var(--success); box-shadow: 0 8px 0 #009933, 0 0 30px rgba(0,255,102,0.4);">GÖREVİ ALDIM</button>
</div>

<div id="bomb-screen" class="screen" style="z-index: 8;">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="bomb-container" id="bomb-box">
        <div style="color:white; font-size: 18px; letter-spacing: 4px; margin-bottom: 10px; font-weight: bold; text-shadow: 0 0 10px #fff;">TIME REMAINING</div>
        <div class="digital-timer" id="bomb-timer-ui">00.00</div>
        <div style="display:flex; justify-content: space-between; width: 100%; margin-bottom: 20px;">
            <span style="color:var(--accent); font-size: 22px; font-weight: 900; text-shadow: 0 0 10px var(--accent);">Soru: <span id="bomb-q-count">1/4</span></span>
        </div>
        <div class="bomb-question" id="bomb-q-text">Soru Yükleniyor...</div>
        <div class="wires-container" id="bomb-wires">
            <div class="wire w-red" onclick="cutWire(0)" id="w-opt-0">Kablo 1</div>
            <div class="wire w-blue" onclick="cutWire(1)" id="w-opt-1">Kablo 2</div>
            <div class="wire w-green" onclick="cutWire(2)" id="w-opt-2">Kablo 3</div>
            <div class="wire w-yellow" onclick="cutWire(3)" id="w-opt-3">Kablo 4</div>
        </div>
    </div>
</div>

<div id="memory-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="scoreboard">
        <div class="stat-box"><span class="stat-lbl">Eşleşme</span><span id="mem-score-ui" class="stat-val">0/8</span></div>
        <div class="stat-box"><span class="stat-lbl">Hamle</span><span id="mem-moves-ui" class="stat-val">0</span></div>
    </div>
    <div class="memory-grid" id="memory-grid"></div>
</div>

<div id="rain-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="scoreboard" style="margin-top: 10px; width: 60%;">
        <div class="stat-box"><span class="stat-lbl">Skor</span><span id="rain-score-ui" class="stat-val">0</span></div>
        <div class="stat-box"><span class="stat-lbl">Can</span><span id="rain-hp-ui" class="stat-val" style="color:var(--danger); text-shadow: 0 0 20px var(--danger);">❤️❤️❤️</span></div>
    </div>
    <div id="rain-area" style="position:absolute; top:150px; left:0; width:100%; height:calc(100vh - 300px);"></div>
    <div class="rain-catcher">YAKALA: <span class="rain-target-word" id="rain-target-ui">APPLE</span></div>
</div>

<div id="voltage-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="menu-header"><h1 class="menu-title" style="color:#00ffff; text-shadow:0 0 30px #00ffff, 0 0 60px #00ffff;">VOLTAGE CUT</h1><span class="menu-sub" style="color:#00ffff;">Kabloyu Koparmadan Bağla!</span></div>
    <div style="font-size: 40px; font-weight: 900; margin-top: 10px; text-shadow: 0 0 20px #fff;" id="voltage-target">Hedef: Yükleniyor...</div>
    <div class="voltage-area" id="voltage-area">
        <div class="v-wire" id="v-wire-main"></div>
        <div class="voltage-node v-start" id="v-start-node">BAŞLA</div>
        <div class="voltage-node v-end" id="v-end-node">HEDEF</div>
    </div>
</div>

<div id="crate-screen" class="screen">
    <div class="ui-top"><button class="nav-btn btn-exit" onclick="resetGame()">ÇIKIŞ</button></div>
    <div class="menu-header" style="margin-top: 50px;"><h1 class="menu-title" style="color:#d97706; text-shadow:0 0 30px #d97706, 0 0 60px #d97706;">CRATE BREAKER</h1><span class="menu-sub" style="color:#d97706;">Doğru Kasayı 3 Kere Vurarak Parçala!</span></div>
    <div style="font-size: 60px; font-weight: 900; margin-top: 50px; color: #fff; text-shadow: 0 0 30px #000, 0 0 15px #fff;" id="crate-q-text">Soru Yükleniyor...</div>
    <div class="crates-container" id="crates-container">
        <div class="crate" id="crate-0" onclick="hitCrate(0)"><div class="crate-q" id="cq-0">A</div></div>
        <div class="crate" id="crate-1" onclick="hitCrate(1)"><div class="crate-q" id="cq-1">B</div></div>
        <div class="crate" id="crate-2" onclick="hitCrate(2)"><div class="crate-q" id="cq-2">C</div></div>
    </div>
</div>

<!-- ================= OVERLAY'LER VE MODALLAR ================= -->

<div id="msg-popup"></div>
<div id="toast">BONUS COMBO!</div>

<!-- DOMAIN EXPANSION OVERLAY -->
<div id="domain-overlay" class="domain-overlay">
    <h1 id="domain-text" class="domain-text">領域展開</h1>
    <h2 id="domain-sub" class="domain-sub">DOMAIN EXPANSION</h2>
</div>

<div id="end-screen" class="end-screen">
    <h1 id="end-header" class="end-title">TEBRİKLER!</h1>
    <p id="end-quote" class="end-quote">"Öğrenenlerin geleceği parlaktır."</p>
    <div style="font-size: 60px; color: var(--accent); font-weight: 900; margin-bottom: 50px; text-shadow: 0 0 30px var(--accent), 0 0 60px var(--accent);">FİNAL SKOR: <span id="end-score">0</span></div>
    <button class="nav-btn" style="background:var(--accent); color:#000; padding:25px 60px; font-size:28px; box-shadow: 0 8px 0 #008b91, 0 15px 30px rgba(0,243,255,0.5);" onclick="resetGame()">ANA MENÜYE DÖN</button>
</div>

<div id="rank-up-modal" class="end-screen" style="z-index: 99999; background: rgba(5,11,20,0.98);">
    <h1 class="end-title" style="color: var(--gold); font-size: 110px; text-shadow: 0 0 50px var(--gold), 0 0 100px var(--gold); animation: popOut 0.5s reverse forwards;">RANK UP!</h1>
    <div id="new-rank-text" style="font-size: 70px; color: #fff; font-weight: 900; margin-bottom: 40px; text-transform: uppercase; text-shadow: 0 0 20px #fff;">🌟 GOLD NOVA I</div>
    <div id="unlock-msg" style="font-size: 32px; color: var(--success); margin-bottom: 60px; font-weight: 900; text-shadow: 0 0 25px var(--success); display: none;">🔓 TEBRİKLER! GİZLİ BAŞARIMLAR AÇILDI!</div>
    <button class="big-btn" onclick="document.getElementById('rank-up-modal').style.display='none'" style="border-color: var(--gold); color: var(--gold); box-shadow: 0 8px 0 #b48600, 0 0 40px rgba(251,191,36,0.6);">DEVAM ET</button>
</div>

<script>
    /* ========================================
       SİSTEM DEĞİŞKENLERİ VE VERİTABANI
       ======================================== */
    const MASTER_DICT = {
        1: { desc: "Daily routines and breakfast habits.", words: [{en:"Routine", tr:"Rutin"}, {en:"Nap", tr:"Kestirmek"}, {en:"Diary", tr:"Günlük"}, {en:"Visit", tr:"Ziyaret"}, {en:"Wake up", tr:"Uyanmak"}, {en:"Arrive", tr:"Varmak"}, {en:"Course", tr:"Kurs"}, {en:"Rest", tr:"Dinlenmek"}, {en:"Breakfast", tr:"Kahvaltı"}, {en:"Wash", tr:"Yıkamak"}, {en:"Brush", tr:"Fırçalamak"}, {en:"Comb", tr:"Taramak"}, {en:"Leave", tr:"Ayrılmak"}, {en:"Attend", tr:"Katılmak"}, {en:"Return", tr:"Dönmek"}, {en:"Sleep", tr:"Uyumak"}, {en:"Read", tr:"Okumak"}] },
        2: { desc: "Food, drinks and healthy life.", words: [{en:"Yummy", tr:"Lezzetli"}, {en:"Healthy", tr:"Sağlıklı"}, {en:"Cheese", tr:"Peynir"}, {en:"Butter", tr:"Tereyağı"}, {en:"Honey", tr:"Bal"}, {en:"Bagel", tr:"Simit"}, {en:"Beverage", tr:"İçecek"}, {en:"Jam", tr:"Reçel"}, {en:"Olive", tr:"Zeytin"}, {en:"Sausage", tr:"Sosis"}, {en:"Egg", tr:"Yumurta"}, {en:"Bread", tr:"Ekmek"}, {en:"Milk", tr:"Süt"}, {en:"Tea", tr:"Çay"}, {en:"Coffee", tr:"Kahve"}, {en:"Juice", tr:"Meyve Suyu"}] },
        3: { desc: "Downtown life, streets and busy cities.", words: [{en:"Downtown", tr:"Şehir Merkezi"}, {en:"Street", tr:"Sokak"}, {en:"Skyscraper", tr:"Gökdelen"}, {en:"Crowded", tr:"Kalabalık"}, {en:"Kiosk", tr:"Büfe"}, {en:"Neighborhood", tr:"Mahalle"}, {en:"Pavement", tr:"Kaldırım"}, {en:"Building", tr:"Bina"}, {en:"Traffic", tr:"Trafik"}, {en:"Pedestrian", tr:"Yaya"}] },
        4: { desc: "Weather conditions and moods.", words: [{en:"Weather", tr:"Hava Durumu"}, {en:"Stormy", tr:"Fırtınalı"}, {en:"Freezing", tr:"Dondurucu"}, {en:"Lightning", tr:"Şimşek"}, {en:"Mood", tr:"Ruh Hali"}, {en:"Anxious", tr:"Endişeli"}, {en:"Frightened", tr:"Korkmuş"}, {en:"Sunny", tr:"Güneşli"}, {en:"Cloudy", tr:"Bulutlu"}, {en:"Rainy", tr:"Yağmurlu"}] },
        5: { desc: "Funfairs, bumper cars and thrill.", words: [{en:"Funfair", tr:"Lunapark"}, {en:"Ferris Wheel", tr:"Dönme Dolap"}, {en:"Bumper cars", tr:"Çarpışan araba"}, {en:"Carousel", tr:"Atlı Karınca"}, {en:"Ticket", tr:"Bilet"}, {en:"Thrilling", tr:"Heyecan verici"}, {en:"Amazing", tr:"Şaşırtıcı"}, {en:"Rollercoaster", tr:"Hız Treni"}, {en:"Ghost Train", tr:"Korku Treni"}] },
        6: { desc: "Occupations and working places.", words: [{en:"Mechanic", tr:"Tamirci"}, {en:"Vet", tr:"Veteriner"}, {en:"Tailor", tr:"Terzi"}, {en:"Driver", tr:"Şoför"}, {en:"Architect", tr:"Mimar"}, {en:"Engineer", tr:"Mühendis"}, {en:"Dentist", tr:"Diş Hekimi"}, {en:"Teacher", tr:"Öğretmen"}, {en:"Nurse", tr:"Hemşire"}, {en:"Lawyer", tr:"Avukat"}] },
        7: { desc: "Vacation, seaside and sightseeing.", words: [{en:"Vacation", tr:"Tatil"}, {en:"Sightseeing", tr:"Şehir Gezisi"}, {en:"Seaside", tr:"Deniz Kenarı"}, {en:"Forest", tr:"Orman"}, {en:"Tent", tr:"Çadır"}, {en:"Skiing", tr:"Kayak yapmak"}, {en:"Hiking", tr:"Doğa yürüyüşü"}, {en:"Beach", tr:"Plaj"}, {en:"Sand", tr:"Kum"}, {en:"Sunbathe", tr:"Güneşlenmek"}] },
        8: { desc: "Bookworms and library rules.", words: [{en:"Bookworm", tr:"Kitap Kurdu"}, {en:"Novel", tr:"Roman"}, {en:"Poetry", tr:"Şiir"}, {en:"Library", tr:"Kütüphane"}, {en:"Shelf", tr:"Raf"}, {en:"Borrow", tr:"Ödünç almak"}, {en:"Dictionary", tr:"Sözlük"}, {en:"Magazine", tr:"Dergi"}, {en:"Author", tr:"Yazar"}, {en:"Page", tr:"Sayfa"}] },
        9: { desc: "Environment, saving the planet.", words: [{en:"Environment", tr:"Çevre"}, {en:"Recycle", tr:"Geri Dönüşüm"}, {en:"Pollution", tr:"Kirlilik"}, {en:"Save", tr:"Korumak"}, {en:"Litter", tr:"Çöp atmak"}, {en:"Waste", tr:"Atık"}, {en:"Planet", tr:"Gezegen"}, {en:"Energy", tr:"Enerji"}, {en:"Solar", tr:"Güneş Enerjisi"}] },
        10:{ desc: "Democracy, elections and voting process.", words: [{en:"Election", tr:"Seçim"}, {en:"Vote", tr:"Oy Vermek"}, {en:"Candidate", tr:"Aday"}, {en:"Ballot box", tr:"Sandık"}, {en:"Democracy", tr:"Demokrasi"}, {en:"Presidential", tr:"Başkanlık"}, {en:"Campaign", tr:"Kampanya"}, {en:"Public", tr:"Halk"}, {en:"Law", tr:"Yasa"}] }
    };

    let GAME_STATE = { 
        mode: '', unit: 1, theme: 'classic', device: 'pc', score: 0, scoreP1: 0, scoreP2: 0, 
        isBattleLocked: false, activeCount: 15, selectedEN: null, selectedTR: null, 
        combo: 0, enData: null, trData: null 
    };
    let MINIGAME = { id: '' };
    
    let QUIZ_STATE = { questions: [], currentIdx: 0 }; let BATTLE_Q = null;
    let BOMB_STATE = { timeLimit: 0, totalQs: 0, currentQ: 0, timeRemaining: 0, interval: null, questions: [], isExploded: false, timeMod: 0 };
    let MEMORY_STATE = { cards: [], firstCard: null, secondCard: null, lockBoard: false, matched: 0, moves: 0 };
    let RAIN_STATE = { targetWord: null, hp: 3, interval: null, spawnInterval: null, fallingDivs: [], speedMod: 1 };
    let VOLTAGE_STATE = { isDragging: false, targetWord: null, currentQ: 0, maxQ: 5 };
    let CRATE_STATE = { currentQ: 0, maxQ: 5, hits: [0,0,0], correctIdx: 0, questions: [] };

    const WHEEL_TASKS = [
        "Tahtada zıplayarak 3 İngilizce kelime söyle!", "Sınıfa dön ve İngilizce olarak kendini tanıt!", "Tahtada tek ayak üstünde 3 İngilizce renk say!", "İngilizce 5 tane hayvan ismi söyle!", "Bomb Defuse modunu 10 saniyede oyna!", "Memory Cards modunda 1 tur oyna!", "Yanındaki arkadaşına İngilizce iltifat et!", "En sevdiğin yemeği İngilizce tarif et!", "Sınıftaki 3 eşyanın İngilizcesini söyle!", "İngilizce 1'den 20'ye kadar geriye doğru say!", "Word Rain modunda 1 tur oyna!", "Bugün ne yaptığını İngilizce 3 cümleyle anlat.", "En sevdiğin rengi İngilizce söyle ve o renkte bir eşya göster.", "Tahtaya İngilizce bir kelime çiz, sınıf tahmin etsin!", "İngilizce 3 tane spor dalı say!", "Öğretmenine İngilizce bir soru sor!", "Hızlıca 5 tane İngilizce meyve say!", "15 saniye boyunca durmadan İngilizce konuş!", "İngilizce haftanın günlerini sırayla say!", "İngilizce ayları say!", "ŞANSLISIN! Görevi pas geçiyorsun! 🎉", "İngilizce 3 tane meslek söyle!", "İngilizce hava durumunu tarif et!", "Tahtaya bir çöp adam çiz ve İngilizce vücut bölümlerini yaz!", "İngilizce 3 tane ulaşım aracı söyle!", "Sınıftan birini seç, onunla İngilizce selamlaş!", "İngilizce 3 tane kıyafet ismi söyle!", "İngilizce bildiğin bir şarkının nakaratını söyle!", "Sınıf kurallarından birini İngilizce söyle!", "Şu an saat kaç? İngilizce olarak söyle!", "En sevdiğin filmi İngilizce 2 cümleyle anlat!", "Alfabeyi İngilizce olarak A'dan Z'ye oku!", "İngilizce 3 tane duygu durumu söyle!", "JOKER! İstediğin bir arkadaşına İngilizce bir görev ver!"
    ];
    let WHEEL_STATE = { isSpinning: false, currentRot: 0 };

    /* ========================================
       CS2 RANK SİSTEMİ
       ======================================== */
    const RANKS = [
        { name: "SILVER I", icon: "🥈", xp: 0 },
        { name: "SILVER II", icon: "🥈", xp: 400 },
        { name: "SILVER III", icon: "🥈", xp: 800 },
        { name: "SILVER IV", icon: "🥈", xp: 1200 },
        { name: "SILVER ELITE", icon: "🥈", xp: 1600 },
        { name: "GOLD NOVA I", icon: "🌟", xp: 2000 }
    ];
    let RANK_STATE = { xp: 0, level: 0 };

    function addXP(amount) {
        if(RANK_STATE.level >= RANKS.length - 1) return; // Zirvedesin kral
        RANK_STATE.xp += amount;
        
        let nextRank = RANKS[RANK_STATE.level + 1];
        if(RANK_STATE.xp >= nextRank.xp) {
            RANK_STATE.level++;
            showRankUpModal();
        }
        updateRankUI();
    }

    function updateRankUI() {
        let current = RANKS[RANK_STATE.level];
        let next = RANKS[RANK_STATE.level + 1];
        document.getElementById('rank-name-ui').innerText = current.icon + " " + current.name;
        
        if(!next) {
            document.getElementById('xp-bar-fill').style.width = "100%";
            document.getElementById('xp-text-ui').innerText = "MAX RANK!";
            document.getElementById('xp-text-ui').style.color = "var(--gold)";
        } else {
            let range = next.xp - current.xp;
            let progress = RANK_STATE.xp - current.xp;
            let pct = (progress / range) * 100;
            document.getElementById('xp-bar-fill').style.width = pct + "%";
            document.getElementById('xp-text-ui').innerText = `${progress} / ${range} XP`;
        }
    }

    function showRankUpModal() {
        playSound('bonus');
        setTimeout(() => playSound('win'), 500); 
        document.getElementById('rank-up-modal').style.display = 'flex';
        document.getElementById('new-rank-text').innerText = RANKS[RANK_STATE.level].icon + " " + RANKS[RANK_STATE.level].name;
        
        if(RANK_STATE.level === 5) {
            document.getElementById('unlock-msg').style.display = 'block';
        }
    }

    /* ========================================
       MATRIX INTRO & HACKER CONSOLE
       ======================================== */
    let SYS = { auth: false, open: false };

    function playIntro() {
        const c = document.getElementById('intro-container');
        const msgs = [
            "[SYSTEM]: Initializing Core Framework...", 
            "[SYSTEM]: Loading English Vocabulary Database...", 
            "[SYSTEM]: Word Match Bug Fully Patched.", 
            "[SYSTEM]: Integrating Domain Expansion Engine...", 
            "[WARN]: Security protocol bypassed by User.", 
            "[OK]: Environment ready. Let the games begin."
        ];
        let delay = 0;
        msgs.forEach(m => {
            setTimeout(() => { 
                let p = document.createElement('div'); 
                p.className='intro-log'; 
                p.innerText=m; 
                c.appendChild(p); 
                playSound('correct'); 
            }, delay);
            delay += 600;
        });
        setTimeout(() => {
            document.getElementById('intro-screen').style.display = 'none';
            document.getElementById('main-menu').style.display = 'flex';
            updateRankUI(); 
            playSound('win');
        }, delay + 800);
    }

    function toggleConsole() {
        SYS.open = !SYS.open;
        const con = document.getElementById('dev-console');
        const inp = document.getElementById('console-input');
        if(SYS.open) {
            con.style.top = '0'; inp.focus();
            if(!SYS.auth) { printConsole("Authentication required. Enter password:", "sys-msg"); inp.type = "password"; }
        } else { con.style.top = '-100%'; inp.blur(); }
    }

    document.getElementById('console-input').addEventListener('keydown', function(e) {
        if(e.key === 'Enter') {
            let val = this.value.trim(); this.value = ''; if(val === "") return;
            if(!SYS.auth) {
                if(val === "LETSBEGİN_") { 
                    SYS.auth = true; this.type = "text"; 
                    printConsole("ACCESS GRANTED. Welcome Admin.", "success-msg"); 
                    printConsole("Type /help for command list.", "sys-msg");
                } else { printConsole("ACCESS DENIED. Incorrect password.", "err-msg"); playSound('wrong'); }
            } else { processCommand(val); }
        }
    });

    function printConsole(txt, cls="") {
        const out = document.getElementById('console-output');
        const div = document.createElement('div'); div.className = cls; div.innerText = "> " + txt;
        out.appendChild(div); out.scrollTop = out.scrollHeight;
    }

    function processCommand(cmd) {
        printConsole(cmd, "");
        let args = cmd.split(' '); let c = args[0].toLowerCase();
        if(c === '/help') {
            printConsole("--- COMMAND LIST ---", "sys-msg");
            printConsole("set_gravity <val> : Word Rain hızını değiştirir", "sys-msg");
            printConsole("add_time <sec>    : Bomb Defuse moduna süre ekler", "sys-msg");
            printConsole("matrix_mode       : Temayı kod akışına çevirir", "sys-msg");
            printConsole("set_rank <level>  : Rütbeyi hileyle zorlar (0-5)", "sys-msg");
            printConsole("clear             : Konsolu temizler", "sys-msg");
            printConsole("exit              : Konsolu kapatır", "sys-msg");
        } else if(c === 'set_gravity') {
            RAIN_STATE.speedMod = parseFloat(args[1]) || 1; printConsole(`Gravity set to ${RAIN_STATE.speedMod}`, "success-msg");
        } else if(c === 'add_time') {
            let t = parseInt(args[1]) || 0; BOMB_STATE.timeMod += t; BOMB_STATE.timeRemaining += (t*1000); printConsole(`Added ${t} seconds.`, "success-msg");
        } else if(c === 'matrix_mode') {
            document.body.style.background = "#000"; document.documentElement.style.setProperty('--accent', '#00ff41'); document.documentElement.style.setProperty('--panel-bg', 'rgba(0,20,0,0.9)'); printConsole("Matrix loaded.", "success-msg");
        } else if(c === 'set_rank') {
            let level = parseInt(args[1]);
            if(level >= 0 && level <= 5) {
                RANK_STATE.level = level;
                RANK_STATE.xp = RANKS[level].xp;
                updateRankUI();
                printConsole(`Rank set to ${RANKS[level].name}`, "success-msg");
            }
        } else if(c === 'clear') { document.getElementById('console-output').innerHTML = '';
        } else if(c === 'exit') { toggleConsole();
        } else { printConsole(`Command not found: ${c}`, "err-msg"); }
    }

    /* ========================================
       SES VE BİLDİRİM MOTORU
       ======================================== */
    const AUDIO_FILES = {
        classic: { correct: 'https://actions.google.com/sounds/v1/water/splash.ogg', wrong: 'https://actions.google.com/sounds/v1/alarms/beep_short.ogg', win: 'https://actions.google.com/sounds/v1/human_voices/applause.ogg', bonus: 'https://actions.google.com/sounds/v1/cartoon/conga_drum_hit.ogg' },
        cs2: { correct: 'https://actions.google.com/sounds/v1/weapons/firework_rocket_launch.ogg', wrong: 'https://actions.google.com/sounds/v1/alarms/digital_alarm_clock.ogg', win: 'https://actions.google.com/sounds/v1/science_fiction/low_fuzz_explosion.ogg', bonus: 'https://actions.google.com/sounds/v1/weapons/automatic_gun_fire.ogg' }
    };

    function playSound(t) { 
        let src = (AUDIO_FILES[GAME_STATE.theme] && AUDIO_FILES[GAME_STATE.theme][t]) ? AUDIO_FILES[GAME_STATE.theme][t] : AUDIO_FILES['classic'][t]; 
        if(src){ 
            let a=new Audio(src); 
            a.volume=0.5; 
            let p=a.play(); 
            if(p!==undefined) p.catch(()=>{}); 
        } 
    }

    function showToast(msg) { 
        const t = document.getElementById('toast'); 
        t.innerText = msg; 
        t.style.display = 'block'; 
        t.style.animation = 'popOut 1.5s forwards'; 
        setTimeout(() => { t.style.display = 'none'; t.style.animation = ''; }, 1500); 
    }

    function showFeedback(txt, cls) { 
        let p = document.getElementById('msg-popup'); 
        p.innerText = txt; 
        p.style.display = 'block'; 
        p.style.color = (cls==="correct-flash") ? "var(--success)" : "var(--danger)"; 
        setTimeout(() => p.style.display = 'none', 600); 
    }

    /* ========================================
       NAVİGASYON VE AYARLAR
       ======================================== */
    function showScreen(id) { 
        document.querySelectorAll('.screen').forEach(el => el.style.display = 'none'); 
        document.getElementById(id).style.display = 'flex'; 
    }
    
    function selectMode(m) { 
        GAME_STATE.mode = m; 
        MINIGAME.id = ''; 
        showScreen('unit-menu'); 
    }
    
    function selectMinigame(id) { 
        MINIGAME.id = id; 
        GAME_STATE.mode = 'minigame'; 
        if(id==='bomb') showScreen('bomb-settings-menu'); 
        else if(id==='wheel') initWheel(); 
        else showScreen('unit-menu'); 
    }
    
    function setBombSettings(t, q) { 
        BOMB_STATE.timeLimit = t; 
        BOMB_STATE.totalQs = q; 
        showScreen('unit-menu'); 
    }
    
    function resetGame() {
        document.getElementById('end-screen').style.display = 'none'; 
        document.body.classList.remove('exploded-bg');
        
        clearInterval(BOMB_STATE.interval); 
        clearInterval(RAIN_STATE.interval); 
        clearInterval(RAIN_STATE.spawnInterval);
        
        RAIN_STATE.fallingDivs.forEach(d => { if(d && d.parentNode) d.parentNode.removeChild(d); }); 
        RAIN_STATE.fallingDivs = [];
        
        WHEEL_STATE.isSpinning = false; 
        VOLTAGE_STATE.isDragging = false;
        
        document.getElementById('domain-overlay').classList.remove('domain-active');
        
        showScreen('main-menu');
    }

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
        const s = document.documentElement.style;
        if(t==='cs2') { 
            s.setProperty('--accent', '#fbbf24'); 
            s.setProperty('--bg-dark', '#111'); 
            s.setProperty('--panel-bg', 'rgba(20, 20, 20, 0.95)'); 
        } else if(t==='Vessel') { 
            s.setProperty('--accent', '#ef4444'); 
            s.setProperty('--bg-dark', '#2a0000'); 
            s.setProperty('--panel-bg', 'rgba(40, 0, 0, 0.9)'); 
        } else if(t==='Honored') { 
            s.setProperty('--accent', '#a855f7'); 
            s.setProperty('--bg-dark', '#1e1b4b'); 
            s.setProperty('--panel-bg', 'rgba(20, 10, 40, 0.9)'); 
        } else if(t==='Gambler') { 
            s.setProperty('--accent', '#f59e0b'); 
            s.setProperty('--bg-dark', '#1a1000'); 
            s.setProperty('--panel-bg', 'rgba(40, 25, 0, 0.9)'); 
        } else { 
            s.setProperty('--accent', '#00f3ff'); 
            s.setProperty('--bg-dark', '#050b14'); 
            s.setProperty('--panel-bg', 'rgba(15, 23, 42, 0.85)'); 
        }
        document.querySelectorAll('#mods-menu .mod-btn').forEach(b => b.classList.remove('active')); 
        document.getElementById('btn-theme-' + t).classList.add('active');
    }

    function setDevice(type) { 
        GAME_STATE.device = type; 
        document.querySelectorAll('#settings-menu .mod-btn').forEach(b=>b.classList.remove('active')); 
        document.getElementById('btn-dev-'+type).classList.add('active'); 
    }
    
    applyTheme('classic'); 
    setDevice('pc');

    /* ========================================
       OYUN BAŞLATICI (ROUTER)
       ======================================== */
    function startGame(uId) {
        GAME_STATE.unit = uId; 
        GAME_STATE.score = 0;
        let uWords = MASTER_DICT[uId].words; 
        let aWords = []; 
        Object.values(MASTER_DICT).forEach(u => aWords.push(...u.words));
        
        if (GAME_STATE.mode === 'minigame') {
            if(MINIGAME.id === 'bomb') startBombDefuse(uWords, aWords);
            else if(MINIGAME.id === 'memory') startMemoryCards(uWords);
            else if(MINIGAME.id === 'rain') startWordRain(uWords);
            else if(MINIGAME.id === 'voltage') startVoltageCut(uWords, aWords);
            else if(MINIGAME.id === 'crate') startCrateBreaker(uWords, aWords);
            return;
        }

        if (GAME_STATE.mode === 'wordmatch') {
            GAME_STATE.activeCount = 15; 
            GAME_STATE.combo = 0; 
            GAME_STATE.selectedEN = null; 
            GAME_STATE.selectedTR = null;
            
            // ==========================================
            // BUG FİX: KELİMELERİ BİR KERE SEÇİP KOPYALIYORUZ
            // Böylece İngilizce tarafında hangi kelime varsa,
            // Türkçe tarafında da %100 o kelimenin eşi olacak.
            // ==========================================
            let safePool = [...uWords].sort(()=>Math.random()-0.5).slice(0, 15);
            
            // Eğer ünitede 15 kelime yoksa aWords'ten takviye yap
            while(safePool.length < 15) {
                let r = aWords[Math.floor(Math.random()*aWords.length)];
                if(!safePool.find(x => x.en === r.en)) safePool.push(r);
            }
            
            // İngilizce Verisi (Renkleri Rastgele Atanıyor)
            GAME_STATE.enData = safePool.map(w => ({ 
                en: w.en, tr: w.tr, pair: w.en, color: Math.floor(Math.random()*4), glow: null 
            }));
            
            // Türkçe Verisi (İngilizce verisinin aynısı, sadece karıştırılmış)
            GAME_STATE.trData = [...safePool].sort(()=>Math.random()-0.5).map(w => ({ 
                en: w.en, tr: w.tr, pair: w.en, color: 'tr', glow: null 
            }));
            
            showScreen('game-screen'); 
            updateWMUI(); 
            renderGrid('en-grid', 'en'); 
            renderGrid('tr-grid', 'tr');
            
        } else if (GAME_STATE.mode === 'quiz') {
            let sel = [...uWords].sort(()=>Math.random()-0.5).slice(0, 10);
            QUIZ_STATE.questions = sel.map(w => { 
                let o = [w.tr]; 
                while(o.length < 4) { 
                    let r = aWords[Math.floor(Math.random()*aWords.length)].tr; 
                    if(!o.includes(r)) o.push(r); 
                } 
                return { en: w.en, correct: w.tr, options: o.sort(()=>Math.random()-0.5) }; 
            });
            QUIZ_STATE.currentIdx = 0; 
            showScreen('quiz-screen'); 
            loadQuizQuestion(); 
            updateQuizUI();
            
        } else if (GAME_STATE.mode === 'battle') {
            GAME_STATE.scoreP1 = 0; 
            GAME_STATE.scoreP2 = 0; 
            document.getElementById('p1-score-ui').innerText = "0"; 
            document.getElementById('p2-score-ui').innerText = "0"; 
            showScreen('battle-screen'); 
            nextBattleQuestion();
        }
    }

    /* ========================================
       WORD MATCH MOTORU (DOMAIN EXPANSION DESTEKLİ)
       ======================================== */
    function renderGrid(id, type) { 
        const c = document.getElementById(id); 
        c.innerHTML = ''; 
        
        GAME_STATE[type+'Data'].forEach((w, i) => { 
            if(!w) return; 
            let row = Math.floor(i/3);
            let col = i%3; 
            
            let d = document.createElement('div'); 
            d.innerText = type === 'en' ? w.en : w.tr; 
            d.dataset.index = i; 
            d.dataset.type = type; 
            d.dataset.pair = w.pair; 
            
            d.className = `tile ${type === 'tr' ? 'tr-tile' : 'c-' + w.color}`; 
            
            // Eğer domain expansion efekti (glow) varsa ekle
            if(w.glow) d.classList.add(w.glow); 
            
            d.style.left = (col * 132 + 20) + "px"; 
            d.style.top = (row * 97 + 20) + "px"; 
            
            d.onclick = () => onTileClick(d); 
            c.appendChild(d); 
        }); 
    }

    function onTileClick(t) { 
        if(t.dataset.type === 'en') {
            if(GAME_STATE.selectedEN) GAME_STATE.selectedEN.classList.remove('active-sel');
            GAME_STATE.selectedEN = t;
        } else {
            if(GAME_STATE.selectedTR) GAME_STATE.selectedTR.classList.remove('active-sel');
            GAME_STATE.selectedTR = t;
        } 
        
        t.classList.add('active-sel'); 
        
        if(GAME_STATE.selectedEN && GAME_STATE.selectedTR) {
            checkPair(); 
        }
    }

    function checkPair() { 
        let e = GAME_STATE.selectedEN;
        let t = GAME_STATE.selectedTR; 
        
        if(e.dataset.pair === t.dataset.pair) {
            // DOĞRU EŞLEŞME
            GAME_STATE.score += 100; 
            addXP(100); 
            GAME_STATE.combo++; 
            
            playSound('correct'); 
            showFeedback(GAME_STATE.combo + " COMBO!", "correct-flash");

            // ==========================================
            // BONUS: YANYANA VEYA L ŞEKLİNDE EŞLEŞME (Takım oyunu için)
            // ==========================================
            let eIdx = parseInt(e.dataset.index);
            let tIdx = parseInt(t.dataset.index);
            let eRow = Math.floor(eIdx/3); let eCol = eIdx%3;
            let tRow = Math.floor(tIdx/3); let tCol = tIdx%3;

            // Eğer aynı satırdalarsa (yanyana) veya aynı sütundalarsa (alt alta)
            if (eRow === tRow || eCol === tCol) {
                GAME_STATE.score += 50;
                addXP(50);
                playSound('bonus');
                showToast("LINE BONUS!");
            }
            // L şeklinde (1 satır 2 sütun veya 2 satır 1 sütun fark varsa)
            else if ( (Math.abs(eRow-tRow)===1 && Math.abs(eCol-tCol)===2) || (Math.abs(eRow-tRow)===2 && Math.abs(eCol-tCol)===1) ) {
                GAME_STATE.score += 50;
                addXP(50);
                playSound('bonus');
                showToast("L-SHAPE BONUS!");
            }
            
            // ==========================================
            // DOMAIN EXPANSION TETİKLEYİCİ (5 COMBO)
            // ==========================================
            if(GAME_STATE.combo === 5) {
                triggerDomainExpansion();
                GAME_STATE.combo = 0; // Trigger olduktan sonra sıfırla
            }
            
            removeTilesWM(e, t);
        } else {
            // YANLIŞ EŞLEŞME
            GAME_STATE.combo = 0; // Hata yaparsa combo sıfırlanır
            playSound('wrong'); 
            showFeedback("YANLIŞ!", "wrong-flash");
            
            e.classList.remove('active-sel'); 
            t.classList.remove('active-sel');
        } 
        
        GAME_STATE.selectedEN = null; 
        GAME_STATE.selectedTR = null; 
        updateWMUI(); 
    }

    function removeTilesWM(e, t) { 
        let eI = parseInt(e.dataset.index);
        let tI = parseInt(t.dataset.index); 
        
        e.classList.add('pop'); 
        t.classList.add('pop'); 
        
        setTimeout(() => {
            GAME_STATE.enData[eI] = null; 
            GAME_STATE.trData[tI] = null;
            
            applyGravity('en'); 
            applyGravity('tr');
            
            GAME_STATE.activeCount--; 
            updateWMUI();
            
            if(GAME_STATE.activeCount <= 0) {
                triggerFinal(false);
            }
        }, 400); 
    }

    function applyGravity(type) { 
        let d = GAME_STATE[type+'Data']; 
        for(let c = 0; c < 3; c++) {
            let emp = []; 
            for(let r = 4; r >= 0; r--) {
                let i = r * 3 + c; 
                if(d[i] === null) {
                    emp.push(i); 
                } else if(emp.length > 0) { 
                    let n = emp.shift(); 
                    d[n] = d[i]; 
                    d[i] = null; 
                    emp.push(i); 
                }
            }
        } 
        renderGrid(type+'-grid', type); 
    }

    function updateWMUI() { 
        document.getElementById('wm-unit').innerText = GAME_STATE.unit; 
        document.getElementById('wm-score').innerText = GAME_STATE.score; 
        document.getElementById('wm-tiles').innerText = GAME_STATE.activeCount; 
    }

    /* ========================================
       DOMAIN EXPANSION MANTIĞI VE EFEKTLERİ
       ======================================== */
    function triggerDomainExpansion() {
        let dText = "";
        let dSub = "";
        let dColor = "";
        
        if(GAME_STATE.theme === 'Honored') {
            dText = "領域展開「無量空処」"; 
            dSub = "UNLIMITED VOID"; 
            dColor = "#a855f7";
        } else if(GAME_STATE.theme === 'Vessel') {
            dText = "領域展開「伏魔御厨子」"; 
            dSub = "MALEVOLENT SHRINE"; 
            dColor = "#ef4444";
        } else if(GAME_STATE.theme === 'Gambler') {
            dText = "領域展開「坐殺博徒」"; 
            dSub = "IDLE DEATH GAMBLE"; 
            dColor = "#f59e0b";
        } else {
            // Normal temalarda (Classic, CS2) Domain açılmaz. Sadece 5 combo XP'si verilir.
            addXP(200);
            showToast("MEGA COMBO!");
            return;
        }
        
        playSound('win');
        
        const overlay = document.getElementById('domain-overlay');
        document.getElementById('domain-text').innerText = dText;
        document.getElementById('domain-sub').innerText = dSub;
        
        // CSS Variable'ı anime rengine göre güncelle
        overlay.style.setProperty('--accent', dColor);
        
        // Animasyonu resetle ve başlat
        overlay.classList.remove('domain-active');
        void overlay.offsetWidth; 
        overlay.classList.add('domain-active');
        
        // Tahtadaki 3 rastgele çifti parlatma fonksiyonunu çağır
        highlightDomainPairs();
    }

    function highlightDomainPairs() {
        let remainingPairs = [];
        GAME_STATE.enData.forEach(w => { 
            if(w) remainingPairs.push(w.pair); 
        });
        
        // Geriye kalanları karıştır
        remainingPairs.sort(() => Math.random() - 0.5);
        
        // Max 3 tane al (Eğer tahtada 3'ten az kelime kaldıysa olanı alır)
        let selectedPairs = remainingPairs.slice(0, 3);
        
        // Önceden belirlediğimiz Neon Renk Sınıfları
        let glowClasses = ['glow-pair-1', 'glow-pair-2', 'glow-pair-3']; // Yeşil, Sarı, Pembe
        
        selectedPairs.forEach((pair, index) => {
            // İlgili kelime objelerini bul
            let enItem = GAME_STATE.enData.find(w => w && w.pair === pair);
            let trItem = GAME_STATE.trData.find(w => w && w.pair === pair);
            
            // Objelere glow class'ı ekle
            if(enItem) enItem.glow = glowClasses[index];
            if(trItem) trItem.glow = glowClasses[index];
        });
        
        // Tahtayı yeni neon efektleriyle tekrar renderla
        renderGrid('en-grid', 'en');
        renderGrid('tr-grid', 'tr');
    }

    /* ========================================
       KLASİK MİNİGAMELERİN TAM MANTIĞI (6 ADET KALDI)
       ======================================== */

    function loadQuizQuestion() { 
        if(QUIZ_STATE.currentIdx >= QUIZ_STATE.questions.length) { triggerFinal(true); return; } 
        let q = QUIZ_STATE.questions[QUIZ_STATE.currentIdx]; 
        document.getElementById('quiz-q-text').innerText = `"${q.en}" = ?`; 
        for(let i=0; i<4; i++) {
            let b = document.getElementById('q-opt-'+i);
            b.innerText = q.options[i];
            b.className = 'quiz-opt-btn';
            b.disabled = false;
        } 
    }
    
    function checkQuizAnswer(i) { 
        let q = QUIZ_STATE.questions[QUIZ_STATE.currentIdx];
        let b = document.getElementById('q-opt-'+i); 
        for(let j=0; j<4; j++) document.getElementById('q-opt-'+j).disabled = true; 
        
        if(b.innerText === q.correct){
            b.classList.add('correct-flash');
            GAME_STATE.score += 100; 
            addXP(150); 
            playSound('correct');
        } else {
            b.classList.add('wrong-flash');
            playSound('wrong');
            for(let j=0; j<4; j++) {
                if(document.getElementById('q-opt-'+j).innerText === q.correct) {
                    document.getElementById('q-opt-'+j).classList.add('correct-flash');
                }
            }
        } 
        updateQuizUI(); 
        setTimeout(()=>{
            QUIZ_STATE.currentIdx++; 
            loadQuizQuestion();
            updateQuizUI();
        }, 1500); 
    }
    
    function updateQuizUI() { 
        document.getElementById('qz-unit').innerText = GAME_STATE.unit; 
        document.getElementById('qz-score').innerText = GAME_STATE.score; 
        document.getElementById('qz-progress').innerText = (QUIZ_STATE.currentIdx>=10 ? 10 : QUIZ_STATE.currentIdx+1)+"/10"; 
    }

    function nextBattleQuestion() { 
        GAME_STATE.isBattleLocked = false; 
        document.getElementById('p1-side').classList.remove('win-flash'); 
        document.getElementById('p2-side').classList.remove('win-flash'); 
        
        let a = []; 
        Object.values(MASTER_DICT).forEach(u => a.push(...u.words)); 
        let c = MASTER_DICT[GAME_STATE.unit].words[Math.floor(Math.random()*MASTER_DICT[GAME_STATE.unit].words.length)]; 
        
        let o = [c.tr]; 
        while(o.length < 4) {
            let r = a[Math.floor(Math.random()*a.length)].tr;
            if(!o.includes(r)) o.push(r);
        } 
        o.sort(()=>Math.random()-0.5); 
        BATTLE_Q = {en:c.en, tr:c.tr, options:o}; 
        
        document.getElementById('battle-q-box').innerText = `"${c.en}"`; 
        for(let i=0; i<4; i++) {
            document.getElementById(`p1-opt-${i}`).innerText = o[i];
            document.getElementById(`p2-opt-${i}`).innerText = o[i];
            document.getElementById(`p1-opt-${i}`).style.background = "";
            document.getElementById(`p2-opt-${i}`).style.background = "";
        } 
    }
    
    function handleBattlePress(p, i) { 
        if(GAME_STATE.isBattleLocked) return; 
        if(BATTLE_Q.options[i] === BATTLE_Q.tr) { 
            GAME_STATE.isBattleLocked = true; 
            playSound('correct'); 
            if(p === 1) {
                GAME_STATE.scoreP1 += 10; 
                addXP(20); 
                document.getElementById('p1-score-ui').innerText = GAME_STATE.scoreP1;
                document.getElementById('p1-side').classList.add('win-flash');
            } else {
                GAME_STATE.scoreP2 += 10; 
                addXP(20); 
                document.getElementById('p2-score-ui').innerText = GAME_STATE.scoreP2;
                document.getElementById('p2-side').classList.add('win-flash');
            } 
            setTimeout(nextBattleQuestion, 1500); 
        } else { 
            playSound('wrong'); 
            document.getElementById(`p${p}-opt-${i}`).style.background = "var(--danger)"; 
        } 
    }

    function startBombDefuse(uWords, aWords) {
        showScreen('bomb-screen'); 
        document.body.classList.remove('exploded-bg'); 
        BOMB_STATE.isExploded = false; 
        BOMB_STATE.currentQ = 0; 
        BOMB_STATE.timeRemaining = (BOMB_STATE.timeLimit + BOMB_STATE.timeMod) * 1000;
        BOMB_STATE.questions = []; 
        
        let pool = [...uWords].sort(()=>Math.random()-0.5);
        for(let i=0; i<BOMB_STATE.totalQs; i++) { 
            let q = pool[i%pool.length]; 
            let opts = [q.tr]; 
            while(opts.length<4) { 
                let r = aWords[Math.floor(Math.random()*aWords.length)].tr; 
                if(!opts.includes(r)) opts.push(r); 
            } 
            BOMB_STATE.questions.push({ en: q.en, correct: q.tr, options: opts.sort(()=>Math.random()-0.5) }); 
        }
        
        loadBombQuestion(); 
        clearInterval(BOMB_STATE.interval); 
        let lastUpdate = Date.now();
        
        BOMB_STATE.interval = setInterval(() => { 
            if(BOMB_STATE.isExploded) return; 
            let dt = Date.now() - lastUpdate; 
            lastUpdate = Date.now(); 
            BOMB_STATE.timeRemaining -= dt; 
            
            if(BOMB_STATE.timeRemaining <= 0) { 
                BOMB_STATE.timeRemaining = 0; 
                updateBombTimerUI(); 
                explodeBomb(); 
            } else {
                updateBombTimerUI(); 
            }
        }, 50);
    }
    
    function updateBombTimerUI() { 
        let secs = Math.floor(BOMB_STATE.timeRemaining/1000);
        let ms = Math.floor((BOMB_STATE.timeRemaining%1000)/10); 
        document.getElementById('bomb-timer-ui').innerText = `${secs.toString().padStart(2,'0')}.${ms.toString().padStart(2,'0')}`; 
    }
    
    function loadBombQuestion() {
        if(BOMB_STATE.currentQ >= BOMB_STATE.totalQs) { defuseBombWin(); return; }
        let q = BOMB_STATE.questions[BOMB_STATE.currentQ]; 
        document.getElementById('bomb-q-text').innerText = `"${q.en}"`; 
        document.getElementById('bomb-q-count').innerText = `${BOMB_STATE.currentQ + 1}/${BOMB_STATE.totalQs}`;
        for(let i=0; i<4; i++) { 
            let w = document.getElementById('w-opt-'+i); 
            w.innerText = q.options[i]; 
            w.className = 'wire w-' + ['red','blue','green','yellow'][i]; 
        }
    }
    
    function cutWire(idx) {
        if(BOMB_STATE.isExploded) return; 
        let w = document.getElementById('w-opt-'+idx); 
        if(w.classList.contains('cut')) return; 
        w.classList.add('cut');
        
        if(w.innerText === BOMB_STATE.questions[BOMB_STATE.currentQ].correct) { 
            playSound('correct'); 
            BOMB_STATE.currentQ++; 
            setTimeout(loadBombQuestion, 400); 
        } else { 
            w.classList.add('cut-wrong'); 
            explodeBomb(); 
        }
    }
    
    function explodeBomb() { 
        BOMB_STATE.isExploded = true; 
        clearInterval(BOMB_STATE.interval); 
        playSound('wrong'); 
        document.body.classList.add('exploded-bg'); 
        document.getElementById('bomb-timer-ui').innerText="ERR.OR"; 
        document.getElementById('bomb-timer-ui').style.color="#000"; 
        document.getElementById('bomb-timer-ui').style.background="#ef4444"; 
        setTimeout(() => { triggerFinal(false, "BOMBA PATLADI! 💥", "Süre doldu veya yanlış kestin."); }, 1500); 
    }
    
    function defuseBombWin() { 
        BOMB_STATE.isExploded = true; 
        clearInterval(BOMB_STATE.interval); 
        playSound('win'); 
        GAME_STATE.score += Math.floor(BOMB_STATE.timeLimit*100 + BOMB_STATE.timeRemaining/10); 
        addXP(BOMB_STATE.timeLimit*40); 
        document.getElementById('bomb-timer-ui').style.color="#22c55e"; 
        setTimeout(() => triggerFinal(false, "BOMB DEFUSED! 🛡️", "Şehri kurtardın!"), 1000); 
    }

    function initWheel() { 
        showScreen('wheel-screen'); 
        drawWheelCanvas(); 
        document.getElementById('wheel-canvas').style.transform = `rotate(0deg)`; 
        WHEEL_STATE.currentRot = 0; 
        WHEEL_STATE.isSpinning = false; 
        document.getElementById('spin-btn').innerText = "ÇEVİR!"; 
    }
    
    function drawWheelCanvas() {
        const ctx = document.getElementById('wheel-canvas').getContext('2d'); 
        const slices = WHEEL_TASKS.length; 
        const ang = (2*Math.PI)/slices; 
        const cols = ["#ef4444", "#3b82f6", "#22c55e", "#eab308", "#a855f7", "#f43f5e"];
        ctx.clearRect(0,0,550,550); 
        ctx.translate(275,275);
        for(let i=0; i<slices; i++) { 
            ctx.beginPath(); ctx.moveTo(0,0); 
            ctx.arc(0,0,275, i*ang, (i+1)*ang); 
            ctx.fillStyle=cols[i%cols.length]; 
            ctx.fill(); ctx.stroke(); 
            ctx.save(); 
            ctx.rotate(i*ang+ang/2); 
            ctx.textAlign="right"; 
            ctx.textBaseline="middle"; 
            ctx.fillStyle="#fff"; 
            ctx.font="bold 16px Arial"; 
            ctx.fillText(i+1, 250, 0); 
            ctx.restore(); 
        } 
        ctx.translate(-275,-275);
    }
    
    function spinWheel() {
        if(WHEEL_STATE.isSpinning) return; 
        WHEEL_STATE.isSpinning = true; 
        document.getElementById('spin-btn').innerText = "DÖNÜYOR..."; 
        playSound('correct');
        
        let total = ((5+Math.random()*5)*360) + Math.floor(Math.random()*360); 
        WHEEL_STATE.currentRot += total;
        document.getElementById('wheel-canvas').style.transform = `rotate(${WHEEL_STATE.currentRot}deg)`;
        
        setTimeout(() => {
            WHEEL_STATE.isSpinning = false; 
            document.getElementById('spin-btn').innerText = "YENİDEN ÇEVİR!"; 
            playSound('win');
            
            let deg = (360 - (WHEEL_STATE.currentRot % 360) + 270) % 360; 
            let idx = Math.floor(deg / (360/WHEEL_TASKS.length));
            
            document.getElementById('wheel-task-num').innerText = `GÖREV KARTI #${idx + 1}`; 
            document.getElementById('wheel-task-text').innerText = WHEEL_TASKS[idx]; 
            document.getElementById('wheel-result-modal').style.display = 'flex';
            
            addXP(100); 
        }, 4100);
    }
    
    function startMemoryCards(uWords) {
        showScreen('memory-screen');
        MEMORY_STATE.firstCard = null;
        MEMORY_STATE.secondCard = null;
        MEMORY_STATE.lockBoard = false;
        MEMORY_STATE.matched = 0;
        MEMORY_STATE.moves = 0;
        GAME_STATE.score = 0;
        document.getElementById('mem-score-ui').innerText = "0/8";
        document.getElementById('mem-moves-ui').innerText = "0";
        
        let pool = [...uWords].sort(()=>Math.random()-0.5).slice(0, 8);
        let cardsData = [];
        pool.forEach((w, index) => {
            cardsData.push({ text: w.en, pair: w.en, type: 'en', id: index });
            cardsData.push({ text: w.tr, pair: w.en, type: 'tr', id: index });
        });
        cardsData.sort(()=>Math.random()-0.5);
        
        const grid = document.getElementById('memory-grid');
        grid.innerHTML = '';
        cardsData.forEach(card => {
            let el = document.createElement('div');
            el.className = 'mem-card';
            el.dataset.pair = card.pair;
            el.dataset.type = card.type;
            
            let inner = document.createElement('div');
            inner.className = 'mem-inner';
            
            let front = document.createElement('div');
            front.className = 'mem-front';
            front.innerText = "?";
            
            let back = document.createElement('div');
            back.className = 'mem-back';
            back.innerText = card.text;
            
            inner.appendChild(front);
            inner.appendChild(back);
            el.appendChild(inner);
            
            el.onclick = () => flipMemoryCard(el);
            grid.appendChild(el);
        });
    }

    function flipMemoryCard(card) {
        if (MEMORY_STATE.lockBoard) return;
        if (card.classList.contains('flipped') || card.classList.contains('matched')) return;

        card.classList.add('flipped');
        playSound('correct');

        if (!MEMORY_STATE.firstCard) {
            MEMORY_STATE.firstCard = card;
            return;
        }

        MEMORY_STATE.secondCard = card;
        MEMORY_STATE.lockBoard = true;
        MEMORY_STATE.moves++;
        document.getElementById('mem-moves-ui').innerText = MEMORY_STATE.moves;

        if (MEMORY_STATE.firstCard.dataset.pair === MEMORY_STATE.secondCard.dataset.pair && MEMORY_STATE.firstCard.dataset.type !== MEMORY_STATE.secondCard.dataset.type) {
            // Eşleşme doğru
            setTimeout(() => {
                MEMORY_STATE.firstCard.classList.add('matched');
                MEMORY_STATE.secondCard.classList.add('matched');
                MEMORY_STATE.matched++;
                GAME_STATE.score += 200;
                addXP(100);
                document.getElementById('mem-score-ui').innerText = `${MEMORY_STATE.matched}/8`;
                playSound('bonus');
                resetMemoryBoard();

                if (MEMORY_STATE.matched === 8) {
                    setTimeout(() => triggerFinal(false, "HAFIZA USTASI!", "Tüm kartları başarıyla eşleştirdin."), 1000);
                }
            }, 600);
        } else {
            // Eşleşme yanlış
            setTimeout(() => {
                MEMORY_STATE.firstCard.classList.remove('flipped');
                MEMORY_STATE.secondCard.classList.remove('flipped');
                playSound('wrong');
                resetMemoryBoard();
            }, 1000);
        }
    }

    function resetMemoryBoard() {
        MEMORY_STATE.firstCard = null;
        MEMORY_STATE.secondCard = null;
        MEMORY_STATE.lockBoard = false;
    }

    function startWordRain(uWords) {
        showScreen('rain-screen');
        RAIN_STATE.hp = 3;
        GAME_STATE.score = 0;
        document.getElementById('rain-score-ui').innerText = "0";
        document.getElementById('rain-hp-ui').innerText = "❤️❤️❤️";
        document.getElementById('rain-area').innerHTML = '';
        
        let pool = [...uWords];
        
        function spawnDrop() {
            if(RAIN_STATE.hp <= 0) return;
            
            let targetQ = pool[Math.floor(Math.random()*pool.length)];
            RAIN_STATE.targetWord = targetQ.en;
            document.getElementById('rain-target-ui').innerText = targetQ.tr;
            
            // Yağacak kelimeler: 1 doğru, gerisi yanlış
            let options = [targetQ.en];
            while(options.length < 3) {
                let r = pool[Math.floor(Math.random()*pool.length)].en;
                if(!options.includes(r)) options.push(r);
            }
            options.sort(()=>Math.random()-0.5);
            
            options.forEach((opt, index) => {
                let drop = document.createElement('div');
                drop.className = 'raindrop';
                drop.innerText = opt;
                drop.style.left = (15 + (index * 30)) + "%";
                
                let duration = (5 + Math.random()*3) / RAIN_STATE.speedMod;
                drop.style.animation = `rainFall ${duration}s linear forwards`;
                
                drop.onclick = () => {
                    if(drop.innerText === RAIN_STATE.targetWord) {
                        playSound('correct');
                        drop.classList.add('rain-explode');
                        GAME_STATE.score += 100;
                        addXP(50);
                        document.getElementById('rain-score-ui').innerText = GAME_STATE.score;
                    } else {
                        playSound('wrong');
                        RAIN_STATE.hp--;
                        updateRainHP();
                        drop.style.background = 'var(--danger)';
                    }
                    setTimeout(() => {
                        if(drop && drop.parentNode) drop.parentNode.removeChild(drop);
                    }, 300);
                };
                
                document.getElementById('rain-area').appendChild(drop);
                RAIN_STATE.fallingDivs.push(drop);
            });
        }
        
        RAIN_STATE.spawnInterval = setInterval(spawnDrop, 3000 / RAIN_STATE.speedMod);
        spawnDrop();
    }

    function updateRainHP() {
        let hpStr = "";
        for(let i=0; i<RAIN_STATE.hp; i++) hpStr += "❤️";
        document.getElementById('rain-hp-ui').innerText = hpStr;
        if(RAIN_STATE.hp <= 0) {
            clearInterval(RAIN_STATE.spawnInterval);
            setTimeout(() => triggerFinal(false, "ISLANDIN!", "Canın bitti."), 500);
        }
    }

    function startVoltageCut(uWords, aWords) {
        showScreen('voltage-screen');
        VOLTAGE_STATE.currentQ = 0;
        GAME_STATE.score = 0;
        
        function nextVoltageQ() {
            if(VOLTAGE_STATE.currentQ >= VOLTAGE_STATE.maxQ) {
                triggerFinal(false, "TAM BAĞLANTI!", "Tüm kabloları başarıyla onardın.");
                return;
            }
            
            let q = uWords[Math.floor(Math.random()*uWords.length)];
            VOLTAGE_STATE.targetWord = q.en;
            document.getElementById('voltage-target').innerText = `Hedef: ${q.tr}`;
            
            document.getElementById('v-start-node').innerText = q.en;
            
            // Hedefi rastgele bir yere koy (yukarı veya aşağı)
            let endNode = document.getElementById('v-end-node');
            let isUp = Math.random() > 0.5;
            endNode.style.top = isUp ? "20%" : "70%";
            endNode.innerText = q.tr; // Aslında hedefin türkçesini göstermiyoruz ama mantık için koyalım
            
            // Yanıltıcı seçenekler ekleyebilirsin, basitlik için tek hedef yapıldı.
            setupVoltageWire();
        }
        
        nextVoltageQ();
    }

    function setupVoltageWire() {
        let area = document.getElementById('voltage-area');
        let startNode = document.getElementById('v-start-node');
        let wire = document.getElementById('v-wire-main');
        let endNode = document.getElementById('v-end-node');
        
        wire.classList.remove('v-active-wire');
        wire.style.width = '0px';
        
        let startX = startNode.offsetLeft + startNode.offsetWidth / 2;
        let startY = startNode.offsetTop + startNode.offsetHeight / 2;
        wire.style.left = startX + 'px';
        wire.style.top = startY + 'px';

        function getMousePos(e) {
            let rect = area.getBoundingClientRect();
            let clientX = e.touches ? e.touches[0].clientX : e.clientX;
            let clientY = e.touches ? e.touches[0].clientY : e.clientY;
            return { x: clientX - rect.left, y: clientY - rect.top };
        }

        function onMove(e) {
            if(!VOLTAGE_STATE.isDragging) return;
            let pos = getMousePos(e);
            let dx = pos.x - startX;
            let dy = pos.y - startY;
            let dist = Math.sqrt(dx*dx + dy*dy);
            let angle = Math.atan2(dy, dx) * 180 / Math.PI;
            
            wire.style.width = dist + 'px';
            wire.style.transform = `rotate(${angle}deg)`;
        }

        function onEnd(e) {
            if(!VOLTAGE_STATE.isDragging) return;
            VOLTAGE_STATE.isDragging = false;
            area.removeEventListener('mousemove', onMove);
            area.removeEventListener('mouseup', onEnd);
            area.removeEventListener('touchmove', onMove);
            area.removeEventListener('touchend', onEnd);
            
            let pos = getMousePos(e.changedTouches ? e.changedTouches[0] : e);
            let endX = endNode.offsetLeft + endNode.offsetWidth / 2;
            let endY = endNode.offsetTop + endNode.offsetHeight / 2;
            
            let distToTarget = Math.sqrt(Math.pow(pos.x - endX, 2) + Math.pow(pos.y - endY, 2));
            
            if(distToTarget < 60) {
                // Doğru bağlandı
                playSound('correct');
                wire.classList.add('v-active-wire');
                area.classList.add('zap-effect');
                setTimeout(() => area.classList.remove('zap-effect'), 300);
                GAME_STATE.score += 150;
                addXP(50);
                VOLTAGE_STATE.currentQ++;
                setTimeout(() => startVoltageCut(MASTER_DICT[GAME_STATE.unit].words, []), 1000); // Reload Q
            } else {
                // Koptu
                playSound('wrong');
                wire.style.width = '0px';
                wire.style.background = 'var(--danger)';
            }
        }

        startNode.onmousedown = (e) => { e.preventDefault(); VOLTAGE_STATE.isDragging = true; area.addEventListener('mousemove', onMove); area.addEventListener('mouseup', onEnd); };
        startNode.ontouchstart = (e) => { e.preventDefault(); VOLTAGE_STATE.isDragging = true; area.addEventListener('touchmove', onMove); area.addEventListener('touchend', onEnd); };
    }

    function startCrateBreaker(uWords, aWords) {
        showScreen('crate-screen');
        CRATE_STATE.currentQ = 0;
        GAME_STATE.score = 0;
        
        function nextCrateQ() {
            if(CRATE_STATE.currentQ >= CRATE_STATE.maxQ) {
                triggerFinal(false, "KASALAR PARÇALANDI!", "İçindeki tüm gizli kelimeleri buldun.");
                return;
            }
            
            CRATE_STATE.hits = [0,0,0];
            let q = uWords[Math.floor(Math.random()*uWords.length)];
            document.getElementById('crate-q-text').innerText = `KIR: "${q.en}"`;
            
            let opts = [q.tr];
            while(opts.length < 3) {
                let r = aWords[Math.floor(Math.random()*aWords.length)].tr;
                if(!opts.includes(r)) opts.push(r);
            }
            opts.sort(()=>Math.random()-0.5);
            
            for(let i=0; i<3; i++) {
                let c = document.getElementById(`crate-${i}`);
                c.className = 'crate'; // Reset
                document.getElementById(`cq-${i}`).innerText = opts[i];
                if(opts[i] === q.tr) CRATE_STATE.correctIdx = i;
            }
        }
        
        nextCrateQ();
    }

    function hitCrate(idx) {
        let c = document.getElementById(`crate-${idx}`);
        if(c.classList.contains('crate-broken')) return;
        
        if(idx === CRATE_STATE.correctIdx) {
            CRATE_STATE.hits[idx]++;
            playSound('correct');
            
            if(CRATE_STATE.hits[idx] === 1) c.classList.add('crate-cracked-1');
            else if(CRATE_STATE.hits[idx] === 2) c.classList.add('crate-cracked-2');
            else if(CRATE_STATE.hits[idx] === 3) {
                c.classList.add('crate-broken');
                playSound('bonus');
                GAME_STATE.score += 200;
                addXP(100);
                setTimeout(() => {
                    CRATE_STATE.currentQ++;
                    startCrateBreaker(MASTER_DICT[GAME_STATE.unit].words, []); // Reload
                }, 1000);
            }
        } else {
            playSound('wrong');
            c.style.animation = 'shake 0.2s';
            setTimeout(()=>c.style.animation='', 200);
        }
    }

    /* --- BİTİŞ EKRANI (Dinamik Final) --- */
    function triggerFinal(man, cT=null, cQ=null) {
        playSound('win'); 
        const s = document.getElementById('end-screen');
        const h = document.getElementById('end-header');
        const q = document.getElementById('end-quote'); 
        document.getElementById('end-score').innerText = GAME_STATE.score;
        
        if(cT) {
            h.innerText = cT; 
            q.innerText = `"${cQ}"`;
        } else {
            if(GAME_STATE.theme === 'cs2') { 
                h.innerText = Math.random() > 0.5 ? "COUNTER-TERRORISTS WIN 💣" : "TERRORISTS WIN 💥"; 
                q.innerText = '"Bomb defused. Good work team."'; 
            }
            else if(GAME_STATE.theme === 'Vessel') { 
                h.innerText = "YOU BRATS ARE MAYBE WORTH TO LİVE"; 
                q.innerText = '"You brats are truly talented; make the most of it."'; 
            }
            else if(GAME_STATE.theme === 'Honored') { 
                h.innerText = "Between earth and sky, you childrens are alone and masters"; 
                q.innerText = '"Congratulations, youve proven your worth. You cant be as good as me, though."'; 
            }
            else if(GAME_STATE.theme === 'Gambler') { 
                h.innerText = "THİS İS  BETTER THAN İ TOUGH JACKPOT! 🎰"; 
                q.innerText = '"you kids must be better than a gambler not gonna lie"'; 
            }
            else { 
                h.innerText = "GÖREV TAMAMLANDI! 🏆"; 
                q.innerText = '"İngilizce ustası oldun!"'; 
            }
        } 
        s.style.display = 'flex';
    }

    // Sistemin Matrix modunda başlaması
    window.onload = () => { playIntro(); };
</script>
</body>
</html>
