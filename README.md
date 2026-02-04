# Good-night-my-lovely-Giselle-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Nightmare Stealth - Giselle ❤️</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; touch-action: manipulation; }
        html, body { width: 100%; height: 100%; overflow: hidden; background: #0c1445; position: fixed; }
        body { font-family: -apple-system, system-ui, sans-serif; }
        #background { position: fixed; inset: 0; background: linear-gradient(to bottom, #020111 0%, #191621 100%); z-index: -2; transition: background 3s ease; }
        #door-container { position: absolute; right: 0; top: 20%; width: 60px; height: 120px; background: #3d2b1f; border-left: 4px solid #2a1d15; z-index: 40; transition: transform 0.6s ease-in-out; transform-origin: right; transform: rotateY(0deg); }
        .door-open { transform: rotateY(-75deg) !important; }
        #parent-eye { position: absolute; top: 45px; right: 10px; font-size: 30px; display: none; z-index: 39; }
        .bed-sheets { position: absolute; bottom: -20px; width: 120%; left: -10%; height: 35%; background: #fdfdfd; border-radius: 50% 50% 0 0; z-index: 10; }
        .pillow { position: absolute; bottom: 12%; left: 50%; transform: translateX(-50%); width: 90%; height: 22%; background: #ffffff; border-radius: 40px; z-index: 9; }
        .moon { position: absolute; top: -100px; right: 12%; width: 75px; height: 75px; background: #fdfae1; border-radius: 50%; box-shadow: 0 0 50px #fdfae1; z-index: 1; transition: top 4s ease; }
        #ui-top { position: absolute; top: 8%; width: 100%; display: flex; justify-content: space-around; align-items: center; z-index: 30; }
        .hud-box { background: rgba(255,255,255,0.1); padding: 8px 15px; border-radius: 15px; color: white; backdrop-filter: blur(5px); font-weight: bold; min-width: 100px; text-align: center; }
        #heart-rate-ui { position: absolute; left: 15px; top: 50%; transform: translateY(-50%); display: flex; flex-direction: column; align-items: center; z-index: 30; color: #ff4d4d; font-weight: bold; }
        #heart-icon { font-size: 30px; animation: beat 1s infinite; }
        @keyframes beat { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.3); } }
        #gameOver { display: none; position: fixed; inset: 0; background: #fff; color: #000; animation: flash 0.08s infinite; z-index: 200; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
        @keyframes flash { 0% { background: #fff; } 50% { background: #f00; } 100% { background: #000; color: #fff; } }
        .item-container { position: absolute; width: 90px; height: 90px; display: flex; justify-content: center; align-items: center; z-index: 15; cursor: pointer; }
        .emoji { font-size: 50px; }
        @keyframes jump { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-80px); } }
        #finalMessage { display: none; position: relative; background: #fff; margin: 0 20px; padding: 35px 25px; border-radius: 30px; text-align: center; z-index: 50; color: #2c3e50; box-shadow: 0 20px 60px rgba(0,0,0,0.6); animation: popIn 0.8s forwards; }
        @keyframes popIn { from { transform: scale(0.8); opacity: 0; } to { transform: scale(1); opacity: 1; } }
        .shake { animation: shake 0.1s infinite; }
        @keyframes shake { 0% { transform: translate(3px, 3px); } 50% { transform: translate(-3px, -3px); } 100% { transform: translate(3px, -3px); } }
    </style>
</head>
<body id="mainBody">
<div id="background"></div>
<div class="moon" id="moon"></div>
<div class="pillow"></div>
<div class="bed-sheets"></div>
<div id="door-container"></div>
<div id="parent-eye">👁️‍🗨️</div>

<audio id="music" loop><source src="https://www.bensound.com/bensound-music/bensound-tenderness.mp3" type="audio/mpeg"></audio>
<audio id="creak"><source src="https://assets.mixkit.co/active_storage/sfx/1001/1001-preview.mp3" type="audio/mpeg"></audio>
<audio id="slam"><source src="https://assets.mixkit.co/active_storage/sfx/2573/2573-preview.mp3" type="audio/mpeg"></audio>
<audio id="winChime"><source src="https://assets.mixkit.co/active_storage/sfx/2019/2019-preview.mp3" type="audio/mpeg"></audio>

<div id="overlay" style="position:fixed; inset:0; background:rgba(0,0,0,0.95); z-index:100; display:flex; flex-direction:column; justify-content:center; align-items:center; color:white; text-align:center; padding:20px;">
    <h1 style="color:#a29bfe; font-size:28px;">Nightmare Stealth ❤️</h1>
    <p>10 sheep. 60 seconds. Don't get caught by mom or dad!</p>
    <button onclick="startGame()" style="padding:18px 45px; font-size:1.1rem; border-radius:50px; border:none; background:#6c5ce7; color:white; margin-top:30px; font-weight:bold;">Sleep 💤</button>
</div>

<div id="ui-top">
    <div class="hud-box" style="color:#ffeb3b;">Time: <span id="time-left">60</span>s</div>
    <div class="hud-box">Sheep: <span id="score">0</span>/10</div>
</div>

<div id="heart-rate-ui">
    <div id="heart-icon">❤️</div>
    <div id="bpm-text">70 BPM</div>
</div>

<div id="gameOver">
    <h1 id="scare-emoji" style="font-size: 70px;">👹</h1>
    <h1 id="scare-text" style="font-size: 35px;">WAKE UP!</h1>
    <p id="scare-sub" style="margin-top: 10px;">Mom or Dad caught you awake!</p>
    <button onclick="location.reload()" style="padding:15px 35px; background:white; color:black; border:none; border-radius:50px; font-weight:bold; margin-top:20px;">Try again</button>
</div>

<div id="finalMessage">
    <h1 style="color: #6c5ce7; margin-bottom: 15px;">Sweet Dreams! 🌙</h1>
    <p>I’m happy you had a wonderful day today!</p>
    <p>Sending you tons of hugs and kisses to keep you warm and sleep wonderfully baby.</p>
    <div style="font-size: 2.8rem; margin-top: 20px;">😴 💋 🤗</div>
</div>

<script>
    let score = 0, currentSpeed = 5.0, isParentLooking = false, timeLeft = 60, gameActive = false, wolvesHit = 0;
    const scoreEl = document.getElementById('score'), timeEl = document.getElementById('time-left');
    const music = document.getElementById('music'), creak = document.getElementById('creak'), slam = document.getElementById('slam'), winChime = document.getElementById('winChime');
    const door = document.getElementById('door-container'), parentEye = document.getElementById('parent-eye');

    function startGame() {
        document.getElementById('overlay').style.display = 'none';
        gameActive = true;
        music.volume = 0.2; music.play();
        startTimer(); spawnLoop(); stealthLoop();
    }

    function startTimer() {
        const t = setInterval(() => {
            if (!gameActive) { clearInterval(t); return; }
            timeLeft--; timeEl.innerText = timeLeft;
            if (timeLeft <= 0) { triggerJumpScare('time'); clearInterval(t); }
        }, 1000);
    }

    function stealthLoop() {
        if (!gameActive) return;
        setTimeout(() => {
            if (!gameActive) return;
            creak.currentTime = 0; creak.play();
            door.classList.add('door-open');
            setTimeout(() => {
                parentEye.style.display = 'block'; isParentLooking = true;
                setTimeout(() => {
                    parentEye.style.display = 'none'; isParentLooking = false;
                    door.classList.remove('door-open');
                    setTimeout(() => { creak.pause(); stealthLoop(); }, 600);
                }, 1800);
            }, 600);
        }, 3000 + Math.random() * 3000);
    }

    function triggerJumpScare(reason) {
        gameActive = false; music.pause(); creak.pause(); slam.play();
        if(reason === 'caught') { 
            document.getElementById('scare-emoji').innerHTML = '👹'; 
            document.getElementById('scare-text').innerHTML = 'CAUGHT YOU!';
            document.getElementById('scare-sub').innerHTML = 'Mom or Dad saw you awake!';
        }
        else if (reason === 'time') { 
            document.getElementById('scare-emoji').innerHTML = '⏰'; 
            document.getElementById('scare-text').innerHTML = "TIME'S UP!"; 
            document.getElementById('scare-sub').innerHTML = 'The nightmare caught you...';
        }
        document.getElementById('mainBody').classList.add('shake');
        document.getElementById('gameOver').style.display = 'flex';
        if (navigator.vibrate) navigator.vibrate([500, 100, 500]);
    }

    function spawnItem() {
        if (!gameActive) return;
        const container = document.createElement('div');
        container.className = 'item-container';
        const rand = Math.random();
        const wolfProb = 0.6 - (score * 0.03); 
        let type = (rand > wolfProb) ? 'wolf' : (rand > (wolfProb - 0.2) ? 'star' : 'sheep');
        
        const emoji = document.createElement('div');
        emoji.className = 'emoji';
        emoji.innerHTML = (type === 'sheep') ? '🐑' : (type === 'wolf' ? '🐺' : '⭐');
        emoji.style.animation = type === 'sheep' ? "jump 0.6s infinite" : "jump 0.3s infinite";
        container.appendChild(emoji);
        
        let xPos = -120, yPos = Math.random() * 30 + 15; 
        container.style.top = yPos + '%'; container.style.left = xPos + 'px';

        const handleTap = (e) => {
            if (!gameActive) return;
            e.preventDefault();
            if (isParentLooking) { triggerJumpScare('caught'); return; }
            if (type === 'sheep') {
                score++; currentSpeed += 1.3; scoreEl.innerText = score;
                if (score >= 10) win();
            } else {
                wolvesHit++;
                if (wolvesHit >= 3) { triggerJumpScare('caught'); return; }
                score = Math.max(0, score - 1); currentSpeed += 3.5;
                scoreEl.innerText = score;
            }
            document.getElementById('bpm-text').innerText = `${70 + (score * 10)} BPM`;
            container.remove();
        };

        container.addEventListener('touchstart', handleTap, { passive: false });
        container.addEventListener('mousedown', handleTap);
        document.body.appendChild(container);

        function move() {
            if (!gameActive) return;
            xPos += currentSpeed; container.style.left = xPos + 'px';
            if (xPos < window.innerWidth + 150 && container.parentNode) {
                requestAnimationFrame(move);
            } else { if (container.parentNode) container.remove(); }
        }
        move();
    }

    function spawnLoop() {
        if (gameActive && score < 10) {
            spawnItem();
            let delay = Math.max(300, 1200 - (score * 110));
            setTimeout(spawnLoop, delay);
        }
    }

    function win() {
        gameActive = false; music.pause(); creak.pause();
        winChime.play();
        document.getElementById('ui-top').style.display = 'none';
        document.getElementById('heart-rate-ui').style.display = 'none';
        document.getElementById('finalMessage').style.display = 'block';
        document.getElementById('moon').style.top = '12%'; 
        door.style.display = 'none'; document.getElementById('background').style.background = '#010108'; 
        document.querySelectorAll('.item-container').forEach(i => i.remove());
    }
</script>
</body>
</html>
