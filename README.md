<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ch 18–20 Quiz & Games</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#080b10;--bg2:#0d1117;--bg3:#141923;--bg4:#1b2333;
  --border:rgba(255,255,255,0.055);--border2:rgba(255,255,255,0.1);
  --text:#e2e8f8;--muted:#5e6b88;
  --teal:#2dd4bf;--blue:#60a5fa;--violet:#a78bfa;
  --amber:#fbbf24;--rose:#f87171;--green:#4ade80;--sky:#38bdf8;--pink:#f472b6;
  --mono:'JetBrains Mono',monospace;--sans:'Plus Jakarta Sans',sans-serif;
}
*{box-sizing:border-box;margin:0;padding:0}
body{background:var(--bg);color:var(--text);font-family:var(--sans);font-size:15px;line-height:1.75;min-height:100vh}

/* ─── NAV ─── */
.topbar{display:flex;align-items:center;justify-content:space-between;padding:14px 32px;border-bottom:1px solid var(--border);position:sticky;top:0;background:rgba(8,11,16,.95);backdrop-filter:blur(10px);z-index:100}
.topbar-logo{font-family:var(--mono);font-size:12px;color:var(--teal);letter-spacing:1px}
.topbar-score{font-family:var(--mono);font-size:11px;color:var(--muted)}
.topbar-score span{color:var(--amber);font-size:13px}

