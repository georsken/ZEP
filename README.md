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
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        h1 {
            font-size: 2rem;
            color: white;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 90%;
            max-width: 400px;
        }

        .button {
            padding: 1rem;
            margin: 0.5rem;
            cursor: pointer;
            font-size: 1.2rem;
            border: none;
            border-radius: 5px;
            color: white;
            transition: 0.3s;
            width: 100%;
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
            margin-top: 1rem;
            font-size: 1.2rem;
            font-weight: bold;
            color: #333;
            padding: 1rem;
            background: #e3e3e3;
            display: inline-block;
            border-radius: 5px;
            width: 100%;
            text-align: center;
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
                font-size: 1.8rem;
            }

            .button {
                font-size: 1rem;
                padding: 0.8rem;
            }

            .question-box {
                font-size: 1rem;
            }
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
                "το χτές δηλώνει τόπο ή χρόνο;",
                "το έξω δηλώνει τόπο ή χρόνο;",
                "το μέσα δηλώνει τόπο ή χρόνο;",
                "το έξω δηλώνει τόπο ή χρόνο;",
                "το πάνω δηλώνει τόπο ή χρόνο;",
                "το κάτω δηλώνει τόπο ή χρόνο;",
                "το μπροστά δηλώνει τόπο ή χρόνο;",
                "το πίσω δηλώνει τόπο ή χρόνο;",
                "το δίπλα δηλώνει τόπο ή χρόνο;",
                "το πέρα δηλώνει τόπο ή χρόνο;",
                "το εδώ δηλώνει τόπο ή χρόνο;",
                "το εκεί δηλώνει τόπο ή χρόνο;",
                "το παρακάτω δηλώνει τόπο ή χρόνο;",
                "το παραπέρα δηλώνει τόπο ή χρόνο;",
                "το τότε δηλώνει τόπο ή χρόνο;",
                "το πριν δηλώνει τόπο ή χρόνο;",
                "το μετά δηλώνει τόπο ή χρόνο;",
                "το σύντομα δηλώνει τόπο ή χρόνο;",
                "το αργότερα δηλώνει τόπο ή χρόνο;",
                "το κάποτε δηλώνει τόπο ή χρόνο;",
                "το ποτέ δηλώνει τόπο ή χρόνο;",
                "το συχνά δηλώνει τόπο ή χρόνο;",
                "το σπάνια δηλώνει τόπο ή χρόνο;",
                "το πάντα δηλώνει τόπο ή χρόνο;",
                "το καθημερινά δηλώνει τόπο ή χρόνο;",
                "το πρωί δηλώνει τόπο ή χρόνο;",
                "το μεσημέρι δηλώνει τόπο ή χρόνο;",
                "το απόγευμα δηλώνει τόπο ή χρόνο;",
                "το βράδυ δηλώνει τόπο ή χρόνο;",
                "το νύχτα δηλώνει τόπο ή χρόνο;",
                "το χειμώνας δηλώνει τόπο ή χρόνο;",
                "το καλοκαίρι δηλώνει τόπο ή χρόνο;",
                "το φθινόπωρο δηλώνει τόπο ή χρόνο;",
                "το άνοιξη δηλώνει τόπο ή χρόνο;",
                "το προχθές δηλώνει τόπο ή χρόνο;",
                "το μεθαύριο δηλώνει τόπο ή χρόνο;",
                "το επόμενη εβδομάδα δηλώνει τόπο ή χρόνο;",
                "το περασμένος μήνας δηλώνει τόπο ή χρόνο;",
                "το προηγούμενη χρονιά δηλώνει τόπο ή χρόνο;",
                "το έπειτα δηλώνει τόπο ή χρόνο;",
                "το ξανά δηλώνει τόπο ή χρόνο;",
                "το μόλις δηλώνει τόπο ή χρόνο;",
                "το ήδη δηλώνει τόπο ή χρόνο;",
                "το ακόμα δηλώνει τόπο ή χρόνο;",
                "το τελικά δηλώνει τόπο ή χρόνο;",
                "το διαρκώς δηλώνει τόπο ή χρόνο;",
                "το ενδιάμεσα δηλώνει τόπο ή χρόνο;",
                "το γύρω δηλώνει τόπο ή χρόνο;",
                "το οπουδήποτε δηλώνει τόπο ή χρόνο;",
                "το κάπου δηλώνει τόπο ή χρόνο;",
                "το πουθενά δηλώνει τόπο ή χρόνο;",
                "το οριστικά δηλώνει τόπο ή χρόνο;"
            ],
            hard: [
                "γ' ενικό ο μαθητής",
                "β' πληθυντικό η κοπέλα",
                "το ρήμα γράφω στον Αόριστο",
                "το ρήμα τρέχω στον Ενεστώτα",
                "το ρήμα μαγειρεύω στον Παρατατικό",
                "το ρήμα τραγουδώ στον Μέλλοντα Εξακολουθητικό",
                "το ρήμα αγαπώ στον Συντελεσμένο Μέλλοντα",
                "το ρήμα χορεύω στον Παρακείμενο",
                "το ρήμα κοιμάμαι στον Υπερσυντέλικο",
                "το ρήμα ακούω στον Ενεστώτα",
                "το ρήμα βλέπω στον Αόριστο",
                "το ρήμα παίζω στον Παρακείμενο",
                "το ρήμα μιλάω στον Μέλλοντα Στιγμιαίο",
                "το ρήμα τρώω στον Υπερσυντέλικο",
                "το ρήμα δίνω στον Μέλλοντα Εξακολουθητικό",
                "το ρήμα φεύγω στον Αόριστο",
                "το ρήμα επιστρέφω στον Παρατατικό",
                "το ρήμα γελάω στον Παρακείμενο",
                "το ρήμα πίνω στον Συντελεσμένο Μέλλοντα",
                "το ρήμα χτίζω στον Μέλλοντα Στιγμιαίο",
                "το ρήμα ρωτάω στον Ενεστώτα",
                "το ρήμα ανοίγω στον Υπερσυντέλικο",
                "το ρήμα κλείνω στον Παρακείμενο",
                "το ρήμα κάθoμαι στον Παρατατικό",
                "το ρήμα φωνάζω στον Μέλλοντα Εξακολουθητικό",
                "το ρήμα γιορτάζω στον Αόριστο",
                "το ρήμα σπουδάζω στον Συντελεσμένο Μέλλοντα",
                "το ρήμα οδηγώ στον Μέλλοντα Στιγμιαίο",
                "το ρήμα θυμάμαι στον Παρακείμενο",
                "το ρήμα ξεχνώ στον Υπερσυντέλικο",
                "το ρήμα βοηθώ στον Μέλλοντα Εξακολουθητικό",
                "το ρήμα εργάζομαι στον Αόριστο",
                "το ρήμα χαμογελώ στον Ενεστώτα",
                "το ρήμα ξυπνώ στον Συντελεσμένο Μέλλοντα",
                "το ρήμα περπατώ στον Παρατατικό",
                "το ρήμα φτάνω στον Παρακείμενο",
                "το ρήμα σηκώνω στον Μέλλοντα Στιγμιαίο",
                "το ρήμα πέφτω στον Υπερσυντέλικο",
                "το ρήμα αλλάζω στον Μέλλοντα Εξακολουθητικό",
                "το ρήμα αγοράζω στον Αόριστο",
                "το ρήμα πουλώ στον Συντελεσμένο Μέλλοντα",
                "το ρήμα γεύομαι στον Ενεστώτα",
                "το ρήμα αθλούμαι στον Παρατατικό",
                "το ρήμα πηγαίνω στον Παρακείμενο",
                "το ρήμα κατεβαίνω στον Μέλλοντα Στιγμιαίο",
                "το ρήμα ανεβαίνω στον Υπερσυντέλικο",
                "το ρήμα σκέφτομαι στον Μέλλοντα Εξακολουθητικό",
                "το ρήμα θυμίζω στον Αόριστο",
                "το ρήμα στέλνω στον Συντελεσμένο Μέλλοντα",
                "το ρήμα υπολογίζω στον Παρατατικό",
                "το ρήμα ακολουθώ στον Παρακείμενο",
                "το ρήμα δημιουργώ στον Μέλλοντα Στιγμιαίο",
                "το ρήμα συνεχίζω στον Υπερσυντέλικο"
            ]
        };

        function showQuestion(difficulty) {
            const randomIndex = Math.floor(Math.random() * questions[difficulty].length);
            document.getElementById("question").innerText = questions[difficulty][randomIndex];
        }
    </script>
</body>
</html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Index Page</title>
</head>
<body>
    <h1>Πήγαινε στο Quiz</h1>
    <button onclick="location.href='quiz.html'">Go to Quiz</button>
</body>
</html>
