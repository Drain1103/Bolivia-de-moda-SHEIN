<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Create Work Account</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(to right, #ffafbd, #ffc3a0);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            padding: 20px;
            overflow: hidden;
        }
        .form-container, .account-layout {
            background-color: #fff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 15px 25px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 400px;
            display: none; /* Initially hidden */
        }
        h2 {
            text-align: center;
            margin-bottom: 30px;
            color: #ff6f61;
            font-size: 1.5em;
        }
        .form-group {
            margin-bottom: 20px;
        }
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-weight: bold;
        }
        .form-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #f1f1f1;
            border-radius: 8px;
            font-size: 1em;
            transition: border-color 0.3s;
        }
        .form-group input:focus {
            border-color: #ff6f61;
            outline: none;
        }
        .form-group button {
            width: 100%;
            padding: 12px;
            background-color: #ff6f61;
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .form-group button:hover {
            background-color: #ff3d3d;
        }

        /* Profile Header */
        .profile-header {
            position: relative;
            background-color: #4a90e2;
            margin-bottom: 20px;
            color: white;
        }
        .cover-photo {
            width: 100%;
            height: 200px; /* Adjusted for mobile view */
            background-image: url('cover-photo.jpg');
            background-size: cover;
            background-position: center;
            border-bottom: 4px solid #0078d7;
        }
        .profile-picture {
            position: absolute;
            bottom: -50px; /* Adjusted for mobile view */
            left: 20px;
            border: 5px solid white;
            border-radius: 50%;
            width: 100px; /* Adjusted for mobile view */
            height: 100px; /* Adjusted for mobile view */
            background-color: white;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer; /* Cursor changes to pointer */
        }
        .profile-picture img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.2s;
        }
        .profile-picture:hover img {
            transform: scale(1.1);
        }
        .profile-info {
            padding: 20px;
            margin-top: 30px; /* Adjusted for mobile view */
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .profile-info h1 {
            font-size: 24px; /* Adjusted for mobile view */
            margin-bottom: 5px;
            color: #333;
        }
        .profile-info p {
            color: #666;
            font-size: 14px; /* Adjusted for mobile view */
        }
        .tabs {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
            background-color: #fff;
            padding: 10px 0;
            border-radius: 10px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
            display: none; /* Initially hidden */
        }
        .tabs a {
            text-decoration: none;
            color: #4a90e2;
            padding: 10px 5px; /* Adjusted for mobile view */
            font-size: 14px; /* Adjusted for mobile view */
            border: 2px solid transparent;
            transition: background-color 0.3s, color 0.3s, border 0.3s;
        }
        .tabs a:hover {
            background-color: #e1f5fe;
            border: 2px solid #4a90e2;
            color: #004d40;
            border-radius: 5px;
        }
        .profile-details {
            margin-top: 20px;
            background-color: #ffffff;
            padding: 10px; /* Adjusted for mobile view */
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .profile-details div {
            margin-bottom: 10px;
        }
        .profile-details div span {
            font-weight: bold;
            color: #333;
        }
        .products-section {
            margin-top: 20px;
            padding: 10px; /* Adjusted for mobile view */
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .products-section h2 {
            font-size: 20px; /* Adjusted for mobile view */
            margin-bottom: 10px; /* Adjusted for mobile view */
            color: #4a90e2;
        }
        .product-grid {
            display: flex;
            gap: 10px; /* Adjusted for mobile view */
            flex-wrap: wrap;
        }
        .product {
            background-color: #f7f7f7;
            padding: 5px; /* Adjusted for mobile view */
            text-align: center;
            border-radius: 8px;
            box-shadow: 0 1px 4px rgba(0, 0, 0, 0.2);
            width: calc(33.333% - 15px); /* Adjusted for mobile view */
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .product:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }
        .product img {
            width: 80px; /* Adjusted for mobile view */
            height: 80px; /* Adjusted for mobile view */
            object-fit: cover;
            border-radius: 5px;
            margin-bottom: 5px; /* Adjusted for mobile view */
        }
        .font-blocks {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
            padding: 10px 0;
        }
        .font-block {
            background-color: #4a90e2;
            color: white;
            padding: 10px; /* Adjusted for mobile view */
            border-radius: 8px;
            text-align: center;
            width: 20%; /* Adjust width for smaller screens */
            transition: background-color 0.3s;
        }
        .font-block:hover {
            background-color: #0078d7;
        }

        /* Full Profile Photo Modal */
        .full-profile-photo {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .full-profile-photo img {
            width: auto;
            height: 70%; /* Adjusted for mobile view */
            max-width: 90%;
        }
        .close-photo {
            position: absolute;
            top: 20px;
            right: 30px;
            color: white;
            cursor: pointer;
            font-size: 24px;
        }

        /* Customer Service Modal */
        .customer-service-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .modal-content {
            background-color: white;
            padding: 20px; /* Adjusted for mobile view */
            border-radius: 12px;
            box-shadow: 0 15px 25px rgba(0, 0, 0, 0.2);
            max-width: 350px; /* Adjusted for mobile view */
            width: 90%;
        }
        .close-modal {
            position: absolute;
            top: 20px;
            right: 30px;
            color: #ff6f61;
            cursor: pointer;
            font-size: 24px;
        }

        @media (max-width: 768px) {
            .product {
                width: calc(50% - 15px); /* Adjusted for mobile view */
            }
        }
        @media (max-width: 480px) {
            .product {
                width: 100%; /* Adjusted for mobile view */
            }
            .font-block {
                width: 48%; /* Adjust for smaller screens */
            }
        }
    </style>
</head>
<body>

    <!-- Account Creation Form -->
    <div class="form-container" id="account-form-container">
        <h2>🛍️ Welcome to the A-Nyar Shopping Platform! 🛍️</h2>
        <form id="account-form" onsubmit="return createAccount(event);">
            <div class="form-group">
                <label for="name">Full Name</label>
                <input type="text" id="name" name="name" placeholder="Enter your full name" required>
            </div>
            <div class="form-group">
                <label for="phone">Phone Number</label>
                <input type="tel" id="phone" name="phone" placeholder="Enter your phone number" required>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" name="password" placeholder="Create a password" required>
            </div>
            <div class="form-group">
                <button type="submit">Create Work Account</button>
            </div>
        </form>
    </div>

    <!-- Profile Mockup -->
    <div class="account-layout" id="profile-mockup">
        <div class="profile-header">
            <div class="cover-photo"></div>
            <div class="profile-picture" onclick="document.getElementById('profile-photo-input').click();">
                <img id="profile-photo" src="profile-picture.jpg" alt="Profile Picture" onclick="showFullPhoto()">
            </div>
            <input type="file" id="profile-photo-input" accept="image/*" style="display: none;" onchange="updateProfilePhoto(event)">
        </div>
        <div class="profile-info">
            <h1 id="profile-name">John Doe</h1>
            <p id="profile-phone">123-456-7890</p>
        </div>
        <!-- Tabs Section (Initially Hidden) -->
        <div class="tabs" id="tabs-section">
            <a href="#home">Home</a>
            <a href="#customer-service" onclick="showCustomerService()">Customer Service</a>
            <a href="#profile">Profile</a>
            <a href="#tasks">Tasks</a>
        </div>
        <div class="profile-details">
            <h2>Profile Details</h2>
            <div>
                <span>Name:</span> <span id="display-name">John Doe</span>
            </div>
            <div>
                <span>Phone:</span> <span id="display-phone">123-456-7890</span>
            </div>
        </div>
        <div class="products-section">
            <h2>Products</h2>
            <div class="product-grid">
                <div class="product">
                    <img src="https://img.ltwebstatic.com/images3_spmp/2023/07/27/169044806227147be7a5fca57929c075e58c9ed112_thumbnail_336x.jpg" alt="Product 1">
                    <h3>Product 1</h3>
                    <p>$10.00</p>
                </div>
                <div class="product">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRnTvo6xNxvNh8ZARdTL5fRn30Z1RHwlFEfRg&s" alt="Product 2">
                    <h3>Product 2</h3>
                    <p>$15.00</p>
                </div>
                <div class="product">
                    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTdE29Ddw7Rc9SIv4MffPMknnYwCDIEKXRruQ&s" alt="Product 3">
                    <h3>Product 3</h3>
                    <p>$20.00</p>
                </div>
            </div>
        </div>
        
        <!-- Full Profile Photo Modal -->
        <div class="full-profile-photo" id="full-profile-photo">
            <span class="close-photo" onclick="closeFullPhoto()">✖️</span>
            <img id="full-photo-image" src="profile-picture.jpg" alt="Full Profile Picture">
        </div>

        <!-- Customer Service Modal -->
        <div class="customer-service-modal" id="customer-service-modal">
            <div class="modal-content">
                <span class="close-modal" onclick="closeCustomerService()">✖️</span>
                <h2>Customer Service</h2>
                <p>For any inquiries, please contact us at support@example.com or call us at (123) 456-7890.</p>
            </div>
        </div>

        <script>
            function createAccount(event) {
                event.preventDefault(); // Prevent the form from submitting
                const name = document.getElementById('name').value;
                const phone = document.getElementById('phone').value;
                const password = document.getElementById('password').value;

                // Update profile mockup
                document.getElementById('profile-name').textContent = name;
                document.getElementById('profile-phone').textContent = phone;
                document.getElementById('display-name').textContent = name;
                document.getElementById('display-phone').textContent = phone;

                // Show the profile mockup and hide the account form
                document.getElementById('profile-mockup').style.display = 'block';
                document.getElementById('account-form-container').style.display = 'none';

                // Show the tabs section
                document.getElementById('tabs-section').style.display = 'flex';
            }

            function showFullPhoto() {
                document.getElementById('full-profile-photo').style.display = 'flex';
            }

            function closeFullPhoto() {
                document.getElementById('full-profile-photo').style.display = 'none';
            }

            function updateProfilePhoto(event) {
                const file = event.target.files[0];
                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById('profile-photo').src = e.target.result;
                    document.getElementById('full-photo-image').src = e.target.result; // Update full photo modal
                };
                if (file) {
                    reader.readAsDataURL(file);
                }
            }

            function showCustomerService() {
                document.getElementById('customer-service-modal').style.display = 'flex';
            }

            function closeCustomerService() {
                document.getElementById('customer-service-modal').style.display = 'none';
            }

            // Show the account form by default
            document.getElementById('account-form-container').style.display = 'block';
        </script>
</body>
</html>
