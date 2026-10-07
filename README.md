# MYGAME
A RETRO GAME
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Retro Dodge Portal</title>
    <style>
        /* ==========================================
           1. สไตล์และโครงสร้างส่วนกลาง (General Styles)
           ========================================== */
        * {
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        /* ระบบสลับหน้าด้วย CSS (:target) */
        .page-wrapper {
            display: none; /* ซ่อนหน้าไว้เริ่มต้น */
            width: 100%;
            max-width: 450px;
            padding: 20px;
        }

        /* จัดการแสดงผลหน้าตาม URL Hash ที่เลือก */
        #home-page:target,
        #game-page:target {
            display: block;
        }

        /* กรณีเปิดมาครั้งแรก (ไม่มี Hash ใน URL) ให้แสดงหน้าแรก */
        :root:not(:has(:target)) #home-page {
            display: block;
        }

        /* ==========================================
           2. สไตล์สำหรับหน้าแรก (Home Page Styles)
           ========================================== */
        .card {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .card h1 {
            color: #333;
            margin-bottom: 10px;
        }

        .card p {
            color: #666;
            font-size: 16px;
            line-height: 1.5;
        }

        .btn {
            display: inline-block;
            margin-top: 15px;
            padding: 12px 24px;
            background-color: #007bff;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            font-weight: bold;
            transition: background 0.3s;
        }

        .btn:hover {
            background-color: #0056b3;
        }

        /* ==========================================
           3. สไตล์สำหรับหน้าเกม (Game Page Styles)
           ========================================== */
        .game-body-theme {
            background-color: #0b0c10;
            border: 4px solid #45f3ff;
            padding: 4px;
            border-radius: 8px;
            box-shadow: 0 0 20px rgba(69, 243, 255, 0.3);
            font-family: 'Courier New', Courier, monospace;
            color: #66fcf1;
            text-align: center;
        }

        .game-screen {
            background-color: #000000;
            border: 2px dashed #45f3ff;
            padding: 20px;
            min-height: 300px;
        }

        .game-title {
            font-size: 24px;
            font-weight: bold;
            color: #ffffff;
            margin-bottom: 20px;
            text-shadow: 2px 2px #ff0055;
        }

        .hud-display {
            display: flex;
            justify-content: space-between;
            background-color: #111;
            padding: 10px;
            margin-bottom: 15px;
            font-size: 14px;
        }

        .story-text {
            color: #ffffff;
            font-size: 14px;
            line-height: 1.6;
            margin: 20px 0;
        }

        .btn-arcade {
            display: block;
            width: 80%;
            margin: 10px auto;
            padding: 12px;
            background-color: #ff0055;
            color: white;
            text-decoration: none;
            font-weight: bold;
            border: 2px solid #ffffff;
            border-radius: 4px;
            box-shadow: 3px 3px 0px #990033;
            cursor: pointer;
        }

        .btn-arcade:hover {
            background-color: #ff3377;
            transform: translate(-1px, -1px);
            box-shadow: 4px 4px 0px #990033;
        }

        .btn-back {
            background-color: #444;
            box-shadow: 3px 3px 0px #222;
        }
        
        .btn-back:hover {
            background-color: #555;
            box-shadow: 4px 4px 0px #222;
        }
    </style>
</head>
<body>

    <!-- โครงสร้างหน้าแรก (Home Page) -->
    <div id="home-page" class="page-wrapper">
        <div class="card">
            <h1>ยินดีต้อนรับ!</h1>
            <p>นี่คือหน้าเว็บแบบ Single Page ที่รวมทุกหน้าไว้ในไฟล์เดียวกันด้วย HTML และ CSS คุณสามารถกดปุ่มด้านล่างเพื่อเข้าสู่หน้าเกมได้ทันที</p>
            <!-- ลิงก์สลับไปยังไอดีหน้าเกม -->
            <a href="#game-page" class="btn">เข้าเล่นเกม Retro Dodge</a>
        </div>
    </div>

    <!-- โครงสร้างหน้าเกม (Game Page) -->
    <div id="game-page" class="page-wrapper">
        <div class="game-body-theme">
            <div class="game-screen">
                <p style="margin: 0; font-size: 12px; color: #888;">NSTME Presents</p>
                <div class="game-title">RETRO DODGE</div>

                <!-- แสดงค่าคะแนนจำลองจากหลยหน้า -->
                <div class="hud-display">
                    <span>POINTS: 0</span>
                    <span>SCORE: 0</span>
                    <span>SPEED ×1</span>
                </div>

                <!-- ข้อความเนื้อเรื่อง -->
                <div class="story-text">
                    YEAR 20XX...<br>
                    THE CITY HAS FALLEN.<br>
                    UNKNOWN CREATURES HAVE APPEARED.<br>
                    <strong>YOU ARE THE LAST PILOT.</strong><br>
                    DODGE EVERYTHING IN YOUR PATH.
                </div>

                <!-- ปุ่มควบคุม -->
                <button class="btn-arcade" onclick="alert('เริ่มเกมตัวอย่าง!')">START GAME</button>
                <button class="btn-arcade" onclick="alert('ระบบร้านค้าเปิดเร็วๆ นี้')">SHOP SYSTEM</button>
                
                <!-- ลิงก์สลับกลับไปยังไอดีหน้าแรก -->
                <a href="#home-page" class="btn-arcade btn-back">BACK TO MAIN MENU</a>
            </div>
        </div>
    </div>

</body>
</html>
