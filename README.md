<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Sign In / Sign Up</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="auth-container">
    <!-- Sign In Form -->
    <div class="auth-form-container sign-in-container">
      <form id="signInForm">
        <div class="input-group">
          <input type="text" id="signInName" placeholder="Full Name" required>
        </div>
        <div class="input-group">
          <input type="tel" id="signInPhone" placeholder="Phone Number" required>
        </div>
        <div class="input-group">
          <input type="password" id="signInPassword" placeholder="Password" required>
        </div>
        <div class="input-group">
          <input type="password" id="signInConfirmPassword" placeholder="Confirm Password" required>
        </div>
        <button type="submit">Sign In</button>
        <p class="toggle-link">Don't have an account? <span id="to-sign-up">Sign Up</span></p>
        <div id="signInError" class="error-message"></div>
      </form>
    </div>

    <!-- Sign Up Form -->
    <div class="auth-form-container sign-up-container hidden">
      <form id="signUpForm">
        <div class="input-group">
          <input type="text" id="signUpName" placeholder="Full Name" required>
        </div>
        <div class="input-group">
          <input type="tel" id="signUpPhone" placeholder="Phone Number" required>
        </div>
        <div class="input-group">
          <input type="password" id="signUpPassword" placeholder="Password" required>
        </div>
        <div class="input-group">
          <input type="password" id="signUpConfirmPassword" placeholder="Confirm Password" required>
        </div>
        <button type="submit">Sign Up</button>
        <p class="toggle-link">Already have an account? <span id="to-sign-in">Sign In</span></p>
        <div id="signUpError" class="error-message"></div>
      </form>
    </div>
  </div>

  <script>
    const signInLink = document.getElementById("to-sign-in");
    const signUpLink = document.getElementById("to-sign-up");
    const signInContainer = document.querySelector(".sign-in-container");
    const signUpContainer = document.querySelector(".sign-up-container");

    // Toggle between Sign In and Sign Up
    signUpLink.addEventListener("click", () => {
      signInContainer.classList.add("hidden");
      signUpContainer.classList.remove("hidden");
    });

    signInLink.addEventListener("click", () => {
      signUpContainer.classList.add("hidden");
      signInContainer.classList.remove("hidden");
    });

    // Handle Sign In form validation
    document.getElementById("signInForm").addEventListener("submit", function(event) {
      event.preventDefault();
      const name = document.getElementById("signInName").value;
      const phone = document.getElementById("signInPhone").value;
      const password = document.getElementById("signInPassword").value;
      const confirmPassword = document.getElementById("signInConfirmPassword").value;
      const errorMessage = document.getElementById("signInError");

      // User name must only contain letters
      const nameRegex = /^[A-Za-z]+$/;
      if (!name || !nameRegex.test(name)) {
        errorMessage.textContent = "Name must contain only letters.";
        errorMessage.style.color = "red";
        return;
      }

      // Phone number should not exceed 11 digits
      if (phone.length > 11) {
        errorMessage.textContent = "Phone number cannot exceed 11 digits.";
        errorMessage.style.color = "red";
        return;
      }

      // Password must be at least 3 characters
      if (password.length < 3) {
        errorMessage.textContent = "Password must be at least 3 characters long.";
        errorMessage.style.color = "red";
        return;
      }

      // Check if passwords match
      if (password !== confirmPassword) {
        errorMessage.textContent = "Passwords do not match.";
        errorMessage.style.color = "red";
        return;
      }

      errorMessage.textContent = "";
      setTimeout(() => {
        alert("Sign In Successful!");
        window.location.href = "2025.html";
      }, 2000);
    });

    // Handle Sign Up form validation
    document.getElementById("signUpForm").addEventListener("submit", function(event) {
      event.preventDefault();
      const name = document.getElementById("signUpName").value;
      const phone = document.getElementById("signUpPhone").value;
      const password = document.getElementById("signUpPassword").value;
      const confirmPassword = document.getElementById("signUpConfirmPassword").value;
      const errorMessage = document.getElementById("signUpError");

      // User name must only contain letters
      const nameRegex = /^[A-Za-z]+$/;
      if (!name || !nameRegex.test(name)) {
        errorMessage.textContent = "Name must contain only letters.";
        errorMessage.style.color = "red";
        return;
      }

      // Phone number should not exceed 11 digits
      if (phone.length > 11) {
        errorMessage.textContent = "Phone number cannot exceed 11 digits.";
        errorMessage.style.color = "red";
        return;
      }

      // Password must be at least 3 characters
      if (password.length < 3) {
        errorMessage.textContent = "Password must be at least 3 characters long.";
        errorMessage.style.color = "red";
        return;
      }

      // Check if passwords match
      if (password !== confirmPassword) {
        errorMessage.textContent = "Passwords do not match.";
        errorMessage.style.color = "red";
        return;
      }

      errorMessage.textContent = "";
      setTimeout(() => {
        alert("Sign Up Successful!");
        window.location.href = "2025.html"; // ✅ Redirect to the correct page
      }, 2000);
    });
  </script>

  <style>
    .hidden {
      display: none;
    }

    .auth-container {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background: #f0f0f0;
    }

    .auth-form-container {
      background: white;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      width: 100%;
      max-width: 400px;
    }

    .input-group {
      margin-bottom: 15px;
    }

    input {
      width: 100%;
      padding: 10px;
      font-size: 16px;
    }

    button {
      width: 100%;
      padding: 10px;
      background: #333;
      color: white;
      border: none;
      cursor: pointer;
      font-size: 16px;
    }

    .toggle-link {
      margin-top: 10px;
      font-size: 14px;
      text-align: center;
    }

    .toggle-link span {
      color: blue;
      cursor: pointer;
      text-decoration: underline;
    }

    .error-message {
      font-size: 14px;
      color: red;
      margin-top: 10px;
    }
  </style>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Product Overview</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      padding: 0;
      background: #fdfdfd;
    }

    .header {
      background-color: #333;
      color: white;
      padding: 15px 20px;
    }

    .header .container {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-links {
      list-style: none;
      display: flex;
      gap: 15px;
    }

    .nav-links a {
      color: white;
      text-decoration: none;
    }

    .product-section {
      padding: 20px;
    }

    .section-title {
      text-align: center;
      margin-bottom: 20px;
    }

    .product-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
    }

    .product-card {
      border: 2px solid #e8e8f1;
      border-radius: 12px;
      padding: 15px;
      text-align: center;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
      transition: transform 0.2s;
    }

    .product-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
    }

    .product-img {
      width: 100%;
      height: auto;
      border-radius: 8px;
      margin-bottom: 10px;
    }

    .footer {
      background: #333;
      color: white;
      padding: 10px;
      text-align: center;
    }

    .bottom-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: #eee;
      padding: 10px 0;
      border-top: 1px solid #ccc;
    }

    .bottom-nav ul {
      display: flex;
      justify-content: space-around;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .bottom-nav a {
      font-size: 24px;
      text-decoration: none;
      color: #000;
    }

    /* Pale Background Colors */
    .pale-1 { background-color: #fef6e4; }
    .pale-2 { background-color: #e8f9f3; }
    .pale-3 { background-color: #f0e8ff; }
    .pale-4 { background-color: #ffe9ec; }
    .pale-5 { background-color: #eaf4ff; }
    .pale-6 { background-color: #f5f9e9; }
    .pale-7 { background-color: #fff3e6; }
    .pale-8 { background-color: #e4f0ff; }
    .pale-9 { background-color: #fce8f1; }
  </style>
</head>
<body>

  <!-- Header Section -->
  <header class="header">
    <div class="container">
      <h1 class="logo">Product Overview</h1>
      <nav>
        <ul class="nav-links">
          <li><a href="#">Dashboard</a></li>
          <li><a href="#">Orders</a></li>
          <li><a href="#">Settings</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <!-- Product Section -->
  <section class="product-section">
    <div class="container">
      <h2 class="section-title">Products Overview</h2>
      <div class="product-grid">

        <!-- Product 1 -->
        <div class="product-card pale-1">
          <img src="hat2.jpg" alt="Product 1" class="product-img">
          <h3 class="product-name">Product 1</h3>
          <p class="price">Price: $25.00</p>
          <p class="commission">Commission: $5.00</p>
        </div>

        <!-- Product 2 -->
        <div class="product-card pale-2">
          <img src="jaket.jpg" alt="Product 2" class="product-img">
          <h3 class="product-name">Product 2</h3>
          <p class="price">Price: MMK 50000</p>
          <p class="commission">Commission: MMK 10000</p>
        </div>

        <!-- Product 3 -->
        <div class="product-card pale-3">
          <img src="baggy.jpg" alt="Product 3" class="product-img">
          <h3 class="product-name">Product 3</h3>
          <p class="price">Price: $30.00</p>
          <p class="commission">Commission: $6.00</p>
        </div>

        <!-- Product 4 -->
        <div class="product-card pale-4">
          <img src="shoe.jpg" alt="Product 4" class="product-img">
          <h3 class="product-name">Product 4</h3>
          <p class="price">Price: $35.00</p>
          <p class="commission">Commission: $7.00</p>
        </div>

        <!-- Product 5 -->
        <div class="product-card pale-5">
          <img src="watch.jpg" alt="Product 5" class="product-img">
          <h3 class="product-name">Product 5</h3>
          <p class="price">Price: $40.00</p>
          <p class="commission">Commission: $8.00</p>
        </div>

        <!-- Product 6 -->
        <div class="product-card pale-6">
          <img src="chain2.jpg" alt="Product 6" class="product-img">
          <h3 class="product-name">Product 6</h3>
          <p class="price">Price: MMK 60000</p>
          <p class="commission">Commission: MMK 12000</p>
        </div>

        <!-- Product 7 -->
        <div class="product-card pale-7">
          <img src="chain.jpg" alt="Product 7" class="product-img">
          <h3 class="product-name">Product 7</h3>
          <p class="price">Price: $28.00</p>
          <p class="commission">Commission: $5.60</p>
        </div>

        <!-- Product 8 -->
        <div class="product-card pale-8">
          <img src="bag.jpg" alt="Product 8" class="product-img">
          <h3 class="product-name">Product 8</h3>
          <p class="price">Price: MMK 45000</p>
          <p class="commission">Commission: MMK 9000</p>
        </div>

        <!-- Product 9 -->
        <div class="product-card pale-9">
          <img src="glass.jpg" alt="Product 9" class="product-img">
          <h3 class="product-name">Product 9</h3>
          <p class="price">Price: $50.00</p>
          <p class="commission">Commission: $10.00</p>
        </div>

      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="footer">
    <div class="container">
      <p>&copy; 2025 Our Shop. All rights reserved.</p>
    </div>
  </footer>

  <!-- Bottom Navigation -->
  <div class="bottom-nav">
    <ul>
      <li><a href="#" id="mainPage">🏠</a></li>
      <li><a href="staff-commissions.html" id="work">🛠️</a></li>
      <li><a href="#" id="orders">📦</a></li>
      <li><a href="profile.html" id="profile">👤</a></li>
    </ul>
  </div>

</body>
</html>


