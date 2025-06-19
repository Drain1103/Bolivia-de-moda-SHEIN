<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Work Account System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #3498db;
            --secondary-color: #2980b9;
            --success-color: #2ecc71;
            --danger-color: #e74c3c;
            --warning-color: #f39c12;
            --light-color: #f8f9fa;
            --dark-color: #343a40;
            --gray-color: #6c757d;
            --border-radius: 8px;
            --box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }

        body.dark-mode {
            background-color: #1a1a1a;
            color: #f5f5f5;
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
            margin-bottom: 30px;
            transition: var(--transition);
        }

        body.dark-mode .card {
            background-color: #2d2d2d;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }

        h1, h2, h3 {
            color: var(--dark-color);
            margin-top: 0;
        }

        body.dark-mode h1, body.dark-mode h2, body.dark-mode h3 {
            color: var(--light-color);
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
        }

        input[type="text"],
        input[type="tel"],
        input[type="password"],
        input[type="date"],
        select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 16px;
            transition: var(--transition);
        }

        body.dark-mode input[type="text"],
        body.dark-mode input[type="tel"],
        body.dark-mode input[type="password"],
        body.dark-mode input[type="date"],
        body.dark-mode select {
            background-color: #3d3d3d;
            border-color: #555;
            color: #fff;
        }

        input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.25);
        }

        .btn {
            display: inline-block;
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: var(--transition);
            text-align: center;
        }

        .btn:hover {
            background-color: var(--secondary-color);
            transform: translateY(-2px);
        }

        .btn-block {
            display: block;
            width: 100%;
        }

        .btn-secondary {
            background-color: var(--gray-color);
        }

        .btn-secondary:hover {
            background-color: #5a6268;
        }

        .btn-success {
            background-color: var(--success-color);
        }

        .btn-success:hover {
            background-color: #27ae60;
        }

        .form-control {
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

        .form-switch {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .form-switch input {
            margin-right: 10px;
        }

        .tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid #ddd;
        }

        body.dark-mode .tabs {
            border-bottom-color: #555;
        }

        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            font-weight: 600;
            transition: var(--transition);
        }

        .tab.active {
            border-bottom-color: var(--primary-color);
            color: var(--primary-color);
        }

        body.dark-mode .tab.active {
            color: var(--primary-color);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .notification {
            padding: 15px;
            margin-bottom: 20px;
            border-radius: var(--border-radius);
            display: none;
        }

        .notification.success {
            background-color: rgba(46, 204, 113, 0.2);
            border: 1px solid var(--success-color);
            color: var(--success-color);
        }

        .notification.error {
            background-color: rgba(231, 76, 60, 0.2);
            border: 1px solid var(--danger-color);
            color: var(--danger-color);
        }

        body.dark-mode .notification.success {
            background-color: rgba(46, 204, 113, 0.3);
            color: #2ecc71;
        }

        body.dark-mode .notification.error {
            background-color: rgba(231, 76, 60, 0.3);
            color: #e74c3c;
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .checkbox-group input {
            margin-right: 10px;
        }

        .admin-controls {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .admin-controls > div {
            margin-bottom: 10px;
            flex: 1;
            min-width: 200px;
            margin-right: 10px;
        }

        .admin-controls > div:last-child {
            margin-right: 0;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        body.dark-mode th, body.dark-mode td {
            border-bottom-color: #555;
        }

        th {
            background-color: #f8f9fa;
            font-weight: 600;
            cursor: pointer;
        }

        body.dark-mode th {
            background-color: #3d3d3d;
        }

        tr:hover {
            background-color: rgba(52, 152, 219, 0.05);
        }

        body.dark-mode tr:hover {
            background-color: rgba(52, 152, 219, 0.1);
        }

        .duplicate {
            background-color: rgba(243, 156, 18, 0.1);
        }

        body.dark-mode .duplicate {
            background-color: rgba(243, 156, 18, 0.2);
        }

        .badge {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: 600;
        }

        .badge-success {
            background-color: rgba(46, 204, 113, 0.2);
            color: var(--success-color);
        }

        .badge-danger {
            background-color: rgba(231, 76, 60, 0.2);
            color: var(--danger-color);
        }

        .password-cell {
            max-width: 120px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 30px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        body.dark-mode .modal-content {
            background-color: #2d2d2d;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--gray-color);
        }

        body.dark-mode .modal-close {
            color: #aaa;
        }

        .modal-footer {
            margin-top: 20px;
            text-align: right;
        }

        .hidden {
            display: none;
        }

        .admin-section {
            display: none;
        }

        .user-section {
            display: block;
        }

        .mode-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: var(--dark-color);
            color: white;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: var(--box-shadow);
            z-index: 100;
            transition: var(--transition);
        }

        .mode-toggle:hover {
            transform: rotate(30deg);
        }

        @media (max-width: 768px) {
            .card {
                padding: 20px;
            }

            .admin-controls > div {
                min-width: 100%;
                margin-right: 0;
            }

            th, td {
                padding: 10px;
            }

            .admin-controls {
                flex-direction: column;
            }
        }

        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top-color: white;
            animation: spin 1s ease-in-out infinite;
            margin-left: 10px;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        .export-options {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .export-btn {
            flex: 1;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- User Section -->
        <div class="user-section">
            <div class="card">
                <h1>Create Your Work Account</h1>
                <p>Sign up or sign in to access your work account.</p>
                
                <div class="tabs">
                    <div class="tab active" data-tab="signup">Sign Up</div>
                    <div class="tab" data-tab="signin">Sign In</div>
                </div>
                
                <div class="notification success" id="success-notification">
                    <i class="fas fa-check-circle"></i> <span id="success-message"></span>
                </div>
                
                <div class="notification error" id="error-notification">
                    <i class="fas fa-exclamation-circle"></i> <span id="error-message"></span>
                </div>
                
                <!-- Sign Up Form -->
                <div class="tab-content active" id="signup-content">
                    <form id="signup-form">
                        <div class="form-group">
                            <label for="signup-phone">Phone Number</label>
                            <div class="form-control">
                                <input type="tel" id="signup-phone" placeholder="Enter your phone number" required>
                                <i class="fas fa-phone" style="position: absolute; right: 50px; color: var(--gray-color);"></i>
                            </div>
                            <small id="phone-help" class="form-text">Format: +1 (123) 456-7890</small>
                        </div>
                        
                        <div class="form-group">
                            <label for="signup-password">Password</label>
                            <div class="form-control">
                                <input type="password" id="signup-password" placeholder="6-digit numeric password" required>
                                <i class="fas fa-eye password-toggle" id="signup-password-toggle"></i>
                            </div>
                            <small id="password-help" class="form-text">Exactly 6 digits (numbers only)</small>
                        </div>
                        
                        <div class="checkbox-group">
                            <input type="checkbox" id="remember-me">
                            <label for="remember-me">Remember my phone number</label>
                        </div>
                        
                        <button type="submit" class="btn btn-block btn-success">
                            Create Work Account
                        </button>
                    </form>
                </div>
                
                <!-- Sign In Form -->
                <div class="tab-content" id="signin-content">
                    <form id="signin-form">
                        <div class="form-group">
                            <label for="signin-phone">Phone Number</label>
                            <div class="form-control">
                                <input type="tel" id="signin-phone" placeholder="Enter your phone number" required>
                                <i class="fas fa-phone" style="position: absolute; right: 50px; color: var(--gray-color);"></i>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="signin-password">Password</label>
                            <div class="form-control">
                                <input type="password" id="signin-password" placeholder="6-digit numeric password" required>
                                <i class="fas fa-eye password-toggle" id="signin-password-toggle"></i>
                            </div>
                        </div>
                        
                        <div class="checkbox-group">
                            <input type="checkbox" id="signin-remember">
                            <label for="signin-remember">Remember my phone number</label>
                        </div>
                        
                        <div class="form-group">
                            <a href="#" id="forgot-password" style="color: var(--primary-color); text-decoration: none;">Forgot Password?</a>
                        </div>
                        
                        <button type="submit" class="btn btn-block">
                            Sign In
                        </button>
                    </form>
                </div>
            </div>
        </div>
        
        <!-- Admin Section -->
        <div class="admin-section">
            <div class="card">
                <div class="admin-controls">
                    <div>
                        <label for="admin-search">Search</label>
                        <input type="text" id="admin-search" placeholder="Search by phone number...">
                    </div>
                    
                    <div>
                        <label for="admin-date-filter">Filter by Date</label>
                        <input type="date" id="admin-date-filter">
                    </div>
                    
                    <div>
                        <label for="show-passwords">Show Passwords</label>
                        <div class="form-switch">
                            <input type="checkbox" id="show-passwords">
                            <span class="toggle"></span>
                        </div>
                    </div>
                    
                    <div>
                        <label for="export-data">Export Data</label>
                        <div class="export-options">
                            <button class="btn btn-secondary export-btn" id="export-csv">
                                <i class="fas fa-file-csv"></i> CSV
                            </button>
                            <button class="btn btn-secondary export-btn" id="export-json">
                                <i class="fas fa-file-code"></i> JSON
                            </button>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <p>Total Accounts: <span id="total-accounts">0</span></p>
                </div>
                
                <table id="accounts-table">
                    <thead>
                        <tr>
                            <th data-sort="phone">Phone Number <i class="fas fa-sort"></i></th>
                            <th data-sort="password">Password <i class="fas fa-sort"></i></th>
                            <th data-sort="date">Date & Time <i class="fas fa-sort"></i></th>
                            <th data-sort="firstTime">First Time? <i class="fas fa-sort"></i></th>
                        </tr>
                    </thead>
                    <tbody id="accounts-body">
                        <!-- Account data will be inserted here -->
                    </tbody>
                </table>
                
                <div class="form-group" style="margin-top: 20px;">
                    <button class="btn btn-secondary" id="admin-logout">
                        <i class="fas fa-sign-out-alt"></i> Exit Admin Mode
                    </button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Admin Login Modal -->
    <div class="modal" id="admin-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Admin Login</h2>
                <button class="modal-close" id="close-admin-modal">&times;</button>
            </div>
            <form id="admin-login-form">
                <div class="form-group">
                    <label for="admin-pin">Admin PIN</label>
                    <input type="password" id="admin-pin" placeholder="Enter admin PIN" required>
                </div>
                <div class="-footer">
                    <button type="submit" class="btn">
                        Login
                        <span class="loading" id="admin-loading" style="display: none;"></span>
                    </button>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Forgot Password Modal -->
    <div class="modal" id="forgot-password-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Reset Password</h2>
                <button class="modal-close" id="close-forgot-modal">&times;</button>
            </div>
            <p>Enter your phone number to receive password reset instructions.</p>
            <form id="forgot-password-form">
                <div class="form-group">
                    <label for="reset-phone">Phone Number</label>
                    <input type="tel" id="reset-phone" placeholder="Enter your phone number" required>
                </div>
                <div class="modal-footer">
                    <button type="submit" class="btn">
                        Send Reset Link
                    </button>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Mode Toggle Button -->
    <button class="mode-toggle" id="mode-toggle">
        <i class="fas fa-moon"></i>
    </button>
    
    <!-- Admin Access Button (Hidden by default) -->
    <button class="btn" id="admin-access" style="position: fixed; bottom: 20px; left: 20px; z-index: 100; display: none;">
        <i class="fas fa-lock"></i> Admin Access
    </button>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM Elements
            const signupForm = document.getElementById('signup-form');
            const signinForm = document.getElementById('signin-form');
            const signupPhone = document.getElementById('signup-phone');
            const signupPassword = document.getElementById('signup-password');
            const signinPhone = document.getElementById('signin-phone');
            const signinPassword = document.getElementById('signin-password');
            const rememberMe = document.getElementById('remember-me');
            const signinRemember = document.getElementById('signin-remember');
            const successNotification = document.getElementById('success-notification');
            const errorNotification = document.getElementById('error-notification');
            const successMessage = document.getElementById('success-message');
            const errorMessage = document.getElementById('error-message');
            const tabs = document.querySelectorAll('.tab');
            const tabContents = document.querySelectorAll('.tab-content');
            const signupPasswordToggle = document.getElementById('signup-password-toggle');
            const signinPasswordToggle = document.getElementById('signin-password-toggle');
            const forgotPassword = document.getElementById('forgot-password');
            const forgotPasswordModal = document.getElementById('forgot-password-modal');
            const closeForgotModal = document.getElementById('close-forgot-modal');
            const forgotPasswordForm = document.getElementById('forgot-password-form');
            const resetPhone = document.getElementById('reset-phone');
            const adminModal = document.getElementById('admin-modal');
            const adminLoginForm = document.getElementById('admin-login-form');
            const adminPin = document.getElementById('admin-pin');
            const closeAdminModal = document.getElementById('close-admin-modal');
            const adminAccessBtn = document.getElementById('admin-access');
            const adminLogout = document.getElementById('admin-logout');
            const userSection = document.querySelector('.user-section');
            const adminSection = document.querySelector('.admin-section');
            const accountsBody = document.getElementById('accounts-body');
            const totalAccounts = document.getElementById('total-accounts');
            const adminSearch = document.getElementById('admin-search');
            const adminDateFilter = document.getElementById('admin-date-filter');
            const showPasswords = document.getElementById('show-passwords');
            const exportCsv = document.getElementById('export-csv');
            const exportJson = document.getElementById('export-json');
            const modeToggle = document.getElementById('mode-toggle');
            const adminLoading = document.getElementById('admin-loading');
            
            // State variables
            let accounts = JSON.parse(localStorage.getItem('workAccounts')) || [];
            let isDarkMode = localStorage.getItem('darkMode') === 'true';
            let currentSort = { column: 'date', direction: 'desc' };
            let adminPinValue = '1234'; // In a real app, this would be securely stored and verified
            
            // Initialize
            if (isDarkMode) {
                document.body.classList.add('dark-mode');
                modeToggle.innerHTML = '<i class="fas fa-sun"></i>';
            }
            
            // Check if we should show admin access button
            checkAdminAccess();
            
            // Load accounts into table
            renderAccountsTable();
            
            // Event Listeners
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    tabs.forEach(t => t.classList.remove('active'));
                    tabContents.forEach(tc => tc.classList.remove('active'));
                    
                    tab.classList.add('active');
                    document.getElementById(`${tab.dataset.tab}-content`).classList.add('active');
                });
            });
            
            signupPasswordToggle.addEventListener('click', () => {
                togglePasswordVisibility(signupPassword, signupPasswordToggle);
            });
            
            signinPasswordToggle.addEventListener('click', () => {
                togglePasswordVisibility(signinPassword, signinPasswordToggle);
            });
            
            // Phone number validation
            signupPhone.addEventListener('input', validatePhoneNumber);
            signinPhone.addEventListener('input', validatePhoneNumber);
            
            // Password validation
            signupPassword.addEventListener('input', validatePassword);
            
            // Remember me functionality
            rememberMe.addEventListener('change', () => {
                if (rememberMe.checked) {
                    localStorage.setItem('rememberedPhone', signupPhone.value);
                } else {
                    localStorage.removeItem('rememberedPhone');
                }
            });
            
            signinRemember.addEventListener('change', () => {
                if (signinRemember.checked) {
                    localStorage.setItem('rememberedPhone', signinPhone.value);
                } else {
                    localStorage.removeItem('rememberedPhone');
                }
            });
            
            // Load remembered phone if exists
            const rememberedPhone = localStorage.getItem('rememberedPhone');
            if (rememberedPhone) {
                signupPhone.value = rememberedPhone;
                signinPhone.value = rememberedPhone;
                rememberMe.checked = true;
                signinRemember.checked = true;
            }
            
            // Form submissions
            signupForm.addEventListener('submit', handleSignup);
            signinForm.addEventListener('submit', handleSignin);
            forgotPasswordForm.addEventListener('submit', handleForgotPassword);
            adminLoginForm.addEventListener('submit', handleAdminLogin);
            
            // Modal controls
            forgotPassword.addEventListener('click', () => {
                forgotPasswordModal.style.display = 'flex';
            });
            
            closeForgotModal.addEventListener('click', () => {
                forgotPasswordModal.style.display = 'none';
            });
            
            closeAdminModal.addEventListener('click', () => {
                adminModal.style.display = 'none';
            });
            
            // Admin access button
            adminAccessBtn.addEventListener('click', () => {
                adminModal.style.display = 'flex';
            });
            
            // Admin logout
            adminLogout.addEventListener('click', () => {
                userSection.style.display = 'block';
                adminSection.style.display = 'none';
                adminAccessBtn.style.display = 'none';
            });
            
            // Mode toggle
            modeToggle.addEventListener('click', () => {
                document.body.classList.toggle('dark-mode');
                isDarkMode = document.body.classList.contains('dark-mode');
                localStorage.setItem('darkMode', isDarkMode);
                
                if (isDarkMode) {
                    modeToggle.innerHTML = '<i class="fas fa-sun"></i>';
                } else {
                    modeToggle.innerHTML = '<i class="fas fa-moon"></i>';
                }
            });
            
            // Admin table controls
            document.querySelectorAll('th[data-sort]').forEach(th => {
                th.addEventListener('click', () => {
                    const column = th.dataset.sort;
                    if (currentSort.column === column) {
                        currentSort.direction = currentSort.direction === 'asc' ? 'desc' : 'asc';
                    } else {
                        currentSort.column = column;
                        currentSort.direction = 'asc';
                    }
                    renderAccountsTable();
                });
            });
            
            adminSearch.addEventListener('input', renderAccountsTable);
            adminDateFilter.addEventListener('change', renderAccountsTable);
            showPasswords.addEventListener('change', renderAccountsTable);
            
            exportCsv.addEventListener('click', () => {
                exportData('csv');
            });
            
            exportJson.addEventListener('click', () => {
                exportData('json');
            });
            
            // Window event for modal closing
            window.addEventListener('click', (e) => {
                if (e.target === forgotPasswordModal) {
                    forgotPasswordModal.style.display = 'none';
                }
                if (e.target === adminModal) {
                    adminModal.style.display = 'none';
                }
            });
            
            // Functions
            function togglePasswordVisibility(passwordField, toggleIcon) {
                if (passwordField.type === 'password') {
                    passwordField.type = 'text';
                    toggleIcon.classList.remove('fa-eye');
                    toggleIcon.classList.add('fa-eye-slash');
                } else {
                    passwordField.type = 'password';
                    toggleIcon.classList.remove('fa-eye-slash');
                    toggleIcon.classList.add('fa-eye');
                }
            }
            
            function validatePhoneNumber(e) {
                const phone = e.target.value;
                const phoneRegex = /^\+?[0-9]{1,3}[-. ]?\(?[0-9]{3}\)?[-. ]?[0-9]{3}[-. ]?[0-9]{4}$/;
                
                if (phone && !phoneRegex.test(phone)) {
                    showError('Please enter a valid phone number format (e.g., +1 (123) 456-7890)');
                    return false;
                }
                
                hideNotifications();
                return true;
            }
            
            function validatePassword(e) {
                const password = e.target.value;
                
                if (password && (!/^\d+$/.test(password) || password.length !== 6)) {
                    showError('Password must be exactly 6 digits');
                    return false;
                }
                
                hideNotifications();
                return true;
            }
            
            function hideNotifications() {
                successNotification.style.display = 'none';
                errorNotification.style.display = 'none';
            }
            
            function showSuccess(message) {
                successMessage.textContent = message;
                successNotification.style.display = 'block';
                errorNotification.style.display = 'none';
                
                // Auto-hide after 5 seconds
                setTimeout(() => {
                    successNotification.style.display = 'none';
                }, 5000);
            }
            
            function showError(message) {
                errorMessage.textContent = message;
                errorNotification.style.display = 'block';
                successNotification.style.display = 'none';
                
                // Auto-hide after 5 seconds
                setTimeout(() => {
                    errorNotification.style.display = 'none';
                }, 5000);
            }
            
            function handleSignup(e) {
                e.preventDefault();
                
                // Validate inputs
                if (!validatePhoneNumber({ target: signupPhone }) || !validatePassword({ target: signupPassword })) {
                    return;
                }
                
                const phone = signupPhone.value.trim();
                const password = signupPassword.value;
                const isFirstTime = !accounts.some(account => account.phone === phone);
                
                // Create new account
                const newAccount = {
                    phone,
                    password,
                    date: new Date().toISOString(),
                    firstTime: isFirstTime
                };
                
                // Add to accounts
                accounts.push(newAccount);
                localStorage.setItem('workAccounts', JSON.stringify(accounts));
                
                // Show success message
                showSuccess('Account created successfully!');
                
                // Reset form
                signupForm.reset();
                
                // Switch to sign in tab
                tabs[1].click();
                
                // Update remembered phone if checked
                if (rememberMe.checked) {
                    localStorage.setItem('rememberedPhone', phone);
                }
                
                // Update admin table
                renderAccountsTable();
                
                // Show admin access button if this is the first account
                if (accounts.length === 1) {
                    adminAccessBtn.style.display = 'block';
                }
            }
            
            function handleSignin(e) {
                e.preventDefault();
                
                const phone = signinPhone.value.trim();
                const password = signinPassword.value;
                
                // Find account
                const account = accounts.find(acc => acc.phone === phone && acc.password === password);
                
                if (account) {
                    showSuccess('Login successful!');
                    
                    // Update remembered phone if checked
                    if (signinRemember.checked) {
                        localStorage.setItem('rememberedPhone', phone);
                    }
                    
                    // Reset form
                    signinForm.reset();
                } else {
                    showError('Invalid phone number or password');
                }
            }
            
            function handleForgotPassword(e) {
                e.preventDefault();
                
                const phone = resetPhone.value.trim();
                
                if (accounts.some(account => account.phone === phone)) {
                    showSuccess('Password reset link sent to your phone number');
                } else {
                    showError('Phone number not found');
                }
                
                forgotPasswordModal.style.display = 'none';
                forgotPasswordForm.reset();
            }
            
            function handleAdminLogin(e) {
                e.preventDefault();
                
                adminLoading.style.display = 'inline-block';
                
                // Simulate loading
                setTimeout(() => {
                    if (adminPin.value === adminPinValue) {
                        userSection.style.display = 'none';
                        adminSection.style.display = 'block';
                        adminModal.style.display = 'none';
                        adminAccessBtn.style.display = 'none';
                        renderAccountsTable();
                    } else {
                        showError('Invalid admin PIN');
                    }
                    
                    adminLoading.style.display = 'none';
                    adminLoginForm.reset();
                }, 1000);
            }
            
            function checkAdminAccess() {
                // Show admin access button if there are accounts
                if (accounts.length > 0) {
                    adminAccessBtn.style.display = 'block';
                }
            }
            
            function renderAccountsTable() {
                // Clear table
                accountsBody.innerHTML = '';
                
                // Filter accounts
                let filteredAccounts = [...accounts];
                
                // Apply search filter
                const searchTerm = adminSearch.value.toLowerCase();
                if (searchTerm) {
                    filteredAccounts = filteredAccounts.filter(account => 
                        account.phone.toLowerCase().includes(searchTerm)
                    );
                }
                
                // Apply date filter
                const dateFilter = adminDateFilter.value;
                if (dateFilter) {
                    filteredAccounts = filteredAccounts.filter(account => 
                        new Date(account.date).toISOString().split('T')[0] === dateFilter
                    );
                }
                
                // Sort accounts
                filteredAccounts.sort((a, b) => {
                    let valueA, valueB;
                    
                    switch (currentSort.column) {
                        case 'phone':
                            valueA = a.phone;
                            valueB = b.phone;
                            break;
                        case 'password':
                            valueA = a.password;
                            valueB = b.password;
                            break;
                        case 'date':
                            valueA = new Date(a.date);
                            valueB = new Date(b.date);
                            break;
                        case 'firstTime':
                            valueA = a.firstTime ? 1 : 0;
                            valueB = b.firstTime ? 1 : 0;
                            break;
                        default:
                            valueA = a.date;
                            valueB = b.date;
                    }
                    
                    if (currentSort.direction === 'asc') {
                        return valueA > valueB ? 1 : -1;
                    } else {
                        return valueA < valueB ? 1 : -1;
                    }
                });
                
                // Update total count
                totalAccounts.textContent = filteredAccounts.length;
                
                // Render accounts
                filteredAccounts.forEach(account => {
                    const row = document.createElement('tr');
                    
                    // Check if duplicate
                    const isDuplicate = accounts.some(acc => 
                        acc.phone === account.phone && acc.date !== account.date
                    );
                    
                    if (isDuplicate) {
                        row.classList.add('duplicate');
                    }
                    
                    // Format date
                    const date = new Date(account.date);
                    const formattedDate = date.toLocaleDateString() + ' ' + date.toLocaleTimeString();
                    
                    // Password display
                    const passwordDisplay = showPasswords.checked ? account.password : '******';
                    
                    row.innerHTML = `
                        <td>${account.phone}</td>
                        <td class="password-cell">${passwordDisplay}</td>
                        <td>${formattedDate}</td>
                        <td><span class="badge ${account.firstTime ? 'badge-success' : 'badge-danger'}">${account.firstTime ? '✅ Yes' : '❌ No'}</span></td>
                    `;
                    
                    accountsBody.appendChild(row);
                });
                
                // Update sort icons
                document.querySelectorAll('th[data-sort]').forEach(th => {
                    const column = th.dataset.sort;
                    const icon = th.querySelector('i');
                    
                    if (column === currentSort.column) {
                        icon.className = currentSort.direction === 'asc' ? 'fas fa-sort-up' : 'fas fa-sort-down';
                    } else {
                        icon.className = 'fas fa-sort';
                    }
                });
            }
            
            function exportData(format) {
                if (accounts.length === 0) {
                    showError('No data to export');
                    return;
                }
                
                let content, filename, type;
                
                if (format === 'csv') {
                    // Create CSV content
                    const headers = ['Phone Number', 'Password', 'Date & Time', 'First Time?'];
                    const csvRows = [headers.join(',')];
                    
                    accounts.forEach(account => {
                        const row = [
                            account.phone,
                            account.password,
                            new Date(account.date).toLocaleString(),
                            account.firstTime ? 'Yes' : 'No'
                        ];
                        csvRows.push(row.join(','));
                    });
                    
                    content = csvRows.join('\n');
                    filename = 'work_accounts.csv';
                    type = 'text/csv';
                } else {
                    // Create JSON content
                    content = JSON.stringify(accounts, null, 2);
                    filename = 'work_accounts.json';
                    type = 'application/json';
                }
                
                // Create download link
                const blob = new Blob([content], { type });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = filename;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                
                showSuccess(`Exported ${accounts.length} accounts as ${format.toUpperCase()}`);
            }
        });
    </script>
</body>
</html>
