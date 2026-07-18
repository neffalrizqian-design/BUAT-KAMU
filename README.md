<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>💖 Nembak Cewe · Modern</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            min-height: 100vh;
            background: linear-gradient(145deg, #fce4ec, #f8bbd0);
            font-family: 'Nunito', sans-serif;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            padding: 1rem;
            position: relative;
            overflow-y: auto;
            overflow-x: hidden;
        }

        #love-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            opacity: 0.6;
        }

        .card {
            position: relative;
            z-index: 10;
            max-width: 520px;
            width: 100%;
            background: rgba(255, 248, 250, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-radius: 48px;
            padding: 1.5rem 1.5rem 2rem;
            box-shadow: 0 30px 60px rgba(180, 60, 100, 0.2), 0 0 0 1px rgba(255, 200, 215, 0.5);
            border: 1px solid rgba(255, 220, 235, 0.6);
            text-align: center;
            margin: 0.5rem auto;
            max-height: 95vh;
            overflow-y: auto;
        }

        .card::-webkit-scrollbar {
            width: 4px;
        }
        .card::-webkit-scrollbar-track {
            background: transparent;
        }
        .card::-webkit-scrollbar-thumb {
            background: #ff4d7a;
            border-radius: 10px;
        }

        .nav-tabs {
            display: flex;
            gap: 0.8rem;
            justify-content: center;
            margin-bottom: 1.2rem;
            background: rgba(255, 200, 215, 0.25);
            padding: 0.3rem;
            border-radius: 60px;
            backdrop-filter: blur(4px);
            flex-shrink: 0;
        }
        .nav-tab {
            flex: 1;
            padding: 0.5rem 0.8rem;
            border: none;
            border-radius: 40px;
            font-family: 'Fredoka One', cursive;
            font-size: 0.9rem;
            background: transparent;
            color: #8a4a5e;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }
        .nav-tab i { font-size: 1rem; }
        .nav-tab.active {
            background: linear-gradient(135deg, #ff4d7a, #e63e6b);
            color: white;
            box-shadow: 0 6px 20px rgba(230, 50, 90, 0.35);
            transform: scale(1.02);
        }
        .nav-tab:hover:not(.active) {
            background: rgba(255, 200, 215, 0.4);
            transform: scale(1.04);
        }

        .page { display: none; animation: fadePage 0.4s cubic-bezier(0.34, 1.56, 0.64, 1); }
        .page.active { display: block; }
        @keyframes fadePage {
            0% { opacity: 0; transform: scale(0.92) translateY(10px); }
            100% { opacity: 1; transform: scale(1) translateY(0); }
        }

        .title {
            font-family: 'Fredoka One', cursive;
            font-size: 2rem;
            color: #b31b4b;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            flex-wrap: wrap;
        }
        .title i { color: #d43f6b; font-size: 1.8rem; filter: drop-shadow(0 0 12px #ff8aaa); }
        .sub {
            font-weight: 700;
            font-size: 0.9rem;
            color: #a53f5f;
            background: rgba(255, 200, 215, 0.3);
            display: inline-block;
            padding: 0.2rem 1.5rem;
            border-radius: 60px;
            margin: 0.2rem 0 0.8rem;
            backdrop-filter: blur(4px);
        }

        .question-box {
            background: rgba(255, 255, 255, 0.4);
            backdrop-filter: blur(8px);
            padding: 1rem 0.8rem;
            border-radius: 40px;
            margin: 0.8rem 0 1.2rem;
            border: 1px solid rgba(255, 200, 215, 0.6);
            box-shadow: inset 0 0 20px #ffd0dd;
            min-height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }
        .question-text {
            font-family: 'Fredoka One', cursive;
            font-size: 1.4rem;
            color: #671c3a;
            line-height: 1.4;
            transition: all 0.3s ease;
        }
        .question-text i { color: #c63a62; margin: 0 6px; }

        .btn-group {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 0.8rem;
            margin: 0.8rem 0 0.3rem;
            position: relative;
        }

        .btn-stretch {
            background: linear-gradient(135deg, #ff4d7a, #e63e6b);
            border: none;
            padding: 0.6rem 1.8rem;
            border-radius: 100px;
            color: white;
            font-weight: 800;
            font-size: 1.2rem;
            font-family: 'Fredoka One', cursive;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 10px 28px rgba(230, 50, 90, 0.4);
            cursor: pointer;
            transition: all 0.2s cubic-bezier(0.34, 1.56, 0.64, 1);
            border: 1px solid rgba(255, 255, 255, 0.3);
            min-width: 100px;
            justify-content: center;
            letter-spacing: 1px;
            position: relative;
        }
        .btn-stretch i { font-size: 1.2rem; filter: drop-shadow(0 0 8px #ffbccd); }
        .btn-stretch:hover { transform: scale(1.15) rotate(-2deg); box-shadow: 0 18px 40px #e63e6b; }
        .btn-stretch:active { transform: scale(0.92) rotate(2deg); }

        .btn-tidak {
            background: rgba(255, 240, 245, 0.8);
            backdrop-filter: blur(8px);
            border: 2px solid #ff6f92;
            color: #a1274b;
            box-shadow: 0 6px 18px rgba(200, 70, 110, 0.2);
            transition: all 0.15s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        .btn-tidak:hover { background: #ffdae6; transform: scale(1.12) rotate(2deg); box-shadow: 0 12px 32px #f26f93; }

        .btn-pantun {
            background: rgba(255, 220, 230, 0.6);
            backdrop-filter: blur(8px);
            border: 2px solid #ff7c9e;
            color: #7a1f3f;
            font-family: 'Fredoka One', cursive;
            padding: 0.5rem 1.5rem;
            border-radius: 60px;
            font-size: 1rem;
            font-weight: 700;
            box-shadow: 0 6px 18px rgba(200, 60, 100, 0.15);
            transition: all 0.25s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            border: 1px solid rgba(255, 200, 215, 0.6);
        }
        .btn-pantun:hover { transform: scale(1.12) rotate(-2deg); background: #ffdae6; box-shadow: 0 10px 28px #f26f93; }

        .pantun-box {
            background: rgba(255, 255, 255, 0.35);
            backdrop-filter: blur(8px);
            padding: 1rem 0.8rem;
            border-radius: 40px;
            margin: 0.8rem 0;
            border: 1px solid rgba(255, 200, 215, 0.6);
            box-shadow: inset 0 0 20px #ffd0dd;
            min-height: 80px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .pantun-text {
            font-family: 'Nunito', sans-serif;
            font-weight: 700;
            font-size: 1rem;
            color: #701c3a;
            line-height: 1.6;
            letter-spacing: 0.3px;
        }
        .pantun-text i { color: #c63a62; margin: 0 4px; }

        .footer {
            margin-top: 1rem;
            font-weight: 700;
            color: #a53f62;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            flex-wrap: wrap;
            font-size: 0.85rem;
            background: rgba(255, 200, 215, 0.15);
            padding: 0.3rem 1.2rem;
            border-radius: 60px;
        }

        .jam-container {
            margin-top: 0.8rem;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 6px;
            font-family: 'Fredoka One', cursive;
            font-size: 1.5rem;
            color: #b31b4b;
            background: rgba(255, 200, 215, 0.2);
            padding: 0.3rem 1rem;
            border-radius: 40px;
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255, 200, 215, 0.3);
        }
        .jam-container i {
            font-size: 1.3rem;
            color: #d43f6b;
            margin-right: 4px;
        }
        .jam-angka {
            display: inline-block;
            min-width: 1.8rem;
            text-align: center;
            background: rgba(255, 255, 255, 0.3);
            padding: 0 4px;
            border-radius: 10px;
            transition: all 0.3s ease;
        }
        .jam-angka:hover {
            transform: scale(1.1);
            background: rgba(255, 200, 215, 0.4);
        }
        .jam-titik {
            animation: blinkDot 1s infinite;
        }
        @keyframes blinkDot {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.2; }
        }

        /* VIDEO INTRO - FULL LAYAR BINGKAI */
        .video-container {
            position: relative;
            width: 100%;
            border-radius: 30px;
            overflow: hidden;
            background: #000;
            box-shadow: 0 8px 30px rgba(180, 60, 100, 0.3);
            margin: 0.8rem 0;
            aspect-ratio: 16/9;
            border: 3px solid rgba(255, 200, 215, 0.4);
        }
        .video-container video {
            width: 100%;
            height: 100%;
            display: block;
            border-radius: 27px;
            object-fit: cover;
            background: #000;
        }
        /* Tombol volume lebih besar */
        .video-container video::-webkit-media-controls-volume-slider {
            width: 80px;
        }
        .video-container video::-webkit-media-controls-volume-slider-container {
            width: 80px;
        }

        /* GAME BLOK - DRAG & DROP ANTAR KOLOM */
        .game-container {
            margin: 0.8rem 0;
            padding: 0.5rem;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 30px;
            backdrop-filter: blur(4px);
        }
        .game-grid {
            display: grid;
            grid-template-columns: repeat(6, 1fr);
            gap: 5px;
            max-width: 380px;
            margin: 0 auto;
        }
        .game-cell {
            aspect-ratio: 1;
            background: rgba(255, 200, 215, 0.15);
            border-radius: 10px;
            transition: all 0.3s ease;
            border: 2px solid rgba(255, 200, 215, 0.2);
            cursor: grab;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            user-select: none;
            position: relative;
            min-height: 40px;
            font-weight: bold;
            color: #fff;
        }
        .game-cell.has-block {
            background: #ff4d7a;
            border-color: #ff4d7a;
            box-shadow: 0 0 25px rgba(255, 77, 122, 0.4);
            transform: scale(0.95);
            cursor: grab;
        }
        .game-cell.has-block:hover {
            transform: scale(1.03);
            box-shadow: 0 0 35px rgba(255, 77, 122, 0.6);
        }
        .game-cell.has-block.dragging {
            opacity: 0.5;
            transform: scale(0.8);
        }
        .game-cell.drag-over {
            border-color: #ff4d7a;
            background: rgba(255, 77, 122, 0.25);
            transform: scale(1.06);
            border-width: 3px;
        }
        .game-cell.empty {
            background: rgba(255, 200, 215, 0.08);
            border-style: dashed;
        }
        .game-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.3rem 0;
            flex-wrap: wrap;
            gap: 0.3rem;
        }
        .game-score {
            font-family: 'Fredoka One', cursive;
            font-size: 1.3rem;
            color: #b31b4b;
        }
        .game-score span {
            background: rgba(255, 200, 215, 0.3);
            padding: 0.1rem 0.8rem;
            border-radius: 20px;
        }
        .game-timer {
            font-family: 'Fredoka One', cursive;
            font-size: 1.3rem;
            color: #b31b4b;
        }
        .game-timer span {
            background: rgba(255, 200, 215, 0.3);
            padding: 0.1rem 0.8rem;
            border-radius: 20px;
        }

        .bubble-container {
            position: fixed;
            bottom: -20px;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 20;
            overflow: hidden;
        }
        .bubble {
            position: absolute;
            bottom: -60px;
            font-size: 2rem;
            animation: bubbleUp 2s ease-out forwards;
            opacity: 0;
        }
        @keyframes bubbleUp {
            0% { opacity: 0; transform: translateY(0) scale(0.3) rotate(0deg); }
            15% { opacity: 1; transform: translateY(-20px) scale(1.2) rotate(10deg); }
            80% { opacity: 1; }
            100% { opacity: 0; transform: translateY(-110vh) scale(0.6) rotate(720deg); }
        }

        .love-3d {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 8rem;
            z-index: 30;
            pointer-events: none;
            animation: love3dSpin 2.5s ease-in-out forwards;
            text-shadow: 0 0 50px rgba(255, 50, 100, 0.8);
        }
        @keyframes love3dSpin {
            0% { transform: translate(-50%, -50%) scale(0.2) rotateY(0deg); opacity: 0; }
            15% { transform: translate(-50%, -50%) scale(1.5) rotateY(-180deg); opacity: 1; }
            30% { transform: translate(-50%, -50%) scale(2.0) rotateY(-360deg); opacity: 1; }
            45% { transform: translate(-50%, -50%) scale(2.8) rotateY(-540deg); opacity: 1; }
            60% { transform: translate(-50%, -50%) scale(3.5) rotateY(-720deg); opacity: 1; }
            75% { transform: translate(-50%, -50%) scale(4.5) rotateY(-900deg); opacity: 1; }
            85% { transform: translate(-50%, -50%) scale(5.5) rotateY(-1080deg); opacity: 1; }
            100% { transform: translate(-50%, -50%) scale(0) rotateY(-1260deg); opacity: 0; }
        }

        .explosion-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 25;
            overflow: hidden;
        }
        .explosion-particle {
            position: absolute;
            font-size: 1.8rem;
            animation: explodeParticle 4s ease-out forwards;
            opacity: 0;
        }
        @keyframes explodeParticle {
            0% { opacity: 0; transform: translate(0, 0) scale(0.5) rotate(0deg); }
            10% { opacity: 1; transform: translate(var(--tx), var(--ty)) scale(1.2) rotate(45deg); }
            60% { opacity: 1; }
            100% { opacity: 0; transform: translate(var(--tx2), var(--ty2)) scale(0.3) rotate(360deg); }
        }

        .success-text-overlay {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 35;
            font-family: 'Fredoka One', cursive;
            font-size: 2rem;
            color: #b31b4b;
            text-align: center;
            pointer-events: none;
            animation: fadeTextIn 3s ease-out forwards;
            opacity: 0;
            text-shadow: 0 0 30px rgba(255, 80, 130, 0.5);
            background: rgba(255, 248, 250, 0.7);
            padding: 1.5rem;
            border-radius: 40px;
            backdrop-filter: blur(8px);
            max-width: 90%;
        }
        @keyframes fadeTextIn {
            0% { opacity: 0; transform: translate(-50%, -50%) scale(0.5); }
            30% { opacity: 0; }
            50% { opacity: 1; transform: translate(-50%, -50%) scale(1.1); }
            70% { transform: translate(-50%, -50%) scale(1); }
            100% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
        }

        @media (max-width: 480px) {
            .card { padding: 1rem 0.8rem; max-height: 98vh; }
            .title { font-size: 1.6rem; }
            .question-text { font-size: 1.2rem; }
            .btn-stretch { font-size: 1rem; padding: 0.5rem 1.2rem; min-width: 80px; }
            .nav-tab { font-size: 0.75rem; padding: 0.3rem 0.5rem; }
            .success-text-overlay { font-size: 1.2rem; padding: 1rem; }
            .love-3d { font-size: 5rem; }
            .jam-container { font-size: 1.2rem; }
            .game-grid { gap: 4px; max-width: 300px; }
            .game-cell { font-size: 1.1rem; min-height: 35px; }
            .game-score, .game-timer { font-size: 1rem; }
            .video-container { aspect-ratio: 16/9; }
        }

        @media (max-width: 380px) {
            .card { padding: 0.8rem 0.5rem; }
            .title { font-size: 1.3rem; }
            .question-text { font-size: 1rem; }
            .btn-stretch { font-size: 0.85rem; padding: 0.4rem 0.8rem; min-width: 65px; gap: 4px; }
            .btn-stretch i { font-size: 0.9rem; }
            .nav-tab { font-size: 0.65rem; padding: 0.2rem 0.4rem; gap: 3px; }
            .nav-tab i { font-size: 0.8rem; }
            .game-grid { gap: 3px; max-width: 240px; }
            .game-cell { min-height: 28px; font-size: 0.9rem; }
            .game-score, .game-timer { font-size: 0.8rem; }
            .jam-container { font-size: 1rem; padding: 0.2rem 0.6rem; }
            .jam-angka { min-width: 1.2rem; }
        }
    </style>
</head>
<body>

    <canvas id="love-canvas"></canvas>
    <div class="bubble-container" id="bubbleContainer"></div>
    <div class="explosion-container" id="explosionContainer"></div>

    <div class="card">

        <div class="nav-tabs">
            <button class="nav-tab active" data-page="nembak">
                <i class="fas fa-heart"></i> Nembak
            </button>
            <button class="nav-tab" data-page="pantun">
                <i class="fas fa-book-open"></i> Pantun
            </button>
        </div>

        <!-- HALAMAN NEMBAK -->
        <div class="page active" id="page-nembak">
            <div class="title">
                <i class="fas fa-heart"></i>
                HAII KAMU
                <i class="fas fa-heart"></i>
            </div>
            <div class="sub">
                <i class="fas fa-arrow-right"></i> buat kamu yang spesial <i class="fas fa-arrow-left"></i>
            </div>

            <div class="question-box" id="questionBox">
                <p class="question-text" id="questionText">
                    <i class="fas fa-question-circle"></i>
                    KAMU MAU GA JADI PACAR AKU?
                    <i class="fas fa-question-circle"></i>
                </p>
            </div>

            <div class="btn-group" id="btnGroup">
                <button class="btn-stretch" id="btnIya">
                    <i class="fas fa-check-circle"></i> IYA
                </button>
                <button class="btn-stretch btn-tidak" id="btnTidak">
                    <i class="fas fa-times-circle"></i> TIDAK
                </button>
            </div>

            <div class="footer">
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
                <span id="hitunganCinta">❤️  ∞  ❤️</span>
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
            </div>

            <div class="jam-container">
                <i class="fas fa-clock"></i>
                <span class="jam-angka" id="jam">00</span>
                <span class="jam-titik">:</span>
                <span class="jam-angka" id="menit">00</span>
                <span class="jam-titik">:</span>
                <span class="jam-angka" id="detik">00</span>
            </div>
        </div>

        <!-- HALAMAN PANTUN -->
        <div class="page" id="page-pantun">
            <div class="title">
                <i class="fas fa-feather-alt"></i>
                PANTUN
                <i class="fas fa-feather-alt"></i>
            </div>
            <div class="sub">
                <i class="fas fa-quote-left"></i> BUAT KAMU <i class="fas fa-quote-right"></i>
            </div>

            <div class="pantun-box">
                <p class="pantun-text" id="pantunDisplay">
                    <i class="fas fa-quote-left"></i>
                    Waktu daftar hari terakhir, waktu terasa banyak terbuang.
                    Kamu nggak perlu khawatir, cintaku hanya untukmu seorang.
                    <i class="fas fa-quote-right"></i>
                </p>
            </div>

            <div class="btn-group" style="gap:0.8rem;">
                <button class="btn-pantun" id="btnGantiPantun">
                    <i class="fas fa-random"></i> Ganti Pantun
                </button>
            </div>

            <!-- TOMBOL SELANJUTNYA -->
            <div class="btn-group" style="margin-top:0.3rem;">
                <button class="btn-stretch" id="btnNextToVideo" style="font-size:1rem; padding:0.5rem 1.5rem;">
                    <i class="fas fa-arrow-right"></i> Selanjutnya
                </button>
            </div>

            <div class="footer">
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
                <span>❤️  4 you  ❤️</span>
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
            </div>

            <div class="jam-container">
                <i class="fas fa-clock"></i>
                <span class="jam-angka" id="jam2">00</span>
                <span class="jam-titik">:</span>
                <span class="jam-angka" id="menit2">00</span>
                <span class="jam-titik">:</span>
                <span class="jam-angka" id="detik2">00</span>
            </div>
        </div>

        <!-- HALAMAN VIDEO INTRO (hidden, muncul via tombol) -->
        <div class="page" id="page-video" style="display:none;">
            <div class="title">
                <i class="fas fa-video"></i>
                INTRO
                <i class="fas fa-heart"></i>
            </div>
            <div class="sub">
                <i class="fas fa-play"></i> tonton dulu yaa <i class="fas fa-play"></i>
            </div>

            <div class="video-container">
                <video id="introVideo" controls autoplay playsinline preload="auto" volume="1.0">
                    <source src="wanna_beyours_video.mp4" type="video/mp4">
                    Browser kamu tidak support video.
                </video>
            </div>

            <div class="footer">
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
                <span>❤️  watch me  ❤️</span>
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
            </div>
        </div>

        <!-- HALAMAN GAME (hidden, muncul via video selesai) -->
        <div class="page" id="page-game" style="display:none;">
            <div class="title">
                <i class="fas fa-gamepad"></i>
                SUSUN BLOK
                <i class="fas fa-heart"></i>
            </div>
            <div class="sub">
                <i class="fas fa-cubes"></i> seret blok ke kolom kosong <i class="fas fa-cubes"></i>
            </div>

            <div class="game-container">
                <div class="game-info">
                    <div class="game-score">
                        Skor: <span id="gameScore">0</span>
                    </div>
                    <div class="game-timer">
                        ⏱️ <span id="gameTimer">30</span>s
                    </div>
                </div>
                <div class="game-grid" id="gameGrid"></div>
            </div>

            <div class="btn-group" style="margin-top:0.3rem;">
                <button class="btn-pantun" id="btnResetGame" style="font-size:0.9rem; padding:0.4rem 1.2rem;">
                    <i class="fas fa-redo"></i> Reset Game
                </button>
            </div>

            <div class="footer">
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
                <span>❤️  main yuk  ❤️</span>
                <i class="fas fa-heart" style="color:#d43f6b;"></i>
            </div>
        </div>

    </div>

    <script>
        (function() {
            // ===== PANTUN =====
            const pantunList = [
                "Waktu daftar hari terakhir, waktu terasa banyak terbuang. Kamu nggak perlu khawatir, cintaku hanya untukmu seorang.",
                "Api kecil dari tungku, apinya kecil habis kayu. Sudah lama kutunggu-tunggu, kapan kamu bilang i love you.",
                "Ayam goreng setengah mateng, belinya di depan tugu. Abang sayang, abangku ganteng, neng di sini setia menunggu.",
                "Jalanan lagi lancar, itu adalah sebuah berkah. Aku bukan nyari pacar, tapi, nyari yang mau diajak nikah.",
                "Minum sekoteng hangat rasanya, minum segelas ada yang minta. Laki-laki ganteng siapa yang punya? Bolehkah aku jatuh cinta.",
                "Bagaimana memanjat pohon randu? Tangan di atas kaki ke hulu. Bagaimana hati tak rindu? Pacarnya lembut suka melucu.",
                "Paling banyak burung gelatik, di atas terbang melayang. Memang banyak wanita cantik, cuma engkau yang aku sayang.",
                "Seribu bebek di kandang singa, hanya satu berwarna belang. Beribu cewek di Indonesia, hanya engkau yang aku sayang.",
                "Bawa paku dipukul batu, dicampur jamu di atas tungku. Cintaku cukuplah satu, untuk kamu sepanjang waktu.",
                "Air mawar di dalam cangkir, disimpan kendi di bawah parang. Sedari awal hinggalah akhir, sayangku tercurah untukmu seorang.",
                "Main mata sambil mesem-mesem, tetep cinta meski baunya asem. Panasin mentega karena mulai beku, kamu mau gak jadi imamku?",
                "Layang-layang terbang melayang, jatuh ke laut taunya hilang. Siapa bilang abang tak sayang, siang malam terbayang-bayang.",
                "Ada duri dalam saku, saku panas tangan pun melepuh. Demi kekasih cantikku, jalan berliku akan ku tempuh.",
                "Malam hari bunga layu, apalagi putik si melati. Abang jangan terus merayu, takut meleleh hatiku ini.",
                "Ke Citayam membeli kenur, pulangnya lewat Pekanbaru. Dari malam susah tidur, selalu teringat wajah cantikmu.",
                "Ke Jakarta naik pesawat, turunnya di Kebakkramat. Kalau cinta sudah melekat, roti basi berasa cokelat.",
                "Habis minum kopi, lanjut makan sayur bayam. Gak ketemu kamu sehari, serasa dua puluh empat jam.",
                "Pulau Buru indah sangat, lihat pantainya bikin tak jemu. Walau bau ketekmu agak menyengat, tapi aku bahagia di sampingmu.",
                "Senangnya jalan-jalan ke Bali, ketemu mantan lagi pacaran. Janganlah gantung perasaan ini, karena hatiku bukanlah jemuran.",
                "Bawa peti ke tengah kota, jatuh di kali berair amis. Setiap kulihat senyum adinda, kopi pahit terasa manis."
            ];

            // ===== DOM =====
            const questionText = document.getElementById('questionText');
            const questionBox = document.getElementById('questionBox');
            const btnIya = document.getElementById('btnIya');
            const btnTidak = document.getElementById('btnTidak');
            const hitunganCinta = document.getElementById('hitunganCinta');
            const pantunDisplay = document.getElementById('pantunDisplay');
            const btnGantiPantun = document.getElementById('btnGantiPantun');
            const btnNextToVideo = document.getElementById('btnNextToVideo');
            const btnResetGame = document.getElementById('btnResetGame');
            const bubbleContainer = document.getElementById('bubbleContainer');
            const explosionContainer = document.getElementById('explosionContainer');
            const video = document.getElementById('introVideo');
            const gameGrid = document.getElementById('gameGrid');
            const gameScoreEl = document.getElementById('gameScore');
            const gameTimerEl = document.getElementById('gameTimer');

            let loveCount = 0;
            let isSuccess = false;
            let tidakCount = 0;
            let tidakPosisi = { x: 0, y: 0 };

            // ===== GAME VARIABLES =====
            let gridSize = 6;
            let grid = [];
            let score = 0;
            let timer = 30;
            let gameRunning = false;
            let timerInterval = null;
            let draggedIndex = null;
            let dragTargetIndex = null;

            // ===== JAM =====
            function updateJam() {
                const now = new Date();
                const j = String(now.getHours()).padStart(2, '0');
                const m = String(now.getMinutes()).padStart(2, '0');
                const d = String(now.getSeconds()).padStart(2, '0');
                
                document.getElementById('jam').textContent = j;
                document.getElementById('menit').textContent = m;
                document.getElementById('detik').textContent = d;
                document.getElementById('jam2').textContent = j;
                document.getElementById('menit2').textContent = m;
                document.getElementById('detik2').textContent = d;
            }
            updateJam();
            setInterval(updateJam, 1000);

            // ===== NAVIGASI =====
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
                    this.classList.add('active');
                    const page = this.dataset.page;
                    document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
                    document.getElementById('page-' + page).style.display = 'block';
                    document.getElementById('page-' + page).classList.add('active');
                });
            });

            // ===== CANVAS LOVE RAIN =====
            const canvas = document.getElementById('love-canvas');
            const ctx = canvas.getContext('2d');
            let width, height;
            let hearts = [];

            function resize() {
                width = canvas.width = window.innerWidth;
                height = canvas.height = window.innerHeight;
            }
            window.addEventListener('resize', resize);
            resize();

            class Heart {
                constructor() {
                    this.reset();
                }
                reset() {
                    this.x = Math.random() * width;
                    this.y = Math.random() * height - height;
                    this.size = 10 + Math.random() * 18;
                    this.speed = 0.4 + Math.random() * 1.0;
                    this.opacity = 0.25 + Math.random() * 0.5;
                    this.color = `hsl(${340 + Math.random() * 25}, 80%, 70%)`;
                    this.phase = Math.random() * Math.PI * 2;
                    this.swing = 0.2 + Math.random() * 0.4;
                }
                update() {
                    this.y += this.speed;
                    this.x += Math.sin(this.phase) * this.swing;
                    this.phase += 0.03;
                    if (this.y > height + 50) {
                        this.reset();
                        this.y = -30 - Math.random() * 40;
                    }
                    if (this.x < -30) this.x = width + 20;
                    if (this.x > width + 30) this.x = -20;
                }
                draw() {
                    ctx.save();
                    ctx.globalAlpha = this.opacity;
                    ctx.font = `${this.size}px "Segoe UI Emoji", "Apple Color Emoji", sans-serif`;
                    ctx.textAlign = 'center';
                    ctx.textBaseline = 'middle';
                    ctx.shadowColor = 'rgba(255,100,150,0.2)';
                    ctx.shadowBlur = 10;
                    ctx.fillStyle = this.color;
                    ctx.fillText('❤️', this.x, this.y);
                    ctx.restore();
                }
            }

            for (let i = 0; i < 20; i++) {
                const h = new Heart();
                h.y = Math.random() * height;
                hearts.push(h);
            }

            function animateHearts() {
                ctx.clearRect(0, 0, width, height);
                for (let h of hearts) {
                    h.update();
                    h.draw();
                }
                requestAnimationFrame(animateHearts);
            }
            animateHearts();

            // ===== BUBBLE =====
            function spawnBubbles(emojis, count = 25) {
                const emojiList = emojis || ['❤️', '💖', '💗', '💘', '💝', '✨', '🌹', '💕', '❣️', '💋'];
                for (let i = 0; i < count; i++) {
                    const el = document.createElement('div');
                    el.className = 'bubble';
                    el.textContent = emojiList[Math.floor(Math.random() * emojiList.length)];
                    el.style.left = (Math.random() * 90 + 5) + '%';
                    el.style.fontSize = (1.6 + Math.random() * 2.4) + 'rem';
                    el.style.animationDuration = (1.8 + Math.random() * 0.8) + 's';
                    el.style.animationDelay = (Math.random() * 0.5) + 's';
                    bubbleContainer.appendChild(el);
                    setTimeout(() => el.remove(), 3000);
                }
            }

            // ===== EXPLOSION PARTICLES =====
            function createExplosion() {
                const emojis = ['❤️', '💖', '💗', '🌹', '🌸', '🌺', '💕', '💘', '💝', '✨', '⭐', '🌷', '🌻', '💋', '🥰', '😘'];
                const count = 50;
                const centerX = window.innerWidth / 2;
                const centerY = window.innerHeight / 2;

                for (let i = 0; i < count; i++) {
                    const el = document.createElement('div');
                    el.className = 'explosion-particle';
                    el.textContent = emojis[Math.floor(Math.random() * emojis.length)];
                    
                    const angle = Math.random() * Math.PI * 2;
                    const distance = 80 + Math.random() * 350;
                    const tx = Math.cos(angle) * distance;
                    const ty = Math.sin(angle) * distance - 80;
                    const tx2 = Math.cos(angle) * (distance + 80 + Math.random() * 180);
                    const ty2 = Math.sin(angle) * (distance + 80 + Math.random() * 180) - 160;
                    
                    el.style.left = centerX + 'px';
                    el.style.top = centerY + 'px';
                    el.style.setProperty('--tx', tx + 'px');
                    el.style.setProperty('--ty', ty + 'px');
                    el.style.setProperty('--tx2', tx2 + 'px');
                    el.style.setProperty('--ty2', ty2 + 'px');
                    el.style.fontSize = (1.5 + Math.random() * 2.5) + 'rem';
                    el.style.animationDuration = (3.5 + Math.random() * 1.5) + 's';
                    el.style.animationDelay = (Math.random() * 0.8) + 's';
                    
                    explosionContainer.appendChild(el);
                    setTimeout(() => el.remove(), 5000);
                }
            }

            // ===== LOVE 3D SPIN + EXPLOSION =====
            function createLove3D() {
                const loveEl = document.createElement('div');
                loveEl.className = 'love-3d';
                loveEl.textContent = '❤️';
                document.body.appendChild(loveEl);

                setTimeout(() => {
                    const textEl = document.createElement('div');
                    textEl.className = 'success-text-overlay';
                    textEl.innerHTML = `
                        <div style="font-size:2.5rem; margin-bottom:0.3rem;">💖🥰</div>
                        YEEYYYYYY KITA RESMIII JADIANN😘🥰<br>
                        SEMOGA HUBUNGAN INI BERTAHAN<br>
                        SAMPAI SETERUSNYA YAHH CINTAKUHH ❤️
                    `;
                    document.body.appendChild(textEl);
                    setTimeout(() => textEl.remove(), 5000);
                }, 2200);

                setTimeout(() => {
                    createExplosion();
                    spawnBubbles(['❤️', '💖', '💗', '🌹', '🌸', '💕', '💘', '💝', '🥰', '😘'], 35);
                }, 2000);

                setTimeout(() => {
                    loveEl.remove();
                }, 2800);
            }

            // ===== TOMBOL IYA =====
            btnIya.addEventListener('click', function() {
                if (isSuccess) return;
                isSuccess = true;
                loveCount++;
                hitunganCinta.innerHTML = `❤️ ${loveCount} × ∞ ❤️`;

                questionText.innerHTML = `
                    <i class="fas fa-check-circle" style="color:#2e7d32;"></i>
                    YEYYY AKHIRNYA KAMU MAU! 💖
                    <i class="fas fa-check-circle" style="color:#2e7d32;"></i>
                `;

                createLove3D();

                this.style.transform = 'scale(1.3) rotate(-4deg)';
                setTimeout(() => { this.style.transform = ''; }, 200);

                btnTidak.style.display = 'none';
                btnTidak.style.position = '';
                btnTidak.style.left = '';
                btnTidak.style.top = '';
                btnTidak.style.zIndex = '';
                btnTidak.style.transition = '';
            });

            // ===== TOMBOL TIDAK =====
            btnTidak.addEventListener('click', function(e) {
                if (isSuccess) return;

                this.style.transform = 'scale(1.2) rotate(6deg)';
                setTimeout(() => { this.style.transform = ''; }, 150);

                tidakCount++;
                if (tidakCount === 1) {
                    questionText.innerHTML = `
                        <i class="fas fa-angry" style="color:#d32f2f;"></i>
                        HARUSS MAUUU 😤
                        <i class="fas fa-angry" style="color:#d32f2f;"></i>
                    `;
                    spawnBubbles(['😤', '😡', '😠', '💢', '🔥'], 12);
                } else if (tidakCount >= 2 && tidakCount < 7) {
                    questionText.innerHTML = `
                        <i class="fas fa-angry" style="color:#d32f2f; font-size:1.8rem;"></i>
                        POKONYA HARUSS MAUUU 😡😡😡😠
                        <i class="fas fa-angry" style="color:#d32f2f; font-size:1.8rem;"></i>
                    `;
                    spawnBubbles(['😡', '😠', '💢', '🔥', '😤'], 15);
                }

                const maxX = window.innerWidth - 160;
                const maxY = window.innerHeight - 100;
                const minX = 10;
                const minY = 10;
                const newX = minX + Math.random() * (maxX - minX);
                const newY = minY + Math.random() * (maxY - minY);

                this.style.position = 'fixed';
                this.style.left = newX + 'px';
                this.style.top = newY + 'px';
                this.style.zIndex = '30';
                this.style.transition = 'all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1)';

                tidakPosisi.x = newX;
                tidakPosisi.y = newY;

                if (tidakCount >= 7) {
                    tidakCount = 0;
                    setTimeout(() => {
                        if (!isSuccess) {
                            this.style.position = '';
                            this.style.left = '';
                            this.style.top = '';
                            this.style.zIndex = '';
                            this.style.transition = '';
                            questionText.innerHTML = `
                                <i class="fas fa-question-circle"></i>
                                KAMU MAU GA JADI PACAR AKU?
                                <i class="fas fa-question-circle"></i>
                            `;
                        }
                    }, 500);
                }

                const marahEmojis = ['😤', '😡', '😠', '💢', '😭', '😫', '🥺'];
                spawnBubbles(marahEmojis, 8);
            });

            // ===== GANTI PANTUN =====
            function tampilPantunRandom() {
                const idx = Math.floor(Math.random() * pantunList.length);
                pantunDisplay.innerHTML = `
                    <i class="fas fa-quote-left"></i>
                    ${pantunList[idx]}
                    <i class="fas fa-quote-right"></i>
                `;
            }

            btnGantiPantun.addEventListener('click', function() {
                tampilPantunRandom();
                this.style.transform = 'scale(1.15)';
                setTimeout(() => { this.style.transform = ''; }, 100);
            });

            // ===== TOMBOL SELANJUTNYA =====
            btnNextToVideo.addEventListener('click', function() {
                document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
                document.getElementById('page-video').style.display = 'block';
                document.getElementById('page-video').classList.add('active');
                if (video) {
                    video.currentTime = 0;
                    video.volume = 1.0;
                    video.play().catch(e => console.log('Auto-play prevented:', e));
                }
                
                this.style.transform = 'scale(1.2)';
                setTimeout(() => { this.style.transform = ''; }, 200);
            });

            // ===== VIDEO ENDED =====
            if (video) {
                video.addEventListener('ended', function() {
                    document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
                    document.getElementById('page-game').style.display = 'block';
                    document.getElementById('page-game').classList.add('active');
                    initGame();
                });
                
                video.addEventListener('error', function() {
                    console.log('Video error, langsung ke game');
                    document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
                    document.getElementById('page-game').style.display = 'block';
                    document.getElementById('page-game').classList.add('active');
                    initGame();
                });
            }

            // ===== GAME - DRAG & DROP ANTAR KOLOM =====
            function initGame() {
                score = 0;
                timer = 30;
                gameRunning = true;
                gameScoreEl.textContent = '0';
                gameTimerEl.textContent = '30';
                clearInterval(timerInterval);
                generateGrid();
                renderGrid();
                startTimer();
            }

            function generateGrid() {
                grid = [];
                for (let i = 0; i < gridSize * gridSize; i++) {
                    grid.push(false);
                }
                // Tempatkan blok di posisi acak (bentuk kotak² berbeda)
                let placed = 0;
                const numActive = 10 + Math.floor(Math.random() * 8);
                while (placed < numActive) {
                    const idx = Math.floor(Math.random() * (gridSize * gridSize));
                    if (!grid[idx]) {
                        grid[idx] = true;
                        placed++;
                    }
                }
            }

            function renderGrid() {
                gameGrid.innerHTML = '';
                for (let i = 0; i < gridSize * gridSize; i++) {
                    const cell = document.createElement('div');
                    cell.className = 'game-cell';
                    if (grid[i]) {
                        cell.classList.add('has-block');
                        cell.textContent = '❤️';
                    } else {
                        cell.classList.add('empty');
                        cell.textContent = '□';
                    }
                    cell.dataset.index = i;
                    cell.draggable = grid[i];
                    
                    cell.addEventListener('dragstart', handleDragStart);
                    cell.addEventListener('dragend', handleDragEnd);
                    cell.addEventListener('dragover', handleDragOver);
                    cell.addEventListener('dragenter', handleDragEnter);
                    cell.addEventListener('dragleave', handleDragLeave);
                    cell.addEventListener('drop', handleDrop);
                    
                    gameGrid.appendChild(cell);
                }
            }

            function handleDragStart(e) {
                const idx = parseInt(this.dataset.index);
                if (!grid[idx]) {
                    e.preventDefault();
                    return;
                }
                draggedIndex = idx;
                this.classList.add('dragging');
                e.dataTransfer.effectAllowed = 'move';
                e.dataTransfer.setData('text/plain', idx);
            }

            function handleDragEnd(e) {
                this.classList.remove('dragging');
                document.querySelectorAll('.game-cell.drag-over').forEach(el => {
                    el.classList.remove('drag-over');
                });
                if (dragTargetIndex !== null && draggedIndex !== null) {
                    if (grid[dragTargetIndex] === false && draggedIndex !== dragTargetIndex) {
                        grid[dragTargetIndex] = true;
                        grid[draggedIndex] = false;
                        renderGrid();
                        checkMatches();
                    }
                }
                draggedIndex = null;
                dragTargetIndex = null;
            }

            function handleDragOver(e) {
                e.preventDefault();
                e.dataTransfer.dropEffect = 'move';
            }

            function handleDragEnter(e) {
                e.preventDefault();
                const idx = parseInt(this.dataset.index);
                if (grid[idx] === false) {
                    this.classList.add('drag-over');
                    dragTargetIndex = idx;
                }
            }

            function handleDragLeave(e) {
                this.classList.remove('drag-over');
                if (dragTargetIndex === parseInt(this.dataset.index)) {
                    dragTargetIndex = null;
                }
            }

            function handleDrop(e) {
                e.preventDefault();
                this.classList.remove('drag-over');
                const idx = parseInt(this.dataset.index);
                if (draggedIndex !== null && draggedIndex !== idx && grid[idx] === false) {
                    grid[idx] = true;
                    grid[draggedIndex] = false;
                    renderGrid();
                    checkMatches();
                }
                draggedIndex = null;
                dragTargetIndex = null;
            }

            function checkMatches() {
                let matched = [];
                
                // Horizontal
                for (let row = 0; row < gridSize; row++) {
                    let count = 0;
                    let start = row * gridSize;
                    for (let col = 0; col < gridSize; col++) {
                        if (grid[start + col]) {
                            count++;
                        } else {
                            if (count >= 3) {
                                for (let c = col - count; c < col; c++) {
                                    matched.push(start + c);
                                }
                            }
                            count = 0;
                        }
                    }
                    if (count >= 3) {
                        for (let c = gridSize - count; c < gridSize; c++) {
                            matched.push(start + c);
                        }
                    }
                }
                
                // Vertikal
                for (let col = 0; col < gridSize; col++) {
                    let count = 0;
                    for (let row = 0; row < gridSize; row++) {
                        if (grid[row * gridSize + col]) {
                            count++;
                        } else {
                            if (count >= 3) {
                                for (let r = row - count; r < row; r++) {
                                    matched.push(r * gridSize + col);
                                }
                            }
                            count = 0;
                        }
                    }
                    if (count >= 3) {
                        for (let r = gridSize - count; r < gridSize; r++) {
                            matched.push(r * gridSize + col);
                        }
                    }
                }
                
                if (matched.length >= 3) {
                    for (let idx of matched) {
                        grid[idx] = false;
                    }
                    score += matched.length * 10;
                    gameScoreEl.textContent = score;
                    
                    createExplosion();
                    spawnBubbles(['🌟', '✨', '💖', '❤️', '🎉'], 30);
                    
                    timer += Math.min(8, matched.length);
                    gameTimerEl.textContent = timer;
                    
                    renderGrid();
                    generateNewBlocks();
                    renderGrid();
                }
            }

            function generateNewBlocks() {
                const numNew = 4 + Math.floor(Math.random() * 5);
                let added = 0;
                let attempts = 0;
                while (added < numNew && attempts < 500) {
                    attempts++;
                    const idx = Math.floor(Math.random() * (gridSize * gridSize));
                    if (!grid[idx]) {
                        grid[idx] = true;
                        added++;
                    }
                }
            }

            function startTimer() {
                clearInterval(timerInterval);
                timerInterval = setInterval(() => {
                    timer--;
                    gameTimerEl.textContent = timer;
                    
                    if (timer <= 0) {
                        clearInterval(timerInterval);
                        gameRunning = false;
                        spawnBubbles(['💔', '😢', '😭', '💥'], 20);
                        setTimeout(() => {
                            initGame();
                        }, 1500);
                    }
                }, 1000);
            }

            btnResetGame.addEventListener('click', function() {
                initGame();
                this.style.transform = 'scale(1.15)';
                setTimeout(() => { this.style.transform = ''; }, 100);
            });

            // ===== INIT =====
            tampilPantunRandom();

            window.addEventListener('resize', () => {
                if (!isSuccess) {
                    btnTidak.style.position = '';
                    btnTidak.style.left = '';
                    btnTidak.style.top = '';
                    btnTidak.style.zIndex = '';
                    btnTidak.style.transition = '';
                }
            });

        })();
    </script>

</body>
</html>
