<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Poland Quiz Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f3f4f6;
            color: #333;
            margin: 0;
            padding: 0;
        }

        .quiz-container {
            max-width: 600px;
            margin: 50px auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        h1 {
            font-size: 24px;
            margin-bottom: 20px;
        }

        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        #score {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>Poland Cold Knowledge Quiz</h1>
        <div id="quiz">
            <!-- Quiz questions will appear here -->
        </div>
        <button id="next-button">Next Question</button>
        <p id="score">Score: 0</p>
    </div>
    <script>
        const questions = [
            {
                question: "Polish people drink vodka with what accompaniment?",
                options: ["Pickled cucumbers", "Bread", "Crying Russians", "Another bottle of vodka"],
                answer: 0
            },
            {
                question: "What is Poland's national dance called?",
                options: ["Polonaise", "Mazurka", "Krakowiak", "All of the above"],
                answer: 3
            },
            {
                question: "Why do Polish people leave an extra chair on Christmas Eve?",
                options: ["For late guests", "For unexpected Jesus", "For aliens", "For tired herring buyers"],
                answer: 1
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;

        function showQuestion() {
            const quizDiv = document.getElementById("quiz");
            quizDiv.innerHTML = ""; // Clear previous content

            const questionData = questions[currentQuestionIndex];
            const questionElement = document.createElement("h2");
            questionElement.textContent = questionData.question;
            quizDiv.appendChild(questionElement);

            questionData.options.forEach((option, index) => {
                const button = document.createElement("button");
                button.textContent = option;
                button.onclick = () => checkAnswer(index);
                quizDiv.appendChild(button);
            });
        }

        function checkAnswer(selectedIndex) {
            const questionData = questions[currentQuestionIndex];
            if (selectedIndex === questionData.answer) {
                score++;
                alert("Correct!");
            } else {
                alert("Wrong answer!");
            }
            document.getElementById("score").textContent = `Score: ${score}`;
            currentQuestionIndex++;
            if (currentQuestionIndex < questions.length) {
                showQuestion();
            } else {
                endQuiz();
            }
        }

        function endQuiz() {
            const quizDiv = document.getElementById("quiz");
            quizDiv.innerHTML = `<h2>Quiz completed!</h2><p>Your final score is ${score} out of ${questions.length}.</p>`;
            document.getElementById("next-button").style.display = "none";
        }

        document.getElementById("next-button").onclick = showQuestion;

        // Initialize the first question on page load
        showQuestion();
    </script>
</body>
</html>