<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wesołych Świąt Wielkanocnych!</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f8ff;
            text-align: center;
            padding: 20px;
            color: #333;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #ff6b6b;
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        .wishes {
            font-size: 1.2em;
            line-height: 1.6;
            margin: 30px 0;
        }
        .images {
            display: flex;
            justify-content: center;
            margin: 30px 0;
            gap: 40px;
        }
        .image-container {
            position: relative;
            width: 200px;
            height: 200px;
            cursor: pointer;
            transition: transform 0.3s;
        }
        .image-container:hover {
            transform: scale(1.1);
        }
        .footer {
            margin-top: 30px;
            font-style: italic;
            color: #777;
        }
        .easter-eggs {
            margin-top: 20px;
        }
        .easter-egg {
            display: inline-block;
            width: 30px;
            height: 40px;
            border-radius: 50%;
            margin: 0 10px;
        }
        
        /* Style dla wyboru postaci */
        .character-selection {
            margin: 20px 0;
            padding: 15px;
            background-color: #fff5e6;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.05);
        }
        
        /* Style dla popupa */
        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0,0,0,0.3);
            z-index: 1000;
            max-width: 400px;
            animation: popIn 0.5s forwards;
        }
        
        .popup-content {
            font-size: 1.3em;
            margin-bottom: 20px;
        }
        
        .close-popup {
            background-color: #ff6b6b;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s;
        }
        
        .close-popup:hover {
            background-color: #ff5252;
        }
        
        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 999;
        }
        
        @keyframes popIn {
            0% {
                opacity: 0;
                transform: translate(-50%, -50%) scale(0.8);
            }
            100% {
                opacity: 1;
                transform: translate(-50%, -50%) scale(1);
            }
        }
        
        /* Style dla przycisków wyboru */
        .character-button {
            background-color: #e0f7fa;
            border: 2px solid #b2ebf2;
            border-radius: 8px;
            padding: 10px 20px;
            margin: 0 10px;
            cursor: pointer;
            font-size: 1.1em;
            transition: all 0.3s;
        }
        
        .character-button:hover {
            background-color: #b2ebf2;
            transform: scale(1.05);
        }
        
        .character-button.active {
            background-color: #4dd0e1;
            color: white;
            border-color: #00acc1;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Wesołych Świąt Wielkanocnych!</h1>
        
        <div class="wishes">
            <p>Z okazji Świąt Wielkanocnych składam najserdeczniejsze życzenia:</p>
            <p>Dużo zdrowia, radości, smacznego jajka, mokrego dyngusa,<br>
            mnóstwo wiosennego słońca i samych szczęśliwych dni!</p>
        </div>
        
        <div class="character-selection">
            <p>Wybierz swojego wielkanocnego przyjaciela:</p>
            <button id="cat-button" class="character-button active">Kot Wielkanocny</button>
            <button id="bunny-button" class="character-button">Zajączek Wielkanocny</button>
        </div>
        
        <div class="images">
            <div id="cat-container" class="image-container" onclick="showPopup('cat')">
                <!-- Kot wielkanocny - SVG -->
                <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
                    <!-- Tło -->
                    <circle cx="100" cy="100" r="80" fill="#ffefcc" />
                    
                    <!-- Ciało kota -->
                    <ellipse cx="100" cy="110" rx="50" ry="60" fill="#777" />
                    
                    <!-- Głowa kota -->
                    <circle cx="100" cy="70" r="40" fill="#777" />
                    
                    <!-- Uszy -->
                    <polygon points="70,45 80,10 90,45" fill="#777" />
                    <polygon points="130,45 120,10 110,45" fill="#777" />
                    
                    <!-- Wewnętrzne uszy -->
                    <polygon points="75,45 80,20 85,45" fill="#ffb6c1" />
                    <polygon points="125,45 120,20 115,45" fill="#ffb6c1" />
                    
                    <!-- Oczy -->
                    <ellipse cx="80" cy="65" rx="8" ry="12" fill="white" />
                    <ellipse cx="120" cy="65" rx="8" ry="12" fill="white" />
                    
                    <!-- Źrenice -->
                    <ellipse cx="80" cy="65" rx="3" ry="8" fill="black" />
                    <ellipse cx="120" cy="65" rx="3" ry="8" fill="black" />
                    
                    <!-- Nos -->
                    <polygon points="95,80 100,85 105,80" fill="#ffb6c1" />
                    
                    <!-- Wąsy -->
                    <line x1="105" y1="83" x2="140" y2="75" stroke="black" stroke-width="1" />
                    <line x1="105" y1="85" x2="140" y2="85" stroke="black" stroke-width="1" />
                    <line x1="105" y1="87" x2="140" y2="95" stroke="black" stroke-width="1" />
                    
                    <line x1="95" y1="83" x2="60" y2="75" stroke="black" stroke-width="1" />
                    <line x1="95" y1="85" x2="60" y2="85" stroke="black" stroke-width="1" />
                    <line x1="95" y1="87" x2="60" y2="95" stroke="black" stroke-width="1" />
                    
                    <!-- Pisanka wielkanocna w łapce -->
                    <ellipse cx="130" cy="140" rx="15" ry="25" fill="#ff6b6b" />
                    <path d="M120,125 Q130,120 140,125" stroke="#fff" stroke-width="2" fill="none" />
                    <path d="M120,135 Q130,130 140,135" stroke="#fff" stroke-width="2" fill="none" />
                    <path d="M120,145 Q130,140 140,145" stroke="#fff" stroke-width="2" fill="none" />
                    <path d="M120,155 Q130,150 140,155" stroke="#fff" stroke-width="2" fill="none" />
                </svg>
            </div>
            
            <div id="bunny-container" class="image-container" onclick="showPopup('bunny')" style="display: none;">
                <!-- Zajączek wielkanocny - SVG -->
                <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
                    <!-- Tło -->
                    <circle cx="100" cy="100" r="80" fill="#e6f7ff" />
                    
                    <!-- Ciało zajączka -->
                    <ellipse cx="100" cy="120" rx="40" ry="50" fill="#f9f9f9" />
                    
                    <!-- Głowa zajączka -->
                    <circle cx="100" cy="70" r="35" fill="#f9f9f9" />
                    
                    <!-- Uszy -->
                    <ellipse cx="75" cy="25" rx="12" ry="30" fill="#f9f9f9" />
                    <ellipse cx="125" cy="25" rx="12" ry="30" fill="#f9f9f9" />
                    
                    <!-- Wewnętrzne uszy -->
                    <ellipse cx="75" cy="25" rx="6" ry="20" fill="#ffb6c1" />
                    <ellipse cx="125" cy="25" rx="6" ry="20" fill="#ffb6c1" />
                    
                    <!-- Oczy -->
                    <circle cx="85" cy="65" r="5" fill="white" />
                    <circle cx="115" cy="65" r="5" fill="white" />
                    
                    <!-- Źrenice -->
                    <circle cx="85" cy="65" r="2" fill="black" />
                    <circle cx="115" cy="65" r="2" fill="black" />
                    
                    <!-- Nos -->
                    <ellipse cx="100" cy="75" rx="7" ry="5" fill="#ffb6c1" />
                    
                    <!-- Wąsy -->
                    <line x1="107" y1="75" x2="130" y2="70" stroke="black" stroke-width="1" />
                    <line x1="107" y1="77" x2="130" y2="77" stroke="black" stroke-width="1" />
                    <line x1="107" y1="79" x2="130" y2="84" stroke="black" stroke-width="1" />
                    
                    <line x1="93" y1="75" x2="70" y2="70" stroke="black" stroke-width="1" />
                    <line x1="93" y1="77" x2="70" y2="77" stroke="black" stroke-width="1" />
                    <line x1="93" y1="79" x2="70" y2="84" stroke="black" stroke-width="1" />
                    
                    <!-- Koszyk z jajkami -->
                    <path d="M70,130 Q100,150 130,130" stroke="#a67c52" stroke-width="5" fill="none" />
                    <ellipse cx="100" cy="140" rx="30" ry="10" fill="#a67c52" />
                    
                    <!-- Pisanki w koszyku -->
                    <ellipse cx="90" cy="135" rx="8" ry="10" fill="#9ceaef" />
                    <ellipse cx="110" cy="135" rx="8" ry="10" fill="#ffb6c1" />
                    <ellipse cx="100" cy="132" rx="8" ry="10" fill="#b5e550" />
                </svg>
            </div>
        </div>
        
        <div class="easter-eggs">
            <div class="easter-egg" style="background-color: #ff6b6b;"></div>
            <div class="easter-egg" style="background-color: #9ceaef;"></div>
            <div class="easter-egg" style="background-color: #b5e550;"></div>
            <div class="easter-egg" style="background-color: #ffb6c1;"></div>
            <div class="easter-egg" style="background-color: #e6f7ff;"></div>
        </div>
        
        <div class="footer">
            <p>Wesołego Alleluja!</p>
        </div>
    </div>
    
    <!-- Overlay dla popupa -->
    <div id="overlay" class="overlay"></div>
    
    <!-- Popup dla kota -->
    <div id="cat-popup" class="popup">
        <div class="popup-content">
            <p>Miauczy kot: "Wesołego Alleluja! Wielkanoc to mój ulubiony czas - mogę polować na kolorowe pisanki zamiast na myszy. Miau-leluja!" 😺🥚</p>
        </div>
        <button class="close-popup" onclick="closePopup()">Zamknij</button>
    </div>
    
    <!-- Popup dla zajączka -->
    <div id="bunny-popup" class="popup">
        <div class="popup-content">
            <p>Hop! Hop! Zajączek mówi: "Czy wiesz, że zajęcie malowania tylu pisanek jest bardzo... zajmujące? Wesołego Dyngusa! Tylko nie mocz mi futerka!" 🐰💦</p>
        </div>
        <button class="close-popup" onclick="closePopup()">Zamknij</button>
    </div>
    
    <script>
        // Funkcja pokazująca popup
        function showPopup(character) {
            document.getElementById('overlay').style.display = 'block';
            if (character === 'cat') {
                document.getElementById('cat-popup').style.display = 'block';
            } else if (character === 'bunny') {
                document.getElementById('bunny-popup').style.display = 'block';
            }
        }
        
        // Funkcja zamykająca popup
        function closePopup() {
            document.getElementById('overlay').style.display = 'none';
            document.getElementById('cat-popup').style.display = 'none';
            document.getElementById('bunny-popup').style.display = 'none';
        }
        
        // Przełączanie między kotem a zajączkiem
        document.getElementById('cat-button').addEventListener('click', function() {
            document.getElementById('cat-container').style.display = 'block';
            document.getElementById('bunny-container').style.display = 'none';
            document.getElementById('cat-button').classList.add('active');
            document.getElementById('bunny-button').classList.remove('active');
        });
        
        document.getElementById('bunny-button').addEventListener('click', function() {
            document.getElementById('cat-container').style.display = 'none';
            document.getElementById('bunny-container').style.display = 'block';
            document.getElementById('bunny-button').classList.add('active');
            document.getElementById('cat-button').classList.remove('active');
        });
        
        // Zamykanie popupa po kliknięciu w overlay
        document.getElementById('overlay').addEventListener('click', closePopup);
    </script>
</body>
</html>
