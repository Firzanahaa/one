<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Buffer Solution Educational Game</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f7fafc;
        }
        header {
            text-align: center;
            padding: 40px 0;
            background-color: #ebf8ff;
            border-radius: 10px;
            margin-bottom: 30px;
        }
        h1 {
            color: #2b6cb0;
            font-size: 3rem;
            margin-bottom: 20px;
        }
        .intro {
            font-size: 1.2rem;
            max-width: 800px;
            margin: 0 auto 30px;
            padding: 0 20px;
            text-align: center;
        }
        .nav-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 40px;
        }
        .nav-button {
            background-color: #4299e1;
            color: white;
            border: none;
            padding: 12px 24px;
            font-size: 1.1rem;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s;
            text-decoration: none;
            display: inline-block;
        }
        .nav-button:hover {
            background-color: #2b6cb0;
        }
        .section {
            display: none;
            padding: 30px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }
        .section.active {
            display: block;
        }
        .home-section {
            display: block;
        }
        h2 {
            color: #2b6cb0;
            margin-bottom: 20px;
        }
        .pH-meter {
            width: 100%;
            height: 50px;
            background: linear-gradient(to right, #ff0000, #ff9900, #ffff00, #33cc33, #0099ff, #6633cc, #cc00cc);
            border-radius: 5px;
            margin: 20px 0;
            position: relative;
        }
        .pH-indicator {
            position: absolute;
            top: -20px;
            transform: translateX(-50%);
            width: 20px;
            height: 60px;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
        }
        .control-panel {
            display: flex;
            justify-content: space-between;
            margin: 20px 0;
            flex-wrap: wrap;
        }
        .control-group {
            margin: 10px;
            flex: 1;
            min-width: 200px;
        }
        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
        }
        .question {
            margin-bottom: 30px;
        }
        .options {
            list-style-type: none;
            padding: 0;
        }
        .options li {
            margin: 10px 0;
            padding: 10px;
            background-color: #e2e8f0;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .options li:hover {
            background-color: #cbd5e0;
        }
        .options li.correct {
            background-color: #48bb78;
            color: white;
        }
        .options li.incorrect {
            background-color: #f56565;
            color: white;
        }
        .feedback {
            font-weight: bold;
            margin-top: 10px;
            min-height: 24px;
        }
        button {
            background-color: #4299e1;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #2b6cb0;
        }
        .hidden {
            display: none;
        }
        .result {
            font-size: 1.2rem;
            font-weight: bold;
            margin-top: 20px;
            text-align: center;
        }
        .back-to-home {
            display: block;
            margin: 20px auto;
        }
        .simulation-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .beaker {
            width: 200px;
            height: 300px;
            border: 5px solid #888;
            border-top: 0;
            border-radius: 0 0 30px 30px;
            position: relative;
            margin: 40px auto;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2rem;
            font-weight: bold;
            overflow: hidden;
        }
        .liquid {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 80%;
            transition: background-color 0.5s, height 1s;
        }
        .info-panel {
            background-color: #e2e8f0;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Buffer Solution Educational Game</h1>
        <div class="intro">
            <p>A buffer solution is a solution that can maintain a relatively constant pH when a small amount of acid or base is added. It is important in various biological and chemical processes. Buffers consist of a weak acid and its conjugate base, or a weak base and its conjugate acid, working together to resist pH changes.</p>
        </div>
        <div class="nav-buttons">
            <button class="nav-button" onclick="showSection('quiz')">Interactive Quiz</button>
            <button class="nav-button" onclick="showSection('simulation')">Buffer Solution Simulation</button>
        </div>
    </header>

    <div id="home" class="section home-section">
        <h2>Welcome to the Buffer Solution Learning Center</h2>
        <p>Select one of the options above to begin your learning journey about buffer solutions!</p>
        <p>Buffer solutions are crucial in:</p>
        <ul>
            <li>Maintaining stable pH in blood and other biological systems</li>
            <li>Laboratory experiments requiring constant pH</li>
            <li>Industrial processes sensitive to pH changes</li>
            <li>Environmental systems like lakes and oceans</li>
        </ul>
    </div>

    <div id="quiz" class="section">
        <h2>Buffer Solution Quiz</h2>
        <div class="quiz-container">
            <div id="question-container">
                <div class="question" id="q1">
                    <h3>1. What is the primary function of a buffer solution?</h3>
                    <ul class="options">
                        <li onclick="checkAnswer(this, true)">To resist changes in pH when acids or bases are added</li>
                        <li onclick="checkAnswer(this, false)">To rapidly change pH when acids or bases are added</li>
                        <li onclick="checkAnswer(this, false)">To neutralize all acids and bases</li>
                        <li onclick="checkAnswer(this, false)">To increase the solubility of compounds</li>
                    </ul>
                    <div class="feedback"></div>
                </div>
                
                <div class="question hidden" id="q2">
                    <h3>2. A buffer solution typically consists of:</h3>
                    <ul class="options">
                        <li onclick="checkAnswer(this, false)">A strong acid and a strong base</li>
                        <li onclick="checkAnswer(this, true)">A weak acid and its conjugate base (or a weak base and its conjugate acid)</li>
                        <li onclick="checkAnswer(this, false)">Two strong acids with different pH values</li>
                        <li onclick="checkAnswer(this, false)">Pure water and a neutral compound</li>
                    </ul>
                    <div class="feedback"></div>
                </div>
                
                <div class="question hidden" id="q3">
                    <h3>3. The Henderson-Hasselbalch equation is used to:</h3>
                    <ul class="options">
                        <li onclick="checkAnswer(this, false)">Calculate the volume of a buffer solution</li>
                        <li onclick="checkAnswer(this, false)">Calculate the temperature of a buffer solution</li>
                        <li onclick="checkAnswer(this, true)">Calculate the pH of a buffer solution</li>
                        <li onclick="checkAnswer(this, false)">Calculate the mass of solute needed for a buffer</li>
                    </ul>
                    <div class="feedback"></div>
                </div>
                
                <div class="question hidden" id="q4">
                    <h3>4. Buffer capacity refers to:</h3>
                    <ul class="options">
                        <li onclick="checkAnswer(this, false)">The volume of solution that can be prepared</li>
                        <li onclick="checkAnswer(this, false)">The maximum temperature a buffer can withstand</li>
                        <li onclick="checkAnswer(this, false)">The shelf life of a buffer solution</li>
                        <li onclick="checkAnswer(this, true)">The amount of acid or base a buffer can neutralize before significant pH change</li>
                    </ul>
                    <div class="feedback"></div>
                </div>
                
                <div class="question hidden" id="q5">
                    <h3>5. Which of the following is an example of a buffer system in the human body?</h3>
                    <ul class="options">
                        <li onclick="checkAnswer(this, false)">Sodium chloride in sweat</li>
                        <li onclick="checkAnswer(this, false)">Glucose in blood</li>
                        <li onclick="checkAnswer(this, true)">Carbonic acid/bicarbonate in blood</li>
                        <li onclick="checkAnswer(this, false)">Calcium in bones</li>
                    </ul>
                    <div class="feedback"></div>
                </div>
            </div>
            
            <div id="quiz-navigation" class="hidden">
                <button id="prev-btn" onclick="prevQuestion()">Previous</button>
                <button id="next-btn" onclick="nextQuestion()">Next</button>
            </div>
            
            <div class="result hidden" id="quiz-result">
                Your score: <span id="score">0</span>/5
            </div>
            
            <button class="back-to-home" onclick="showSection('home')">Back to Home</button>
        </div>
    </div>

    <div id="simulation" class="section">
        <h2>Buffer Solution Simulation</h2>
        <div class="simulation-container">
            <div class="info-panel">
                <p>Current pH: <span id="current-pH">7.0</span></p>
                <p>Buffer System: <span id="buffer-type">Acetate buffer (CH₃COOH / CH₃COO⁻)</span></p>
            </div>
            
            <div class="beaker">
                <div class="liquid" id="solution"></div>
                <span id="pH-display">7.0</span>
            </div>
            
            <div class="control-panel">
                <div class="control-group">
                    <h3>Add Acid/Base</h3>
                    <button onclick="addAcid()">Add HCl (drops)</button>
                    <button onclick="addBase()">Add NaOH (drops)</button>
                </div>
                
                <div class="control-group">
                    <h3>Buffer Controls</h3>
                    <button onclick="toggleBuffer()">Toggle Buffer On/Off</button>
                    <button onclick="resetSimulation()">Reset Simulation</button>
                </div>
            </div>
            
            <div class="pH-meter">
                <div class="pH-indicator" id="pH-indicator" style="left: 50%;">7</div>
            </div>
            
            <div class="info-panel">
                <h3>Observations</h3>
                <div id="observations">
                    <p>Start by adding acid or base to see how the buffer works!</p>
                </div>
            </div>
            
            <button class="back-to-home" onclick="showSection('home')">Back to Home</button>
        </div>
    </div>

    <script>
        // Navigation
        function showSection(sectionId) {
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionId).classList.add('active');
            
            // If quiz section, show quiz navigation
            if (sectionId === 'quiz') {
                document.getElementById('quiz-navigation').classList.remove('hidden');
                currentQuestion = 1;
                updateQuestionVisibility();
            }
        }
        
        // Quiz functionality
        let currentQuestion = 1;
        let score = 0;
        let answeredQuestions = 0;
        
        function checkAnswer(element, isCorrect) {
            const questionElement = element.closest('.question');
            const options = questionElement.querySelectorAll('.options li');
            const feedback = questionElement.querySelector('.feedback');
            
            // Prevent multiple answers
            if (options[0].classList.contains('correct') || options[0].classList.contains('incorrect')) {
                return;
            }
            
            options.forEach(option => {
                option.style.pointerEvents = 'none';
            });
            
            if (isCorrect) {
                element.classList.add('correct');
                feedback.textContent = 'Correct!';
                score++;
            } else {
                element.classList.add('incorrect');
                feedback.textContent = 'Incorrect. The first option is correct.';
                
                // Show correct answer
                options.forEach(option => {
                    if (option.onclick.toString().includes('true')) {
                        option.classList.add('correct');
                    }
                });
            }
            
            answeredQuestions++;
            
            // Check if quiz is completed
            if (answeredQuestions === 5) {
                document.getElementById('score').textContent = score;
                document.getElementById('quiz-result').classList.remove('hidden');
            }
        }
        
        function updateQuestionVisibility() {
            for (let i = 1; i <= 5; i++) {
                const question = document.getElementById('q' + i);
                if (i === currentQuestion) {
                    question.classList.remove('hidden');
                } else {
                    question.classList.add('hidden');
                }
            }
            
            // Update navigation buttons
            const prevBtn = document.getElementById('prev-btn');
            const nextBtn = document.getElementById('next-btn');
            
            prevBtn.disabled = currentQuestion === 1;
            nextBtn.textContent = currentQuestion === 5 ? 'Finish' : 'Next';
        }
        
        function nextQuestion() {
            if (currentQuestion < 5) {
                currentQuestion++;
                updateQuestionVisibility();
            } else {
                // Show results
                document.getElementById('score').textContent = score;
                document.getElementById('quiz-result').classList.remove('hidden');
            }
        }
        
        function prevQuestion() {
            if (currentQuestion > 1) {
                currentQuestion--;
                updateQuestionVisibility();
            }
        }
        
        // Simulation functionality
        let pH = 7.0;
        let bufferActive = true;
        let acidAdded = 0;
        let baseAdded = 0;
        
        function updatepH() {
            // Update display
            document.getElementById('current-pH').textContent = pH.toFixed(1);
            document.getElementById('pH-display').textContent = pH.toFixed(1);
            
            // Update pH meter indicator position (0-14 scale)
            const position = (pH / 14) * 100;
            document.getElementById('pH-indicator').style.left = position + '%';
            
            // Update solution color
            const solution = document.getElementById('solution');
            
            // Color based on pH
            if (pH <= 3) {
                solution.style.backgroundColor = 'rgba(255, 0, 0, 0.7)'; // Red for strong acid
            } else if (pH <= 6) {
                solution.style.backgroundColor = 'rgba(255, 165, 0, 0.7)'; // Orange for weak acid
            } else if (pH < 8) {
                solution.style.backgroundColor = 'rgba(144, 238, 144, 0.7)'; // Light green for neutral
            } else if (pH < 11) {
                solution.style.backgroundColor = 'rgba(0, 191, 255, 0.7)'; // Deep sky blue for weak base
            } else {
                solution.style.backgroundColor = 'rgba(75, 0, 130, 0.7)'; // Indigo for strong base
            }
        }
        
        function addAcid() {
            acidAdded++;
            const observations = document.getElementById('observations');
            
            if (bufferActive) {
                // Buffer active - pH changes very slowly
                if (acidAdded <= 5) {
                    pH -= 0.1;
                } else if (acidAdded <= 10) {
                    pH -= 0.2;
                } else {
                    pH -= 0.5; // Buffer capacity exceeded
                }
                
                if (acidAdded === 1) {
                    observations.innerHTML = '<p>Acid added. The buffer is neutralizing the acid, maintaining a stable pH.</p>';
                } else if (acidAdded === 5) {
                    observations.innerHTML += '<p>More acid added. The buffer continues to resist pH change.</p>';
                } else if (acidAdded === 10) {
                    observations.innerHTML += '<p>Buffer capacity is reaching its limit!</p>';
                } else if (acidAdded > 10) {
                    observations.innerHTML += '<p>Buffer capacity exceeded! pH is dropping more rapidly now.</p>';
                }
            } else {
                // No buffer - pH changes dramatically
                pH -= 1.0;
                
                if (acidAdded === 1) {
                    observations.innerHTML = '<p>Acid added. Without a buffer, the pH drops significantly!</p>';
                } else {
                    observations.innerHTML += '<p>More acid added. The pH continues to drop rapidly.</p>';
                }
            }
            
            // Limit pH
            if (pH < 0) pH = 0;
            
            updatepH();
        }
        
        function addBase() {
            baseAdded++;
            const observations = document.getElementById('observations');
            
            if (bufferActive) {
                // Buffer active - pH changes very slowly
                if (baseAdded <= 5) {
                    pH += 0.1;
                } else if (baseAdded <= 10) {
                    pH += 0.2;
                } else {
                    pH += 0.5; // Buffer capacity exceeded
                }
                
                if (baseAdded === 1) {
                    observations.innerHTML = '<p>Base added. The buffer is neutralizing the base, maintaining a stable pH.</p>';
                } else if (baseAdded === 5) {
                    observations.innerHTML += '<p>More base added. The buffer continues to resist pH change.</p>';
                } else if (baseAdded === 10) {
                    observations.innerHTML += '<p>Buffer capacity is reaching its limit!</p>';
                } else if (baseAdded > 10) {
                    observations.innerHTML += '<p>Buffer capacity exceeded! pH is increasing more rapidly now.</p>';
                }
            } else {
                // No buffer - pH changes dramatically
                pH += 1.0;
                
                if (baseAdded === 1) {
                    observations.innerHTML = '<p>Base added. Without a buffer, the pH rises significantly!</p>';
                } else {
                    observations.innerHTML += '<p>More base added. The pH continues to rise rapidly.</p>';
                }
            }
            
            // Limit pH
            if (pH > 14) pH = 14;
            
            updatepH();
        }
        
        function toggleBuffer() {
            bufferActive = !bufferActive;
            const observations = document.getElementById('observations');
            const bufferType = document.getElementById('buffer-type');
            
            if (bufferActive) {
                observations.innerHTML = '<p>Buffer activated! The solution will now resist pH changes.</p>';
                bufferType.textContent = 'Acetate buffer (CH₃COOH / CH₃COO⁻)';
            } else {
                observations.innerHTML = '<p>Buffer deactivated! The solution will now experience large pH changes.</p>';
                bufferType.textContent = 'No buffer (plain water)';
            }
        }
        
        function resetSimulation() {
            pH = 7.0;
            acidAdded = 0;
            baseAdded = 0;
            bufferActive = true;
            
            updatepH();
            
            const observations = document.getElementById('observations');
            observations.innerHTML = '<p>Simulation reset. Start by adding acid or base to see how the buffer works!</p>';
            
            const bufferType = document.getElementById('buffer-type');
            bufferType.textContent = 'Acetate buffer (CH₃COOH / CH₃COO⁻)';
        }
        
        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            updatepH();
            updateQuestionVisibility();
        });
    </script>
</body>
</html># one
