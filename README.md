<!DOCTYPE html>
<html lang="el">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Επιλογή Δυσκολίας</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap');
        
        body {
            font-family: 'Poppins', sans-serif;
            text-align: center;
            background: url('https://i.ibb.co/Y7J7F57D/Screenshot.png') no-repeat center center fixed;
            background-size: cover;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            color: white;
        }

        h1 {
            font-size: 2.5rem;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.7);
            animation: fadeIn 1s ease-in-out;
        }

        .container {
            background: rgba(255, 255, 255, 0.15);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 90%;
            max-width: 400px;
            animation: slideIn 1s ease-in-out;
        }

        .button {
            padding: 1rem;
            margin: 0.7rem;
            cursor: pointer;
            font-size: 1.3rem;
            border: none;
            border-radius: 8px;
            color: white;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            width: 100%;
            font-weight: 600;
        }

        .button:nth-child(1) {
            background: linear-gradient(45deg, #4CAF50, #2E7D32);
        }

        .button:nth-child(2) {
            background: linear-gradient(45deg, #FF5733, #C70039);
        }

        .button:hover {
            transform: scale(1.05);
            box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
            opacity: 0.9;
        }

        .question-box {
            margin-top: 1rem;
            font-size: 1.3rem;
            font-weight: bold;
            color: #fff;
            padding: 1rem;
            background: rgba(0, 0, 0, 0.6);
            display: inline-block;
            border-radius: 8px;
            width: 100%;
            text-align: center;
            animation: fadeIn 0.5s ease-in-out;
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            body {
                height: auto;
                padding: 2rem 0;
            }

            .container {
                width: 95%;
                padding: 1.5rem;
            }

            h1 {
                font-size: 2rem;
            }

            .button {
                font-size: 1.1rem;
                padding: 0.9rem;
            }

            .question-box {
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <h1>Επιλέξτε Δυσκολία</h1>
    <div class="container">
        <button class="button" onclick="showQuestion('easy')">Εύκολο</button>
        <button class="button" onclick="showQuestion('hard')">Δύσκολο</button>
        <div id="question" class="question-box"></div>
    </div>

    <script>
        const questions = {
            easy: [
                "Το τώρα δηλώνει τόπο ή χρόνο;",
                "Το χτες δηλώνει τόπο ή χρόνο;",
                "Το έξω δηλώνει τόπο ή χρόνο;"
            ],
            hard: [
                "Το ρήμα γράφω στον Αόριστο;",
                "Το ρήμα τρέχω στον Ενεστώτα;",
                "Το ρήμα μαγειρεύω στον Παρατατικό;"
            ]
        };

        function showQuestion(level) {
            const questionBox = document.getElementById("question");
            const randomIndex = Math.floor(Math.random() * questions[level].length);
            questionBox.innerHTML = questions[level][randomIndex];
        }
    </script>
</body>
</html>
