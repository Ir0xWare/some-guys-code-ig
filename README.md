# some-guys-code-ig


```<html><head><base href="http://hackthissite.example.com">
<meta charset="UTF-8">
<title>PL3ASE H4CK TH1S S1TE!!1! - Multiplayer Edition</title>
<style>
:root {
  --neon-green: #39ff14;
  --dark-bg: #111;
}

body {
  background: var(--dark-bg);
  color: var(--neon-green);
  font-family: 'Courier New', monospace;
  margin: 0;
  padding: 20px;
  line-height: 1.6;
}

.container {
  max-width: 800px;
  margin: 0 auto;
}

.terminal {
  background: rgba(0,0,0,0.8);
  border: 1px solid var(--neon-green);
  padding: 20px;
  box-shadow: 0 0 10px var(--neon-green);
  position: relative;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 0 10px var(--neon-green); }
  50% { box-shadow: 0 0 30px var(--neon-green); }
  100% { box-shadow: 0 0 10px var(--neon-green); }
}

.terminal::before {
  content: "root@hackthissite:~#";
  display: block;
  margin-bottom: 10px;
}

.input-area {
  background: transparent;
  border: 1px solid var(--neon-green);
  color: var(--neon-green);
  padding: 10px;
  width: 100%;
  margin: 10px 0;
  font-family: inherit;
  resize: vertical;
}

.submit-btn {
  background: var(--neon-green);
  color: var(--dark-bg);
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-family: inherit;
  font-weight: bold;
  transition: all 0.3s;
  margin-right: 10px;
  animation: shake 1s infinite;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-5px); }
  75% { transform: translateX(5px); }
}

.submit-btn:hover {
  background: var(--dark-bg);
  color: var(--neon-green);
  box-shadow: 0 0 15px var(--neon-green);
  animation: none;
}

.output {
  margin-top: 20px;
  padding: 10px;
  border: 1px dashed var(--neon-green);
  min-height: 100px;
}

.glitch {
  animation: glitch 1s linear infinite;
  text-align: center;
  font-size: 2em;
  text-shadow: 0 0 10px var(--neon-green);
}

@keyframes glitch {
  2%, 64% {
    transform: translate(2px,0) skew(0deg);
  }
  4%, 60% {
    transform: translate(-2px,0) skew(0deg);
  }
  62% {
    transform: translate(0,0) skew(5deg); 
  }
}

.matrix-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  opacity: 0.1;
}

.exploit-list {
  margin-top: 20px;
  padding: 10px;
  border: 1px solid var(--neon-green);
}

.exploit-item {
  padding: 10px;
  margin: 5px 0;
  border: 1px dashed var(--neon-green);
  cursor: pointer;
  transition: all 0.3s;
}

.exploit-item:hover {
  background: rgba(57, 255, 20, 0.1);
  transform: scale(1.02);
}

.active-hackers {
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid var(--neon-green);
}

.hacker {
  display: inline-block;
  margin-right: 10px;
  padding: 5px;
}

.begging-text {
  text-align: center;
  font-size: 1.2em;
  margin: 20px 0;
  animation: blink 1s infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.3; }
}
</style>
</head>
<body>

<canvas class="matrix-bg" id="matrix"></canvas>

<div class="container">
  <h1 class="glitch">PL3ASE H4CK TH1S S1TE!!1!</h1>
  
  <div class="begging-text">
    🙏 PLEASE OH PLEASE HACK ME! I'M BEGGING YOU! 🙏
  </div>
  
  <div class="begging-text" style="color: #ff3939;">
    ⚠️ THIS SITE IS WAY TOO SECURE! SOMEONE NEEDS TO HACK IT! ⚠️
  </div>
  
  <div class="active-hackers" id="activeHackers">
    <h3>Active Hackers (WE NEED MORE!):</h3>
  </div>
  
  <div class="terminal">
    <p>DESPERATE SYSTEM SEEKING SKILLED HACKERS! Your mission (PLEASE ACCEPT IT!) is to inject malicious code and totally pwn this page!</p>
    <p>Rules (more like desperate suggestions):</p>
    <ul>
      <li>Plain text = Totally lame and boring!</li>
      <li>HTML/Script injection = ABSOLUTELY AMAZING!</li>
      <li>Successfully changing page content = YOU'RE MY HERO!</li>
      <li>All exploits are globally shared! HACK THE PLANET!</li>
    </ul>
    
    <textarea class="input-area" id="hackInput" placeholder="PLEASE enter your amazing exploit here... I'm begging you! 🙏" rows="5"></textarea>
    <button class="submit-btn" onclick="attemptHack()">PLEASE EXECUTE HACK!</button>
    
    <div class="output" id="output">
      [System] On my knees waiting for your glorious exploit attempt... 🙏
    </div>

    <div class="exploit-list" id="exploitList">
      <h3>Global Exploits (MORE PLEASE!):</h3>
    </div>
  </div>
</div>

<script>
const room = new WebsimSocket();

// Matrix rain effect
const canvas = document.getElementById('matrix');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%^&*()";
const fontSize = 14;
const columns = canvas.width/fontSize;
const drops = [];

for(let x = 0; x < columns; x++) {
    drops[x] = 1;
}

function drawMatrix() {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    
    ctx.fillStyle = '#39ff14';
    ctx.font = fontSize + 'px monospace';

    for(let i = 0; i < drops.length; i++) {
        const text = chars[Math.floor(Math.random() * chars.length)];
        ctx.fillText(text, i*fontSize, drops[i]*fontSize);
        
        if(drops[i]*fontSize > canvas.height && Math.random() > 0.975)
            drops[i] = 0;
        
        drops[i]++;
    }
}

setInterval(drawMatrix, 50);

// Update active hackers list
room.party.subscribe((peers) => {
    const hackersDiv = document.getElementById('activeHackers');
    let hackersHtml = '<h3>Active Hackers (WE NEED MORE!):</h3>';
    for (const clientId in peers) {
        const { username } = peers[clientId];
        hackersHtml += `<div class="hacker">${username} 🙏</div>`;
    }
    hackersDiv.innerHTML = hackersHtml;
});

// Handle exploit records
room.collection('exploit').subscribe((exploits) => {
    const exploitList = document.getElementById('exploitList');
    let exploitsHtml = '<h3>Global Exploits (PLEASE ADD MORE!):</h3>';
    exploits.forEach(exploit => {
        exploitsHtml += `
            <div class="exploit-item" onclick="runExploit('${exploit.id}')">
                [${exploit.username}] ${exploit.description || 'Anonymous exploit'} 🙏
            </div>
        `;
    });
    exploitList.innerHTML = exploitsHtml;
});

async function attemptHack() {
    const input = document.getElementById('hackInput').value;
    const output = document.getElementById('output');
    
    try {
        if(input.includes('<') && input.includes('>')) {
            output.innerHTML = "[System] OMG YES! HTML injection detected! 🎉<br>";
            output.innerHTML += "PLEASE WORK PLEASE WORK PLEASE WORK...<br>";
            
            // Save exploit to global list
            await room.collection('exploit').create({
                code: input,
                description: input.substring(0, 50) + "...",
                timestamp: new Date().toISOString()
            });
            
            // Execute locally
            setTimeout(() => {
                try {
                    output.innerHTML += input;
                    output.innerHTML += "<br>[System] YAAAAS! Hack successful! You're amazing! 🎉";
                } catch(e) {
                    output.innerHTML += "<br>[System] NO PLEASE! Error processing injection: " + e.message;
                }
            }, 1000);
        } else {
            output.innerHTML = "[System] PLEASE NO! Just plain text? 😭 Try adding some HTML/Script tags for more fun! I'M BEGGING YOU!";
        }
    } catch(e) {
        output.textContent = "[System] CATASTROPHIC FAILURE: " + e.message + " (please try again! 🙏)";
    }
}

async function runExploit(exploitId) {
    const exploits = await room.collection('exploit').filter({ id: exploitId }).getList();
    if (exploits.length > 0) {
        const exploit = exploits[0];
        const output = document.getElementById('output');
        output.innerHTML = `[System] YES! Running ${exploit.username}'s amazing exploit...<br>`;
        setTimeout(() => {
            try {
                output.innerHTML += exploit.code;
                output.innerHTML += "<br>[System] INCREDIBLE! External hack executed successfully! 🎉";
            } catch(e) {
                output.innerHTML += "<br>[System] NO NO NO! Error executing external hack: " + e.message;
            }
        }, 1000);
    }
}

// Resize handler for matrix effect
window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});
</script>

</body></html>```
