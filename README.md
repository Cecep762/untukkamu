<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Untuk Kamu yang Spesial ❤️</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background: linear-gradient(to right, #ffecd2 0%, #fcb69f 100%);
            color: #333;
            text-align: center;
            overflow: hidden; /* Prevent scrollbar from appearing */
            position: relative;
        }

        .container {
            background-color: rgba(255, 255, 255, 0.9);
            padding: 40px 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            max-width: 500px;
            width: 90%;
            animation: fadeInScale 1s ease-out;
        }

        h1 {
            color: #e91e63;
            margin-bottom: 20px;
            font-size: 2.5em;
        }

        p {
            font-size: 1.1em;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .button-group {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }

        .button {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.2em;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        #yes-button {
            background-color: #4CAF50;
            color: white;
        }

        #yes-button:hover {
            background-color: #45a049;
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
        }

        #no-button {
            background-color: #f44336;
            color: white;
            position: relative; /* For dynamic positioning */
        }

        #no-button:hover {
            background-color: #da3329;
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
        }

        .heart-animation {
            position: absolute;
            background-color: #e91e63;
            transform: rotate(-45deg);
            animation: pulse 1.5s infinite;
        }
        .heart-animation::before,
        .heart-animation::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: #e91e63;
            border-radius: 50%;
        }
        .heart-animation::before {
            top: -50%;
            left: 0;
        }
        .heart-animation::after {
            top: 0;
            left: 50%;
        }

        @keyframes fadeInScale {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes pulse {
            0% { transform: scale(1) rotate(-45deg); opacity: 1; }
            50% { transform: scale(1.1) rotate(-45deg); opacity: 0.8; }
            100% { transform: scale(1) rotate(-45deg); opacity: 1; }
        }

        /* Animation for falling hearts */
        .falling-heart {
            position: absolute;
            top: -20px; /* Start above the screen */
            font-size: 2em;
            color: #e91e63;
            opacity: 0;
            animation: fall 5s linear infinite;
        }

        @keyframes fall {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Hai Kamu yang Spesial!</h1>
        <p>Ada sesuatu yang ingin aku sampaikan padamu...</p>
        <p>Sejak pertama kali aku mengenalmu, hari-hariku jadi lebih berwarna. Kamu itu lucu, baik, dan bikin aku nyaman banget.</p>
        <p>Mungkin ini terdengar klise, tapi aku beneran suka sama kamu. Dan aku pengen tau, apakah kamu juga merasakan hal yang sama?</p>
        <p><strong>Maukah kamu jadi pacarku?</strong></p>
        <div class="button-group">
            <button id="yes-button" class="button">Iya, Mau! ❤️</button>
            <button id="no-button" class="button">Nggak Mau</button>
        </div>
    </div>

    <script>
        const yesButton = document.getElementById('yes-button');
        const noButton = document.getElementById('no-button');
        const container = document.querySelector('.container');

        let noClickCount = 0;

        yesButton.addEventListener('click', () => {
            container.innerHTML = `
                <h1>YAY! Aku Senang Sekali! 🎉</h1>
                <p>Makasih banyak udah mau jadi bagian dari duniaku. Ini adalah hari terbaik!</p>
                <p>Aku janji akan selalu berusaha bikin kamu bahagia.</p>
                <p>Tunggu aku ya, aku langsung hubungi kamu! 🥰</p>
            `;
            container.style.backgroundColor = '#d4edda'; /* Light green for success */
            container.style.borderColor = '#28a745';
            createHearts(20); // Create more hearts on success
            stopNoButtonMovement(); // Stop any pending movement of the No button
        });

        noButton.addEventListener('mouseover', () => {
            if (noClickCount < 3) { // Make it move only a few times
                const maxX = window.innerWidth - noButton.offsetWidth;
                const maxY = window.innerHeight - noButton.offsetHeight;

                const randomX = Math.floor(Math.random() * maxX);
                const randomY = Math.floor(Math.random() * maxY);

                noButton.style.position = 'absolute';
                noButton.style.left = `${randomX}px`;
                noButton.style.top = `${randomY}px`;
            }
        });

        noButton.addEventListener('click', () => {
            noClickCount++;
            if (noClickCount === 1) {
                alert('Yakin nih? Coba pikir-pikir lagi deh...');
            } else if (noClickCount === 2) {
                alert('Aduh, jangan gitu dong... Sekali lagi deh, ya? 🙏');
            } else if (noClickCount === 3) {
                alert('Seriusan? Hati aku sakit nih... 💔 Masa iya sih nggak mau? Coba deh klik "Iya, Mau!"');
                noButton.style.display = 'none'; // Make it disappear
                // Optionally, make a small heart animation appear
                const heart = document.createElement('div');
                heart.classList.add('heart-animation');
                heart.style.width = '50px';
                heart.style.height = '50px';
                heart.style.position = 'absolute';
                heart.style.left = `${noButton.offsetLeft + noButton.offsetWidth / 2 - 25}px`;
                heart.style.top = `${noButton.offsetTop + noButton.offsetHeight / 2 - 25}px`;
                document.body.appendChild(heart);
                setTimeout(() => heart.remove(), 2000);
            } else {
                 // For more than 3 clicks, just keep it hidden
                 noButton.style.display = 'none';
            }
        });

        // Function to stop the No button from moving (if it's set to absolute position)
        function stopNoButtonMovement() {
            noButton.style.position = 'static'; // Reset to default positioning
        }

        // Falling hearts animation
        function createFallingHeart() {
            const heart = document.createElement('span');
            heart.classList.add('falling-heart');
            heart.innerHTML = '❤️'; // Or any other heart emoji or SVG
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 3 + 's'; // Between 3 and 6 seconds
            heart.style.opacity = '0'; // Start invisible
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, parseFloat(heart.style.animationDuration) * 1000);
        }

        function createHearts(numHearts) {
            for (let i = 0; i < numHearts; i++) {
                setTimeout(createFallingHeart, i * 200); // Stagger the appearance
            }
        }

        // Initial falling hearts
        createHearts(10);
        setInterval(() => createHearts(5), 5000); // Add new hearts periodically
    </script>
</body>
</html>
