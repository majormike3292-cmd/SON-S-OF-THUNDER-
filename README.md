# SON-S-OF-THUNDER-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="theme-color" content="#030508">
<meta name="description" content="JAKE — SONS OF THUNDER ⚡ The race isn't over.">

<title>JAKE — SONS OF THUNDER ⚡</title>

<style>
/* =========================================================
   JAKE — SONS OF THUNDER
   VERSION 1
   Single-file application
   ========================================================= */

:root {
    --bg: #030508;
    --bg2: #07101a;
    --blue: #00aaff;
    --blue2: #0066ff;
    --white: #f5f8ff;
    --silver: #aeb8c5;
    --red: #ff321f;
    --orange: #ff7a18;
    --card: rgba(8, 15, 24, 0.88);
    --border: rgba(0, 170, 255, 0.38);
    --shadow: 0 0 25px rgba(0, 145, 255, 0.18);
}

* {
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
}

html {
    scroll-behavior: smooth;
    background: var(--bg);
}

body {
    margin: 0;
    min-height: 100vh;
    background:
        radial-gradient(circle at 50% 10%, rgba(0, 120, 255, .14), transparent 35%),
        radial-gradient(circle at 15% 80%, rgba(255, 50, 20, .06), transparent 30%),
        linear-gradient(180deg, #020407 0%, #06101a 50%, #020305 100%);
    color: var(--white);
    font-family: Arial, Helvetica, sans-serif;
    overflow-x: hidden;
}

/* ---------- ATMOSPHERE ---------- */

body::before {
    content: "";
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 1;
    opacity: .18;
    background-image:
        linear-gradient(rgba(255,255,255,.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.018) 1px, transparent 1px);
    background-size: 45px 45px;
}

body::after {
    content: "";
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 20;
    background: radial-gradient(ellipse at center, transparent 45%, rgba(0,0,0,.55) 100%);
}

#particles {
    position: fixed;
    inset: 0;
    pointer-events: none;
    overflow: hidden;
    z-index: 2;
}

.spark {
    position: absolute;
    width: 2px;
    height: 2px;
    border-radius: 50%;
    background: #fff;
    box-shadow: 0 0 7px var(--blue);
    animation: floatSpark linear infinite;
    opacity: .75;
}

@keyframes floatSpark {
    from {
        transform: translateY(105vh) translateX(0);
        opacity: 0;
    }
    15% {
        opacity: .9;
    }
    85% {
        opacity: .7;
    }
    to {
        transform: translateY(-10vh) translateX(80px);
        opacity: 0;
    }
}

/* ---------- APP ---------- */

#app {
    position: relative;
    z-index: 5;
    width: 100%;
    min-height: 100vh;
}

.screen {
    display: none;
    width: 100%;
    min-height: 100vh;
    padding: 24px 18px 45px;
    animation: screenIn .4s ease both;
}

.screen.active {
    display: flex;
    flex-direction: column;
}

