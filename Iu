<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gửi người phụ nữ tuyệt vời nhất - 20/10</title>
    
    <style>
        body {
            background-color: #fce4ec;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            flex-direction: column; 
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            overflow: hidden; 
        }

        /* --- Nút nhấn ban đầu --- */
        .open-button {
            cursor: pointer;
            padding: 20px 40px;
            background-color: #ff80ab;
            color: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(255, 128, 171, 0.4);
            transition: transform 0.3s, opacity 0.3s;
            text-align: center;
        }

        .open-button:hover {
            transform: scale(1.05);
            background-color: #ff4d94;
        }
        
        .flower-icon {
            font-size: 40px;
            display: block;
            margin-bottom: 5px;
        }

        /* --- Thiệp chúc mừng --- */
        .card {
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            padding: 30px;
            width: 90%;
            max-width: 500px;
            text-align: center;
            border: 5px solid #ff80ab;
            opacity: 0; 
            transform: scale(0.8); 
            transition: opacity 1s ease-out, transform 1s ease-out;
            position: absolute; 
            visibility: hidden; 
            display: flex; /* Bật flex cho thẻ cha */
            flex-direction: column;
            align-items: center;
        }

        /* Lớp sẽ được thêm vào bằng JavaScript để hiện thiệp */
        .card.is-active {
            opacity: 1;
            transform: scale(1);
            visibility: visible;
            position: relative; /* Trở lại flow bình thường */
        }

        .main-heart {
            color: #ff4d94;
            font-size: 50px;
            margin-bottom: 15px;
            display: inline-block;
            animation: pulse 1.5s infinite alternate;
        }

        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.1); }
        }

        h1 { color: #d81b60; font-size: 28px; margin-top: 0; border-bottom: 2px solid #ffcdd2; padding-bottom: 10px; width: 100%; }
        p { color: #4a4a4a; font-size: 16px; line-height: 1.6; margin-bottom: 20px; }
        .signature { margin-top: 25px; font-style: italic; color: #888; font-size: 14px; }

        /* --- Trái tim bay (Animation) --- */
        .heart {
            position: absolute;
            color: #ff4d94;
            font-size: 20px;
            animation: flyUp 5s ease-out forwards;
            pointer-events: none; 
            z-index: 10;
            text-shadow: 0 0 5px rgba(255, 255, 255, 0.8);
        }

        @keyframes flyUp {
            0% {
                opacity: 1;
                transform: translateY(0) rotate(0deg);
            }
            100% {
                opacity: 0;
                /* Bay lên cao, xoay và lệch sang ngang ngẫu nhiên */
                transform: translateY(-800px) rotate(720deg) translateX(var(--random-x)); 
            }
        }

        /* --- Nút Quà Tặng (Thanh Ngang) --- */
        .gift-bar-button {
            width: 90%; /* Chiều rộng gần bằng thiệp */
            max-width: 400px; /* Độ rộng tối đa */
            background-color: #4CAF50; /* Màu xanh lá cây */
            color: white;
            padding: 15px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            margin-top: 25px;
            font-weight: bold;
            font-size: 18px;
            transition: background-color 0.3s, transform 0.3s;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            z-index: 1; /* Đảm bảo nó nằm trên các thành phần khác */
        }

        .gift-bar-button:hover {
            background-color: #45a049;
            transform: translateY(-2px);
        }

        .gift-message {
            margin-top: 15px;
            padding: 10px;
            font-size: 18px;
            font-weight: bold;
            color: #d81b60;
            background-color: #ffe0f6; /* Nền nhẹ cho tin nhắn */
            border-radius: 5px;
            opacity: 0;
            transition: opacity 1s ease-in;
            text-align: center;
        }

        .gift-message.show {
            opacity: 1;
        }
    </style>
</head>
<body>

    <div class="open-button" id="openCardButton">
        <span class="flower-icon">🌸</span>
        <p>Nhấn vào đây để mở thiệp!</p>
    </div>

    <div class="card" id="greetingCard">
        <span class="main-heart">❤️</span>
        <h1>Chúc Mừng Ngày 20/10</h1>
        
        <p>Gửi đến Em - người phụ nữ tuyệt vời nhất,</p>
        
        <p>Chúc mừng em nhân ngày 20/10! Anh không hứa sẽ mang lại mọi điều tốt đẹp trên đời, nhưng anh hứa sẽ luôn ở bên, yêu thương và làm em hạnh phúc mỗi ngày. Mãi là công chúa của anh nhé!.</p>

        <p class="signature">Thân gửi,<br>Người luôn yêu Thương Em</p>

        <button class="gift-bar-button" id="surpriseGiftButton">
            Bấm vào đây để nhận MÓN QUÀ BẤT NGỜ! 🎁😗
        </button>

        <div class="gift-message" id="giftMessage">
            "Em xứng đáng nhận được tất cả những điều tốt đẹp nhất trên đời này. Nhất Là Được Iu Anh Này 😗!"
        </div>
    </div>

    <div class="hearts-container" id="heartsContainer"></div>

    <script>
        const button = document.getElementById('openCardButton');
        const card = document.getElementById('greetingCard');
        const heartsContainer = document.getElementById('heartsContainer');
        const surpriseButton = document.getElementById('surpriseGiftButton');
        const giftMessage = document.getElementById('giftMessage');

        // Logic Mở Thiệp và Trái Tim Bay
        button.addEventListener('click', () => {
            // 1. Ẩn nút nhấn
            button.style.opacity = '0';
            setTimeout(() => {
                button.style.display = 'none';
                card.style.position = 'relative'; // Đảm bảo thiệp chiếm không gian sau khi nút ẩn
            }, 300); 

            // 2. Hiện thiệp
            card.classList.add('is-active');

            // 3. Tạo hiệu ứng trái tim bay
            generateHearts(50); 
        });

        // Logic Món Quà Bất Ngờ (Thanh Ngang)
        surpriseButton.addEventListener('click', () => {
            // Hiện tin nhắn
            giftMessage.classList.add('show');
            // Tùy chọn: Vô hiệu hóa nút sau khi bấm
            surpriseButton.disabled = true;
            surpriseButton.textContent = "Bạn đã nhận quà rồi! ❤️";
            surpriseButton.style.backgroundColor = "#ff4d94"; // Đổi màu sau khi bấm
        });

        function generateHearts(count) {
            for (let i = 0; i < count; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = '💖'; 

                // Đặt vị trí xuất phát ngẫu nhiên gần khu vực thiệp
                const startX = window.innerWidth / 2 + (Math.random() - 0.5) * 100;
                const startY = window.innerHeight / 2 + (Math.random() - 0.5) * 100;
                
                heart.style.left = `${startX}px`;
                heart.style.top = `${startY}px`;

                // Tạo biến CSS ngẫu nhiên để trái tim bay lệch hướng khác nhau
                const randomXOffset = (Math.random() - 0.5) * 300; 
                heart.style.setProperty('--random-x', `${randomXOffset}px`);
                
                // Kích thước và độ trễ ngẫu nhiên
                heart.style.fontSize = `${15 + Math.random() * 20}px`; 
                heart.style.animationDelay = `${Math.random() * 2}s`;

                heartsContainer.appendChild(heart);
                
                // Xóa trái tim sau khi bay xong để giữ cho DOM gọn gàng
                heart.addEventListener('animationend', () => {
                    heart.remove();
                });
            }
        }
    </script>
</body>
</html>
