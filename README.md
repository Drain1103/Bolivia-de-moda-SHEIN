
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Work Account System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #4361ee;
            --secondary-color: #3f37c9;
            --success-color: #4cc9f0;
            --danger-color: #f72585;
            --warning-color: #f8961e;
            --light-color: #f8f9fa;
            --dark-color: #212529;
            --gray-color: #6c757d;
            --border-radius: 8px;
            --box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f7fb;
            color: var(--dark-color);
            transition: var(--transition);
        }

        body.dark-mode {
            background-color: #121212;
            color: #e0e0e0;
        }

        .dark-mode .card {
            background-color: #1e1e1e;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }

        .dark-mode input, 
        .dark-mode .form-select {
            background-color: #2d2d2d;
            color: #e0e0e0;
            border-color: #444;
        }

        .dark-mode .btn-primary {
            background-color: var(--primary-color);
            border-color: var(--primary-color);
        }

        .dark-mode .btn-outline-secondary {
            color: #e0e0e0;
            border-color: #444;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .card {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 30px;
            margin-bottom: 20px;
            transition: var(--transition);
        }

        .auth-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }

        .auth-tabs {
            display: flex;
            margin-bottom: 30px;
            width: 100%;
            max-width: 400px;
        }

        .auth-tab {
            flex: 1;
            text-align: center;
            padding: 15px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
            font-weight: 600;
            transition: var(--transition);
        }

        .auth-tab.active {
            border-bottom: 2px solid var(--primary-color);
            color: var(--primary-color);
        }

        .auth-form {
            width: 100%;
            max-width: 400px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 16px;
            transition: var(--transition);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
        }

        .password-container {
            position: relative;
        }

        .password-toggle {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: var(--gray-color);
        }

        .btn {
            display: inline-block;
            padding: 12px 20px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            text-align: center;
            transition: var(--transition);
            width: 100%;
        }

        .btn:hover {
            background-color: var(--secondary-color);
            transform: translateY(-2px);
        }

        .btn-outline-secondary {
            background-color: transparent;
            border: 1px solid var(--gray-color);
            color: var(--gray-color);
        }

        .btn-outline-secondary:hover {
            background-color: var(--gray-color);
            color: white;
        }

        .form-check {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .form-check-input {
            margin-right: 10px;
        }

        .form-check-label {
            margin-bottom: 0;
        }

        .forgot-password {
            text-align: right;
            font-size: 14px;
            color: var(--primary-color);
            text-decoration: none;
            transition: var(--transition);
        }

        .forgot-password:hover {
            text-decoration: underline;
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: var(--border-radius);
            background-color: white;
            box-shadow: var(--box-shadow);
            transform: translateX(150%);
            transition: transform 0.3s ease;
            z-index: 1000;
            display: flex;
            align-items: center;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.success {
            border-left: 4px solid var(--success-color);
        }

        .notification.error {
            border-left: 4px solid var(--danger-color);
        }

        .notification-icon {
            margin-right: 15px;
            font-size: 20px;
        }

        .notification.success .notification-icon {
            color: var(--success-color);
        }

        .notification.error .notification-icon {
            color: var(--danger-color);
        }

        .admin-container {
            display: none;
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .admin-title {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-color);
        }

        .admin-actions {
            display: flex;
            gap: 10px;
        }

        .search-container {
            margin-bottom: 20px;
        }

        .search-input {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 16px;
            transition: var(--transition);
        }

        .search-input:focus {
            outline: none;
            border-color: var(--primary-color);
        }

        .table-container {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        th {
            background-color: #f8f9fa;
            font-weight: 600;
            cursor: pointer;
        }

        th:hover {
            background-color: #e9ecef;
        }

        tr:hover {
            background-color: #f5f5f5;
        }

        .dark-mode th {
            background-color: #2d2d2d;
        }

        .dark-mode tr:hover {
            background-color: #2d2d2d;
        }

        .duplicate {
            background-color: rgba(247, 37, 133, 0.1);
        }

        .dark-mode .duplicate {
            background-color: rgba(247, 37, 133, 0.2);
        }

        .password-cell {
            position: relative;
        }

        .password-value {
            max-width: 100px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }

        .stats-container {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
        }

        .stat-card {
            flex: 1;
            padding: 20px;
            border-radius: var(--border-radius);
            background-color: white;
            box-shadow: var(--box-shadow);
            text-align: center;
        }

        .stat-card h3 {
            font-size: 24px;
            margin-bottom: 5px;
            color: var(--primary-color);
        }

        .stat-card p {
            color: var(--gray-color);
            margin: 0;
        }

        .dark-mode .stat-card {
            background-color: #1e1e1e;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }

        .admin-login {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }

        .admin-login-form {
            width: 100%;
            max-width: 350px;
        }

        .admin-login-title {
            text-align: center;
            margin-bottom: 30px;
        }

        .toggle-container {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .toggle-label {
            margin-right: 10px;
            font-size: 14px;
        }

        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 50px;
            height: 24px;
        }

        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .toggle-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 24px;
        }

        .toggle-slider:before {
            position: absolute;
            content: "";
            height: 16px;
            width: 16px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .toggle-slider {
            background-color: var(--primary-color);
        }

        input:checked + .toggle-slider:before {
            transform: translateX(26px);
        }

        .action-cell {
            display: flex;
            gap: 10px;
        }

        .btn-icon {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 16px;
            color: var(--gray-color);
            transition: var(--transition);
        }

        .btn-icon:hover {
            color: var(--danger-color);
        }

        .hidden {
            display: none;
        }

        @media (max-width: 768px) {
            .auth-tabs {
                width: 100%;
            }
            
            .auth-form {
                width: 100%;
            }
            
            .stats-container {
                flex-direction: column;
            }
            
            .admin-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }
            
            .admin-actions {
                width: 100%;
            }
            
            .btn {
                padding: 10px 15px;
            }
        }
    </style>
</head>
<body>
    <!-- Notification Component -->
    <div class="notification" id="notification">
        <div class="notification-icon">
            <i class="fas fa-check-circle"></i>
        </div>
        <div class="notification-content">
            <div class="notification-message">Notification message</div>
        </div>
    </div>

    <!-- User Authentication Container -->
    <div class="auth-container" id="authContainer">
        <div class="toggle-container">
            <span class="toggle-label">Dark Mode</span>
            <label class="toggle-switch">
                <input type="checkbox" id="darkModeToggle">
                <span class="toggle-slider"></span>
            </label>
        </div>

        <div class="auth-tabs">
            <div class="auth-tab active" id="signInTab">Sign In</div>
            <div class="auth-tab" id="signUpTab">Create Work Account</div>
        </div>

        <div class="auth-form" id="signInForm">
            <div class="form-group">
                <label for="signInPhone" class="form-label">Phone Number</label>
                <input type="tel" id="signInPhone" class="form-control" placeholder="Enter your phone number">
                <small class="form-text text-muted">We'll never share your phone number with anyone else.</small>
            </div>
            <div class="form-group">
                <label for="signInPassword" class="form-label">Password</label>
                <div class="password-container">
                    <input type="password" id="signInPassword" class="form-control" placeholder="Enter 6-digit password">
                    <span class="password-toggle" id="signInPasswordToggle">
                        <i class="fas fa-eye"></i>
                    </span>
                </div>
            </div>
            <div class="form-check">
                <input type="checkbox" class="form-check-input" id="rememberMe">
                <label class="form-check-label" for="rememberMe">Remember me</label>
            </div>
            <button type="button" class="btn" id="signInButton">Sign In</button>
            <div class="text-center mt-3">
                <a href="#" class="forgot-password">Forgot Password?</a>
            </div>
        </div>

        <div class="auth-form hidden" id="signUpForm">
            <div class="form-group">
                <label for="signUpPhone" class="form-label">Phone Number</label>
                <input type="tel" id="signUpPhone" class="form-control" placeholder="Enter your phone number">
                <small class="form-text text-muted">We'll never share your phone number with anyone else.</small>
            </div>
            <div class="form-group">
                <label for="signUpPassword" class="form-label">Password</label>
                <div class="password-container">
                    <input type="password" id="signUpPassword" class="form-control" placeholder="Enter 6-digit password">
                    <span class="password-toggle" id="signUpPasswordToggle">
                        <i class="fas fa-eye"></i>
                    </span>
                </div>
            </div>
            <div class="form-group">
                <label for="confirmPassword" class="form-label">Confirm Password</label>
                <div class="password-container">
                    <input type="password" id="confirmPassword" class="form-control" placeholder="Confirm your password">
                    <span class="password-toggle" id="confirmPasswordToggle">
                        <i class="fas fa-eye"></i>
                    </span>
                </div>
            </div>
            <div class="form-check">
                <input type="checkbox" class="form-check-input" id="rememberMeSignUp">
                <label class="form-check-label" for="rememberMeSignUp">Remember me</label>
            </div>
            <button type="button" class="btn" id="signUpButton">Create Work Account</button>
        </div>
    </div>

    <!-- Admin Login Container -->
    <div class="admin-login hidden" id="adminLoginContainer">
        <div class="card admin-login-form">
            <h2 class="admin-login-title">Admin Login</h2>
            <div class="form-group">
                <label for="adminPin" class="form-label">Admin PIN</label>
                <input type="password" id="adminPin" class="form-control" placeholder="Enter admin PIN">
            </div>
            <button type="button" class="btn" id="adminLoginButton">Access Admin Panel</button>
        </div>
    </div>

    <!-- Admin Dashboard Container -->
    <div class="admin-container hidden" id="adminContainer">
        <div class="container">
            <div class="admin-header">
                <div class="admin-title">Work Account Tracker</div>
                <div class="admin-actions">
                    <button class="btn btn-outline-secondary" id="adminLogoutButton">
                        <i class="fas fa-sign-out-alt"></i> Logout
                    </button>
                </div>
            </div>

            <div class="toggle-container">
                <span class="toggle-label">Dark Mode</span>
                <label class="toggle-switch">
                    <input type="checkbox" id="adminDarkModeToggle">
                    <span class="toggle-slider"></span>
                </label>
            </div>

            <div class="stats-container">
                <div class="stat-card">
                    <h3 id="totalAccounts">0</h3>
                    <p>Total Accounts</p>
                </div>
                <div class="stat-card">
                    <h3 id="newToday">0</h3>
                    <p>New Today</p>
                </div>
                <div class="stat-card">
                    <h3 id="firstTimeUsers">0</h3>
                    <p>First Time Users</p>
                </div>
            </div>

            <div class="search-container">
                <input type="text" id="searchInput" class="search-input" placeholder="Search by phone number...">
            </div>

            <div class="card">
                <div class="table-container">
                    <table id="accountsTable">
                        <thead>
                            <tr>
                                <th data-sort="phone">Phone Number <i class="fas fa-sort"></i></th>
                                <th data-sort="password">Password <i class="fas fa-sort"></i></th>
                                <th data-sort="date">Date & Time <i class="fas fa-sort"></i></th>
                                <th data-sort="firstTime">First Time <i class="fas fa-sort"></i></th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="accountsTableBody">
                            <!-- Table rows will be added dynamically -->
                        </tbody>
                    </table>
                </div>
            </div>

            <div class="card" style="margin-top: 20px;">
                <div class="form-group">
                    <button class="btn" id="exportCSVButton">
                        <i class="fas fa-file-csv"></i> Export as CSV
                    </button>
                    <button class="btn btn-outline-secondary" id="exportJSONButton" style="margin-left: 10px;">
                        <i class="fas fa-file-code"></i> Export as JSON
                    </button>
                    <div class="form-check" style="margin-top: 10px;">
                        <input type="checkbox" class="form-check-input" id="showPasswords">
                        <label class="form-check-label" for="showPasswords">Show passwords in export</label>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // DOM Elements
        const authContainer = document.getElementById('authContainer');
        const adminLoginContainer = document.getElementById('adminLoginContainer');
        const adminContainer = document.getElementById('adminContainer');
        const signInTab = document.getElementById('signInTab');
        const signUpTab = document.getElementById('signUpTab');
        const signInForm = document.getElementById('signInForm');
        const signUpForm = document.getElementById('signUpForm');
        const signInPhone = document.getElementById('signInPhone');
        const signInPassword = document.getElementById('signInPassword');
        const signUpPhone = document.getElementById('signUpPhone');
        const signUpPassword = document.getElementById('signUpPassword');
        const confirmPassword = document.getElementById('confirmPassword');
        const rememberMe = document.getElementById('rememberMe');
        const rememberMeSignUp = document.getElementById('rememberMeSignUp');
        const signInButton = document.getElementById('signInButton');
        const signUpButton = document.getElementById('signUpButton');
        const signInPasswordToggle = document.getElementById('signInPasswordToggle');
        const signUpPasswordToggle = document.getElementById('signUpPasswordToggle');
        const confirmPasswordToggle = document.getElementById('confirmPasswordToggle');
        const adminPin = document.getElementById('adminPin');
        const adminLoginButton = document.getElementById('adminLoginButton');
        const adminLogoutButton = document.getElementById('adminLogoutButton');
        const accountsTableBody = document.getElementById('accountsTableBody');
        const searchInput = document.getElementById('searchInput');
        const exportCSVButton = document.getElementById('exportCSVButton');
        const exportJSONButton = document.getElementById('exportJSONButton');
        const showPasswords = document.getElementById('showPasswords');
        const totalAccounts = document.getElementById('totalAccounts');
        const newToday = document.getElementById('newToday');
        const firstTimeUsers = document.getElementById('firstTimeUsers');
        const notification = document.getElementById('notification');
        const darkModeToggle = document.getElementById('darkModeToggle');
        const adminDarkModeToggle = document.getElementById('adminDarkModeToggle');

        // Constants
        const ADMIN_PIN = '1234'; // In a real app, this should be stored securely
        const STORAGE_KEY = 'workAccountSystem';

        // State
        let accounts = JSON.parse(localStorage.getItem(STORAGE_KEY)) || [];
        let currentSort = { column: 'date', direction: 'desc' };
        let filteredAccounts = [...accounts];

        // Initialize
        function init() {
            // Check for remembered phone number
            const rememberedPhone = localStorage.getItem('rememberedPhone');
            if (rememberedPhone) {
                signInPhone.value = rememberedPhone;
                signUpPhone.value = rememberedPhone;
            }

            // Check for dark mode preference
            const isDarkMode = localStorage.getItem('darkMode') === 'true';
            if (isDarkMode) {
                document.body.classList.add('dark-mode');
                darkModeToggle.checked = true;
                adminDarkModeToggle.checked = true;
            }

            // Render accounts table
            renderAccountsTable();
            updateStats();
        }

        // Tab switching
        signInTab.addEventListener('click', () => {
            signInTab.classList.add('active');
            signUpTab.classList.remove('active');
            signInForm.classList.remove('hidden');
            signUpForm.classList.add('hidden');
        });

        signUpTab.addEventListener('click', () => {
            signUpTab.classList.add('active');
            signInTab.classList.remove('active');
            signUpForm.classList.remove('hidden');
            signInForm.classList.add('hidden');
        });

        // Password visibility toggle
        signInPasswordToggle.addEventListener('click', () => {
            togglePasswordVisibility(signInPassword, signInPasswordToggle.querySelector('i'));
        });

        signUpPasswordToggle.addEventListener('click', () => {
            togglePasswordVisibility(signUpPassword, signUpPasswordToggle.querySelector('i'));
        });

        confirmPasswordToggle.addEventListener('click', () => {
            togglePasswordVisibility(confirmPassword, confirmPasswordToggle.querySelector('i'));
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

        // Form validation
        function validatePhoneNumber(phone) {
            // Basic validation - can be enhanced with country codes
            return /^\d{10}$/.test(phone);
        }

        function validatePassword(password) {
            // 6-digit numeric password
            return /^\d{6}$/.test(password);
        }

        function validateSignUp() {
            const phone = signUpPhone.value.trim();
            const password = signUpPassword.value;
            const confirmPwd = confirmPassword.value;
            
            if (!validatePhoneNumber(phone)) {
                showNotification('Please enter a valid 10-digit phone number', 'error');
                return false;
            }
            
            if (!validatePassword(password)) {
                showNotification('Password must be exactly 6 digits', 'error');
                return false;
            }
            
            if (password !== confirmPwd) {
                showNotification('Passwords do not match', 'error');
                return false;
            }
            
            return true;
        }

        function validateSignIn() {
            const phone = signInPhone.value.trim();
            const password = signInPassword.value;
            
            if (!validatePhoneNumber(phone)) {
                showNotification('Please enter a valid 10-digit phone number', 'error');
                return false;
            }
            
            if (!validatePassword(password)) {
                showNotification('Password must be exactly 6 digits', 'error');
                return false;
            }
            
            return true;
        }

        // Sign Up
        signUpButton.addEventListener('click', () => {
            if (!validateSignUp()) return;
            
            const phone = signUpPhone.value.trim();
            const password = signUpPassword.value;
            const isFirstTime = !accounts.some(account => account.phone === phone);
            
            const newAccount = {
                phone,
                password,
                date: new Date().toISOString(),
                firstTime: isFirstTime
            };
            
            accounts.push(newAccount);
            localStorage.setItem(STORAGE_KEY, JSON.stringify(accounts));
            
            // Remember phone number if checked
            if (rememberMeSignUp.checked) {
                localStorage.setItem('rememberedPhone', phone);
            }
            
            showNotification('Account created successfully!', 'success');
            
            // Reset form
            signUpForm.reset();
            
            // Switch to sign in tab
            signInTab.click();
        });

        // Sign In
        signInButton.addEventListener('click', () => {
            if (!validateSignIn()) return;
            
            const phone = signInPhone.value.trim();
            const password = signInPassword.value;
            
            const account = accounts.find(account => 
                account.phone === phone && account.password === password
            );
            
            if (account) {
                showNotification('Sign in successful!', 'success');
                
                // Remember phone number if checked
                if (rememberMe.checked) {
                    localStorage.setItem('rememberedPhone', phone);
                }
            } else {
                showNotification('Invalid phone number or password', 'error');
            }
        });

        // Admin Login
        adminLoginButton.addEventListener('click', () => {
            const pin = adminPin.value;
            
            if (pin === ADMIN_PIN) {
                adminLoginContainer.classList.add('hidden');
                adminContainer.classList.remove('hidden');
                showNotification('Admin access granted', 'success');
            } else {
                showNotification('Invalid admin PIN', 'error');
                adminPin.value = '';
            }
        });

        // Admin Logout
        adminLogoutButton.addEventListener('click', () => {
            adminContainer.classList.add('hidden');
            adminLoginContainer.classList.remove('hidden');
            adminPin.value = '';
        });

        // Render accounts table
        function renderAccountsTable() {
            // Apply search filter
            const searchTerm = searchInput.value.toLowerCase();
            filteredAccounts = accounts.filter(account => 
                account.phone.toLowerCase().includes(searchTerm)
            );
            
            // Sort accounts
            sortAccounts(currentSort.column, currentSort.direction);
            
            // Clear table
            accountsTableBody.innerHTML = '';
            
            // Check for duplicate phone numbers
            const phoneNumbers = new Set();
            const duplicatePhones = new Set();
            
            accounts.forEach(account => {
                if (phoneNumbers.has(account.phone)) {
                    duplicatePhones.add(account.phone);
                } else {
                    phoneNumbers.add(account.phone);
                }
            });
            
            // Render rows
            filteredAccounts.forEach(account => {
                const row = document.createElement('tr');
                
                if (duplicatePhones.has(account.phone)) {
                    row.classList.add('duplicate');
                }
                
                const date = new Date(account.date);
                const formattedDate = `${date.toLocaleDateString()} ${date.toLocaleTimeString()}`;
                
                const passwordDisplay = showPasswords.checked ? 
                    account.password : 
                    '••••••';
                
                row.innerHTML = `
                    <td>${account.phone}</td>
                    <td class="password-cell">
                        <div class="password-value">${passwordDisplay}</div>
                    </td>
                    <td>${formattedDate}</td>
                    <td>${account.firstTime ? '<i class="fas fa-check-circle" style="color: #4cc9f0;"></i>' : '<i class="fas fa-times-circle" style="color: #f72585;"></i>'}</td>
                    <td class="action-cell">
                        <button class="btn-icon delete-account" data-phone="${account.phone}">
                            <i class="fas fa-trash-alt"></i>
                        </button>
                    </td>
                `;
                
                accountsTableBody.appendChild(row);
            });
            
            // Add event listeners to delete buttons
            document.querySelectorAll('.delete-account').forEach(button => {
                button.addEventListener('click', (e) => {
                    const phone = e.currentTarget.dataset.phone;
                    deleteAccount(phone);
                });
            });
        }

        // Sort accounts
        function sortAccounts(column, direction) {
            filteredAccounts.sort((a, b) => {
                let valueA, valueB;
                
                if (column === 'date') {
                    valueA = new Date(a.date).getTime();
                    valueB = new Date(b.date).getTime();
                } else {
                    valueA = a[column];
                    valueB = b[column];
                }
                
                if (valueA < valueB) return direction === 'asc' ? -1 : 1;
                if (valueA > valueB) return direction === 'asc' ? 1 : -1;
                return 0;
            });
        }

        // Delete account
        function deleteAccount(phone) {
            if (confirm('Are you sure you want to delete this account?')) {
                accounts = accounts.filter(account => account.phone !== phone);
                localStorage.setItem(STORAGE_KEY, JSON.stringify(accounts));
                renderAccountsTable();
                updateStats();
                showNotification('Account deleted successfully', 'success');
            }
        }

        // Search functionality
        searchInput.addEventListener('input', () => {
            renderAccountsTable();
        });

        // Export functionality
        exportCSVButton.addEventListener('click', () => {
            exportToCSV();
        });

        exportJSONButton.addEventListener('click', () => {
            exportToJSON();
        });

        function exportToCSV() {
            let csv = 'Phone Number,Password,Date & Time,First Time?\n';
            
            accounts.forEach(account => {
                const date = new Date(account.date);
                const formattedDate = `${date.toLocaleDateString()} ${date.toLocaleTimeString()}`;
                const password = showPasswords.checked ? account.password : '••••••';
                const firstTime = account.firstTime ? '✅' : '❌';
                
                csv += `"${account.phone}","${password}","${formattedDate}","${firstTime}"\n`;
            });
            
            downloadFile(csv, 'accounts.csv', 'text/csv');
            showNotification('CSV file exported successfully', 'success');
        }

        function exportToJSON() {
            let json = JSON.stringify(accounts, (key, value) => {
                // Handle circular references and format dates
                if (key === 'date') {
                    return new Date(value).toISOString();
                }
                return value;
            }, 2);
            
            downloadFile(json, 'accounts.json', 'application/json');
            showNotification('JSON file exported successfully', 'success');
        }

        function downloadFile(content, fileName, contentType) {
            const blob = new Blob([content], { type: contentType });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = fileName;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }

        // Update statistics
        function updateStats() {
            totalAccounts.textContent = accounts.length;
            
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            
            const newTodayCount = accounts.filter(account => {
                const accountDate = new Date(account.date);
                accountDate.setHours(0, 0, 0, 0);
                return accountDate.getTime() === today.getTime();
            }).length;
            
            newToday.textContent = newTodayCount;
            
            const firstTimeCount = accounts.filter(account => account.firstTime).length;
            firstTimeUsers.textContent = firstTimeCount;
        }

        // Table sorting
        document.querySelectorAll('th[data-sort]').forEach(th => {
            th.addEventListener('click', () => {
                const column = th.dataset.sort;
                let direction = 'asc';
                
                if (currentSort.column === column) {
                    direction = currentSort.direction === 'asc' ? 'desc' : 'asc';
                }
                
                currentSort = { column, direction };
                
                // Update sort indicators
                document.querySelectorAll('th[data-sort] i').forEach(icon => {
                    icon.className = 'fas fa-sort';
                });
                
                const icon = th.querySelector('i');
                icon.className = direction === 'asc' ? 'fas fa-sort-up' : 'fas fa-sort-down';
                
                renderAccountsTable();
            });
        });

        // Show passwords toggle
        showPasswords.addEventListener('change', () => {
            renderAccountsTable();
        });

        // Notification
        function showNotification(message, type) {
            notification.className = `notification ${type}`;
            notification.querySelector('.notification-message').textContent = message;
            
            // Update icon
            const icon = notification.querySelector('.notification-icon i');
            if (type === 'success') {
                icon.className = 'fas fa-check-circle';
            } else {
                icon.className = 'fas fa-exclamation-circle';
            }
            
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Dark mode toggle
        darkModeToggle.addEventListener('change', () => {
            document.body.classList.toggle('dark-mode');
            adminDarkModeToggle.checked = darkModeToggle.checked;
            localStorage.setItem('darkMode', darkModeToggle.checked);
        });

        adminDarkModeToggle.addEventListener('change', () => {
            document.body.classList.toggle('dark-mode');
            darkModeToggle.checked = adminDarkModeToggle.checked;
            localStorage.setItem('darkMode', adminDarkModeToggle.checked);
        });

        // Initialize the app
        init();
    </script>
</body>
</html>