@keyframes screenIn {
    from {
        opacity: 0;
        transform: translateY(15px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* ---------- OPENING ---------- */

#opening {
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 30px 20px;
}

.logo-mark {
    width: 110px;
    height: 110px;
    margin: 0 auto 20px;
    border: 2px solid rgba(0,170,255,.7);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    box-shadow:
        0 0 15px rgba(0,170,255,.5),
        inset 0 0 25px rgba(0,170,255,.15);
    animation: pulse 2.5s ease-in-out infinite;
}

.logo-mark::before {
    content: "⚡";
    font-size: 52px;
    color: var(--blue);
    text-shadow:
        0 0 8px #fff,
        0 0 25px var(--blue);
}

.logo-mark::after {
    content: "";
    position: absolute;
    inset: -8px;
    border: 1px solid rgba(255,70,30,.25);
    border-radius: 50%;
    animation: spin 12s linear infinite;
}

@keyframes pulse {
    50% {
        transform: scale(1.04);
        box-shadow:
            0 0 35px rgba(0,170,255,.7),
            inset 0 0 30px rgba(0,170,255,.2);
    }
}

@keyframes spin {
    to {
        transform: rotate(360deg);
    }
}

.brand {
    font-size: clamp(58px, 18vw, 105px);
    line-height: .85;
    font-weight: 1000;
    letter-spacing: -5px;
    color: #fff;
    text-shadow:
        0 0 8px #fff,
        0 0 20px var(--blue),
        0 0 45px rgba(0,140,255,.55);
}

.subtitle {
    margin-top: 14px;
    font-size: clamp(22px, 6vw, 35px);
    letter-spacing: 7px;
    font-weight: 900;
    color: var(--silver);
    text-shadow: 0 0 15px rgba(255,255,255,.25);
}

.race-line {
    margin: 32px auto 18px;
    max-width: 700px;
    font-size: clamp(25px, 7vw, 42px);
    font-weight: 1000;
    color: #fff;
    letter-spacing: 2px;
    text-shadow:
        0 0 10px var(--blue),
        0 0 30px rgba(0,140,255,.7);
}

.opening-copy {
    max-width: 650px;
    margin: 0 auto 30px;
    color: #c7d0dc;
    line-height: 1.75;
    font-size: 16px;
}

.fire-line {
    width: 170px;
    height: 3px;
    margin: 25px auto;
    background: linear-gradient(90deg, transparent, var(--orange), var(--blue), transparent);
    box-shadow: 0 0 15px var(--orange);
}

/* ---------- BUTTONS ---------- */

button {
    font: inherit;
}

.primary-btn,
.menu-btn,
.back-btn,
.action-btn {
    border: 1px solid var(--border);
    color: #fff;
    background:
        linear-gradient(135deg, rgba(0,130,255,.18), rgba(4,9,15,.95));
    box-shadow:
        inset 0 0 18px rgba(0,120,255,.06),
        0 0 16px rgba(0,120,255,.12);
    cursor: pointer;
    transition:
        transform .18s ease,
        box-shadow .18s ease,
        border-color .18s ease,
        background .18s ease;
    -webkit-user-select: none;
    user-select: none;
}

.primary-btn {
    display: inline-block;
    padding: 18px 30px;
    border-radius: 8px;
    font-size: 17px;
    font-weight: 1000;
    letter-spacing: 2px;
    min-width: 240px;
    text-shadow: 0 0 10px var(--blue);
}

.primary-btn:hover,
.menu-btn:hover,
.action-btn:hover {
    transform: translateY(-3px);
    border-color: var(--blue);
    box-shadow:
        0 0 25px rgba(0,150,255,.3),
        inset 0 0 25px rgba(0,130,255,.1);
}

.primary-btn:active,
.menu-btn:active,
.action-btn:active {
    transform: scale(.97);
}

.back-btn {
    align-self: flex-start;
    margin-bottom: 24px;
    padding: 10px 16px;
    border-radius: 7px;
    font-size: 13px;
    font-weight: 900;
    letter-spacing: 1px;
}

.action-btn {
    padding: 17px 20px;
    border-radius: 8px;
    font-weight: 1000;
    letter-spacing: 1px;
}

/* ---------- SECTION HEADER ---------- */

.section-header {
    width: 100%;
    max-width: 950px;
    margin: 0 auto 30px;
}

.section-kicker {
    color: var(--blue);
    font-size: 12px;
    font-weight: 900;
    letter-spacing: 4px;
    margin-bottom: 8px;
}

.section-title {
    margin: 0;
    font-size: clamp(38px, 11vw, 72px);
    line-height: .95;
    font-weight: 1000;
    letter-spacing: -2px;
    text-shadow:
        0 0 8px rgba(255,255,255,.25),
        0 0 30px rgba(0,140,255,.45);
}

.section-intro {
    max-width: 800px;
    color: #bdc7d3;
    font-size: 17px;
    line-height: 1.8;
    margin-top: 18px;
}

/* ---------- MAIN MENU ---------- */

#menu {
    align-items: center;
}

.menu-inner {
    width: 100%;
    max-width: 850px;
    margin: auto;
}

.menu-top {
    text-align: center;
    margin: 15px 0 28px;
}

.menu-top h1 {
    margin: 0;
    font-size: clamp(35px, 10vw, 62px);
    font-weight: 1000;
    text-shadow: 0 0 25px var(--blue);
}

.menu-top p {
    margin: 10px 0 0;
    color: var(--silver);
}

.menu-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 12px;
}

.menu-btn {
    min-height: 92px;
    border-radius: 12px;
    padding: 17px 12px;
    text-align: left;
    font-size: 16px;
    font-weight: 1000;
    letter-spacing: .5px;
}