/* ─── HERO ─── */
.hero{text-align:center;padding:52px 32px 40px;border-bottom:1px solid var(--border);position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;top:-120px;left:50%;transform:translateX(-50%);width:600px;height:600px;background:radial-gradient(circle,rgba(167,139,250,.07) 0%,transparent 65%);pointer-events:none}
.hero-badge{display:inline-block;font-family:var(--mono);font-size:10px;color:var(--violet);border:1px solid rgba(167,139,250,.3);background:rgba(167,139,250,.08);padding:4px 14px;border-radius:20px;letter-spacing:2px;text-transform:uppercase;margin-bottom:14px}
.hero h1{font-size:38px;font-weight:700;line-height:1.12;margin-bottom:10px}
.hero h1 .g1{background:linear-gradient(90deg,var(--teal),var(--blue));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero h1 .g2{background:linear-gradient(90deg,var(--violet),var(--pink));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-sub{color:var(--muted);max-width:520px;margin:0 auto 28px;font-size:14px}
.mode-btns{display:flex;justify-content:center;gap:10px;flex-wrap:wrap}
.mode-btn{font-family:var(--mono);font-size:11px;padding:10px 20px;border-radius:8px;border:1px solid var(--border2);background:var(--bg3);color:var(--text);cursor:pointer;transition:all .2s;display:flex;align-items:center;gap:8px}
.mode-btn:hover,.mode-btn.active{transform:translateY(-2px);box-shadow:0 4px 20px rgba(0,0,0,.4)}
.mode-btn.m-quiz.active{border-color:var(--teal);color:var(--teal);background:rgba(45,212,191,.08);box-shadow:0 4px 20px rgba(45,212,191,.15)}
.mode-btn.m-flash.active{border-color:var(--blue);color:var(--blue);background:rgba(96,165,250,.08);box-shadow:0 4px 20px rgba(96,165,250,.15)}
.mode-btn.m-tree.active{border-color:var(--violet);color:var(--violet);background:rgba(167,139,250,.08);box-shadow:0 4px 20px rgba(167,139,250,.15)}
.mode-btn.m-sort.active{border-color:var(--amber);color:var(--amber);background:rgba(251,191,36,.08);box-shadow:0 4px 20px rgba(251,191,36,.15)}
.mode-btn.m-match.active{border-color:var(--pink);color:var(--pink);background:rgba(244,114,182,.08);box-shadow:0 4px 20px rgba(244,114,182,.15)}
.mode-btn.m-speed.active{border-color:var(--rose);color:var(--rose);background:rgba(248,113,113,.08);box-shadow:0 4px 20px rgba(248,113,113,.15)}

/* ─── PANEL ─── */
.panel{display:none;max-width:820px;margin:0 auto;padding:40px 32px 80px}
.panel.active{display:block}

/* ─── SHARED CARDS ─── */
.card{background:var(--bg2);border:1px solid var(--border2);border-radius:14px;padding:28px;margin-bottom:24px}
.card-title{font-family:var(--mono);font-size:10px;text-transform:uppercase;letter-spacing:1.5px;margin-bottom:18px;display:flex;align-items:center;gap:8px}

/* ─── BUTTONS ─── */
.btn{font-family:var(--mono);font-size:11px;padding:8px 18px;border-radius:7px;border:1px solid var(--border2);background:var(--bg3);color:var(--text);cursor:pointer;transition:all .18s}
.btn:hover{border-color:var(--teal);color:var(--teal)}
.btn:disabled{opacity:.35;cursor:not-allowed}
.btn-t{border-color:var(--teal);color:var(--teal);background:rgba(45,212,191,.07)}
.btn-v{border-color:var(--violet);color:var(--violet);background:rgba(167,139,250,.07)}
.btn-r{border-color:var(--rose);color:var(--rose);background:rgba(248,113,113,.07)}
.btn-a{border-color:var(--amber);color:var(--amber);background:rgba(251,191,36,.07)}
.btn-g{border-color:var(--green);color:var(--green);background:rgba(74,222,128,.07)}

/* ─── PROGRESS ─── */
.prog-bar{height:4px;background:var(--bg4);border-radius:2px;margin-bottom:28px;overflow:hidden}
.prog-fill{height:100%;background:linear-gradient(90deg,var(--teal),var(--blue));border-radius:2px;transition:width .4s ease}
.prog-label{font-family:var(--mono);font-size:10px;color:var(--muted);margin-bottom:8px;display:flex;justify-content:space-between}

/* ══════════════════════════
   GAME 1 — QUIZ
══════════════════════════ */
.quiz-chapter-tabs{display:flex;gap:8px;margin-bottom:24px;flex-wrap:wrap}
.ctab{font-family:var(--mono);font-size:10px;padding:6px 14px;border-radius:6px;border:1px solid var(--border2);background:var(--bg3);color:var(--muted);cursor:pointer;transition:all .18s}
.ctab.active{border-color:var(--teal);color:var(--teal);background:rgba(45,212,191,.08)}
.q-text{font-size:16px;font-weight:600;color:var(--text);margin-bottom:20px;line-height:1.5}
.q-opts{display:flex;flex-direction:column;gap:8px;margin-bottom:18px}
.q-opt{padding:12px 16px;border:1.5px solid var(--border2);border-radius:9px;cursor:pointer;transition:all .18s;font-size:14px;color:#b8c4dc;background:var(--bg3);text-align:left;font-family:var(--sans)}
.q-opt:hover:not(:disabled){border-color:var(--blue);color:var(--text);background:rgba(96,165,250,.07);transform:translateX(4px)}
.q-opt.cor{border-color:var(--teal)!important;background:rgba(45,212,191,.1)!important;color:var(--teal)!important}
.q-opt.wrg{border-color:var(--rose)!important;background:rgba(248,113,113,.1)!important;color:var(--rose)!important}
.q-opt:disabled{cursor:default}
.q-explain{background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:14px 16px;font-size:13.5px;color:#b8c4dc;margin-top:4px;display:none}
.q-explain.show{display:block}
.q-explain.cor-explain{border-left:3px solid var(--teal)}
.q-explain.wrg-explain{border-left:3px solid var(--rose)}
.streak{font-family:var(--mono);font-size:11px;color:var(--amber);margin-left:auto}

/* ══════════════════════════
   GAME 2 — FLASHCARDS
══════════════════════════ */
.flashcard-wrap{perspective:1000px;margin:0 auto 24px;max-width:560px;height:240px;cursor:pointer}
.flashcard{width:100%;height:100%;position:relative;transform-style:preserve-3d;transition:transform .55s cubic-bezier(.4,0,.2,1)}
.flashcard.flipped{transform:rotateY(180deg)}
.fc-face{position:absolute;width:100%;height:100%;backface-visibility:hidden;border-radius:16px;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:28px;text-align:center}
.fc-front{background:var(--bg2);border:1.5px solid var(--border2)}
.fc-back{background:var(--bg3);border:1.5px solid var(--teal);transform:rotateY(180deg)}
.fc-label{font-family:var(--mono);font-size:9px;text-transform:uppercase;letter-spacing:1.5px;color:var(--muted);margin-bottom:12px}
.fc-text{font-size:17px;font-weight:600;color:var(--text);line-height:1.4}
.fc-sub{font-size:12.5px;color:var(--muted);margin-top:8px;font-family:var(--mono)}
.fc-back .fc-text{color:var(--teal);font-size:15px}
.fc-hint{font-family:var(--mono);font-size:10px;color:var(--muted);text-align:center;margin-bottom:14px}
.fc-nav{display:flex;justify-content:center;gap:12px;align-items:center}
.fc-count{font-family:var(--mono);font-size:11px;color:var(--muted)}
.fc-rating{display:flex;gap:8px;justify-content:center;margin-top:14px}
.fc-rate-btn{font-family:var(--mono);font-size:10px;padding:5px 14px;border-radius:5px;cursor:pointer;border:1px solid;transition:all .18s}
.fcr-easy{border-color:var(--teal);color:var(--teal);background:rgba(45,212,191,.07)}
.fcr-hard{border-color:var(--rose);color:var(--rose);background:rgba(248,113,113,.07)}
.fcr-ok{border-color:var(--amber);color:var(--amber);background:rgba(251,191,36,.07)}

/* ══════════════════════════
   GAME 3 — BUILD A TREE
══════════════════════════ */
.bst-game-wrap{text-align:center}
.bst-instruction{font-family:var(--mono);font-size:12px;color:var(--muted);margin-bottom:14px;padding:10px 14px;background:var(--bg3);border-radius:6px;border:1px solid var(--border)}
#bst-game-svg{width:100%;border-radius:10px;border:1px solid var(--border);background:var(--bg);cursor:crosshair;display:block}
.bst-pending{display:flex;gap:8px;flex-wrap:wrap;margin:12px 0;justify-content:center}
.pend-item{font-family:var(--mono);font-size:13px;padding:6px 14px;border-radius:6px;background:var(--bg3);border:1px solid var(--border2);color:var(--text);cursor:pointer;transition:all .18s}
.pend-item:hover,.pend-item.sel{border-color:var(--teal);color:var(--teal);background:rgba(45,212,191,.08)}
.bst-feedback{font-family:var(--mono);font-size:12px;padding:10px 14px;border-radius:6px;margin-top:10px;min-height:36px}

/* ══════════════════════════
   GAME 4 — ROTATION SORTER
══════════════════════════ */
.rot-scenario{background:var(--bg3);border:1px solid var(--border);border-radius:10px;padding:20px;margin-bottom:18px;text-align:center}
.rot-question{font-size:15px;font-weight:600;margin-bottom:14px}
.rot-choices{display:grid;grid-template-columns:1fr 1fr;gap:10px}
@media(max-width:500px){.rot-choices{grid-template-columns:1fr}}
.rot-choice{padding:14px;border:1.5px solid var(--border2);border-radius:9px;cursor:pointer;font-family:var(--mono);font-size:12px;color:#b8c4dc;background:var(--bg2);transition:all .18s;text-align:center}
.rot-choice:hover:not(:disabled){border-color:var(--violet);color:var(--violet);background:rgba(167,139,250,.08)}
.rot-choice.cor{border-color:var(--teal)!important;background:rgba(45,212,191,.1)!important;color:var(--teal)!important}
.rot-choice.wrg{border-color:var(--rose)!important;background:rgba(248,113,113,.1)!important;color:var(--rose)!important}

/* ══════════════════════════
   GAME 5 — MATCH PAIRS
══════════════════════════ */
.match-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px}
.match-col-title{font-family:var(--mono);font-size:10px;color:var(--muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:8px;text-align:center}
.match-card{padding:11px 14px;border:1.5px solid var(--border2);border-radius:8px;cursor:pointer;font-size:13px;color:#b8c4dc;background:var(--bg3);transition:all .2s;text-align:center;min-height:48px;display:flex;align-items:center;justify-content:center}
.match-card:hover:not(.done){border-color:var(--blue);color:var(--text)}
.match-card.selected{border-color:var(--amber);color:var(--amber);background:rgba(251,191,36,.09);transform:scale(1.02)}
.match-card.matched{border-color:var(--teal);color:var(--teal);background:rgba(45,212,191,.09);cursor:default}
.match-card.wrong{border-color:var(--rose);background:rgba(248,113,113,.09);animation:shake .3s}
@keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-5px)}75%{transform:translateX(5px)}}

/* ══════════════════════════
   GAME 6 — SPEED CHALLENGE
══════════════════════════ */
.speed-display{text-align:center;padding:24px;background:var(--bg3);border-radius:12px;margin-bottom:18px;border:1px solid var(--border)}
.speed-timer{font-family:var(--mono);font-size:48px;font-weight:600;color:var(--amber);line-height:1}
.speed-timer.low{color:var(--rose)}
.speed-q{font-size:18px;font-weight:600;margin:16px 0 8px;color:var(--text)}
.speed-hint{font-family:var(--mono);font-size:11px;color:var(--muted)}
.speed-opts{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:16px 0}
.speed-opt{padding:14px;border:1.5px solid var(--border2);border-radius:9px;cursor:pointer;font-family:var(--mono);font-size:13px;color:#b8c4dc;background:var(--bg2);transition:all .15s;text-align:center}
.speed-opt:hover:not(:disabled){border-color:var(--blue);color:var(--blue);background:rgba(96,165,250,.08)}
.speed-opt.cor{border-color:var(--teal)!important;background:rgba(45,212,191,.12)!important;color:var(--teal)!important}
.speed-opt.wrg{border-color:var(--rose)!important;background:rgba(248,113,113,.12)!important;color:var(--rose)!important}
.speed-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:16px}
.speed-stat{text-align:center;background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:12px}
.speed-stat-val{font-family:var(--mono);font-size:22px;font-weight:600;color:var(--teal)}
.speed-stat-lbl{font-family:var(--mono);font-size:9px;color:var(--muted);margin-top:2px;text-transform:uppercase}

/* ─── RESULTS ─── */
.result-card{background:var(--bg2);border:1px solid var(--border2);border-radius:14px;padding:32px;text-align:center;margin-top:20px}
.result-score{font-family:var(--mono);font-size:52px;font-weight:600;margin:10px 0}
.result-grade{font-family:var(--mono);font-size:14px;margin-bottom:18px}
.result-breakdown{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:20px 0}
.rb-item{background:var(--bg3);border:1px solid var(--border);border-radius:8px;padding:14px}
.rb-val{font-family:var(--mono);font-size:20px;font-weight:600;color:var(--teal)}
.rb-lbl{font-family:var(--mono);font-size:9px;color:var(--muted);margin-top:3px;text-transform:uppercase}

/* ─── MISC ─── */
code{font-family:var(--mono);font-size:12px;background:rgba(255,255,255,.06);padding:1px 7px;border-radius:3px;color:var(--sky)}
.tag{display:inline-block;font-family:var(--mono);font-size:9px;padding:2px 8px;border-radius:4px;margin-right:4px}
.tag-18{background:rgba(45,212,191,.1);color:var(--teal);border:1px solid rgba(45,212,191,.2)}
.tag-19{background:rgba(96,165,250,.1);color:var(--blue);border:1px solid rgba(96,165,250,.2)}
.tag-20{background:rgba(167,139,250,.1);color:var(--violet);border:1px solid rgba(167,139,250,.2)}
.tag-hard{background:rgba(248,113,113,.1);color:var(--rose);border:1px solid rgba(248,113,113,.2)}
.emoji{font-size:20px}
</style>
</head>
<body>

<!-- TOPBAR -->
<div class="topbar">
  <div class="topbar-logo">ch18–20 // quiz & games</div>
  <div class="topbar-score">XP: <span id="total-xp">0</span> pts</div>
</div>

<!-- HERO -->
<div class="hero">
  <div class="hero-badge">Chapters 18 · 19 · 20</div>
  <h1><span class="g1">Quiz & Games</span><br><span class="g2">Master Mode</span></h1>
  <p class="hero-sub">6 interactive modes to lock in every concept — from flashcards to speed rounds. All topics: Linked Lists, Stacks, Queues, BSTs, AVL Trees.</p>
  <div class="mode-btns">
    <button class="mode-btn m-quiz active" onclick="switchMode('quiz')"><span>📝</span> Full Quiz</button>
    <button class="mode-btn m-flash" onclick="switchMode('flash')"><span>🃏</span> Flashcards</button>
    <button class="mode-btn m-tree" onclick="switchMode('tree')"><span>🌳</span> Build a BST</button>
    <button class="mode-btn m-sort" onclick="switchMode('rot')"><span>🔄</span> Rotation ID</button>
    <button class="mode-btn m-match" onclick="switchMode('match')"><span>🔗</span> Match Pairs</button>
    <button class="mode-btn m-speed" onclick="switchMode('speed')"><span>⚡</span> Speed Round</button>
  </div>
</div>

<!-- ═══════════════════════════════════════
     PANEL 1 — FULL QUIZ
═══════════════════════════════════════ -->
<div class="panel active" id="panel-quiz">
  <div style="display:flex;align-items:center;gap:12px;margin-bottom:20px;flex-wrap:wrap">
    <div class="quiz-chapter-tabs">
      <button class="ctab active" onclick="setChapter('all',this)">All Chapters</button>
      <button class="ctab" onclick="setChapter('18',this)">Ch 18 — Linked/Stack/Queue</button>
      <button class="ctab" onclick="setChapter('19',this)">Ch 19 — BST</button>
      <button class="ctab" onclick="setChapter('20',this)">Ch 20 — AVL</button>
    </div>
    <div class="streak" id="quiz-streak"></div>
  </div>
  <div class="prog-label"><span id="q-num">Question 1 / 30</span><span id="q-score">Score: 0</span></div>
  <div class="prog-bar"><div class="prog-fill" id="q-prog" style="width:0%"></div></div>
  <div class="card" id="quiz-card">
    <div style="display:flex;align-items:center;gap:8px;margin-bottom:16px">
      <span id="q-tag"></span>
      <span id="q-diff"></span>
    </div>
    <div class="q-text" id="q-text"></div>
    <div class="q-opts" id="q-opts"></div>
    <div class="q-explain" id="q-explain"></div>
    <div style="display:flex;gap:10px;margin-top:16px" id="q-next-row" style="display:none">
      <button class="btn btn-t" id="q-next" onclick="nextQuestion()" disabled>Next →</button>
      <button class="btn" onclick="restartQuiz()">Restart</button>
    </div>
  </div>
  <div class="result-card" id="quiz-result" style="display:none">
    <div style="font-size:32px;margin-bottom:8px">🏆</div>
    <div class="result-score" id="res-score"></div>
    <div class="result-grade" id="res-grade"></div>
    <div class="result-breakdown">
      <div class="rb-item"><div class="rb-val" id="res-ch18">–</div><div class="rb-lbl">Ch 18</div></div>
      <div class="rb-item"><div class="rb-val" id="res-ch19">–</div><div class="rb-lbl">Ch 19</div></div>
      <div class="rb-item"><div class="rb-val" id="res-ch20">–</div><div class="rb-lbl">Ch 20</div></div>
    </div>
    <button class="btn btn-t" onclick="restartQuiz()" style="margin-top:8px">Play Again</button>
  </div>
</div>

<!-- ═══════════════════════════════════════
     PANEL 2 — FLASHCARDS
═══════════════════════════════════════ -->
<div class="panel" id="panel-flash">
  <div class="card-title" style="color:var(--blue)"><span>🃏</span> Flashcards — Click card to reveal answer</div>
  <div class="fc-hint">Click the card to flip it · Rate yourself · Navigate with arrows</div>
  <div class="flashcard-wrap" onclick="flipCard()">
    <div class="flashcard" id="fc-card">
      <div class="fc-face fc-front">
        <div class="fc-label" id="fc-front-tag">concept</div>
        <div class="fc-text" id="fc-q"></div>
        <div class="fc-sub" id="fc-hint-text"></div>
      </div>
      <div class="fc-face fc-back">
        <div class="fc-label">answer</div>
        <div class="fc-text" id="fc-a"></div>
      </div>
    </div>
  </div>
  <div class="fc-rating" id="fc-rating" style="display:none">
    <button class="fc-rate-btn fcr-easy" onclick="rateCard('easy')">✓ Got it</button>
    <button class="fc-rate-btn fcr-ok" onclick="rateCard('ok')">~ Almost</button>
    <button class="fc-rate-btn fcr-hard" onclick="rateCard('hard')">✗ Review</button>
  </div>
  <div class="fc-nav" style="margin-top:18px">
    <button class="btn" onclick="prevCard()">← Prev</button>
    <div class="fc-count" id="fc-count">1 / 30</div>
    <button class="btn" onclick="nextCard()">Next →</button>
    <button class="btn btn-v" onclick="shuffleCards()" style="margin-left:10px">Shuffle</button>
  </div>
  <div style="font-family:var(--mono);font-size:11px;color:var(--muted);text-align:center;margin-top:14px">
    Easy: <span id="fc-easy" style="color:var(--teal)">0</span> · 
    Almost: <span id="fc-ok" style="color:var(--amber)">0</span> · 
    Review: <span id="fc-hard" style="color:var(--rose)">0</span>
  </div>
</div>

<!-- ═══════════════════════════════════════
     PANEL 3 — BUILD A BST
═══════════════════════════════════════ -->
<div class="panel" id="panel-tree">
  <div class="card-title" style="color:var(--violet)"><span>🌳</span> Build a BST — Insert numbers in the correct order</div>
  <div class="card">
    <div id="bst-game-challenge" style="font-size:15px;font-weight:600;margin-bottom:14px;color:var(--text)"></div>
    <div class="bst-instruction" id="bst-instr">Select a number from below, then click where to insert it in the tree.</div>
    <svg id="bst-game-svg" viewBox="0 0 680 300" style="min-height:200px"></svg>
    <div style="margin-top:12px">
      <div style="font-family:var(--mono);font-size:10px;color:var(--muted);margin-bottom:8px;text-transform:uppercase;letter-spacing:1px">Numbers to insert (click to select, then click tree):</div>
      <div class="bst-pending" id="bst-pending"></div>
    </div>
    <div class="bst-feedback" id="bst-feedback"></div>
    <div style="display:flex;gap:10px;margin-top:12px">
      <button class="btn btn-v" onclick="newBSTChallenge()">New Challenge</button>
      <button class="btn" onclick="showBSTAnswer()">Show Answer</button>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════
     PANEL 4 — ROTATION IDENTIFIER
═══════════════════════════════════════ -->
<div class="panel" id="panel-rot">
  <div class="card-title" style="color:var(--amber)"><span>🔄</span> Rotation Identifier — Which AVL rotation fixes this?</div>
  <div class="prog-label"><span id="rot-num">Scenario 1 / 12</span><span id="rot-score">Score: 0</span></div>
  <div class="prog-bar"><div class="prog-fill" id="rot-prog" style="width:0%;background:linear-gradient(90deg,var(--amber),var(--rose))"></div></div>
  <div class="rot-scenario card">
    <div id="rot-svg-area" style="margin-bottom:16px;display:flex;justify-content:center"></div>
    <div class="rot-question" id="rot-question"></div>
    <div class="rot-choices">
      <button class="rot-choice" id="rc0" onclick="answerRot(0)"></button>
      <button class="rot-choice" id="rc1" onclick="answerRot(1)"></button>
      <button class="rot-choice" id="rc2" onclick="answerRot(2)"></button>
      <button class="rot-choice" id="rc3" onclick="answerRot(3)"></button>
    </div>
    <div class="q-explain" id="rot-explain" style="margin-top:14px"></div>
    <div style="margin-top:14px;display:flex;gap:10px;justify-content:center">
      <button class="btn btn-a" id="rot-next" onclick="nextRot()" disabled>Next →</button>
      <button class="btn" onclick="restartRot()">Restart</button>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════
     PANEL 5 — MATCH PAIRS
═══════════════════════════════════════ -->
<div class="panel" id="panel-match">
  <div class="card-title" style="color:var(--pink)"><span>🔗</span> Match Pairs — Connect concept to definition</div>
  <div id="match-score-row" style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px">
    <div style="font-family:var(--mono);font-size:11px;color:var(--muted)">Matches: <span id="match-count" style="color:var(--teal)">0</span> / <span id="match-total">0</span></div>
    <button class="btn btn-v" onclick="newMatchGame()">New Set</button>
  </div>
  <div id="match-grid-wrap"></div>
  <div id="match-feedback" style="font-family:var(--mono);font-size:12px;min-height:32px;text-align:center;margin-top:10px"></div>
</div>

<!-- ═══════════════════════════════════════
     PANEL 6 — SPEED ROUND
═══════════════════════════════════════ -->
<div class="panel" id="panel-speed">
  <div class="card-title" style="color:var(--rose)"><span>⚡</span> Speed Round — Answer 10 questions before time runs out!</div>
  <div class="speed-stats">
    <div class="speed-stat"><div class="speed-stat-val" id="sp-score">0</div><div class="speed-stat-lbl">Score</div></div>
    <div class="speed-stat"><div class="speed-stat-val" id="sp-combo">0</div><div class="speed-stat-lbl">Combo ×</div></div>
    <div class="speed-stat"><div class="speed-stat-val" id="sp-best">0</div><div class="speed-stat-lbl">Best Score</div></div>
  </div>
  <div class="speed-display">
    <div class="speed-timer" id="sp-timer">10</div>
    <div class="speed-q" id="sp-question">Press Start to play!</div>
    <div class="speed-hint" id="sp-hint"></div>
  </div>
  <div class="speed-opts" id="sp-opts"></div>
  <div style="display:flex;gap:10px;justify-content:center;margin-top:10px">
    <button class="btn btn-r" id="sp-start" onclick="startSpeed()">▶ Start</button>
    <button class="btn" onclick="stopSpeed()">■ Stop</button>
  </div>
  <div id="sp-result" style="display:none;text-align:center;margin-top:20px">
    <div style="font-size:28px;margin-bottom:8px" id="sp-res-emoji"></div>
    <div style="font-family:var(--mono);font-size:22px;font-weight:600;color:var(--amber)" id="sp-res-score"></div>
    <div style="font-family:var(--mono);font-size:12px;color:var(--muted);margin-top:6px" id="sp-res-msg"></div>
  </div>
</div>

<script>
// ═══════════════════════════════════════════════
// QUESTION BANK — 42 questions, 3 chapters
// ═══════════════════════════════════════════════
const QB = [
  // ─── CHAPTER 18 ───
  {ch:'18',diff:'easy',q:'What is the time complexity of <code>addFirst(e)</code> in a singly linked list?',opts:['O(n)','O(log n)','O(1)','O(n²)'],ans:2,tag:'Linked List',exp:'<code>addFirst</code> creates a new node, points it to the old head, and updates head. No traversal needed — always O(1).'},
  {ch:'18',diff:'easy',q:'A <strong>Stack</strong> follows which principle?',opts:['FIFO — First In, First Out','LIFO — Last In, First Out','Random access','Priority-based'],ans:1,tag:'Stack',exp:'Stack = LIFO. The last item pushed is the first item popped. Think of a stack of plates.'},
  {ch:'18',diff:'easy',q:'A <strong>Queue</strong> follows which principle?',opts:['LIFO','Random access','FIFO — First In, First Out','Priority-based'],ans:2,tag:'Queue',exp:'Queue = FIFO. The first item enqueued is the first item dequeued. Think of a checkout line.'},
  {ch:'18',diff:'medium',q:'Why is <code>removeLast()</code> O(n) in a <strong>singly</strong> linked list, while <code>removeFirst()</code> is O(1)?',opts:['The last node is encrypted','You must traverse from head to find the second-to-last node','Python\'s garbage collector is slow','Size must be recounted'],ans:1,tag:'Linked List',exp:'To remove the tail, you need to update the tail pointer to the second-to-last node. But you can\'t go backwards in a singly linked list — you must walk from head. A doubly linked list solves this in O(1).'},
  {ch:'18',diff:'medium',q:'Why is a <strong>LinkedList</strong> used to implement a Queue instead of Python\'s built-in list?',opts:['LinkedList uses less memory','LinkedList supports index access','removeFirst() is O(1) in LinkedList but O(n) in Python list','LinkedList is a built-in Python class'],ans:2,tag:'Queue',exp:'Dequeue removes from the head (index 0). Python list shifts all elements left on index-0 removal → O(n). LinkedList just moves the head pointer → O(1).'},
  {ch:'18',diff:'medium',q:'What does the <code>yield</code> keyword do in a Python generator?',opts:['Returns a value and terminates the function','Raises StopIteration immediately','Pauses execution, returns value, resumes from same point next call','Converts the function to a class'],ans:2,tag:'Generators',exp:'yield is like a pause button. All local variables are frozen until __next__ is called again. The function resumes right after the yield statement.'},
  {ch:'18',diff:'medium',q:'Which data structure does a <strong>Priority Queue</strong> use internally?',opts:['Linked List','Stack','Heap (max-heap)','Hash Table'],ans:2,tag:'Priority Queue',exp:'A priority queue is backed by a max-heap. The root always holds the highest-priority element. Every enqueue inserts into the heap; every dequeue removes the root.'},
  {ch:'18',diff:'hard',q:'In the <strong>two-stack expression evaluator</strong>, when you encounter a closing parenthesis ")", what do you do?',opts:['Push ")" onto operatorStack','Push ")" onto operandStack','Process operators from operatorStack until you find the matching "("','Immediately evaluate the entire expression'],ans:2,tag:'Expression Eval',exp:'")" triggers processing of everything inside that pair of parentheses. Pop and apply operators until you hit "(", then discard the "(".'},
  {ch:'18',diff:'easy',q:'Which linked list variation allows O(1) <code>removeLast()</code>?',opts:['Singly linked list','Circular singly linked list','Doubly linked list','Priority list'],ans:2,tag:'Linked List',exp:'A doubly linked list has a <code>previous</code> pointer in every node. To remove the tail, just follow <code>tail.previous</code> — no traversal. O(1).'},
  {ch:'18',diff:'medium',q:'What two methods must an <strong>iterator class</strong> implement in Python?',opts:['__get__ and __set__','__iter__ and __next__','__start__ and __stop__','__yield__ and __return__'],ans:1,tag:'Iterators',exp:'__iter__ returns the iterator object itself. __next__ returns the next element and raises StopIteration when done. These enable for-loop support.'},
  {ch:'18',diff:'easy',q:'A Python <strong>Stack</strong> is most efficiently implemented using:',opts:['A LinkedList','A Python list (append/pop from end)','A dictionary','A tuple'],ans:1,tag:'Stack',exp:'Python list\'s append() and pop() both operate on the end — O(1) each. The end of the list acts as the top of the stack.'},
  {ch:'18',diff:'hard',q:'What is the difference between an <strong>iterable</strong> and an <strong>iterator</strong>?',opts:['They are the same thing','Iterable has __iter__; iterator has __iter__ AND __next__','Iterator has __iter__; iterable has __next__','Iterators are faster than iterables'],ans:1,tag:'Iterators',exp:'An iterable (e.g., list) only needs __iter__ returning an iterator. An iterator has both __iter__ (returning itself) and __next__ (returning next value). Iterators are consumed; iterables can create fresh iterators.'},

  // ─── CHAPTER 19 ───
  {ch:'19',diff:'easy',q:'In a Binary Search Tree, all values in the <strong>left subtree</strong> of any node are:',opts:['Greater than the node\'s value','Equal to the node\'s value','Less than the node\'s value','Any value'],ans:2,tag:'BST Property',exp:'BST property: left subtree values < node < right subtree values. This holds for EVERY node in the tree, not just the root.'},
  {ch:'19',diff:'easy',q:'Which traversal visits nodes in <strong>sorted ascending order</strong> in a BST?',opts:['Preorder (Root→Left→Right)','Postorder (Left→Right→Root)','Inorder (Left→Root→Right)','Breadth-first'],ans:2,tag:'Traversal',exp:'Inorder (Left→Root→Right) follows the BST property: everything left is smaller, then root, then right is larger. This produces sorted output.'},
  {ch:'19',diff:'easy',q:'Where is a new element <strong>always inserted</strong> in a BST?',opts:['At the root','As a leaf node','In the middle of the tree','After the first larger element'],ans:1,tag:'BST Insert',exp:'New elements are always leaf nodes. The algorithm walks down to find the parent, then attaches the new node as left or right child of that parent.'},
  {ch:'19',diff:'medium',q:'What is the <strong>worst-case</strong> time complexity for searching in a BST?',opts:['O(1)','O(log n)','O(n)','O(n log n)'],ans:2,tag:'Complexity',exp:'Worst case is O(n) — when elements are inserted in sorted order, the tree degenerates into a linked list (straight chain). Height = n. AVL trees guarantee O(log n).'},
  {ch:'19',diff:'medium',q:'To <strong>delete a node</strong> that HAS a left child (Case 2), you:',opts:['Simply connect parent to node\'s right child','Rebuild the entire subtree','Find rightMost in left subtree, copy its value up, delete rightMost','Swap with root and delete'],ans:2,tag:'BST Delete',exp:'Case 2: find the rightMost node (largest value in left subtree). Copy rightMost\'s value into the current node. Then delete rightMost (which has no right child — Case 1 deletion).'},
  {ch:'19',diff:'medium',q:'Breadth-first traversal of a BST is implemented using which data structure?',opts:['A stack','A priority queue','A queue','A linked list'],ans:2,tag:'Traversal',exp:'Breadth-first (level-order) uses a queue. Enqueue root, then repeatedly dequeue a node, process it, and enqueue its children. FIFO order ensures level-by-level processing.'},
  {ch:'19',diff:'hard',q:'In <strong>Huffman coding</strong>, the prefix-free property means:',opts:['All codes have the same length','No code is a prefix of another — all characters are at leaf nodes','The most frequent character gets code "0"','The tree is always perfectly balanced'],ans:1,tag:'Huffman',exp:'Characters are placed at leaf nodes. Since no leaf is an ancestor of another leaf, no character\'s code can be a prefix of another\'s. This guarantees unambiguous decoding.'},
  {ch:'19',diff:'medium',q:'What is the <strong>Factory Method Pattern</strong> as used in BST?',opts:['A method that creates all nodes in the tree at once','createNewNode() is defined in BST but overridden in subclasses to return different node types','A method that builds the tree from a list','A factory function that checks BST validity'],ans:1,tag:'Design Pattern',exp:'BST.createNewNode() returns TreeNode. AVLTree overrides it to return AVLTreeNode (with height field). When BST.insert() calls self.createNewNode(), it automatically gets the right node type via polymorphism.'},
  {ch:'19',diff:'easy',q:'Postorder traversal visits nodes in which order?',opts:['Root → Left → Right','Left → Root → Right','Left → Right → Root','Right → Root → Left'],ans:2,tag:'Traversal',exp:'Postorder: Left → Right → Root. The root is always visited last. Used for: deleting a tree (delete children before parent), evaluating expression trees.'},
  {ch:'19',diff:'hard',q:'In the <strong>MVC pattern</strong> for the BST visualiser, what is the View\'s role?',opts:['Stores the tree data and handles BST operations','Handles button clicks and user input','Renders the tree graphically on screen','Converts tree nodes to bit sequences'],ans:2,tag:'MVC Pattern',exp:'MVC: Model = data + logic (BST class). View = visual display (BTView — renders nodes as circles). Controller = user interaction handler. Separating these makes code reusable and testable.'},
  {ch:'19',diff:'medium',q:'Huffman coding is an example of which algorithm design technique?',opts:['Dynamic programming','Divide and conquer','Backtracking','Greedy algorithm'],ans:3,tag:'Huffman',exp:'Huffman uses a greedy algorithm — always combining the two lowest-weight trees. Each local choice (smallest available) leads to a globally optimal result (minimum total bits).'},
  {ch:'19',diff:'hard',q:'What is the <strong>path(e)</strong> method in the BST class?',opts:['The sequence of values visited during inorder traversal','The list of nodes from root down to the node containing e','The shortest path between any two nodes','The height of the subtree rooted at node e'],ans:1,tag:'BST Class',exp:'path(e) returns a list of nodes from the root down to the node containing e. Even if e is not in the tree, it returns the path you would have taken. Used by AVLTree\'s balancePath().'},

  // ─── CHAPTER 20 ───
  {ch:'20',diff:'easy',q:'What is the <strong>balance factor</strong> of a node?',opts:['height(left) − height(right)','height(right) − height(left)','height(left) + height(right)','max(height(left), height(right))'],ans:1,tag:'Balance Factor',exp:'BF = height(right) − height(left). Positive = right-heavy. Negative = left-heavy. Valid AVL range: {−1, 0, +1}.'},
  {ch:'20',diff:'easy',q:'A node A has BF = −2 and left child B has BF = −1. Which rotation?',opts:['RR (single left at A)','LR (left at B, right at A)','LL (single right at A)','RL (right at B, left at A)'],ans:2,tag:'Rotations',exp:'BF(A)=−2 (left-heavy) and BF(B)=−1 → LL rotation (single right rotation at A). The name LL = new node went Left-Left.'},
  {ch:'20',diff:'easy',q:'A node A has BF = +2 and right child B has BF = +1. Which rotation?',opts:['LL (single right at A)','LR (left at B, right at A)','RL (right at B, left at A)','RR (single left at A)'],ans:3,tag:'Rotations',exp:'BF(A)=+2 (right-heavy) and BF(B)=+1 → RR rotation (single left rotation at A). The mirror image of LL.'},
  {ch:'20',diff:'medium',q:'A node A has BF = −2 and left child B has BF = <strong>+1</strong>. Which rotation?',opts:['LL rotation','RR rotation','LR rotation (left at B, then right at A)','RL rotation'],ans:2,tag:'Rotations',exp:'BF(A)=−2 and BF(B)=+1 → LR (double rotation). Left-heavy A but B leans right — a zig-zag. Fix: left-rotate B to straighten it, then right-rotate A.'},
  {ch:'20',diff:'medium',q:'A node A has BF = +2 and right child B has BF = <strong>−1</strong>. Which rotation?',opts:['LL rotation','RR rotation','LR rotation','RL rotation (right at B, then left at A)'],ans:3,tag:'Rotations',exp:'BF(A)=+2 and BF(B)=−1 → RL (double rotation). Right-heavy A but B leans left. Fix: right-rotate B, then left-rotate A. The mirror of LR.'},
  {ch:'20',diff:'medium',q:'In an LL rotation at node A, B\'s old right child (T2) becomes:',opts:['B\'s left child','A\'s right child','A\'s left child','The new root'],ans:2,tag:'LL Rotation',exp:'In LL rotation: A.left = B.right (T2). T2 moves from under B to under A on the left side. This preserves BST ordering because T2 values are between B and A.'},
  {ch:'20',diff:'hard',q:'Why must node A\'s height be updated <strong>before</strong> node B\'s height in a rotation?',opts:['For performance reasons','A is now a child of B — B\'s height calculation needs A\'s correct height','Python requires bottom-up evaluation','B\'s height never changes in a rotation'],ans:1,tag:'Height Update',exp:'After rotation, A is a child of B. B.height = 1 + max(A.height, ...). If you update B first, it reads A\'s stale old height. Always update lower nodes before higher ones.'},
  {ch:'20',diff:'medium',q:'AVLTree extends BST and overrides <code>createNewNode()</code>. This is an example of:',opts:['Observer Pattern','Singleton Pattern','Factory Method Pattern','Strategy Pattern'],ans:2,tag:'Design Pattern',exp:'Factory Method Pattern: BST defines createNewNode() but lets subclasses (AVLTree) decide what type of node to create. AVLTree creates AVLTreeNode (with height field) instead of plain TreeNode.'},
  {ch:'20',diff:'hard',q:'How many rotations does a single <strong>insertion</strong> into an AVL tree require at most?',opts:['O(log n) rotations','O(n) rotations','Exactly 2 rotations','At most 1 (single or double rotation)'],ans:3,tag:'AVL Insert',exp:'Insertion requires at most 1 rotation. Once the first imbalanced node on the path is fixed, all ancestors automatically become balanced. Deletion, however, may need O(log n) rotations.'},
  {ch:'20',diff:'hard',q:'The minimum nodes in an AVL tree of height h follows G(h) = G(h-1) + G(h-2) + 1. This is related to:',opts:['Pascal\'s triangle','Powers of 2','Fibonacci numbers','Prime numbers'],ans:2,tag:'Height Proof',exp:'Fibonacci: F(i)=F(i-1)+F(i-2). G(h) follows the same pattern. Since Fibonacci grows as φ^h, G(h) grows exponentially, meaning height grows as log(n). This proves AVL height = O(log n).'},
  {ch:'20',diff:'hard',q:'What is the <strong>maximum height</strong> of an AVL tree with n nodes?',opts:['n−1','n/2','O(n log n)','≈ 1.44 × log₂(n)'],ans:3,tag:'Height Proof',exp:'Proved via Fibonacci connection: height ≤ 1.44 × log₂(n). With 1 million nodes, max height ≈ 29. With a degenerate BST, height could be 999,999.'},
  {ch:'20',diff:'medium',q:'What extra data field does <code>AVLTreeNode</code> have compared to <code>TreeNode</code>?',opts:['parent — pointer to parent node','color — red or black','height — the height of this node','weight — subtree size'],ans:2,tag:'AVL Class',exp:'AVLTreeNode inherits element, left, right from TreeNode and adds a height field. This field is needed to quickly compute balance factors without traversing the subtree each time.'},
];

// ═══════════════════════════════════════════════
// GLOBAL STATE
// ═══════════════════════════════════════════════
let totalXP = 0;
function addXP(n){ totalXP+=n; document.getElementById('total-xp').textContent=totalXP; }

function switchMode(mode){
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.mode-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('panel-'+mode).classList.add('active');
  document.querySelector(`.m-${mode}`).classList.add('active');
  if(mode==='flash') initFlash();
  if(mode==='tree') newBSTChallenge();
  if(mode==='rot') initRot();
  if(mode==='match') newMatchGame();
  if(mode==='speed') initSpeed();
}

// ═══════════════════════════════════════════════
// GAME 1 — FULL QUIZ
// ═══════════════════════════════════════════════
let quizQs=[], quizIdx=0, quizScore=0, quizStreak=0;
let ch18right=0,ch18total=0,ch19right=0,ch19total=0,ch20right=0,ch20total=0;
let currentChFilter='all';

function setChapter(ch,btn){
  currentChFilter=ch;
  document.querySelectorAll('.ctab').forEach(t=>t.classList.remove('active'));
  btn.classList.add('active');
  restartQuiz();
}

function restartQuiz(){
  document.getElementById('quiz-card').style.display='';
  document.getElementById('quiz-result').style.display='none';
  quizScore=0; quizStreak=0; ch18right=ch18total=ch19right=ch19total=ch20right=ch20total=0;
  quizQs = shuffle(QB.filter(q=>currentChFilter==='all'||q.ch===currentChFilter)).slice(0,Math.min(30,QB.filter(q=>currentChFilter==='all'||q.ch===currentChFilter).length));
  quizIdx=0;
  renderQuestion();
}

function renderQuestion(){
  const total=quizQs.length;
  if(quizIdx>=total){ showQuizResult(); return; }
  const q=quizQs[quizIdx];
  document.getElementById('q-num').textContent=`Question ${quizIdx+1} / ${total}`;
  document.getElementById('q-score').textContent=`Score: ${quizScore}`;
  document.getElementById('q-prog').style.width=`${(quizIdx/total)*100}%`;
  document.getElementById('q-tag').innerHTML=`<span class="tag tag-${q.ch}">Ch ${q.ch}</span>`;
  document.getElementById('q-diff').innerHTML=`<span class="tag ${q.diff==='hard'?'tag-hard':''}" style="${q.diff!=='hard'?'background:rgba(255,255,255,.05);color:var(--muted);border:1px solid var(--border)':''}">★ ${q.diff}</span>`;
  document.getElementById('q-text').innerHTML=q.q;
  document.getElementById('q-explain').className='q-explain';
  document.getElementById('q-explain').style.display='none';
  document.getElementById('q-next').disabled=true;
  const streak=quizStreak>1?`<span class="streak">🔥 ${quizStreak} streak</span>`:'';
  document.getElementById('quiz-streak').innerHTML=streak;
  const optsEl=document.getElementById('q-opts');
  optsEl.innerHTML='';
  q.opts.forEach((o,i)=>{
    const btn=document.createElement('button');
    btn.className='q-opt'; btn.innerHTML=o;
    btn.onclick=()=>answerQuiz(i,q,btn);
    optsEl.appendChild(btn);
  });
  document.getElementById('q-next-row').style.display='flex';
}

function answerQuiz(i,q,btn){
  document.querySelectorAll('.q-opt').forEach(b=>{b.disabled=true;b.onclick=null;});
  const correct=i===q.ans;
  btn.classList.add(correct?'cor':'wrg');
  if(!correct) document.querySelectorAll('.q-opt')[q.ans].classList.add('cor');
  const exp=document.getElementById('q-explain');
  exp.innerHTML=q.exp; exp.style.display='block';
  exp.className=`q-explain show ${correct?'cor-explain':'wrg-explain'}`;
  if(correct){
    quizScore+=10*(quizStreak>2?2:1); quizStreak++;
    if(q.ch==='18'){ch18right++;} if(q.ch==='19'){ch19right++;} if(q.ch==='20'){ch20right++;}
    addXP(10);
  } else { quizStreak=0; }
  if(q.ch==='18')ch18total++; if(q.ch==='19')ch19total++; if(q.ch==='20')ch20total++;
  document.getElementById('q-score').textContent=`Score: ${quizScore}`;
  document.getElementById('q-next').disabled=false;
  if(quizStreak>1) document.getElementById('quiz-streak').innerHTML=`<span class="streak">🔥 ${quizStreak} streak</span>`;
}

function nextQuestion(){ quizIdx++; renderQuestion(); }

function showQuizResult(){
  document.getElementById('quiz-card').style.display='none';
  const res=document.getElementById('quiz-result');
  res.style.display='block';
  const total=quizQs.length;
  const pct=Math.round((quizScore/(total*10))*100);
  document.getElementById('res-score').textContent=`${quizScore} / ${total*10}`;
  const grades=[['A+ 🏆',90],['A 🎉',80],['B 👍',65],['C 📖',50],['D 💪',0]];
  const grade=grades.find(g=>pct>=g[1]);
  document.getElementById('res-grade').textContent=`${grade[0]} — ${pct}%`;
  document.getElementById('res-grade').style.color=pct>=80?'var(--teal)':pct>=65?'var(--amber)':'var(--rose)';
  document.getElementById('res-ch18').textContent=ch18total?`${ch18right}/${ch18total}`:'–';
  document.getElementById('res-ch19').textContent=ch19total?`${ch19right}/${ch19total}`:'–';
  document.getElementById('res-ch20').textContent=ch20total?`${ch20right}/${ch20total}`:'–';
  addXP(50);
}

restartQuiz();

// ═══════════════════════════════════════════════
// GAME 2 — FLASHCARDS
// ═══════════════════════════════════════════════
const FLASHCARDS=[
  {ch:'18',q:'What is the time complexity of addFirst() in a singly linked list?',a:'O(1) — just update head pointer. No traversal needed.',hint:'Think: how many nodes do you visit?'},
  {ch:'18',q:'What makes a generator function different from a regular function?',a:'Uses yield instead of return. Execution pauses at yield and resumes on next call. Local state is preserved.',hint:'yield vs return'},
  {ch:'18',q:'What 3 things does a LinkedList track internally?',a:'head (first node), tail (last node), size (count of nodes)',hint:'Think about what you need for O(1) access'},
  {ch:'18',q:'LIFO vs FIFO — which is Stack, which is Queue?',a:'Stack = LIFO (Last In, First Out). Queue = FIFO (First In, First Out).',hint:'Plates vs waiting line'},
  {ch:'18',q:'Why use a LinkedList to back a Queue (not a Python list)?',a:'removeFirst() = O(1) in LinkedList. Python list index-0 removal = O(n) because all elements shift.',hint:'Where does dequeue happen?'},
  {ch:'18',q:'What two methods does the iterator protocol require?',a:'__iter__(self) → returns iterator object. __next__(self) → returns next element or raises StopIteration.',hint:'What does for-loop secretly call?'},
  {ch:'18',q:'What is a circular linked list?',a:'The last node\'s next pointer points back to head. No tail needed. Used in OS round-robin scheduling.',hint:'What happens at the end?'},
  {ch:'18',q:'What does a Priority Queue always dequeue?',a:'The element with the highest priority value — regardless of insertion order. Backed by a max-heap.',hint:'Not FIFO, not LIFO...'},
  {ch:'18',q:'In the expression evaluator, what two stacks are used?',a:'operandStack (holds numbers) and operatorStack (holds +−×÷ and parentheses)',hint:'One for numbers, one for...'},
  {ch:'18',q:'What is the difference between a singly and doubly linked list?',a:'Singly: each node has only next pointer. Doubly: each node has next AND previous pointer. Doubly allows O(1) removeLast.',hint:'Count the pointers per node'},
  {ch:'19',q:'State the BST property in one sentence.',a:'For every node: all values in the left subtree are strictly less than the node\'s value, and all values in the right subtree are strictly greater.',hint:'Left < ? < Right'},
  {ch:'19',q:'Which traversal produces sorted output from a BST?',a:'Inorder (Left → Root → Right). BST ordering ensures left < root < right at every level.',hint:'What order visits left first?'},
  {ch:'19',q:'What is the height of a single-node tree (a leaf)?',a:'Height = 0. An empty tree (null) has height = −1. Height = max depth of any leaf.',hint:'Count edges from root to leaf'},
  {ch:'19',q:'BST deletion Case 2: what is the rightMost node?',a:'The node with the largest value in the current node\'s LEFT subtree. Found by going left once, then all the way right.',hint:'Biggest in the left side'},
  {ch:'19',q:'What data structures does breadth-first traversal use?',a:'A queue. Enqueue root, then repeatedly: dequeue node, process it, enqueue its children.',hint:'FIFO visits level by level'},
  {ch:'19',q:'How does Huffman coding achieve compression?',a:'Assigns shorter bit codes to more frequent characters. Built by repeatedly merging the two lowest-frequency trees.',hint:'Frequency → code length'},
  {ch:'19',q:'What is the Factory Method pattern in BST?',a:'createNewNode(e) is defined in BST to return TreeNode. Subclasses (AVLTree) override it to return a different node type (AVLTreeNode).',hint:'Let subclass decide the type'},
  {ch:'19',q:'What is the worst-case search time for a BST?',a:'O(n) — when inserted in sorted order, the tree becomes a straight chain (linked list). Height = n.',hint:'What does sorted insertion produce?'},
  {ch:'19',q:'What does path(e) return in the BST class?',a:'A list of nodes from the root down to the node containing e (or where e would be if not found).',hint:'The route from root to target'},
  {ch:'20',q:'What is the balance factor formula?',a:'BF = height(right subtree) − height(left subtree). Empty subtree = −1. Valid range: {−1, 0, +1}.',hint:'Right minus Left'},
  {ch:'20',q:'When does LL rotation happen? What does it do?',a:'BF(A)=−2 and BF(left child B)=−1 or 0. Single right rotation at A. B becomes new root, A drops to B\'s right.',hint:'Too left-heavy, lean right'},
  {ch:'20',q:'When does LR rotation happen? What makes it different from LL?',a:'BF(A)=−2 and BF(B)=+1. Double rotation: left at B first, then right at A. Needed because of zig-zag shape.',hint:'Zig-zag needs two fixes'},
  {ch:'20',q:'In a rotation, which node\'s height must be updated FIRST — A or B?',a:'A (the lower node) must be updated first. B\'s height depends on A\'s height. Stale height = wrong result.',hint:'Bottom up always'},
  {ch:'20',q:'What extra field does AVLTreeNode have vs TreeNode?',a:'height — stores the height of the subtree rooted at this node. Leaf = 0. Needed for O(1) balance factor computation.',hint:'What AVL needs that BST doesn\'t'},
  {ch:'20',q:'How many rotations does one INSERT require in an AVL tree?',a:'At most 1 (single or double). Once the first imbalanced node is fixed, all ancestors automatically re-balance.',hint:'Insertion vs deletion differ here'},
  {ch:'20',q:'What is the maximum height of an AVL tree with n nodes?',a:'≈ 1.44 × log₂(n). For 1 million nodes: max height ≈ 29. Proved via Fibonacci recurrence G(h) = G(h-1)+G(h-2)+1.',hint:'Log-based, but slightly more than log₂'},
  {ch:'20',q:'What does balancePath(e) do?',a:'Gets path from node e to root. Iterates bottom-up. For each node: update height, compute BF, apply rotation if BF = ±2.',hint:'The engine that keeps AVL balanced'},
  {ch:'20',q:'Why does AVLTree override insert() instead of just using BST\'s insert()?',a:'To call balancePath(e) after BST insertion. The balance check and rotation step are not in BST. AVL wraps BST insert with rebalancing.',hint:'What step is added?'},
  {ch:'20',q:'State the G(h) recurrence and what it proves.',a:'G(0)=1, G(1)=2, G(h)=G(h-1)+G(h-2)+1. Like Fibonacci. Proves minimum nodes grows exponentially with h, so h = O(log n).',hint:'Minimum nodes → maximum height'},
  {ch:'20',q:'RL rotation: what is C and where does it end up?',a:'C = right child B\'s LEFT child. After RL: C becomes new local root. A is C\'s left child. B is C\'s right child.',hint:'The grandchild rises to the top'},
];

let fcIdx=0, fcCards=[], fcEasy=0,fcOk=0,fcHard=0;
function initFlash(){
  fcCards=shuffle([...FLASHCARDS]);
  fcIdx=0; fcEasy=0;fcOk=0;fcHard=0;
  renderFlash();
}
function renderFlash(){
  const card=fcCards[fcIdx];
  document.getElementById('fc-q').innerHTML=card.q;
  document.getElementById('fc-a').innerHTML=card.a;
  document.getElementById('fc-hint-text').textContent=card.hint?'💡 '+card.hint:'';
  document.getElementById('fc-front-tag').innerHTML=`<span class="tag tag-${card.ch}">Ch ${card.ch}</span> ${card.ch==='18'?'Linked/Stack/Queue':card.ch==='19'?'BST':'AVL Tree'}`;
  document.getElementById('fc-count').textContent=`${fcIdx+1} / ${fcCards.length}`;
  const fc=document.getElementById('fc-card');
  fc.classList.remove('flipped');
  document.getElementById('fc-rating').style.display='none';
  updateFCstats();
}
function flipCard(){
  document.getElementById('fc-card').classList.toggle('flipped');
  setTimeout(()=>{ document.getElementById('fc-rating').style.display='flex'; },300);
}
function rateCard(r){
  if(r==='easy')fcEasy++;
  else if(r==='ok')fcOk++;
  else fcHard++;
  addXP(r==='easy'?5:r==='ok'?3:1);
  nextCard();
}
function nextCard(){ fcIdx=(fcIdx+1)%fcCards.length; renderFlash(); }
function prevCard(){ fcIdx=(fcIdx-1+fcCards.length)%fcCards.length; renderFlash(); }
function shuffleCards(){ fcCards=shuffle(fcCards); fcIdx=0; renderFlash(); }
function updateFCstats(){
  document.getElementById('fc-easy').textContent=fcEasy;
  document.getElementById('fc-ok').textContent=fcOk;
  document.getElementById('fc-hard').textContent=fcHard;
}

// ═══════════════════════════════════════════════
// GAME 3 — BUILD A BST
// ═══════════════════════════════════════════════
const BST_CHALLENGES=[
  {nums:[40,20,60,10,30,50,70],desc:'Insert 7 numbers and build the correct BST'},
  {nums:[50,25,75,12,37,62,87],desc:'Build a balanced BST from these 7 values'},
  {nums:[45,20,80,10,35,60,90,5,15],desc:'Build a 9-node BST — watch the structure!'},
  {nums:[30,15,60,10,20,45,75],desc:'Classic BST structure challenge'},
  {nums:[55,30,80,20,40,70,90,25,35],desc:'Build this 9-node BST correctly'},
];

class SimpleBST {
  constructor(){this.root=null;}
  insert(v){this.root=this._ins(this.root,v);}
  _ins(n,v){
    if(!n){return {v,left:null,right:null};}
    if(v<n.v)n.left=this._ins(n.left,v);
    else if(v>n.v)n.right=this._ins(n.right,v);
    return n;
  }
  contains(v){let c=this.root;while(c){if(v===c.v)return true;c=v<c.v?c.left:c.right;}return false;}
}

let bstChallenge=null, bstBuilt=null, bstRemaining=[], bstSelected=null, bstCorrectOrder=[];

function newBSTChallenge(){
  const ch=BST_CHALLENGES[Math.floor(Math.random()*BST_CHALLENGES.length)];
  bstChallenge=ch;
  bstBuilt=new SimpleBST();
  bstRemaining=[...ch.nums];
  bstSelected=null;
  document.getElementById('bst-game-challenge').textContent=ch.desc;
  document.getElementById('bst-feedback').textContent='';
  document.getElementById('bst-feedback').style.background='';
  renderBSTGame();
}

function renderBSTGame(){
  renderBSTTree();
  const pend=document.getElementById('bst-pending');
  pend.innerHTML='';
  bstRemaining.forEach(n=>{
    const div=document.createElement('div');
    div.className='pend-item'+(n===bstSelected?' sel':'');
    div.textContent=n;
    div.onclick=()=>{bstSelected=n; renderBSTGame();};
    pend.appendChild(div);
  });
  document.getElementById('bst-instr').textContent=bstSelected?`Selected: ${bstSelected} — now click the tree to insert it!`:'Select a number below, then click the tree to insert it.';
}

function renderBSTTree(){
  const svg=document.getElementById('bst-game-svg');
  const pos={};
  const assign=(n,x,y,sp)=>{if(!n)return;pos[n.v]={x,y};assign(n.left,x-sp,y+65,sp/2);assign(n.right,x+sp,y+65,sp/2);};
  assign(bstBuilt.root,340,44,130);
  let html='';
  const edges=(n)=>{
    if(!n)return;
    if(n.left&&pos[n.v]&&pos[n.left.v])html+=`<line x1="${pos[n.v].x}" y1="${pos[n.v].y}" x2="${pos[n.left.v].x}" y2="${pos[n.left.v].y}" stroke="#2a3347" stroke-width="1.5"/>`;
    if(n.right&&pos[n.v]&&pos[n.right.v])html+=`<line x1="${pos[n.v].x}" y1="${pos[n.v].y}" x2="${pos[n.right.v].x}" y2="${pos[n.right.v].y}" stroke="#2a3347" stroke-width="1.5"/>`;
    edges(n.left);edges(n.right);
  };
  edges(bstBuilt.root);
  Object.entries(pos).forEach(([v,{x,y}])=>{
    html+=`<circle cx="${x}" cy="${y}" r="22" fill="rgba(45,212,191,.1)" stroke="var(--teal)" stroke-width="1.5"/>`;
    html+=`<text x="${x}" y="${y+5}" text-anchor="middle" style="font-family:var(--mono);font-size:13px;fill:var(--text)">${v}</text>`;
  });
  // click target
  if(bstSelected!==null){
    svg.onclick=(e)=>{
      const rect=svg.getBoundingClientRect();
      insertBSTValue(bstSelected);
    };
  } else { svg.onclick=null; }
  if(!bstBuilt.root){
    html+='<text x="340" y="150" text-anchor="middle" style="font-family:var(--mono);font-size:13px;fill:var(--muted)">Click a number below, then click here to insert</text>';
  }
  svg.innerHTML=html;
}

function insertBSTValue(v){
  bstBuilt.insert(v);
  bstRemaining=bstRemaining.filter(n=>n!==v);
  bstSelected=null;
  addXP(5);
  const fb=document.getElementById('bst-feedback');
  if(bstRemaining.length===0){
    fb.textContent=`✓ Complete! All ${bstChallenge.nums.length} nodes inserted. BST property holds at every node.`;
    fb.style.background='rgba(45,212,191,.08)'; fb.style.color='var(--teal)'; fb.style.border='1px solid rgba(45,212,191,.2)'; fb.style.borderRadius='8px';
    addXP(30);
  } else {
    fb.textContent=`Inserted ${v}. ${bstRemaining.length} remaining.`;
    fb.style.background=''; fb.style.color='var(--muted)'; fb.style.border='';
  }
  renderBSTGame();
}

function showBSTAnswer(){
  const t=new SimpleBST();
  bstChallenge.nums.forEach(n=>t.insert(n));
  bstBuilt=t; bstRemaining=[];
  const fb=document.getElementById('bst-feedback');
  fb.textContent='Answer shown — the correct BST structure above. Insertion order: '+bstChallenge.nums.join(' → ');
  fb.style.background='rgba(251,191,36,.07)'; fb.style.color='var(--amber)'; fb.style.border='1px solid rgba(251,191,36,.2)'; fb.style.borderRadius='8px';
  renderBSTGame();
}

// ═══════════════════════════════════════════════
// GAME 4 — ROTATION IDENTIFIER
// ═══════════════════════════════════════════════
const ROT_SCENARIOS=[
  {bf_a:-2,bf_b:-1,ans:0,choices:['LL (single right at A)','RR (single left at A)','LR (double: left at B, right at A)','RL (double: right at B, left at A)'],exp:'BF(A)=−2 (left-heavy) + BF(B)=−1 (also left-heavy) → LL rotation. Single right rotation at A. B becomes new root.'},
  {bf_a:2,bf_b:1,ans:1,choices:['LL (single right at A)','RR (single left at A)','LR (double: left at B, right at A)','RL (double: right at B, left at A)'],exp:'BF(A)=+2 (right-heavy) + BF(B)=+1 (also right-heavy) → RR rotation. Single left rotation at A. B becomes new root.'},
  {bf_a:-2,bf_b:1,ans:2,choices:['LL (single right at A)','RR (single left at A)','LR (double: left at B, right at A)','RL (double: right at B, left at A)'],exp:'BF(A)=−2 + BF(B)=+1 (zig-zag!) → LR double rotation. Left-rotate B first to straighten, then right-rotate A.'},
  {bf_a:2,bf_b:-1,ans:3,choices:['LL (single right at A)','RR (single left at A)','LR (double: left at B, right at A)','RL (double: right at B, left at A)'],exp:'BF(A)=+2 + BF(B)=−1 (zig-zag!) → RL double rotation. Right-rotate B first to straighten, then left-rotate A.'},
  {bf_a:-2,bf_b:0,ans:0,choices:['LL (single right at A)','RR (single left at A)','LR (double: left at B, right at A)','RL (double: right at B, left at A)'],exp:'BF(A)=−2 + BF(B)=0 → LL rotation (occurs during deletion). B has equal subtrees. Single right at A fixes it.'},
  {bf_a:2,bf_b:0,ans:1,choices:['LL (single right at A)','RR (single left at A)','LR (double: left at B, right at A)','RL (double: right at B, left at A)'],exp:'BF(A)=+2 + BF(B)=0 → RR rotation (occurs during deletion). B has equal subtrees. Single left at A.'},
  {bf_a:-2,bf_b:-1,ans:0,choices:['LR','LL','RL','RR'],exp:'BF(A)=−2 and child leans same direction (−1) → single rotation (LL). Same-direction lean = single fix.'},
  {bf_a:2,bf_b:1,ans:3,choices:['LR','LL','RL','RR'],exp:'BF(A)=+2 and right child leans right (+1) → RR. B takes A\'s place, A drops left of B.'},
  {bf_a:-2,bf_b:1,ans:0,choices:['RL','RR','LR','LL'],exp:'BF(A)=−2, left child leans RIGHT (+1) → LR (option C in original set, but here choice index 2 = LR). Zig-zag → double rotation.'},
  {bf_a:2,bf_b:-1,ans:0,choices:['RL (right at B, left at A)','LL (right at A)','LR (left at B, right at A)','RR (left at A)'],exp:'BF(A)=+2, right child leans LEFT (−1) → RL. C (B\'s left child) becomes new root after both rotations.'},
  {bf_a:-2,bf_b:-1,ans:1,choices:['Insert went right-right','Insert went left-left or deletion left subtree','Insert went left-right zig-zag','Insert went right-left zig-zag'],exp:'BF(A)=−2 and BF(B)=−1 means the path went left then left again (or left subtree shrank). LL imbalance.'},
  {bf_a:2,bf_b:-1,ans:3,choices:['Same-direction lean → single rotation','Opposite-direction lean → double rotation needed','Always use LL when BF=+2','RR is always the answer for positive BF'],exp:'BF(A)=+2 but B leans OPPOSITE direction (−1). Zig-zag shape needs two rotations (RL). Single rotation would just move the problem up.'},
];

let rotIdx=0, rotScore=0, rotScenarios=[];
function initRot(){
  rotScenarios=shuffle([...ROT_SCENARIOS]);
  rotIdx=0; rotScore=0;
  renderRot();
}
function renderRot(){
  const s=rotScenarios[rotIdx];
  document.getElementById('rot-num').textContent=`Scenario ${rotIdx+1} / ${rotScenarios.length}`;
  document.getElementById('rot-score').textContent=`Score: ${rotScore}`;
  document.getElementById('rot-prog').style.width=`${(rotIdx/rotScenarios.length)*100}%`;
  // Draw SVG diagram
  const svgHTML=drawRotSVG(s.bf_a,s.bf_b);
  document.getElementById('rot-svg-area').innerHTML=svgHTML;
  document.getElementById('rot-question').innerHTML=`Node A has balance factor <span style="color:${s.bf_a<0?'var(--rose)':'var(--blue)'}">${s.bf_a>0?'+':''}${s.bf_a}</span> and its relevant child B has balance factor <span style="color:${s.bf_b<0?'var(--rose)':s.bf_b>0?'var(--blue)':'var(--teal)'}">${s.bf_b>0?'+':''}${s.bf_b}</span>. Which rotation fixes this?`;
  s.choices.forEach((c,i)=>{
    const btn=document.getElementById(`rc${i}`);
    btn.textContent=c; btn.className='rot-choice'; btn.disabled=false; btn.onclick=()=>answerRot(i);
  });
  document.getElementById('rot-explain').className='q-explain';
  document.getElementById('rot-next').disabled=true;
}

function drawRotSVG(bfA,bfB){
  const isLeft=bfA<0;
  const childSide=isLeft?'left':'right';
  const cx=isLeft?100:220, cy=140;
  const ax=160, ay=60;
  let html=`<svg viewBox="0 0 320 210" width="280" style="background:var(--bg);border-radius:8px;border:1px solid var(--border)">`;
  // edges
  html+=`<line x1="${ax}" y1="${ay}" x2="${cx}" y2="${cy}" stroke="var(--muted)" stroke-width="1.5"/>`;
  if(isLeft){
    html+=`<line x1="${ax}" y1="${ay}" x2="240" y2="${cy}" stroke="var(--muted)" stroke-width="1.5" stroke-dasharray="4,3"/>`;
    // grandchild
    const gcx = bfB>0 ? 140 : 70;
    html+=`<line x1="${cx}" y1="${cy}" x2="${gcx}" y2="210" stroke="var(--muted)" stroke-width="1.2" stroke-dasharray="3,3"/>`;
    html+=`<circle cx="${gcx}" cy="210" r="16" fill="rgba(167,139,250,.1)" stroke="var(--violet)" stroke-width="1.2"/>`;
    html+=`<text x="${gcx}" y="215" text-anchor="middle" style="font-family:var(--mono);font-size:9px;fill:var(--violet)">new</text>`;
  } else {
    html+=`<line x1="${ax}" y1="${ay}" x2="80" y2="${cy}" stroke="var(--muted)" stroke-width="1.5" stroke-dasharray="4,3"/>`;
    const gcx = bfB>0 ? 220 : 240;
    html+=`<line x1="${cx}" y1="${cy}" x2="${gcx}" y2="210" stroke="var(--muted)" stroke-width="1.2" stroke-dasharray="3,3"/>`;
    html+=`<circle cx="${gcx}" cy="210" r="16" fill="rgba(167,139,250,.1)" stroke="var(--violet)" stroke-width="1.2"/>`;
    html+=`<text x="${gcx}" y="215" text-anchor="middle" style="font-family:var(--mono);font-size:9px;fill:var(--violet)">new</text>`;
  }
  // A node
  html+=`<circle cx="${ax}" cy="${ay}" r="26" fill="rgba(248,113,113,.12)" stroke="var(--rose)" stroke-width="2"/>`;
  html+=`<text x="${ax}" y="${ay-4}" text-anchor="middle" style="font-family:var(--mono);font-size:13px;fill:var(--text)">A</text>`;
  html+=`<text x="${ax}" y="${ay+12}" text-anchor="middle" style="font-family:var(--mono);font-size:9px;fill:var(--rose)">BF:${bfA>0?'+':''}${bfA}</text>`;
  // B node
  html+=`<circle cx="${cx}" cy="${cy}" r="26" fill="rgba(96,165,250,.12)" stroke="var(--blue)" stroke-width="2"/>`;
  html+=`<text x="${cx}" y="${cy-4}" text-anchor="middle" style="font-family:var(--mono);font-size:13px;fill:var(--text)">B</text>`;
  html+=`<text x="${cx}" y="${cy+12}" text-anchor="middle" style="font-family:var(--mono);font-size:9px;fill:var(--blue)">BF:${bfB>0?'+':''}${bfB}</text>`;
  html+=`</svg>`;
  return html;
}

function answerRot(i){
  const s=rotScenarios[rotIdx];
  const correct=i===s.ans;
  for(let j=0;j<4;j++){
    const btn=document.getElementById(`rc${j}`);
    btn.disabled=true; btn.onclick=null;
    if(j===s.ans) btn.classList.add('cor');
    else if(j===i&&!correct) btn.classList.add('wrg');
  }
  const exp=document.getElementById('rot-explain');
  exp.innerHTML=s.exp; exp.className='q-explain show '+(correct?'cor-explain':'wrg-explain');
  if(correct){rotScore+=10;addXP(10);}
  document.getElementById('rot-score').textContent=`Score: ${rotScore}`;
  document.getElementById('rot-next').disabled=false;
}
function nextRot(){
  rotIdx++;
  if(rotIdx>=rotScenarios.length){rotIdx=0;}
  renderRot();
}
function restartRot(){rotIdx=0;rotScore=0;renderRot();}

// ═══════════════════════════════════════════════
// GAME 5 — MATCH PAIRS
// ═══════════════════════════════════════════════
const MATCH_SETS=[
  {title:'Ch 18 — Operations & Complexity',pairs:[
    ['addFirst(e) in LinkedList','O(1) — update head pointer'],
    ['removeLast() in singly LinkedList','O(n) — must find 2nd-to-last node'],
    ['Stack.push(e)','O(1) — append to end of list'],
    ['Queue.dequeue()','O(1) — removeFirst() from LinkedList'],
    ['Priority Queue internal structure','Max-Heap — root = highest priority'],
    ['Generator uses','yield — pauses, returns value, resumes'],
  ]},
  {title:'Ch 18/19 — Vocabulary Match',pairs:[
    ['LIFO','Stack'],
    ['FIFO','Queue'],
    ['Highest priority first','Priority Queue'],
    ['Left < Root < Right (every node)','BST Property'],
    ['Inorder traversal result','Sorted ascending output'],
    ['New node always placed here in BST','As a leaf node'],
  ]},
  {title:'Ch 19 — Traversal Orders',pairs:[
    ['Preorder','Root → Left → Right'],
    ['Inorder','Left → Root → Right'],
    ['Postorder','Left → Right → Root'],
    ['Breadth-first / Level-order','Uses a Queue internally'],
    ['BST Delete — Case 1','Node has NO left child → connect parent to right'],
    ['BST Delete — Case 2','Node HAS left child → replace with rightMost'],
  ]},
  {title:'Ch 20 — AVL Rotations',pairs:[
    ['LL rotation','Single right rotation at A'],
    ['RR rotation','Single left rotation at A'],
    ['LR rotation','Left at B then right at A (double)'],
    ['RL rotation','Right at B then left at A (double)'],
    ['BF = −2, child BF = +1','LR rotation needed'],
    ['BF = +2, child BF = −1','RL rotation needed'],
  ]},
  {title:'Ch 20 — AVL Concepts',pairs:[
    ['Balance factor formula','height(right) − height(left)'],
    ['Valid balance factor range','{−1, 0, +1}'],
    ['AVLTreeNode extra field','height — for O(1) BF computation'],
    ['Max AVL tree height','≈ 1.44 × log₂(n)'],
    ['Rotations per single insert','At most 1 (single or double)'],
    ['createNewNode() override pattern','Factory Method Design Pattern'],
  ]},
];

let matchLeft=[], matchRight=[], matchSelectedLeft=null, matchSelectedRight=null;
let matchedPairs=0, matchTotal=0, matchSetIdx=0;

function newMatchGame(){
  const setIdx=Math.floor(Math.random()*MATCH_SETS.length);
  const set=MATCH_SETS[setIdx];
  matchLeft=shuffle(set.pairs.map((p,i)=>({id:i,text:p[0],matched:false})));
  matchRight=shuffle(set.pairs.map((p,i)=>({id:i,text:p[1],matched:false})));
  matchSelectedLeft=null; matchSelectedRight=null;
  matchedPairs=0; matchTotal=set.pairs.length;
  document.getElementById('match-total').textContent=matchTotal;
  document.getElementById('match-count').textContent=0;
  document.getElementById('match-feedback').textContent=set.title;
  document.getElementById('match-feedback').style.color='var(--muted)';
  renderMatch();
}

function renderMatch(){
  const wrap=document.getElementById('match-grid-wrap');
  wrap.innerHTML='';
  const grid=document.createElement('div');
  grid.className='match-grid';
  const leftCol=document.createElement('div');
  const rightCol=document.createElement('div');
  leftCol.innerHTML='<div class="match-col-title">Concept / Term</div>';
  rightCol.innerHTML='<div class="match-col-title">Definition / Answer</div>';
  matchLeft.forEach(item=>{
    const card=document.createElement('div');
    card.className='match-card'+(item.matched?' matched':item===matchSelectedLeft?' selected':'');
    card.textContent=item.text;
    if(!item.matched) card.onclick=()=>selectLeft(item);
    leftCol.appendChild(card);
  });
  matchRight.forEach(item=>{
    const card=document.createElement('div');
    card.className='match-card'+(item.matched?' matched':item===matchSelectedRight?' selected':'');
    card.textContent=item.text;
    if(!item.matched) card.onclick=()=>selectRight(item);
    rightCol.appendChild(card);
  });
  grid.appendChild(leftCol); grid.appendChild(rightCol);
  wrap.appendChild(grid);
}

function selectLeft(item){
  if(item.matched)return;
  matchSelectedLeft=item;
  checkMatch();
  renderMatch();
}
function selectRight(item){
  if(item.matched)return;
  matchSelectedRight=item;
  checkMatch();
  renderMatch();
}
function checkMatch(){
  if(!matchSelectedLeft||!matchSelectedRight)return;
  const fb=document.getElementById('match-feedback');
  if(matchSelectedLeft.id===matchSelectedRight.id){
    matchSelectedLeft.matched=true; matchSelectedRight.matched=true;
    matchedPairs++;
    document.getElementById('match-count').textContent=matchedPairs;
    fb.textContent=`✓ Correct! "${matchSelectedLeft.text}" matches "${matchSelectedRight.text}"`;
    fb.style.color='var(--teal)';
    addXP(10);
    if(matchedPairs===matchTotal){
      setTimeout(()=>{fb.textContent='🏆 All pairs matched! +50 XP';addXP(50);},300);
    }
  } else {
    fb.textContent=`✗ "${matchSelectedLeft.text}" does not match "${matchSelectedRight.text}". Try again!`;
    fb.style.color='var(--rose)';
  }
  matchSelectedLeft=null; matchSelectedRight=null;
  renderMatch();
}

// ═══════════════════════════════════════════════
// GAME 6 — SPEED ROUND
// ═══════════════════════════════════════════════
let spScore=0,spCombo=0,spBest=0,spCurrent=null,spTimer=null,spTimeLeft=10,spActive=false,spUsed=[];

function initSpeed(){ document.getElementById('sp-opts').innerHTML=''; }

function startSpeed(){
  spScore=0; spCombo=0; spUsed=[];
  spActive=true;
  document.getElementById('sp-result').style.display='none';
  document.getElementById('sp-start').textContent='▶ Playing...';
  nextSpeedQ();
}

function nextSpeedQ(){
  if(!spActive)return;
  clearInterval(spTimer);
  // pick question not recently used
  let pool=QB.filter(q=>!spUsed.includes(q));
  if(pool.length===0){spUsed=[];pool=QB;}
  const q=pool[Math.floor(Math.random()*pool.length)];
  spUsed.push(q); spCurrent=q;
  spTimeLeft=12;
  document.getElementById('sp-question').innerHTML=q.q;
  document.getElementById('sp-hint').textContent=`Chapter ${q.ch} — ${q.tag}`;
  const opts=document.getElementById('sp-opts');
  opts.innerHTML='';
  q.opts.forEach((o,i)=>{
    const btn=document.createElement('button');
    btn.className='speed-opt'; btn.innerHTML=o;
    btn.onclick=()=>answerSpeed(i,q,btn);
    opts.appendChild(btn);
  });
  updateSpeedTimer();
  spTimer=setInterval(()=>{
    spTimeLeft--;
    updateSpeedTimer();
    if(spTimeLeft<=0){
      clearInterval(spTimer);
      handleSpeedTimeout();
    }
  },1000);
}

function updateSpeedTimer(){
  const el=document.getElementById('sp-timer');
  el.textContent=spTimeLeft;
  el.className='speed-timer'+(spTimeLeft<=4?' low':'');
}

function answerSpeed(i,q,btn){
  clearInterval(spTimer);
  document.querySelectorAll('.speed-opt').forEach(b=>{b.disabled=true;b.onclick=null;});
  const correct=i===q.ans;
  btn.classList.add(correct?'cor':'wrg');
  if(!correct) document.querySelectorAll('.speed-opt')[q.ans].classList.add('cor');
  if(correct){
    spCombo++;
    const bonus=Math.floor(spTimeLeft/3);
    const pts=10*(spCombo>2?2:1)+bonus;
    spScore+=pts; addXP(pts);
  } else { spCombo=0; }
  if(spScore>spBest) spBest=spScore;
  document.getElementById('sp-score').textContent=spScore;
  document.getElementById('sp-combo').textContent=spCombo;
  document.getElementById('sp-best').textContent=spBest;
  setTimeout(()=>nextSpeedQ(),900);
}

function handleSpeedTimeout(){
  document.querySelectorAll('.speed-opt').forEach(b=>{b.disabled=true;b.onclick=null;});
  if(spCurrent) document.querySelectorAll('.speed-opt')[spCurrent.ans].classList.add('cor');
  spCombo=0;
  document.getElementById('sp-combo').textContent=0;
  setTimeout(()=>nextSpeedQ(),1000);
}

function stopSpeed(){
  spActive=false; clearInterval(spTimer);
  document.getElementById('sp-start').textContent='▶ Start';
  const res=document.getElementById('sp-result');
  res.style.display='block';
  const emojis=['😤 Keep Practising!','👍 Not Bad!','🎉 Great Work!','🏆 Champion!'];
  const tier=spScore<50?0:spScore<100?1:spScore<200?2:3;
  document.getElementById('sp-res-emoji').textContent=emojis[tier].split(' ')[0];
  document.getElementById('sp-res-score').textContent=`${spScore} points`;
  document.getElementById('sp-res-msg').textContent=emojis[tier].slice(2)+` Best: ${spBest}`;
  document.getElementById('sp-opts').innerHTML='';
  document.getElementById('sp-question').textContent='Press Start to play again!';
  document.getElementById('sp-hint').textContent='';
  document.getElementById('sp-timer').textContent='–';
}

// ═══════════════════════════════════════════════
// UTILITIES
// ═══════════════════════════════════════════════
function shuffle(arr){ const a=[...arr]; for(let i=a.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[a[i],a[j]]=[a[j],a[i]];} return a; }

// INIT
initFlash();
newBSTChallenge();
initRot();
newMatchGame();
initSpeed();
</script>
</body>
</html>
