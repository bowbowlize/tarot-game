<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>澤誼每日占星指引卡</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Noto Sans TC', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            width: 100%;
            text-align: center;
        }
        
        .header {
            margin-bottom: 40px;
        }
        
        .title {
            font-size: 2.5em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #ffd700, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: shimmer 3s ease-in-out infinite;
        }
        
        @keyframes shimmer {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.8; }
        }
        
        .subtitle {
            font-size: 1.2em;
            color: #b8c6db;
            margin-bottom: 20px;
        }
        
        .date-display {
            font-size: 1em;
            color: #ffd700;
            margin-bottom: 30px;
        }
        
        .card-area {
            perspective: 1000px;
            margin: 40px 0;
        }
        
        .card-back {
            width: 280px;
            height: 400px;
            margin: 0 auto;
            background: linear-gradient(145deg, #2c5aa0, #1e3a8a);
            border: 3px solid #ffd700;
            border-radius: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.6s ease;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        
        .card-back::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 25% 25%, rgba(255, 215, 0, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 75% 75%, rgba(255, 107, 107, 0.1) 0%, transparent 50%);
            pointer-events: none;
        }
        
        .card-back:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(255, 215, 0, 0.3);
        }
        
        .card-icon {
            font-size: 4em;
            margin-bottom: 20px;
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        .card-text {
            font-size: 1.3em;
            font-weight: bold;
            color: #ffd700;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }
        
        .card-revealed {
            width: 350px;
            background: linear-gradient(145deg, #ffffff, #f0f0f0);
            color: #333;
            border: 3px solid #ffd700;
            border-radius: 20px;
            padding: 30px;
            margin: 0 auto;
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
            animation: cardReveal 0.8s ease-out;
        }
        
        @keyframes cardReveal {
            from {
                opacity: 0;
                transform: rotateY(90deg) scale(0.8);
            }
            to {
                opacity: 1;
                transform: rotateY(0deg) scale(1);
            }
        }
        
        .card-energy {
            font-size: 1.4em;
            font-weight: bold;
            color: #1e3a8a;
            margin-bottom: 20px;
            border-bottom: 2px solid #ffd700;
            padding-bottom: 10px;
        }
        
        .card-content {
            text-align: left;
            line-height: 1.6;
        }
        
        .card-section {
            margin-bottom: 20px;
        }
        
        .card-section h4 {
            color: #2c5aa0;
            margin-bottom: 8px;
            font-size: 1.1em;
        }
        
        .card-section p {
            color: #555;
            font-size: 1em;
        }
        
        .zeyi-note {
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #333;
            padding: 15px;
            border-radius: 15px;
            margin-top: 20px;
            font-style: italic;
            box-shadow: 0 5px 15px rgba(255, 215, 0, 0.3);
        }
        
        .draw-button {
            background: linear-gradient(45deg, #ffd700, #ffb347);
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            margin: 30px 10px;
            transition: all 0.3s ease;
            color: #333;
            box-shadow: 0 5px 20px rgba(255, 215, 0, 0.4);
        }
        
        .draw-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 215, 0, 0.5);
        }
        
        .draw-button:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }
        
        .footer {
            margin-top: 50px;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            backdrop-filter: blur(10px);
        }
        
        .footer h3 {
            color: #ffd700;
            margin-bottom: 15px;
        }
        
        .footer p {
            color: #b8c6db;
            line-height: 1.6;
            margin-bottom: 10px;
        }
        
        .footer a {
            color: #4ecdc4;
            text-decoration: none;
        }
        
        .footer a:hover {
            color: #ffd700;
        }
        
        @media (max-width: 768px) {
            .title {
                font-size: 2em;
            }
            
            .card-back, .card-revealed {
                width: 90%;
                max-width: 300px;
            }
            
            .card-back {
                height: 350px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1 class="title">🌟 澤誼每日占星指引卡 🌟</h1>
            <p class="subtitle">讓宇宙的智慧指引你的每一天</p>
            <div class="date-display" id="dateDisplay"></div>
        </div>
        
        <div class="card-area">
            <div id="cardBack" class="card-back" onclick="drawCard()">
                <div class="card-icon">🔮</div>
                <div class="card-text">點擊抽取今日指引</div>
            </div>
            
            <div id="cardRevealed" class="card-revealed" style="display: none;">
                <div class="card-energy" id="cardEnergy"></div>
                <div class="card-content">
                    <div class="card-section">
                        <h4>當下的你：</h4>
                        <p id="currentState"></p>
                    </div>
                    <div class="card-section">
                        <h4>今日提醒：</h4>
                        <p id="dailyReminder"></p>
                    </div>
                    <div class="zeyi-note">
                        <strong>澤誼碎念：</strong><br>
                        <span id="zeyiNote"></span>
                    </div>
                </div>
            </div>
        </div>
        
        <button id="newCardBtn" class="draw-button" onclick="resetCard()" style="display: none;">
            重新抽卡 ✨
        </button>
        
        <div class="footer">
            <h3>關於澤誼</h3>
            <p>我是占星師、能量療癒師、催眠師、作家</p>
            <p>想了解更深層的占星智慧嗎？</p>
            <p><a href="https://fadaround.com/" target="_blank">預約澤誼的靈魂藍圖占星諮詢</a></p>
        </div>
    </div>

    <script>
        // 占星卡片資料庫
        const astrologyCards = [
            {
                energy: "太陽在牡羊座",
                current: "充滿行動力和開創精神，想要開始新的計畫",
                reminder: "相信自己的直覺，勇敢踏出第一步，但記得考慮他人感受",
                note: "有時候衝動不是壞事，是你的超能力 🔥"
            },
            {
                energy: "月亮在巨蟹座", 
                current: "情感特別敏感，容易被過去的回憶影響",
                reminder: "給自己一些溫柔的時間，照顧好內在的小孩",
                note: "家就是你的能量充電站，回家吧 🏠"
            },
            {
                energy: "水星逆行期間",
                current: "溝通容易出現誤解，計畫可能需要重新調整",
                reminder: "放慢腳步，仔細確認細節，避免簽署重要文件",
                note: "逆行不是詛咒，是宇宙叫你慢下來反思 ⏰"
            },
            {
                energy: "金星在天秤座",
                current: "對美感和和諧特別敏銳，人際關係是重點",
                reminder: "今天適合處理關係議題，用溫和的方式溝通",
                note: "美麗的事物會療癒你的心，去看看花吧 🌸"
            },
            {
                energy: "火星在天蠍座",
                current: "內在有股強烈的轉化能量，想要深度改變",
                reminder: "別急著做決定，先感受這股力量想帶你去哪裡",
                note: "有些傷口要撕開才能真正癒合，痛但值得 💪"
            },
            {
                energy: "木星帶來的擴張",
                current: "充滿樂觀和希望，看見更多可能性",
                reminder: "把握機會但不要過度樂觀，實際行動最重要",
                note: "幸運之神在你身邊，但他喜歡努力的人 🍀"
            },
            {
                energy: "土星的考驗時刻",
                current: "面臨現實的壓力，需要承擔更多責任",
                reminder: "這是成長的必經之路，堅持下去會有收穫",
                note: "土星是嚴格的老師，但教出來的學生最厲害 📚"
            },
            {
                energy: "天王星的突破",
                current: "渴望自由和改變，想要打破舊有模式",
                reminder: "改變是好的，但要考慮實際狀況，不要太激進",
                note: "有時候叛逆一下是必要的，做自己吧 ⚡"
            },
            {
                energy: "海王星的夢幻",
                current: "直覺力增強，容易受到靈感啟發",
                reminder: "相信直覺但保持清醒，不要被幻象迷惑",
                note: "夢想很美，但要記得回到現實執行 🌙"
            },
            {
                energy: "冥王星的深度轉化",
                current: "內在正在經歷深層的變化，舊的自己在死去",
                reminder: "接受轉變的痛苦，新的自己正在誕生",
                note: "鳳凰涅槃不是傳說，是你正在經歷的過程 🔥"
            },
            {
                energy: "新月許願時刻",
                current: "適合種下新的希望種子，設定新目標",
                reminder: "把願望寫下來，相信宇宙會幫助你實現",
                note: "許願不是迷信，是對未來的承諾 ✨"
            },
            {
                energy: "滿月釋放能量",
                current: "情緒達到高峰，適合釋放不需要的東西",
                reminder: "放下那些阻礙你的人事物，為新的開始騰出空間",
                note: "有時候放手比抓住更需要勇氣 🌕"
            }
        ];

        let hasDrawnToday = false;

        function updateDate() {
            const today = new Date();
            const options = { 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric',
                weekday: 'long'
            };
            document.getElementById('dateDisplay').textContent = 
                today.toLocaleDateString('zh-TW', options);
        }

        function drawCard() {
            if (hasDrawnToday) return;

            // 隨機選擇一張卡
            const randomIndex = Math.floor(Math.random() * astrologyCards.length);
            const card = astrologyCards[randomIndex];

            // 更新卡片內容
            document.getElementById('cardEnergy').textContent = card.energy;
            document.getElementById('currentState').textContent = card.current;
            document.getElementById('dailyReminder').textContent = card.reminder;
            document.getElementById('zeyiNote').textContent = card.note;

            // 顯示翻牌動畫
            const cardBack = document.getElementById('cardBack');
            const cardRevealed = document.getElementById('cardRevealed');
            const newCardBtn = document.getElementById('newCardBtn');

            cardBack.style.display = 'none';
            cardRevealed.style.display = 'block';
            newCardBtn.style.display = 'inline-block';

            hasDrawnToday = true;
        }

        function resetCard() {
            const cardBack = document.getElementById('cardBack');
            const cardRevealed = document.getElementById('cardRevealed');
            const newCardBtn = document.getElementById('newCardBtn');

            cardRevealed.style.display = 'none';
            cardBack.style.display = 'flex';
            newCardBtn.style.display = 'none';

            hasDrawnToday = false;
        }

        // 頁面載入時更新日期
        updateDate();
    </script>
</body>
</html>
