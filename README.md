# Password-game
The "Password Game" is a word association game where players guess a hidden word using one-word clues. It's a fast-paced test of vocabulary and communication skills, often leading to hilarious and exciting moments.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Password Game</title>
    <style>
        /* Add your CSS styles for game design here */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }

        #container {
            margin: 20px auto;
            width: 400px;
        }

        #output {
            font-size: 18px;
            margin: 10px 0;
        }

        input[type="text"] {
            padding: 5px;
            font-size: 16px;
            width: 100%;
        }

        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Password Game</h1>
    <div id="container">
        <p>Enter the password:</p>
        <input type="text" id="guessInput">
        <button onclick="checkPassword()">Submit</button>
        <div id="output"></div>
    </div>

    <script>
        const rules = [
            "Password must be at least 8 characters long.",
            "Password must contain at least one uppercase letter.",
            "Password must contain at least one lowercase letter.",
            "Password must contain at least one digit.",
            "Password must contain at least one special character (e.g., @, #, $, %)."
            // Add more rules here...
        ];

        const password = "Secret@123"; // Change this to the desired password
        let currentRuleIndex = 0;

        function checkPassword() {
            const guess = document.getElementById("guessInput").value;

            if (guess === password) {
                document.getElementById("output").innerHTML = "Congratulations! You've guessed the correct password.";
                document.getElementById("output").style.color = "green";
                document.getElementById("guessInput").setAttribute("disabled", "true");
            } else {
                if (currentRuleIndex < rules.length) {
                    document.getElementById("output").innerHTML = `Password does not meet the rule: ${rules[currentRuleIndex]}`;
                    document.getElementById("output").style.color = "red";
                    currentRuleIndex++;
                } else {
                    document.getElementById("output").innerHTML = "Sorry, you've exceeded the number of attempts. Refresh the page to try again.";
                    document.getElementById("output").style.color = "red";
                    document.getElementById("guessInput").setAttribute("disabled", "true");
                }
            }
        }
    </script>
</body>
</html>
