# Quiz-Game2
This is a quiz game 2
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        h1 {
            color: #333;
        }
        .question-container {
            width: 400px;
            margin: 20px auto;
            padding: 20px;
            border: 1px solid #ccc;
            background-color: #f9f9f9;
        }
        .options {
            text-align: left;
        }
        button {
            margin-top: 10px;
            padding: 10px;
            background-color: #4caf50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <h1>Quiz Game</h1>
    
    <div id="quiz-container" class="question-container">
        <div id="question"></div>
        <div id="options" class="options"></div>
        <button onclick="checkAnswer()">Next Question</button>
    </div>

    <script>
        const questions = [
            {
                question: "What is the capital of France?",
                options: ["Paris", "Berlin", "Madrid", "Rome"],
                correctAnswer: "Paris"
            },
            {
                question: "Which planet is known as the Red Planet?",
                options: ["Mars", "Venus", "Jupiter", "Saturn"],
                correctAnswer: "Mars"
            },
            {
                question: "What is the largest mammal in the world?",
                options: ["Elephant", "Blue Whale", "Giraffe", "Hippopotamus"],
                correctAnswer: "Blue Whale"
            }
        ];

        let currentQuestion = 0;
        let score = 0;

        function displayQuestion() {
            const questionContainer = document.getElementById('quiz-container');
            const questionElement = document.getElementById('question');
            const optionsElement = document.getElementById('options');

            const currentQues = questions[currentQuestion];
            questionElement.textContent = currentQues.question;

            optionsElement.innerHTML = '';
            currentQues.options.forEach((option, index) => {
                const button = document.createElement('button');
                button.textContent = option;
                button.onclick = () => selectAnswer(option);
                optionsElement.appendChild(button);
            });
        }

        function selectAnswer(selectedOption) {
            const currentQues = questions[currentQuestion];
            if (selectedOption === currentQues.correctAnswer) {
                score++;
            }

            if (currentQuestion < questions.length - 1) {
                currentQuestion++;
                displayQuestion();
            } else {
                showResult();
            }
        }

        function showResult() {
            const questionContainer = document.getElementById('quiz-container');
            const optionsElement = document.getElementById('options');
            questionContainer.innerHTML = `<h2>Your Score: ${score} / ${questions.length}</h2>`;
            optionsElement.innerHTML = '';
        }

        // Display the first question when the page loads
        displayQuestion();
    </script>
</body>
</html>