.menu-btn span {
    display: block;
    font-size: 11px;
    margin-top: 8px;
    color: #71869c;
    font-weight: 600;
}

.menu-btn.secret {
    border-color: rgba(255,120,20,.45);
    background:
        linear-gradient(135deg, rgba(100,35,8,.18), rgba(5,7,10,.95));
}

.menu-btn.secret:hover {
    border-color: var(--orange);
    box-shadow: 0 0 25px rgba(255,100,20,.2);
}

/* ---------- CONTENT ---------- */

.content {
    width: 100%;
    max-width: 950px;
    margin: 0 auto;
}

.quote {
    position: relative;
    margin: 35px 0;
    padding: 30px 24px;
    border-left: 4px solid var(--blue);
    background: linear-gradient(90deg, rgba(0,100,180,.13), transparent);
    font-size: clamp(23px, 6vw, 38px);
    line-height: 1.3;
    font-weight: 900;
    font-style: italic;
    text-shadow: 0 0 15px rgba(0,140,255,.4);
}

.text-block {
    color: #cbd3dd;
    font-size: 17px;
    line-height: 1.9;
}

.text-block strong {
    color: #fff;
}

.big-ending {
    margin: 45px 0 20px;
    text-align: center;
    font-size: clamp(31px, 9vw, 60px);
    font-weight: 1000;
    color: #fff;
    text-shadow:
        0 0 8px #fff,
        0 0 25px var(--blue),
        0 0 45px rgba(0,130,255,.45);
}

.fire-ending {
    text-align: center;
    color: var(--orange);
    font-size: 13px;
    font-weight: 1000;
    letter-spacing: 4px;
}

/* ---------- CARDS ---------- */

.cards {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 14px;
    margin: 25px 0;
}

.card {
    min-height: 130px;
    padding: 22px;
    border-radius: 12px;
    border: 1px solid rgba(0,170,255,.2);
    background:
        linear-gradient(145deg, rgba(12,25,39,.88), rgba(3,7,12,.96));
    box-shadow: var(--shadow);
    position: relative;
    overflow: hidden;
}

.card::after {
    content: "";
    position: absolute;
    width: 90px;
    height: 90px;
    right: -35px;
    bottom: -35px;
    border-radius: 50%;
    background: rgba(0,150,255,.08);
    filter: blur(5px);
}

.card h3 {
    margin: 0 0 12px;
    font-size: 19px;
    font-weight: 1000;
}

.card p {
    margin: 0;
    color: #9daabb;
    line-height: 1.6;
}

.encourage-card {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 110px;
    text-align: center;
    font-weight: 1000;
    font-size: 18px;
    letter-spacing: 1px;
    animation: cardGlow 3s ease-in-out infinite;
}

@keyframes cardGlow {
    50% {
        border-color: rgba(0,170,255,.48);
        box-shadow: 0 0 24px rgba(0,140,255,.18);
    }
}

/* ---------- DREAM ---------- */

.dream-list {
    display: grid;
    gap: 10px;
    margin: 25px 0;
}

.dream-item {
    padding: 18px 20px;
    border-left: 3px solid var(--blue);
    background: rgba(255,255,255,.025);
    font-size: 19px;
    font-weight: 900;
    box-shadow: inset 15px 0 30px rgba(0,130,255,.025);
}

/* ---------- DAUGHTER ---------- */

.photo-placeholder {
    min-height: 260px;
    margin: 30px 0;
    border: 2px dashed rgba(0,170,255,.35);
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 30px;
    background:
        radial-gradient(circle, rgba(0,140,255,.09), transparent 60%);
}

.photo-placeholder .icon {
    font-size: 52px;
    margin-bottom: 15px;
}

.photo-placeholder strong {
    font-size: 18px;
}

.photo-placeholder small {
    margin-top: 10px;
    color: #728295;
}

/* ---------- GARAGE ---------- */

.garage {
    padding: 22px;
    border-radius: 15px;
    background:
        linear-gradient(rgba(5,9,13,.82), rgba(2,5,8,.96)),
        repeating-linear-gradient(
            90deg,
            transparent 0,
            transparent 49px,
            rgba(255,255,255,.025) 50px
        );
    border: 1px solid rgba(255,100,20,.22);
}

