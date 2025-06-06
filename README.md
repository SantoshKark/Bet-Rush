<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bet Rush - Casino</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-bg: #1a1a1a;
            --secondary-bg: #2c2c2c;
            --accent-gold: #FFD700;
            --text-light: #f0f0f0;
            --text-dark: #333;
            --success: #28a745;
            --danger: #dc3545;
        }

        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            background-color: var(--primary-bg);
            color: var(--text-light);
            overflow-x: hidden;
        }

        .hidden { display: none !important; }

        /* --- Auth Section (THIS IS THE CHANGED PART) --- */
        #auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://www.imghippo.com/i/fl5582RnU.jpg') center/cover no-repeat;
        }
        .auth-form-wrapper {
            background-color: var(--secondary-bg);
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            width: 100%;
            max-width: 400px;
            text-align: center;
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }
        .auth-form-wrapper h2 {
            color: var(--accent-gold);
            margin-bottom: 20px;
        }
        .auth-form-wrapper input {
            width: 100%;
            padding: 12px;
            margin-bottom: 15px;
            border: 1px solid #444;
            border-radius: 5px;
            background-color: #333;
            color: var(--text-light);
            box-sizing: border-box;
        }
        .auth-btn {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 5px;
            background-color: var(--accent-gold);
            color: var(--text-dark);
            font-weight: 700;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .auth-btn:hover { background-color: #f0c400; }
        .google-btn { background-color: #fff; color: #555; margin-top: 10px; }
        .google-btn:hover { background-color: #eee; }
        .form-switch {
            margin-top: 20px;
            font-size: 0.9em;
        }
        .form-switch a {
            color: var(--accent-gold);
            text-decoration: none;
            font-weight: 600;
        }
        #error-message, #success-message { margin-top: 15px; font-weight: 600; }
        #error-message { color: var(--danger); }
        #success-message { color: var(--success); }

        /* --- App Section --- */
        #app-container {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 30px;
            background-color: var(--secondary-bg);
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        header .logo {
            font-size: 1.8em;
            font-weight: 700;
            color: var(--accent-gold);
        }
        header nav button {
            background: none;
            border: 1px solid var(--accent-gold);
            color: var(--accent-gold);
            padding: 8px 16px;
            margin: 0 10px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        header nav button:hover, header nav button.active {
            background-color: var(--accent-gold);
            color: var(--text-dark);
        }
        .header-right { display: flex; align-items: center; }
        #balance-display {
            background-color: rgba(255, 255, 255, 0.1);
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 600;
        }

        main {
            flex-grow: 1;
            padding: 40px;
            animation: fadeIn 0.5s;
        }

        /* --- Home Page --- */
        #home-page .game-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        .game-card {
            background-color: var(--secondary-bg);
            border-radius: 10px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            justify-content: center;
            min-height: 350px;
        }
        .game-card:hover { 
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(255, 215, 0, 0.2);
        }
        .game-card h3 {
            color: var(--accent-gold);
            margin-top: 0;
            font-size: 1.5em;
        }
        
        .game-cover { animation: fadeIn 0.5s; }
        .game-cover p { color: #ccc; margin: 15px 0 25px 0; }
        .btn-play-now { padding: 12px 24px; background-color: var(--accent-gold); color: var(--text-dark); border: none; border-radius: 5px; font-weight: 700; cursor: pointer; transition: all 0.3s ease; }
        .btn-play-now:hover { background-color: #f0c400; transform: scale(1.05); }

        .game-interface { position: relative; animation: fadeIn 0.5s; }
        .game-interface .btn-back-to-games { background: none; border: 1px solid #555; color: #ccc; padding: 5px 10px; border-radius: 5px; cursor: pointer; position: absolute; top: -10px; left: -10px; font-size: 0.9em; }
        .game-interface .btn-back-to-games:hover { background-color: #444; color: #fff; }
        
        .game-controls button { padding: 12px 20px; margin: 5px; font-size: 1em; cursor: pointer; border-radius: 5px; border: 2px solid var(--accent-gold); background-color: transparent; color: var(--accent-gold); font-weight: 600; transition: all 0.3s ease; }
        .game-controls button:hover, .game-controls button.active { background-color: var(--accent-gold); color: var(--text-dark); }
        .bet-input { width: 80%; margin: 20px auto; }
        .bet-input input { width: 100%; padding: 10px; text-align: center; background-color: #333; border: 1px solid #555; color: var(--text-light); border-radius: 5px; font-size: 1.1em; }
        .play-btn { width: 80%; padding: 12px; background-color: var(--success); color: #fff; border: none; border-radius: 5px; font-weight: 700; cursor: pointer; transition: background-color 0.3s; }
        .play-btn:hover { background-color: #218838; }
        .game-result { margin-top: 20px; font-size: 1.2em; font-weight: 600; min-height: 50px; }
        .game-result .details { font-size: 0.8em; color: #ccc; margin-top: 5px; }

        #coin { width: 100px; height: 100px; margin: 15px auto; position: relative; transform-style: preserve-3d; }
        .coin-side { position: absolute; width: 100%; height: 100%; backface-visibility: hidden; display: flex; justify-content: center; align-items: center; font-size: 1.5em; border-radius: 50%; background-color: var(--accent-gold); color: var(--text-dark); }
        .tails { transform: rotateY(180deg); }
        .flip-heads { animation: flip-heads 2s forwards; }
        .flip-tails { animation: flip-tails 2s forwards; }
        @keyframes flip-heads { from { transform: rotateY(0); } to { transform: rotateY(1800deg); } }
        @keyframes flip-tails { from { transform: rotateY(0); } to { transform: rotateY(1980deg); } }

        /* --- Profile Page --- */
        #profile-page .profile-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px; }
        #profile-username { font-size: 2em; font-weight: 700; }
        .profile-actions button, .modal-actions button { background-color: var(--accent-gold); color: var(--text-dark); border: none; padding: 12px 24px; margin-left: 10px; border-radius: 5px; cursor: pointer; font-weight: 600; transition: background-color 0.3s ease; }
        .profile-actions button:hover, .modal-actions button:hover { background-color: #f0c400; }
        #logout-btn { background-color: var(--danger); color: white; }
        #logout-btn:hover { background-color: #c82333; }

        /* Modal Styles */
        .modal { position: fixed; z-index: 2000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(0,0,0,0.7); display: flex; justify-content: center; align-items: center; }
        .modal-content { background: var(--secondary-bg); padding: 30px; border-radius: 10px; width: 90%; max-width: 500px; animation: fadeIn 0.3s; }
        .modal-header { display: flex; justify-content: space-between; align-items: center; }
        .modal-header h3 { margin: 0; color: var(--accent-gold); }
        .close-btn { font-size: 2em; cursor: pointer; color: #aaa; }
        .modal-body { margin-top: 20px; }
        .modal-body input { width: 100%; padding: 12px; margin-bottom: 15px; border: 1px solid #444; border-radius: 5px; background-color: #333; color: var(--text-light); box-sizing: border-box; }
        .copyable-number { background: #333; padding: 10px; border-radius: 5px; display: flex; justify-content: space-between; align-items: center; margin: 20px 0; }
        .copyable-number button { background: var(--accent-gold); border: none; padding: 5px 10px; border-radius: 3px; cursor: pointer; }
        .modal-actions { text-align: right; margin-top: 20px; }

        /* History Table */
        #history-content table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        #history-content th, #history-content td { padding: 12px; border-bottom: 1px solid #444; text-align: left; }
        #history-content th { background-color: #333; }
        .status-pending { color: orange; }
        .status-approved { color: var(--success); }
        .status-rejected { color: var(--danger); }
        .type-deposit, .type-win { color: var(--success); }
        .type-withdraw, .type-loss { color: var(--danger); }
        .type-game, .type-tie { color: lightblue; }
    </style>
</head>
<body>

    <!-- AUTHENTICATION CONTAINER -->
    <div id="auth-container">
        <div class="auth-form-wrapper">
            <form id="signup-form">
                <h2>Create Account</h2>
                <input type="text" id="signup-username" placeholder="Username" required>
                <input type="email" id="signup-email" placeholder="Email" required>
                <input type="password" id="signup-password" placeholder="Password" required>
                <input type="password" id="signup-confirm-password" placeholder="Confirm Password" required>
                <button type="submit" class="auth-btn">Sign Up</button>
                <div id="error-message"></div>
                <div id="success-message"></div>
                <p class="form-switch">Already have an account? <a href="#" id="show-login">Login</a></p>
            </form>
            <form id="login-form" class="hidden">
                <h2>Welcome to Bet Rush</h2>
                <input type="email" id="login-email" placeholder="Email" required>
                <input type="password" id="login-password" placeholder="Password" required>
                <button type="submit" class="auth-btn">Login</button>
                <button type="button" id="google-login-btn" class="auth-btn google-btn">Login with Google</button>
                <div id="login-error-message"></div>
                <p class="form-switch">Don't have an account? <a href="#" id="show-signup">Sign Up</a></p>
            </form>
        </div>
    </div>

    <!-- MAIN APP CONTAINER -->
    <div id="app-container" class="hidden">
        <header>
            <div class="logo">Bet Rush</div>
            <nav>
                <button id="nav-home" class="active">Home</button>
                <button id="nav-profile">Profile</button>
            </nav>
            <div class="header-right">
                <div id="balance-display">Balance: Rs 0.00</div>
            </div>
        </header>

        <main>
            <!-- HOME PAGE -->
            <section id="home-page">
                <div class="game-container">
                    
                    <div class="game-card" id="ht-card">
                        <div class="game-cover">
                            <h3>Heads or Tails</h3>
                            <p>A classic 50/50 game of chance. Guess the flip!</p>
                            <button class="btn-play-now">Play Now</button>
                        </div>
                        <div class="game-interface hidden">
                            <button class="btn-back-to-games">← Back</button>
                            <div id="coin">
                                <div class="coin-side heads">H</div>
                                <div class="coin-side tails">T</div>
                            </div>
                            <div class="game-controls">
                                <button data-choice="heads">Heads</button>
                                <button data-choice="tails">Tails</button>
                            </div>
                            <div class="bet-input">
                                <input type="number" id="ht-bet" placeholder="Bet Amount" min="10">
                            </div>
                            <button class="play-btn" id="ht-play-btn">Flip Coin</button>
                            <div class="game-result" id="ht-result"></div>
                        </div>
                    </div>

                    <div class="game-card" id="rps-card">
                        <div class="game-cover">
                            <h3>Rock Paper Scissors</h3>
                            <p>Outsmart your opponent. Rock, paper, or scissors?</p>
                            <button class="btn-play-now">Play Now</button>
                        </div>
                        <div class="game-interface hidden">
                            <button class="btn-back-to-games">← Back</button>
                            <h3>Rock Paper Scissors</h3>
                            <div class="game-controls">
                                <button data-choice="rock">Rock</button>
                                <button data-choice="paper">Paper</button>
                                <button data-choice="scissors">Scissors</button>
                            </div>
                            <div class="bet-input">
                                <input type="number" id="rps-bet" placeholder="Bet Amount" min="10">
                            </div>
                            <button class="play-btn" id="rps-play-btn">Play</button>
                            <div class="game-result" id="rps-result"></div>
                        </div>
                    </div>
                    
                    <div class="game-card" id="ou7-card">
                        <div class="game-cover">
                            <h3>Over / Under 7</h3>
                            <p>Predict if the sum of two dice will be over or under 7.</p>
                            <button class="btn-play-now">Play Now</button>
                        </div>
                        <div class="game-interface hidden">
                            <button class="btn-back-to-games">← Back</button>
                             <h3>Over / Under 7</h3>
                            <div class="game-controls">
                                <button data-choice="under">Under 7</button>
                                <button data-choice="over">Over 7</button>
                            </div>
                            <div class="bet-input">
                                <input type="number" id="ou7-bet" placeholder="Bet Amount" min="10">
                            </div>
                            <button class="play-btn" id="ou7-play-btn">Roll Dice</button>
                            <div class="game-result" id="ou7-result"></div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- PROFILE PAGE -->
            <section id="profile-page" class="hidden">
                <div class="profile-header">
                    <h2 id="profile-username">Username</h2>
                    <div class="profile-actions">
                        <button id="deposit-btn">Deposit</button>
                        <button id="withdraw-btn">Withdraw</button>
                        <button id="history-btn">History</button>
                        <button id="logout-btn">Logout</button>
                    </div>
                </div>
                <div id="profile-content"></div>
            </section>
        </main>
    </div>

    <!-- MODALS -->
    <div id="deposit-modal" class="modal hidden"> <div class="modal-content"> <div class="modal-header"> <h3>Deposit Funds</h3> <span class="close-btn">×</span> </div> <div class="modal-body"> <div id="deposit-step-1"> <p>Select Payment Method:</p> <select id="deposit-method" class="modal-body input"> <option value="esewa">eSewa</option> <option value="khalti">Khalti</option> </select> <input type="number" id="deposit-amount" placeholder="Amount (Min Rs 100)" min="100"> <div class="modal-actions"> <button id="deposit-next-1">Next</button> </div> </div> <div id="deposit-step-2" class="hidden"> <p>Transfer the amount to the following eSewa number:</p> <div class="copyable-number"> <span id="esewa-number">9767879311</span> <button id="copy-btn">Copy</button> </div> <div class="modal-actions"> <button class="back-btn">Back</button> <button id="deposit-next-2">Next</button> </div> </div> <div id="deposit-step-3" class="hidden"> <p>Enter transaction details:</p> <input type="text" id="deposit-name" placeholder="Your Name" required> <input type="text" id="deposit-number" placeholder="Your eSewa/Khalti Number" required> <input type="text" id="deposit-tx-code" placeholder="Transaction Code" required> <div class="modal-actions"> <button class="back-btn">Back</button> <button id="deposit-confirm">Confirm</button> </div> </div> </div> </div> </div>
    <div id="withdraw-modal" class="modal hidden"> <div class="modal-content"> <div class="modal-header"> <h3>Withdraw Funds</h3> <span class="close-btn">×</span> </div> <div class="modal-body"> <div id="withdraw-step-1"> <p>Select Payment Method:</p> <select id="withdraw-method" class="modal-body input"> <option value="esewa">eSewa</option> <option value="khalti">Khalti</option> </select> <input type="number" id="withdraw-amount" placeholder="Amount (Min Rs 5000)" min="5000"> <div class="modal-actions"> <button id="withdraw-next-1">Next</button> </div> </div> <div id="withdraw-step-2" class="hidden"> <p>Enter your details:</p> <input type="text" id="withdraw-name" placeholder="Account Holder Name" required> <input type="text" id="withdraw-number" placeholder="eSewa/Khalti Number" required> <div class="modal-actions"> <button class="back-btn">Back</button> <button id="withdraw-confirm">Confirm Withdrawal</button> </div> </div> </div> </div> </div>
    <div id="history-modal" class="modal hidden"> <div class="modal-content"> <div class="modal-header"> <h3>Transaction History</h3> <span class="close-btn">×</span> </div> <div class="modal-body" id="history-content"> <p>Loading history...</p> </div> </div> </div>

    <!-- Firebase SDKs -->
    <script type="module">
        // Import functions from the SDKs
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.15.0/firebase-app.js";
        import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, onAuthStateChanged, signOut, GoogleAuthProvider, signInWithPopup } from "https://www.gstatic.com/firebasejs/9.15.0/firebase-auth.js";
        import { getFirestore, doc, setDoc, getDoc, onSnapshot, collection, addDoc, serverTimestamp, query, where, orderBy, writeBatch, increment } from "https://www.gstatic.com/firebasejs/9.15.0/firebase-firestore.js";

        // Your web app's Firebase configuration
        const firebaseConfig = {
            apiKey: "AIzaSyBiF0xwUgaaMQmzbv_Rc2eM_MWIrArPDE4",
            authDomain: "bet-rush-130f3.firebaseapp.com",
            projectId: "bet-rush-130f3",
            storageBucket: "bet-rush-130f3.firebasestorage.app",
            messagingSenderId: "920543164659",
            appId: "1:920543164659:web:829817d15a49c3f35f1f86",
            measurementId: "G-HS3E9MV5ES"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);

        // --- All JavaScript logic from the previous correct version goes here ---
        // (It is unchanged, so for brevity it is represented by this comment)
        // ...
        let currentUser = null;
        let currentUserData = {};
        let unsubscribeUser;
        const authContainer = document.getElementById('auth-container');
        const appContainer = document.getElementById('app-container');
        const signupForm = document.getElementById('signup-form');
        const loginForm = document.getElementById('login-form');
        onAuthStateChanged(auth, (user) => { if (user) { currentUser = user; authContainer.classList.add('hidden'); appContainer.classList.remove('hidden'); listenToUserData(user.uid); document.getElementById('profile-username').textContent = 'Loading...'; } else { currentUser = null; if(unsubscribeUser) unsubscribeUser(); authContainer.classList.remove('hidden'); appContainer.classList.add('hidden'); loginForm.classList.add('hidden'); signupForm.classList.remove('hidden'); } });
        document.getElementById('show-login').addEventListener('click', (e) => { e.preventDefault(); signupForm.classList.add('hidden'); loginForm.classList.remove('hidden'); });
        document.getElementById('show-signup').addEventListener('click', (e) => { e.preventDefault(); loginForm.classList.add('hidden'); signupForm.classList.remove('hidden'); });
        signupForm.addEventListener('submit', async (e) => { e.preventDefault(); const username = document.getElementById('signup-username').value; const email = document.getElementById('signup-email').value; const password = document.getElementById('signup-password').value; const confirmPassword = document.getElementById('signup-confirm-password').value; const errorMessage = document.getElementById('error-message'); const successMessage = document.getElementById('success-message'); errorMessage.textContent = ''; successMessage.textContent = ''; if (password !== confirmPassword) { errorMessage.textContent = 'Passwords do not match.'; return; } try { const userCredential = await createUserWithEmailAndPassword(auth, email, password); const user = userCredential.user; await setDoc(doc(db, "users", user.uid), { username: username, email: email, balance: 0, createdAt: serverTimestamp(), lastOnline: serverTimestamp() }); successMessage.textContent = 'Account created successfully! Please login.'; signupForm.reset(); setTimeout(() => { signupForm.classList.add('hidden'); loginForm.classList.remove('hidden'); successMessage.textContent = ''; }, 2000); } catch (error) { errorMessage.textContent = error.message; } });
        loginForm.addEventListener('submit', async (e) => { e.preventDefault(); const email = document.getElementById('login-email').value; const password = document.getElementById('login-password').value; const errorMessage = document.getElementById('login-error-message'); errorMessage.textContent = ''; try { await signInWithEmailAndPassword(auth, email, password); } catch (error) { errorMessage.textContent = error.message; } });
        document.getElementById('google-login-btn').addEventListener('click', async () => { const provider = new GoogleAuthProvider(); try { const result = await signInWithPopup(auth, provider); const user = result.user; const userDocRef = doc(db, "users", user.uid); const userDoc = await getDoc(userDocRef); if (!userDoc.exists()) { await setDoc(userDocRef, { username: user.displayName || 'GoogleUser', email: user.email, balance: 0, createdAt: serverTimestamp(), lastOnline: serverTimestamp() }); } } catch (error) { document.getElementById('login-error-message').textContent = error.message; } });
        document.getElementById('logout-btn').addEventListener('click', async () => { await signOut(auth); });
        function listenToUserData(uid) { const userDocRef = doc(db, "users", uid); unsubscribeUser = onSnapshot(userDocRef, (doc) => { if (doc.exists()) { currentUserData = { id: doc.id, ...doc.data() }; document.getElementById('balance-display').textContent = `Balance: Rs ${currentUserData.balance.toFixed(2)}`; document.getElementById('profile-username').textContent = currentUserData.username; } else { console.log("No such user document!"); } }); }
        const pages = ['home-page', 'profile-page']; const navButtons = {'nav-home': 'home-page', 'nav-profile': 'profile-page'}; Object.keys(navButtons).forEach(btnId => { document.getElementById(btnId).addEventListener('click', () => { document.querySelector('header nav button.active').classList.remove('active'); document.getElementById(btnId).classList.add('active'); pages.forEach(pageId => { document.getElementById(pageId).classList.toggle('hidden', pageId !== navButtons[btnId]); }); }); });
        const modals = ['deposit-modal', 'withdraw-modal', 'history-modal']; document.getElementById('deposit-btn').addEventListener('click', () => document.getElementById('deposit-modal').classList.remove('hidden')); document.getElementById('withdraw-btn').addEventListener('click', () => document.getElementById('withdraw-modal').classList.remove('hidden')); document.getElementById('history-btn').addEventListener('click', () => { document.getElementById('history-modal').classList.remove('hidden'); loadHistory(); }); document.querySelectorAll('.close-btn').forEach(btn => { btn.addEventListener('click', () => { modals.forEach(modalId => document.getElementById(modalId).classList.add('hidden')); }); }); document.querySelectorAll('.back-btn').forEach(btn => { btn.addEventListener('click', (e) => { const currentStep = e.target.parentElement.parentElement; const prevStep = currentStep.previousElementSibling; if(prevStep) { currentStep.classList.add('hidden'); prevStep.classList.remove('hidden'); } }); });
        document.getElementById('deposit-next-1').addEventListener('click', () => { if(document.getElementById('deposit-amount').value >= 100){ document.getElementById('deposit-step-1').classList.add('hidden'); document.getElementById('deposit-step-2').classList.remove('hidden'); } else { alert('Minimum deposit is Rs 100.'); } }); document.getElementById('deposit-next-2').addEventListener('click', () => { document.getElementById('deposit-step-2').classList.add('hidden'); document.getElementById('deposit-step-3').classList.remove('hidden'); }); document.getElementById('copy-btn').addEventListener('click', () => { navigator.clipboard.writeText(document.getElementById('esewa-number').textContent).then(() => alert('Number copied!')); }); document.getElementById('deposit-confirm').addEventListener('click', async () => { const amount = parseFloat(document.getElementById('deposit-amount').value); const name = document.getElementById('deposit-name').value; const number = document.getElementById('deposit-number').value; const txCode = document.getElementById('deposit-tx-code').value; if(!name || !number || !txCode) { alert('Please fill all fields.'); return; } try { await addDoc(collection(db, "transactions"), { userId: currentUser.uid, username: currentUserData.username, email: currentUser.email, type: 'deposit', method: document.getElementById('deposit-method').value, amount: amount, details: { name, number, transactionCode: txCode }, status: 'pending', createdAt: serverTimestamp() }); alert('Deposit request submitted.'); document.getElementById('deposit-modal').classList.add('hidden'); document.getElementById('deposit-step-3').classList.add('hidden'); document.getElementById('deposit-step-1').classList.remove('hidden'); } catch (error) { alert('Error: ' + error.message); } });
        document.getElementById('withdraw-next-1').addEventListener('click', () => { const amount = parseFloat(document.getElementById('withdraw-amount').value); if (amount < 5000) { alert('Minimum withdrawal is Rs 5000.'); return; } if (amount > currentUserData.balance) { alert('Insufficient balance.'); return; } document.getElementById('withdraw-step-1').classList.add('hidden'); document.getElementById('withdraw-step-2').classList.remove('hidden'); });
        document.getElementById('withdraw-confirm').addEventListener('click', async () => { const amount = parseFloat(document.getElementById('withdraw-amount').value); const name = document.getElementById('withdraw-name').value; const number = document.getElementById('withdraw-number').value; if(!name || !number) { alert('Please fill all fields.'); return; } try { await addDoc(collection(db, "transactions"), { userId: currentUser.uid, username: currentUserData.username, email: currentUser.email, type: 'withdraw', method: document.getElementById('withdraw-method').value, amount: amount, details: { name, number }, status: 'pending', createdAt: serverTimestamp() }); alert('Withdrawal request submitted.'); document.getElementById('withdraw-modal').classList.add('hidden'); document.getElementById('withdraw-step-2').classList.add('hidden'); document.getElementById('withdraw-step-1').classList.remove('hidden'); } catch (error) { alert('Error: ' + error.message); } });
        async function loadHistory() { const historyContent = document.getElementById('history-content'); historyContent.innerHTML = '<table><thead><tr><th>Date</th><th>Type</th><th>Details</th><th>Amount</th><th>Status</th></tr></thead><tbody id="history-table-body"></tbody></table>'; const tableBody = document.getElementById('history-table-body'); const q = query(collection(db, "transactions"), where("userId", "==", currentUser.uid), orderBy("createdAt", "desc")); onSnapshot(q, (querySnapshot) => { tableBody.innerHTML = ''; querySnapshot.forEach((doc) => { const data = doc.data(); const date = data.createdAt ? data.createdAt.toDate().toLocaleString() : 'N/A'; const typeClass = `type-${data.type.toLowerCase()}`; const statusClass = `status-${data.status.toLowerCase()}`; let details = ''; if(data.type === 'game') { details = `${data.gameName}: ${data.outcome.toUpperCase()}`; } else { details = data.method.toUpperCase(); } const row = `<tr><td>${date}</td><td class="${typeClass}">${data.type.toUpperCase()}</td><td>${details}</td><td class="${typeClass}">${data.type === 'deposit' || data.type === 'win' ? '+' : '-'} Rs ${data.amount.toFixed(2)}</td><td class="${statusClass}">${data.status.toUpperCase()}</td></tr>`; tableBody.innerHTML += row; }); if (querySnapshot.empty) { historyContent.innerHTML = '<p>No transactions found.</p>'; } }); }
        document.querySelectorAll('.btn-play-now').forEach(button => { button.addEventListener('click', (e) => { const gameCard = e.target.closest('.game-card'); gameCard.querySelector('.game-cover').classList.add('hidden'); gameCard.querySelector('.game-interface').classList.remove('hidden'); }); });
        document.querySelectorAll('.btn-back-to-games').forEach(button => { button.addEventListener('click', (e) => { const gameCard = e.target.closest('.game-card'); gameCard.querySelector('.game-cover').classList.remove('hidden'); gameCard.querySelector('.game-interface').classList.add('hidden'); }); });
        document.querySelectorAll('.game-controls button').forEach(button => { button.addEventListener('click', (e) => { const parent = e.target.parentElement; parent.querySelectorAll('button').forEach(btn => btn.classList.remove('active')); e.target.classList.add('active'); }); });
        async function handleGamePlay(gameName, bet, playerChoice, resultDiv, winLogicFn) { if (!playerChoice) { alert("Please make a selection."); return; } if (isNaN(bet) || bet <= 0) { alert("Please enter a valid bet amount."); return; } if (bet > currentUserData.balance) { alert("Insufficient balance."); return; } resultDiv.innerHTML = "Processing..."; const gameResult = winLogicFn(playerChoice); let balanceChange = 0; let transactionType = 'game'; let transactionStatus = 'completed'; if (gameResult.outcome === 'win') { balanceChange = bet; transactionType = 'win'; resultDiv.style.color = 'var(--success)'; } else if (gameResult.outcome === 'loss') { balanceChange = -bet; transactionType = 'loss'; resultDiv.style.color = 'var(--danger)'; } else { resultDiv.style.color = 'var(--text-light)'; transactionType = 'tie'; } try { const userRef = doc(db, "users", currentUser.uid); const newTxRef = doc(collection(db, "transactions")); const batch = writeBatch(db); batch.update(userRef, { balance: increment(balanceChange) }); batch.set(newTxRef, { userId: currentUser.uid, username: currentUserData.username, type: transactionType, status: transactionStatus, gameName: gameName, outcome: gameResult.outcome, amount: bet, createdAt: serverTimestamp() }); await batch.commit(); resultDiv.innerHTML = `${gameResult.wording}<br><span class="details">${gameResult.details}</span>`; } catch (error) { console.error("Error processing game:", error); resultDiv.innerHTML = "An error occurred. Please try again."; resultDiv.style.color = 'var(--danger)'; } }
        document.getElementById('ht-play-btn').addEventListener('click', () => { const bet = parseFloat(document.getElementById('ht-bet').value); const choice = document.querySelector('#ht-card .game-controls button.active')?.dataset.choice; const resultDiv = document.getElementById('ht-result'); const coin = document.getElementById('coin'); resultDiv.innerHTML = ""; coin.className = 'coin'; void coin.offsetWidth; const winLogic = (playerChoice) => { const result = Math.random() < 0.5 ? 'heads' : 'tails'; if (result === 'heads') coin.classList.add('flip-heads'); else coin.classList.add('flip-tails'); let outcome = 'loss'; if (result === playerChoice) outcome = 'win'; return { outcome: outcome, wording: `You ${outcome === 'win' ? 'Won' : 'Lost'} Rs ${bet}!`, details: `The coin landed on ${result}.` }; }; setTimeout(() => { handleGamePlay('Heads or Tails', bet, choice, resultDiv, winLogic); }, 100); });
        document.getElementById('rps-play-btn').addEventListener('click', () => { const bet = parseFloat(document.getElementById('rps-bet').value); const choice = document.querySelector('#rps-card .game-controls button.active')?.dataset.choice; const resultDiv = document.getElementById('rps-result'); const winLogic = (playerChoice) => { const options = ['rock', 'paper', 'scissors']; const computerChoice = options[Math.floor(Math.random() * 3)]; let outcome; if (playerChoice === computerChoice) { outcome = 'tie'; } else if ( (playerChoice === 'rock' && computerChoice === 'scissors') || (playerChoice === 'scissors' && computerChoice === 'paper') || (playerChoice === 'paper' && computerChoice === 'rock') ) { outcome = 'win'; } else { outcome = 'loss'; } let wording = `It's a tie!`; if(outcome === 'win') wording = `You Won Rs ${bet}!`; if(outcome === 'loss') wording = `You Lost Rs ${bet}.`; return { outcome, wording, details: `You chose ${playerChoice}, computer chose ${computerChoice}.` }; }; handleGamePlay('Rock Paper Scissors', bet, choice, resultDiv, winLogic); });
        document.getElementById('ou7-play-btn').addEventListener('click', () => { const bet = parseFloat(document.getElementById('ou7-bet').value); const choice = document.querySelector('#ou7-card .game-controls button.active')?.dataset.choice; const resultDiv = document.getElementById('ou7-result'); const winLogic = (playerChoice) => { const die1 = Math.floor(Math.random() * 6) + 1; const die2 = Math.floor(Math.random() * 6) + 1; const sum = die1 + die2; let outcome = 'loss'; if (sum === 7) { outcome = 'loss'; } else if (playerChoice === 'under' && sum < 7) { outcome = 'win'; } else if (playerChoice === 'over' && sum > 7) { outcome = 'win'; } let wording = `You Lost Rs ${bet}.`; if(outcome === 'win') wording = `You Won Rs ${bet}!`; return { outcome, wording, details: `The dice rolled ${die1} + ${die2} = ${sum}.` }; }; handleGamePlay('Over / Under 7', bet, choice, resultDiv, winLogic); });
    </script>
</body>
</html>
