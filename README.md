<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Work Account - Mobile Interface</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Arial, sans-serif;
            height: 100vh;
            background: linear-gradient(180deg, #e3f2fd 0%, #bbdefb 25%, #90caf9 50%, #64b5f6 75%, #42a5f5 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .mobile-container {
            width: 375px;
            height: 812px;
            background: linear-gradient(180deg, #e8f4fd 0%, #cce7f0 25%, #90caf9 50%, #64b5f6 75%, #4fc3f7 100%);
            border-radius: 25px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 60px 40px 40px;
        }

        .header-section {
            text-align: left;
            z-index: 10;
            position: relative;
        }

        .main-title {
            font-size: 48px;
            font-weight: 900;
            color: #1e3a8a;
            letter-spacing: 2px;
            margin-bottom: 8px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .subtitle {
            font-size: 16px;
            color: #64748b;
            font-weight: 400;
            margin-bottom: 20px;
        }

        .illustration-section {
            flex-grow: 1;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .cityscape {
            position: absolute;
            right: 20px;
            bottom: 80px;
            display: flex;
            align-items: flex-end;
            gap: 8px;
        }

        .building {
            background: linear-gradient(180deg, #1e40af, #1d4ed8);
            border-radius: 4px 4px 0 0;
            box-shadow: 0 4px 8px rgba(30, 64, 175, 0.3);
        }

        .building:nth-child(1) { width: 25px; height: 80px; }
        .building:nth-child(2) { width: 30px; height: 100px; }
        .building:nth-child(3) { width: 35px; height: 120px; }
        .building:nth-child(4) { width: 28px; height: 90px; }
        .building:nth-child(5) { width: 32px; height: 110px; }

        .plant {
            position: absolute;
            left: 40px;
            bottom: 140px;
            width: 60px;
            height: 80px;
        }

        .plant-stem {
            width: 4px;
            height: 50px;
            background: #16a34a;
            margin: 0 auto;
            border-radius: 2px;
        }

        .plant-leaves {
            display: flex;
            justify-content: center;
            margin-top: -10px;
        }

        .leaf {
            width: 25px;
            height: 35px;
            background: linear-gradient(45deg, #22c55e, #16a34a);
            border-radius: 50% 0;
            margin: 0 2px;
            transform-origin: bottom center;
        }

        .leaf:nth-child(1) { transform: rotate(-30deg); }
        .leaf:nth-child(2) { transform: rotate(0deg); }
        .leaf:nth-child(3) { transform: rotate(30deg); }

        .car {
            position: absolute;
            left: 50px;
            bottom: 90px;
            width: 80px;
            height: 35px;
            background: #ffffff;
            border-radius: 20px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
        }

        .car::before {
            content: '';
            position: absolute;
            top: -8px;
            left: 15px;
            width: 40px;
            height: 15px;
            background: #e5e7eb;
            border-radius: 8px 8px 0 0;
        }

        .car::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 12px;
            width: 16px;
            height: 16px;
            background: #374151;
            border-radius: 50%;
            box-shadow: 44px 0 0 #374151;
        }

        .clouds {
            position: absolute;
            top: 100px;
            left: 0;
            right: 0;
        }

        .cloud {
            position: absolute;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 50px;
            opacity: 0.8;
        }

        .cloud:nth-child(1) {
            width: 60px;
            height: 30px;
            top: 20px;
            left: 50px;
            animation: float 6s ease-in-out infinite;
        }

        .cloud:nth-child(2) {
            width: 80px;
            height: 40px;
            top: 60px;
            right: 30px;
            animation: float 8s ease-in-out infinite reverse;
        }

        .cloud:nth-child(3) {
            width: 45px;
            height: 25px;
            top: 10px;
            right: 80px;
            animation: float 7s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .button-section {
            display: flex;
            flex-direction: column;
            gap: 16px;
            z-index: 10;
            position: relative;
        }

        .btn {
            width: 100%;
            padding: 18px;
            border: none;
            border-radius: 25px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #1e40af, #1d4ed8);
            color: white;
            box-shadow: 0 8px 20px rgba(30, 64, 175, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 25px rgba(30, 64, 175, 0.4);
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.95);
            color: #1e40af;
            border: 2px solid rgba(30, 64, 175, 0.2);
            backdrop-filter: blur(10px);
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 1);
            border-color: #1e40af;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(255, 255, 255, 0.3);
        }

        .home-indicator {
            width: 134px;
            height: 5px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 2.5px;
            margin: 20px auto 0;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: white;
            padding: 40px;
            border-radius: 20px;
            width: 320px;
            text-align: center;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .modal h2 {
            color: #1e40af;
            margin-bottom: 20px;
            font-size: 24px;
        }

        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #374151;
            font-weight: 500;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e5e7eb;
            border-radius: 12px;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #1e40af;
        }

        .close-btn {
            background: #6b7280;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 12px;
            margin-left: 10px;
            cursor: pointer;
        }

        @media (max-width: 425px) {
            .mobile-container {
                width: 100vw;
                height: 100vh;
                border-radius: 0;
                margin: 0;
            }
        }
    </style>
</head>
<body>
    <div class="mobile-container">
        <div class="header-section">
            <h1 class="main-title">HELLO</h1>
            <p class="subtitle">Join our team today</p>
        </div>
        
        <div class="illustration-section">
            <div class="clouds">
                <div class="cloud"></div>
                <div class="cloud"></div>
                <div class="cloud"></div>
            </div>
            
            <div class="cityscape">
                <div class="building"></div>
                <div class="building"></div>
                <div class="building"></div>
                <div class="building"></div>
                <div class="building"></div>
            </div>
            
            <div class="plant">
                <div class="plant-leaves">
                    <div class="leaf"></div>
                    <div class="leaf"></div>
                    <div class="leaf"></div>
                </div>
                <div class="plant-stem"></div>
            </div>
            
            <div class="car"></div>
        </div>
        
        <div class="button-section">
            <button class="btn btn-primary" onclick="openModal('signin')">Sign In</button>
            <button class="btn btn-secondary" onclick="openModal('signup')">Create Work Account</button>
        </div>
        
        <div class="home-indicator"></div>
    </div>

    <!-- Sign In Modal -->
    <div id="signinModal" class="modal">
        <div class="modal-content">
            <h2>Employee Sign In</h2>
            <form id="signinForm">
                <div class="form-group">
                    <label>Employee ID or Email</label>
                    <input type="text" required placeholder="Enter your employee ID">
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" required placeholder="Enter your password">
                </div>
                <button type="submit" class="btn btn-primary">Sign In</button>
                <button type="button" class="close-btn" onclick="closeModal('signin')">Cancel</button>
            </form>
        </div>
    </div>

    <!-- Sign Up Modal -->
    <div id="signupModal" class="modal">
        <div class="modal-content">
            <h2>Create Work Account</h2>
            <form id="signupForm">
                <div class="form-group">
                    <label>Full Name</label>
                    <input type="text" required placeholder="Enter your full name">
                </div>
                <div class="form-group">
                    <label>Employee ID</label>
                    <input type="text" required placeholder="Assigned employee ID">
                </div>
                <div class="form-group">
                    <label>Work Email</label>
                    <input type="email" required placeholder="your.email@company.com">
                </div>
                <div class="form-group">
                    <label>Department</label>
                    <select required>
                        <option value="">Select Department</option>
                        <option value="sales">Sales</option>
                        <option value="marketing">Marketing</option>
                        <option value="it">IT</option>
                        <option value="hr">Human Resources</option>
                        <option value="finance">Finance</option>
                        <option value="operations">Operations</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" required placeholder="Create a secure password">
                </div>
                <button type="submit" class="btn btn-primary">Create Account</button>
                <button type="button" class="close-btn" onclick="closeModal('signup')">Cancel</button>
            </form>
        </div>
    </div>

    <script>
        function openModal(type) {
            const modal = document.getElementById(type + 'Modal');
            modal.style.display = 'flex';
        }

        function closeModal(type) {
            const modal = document.getElementById(type + 'Modal');
            modal.style.display = 'none';
        }

        // Close modal when clicking outside
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }

        // Handle form submissions
        document.getElementById('signinForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Sign in functionality - Connect to your authentication system');
            closeModal('signin');
        });

        document.getElementById('signupForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Account creation functionality - Connect to your backend system');
            closeModal('signup');
        });

        // Add some interactive animations
        document.addEventListener('DOMContentLoaded', function() {
            const buildings = document.querySelectorAll('.building');
            buildings.forEach((building, index) => {
                building.style.animationDelay = (index * 0.2) + 's';
                building.style.animation = 'buildingGrow 2s ease-out forwards';
            });
        });

        // CSS animation for buildings
        const style = document.createElement('style');
        style.textContent = `
            @keyframes buildingGrow {
                from {
                    transform: scaleY(0);
                    opacity: 0;
                }
                to {
                    transform: scaleY(1);
                    opacity: 1;
                }
            }
            .building {
                transform-origin: bottom;
                opacity: 0;
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
