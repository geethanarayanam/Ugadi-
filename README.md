<html lang="te">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ugadi Subhakankshalu</title>
    <style>
        body { margin: 0; font-family: 'Arial', sans-serif; overflow: hidden; background: #fff9e6; text-align: center; }
        .page { height: 100vh; width: 100vw; display: flex; flex-direction: column; align-items: center; justify-content: center; position: absolute; transition: transform 0.6s ease-in-out; }
        #page2 { transform: translateX(100%); background: #fff0d4; }
        
        /* Elements */
        .temple { font-size: 150px; position: relative; cursor: pointer; z-index: 5; }
        .bird-top { font-size: 40px; position: absolute; top: -40px; left: 50%; transform: translateX(-50%); transition: 0.5s; }
        .bird-flying { font-size: 40px; position: absolute; animation: fly 10s linear infinite; top: 10%; }
        .items-down { font-size: 50px; margin-top: -20px; }
        .bell { font-size: 50px; cursor: pointer; display: inline-block; }
        .bell:active { transform: rotate(20deg); }
        
        /* Animations */
        @keyframes fly { 
            0% { left: -10%; top: 10%; } 
            100% { left: 110%; top: 15%; } 
        }
        .leaf { position: absolute; top: -50px; font-size: 24px; animation: fall 5s linear infinite; }
        @keyframes fall {
            to { transform: translateY(100vh) rotate(360deg); }
        }
        .om-symbol { font-size: 100px; animation: rotateOm 4s linear infinite; cursor: pointer; margin: 20px; }
        @keyframes rotateOm { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        
        .btn { padding: 15px 30px; font-size: 20px; background: #ff9933; color: white; border: none; border-radius: 25px; cursor: pointer; margin-top: 20px; }
        .blessing-text { font-size: 24px; color: #b35900; display: none; font-weight: bold; }
    </style>
</head>
<body>

    <div id="page1" class="page">
        <h1>🙏 నమస్కారం (Namaskaram)</h1>
        <div style="font-size: 28px; color: #d2691e; font-weight: bold;">
            విశ్వావసు నామ సంవత్సర శుభాకాంక్షలు <br>
            (Viswavasu Nama Samvastra Subhakankshalu)
        </div>

        <div class="bird-flying">🕊️</div>

        <div style="position: relative; margin-top: 50px;">
            <div id="sittingBird" class="bird-top">🐦</div>
            <div class="temple">🛕</div>
            <div class="bell" onclick="playSound()">🔔</div>
        </div>

        <div class="items-down">🥥 🥭 🥭 🥥</div>

        <button class="btn" onclick="goToPage2()">Get Blessings ➔</button>
    </div>

    <div id="page2" class="page">
        <div id="om" class="om-symbol" onclick="showBlessings()">🕉️</div>
        <div id="blessingMsg" class="blessing-text">దేవుని ఆశీస్సులు మీకు ఎల్లప్పుడూ ఉండాలి! <br> (God's blessings are always with you!)</div>
        <button class="btn" onclick="goToPage1()">⬅ Back</button>
    </div>

    <script>
        // Create falling leaves
        function createLeaf() {
            const leaves = ['🍃', '🌿'];
            const leaf = document.createElement('div');
            leaf.classList.add('leaf');
            leaf.innerText = leaves[Math.floor(Math.random() * leaves.length)];
            leaf.style.left = Math.random() * 100 + 'vw';
            leaf.style.animationDuration = (Math.random() * 3 + 2) + 's';
            document.body.appendChild(leaf);
            setTimeout(() => leaf.remove(), 5000);
        }
        setInterval(createLeaf, 500);

        // Page Navigation
        function goToPage2() {
            document.getElementById('page1').style.transform = 'translateX(-100%)';
            document.getElementById('page2').style.transform = 'translateX(0)';
        }
        function goToPage1() {
            document.getElementById('page1').style.transform = 'translateX(0)';
            document.getElementById('page2').style.transform = 'translateX(100%)';
        }

        // Sound Simulation (Beep since I can't provide an MP3 file)
        function playSound() {
            const context = new (window.AudioContext || window.webkitAudioContext)();
            const osc = context.createOscillator();
            const gain = context.createGain();
            osc.connect(gain);
            gain.connect(context.destination);
            osc.type = 'sine';
            osc.frequency.value = 880; // High pitch bell sound
            osc.start();
            gain.gain.exponentialRampToValueAtTime(0.00001, context.currentTime + 1);
            osc.stop(context.currentTime + 1);
        }

        function showBlessings() {
            document.getElementById('blessingMsg').style.display = 'block';
        }
    </script>
</body>
</html>
