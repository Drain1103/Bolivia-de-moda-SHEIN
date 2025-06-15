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
        window.location.href = "https://drain1103.github.io/Welcome-My-Page./"; // ✅ Redirect to the correct page
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
