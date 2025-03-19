<!DOCTYPE html>
<html lang="el">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Επιλογή Δυσκολίας</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            background: url('https://i.ibb.co/Y7J7F57D/Screenshot.png') no-repeat center center fixed;
            background-size: cover;
            margin: 0;
            padding: 0;
        }
        .container {
            margin-top: 50px;
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        .button {
            padding: 12px 25px;
            margin: 10px;
            cursor: pointer;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            color: white;
            transition: 0.3s;
        }
        .button:nth-child(1) {
            background-color: #4CAF50;
        }
        .button:nth-child(2) {
            background-color: #FF5733;
        }
        .button:hover {
            opacity: 0.8;
        }
        .question-box {
            margin-top: 20px;
            font-size: 20px;
            font-weight: bold;
            color: #333;
            padding: 15px;
            background: #e3e3e3;
            display: inline-block;
            border-radius: 5px;
            min-width: 300px;
        }
    </style>
</head>
<body>
    <h1>Επιλέξτε Δυσκολία</h1>
    <div class="container">
        <button class="button" onclick="showQuestion('easy')">Απλό</button>
        <button class="button" onclick="showQuestion('hard')">Δύσκολο</button>
        <div id="question" class="question-box"></div>
    </div>

    <script>
        const questions = {
            easy: [
                "το τώρα δηλώνει τόπο ή χρόνο;",
                "το χτές δηλώνει τόπο ή χρόνο;"
            ],
            hard: [
                "γ' ενικό ο μαθητής",
                "β' πληθυντικό η κοπέλα"
            ]
        };

        function showQuestion(difficulty) {
            const randomIndex = Math.floor(Math.random() * questions[difficulty].length);
            document.getElementById('question').textContent = questions[difficulty][randomIndex];
        }
    </script>
</body>
</html>
