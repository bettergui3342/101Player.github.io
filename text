<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>101Player</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #1c2526 0%, #2a2f32 50%, #3a1c5a 100%);
            color: #ffffff;
            font-family: Arial, sans-serif;
            display: flex;
            height: 100vh;
            overflow: hidden;
        }
        .container {
            display: flex;
            width: 100%;
            height: 100%;
            position: relative;
        }
        .menu-btn {
            position: absolute;
            top: 20px;
            left: 20px;
            z-index: 1000;
        }
        .btn {
            display: flex;
            align-items: center;
            padding: 10px 20px;
            background-color: #3a3f44;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .btn:hover {
            background-color: #4a4f54;
        }
        .btn .icon {
            margin-right: 10px;
        }
        .btn .text {
            font-size: 16px;
            color: #ffffff;
            font-weight: bold;
        }
        .sidebar {
            width: 250px;
            background-color: #2a2f32;
            padding: 20px;
            border-right: 1px solid #444;
            height: 100%;
            box-sizing: border-box;
            transition: transform 0.3s ease;
            transform: translateX(-100%);
        }
        .sidebar.visible {
            transform: translateX(0);
        }
        .sidebar h2 {
            margin: 0 0 20px 0;
            font-size: 24px;
            color: #ffffff;
        }
        .sidebar p {
            font-size: 14px;
            color: #cccccc;
            margin-bottom: 30px;
        }
        .menu {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        .menu li {
            padding: 15px 20px;
            margin-bottom: 5px;
            cursor: pointer;
            font-size: 16px;
            color: #ffffff;
            background-color: #3a3f44;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        .menu li:hover {
            background-color: #4a4f54;
        }
        .menu li.active {
            background-color: #5a5f64;
        }
        .menu li.secret-link {
            font-size: 12px;
            color: #888888;
            background-color: transparent;
            text-align: right;
            padding: 10px 20px;
        }
        .menu li.secret-link:hover {
            color: #cccccc;
            background-color: transparent;
        }
        .content {
            flex: 1;
            padding: 40px;
            overflow-y: auto;
        }
        .content h1 {
            margin-top: 0;
            font-size: 28px;
        }
        .content p {
            font-size: 16px;
            line-height: 1.6;
            color: #cccccc;
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        /* From Uiverse.io by cssbuttons-io */
        button {
            padding: 1.3em 3em;
            font-size: 12px;
            text-transform: uppercase;
            letter-spacing: 2.5px;
            font-weight: 500;
            color: #000;
            background-color: #fff;
            border: none;
            border-radius: 45px;
            box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease 0s;
            cursor: pointer;
            outline: none;
            margin-top: 20px;
            margin-right: 10px;
        }
        button:hover {
            background-color: #23c483;
            box-shadow: 0px 15px 20px rgba(46, 229, 157, 0.4);
            color: #fff;
            transform: translateY(-7px);
        }
        button:active {
            transform: translateY(-1px);
        }
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: #2a2f32;
            padding: 20px;
            border-radius: 10px;
            width: 90%;
            max-width: 500px;
            text-align: center;
        }
        .modal-content h2 {
            margin-top: 0;
            color: #ffffff;
        }
        .modal-content textarea {
            width: 100%;
            height: 100px;
            padding: 10px;
            margin-bottom: 20px;
            border-radius: 5px;
            border: none;
            background-color: #3a3f44;
            color: #ffffff;
            resize: none;
        }
        .modal-content button {
            margin: 0 10px;
        }
        /* Secret Page Styles */
        #secret-page {
            display: none;
            flex: 1;
            padding: 40px;
            overflow-y: auto;
        }
        #secret-page h1 {
            margin-top: 0;
            font-size: 28px;
        }
        #secret-page .password-input {
            margin-bottom: 20px;
        }
        #secret-page input[type="password"] {
            padding: 10px;
            border-radius: 5px;
            border: none;
            background-color: #3a3f44;
            color: #ffffff;
            margin-right: 10px;
        }
        #questions-list {
            margin-top: 20px;
        }
        #questions-list p {
            background-color: #3a3f44;
            padding: 10px;
            border-radius: 5px;
            margin: 10px 0;
            color: #cccccc;
        }
        @media (max-width: 768px) {
            .content, #secret-page {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="menu-btn">
        <!-- From Uiverse.io by gagan-gv -->
        <button class="btn" onclick="toggleSidebar()">
            <span class="icon">
                <svg viewBox="0 0 175 80" width="40" height="40">
                    <rect width="80" height="15" fill="#f0f0f0" rx="10"></rect>
                    <rect y="30" width="80" height="15" fill="#f0f0f0" rx="10"></rect>
                    <rect y="60" width="80" height="15" fill="#f0f0f0" rx="10"></rect>
                </svg>
            </span>
            <span class="text">MENU</span>
        </button>
    </div>
    <div class="container">
        <div class="sidebar" id="sidebar">
            <h2>101Player</h2>
            <p>Welcome to 101Player, your ultimate hub for gaming stats, player rankings, and community updates. Connect with me on Discord: 101PlayerYT. Stay connected and level up!</p>
            <ul class="menu">
                <li class="active" onclick="showPage('page1')">Stats</li>
                <li onclick="showPage('page2')">Rankings</li>
                <li onclick="showPage('page3')">Community</li>
                <li class="secret-link" onclick="showSecretPage()">Secret Page</li>
            </ul>
        </div>
        <div class="content">
            <div id="page1" class="page active">
                <h1>Player Stats</h1>
                <p>Track your gaming performance with detailed statistics. Monitor your wins, losses, and overall progress across multiple games.</p>
                <button onclick="openQuestionModal()">Ask 101Player</button>
                <button>Learn More</button>
            </div>
            <div id="page2" class="page">
                <h1>Rankings</h1>
                <p>Check out the top players in the 101Player community. See where you stand and aim for the top spot!</p>
                <button>View Leaderboard</button>
                <button onclick="shareRank()">Share Your Rank</button>
            </div>
            <div id="page3" class="page">
                <h1>Community</h1>
                <p>Join the conversation! Share tips, strategies, and connect with other players in the 101Player community.</p>
                <button>Join Now</button>
                <button onclick="joinDiscord()">Join Discord</button>
            </div>
        </div>
        <div id="secret-page">
            <h1>Secret Page - View Questions</h1>
            <div class="password-input">
                <input type="password" id="password" placeholder="Enter Password">
                <button onclick="checkPassword()">Submit</button>
            </div>
            <div id="questions-list" style="display: none;">
                <h2>Submitted Questions</h2>
                <!-- Questions will be displayed here -->
                <button onclick="clearQuestions()">Clear Questions</button>
            </div>
        </div>
    </div>

    <!-- Question Modal -->
    <div id="question-modal" class="modal">
        <div class="modal-content">
            <h2>Ask 101Player</h2>
            <textarea id="question-text" placeholder="Type your question here..."></textarea>
            <button onclick="submitQuestion()">Submit</button>
            <button onclick="closeQuestionModal()">Cancel</button>
        </div>
    </div>

    <script>
        // Page Navigation
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
            document.querySelectorAll('.menu li').forEach(item => {
                item.classList.remove('active');
            });
            event.target.classList.add('active');
            toggleSidebar();
            document.getElementById('secret-page').style.display = 'none';
            document.querySelector('.content').style.display = 'block';
        }

        // Show Secret Page
        function showSecretPage() {
            document.querySelector('.content').style.display = 'none';
            document.getElementById('secret-page').style.display = 'block';
            window.location.hash = 'secret';
            toggleSidebar();
        }

        // Sidebar Toggle
        function toggleSidebar() {
            const sidebar = document.getElementById('sidebar');
            sidebar.classList.toggle('visible');
        }

        // Question Modal
        function openQuestionModal() {
            document.getElementById('question-modal').style.display = 'flex';
        }

        function closeQuestionModal() {
            document.getElementById('question-modal').style.display = 'none';
            document.getElementById('question-text').value = '';
        }

        function submitQuestion() {
            const question = document.getElementById('question-text').value.trim();
            if (question) {
                let questions = JSON.parse(localStorage.getItem('questions')) || [];
                questions.push(question);
                localStorage.setItem('questions', JSON.stringify(questions));
                alert('Question submitted successfully!');
                closeQuestionModal();
            } else {
                alert('Please enter a question.');
            }
        }

        // Secret Page Access
        function checkPassword() {
            const password = document.getElementById('password').value;
            if (password === '12345678') {
                document.getElementById('questions-list').style.display = 'block';
                document.querySelector('.password-input').style.display = 'none';
                displayQuestions();
            } else {
                alert('Incorrect password!');
            }
        }

        function displayQuestions() {
            const questionsList = document.getElementById('questions-list');
            const questions = JSON.parse(localStorage.getItem('questions')) || [];
            questionsList.innerHTML = '<h2>Submitted Questions</h2>';
            if (questions.length === 0) {
                questionsList.innerHTML += '<p>No questions submitted yet.</p>';
            } else {
                questions.forEach((question, index) => {
                    questionsList.innerHTML += `<p>${index + 1}. ${question}</p>`;
                });
            }
            questionsList.innerHTML += '<button onclick="clearQuestions()">Clear Questions</button>';
        }

        function clearQuestions() {
            localStorage.removeItem('questions');
            displayQuestions();
            alert('All questions have been cleared.');
        }

        // Share Rank Function
        function shareRank() {
            const rankText = "I'm ranked #5 on 101Player! Check out my stats: [Your Profile Link]";
            navigator.clipboard.writeText(rankText).then(() => {
                alert('Rank copied to clipboard! Share it with your friends.');
            }).catch(err => {
                alert('Failed to copy rank: ' + err);
            });
        }

        // Join Discord Function
        function joinDiscord() {
            window.open('https://discord.gg/your-discord-invite-link', '_blank');
            alert('Opening Discord... Add me as a friend: 101PlayerYT (Replace the link with your actual Discord server invite!)');
        }

        // Check URL for Secret Page
        window.onload = function() {
            if (window.location.hash === '#secret') {
                document.querySelector('.content').style.display = 'none';
                document.getElementById('secret-page').style.display = 'block';
            }
        };
    </script>
</body>
</html>
