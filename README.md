<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Number Prediction Trick</title>
    <!-- Include Font Awesome for icons -->
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"
    />
    <style>
        /* Styles */
        @keyframes buttonHover {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #ffecd2, #fcb69f);
            color: #333;
            margin: 0;
            padding: 0;
            overflow: hidden; /* Prevent scrollbar when overlay is active */
        }
        .container {
            max-width: 900px;
            margin: 0 auto;
            background-color: #ffffff;
            padding: 40px 20px;
            border-radius: 15px;
            box-shadow: 0 0 25px rgba(0, 0, 0, 0.1);
            text-align: center;
            position: relative;
            overflow: hidden;
            z-index: 1;
        }
        /* Other styles remain as before */
        /* ... (previous CSS styles) ... */
        /* Full-Screen Overlay Styles */
        #full-screen-result {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(5px);
            z-index: 9999;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            animation: fadeIn 1s forwards;
        }
        #full-screen-result h1 {
            font-size: 3em;
            color: #e74c3c;
            margin-bottom: 20px;
            animation: popIn 1s forwards;
        }
        #full-screen-result .icon {
            font-size: 5em;
            color: #e74c3c;
            animation: spin 2s infinite;
        }
        #close-button {
            margin-top: 30px;
            padding: 10px 20px;
            background-color: #e74c3c;
            color: #fff;
            border: none;
            border-radius: 5px;
            font-size: 1.2em;
            cursor: pointer;
            animation: fadeIn 2s forwards;
        }
        #close-button:hover {
            background-color: #c0392b;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes popIn {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        /* Rest of the styles */
        /* Responsive Styles */
        @media (max-width: 768px) {
            #full-screen-result h1 {
                font-size: 2em;
            }
            #full-screen-result .icon {
                font-size: 3em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Existing content -->
        <!-- Character Icons -->
        <i class="fas fa-chalkboard-teacher icon icon-boy-teacher"></i>
        <i class="fas fa-user-graduate icon icon-female-teacher"></i>
        <i class="fas fa-users icon icon-students"></i>

        <h1>🔮 Number Prediction Trick</h1>
        <div class="instructions">
            <h2>📜 Instructions:</h2>
            <ol>
                <li>Think of a 2-digit number. 🤔</li>
                <li>Sum the digits of your number. ➕</li>
                <li>Reverse your original number. 🔄</li>
                <li>Subtract the sum of the digits from the reversed number. ➖</li>
                <li>Enter the range of your result: 🔢
                    <ul style="list-style-type: none; margin-top: 10px;">
                        <li>• 1 for 1-10</li>
                        <li>• 2 for 11-20</li>
                        <li>• 3 for 21-30</li>
                        <li>• 4 for 31-40</li>
                        <li>• 5 for 41-50</li>
                        <li>• 6 for 51-60</li>
                        <li>• 7 for 61-70</li>
                        <li>• 8 for 71-80</li>
                        <li>• 9 for 81-90</li>
                    </ul>
                </li>
            </ol>
        </div>
        <h2>Enter Your Range:</h2>
        <div class="input-field">
            <i class="fas fa-magic"></i>
            <input type="number" id="userRange" min="1" max="9" placeholder="Enter range number (1-9)">
        </div>
        <button onclick="showResult()">🔮 Reveal My Number!</button>
        <!-- We remove the previous result div -->
        <!-- <div id="result"></div> -->
    </div>
    <!-- Full-Screen Result Overlay -->
    <div id="full-screen-result">
        <h1 id="result-text"></h1>
        <i class="fas fa-magic icon"></i>
        <button id="close-button" onclick="closeResult()">Close</button>
    </div>
    <script>
        function printNumberInRange(range) {
            const results = {
                1: "Your thought number is: 9 🎉",
                2: "Your thought number is: 18 🎉",
                3: "Your thought number is: 27 🎉",
                4: "Your thought number is: 36 🎉",
                5: "Your thought number is: 45 🎉",
                6: "Your thought number is: 54 🎉",
                7: "Your thought number is: 63 🎉",
                8: "Your thought number is: 72 🎉",
                9: "Your thought number is: 81 🎉",
            };
            return results[range] || "Invalid range. Please enter a number between 1 and 9. 🚫";
        }
        function showResult() {
            const userRange = parseInt(document.getElementById('userRange').value, 10);
            if (isNaN(userRange) || userRange < 1 || userRange > 9) {
                alert("Please enter a valid number between 1 and 9.");
                return;
            }
            const resultText = printNumberInRange(userRange);
            // Display the full-screen result overlay
            const fullScreenResult = document.getElementById('full-screen-result');
            const resultTextElement = document.getElementById('result-text');
            resultTextElement.textContent = resultText;
            fullScreenResult.style.display = 'flex';
        }
        function closeResult() {
            // Hide the full-screen result overlay
            const fullScreenResult = document.getElementById('full-screen-result');
            fullScreenResult.style.display = 'none';
        }
    </script>
</body>
</html>
