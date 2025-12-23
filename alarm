<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIP Alarm Master - Chonanhnhanh.vn</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@900&family=Roboto:wght@400;700;900&display=swap&subset=vietnamese" rel="stylesheet">
    <style>
        :root { 
            --primary: #00ebb0; 
            --rainbow: linear-gradient(90deg, #ff0000, #ff7f00, #ffff00, #00ff00, #00ffff, #0000ff, #8b00ff, #ff0000);
            --bg-card: #080d1a;
            --bg-deep: #050a14;
        }

        body { 
            background-color: var(--bg-deep); color: #fff; font-family: 'Roboto', sans-serif; 
            display: flex; flex-direction: column; justify-content: center; align-items: center; 
            min-height: 100vh; margin: 0; padding: 20px; box-sizing: border-box;
        }

        /* NAVBAR 7 TAB */
        .navbar {
            position: fixed; top: 0; left: 0; width: 100%; height: 70px;
            background: rgba(5, 10, 20, 0.8); backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.05);
            display: flex; justify-content: center; align-items: center; z-index: 1000;
        }
        .navbar-nav { display: flex; list-style: none; gap: 10px; margin: 0; padding: 0; }
        .nav-link { 
            color: #94a3b8; font-weight: 700; font-size: 0.7rem; text-transform: uppercase; 
            padding: 8px 12px; cursor: pointer; transition: 0.3s; text-decoration: none;
        }
        .nav-link:hover { color: var(--primary); }

        /* CONTAINER BÁO THỨC */
        .alarm-container {
            width: 95%; max-width: 550px; padding: 3px; border-radius: 40px;
            background: var(--rainbow); background-size: 200% auto; animation: rainbow-move 4s linear infinite;
        }
        .alarm-card { background: var(--bg-card); border-radius: 37px; padding: 40px; text-align: center; position: relative; }
        .luxury-header { font-family: 'Montserrat'; font-size: 1.1rem; color: #fff; margin-bottom: 20px; letter-spacing: 2px; text-transform: uppercase; }
        
        .current-time { 
            font-family: 'Montserrat', sans-serif; font-size: 4rem; font-weight: 900; 
            color: var(--primary); text-shadow: 0 0 25px rgba(0, 235, 176, 0.4); margin-bottom: 35px; 
        }

        .input-row { display: flex; gap: 20px; margin-bottom: 30px; justify-content: center; position: relative; z-index: 100; }
        
        .custom-dropdown { width: 110px; background: #0f172a; border-radius: 18px; padding: 12px; border: 1px solid rgba(255,255,255,0.1); position: relative; cursor: pointer; }
        .custom-dropdown label { display: block; font-size: 0.7rem; color: #94a3b8; font-weight: 900; margin-bottom: 5px; }
        .selected-value { font-size: 1.8rem; font-family: 'Montserrat'; font-weight: 900; color: var(--primary); }

        .dropdown-menu {
            position: absolute; top: 110%; left: 0; width: 100%; max-height: 220px; background: #16213e; border-radius: 15px; 
            overflow-y: auto; overflow-x: hidden; display: none; z-index: 999; border: 1px solid var(--primary);
            scrollbar-width: none;
        }
        .dropdown-menu div { padding: 12px; font-size: 1.3rem; font-weight: 700; text-align: center; border-bottom: 1px solid rgba(255,255,255,0.05); }
        .dropdown-menu div:hover { background: var(--primary); color: #000; }

        .tone-select-vip { background: #0f172a; padding: 18px; border-radius: 22px; border: 1px solid rgba(255,255,255,0.05); margin-bottom: 30px; text-align: left; position: relative; z-index: 50; }
        
        /* FIX FONT CHỮ NÚT BẤM */
        .btn-alarm { 
            width: 100%; padding: 20px; border-radius: 55px; border: none; 
            font-family: 'Roboto', sans-serif; font-weight: 900; 
            text-transform: uppercase; cursor: pointer; transition: 0.4s; font-size: 1.1rem; 
        }
        .btn-set { background: var(--primary); color: #000; }

        #countdownBox { display: none; padding: 30px; border-radius: 25px; background: rgba(0, 235, 176, 0.05); border: 2px dashed var(--primary); }
        .countdown-timer { font-family: 'Montserrat'; font-size: 3.2rem; color: #ff9f43; font-weight: 900; margin: 15px 0; }

        .blink-red { color: #ff4757; font-size: 1.8rem; font-weight: 900; animation: blink 0.5s infinite; margin-bottom: 20px; font-family: 'Roboto', sans-serif; }
        
        @keyframes rainbow-move { 0% { background-position: 0% 50%; } 100% { background-position: 200% 50%; } }
        @keyframes blink { 50% { opacity: 0; } }
    </style>
</head>
<body>

    <nav class="navbar">
        <ul class="navbar-nav">
            <li><a href="admin.html" class="nav-link">Tạo Album</a></li>
            <li><a href="managa.html" class="nav-link">Quản Lý</a></li>
            <li><a href="copy_local.html" class="nav-link">Sao Chép</a></li>
            <li><a href="blog.html" class="nav-link">Blog</a></li>
            <li><a href="payment.html" class="nav-link">Gia Hạn</a></li>
            <li><a href="lienhe.html" class="nav-link">Liên Hệ</a></li>
            <li><a href="fedback.html" class="nav-link">Góp Ý</a></li>
        </ul>
    </nav>

    <div class="alarm-container">
        <div class="alarm-card">
            <div class="luxury-header">VIP ALARM MASTER</div>
            <div class="current-time" id="clock">00:00:00</div>

            <div id="setupArea">
                <div class="input-row">
                    <div class="custom-dropdown" onclick="toggleDrop('hourMenu')">
                        <label>GIỜ</label>
                        <div class="selected-value" id="hourDisp">00</div>
                        <div class="dropdown-menu" id="hourMenu"></div>
                    </div>
                    <div class="custom-dropdown" onclick="toggleDrop('minMenu')">
                        <label>PHÚT</label>
                        <div class="selected-value" id="minDisp">00</div>
                        <div class="dropdown-menu" id="minMenu"></div>
                    </div>
                </div>
                
                <div class="tone-select-vip" onclick="toggleDrop('toneMenu')">
                    <label style="display:block; font-size:0.75rem; color:#94a3b8; font-weight:900; margin-bottom:8px">HỆ THỐNG CHUÔNG</label>
                    <div style="display:flex; justify-content:space-between; align-items:center; cursor:pointer">
                        <span id="toneDisp" style="font-weight:700; font-size:1rem">Beep Mặc định</span>
                        <i class="fas fa-chevron-down" style="color:var(--primary); font-size:0.9rem"></i>
                    </div>
                    <div class="dropdown-menu" id="toneMenu" style="width:100%; left:0">
                        <div onclick="selectTone('Beep Mặc định', 'https://www.soundjay.com/buttons/beep-01a.mp3')">Beep Mặc định</div>
                        <div onclick="selectTone('Beep Dồn dập', 'https://www.soundjay.com/buttons/beep-02.mp3')">Beep Dồn dập</div>
                        <div onclick="selectTone('Còi hú khẩn cấp', 'https://bigsoundbank.com/UPLOAD/mp3/0001.mp3')">Còi hú khẩn cấp</div>
                    </div>
                </div>

                <button class="btn-alarm btn-set" onclick="setAlarm()">ĐẶT BÁO THỨC</button>
            </div>

            <div id="countdownBox">
                <div style="font-weight:700; color:var(--primary); font-size:0.9rem; letter-spacing:2px">CÒN LẠI</div>
                <div class="countdown-timer" id="countdownDisplay">00:00:00</div>
                <button onclick="stopAlarm()" style="background:transparent; border:2px solid #ff4757; color:#ff4757; padding:10px 30px; border-radius:50px; cursor:pointer; font-weight:bold; text-transform:uppercase; font-family: 'Roboto', sans-serif;">Hủy báo thức</button>
            </div>
            
            <div id="alarmActiveBox" style="display:none">
                <div class="blink-red">ĐẾN GIỜ RỒI!</div>
                <button class="btn-alarm" style="background:#ff4757; color:#fff" onclick="stopAlarm()">TẮT CHUÔNG</button>
            </div>
        </div>
    </div>

    <audio id="alarmAudio" loop preload="auto"></audio>

    <script>
        const alarmAudio = document.getElementById('alarmAudio');
        let alarmTime = { h: 0, m: 0 };
        let countdownTimer = null;
        let isRinging = false;
        let previewTimeout = null;

        const hMenu = document.getElementById('hourMenu');
        const mMenu = document.getElementById('minMenu');
        for(let i=0; i<24; i++) hMenu.innerHTML += `<div onclick="selectValue('hour', '${String(i).padStart(2,'0')}')">${String(i).padStart(2,'0')}</div>`;
        for(let i=0; i<60; i++) mMenu.innerHTML += `<div onclick="selectValue('min', '${String(i).padStart(2,'0')}')">${String(i).padStart(2,'0')}</div>`;

        function toggleDrop(id) {
            const el = document.getElementById(id);
            const isVisible = el.style.display === 'block';
            document.querySelectorAll('.dropdown-menu').forEach(m => m.style.display = 'none');
            if(!isVisible) el.style.display = 'block';
        }

        function selectValue(type, val) {
            if(type === 'hour') { document.getElementById('hourDisp').innerText = val; alarmTime.h = parseInt(val); }
            else { document.getElementById('minDisp').innerText = val; alarmTime.m = parseInt(val); }
        }

        function selectTone(name, url) {
            if (previewTimeout) clearTimeout(previewTimeout);
            alarmAudio.pause();
            alarmAudio.currentTime = 0;
            document.getElementById('toneDisp').innerText = name;
            alarmAudio.src = url;
            alarmAudio.load();
            alarmAudio.play().then(() => { 
                previewTimeout = setTimeout(() => { 
                    if(!isRinging && document.getElementById('setupArea').style.display !== 'none') { 
                        alarmAudio.pause(); 
                        alarmAudio.currentTime = 0; 
                    } 
                }, 4000); 
            }).catch(e => console.log("Cần tương tác"));
        }

        setInterval(() => {
            document.getElementById('clock').innerText = new Date().toLocaleTimeString('vi-VN', { hour12: false });
        }, 100);

        function setAlarm() {
            if (previewTimeout) clearTimeout(previewTimeout);
            alarmAudio.pause();
            alarmAudio.currentTime = 0;
            if(!alarmAudio.src) alarmAudio.src = 'https://www.soundjay.com/buttons/beep-01a.mp3';
            alarmAudio.load();
            document.getElementById('setupArea').style.display = 'none';
            document.getElementById('countdownBox').style.display = 'block';
            if (countdownTimer) clearInterval(countdownTimer);
            updateCountdown();
            countdownTimer = setInterval(updateCountdown, 500);
        }

        function updateCountdown() {
            const now = new Date();
            let target = new Date();
            target.setHours(alarmTime.h, alarmTime.m, 0, 0);
            if (target <= now) target.setDate(target.getDate() + 1);
            const diff = target - now;
            if (diff <= 500) { triggerAlarm(); return; }
            const totalSecs = Math.ceil(diff / 1000);
            const hrs = Math.floor(totalSecs / 3600);
            const mins = Math.floor((totalSecs % 3600) / 60);
            const secs = totalSecs % 60;
            document.getElementById('countdownDisplay').innerText = `${String(hrs).padStart(2,'0')}:${String(mins).padStart(2,'0')}:${String(secs).padStart(2,'0')}`;
        }

        function triggerAlarm() {
            isRinging = true;
            clearInterval(countdownTimer);
            alarmAudio.play().catch(() => { alert("ĐẾN GIỜ RỒI!"); alarmAudio.play(); });
            document.getElementById('countdownBox').style.display = 'none';
            document.getElementById('alarmActiveBox').style.display = 'block';
        }

        function stopAlarm() {
            isRinging = false;
            if (previewTimeout) clearTimeout(previewTimeout);
            alarmAudio.pause(); alarmAudio.currentTime = 0;
            clearInterval(countdownTimer);
            document.getElementById('setupArea').style.display = 'block';
            document.getElementById('countdownBox').style.display = 'none';
            document.getElementById('alarmActiveBox').style.display = 'none';
        }

        window.onclick = function(e) {
            if (!e.target.closest('.custom-dropdown') && !e.target.closest('.tone-select-vip')) {
                document.querySelectorAll('.dropdown-menu').forEach(m => m.style.display = 'none');
            }
        }
    </script>
</body>
</html>