.garage-title {
    font-size: 13px;
    color: var(--orange);
    letter-spacing: 4px;
    font-weight: 1000;
    margin-bottom: 18px;
}

.tool-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0,1fr));
    gap: 10px;
}

.tool {
    min-height: 100px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    border: 1px solid rgba(255,255,255,.1);
    background: rgba(255,255,255,.025);
    border-radius: 9px;
    font-size: 17px;
    font-weight: 1000;
    transition: .2s ease;
}

.tool:hover {
    transform: translateY(-3px);
    border-color: var(--orange);
}

/* ---------- CAMP ---------- */

.camp-grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0,1fr));
    gap: 12px;
    margin: 28px 0;
}

.camp-card {
    min-height: 170px;
    border-radius: 13px;
    border: 1px solid rgba(0,170,255,.25);
    background: linear-gradient(145deg, rgba(8,20,30,.95), rgba(3,6,9,.98));
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-size: 20px;
    font-weight: 1000;
    box-shadow: 0 0 20px rgba(0,100,180,.1);
}

.camp-card .emoji {
    font-size: 48px;
    margin-bottom: 15px;
}

/* ---------- PRAYER ---------- */

.reminder-box {
    margin: 25px 0;
    padding: 25px;
    border-radius: 15px;
    text-align: center;
    background:
        radial-gradient(circle at center, rgba(0,130,255,.15), transparent 65%),
        rgba(5,10,17,.92);
    border: 1px solid rgba(0,170,255,.3);
}

#reminderText {
    min-height: 80px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 25px 0;
    font-size: clamp(21px, 6vw, 32px);
    line-height: 1.4;
    font-weight: 900;
    text-shadow: 0 0 18px rgba(0,140,255,.45);
}

.prayer {
    margin-top: 30px;
    padding: 25px;
    border: 1px solid rgba(255,255,255,.1);
    border-radius: 13px;
    background: rgba(255,255,255,.025);
}

.prayer h3 {
    margin-top: 0;
    color: var(--blue);
    letter-spacing: 3px;
}

.prayer p {
    color: #c8d0da;
    line-height: 1.85;
    font-style: italic;
}

/* ---------- FUTURE ---------- */

.legacy-grid {
    display: grid;
    grid-template-columns: repeat(2,1fr);
    gap: 12px;
    margin-top: 25px;
}

.legacy-card {
    padding: 25px;
    min-height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    border: 1px solid rgba(255,120,20,.25);
    background: linear-gradient(145deg, rgba(80,30,5,.13), rgba(5,8,12,.95));
    border-radius: 12px;
    font-size: 20px;
    font-weight: 1000;
    letter-spacing: 2px;
}

/* ---------- SECRET ---------- */

#secret {
    text-align: center;
}

.lock {
    font-size: 75px;
    margin: 20px auto;
    filter: drop-shadow(0 0 18px var(--blue));
}

.locked-box {
    max-width: 500px;
    width: 100%;
    margin: auto;
    padding: 30px 20px;
    border: 1px solid rgba(0,170,255,.3);
    border-radius: 15px;
    background: rgba(3,8,14,.92);
    box-shadow: 0 0 35px rgba(0,100,200,.12);
}

.password-input {
    width: 100%;
    margin: 20px 0 12px;
    padding: 16px;
    border-radius: 7px;
    border: 1px solid rgba(0,170,255,.35);
    background: #020508;
    color: #fff;
    text-align: center;
    font-size: 18px;
    font-weight: 900;
    letter-spacing: 4px;
    outline: none;
}

.password-input:focus {
    border-color: var(--blue);
    box-shadow: 0 0 20px rgba(0,150,255,.2);
}

.secret-result {
    display: none;
    margin-top: 25px;
    padding: 25px 10px;
}

.secret-result.show {
    display: block;
    animation: screenIn .5s ease;
}

.access {
    color: var(--blue);
    font-size: 26px;
    font-weight: 1000;
    text-shadow: 0 0 20px var(--blue);
}

.secret-message {
    margin-top: 25px;
    color: #d4dce5;
    line-height: 1.8;
}

.letter-placeholder {
    margin-top: 25px;
    padding: 25px;
    border: 1px dashed rgba(255,255,255,.2);
    color: #748395;
    border-radius: 10px;
}

/* ---------- FINAL ---------- */

