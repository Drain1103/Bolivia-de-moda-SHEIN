
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Work Account Portal</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #1a365d;
            --secondary-color: #2a4365;
            --accent-color: #3182ce;
            --text-color: #2d3748;
            --text-light: #718096;
            --bg-color: #f7fafc;
            --card-bg: #ffffff;
            --border-color: #e2e8f0;
            --error-color: #e53e3e;
            --success-color: #38a169;
        }

        .dark-mode {
            --primary-color: #2d3748;
            --secondary-color: #1a202c;
            --accent-color: #4299e1;
            --text-color: #e2e8f0;
            --text-light: #a0aec0;
            --bg-color: #1a202c;
            --card-bg: #2d3748;
            --border-color: #4a5568;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            transition: background-color 0.3s, color 0.3s;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .container {
            width: 100%;
            max-width: 420px;
            margin: 0 auto;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 12px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
            padding: 2rem;
            width: 100%;
            margin-bottom: 1.5rem;
        }

        .logo-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary-color);
        }

        .mode-toggle {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: none;
            border: none;
            color: var(--text-light);
            font-size: 1.2rem;
            cursor: pointer;
        }

        .tabs {
            display: flex;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid var(--border-color);
        }

        .tab {
            flex: 1;
            text-align: center;
            padding: 0.75rem;
            cursor: pointer;
            font-weight: 500;
            color: var(--text-light);
            position: relative;
        }

        .tab.active {
            color: var(--accent-color);
        }

        .tab.active::after {
            content: '';
            position: absolute;
            bottom: -1px;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--accent-color);
        }

        .form-group {
            margin-bottom: 1.25rem;
        }

        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--text-color);
        }

        .input-group {
            position: relative;
        }

        .form-input {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            font-size: 1rem;
            background-color: var(--card-bg);
            color: var(--text-color);
            transition: border-color 0.3s;
        }

        .form-input:focus {
            outline: none;
            border-color: var(--accent-color);
            box-shadow: 0 0 0 3px rgba(49, 130, 206, 0.2);
        }

        .form-input.error {
            border-color: var(--error-color);
        }

        .input-icon {
            position: absolute;
            right: 1rem;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-light);
            cursor: pointer;
        }

        .password-strength {
            height: 4px;
            width: 100%;
            background-color: var(--border-color);
            margin-top: 0.5rem;
            border-radius: 2px;
            overflow: hidden;
        }

        .password-strength-meter {
            height: 100%;
            width: 0;
            background-color: var(--error-color);
            transition: width 0.3s, background-color 0.3s;
        }

        .password-strength-text {
            font-size: 0.75rem;
            margin-top: 0.25rem;
            color: var(--text-light);
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .checkbox {
            margin-right: 0.5rem;
            cursor: pointer;
        }

        .checkbox-label {
            font-size: 0.875rem;
            color: var(--text-light);
            cursor: pointer;
        }

        .btn {
            display: block;
            width: 100%;
            padding: 0.75rem;
            background-color: var(--accent-color);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 500;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: var(--secondary-color);
        }

        .btn:disabled {
            background-color: var(--text-light);
            cursor: not-allowed;
        }

        .error-message {
            color: var(--error-color);
            font-size: 0.75rem;
            margin-top: 0.25rem;
            display: none;
        }

        .error-message.visible {
            display: block;
        }

        .notification {
            position: fixed;
            top: 1rem;
            right: 1rem;
            padding: 1rem;
            border-radius: 8px;
            background-color: var(--success-color);
            color: white;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            transform: translateX(120%);
            transition: transform 0.3s;
            z-index: 1000;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.error {
            background-color: var(--error-color);
        }

        @media (max-width: 480px) {
            .card {
                padding: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <button class="mode-toggle" id="modeToggle">
        <i class="fas fa-moon"></i>
    </button>

    <div class="container">
        <div class="card">
            <div class="logo-container">
                <div class="logo">WorkPortal</div>
            </div>

            <div class="tabs">
                <div class="tab active" id="signInTab">Sign In</div>
                <div class="tab" id="signUpTab">Sign Up</div>
            </div>

            <form id="signInForm">
                <div class="form-group">
                    <label for="signInPhone" class="form-label">Phone Number</label>
                    <div class="input-group">
                        <input type="tel" id="signInPhone" class="form-input" placeholder="Enter your phone number" autocomplete="tel">
                    </div>
                    <div class="error-message" id="signInPhoneError">Please enter a valid phone number (10-15 digits)</div>
                </div>

                <div class="form-group">
                    <label for="signInPassword" class="form-label">Password</label>
                    <div class="input-group">
                        <input type="password" id="signInPassword" class="form-input" placeholder="Enter 6-digit password" autocomplete="current-password">
                        <i class="fas fa-eye input-icon" id="signInPasswordToggle"></i>
                    </div>
                    <div class="error-message" id="signInPasswordError">Password must be 6 digits</div>
                </div>

                <div class="checkbox-group">
                    <input type="checkbox" id="rememberSignIn" class="checkbox">
                    <label for="rememberSignIn" class="checkbox-label">Remember me</label>
                </div>

                <button type="submit" class="btn" id="signInButton">Sign In</button>
            </form>

            <form id="signUpForm" style="display: none;">
                <div class="form-group">
                    <label for="signUpPhone" class="form-label">Phone Number</label>
                    <div class="input-group">
                        <input type="tel" id="signUpPhone" class="form-input" placeholder="Enter your phone number" autocomplete="tel">
                    </div>
                    <div class="error-message" id="signUpPhoneError">Please enter a valid phone number (10-15 digits)</div>
                </div>

                <div class="form-group">
                    <label for="signUpPassword" class="form-label">Password</label>
                    <div class="input-group">
                        <input type="password" id="signUpPassword" class="form-input" placeholder="Enter 6-digit password" autocomplete="new-password">
                        <i class="fas fa-eye input-icon" id="signUpPasswordToggle"></i>
                    </div>
                    <div class="password-strength">
                        <div class="password-strength-meter" id="passwordStrengthMeter"></div>
                    </div>
                    <div class="password-strength-text" id="passwordStrengthText">Password must be 6 digits</div>
                    <div class="error-message" id="signUpPasswordError">Password must be 6 digits</div>
                </div>

                <div class="checkbox-group">
                    <input type="checkbox" id="rememberSignUp" class="checkbox">
                    <label for="rememberSignUp" class="checkbox-label">Remember me</label>
                </div>

                <button type="submit" class="btn" id="signUpButton">Create Account</button>
            </form>
        </div>
    </div>

    <div class="notification" id="notification">
        <span id="notificationText"></span>
    </div>

    <script>
        // DOM Elements
        const modeToggle = document.getElementById('modeToggle');
        const signInTab = document.getElementById('signInTab');
        const signUpTab = document.getElementById('signUpTab');
        const signInForm = document.getElementById('signInForm');
        const signUpForm = document.getElementById('signUpForm');
        const signInPhone = document.getElementById('signInPhone');
        const signInPassword = document.getElementById('signInPassword');
        const signUpPhone = document.getElementById('signUpPhone');
        const signUpPassword = document.getElementById('signUpPassword');
        const signInPasswordToggle = document.getElementById('signInPasswordToggle');
        const signUpPasswordToggle = document.getElementById('signUpPasswordToggle');
        const rememberSignIn = document.getElementById('rememberSignIn');
        const rememberSignUp = document.getElementById('rememberSignUp');
        const notification = document.getElementById('notification');
        const notificationText = document.getElementById('notificationText');
        const passwordStrengthMeter = document.getElementById('passwordStrengthMeter');
        const passwordStrengthText = document.getElementById('passwordStrengthText');

        // Error elements
        const signInPhoneError = document.getElementById('signInPhoneError');
        const signInPasswordError = document.getElementById('signInPasswordError');
        const signUpPhoneError = document.getElementById('signUpPhoneError');
        const signUpPasswordError = document.getElementById('signUpPasswordError');

        // State
        let accounts = JSON.parse(localStorage.getItem('workAccounts')) || [];
        let isDarkMode = localStorage.getItem('darkMode') === 'true';

        // Initialize
        if (isDarkMode) {
            document.body.classList.add('dark-mode');
            modeToggle.innerHTML = '<i class="fas fa-sun"></i>';
        }

        // Auto-fill phone number if remembered
        const rememberedPhone = localStorage.getItem('rememberedPhone');
        if (rememberedPhone) {
            signInPhone.value = rememberedPhone;
            signUpPhone.value = rememberedPhone;
            rememberSignIn.checked = true;
            rememberSignUp.checked = true;
        }

        // Focus on phone input on load
        window.addEventListener('DOMContentLoaded', () => {
            signInPhone.focus();
        });

        // Dark mode toggle
        modeToggle.addEventListener('click', () => {
            isDarkMode = !isDarkMode;
            document.body.classList.toggle('dark-mode');
            modeToggle.innerHTML = isDarkMode ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
            localStorage.setItem('darkMode', isDarkMode);
        });

        // Tab switching
        signInTab.addEventListener('click', () => {
            signInTab.classList.add('active');
            signUpTab.classList.remove('active');
            signInForm.style.display = 'block';
            signUpForm.style.display = 'none';
            signInPhone.focus();
        });

        signUpTab.addEventListener('click', () => {
            signUpTab.classList.add('active');
            signInTab.classList.remove('active');
            signUpForm.style.display = 'block';
            signInForm.style.display = 'none';
            signUpPhone.focus();
        });

        // Password visibility toggle
        signInPasswordToggle.addEventListener('click', () => {
            togglePasswordVisibility(signInPassword, signInPasswordToggle);
        });

        signUpPasswordToggle.addEventListener('click', () => {
            togglePasswordVisibility(signUpPassword, signUpPasswordToggle);
        });

        function togglePasswordVisibility(input, icon) {
            if (input.type === 'password') {
                input.type = 'text';
                icon.classList.remove('fa-eye');
                icon.classList.add('fa-eye-slash');
            } else {
                input.type = 'password';
                icon.classList.remove('fa-eye-slash');
                icon.classList.add('fa-eye');
            }
        }

        // Phone number validation
        function validatePhoneNumber(phone) {
            const phoneRegex = /^\d{10,15}$/;
            return phoneRegex.test(phone);
        }

        // Password validation
        function validatePassword(password) {
            return password.length === 6 && /^\d+$/.test(password);
        }

        // Update password strength meter
        function updatePasswordStrength(password) {
            if (!password) {
                passwordStrengthMeter.style.width = '0%';
                passwordStrengthMeter.style.backgroundColor = 'var(--border-color)';
                passwordStrengthText.textContent = 'Password must be 6 digits';
                return;
            }

            if (!/^\d+$/.test(password)) {
                passwordStrengthMeter.style.width = '0%';
                passwordStrengthMeter.style.backgroundColor = 'var(--error-color)';
                passwordStrengthText.textContent = 'Password must contain only numbers';
                return;
            }

            const strength = Math.min(password.length / 6 * 100, 100);
            passwordStrengthMeter.style.width = `${strength}%`;

            if (password.length < 3) {
                passwordStrengthMeter.style.backgroundColor = 'var(--error-color)';
                passwordStrengthText.textContent = 'Weak password';
            } else if (password.length < 5) {
                passwordStrengthMeter.style.backgroundColor = '#ed8936';
                passwordStrengthText.textContent = 'Medium password';
            } else {
                passwordStrengthMeter.style.backgroundColor = 'var(--success-color)';
                passwordStrengthText.textContent = 'Strong password';
            }
        }

        // Show notification
        function showNotification(message, isError = false) {
            notificationText.textContent = message;
            notification.classList.toggle('error', isError);
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Input event listeners for real-time validation
        signInPhone.addEventListener('input', () => {
            if (signInPhone.value) {
                if (!validatePhoneNumber(signInPhone.value)) {
                    signInPhone.classList.add('error');
                    signInPhoneError.classList.add('visible');
                } else {
                    signInPhone.classList.remove('error');
                    signInPhoneError.classList.remove('visible');
                }
            } else {
                signInPhone.classList.remove('error');
                signInPhoneError.classList.remove('visible');
            }
        });

        signInPassword.addEventListener('input', () => {
            if (signInPassword.value) {
                if (!validatePassword(signInPassword.value)) {
                    signInPassword.classList.add('error');
                    signInPasswordError.classList.add('visible');
                } else {
                    signInPassword.classList.remove('error');
                    signInPasswordError.classList.remove('visible');
                }
            } else {
                signInPassword.classList.remove('error');
                signInPasswordError.classList.remove('visible');
            }
        });

        signUpPhone.addEventListener('input', () => {
            if (signUpPhone.value) {
                if (!validatePhoneNumber(signUpPhone.value)) {
                    signUpPhone.classList.add('error');
                    signUpPhoneError.classList.add('visible');
                } else {
                    signUpPhone.classList.remove('error');
                    signUpPhoneError.classList.remove('visible');
                }
            } else {
                signUpPhone.classList.remove('error');
                signUpPhoneError.classList.remove('visible');
            }
        });

        signUpPassword.addEventListener('input', () => {
            if (signUpPassword.value) {
                if (!/^\d+$/.test(signUpPassword.value)) {
                    signUpPassword.classList.add('error');
                    signUpPasswordError.textContent = 'Password must contain only numbers';
                    signUpPasswordError.classList.add('visible');
                } else {
                    signUpPassword.classList.remove('error');
                    updatePasswordStrength(signUpPassword.value);
                    if (signUpPassword.value.length !== 6) {
                        signUpPasswordError.textContent = 'Password must be exactly 6 digits';
                        signUpPasswordError.classList.add('visible');
                    } else {
                        signUpPasswordError.classList.remove('visible');
                    }
                }
            } else {
                signUpPassword.classList.remove('error');
                signUpPasswordError.classList.remove('visible');
                updatePasswordStrength('');
            }
        });

        // Form submission
        signInForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const phone = signInPhone.value.trim();
            const password = signInPassword.value.trim();
            
            let isValid = true;
            
            if (!validatePhoneNumber(phone)) {
                signInPhone.classList.add('error');
                signInPhoneError.classList.add('visible');
                isValid = false;
            } else {
                signInPhone.classList.remove('error');
                signInPhoneError.classList.remove('visible');
            }
            
            if (!validatePassword(password)) {
                signInPassword.classList.add('error');
                signInPasswordError.classList.add('visible');
                isValid = false;
            } else {
                signInPassword.classList.remove('error');
                signInPasswordError.classList.remove('visible');
            }
            
            if (isValid) {
                // Check if account exists
                const account = accounts.find(acc => acc.phone === phone && acc.password === password);
                
                if (account) {
                    // Store remembered phone number if checked
                    if (rememberSignIn.checked) {
                        localStorage.setItem('rememberedPhone', phone);
                    } else {
                        localStorage.removeItem('rememberedPhone');
                    }
                    
                    showNotification('Sign in successful!');
                    
                    // In a real app, you would redirect to a dashboard or perform other actions
                    // For this demo, we'll just show a notification
                } else {
                    showNotification('Invalid phone number or password', true);
                }
            }
        });

        signUpForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const phone = signUpPhone.value.trim();
            const password = signUpPassword.value.trim();
            
            let isValid = true;
            
            if (!validatePhoneNumber(phone)) {
                signUpPhone.classList.add('error');
                signUpPhoneError.classList.add('visible');
                isValid = false;
            } else {
                signUpPhone.classList.remove('error');
                signUpPhoneError.classList.remove('visible');
            }
            
            if (!validatePassword(password)) {
                signUpPassword.classList.add('error');
                signUpPasswordError.classList.add('visible');
                isValid = false;
            } else {
                signUpPassword.classList.remove('error');
                signUpPasswordError.classList.remove('visible');
            }
            
            if (isValid) {
                // Check if account already exists
                const accountExists = accounts.some(acc => acc.phone === phone);
                
                if (accountExists) {
                    showNotification('Account with this phone number already exists. Please sign in.', true);
                    return;
                }
                
                // Create new account
                const newAccount = {
                    phone,
                    password,
                    createdAt: new Date().toISOString(),
                    isFirstTime: true
                };
                
                accounts.push(newAccount);
                localStorage.setItem('workAccounts', JSON.stringify(accounts));
                
                // Store remembered phone number if checked
                if (rememberSignUp.checked) {
                    localStorage.setItem('rememberedPhone', phone);
                }
                
                showNotification('Account created successfully!');
                
                // Reset form
                signUpForm.reset();
                updatePasswordStrength('');
                
                // Switch to sign in tab
                signInTab.click();
            }
        });

        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') {
                const activeElement = document.activeElement;
                
                if (activeElement === signInPhone && !signInPhone.classList.contains('error')) {
                    signInPassword.focus();
                } else if (activeElement === signInPassword && !signInPassword.classList.contains('error')) {
                    signInForm.dispatchEvent(new Event('submit'));
                } else if (activeElement === signUpPhone && !signUpPhone.classList.contains('error')) {
                    signUpPassword.focus();
                } else if (activeElement === signUpPassword && !signUpPassword.classList.contains('error')) {
                    signUpForm.dispatchEvent(new Event('submit'));
                }
            }
        });
    </script>
</body>
</html>
