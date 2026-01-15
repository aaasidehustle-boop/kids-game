# kids-game
Educational kids game
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Tap the Animal!</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(#87CEEB, #ffffff);
        text-align: center;
        margin: 0;
        padding: 20px;
    }

    h1 {
        font-size: 2.5em;
        color: #ff6600;
    }

    #animal {
        font-size: 120px;
        cursor: pointer;
        margin: 40px 0;
        transition: transform 0.2s;
    }

    #animal:active {
        transform: scale(1.2);
    }

    #message {
        font-size: 1.8em;
        color: #008000;
    }

    button {
        font-size: 1.5em;
        padding: 15px 30px;
        border-radius: 15px;
        border: none;
        background-color: #ffcc00;
        cursor: pointer;
        margin-top: 20px;
    }

    button:hover {
        background-color: #ffdd33;
    }
</style>
</head>

<body>

<h1>🐾 Tap the Animal!</h1>

<div id="animal">🐶</div>

<div id="message">Tap the animal!</div>

<button onclick="nextAnimal()">Next</button>

<script>
    const animals = [
        { emoji: "🐶", name: "Dog", sound: "Woof!" },
        { emoji: "🐱", name: "Cat", sound: "Meow!" },
        { emoji: "🐮", name: "Cow", sound: "Moo!" },
        { emoji: "🐷", name: "Pig", sound: "Oink!" },
        { emoji: "🐔", name: "Chicken", sound: "Cluck!" }
    ];

    let current = 0;

    const animalDiv = document.getElementById("animal");
    const messageDiv = document.getElementById("message");

    animalDiv.addEventListener("click", () => {
        messageDiv.textContent = animals[current].sound + " ⭐⭐⭐";
        speak(animals[current].name);
    });

    function nextAnimal() {
        current = (current + 1) % animals.length;
        animalDiv.textContent = animals[current].emoji;
        messageDiv.textContent = "Tap the animal!";
        speak(animals[current].name);
    }

    function speak(text) {
        const speech = new SpeechSynthesisUtterance(text);
        speech.rate = 0.7;
        speech.pitch = 1.3;
        window.speechSynthesis.speak(speech);
    }
</script>

</body>
</html>