#final {
    align-items: center;
    justify-content: center;
    text-align: center;
}

.final-content {
    max-width: 800px;
    margin: auto;
}

.final-name {
    font-size: clamp(45px, 13vw, 90px);
    font-weight: 1000;
    text-shadow: 0 0 30px var(--blue);
}

.final-list {
    margin: 30px 0;
    display: grid;
    gap: 7px;
}

.final-list div {
    font-size: clamp(19px, 5vw, 28px);
    font-weight: 900;
    color: #c6d0dc;
}

.final-race {
    margin: 45px 0 25px;
    font-size: clamp(42px, 12vw, 82px);
    line-height: .95;
    font-weight: 1000;
    color: #fff;
    text-shadow:
        0 0 10px #fff,
        0 0 25px var(--blue),
        0 0 55px rgba(0,140,255,.65);
}

.signature {
    color: var(--silver);
    font-size: 18px;
    margin-top: 25px;
}

.facebook-note {
    max-width: 600px;
    margin: 35px auto 0;
    padding: 12px 15px;
    color: #708096;
    font-size: 12px;
    line-height: 1.5;
    border-top: 1px solid rgba(255,255,255,.08);
}

/* ---------- RESPONSIVE ---------- */

@media (max-width: 650px) {
    .screen {
        padding: 20px 15px 40px;
    }

    .menu-grid,
    .cards,
    .legacy-grid {
        grid-template-columns: 1fr;
    }

    .camp-grid {
        grid-template-columns: 1fr;
    }

    .camp-card {
        min-height: 125px;
    }

    .tool-grid {
        grid-template-columns: 1fr 1fr;
    }

    .quote {
        padding: 24px 18px;
    }

    .primary-btn {
        width: 100%;
    }
}

@media (max-width: 380px) {
    .tool-grid {
        grid-template-columns: 1fr;
    }

    .menu-btn {
        min-height: 85px;
        font-size: 14px;
    }
}

/* Accessibility */
button:focus-visible,
input:focus-visible {
    outline: 2px solid var(--blue);
    outline-offset: 3px;
}
</style>
</head>

<body>

<div id="particles"></div>

<div id="app">

<!-- ======================================================
     OPENING SCREEN
     ====================================================== -->

<section id="opening" class="screen active">

    <div class="logo-mark"></div>

    <div class="brand">JAKE</div>

    <div class="subtitle">SON OF THUNDER</div>

    <div class="fire-line"></div>

    <div class="race-line">THE RACE ISN'T OVER.</div>

    <div class="opening-copy">
        You're a survivor. You're a brother. You're a dad.
        You're a son. You're a mechanic. You're a racer.
        And there's still a lot of road ahead.
    </div>

    <button class="primary-btn" onclick="showScreen('menu')">
        ⚡ START THE RIDE ⚡
    </button>

    <div class="facebook-note">
        If a button doesn't respond inside Messenger, tap ⋮ and choose
        <strong>Open in Chrome.</strong>
    </div>

</section>


<!-- ======================================================
     MAIN MENU
     ====================================================== -->

<section id="menu" class="screen">

    <div class="menu-inner">

        <div class="menu-top">
            <div class="section-kicker">WELCOME BACK, JAKE</div>
            <h1>SONS OF THUNDER ⚡</h1>
            <p>Choose your road.</p>
        </div>

        <div class="menu-grid">

            <button class="menu-btn" onclick="showScreen('ride')">
                🏍️ THE RIDE
                <span>TWO WHEELS • DIRT • SPEED</span>
            </button>

            <button class="menu-btn" onclick="showScreen('sons')">
                ⚡ SONS OF THUNDER
                <span>JAKE + MIKE</span>
            </button>

            <button class="menu-btn" onclick="showScreen('fearless')">
                🔥 FEARLESS
                <span>KEEP MOVING FORWARD</span>
            </button>

            <button class="menu-btn" onclick="showScreen('dream')">
                🏁 THE DREAM
                <span>THE PROFESSIONAL DREAM</span>
            </button>

            <button class="menu-btn" onclick="showScreen('daughter')">
                👧 HIS LITTLE GIRL
                <span>DAD • DAUGHTER • LEGACY</span>
            </button>

            <button class="menu-btn" onclick="showScreen('mechanic')">
                🔧 THE MECHANIC
                <span>BUIL
