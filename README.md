<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Do You LOVE Me?</title>
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
        background: radial-gradient(ellipse at bottom, #1B2735 0%, #090A0F 100%); /* Dark background */
    }
    .question {
        font-size: 48px;
        margin-top: 50px;
        color: #fff;
    }
    .options {
        margin-top: 20px;
    }
    .option-button {
        font-size: 36px;
        padding: 20px 40px;
        margin: 20px;
        cursor: pointer;
        border: none;
        border-radius: 50%;
        position: relative;
        overflow: hidden;
    }
    .option-yes {
        background-color: #ff6f61; /* Red */
        color: white;
    }
    .option-no {
        background-color: #ffaaaa; /* Light Red */
        color: white;
    }
    .heart {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        opacity: 0.5;
        pointer-events: none;
    }
    .star {
        position: absolute;
        width: 2px;
        height: 2px;
        background-color: #fff;
        border-radius: 50%;
        animation: twinkle 2s infinite alternate;
    }
    @keyframes twinkle {
        0% {
            opacity: 0;
        }
        100% {
            opacity: 1;
        }
    }
</style>
</head>
<body>

<div class="question">Do You LOVE Me? 💖</div>
<div class="options">
    <button class="option-button option-yes" onclick="handleOption('yes')">Yes 😍</button>
    <button class="option-button option-no" onclick="handleOption('no')">No 😔</button>
    <img class="heart" src="https://emojicdn.elk.sh/❤️" alt="Heart">
    <div class="stars"></div>
</div>

<script>
    let clicked = false;
    function handleOption(option) {
        if (option === 'no') {
            let noButton = document.querySelector('.options .option-no');
            noButton.style.display = 'none';

            let yesButton = document.querySelector('.options .option-yes');
            let newNoButton = document.createElement('button');
            newNoButton.className = 'option-button option-no';
            newNoButton.textContent = 'No 😔';
            newNoButton.onclick = function() {
                noButton.style.display = 'block';
                this.remove();
            };
            randomizePosition(newNoButton);
            yesButton.parentNode.insertBefore(newNoButton, yesButton);
        } else if (option === 'yes') {
            let container = document.querySelector('.options');
            container.innerHTML = '<div style="font-size: 72px; color: white; margin-top: 100px;">Love u too! 💖😘</div>';
        }
    }

    function randomizePosition(element) {
        let maxWidth = window.innerWidth - 300; // Width of the viewport minus button width
        let maxHeight = window.innerHeight - 300; // Height of the viewport minus button height
        let randomX = Math.floor(Math.random() * maxWidth);
        let randomY = Math.floor(Math.random() * maxHeight);
        element.style.left = randomX + 'px';
        element.style.top = randomY + 'px';
    }

    // Generate random stars
    const starsContainer = document.querySelector('.stars');
    for (let i = 0; i < 50; i++) {
        const star = document.createElement('div');
        star.className = 'star';
        star.style.left = Math.random() * 100 + '%';
        star.style.top = Math.random() * 100 + '%';
        starsContainer.appendChild(star);
    }
</script>

</body>
</html>
