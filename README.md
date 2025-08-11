
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 당첨번호</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;800;900&display=swap');

        /* 공통 스타일 */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #1a202c;
            color: #e2e8f0;
            padding: 2rem;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            flex-wrap: wrap;
        }

        .container {
            width: 100%;
            max-width: 1280px;
            display: flex;
            flex-direction: column;
            gap: 2rem;
        }

        .main-content {
            display: flex;
            flex-direction: column;
            gap: 2rem;
            flex: 1;
        }
        
        .main-display,
        .mini-game,
        .sidebar,
        .historical-data {
            background-color: #2d3748;
            border-radius: 1.5rem;
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
            padding: 2.5rem;
            border: 4px solid #f6e05e;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .sidebar, .historical-data {
            border: 4px solid #4a5568;
        }

        .title {
            font-size: 3rem;
            font-weight: 800;
            color: #f6e05e;
            text-align: center;
            margin-bottom: 1.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
        }

        .subtitle {
            font-size: 2.25rem;
            font-weight: 700;
            color: #cbd5e0;
            margin-bottom: 2rem;
        }
        
.subtitle span {
            color: #f6e05e;
        }

        .numbers-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            background-color: #4a5568;
            border-radius: 0.75rem;
            box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
            min-height: 5rem;
        }

        .ball {
            width: 4rem;
            height: 4rem;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 9999px;
            color: white;
            font-weight: 800;
            font-size: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
            transition: transform 0.2s ease-in-out;
            cursor: default;
            position: relative;
            animation: drop 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55) forwards;
            opacity: 0;
        }

        /* 공이 위에서 아래로 떨어지는 애니메이션 */
        @keyframes drop {
            0% {
                transform: translateY(-100px) scale(0);
                opacity: 0;
            }
            100% {
                transform: translateY(0) scale(1);
                opacity: 1;
            }
        }
        
        .ball:hover {
            transform: scale(1.1);
        }

        /* 로또 공 색상 스타일 */
        .ball-yellow { background-color: #f6e05e; }
        .ball-blue { background-color: #4299e1; }
        .ball-red { background-color: #f56565; }
        .ball-gray { background-color: #a0aec0; }
        .ball-green { background-color: #48bb78; }

        .plus-sign {
            font-size: 1.875rem;
            color: #a0aec0;
            font-weight: 700;
            margin: 0 0.5rem;
        }

        .sidebar-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: #cbd5e0;
            margin-bottom: 1rem;
            text-align: center;
        }

        .lotto-list {
            list-style: none;
            padding: 0;
            margin: 0;
            max-height: 24rem;
            overflow-y: auto;
            width: 100%;
        }

        .lotto-item {
            padding: 0.75rem;
            border-radius: 0.75rem;
            cursor: pointer;
            transition: all 0.2s ease-in-out;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #4a5568;
            margin-bottom: 0.5rem;
        }
        
        .lotto-item:hover {
            transform: scale(1.03);
            background-color: #374151;
        }

        .lotto-item.selected {
            background-color: #2b6cb0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }

        .lotto-item-title {
            font-size: 1.125rem;
            font-weight: 600;
        }

        .small-ball-container {
            display: flex;
            gap: 0.25rem;
            align-items: center;
        }

        .small-ball {
            width: 1.5rem;
            height: 1.5rem;
            line-height: 1.5rem;
            text-align: center;
            border-radius: 9999px;
            color: white;
            font-weight: 700;
            font-size: 0.75rem;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
            flex-shrink: 0;
        }

        .mini-game-description {
            font-size: 1.125rem;
            color: #cbd5e0;
            text-align: center;
            margin-bottom: 1.5rem;
        }

        .generate-button {
            padding: 1rem 2rem;
            border-radius: 9999px;
            background-color: #f6e05e;
            color: #1a202c;
            font-weight: 800;
            font-size: 1.25rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease-in-out;
            border: none;
            cursor: pointer;
        }

        .generate-button:hover {
            transform: scale(1.05);
            background-color: #ecc94b;
        }
        
        .generate-button:active {
            transform: scale(0.95);
        }
        
        .historical-list {
            list-style: none;
            padding: 0;
            margin: 0;
            max-height: 24rem;
            overflow-y: auto;
            width: 100%;
        }

        @media (min-width: 768px) {
            .container {
                flex-direction: row;
                gap: 2rem;
            }
            
            .main-content {
                flex: 1;
            }
            
            .sidebar-container {
                display: flex;
                flex-direction: column;
                gap: 2rem;
                width: 33.333%;
                max-width: 400px;
                flex-shrink: 0;
            }

            .ball {
                width: 5rem;
                height: 5rem;
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- 메인 콘텐츠 영역 -->
        <div class="main-content">
            <div id="main-display" class="main-display">
                <!-- 여기에 메인 당첨번호가 렌더링됩니다 -->
            </div>
            <!-- 미니게임 영역 -->
            <div id="mini-game" class="mini-game">
                <!-- 여기에 미니게임이 렌더링됩니다 -->
            </div>
        </div>

        <!-- 사이드바와 과거 데이터 컨테이너 -->
        <div class="sidebar-container">
            <!-- 회차 목록 사이드바 -->
            <div id="sidebar" class="sidebar">
                <h2 class="sidebar-title">최근 20회차</h2>
                <ul id="lotto-list" class="lotto-list">
                    <!-- 여기에 회차 목록이 렌더링됩니다 -->
                </ul>
            </div>
            <!-- 과거 당첨번호 영역 -->
            <div id="historical-data" class="historical-data">
                <!-- 여기에 과거 당첨번호가 렌더링됩니다 -->
            </div>
        </div>
    </div>

    <script>
        // 로또 당첨번호 데이터
        const lottoData = [
          { draw: 1133, numbers: [11, 22, 23, 24, 30, 39], bonus: 19 },
          { draw: 1132, numbers: [1, 13, 22, 30, 33, 40], bonus: 18 },
          { draw: 1131, numbers: [5, 6, 21, 24, 39, 40], bonus: 36 },
          { draw: 1130, numbers: [14, 25, 29, 32, 33, 39], bonus: 16 },
          { draw: 1129, numbers: [1, 6, 12, 17, 26, 39], bonus: 15 },
          { draw: 1128, numbers: [15, 17, 24, 28, 41, 42], bonus: 26 },
          { draw: 1127, numbers: [10, 16, 21, 22, 30, 41], bonus: 37 },
          { draw: 1126, numbers: [2, 7, 10, 16, 26, 36], bonus: 32 },
          { draw: 1125, numbers: [11, 13, 14, 23, 31, 36], bonus: 45 },
          { draw: 1124, numbers: [12, 17, 25, 30, 32, 45], bonus: 39 },
          { draw: 1123, numbers: [1, 10, 15, 26, 32, 38], bonus: 29 },
          { draw: 1122, numbers: [8, 12, 13, 20, 39, 40], bonus: 19 },
          { draw: 1121, numbers: [6, 14, 18, 22, 32, 43], bonus: 4 },
          { draw: 1120, numbers: [13, 18, 22, 24, 30, 32], bonus: 2 },
          { draw: 1119, numbers: [1, 4, 29, 39, 43, 45], bonus: 35 },
          { draw: 1118, numbers: [3, 11, 15, 29, 35, 38], bonus: 28 },
          { draw: 1117, numbers: [1, 3, 9, 21, 38, 45], bonus: 30 },
          { draw: 1116, numbers: [2, 8, 19, 22, 30, 33], bonus: 28 },
          { draw: 1115, numbers: [13, 23, 24, 34, 35, 41], bonus: 42 },
          { draw: 1114, numbers: [1, 7, 10, 22, 31, 35], bonus: 44 },
        ];

        // 950회부터 1113회까지의 과거 당첨번호 (예시 데이터)
        const historicalLottoData = [
            { draw: 1113, numbers: [3, 13, 30, 33, 43, 45] },
            { draw: 1100, numbers: [1, 5, 12, 15, 17, 26] },
            { draw: 1050, numbers: [11, 15, 28, 30, 38, 45] },
            { draw: 1000, numbers: [2, 10, 13, 17, 23, 27] },
            { draw: 950, numbers: [1, 17, 30, 34, 35, 36] }
        ];

        // 상태 변수
        let selectedDraw = lottoData[0];
        let generatedNumbers = [];

        // 로또 번호 공의 색상을 결정하는 함수
        const getBallColorClass = (number) => {
            if (number <= 10) return 'ball-yellow';
            if (number <= 20) return 'ball-blue';
            if (number <= 30) return 'ball-red';
            if (number <= 40) return 'ball-gray';
            return 'ball-green';
        };

        // 메인 당첨번호를 렌더링하는 함수
        const renderMainDisplay = () => {
            const mainDisplayEl = document.getElementById('main-display');
            
            const numbersHtml = selectedDraw.numbers.map(num => `
                <div class="ball ${getBallColorClass(num)}">${num}</div>
            `).join('');

            const bonusHtml = `<div class="plus-sign">+</div><div class="ball ${getBallColorClass(selectedDraw.bonus)}">${selectedDraw.bonus}</div>`;

            mainDisplayEl.innerHTML = `
                <h1 class="title">로또 당첨번호</h1>
                <h2 class="subtitle"><span>${selectedDraw.draw}</span>회</h2>
                <div class="numbers-container">
                    ${numbersHtml}
                    ${bonusHtml}
                </div>
            `;
        };

        // 회차 목록 사이드바를 렌더링하는 함수 (번호 보이도록 수정)
        const renderSidebar = () => {
            const lottoListEl = document.getElementById('lotto-list');
            lottoListEl.innerHTML = lottoData.map(item => {
                const isSelected = item.draw === selectedDraw.draw;
                const selectedClass = isSelected ? 'selected' : '';
                
                const smallBallsHtml = item.numbers.map(num => `
                    <span class="small-ball ${getBallColorClass(num)}">${num}</span>
                `).join('');

                return `
                    <li class="lotto-item ${selectedClass}" onclick="handleSelectDraw(${item.draw})">
                        <span class="lotto-item-title">${item.draw}회</span>
                        <div class="small-ball-container">
                            ${smallBallsHtml}
                        </div>
                    </li>
                `;
            }).join('');
        };
        
        // 미니게임 영역을 렌더링하는 함수
        const renderMiniGame = () => {
            const miniGameEl = document.getElementById('mini-game');
            const generatedNumbersContainer = document.createElement('div');
            generatedNumbersContainer.id = 'generated-numbers';
            generatedNumbersContainer.className = 'numbers-container';

            // 기존 내용을 비우고 새로운 번호 공을 생성합니다.
            miniGameEl.innerHTML = `
                <h2 class="title">로또번호 대포</h2>
                <p class="mini-game-description">
                    버튼을 눌러 나만의 행운 번호 6개를 뽑아보세요!
                </p>
                <button class="generate-button" onclick="generateRandomNumbers()">
                    번호 발사!
                </button>
            `;
            miniGameEl.appendChild(generatedNumbersContainer);

            // 각 번호에 애니메이션을 적용합니다.
            generatedNumbers.forEach((num, index) => {
                const ballEl = document.createElement('div');
                ballEl.className = `ball ${getBallColorClass(num)}`;
                ballEl.textContent = num;
                ballEl.style.animationDelay = `${index * 0.1}s`; // 공이 순차적으로 떨어지도록 딜레이 적용
                generatedNumbersContainer.appendChild(ballEl);
            });
        };

        // 과거 당첨번호 영역을 렌더링하는 함수
        const renderHistoricalData = () => {
            const historicalDataEl = document.getElementById('historical-data');
            
            const historicalListHtml = historicalLottoData.map(item => {
                const smallBallsHtml = item.numbers.map(num => `
                    <span class="small-ball ${getBallColorClass(num)}">${num}</span>
                `).join('');
                
                return `
                    <li class="lotto-item">
                        <span class="lotto-item-title">${item.draw}회</span>
                        <div class="small-ball-container">
                            ${smallBallsHtml}
                        </div>
                    </li>
                `;
            }).join('');

            historicalDataEl.innerHTML = `
                <h2 class="sidebar-title">과거 당첨번호 (950회 ~ 1113회)</h2>
                <ul class="historical-list">
                    ${historicalListHtml}
                </ul>
            `;
        };

        // 회차 선택 이벤트 핸들러
        window.handleSelectDraw = (drawNumber) => {
            selectedDraw = lottoData.find(item => item.draw === drawNumber);
            renderMainDisplay();
            renderSidebar();
        };

        // 로또 번호를 랜덤으로 생성하는 함수
        window.generateRandomNumbers = () => {
            const numbers = Array.from({ length: 45 }, (_, i) => i + 1);
            // Fisher-Yates shuffle 알고리즘을 사용해 번호를 섞음
            for (let i = numbers.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [numbers[i], numbers[j]] = [numbers[j], numbers[i]];
            }
            generatedNumbers = numbers.slice(0, 6).sort((a, b) => a - b);
            renderMiniGame();
        };
        
        // 페이지 로드 시 초기 렌더링
        window.onload = () => {
            renderMainDisplay();
            renderSidebar();
            renderMiniGame();
            renderHistoricalData();
        };
    </script>
</body>
</html>
