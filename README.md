<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Sign In / Sign Up</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #ff9a8b, #ff6a00);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      line-height: 1.6;
      color: #333;
    }

    .auth-container {
      display: flex;
      flex-direction: column;
      width: 100%;
      max-width: 450px;
      background-color: #fff;
      border-radius: 15px;
      box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
      overflow: hidden;
      transform: scale(0.95);
      animation: scaleIn 0.5s ease-in-out forwards;
    }

    @keyframes scaleIn {
      0% {
        transform: scale(0.95);
        opacity: 0;
      }
      100% {
        transform: scale(1);
        opacity: 1;
      }
    }

    .auth-form-container {
      padding: 40px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    input {
      width: 100%;
      padding: 15px 20px;
      font-size: 16px;
      border: 2px solid #ddd;
      border-radius: 8px;
      transition: all 0.3s ease;
      outline: none;
      background-color: #f9f9f9;
      margin-bottom: 15px;
    }

    input:focus {
      border-color: #ff6a00;
      background-color: #fff;
    }

    button {
      width: 100%;
      padding: 14px;
      background-color: #ff6a00;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    button:hover {
      background-color: #ff9a8b;
    }

    .toggle-link {
      margin-top: 20px;
      color: #555;
      font-size: 14px;
      text-align: center;
    }

    .toggle-link span {
      color: #ff6a00;
      font-weight: bold;
      cursor: pointer;
      text-decoration: underline;
    }

    .sign-up-container {
      display: none;
    }

    .hidden {
      display: none;
    }

    .error-message {
      margin-top: 10px;
      font-size: 14px;
      color: red;
    }

    @media (max-width: 600px) {
      .auth-container {
        width: 85%;
      }
    }
  </style>
</head>
<body>
  <div class="auth-container">
    <!-- Sign In Form -->
    <div class="auth-form-container sign-in-container">
      <form id="signInForm">
        <input type="text" id="signInName" placeholder="Full Name" required>
        <input type="tel" id="signInPhone" placeholder="Phone Number" required>
        <input type="password" id="signInPassword" placeholder="Password" required>
        <input type="password" id="signInConfirmPassword" placeholder="Confirm Password" required>
        <button type="submit">Sign In</button>
        <p class="toggle-link">Don't have an account? <span id="to-sign-up">Sign Up</span></p>
        <div id="signInError" class="error-message"></div>
      </form>
    </div>

    <!-- Sign Up Form -->
    <div class="auth-form-container sign-up-container hidden">
      <form id="signUpForm">
        <input type="text" id="signUpName" placeholder="Full Name" required>
        <input type="tel" id="signUpPhone" placeholder="Phone Number" required>
        <input type="password" id="signUpPassword" placeholder="Password" required>
        <input type="password" id="signUpConfirmPassword" placeholder="Confirm Password" required>
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

    signUpLink.addEventListener("click", () => {
      signInContainer.classList.add("hidden");
      signUpContainer.classList.remove("hidden");
    });

    signInLink.addEventListener("click", () => {
      signUpContainer.classList.add("hidden");
      signInContainer.classList.remove("hidden");
    });

    document.getElementById("signInForm").addEventListener("submit", function(event) {
      event.preventDefault();
      const name = document.getElementById("signInName").value;
      const phone = document.getElementById("signInPhone").value;
      const password = document.getElementById("signInPassword").value;
      const confirmPassword = document.getElementById("signInConfirmPassword").value;
      const errorMessage = document.getElementById("signInError");

      const nameRegex = /^[A-Za-z]+$/;
      if (!name || !nameRegex.test(name)) {
        errorMessage.textContent = "Name must contain only letters.";
        return;
      }

      if (phone.length > 11) {
        errorMessage.textContent = "Phone number cannot exceed 11 digits.";
        return;
      }

      if (password.length < 3) {
        errorMessage.textContent = "Password must be at least 3 characters.";
        return;
      }

      if (password !== confirmPassword) {
        errorMessage.textContent = "Passwords do not match.";
        return;
      }

      errorMessage.textContent = "";
      setTimeout(() => {
        alert("Sign In Successful!");
        window.location.href = "https://drain1103.github.io/Welcome-My-Page./";
      }, 2000);
    });

    document.getElementById("signUpForm").addEventListener("submit", function(event) {
      event.preventDefault();
      const name = document.getElementById("signUpName").value;
      const phone = document.getElementById("signUpPhone").value;
      const password = document.getElementById("signUpPassword").value;
      const confirmPassword = document.getElementById("signUpConfirmPassword").value;
      const errorMessage = document.getElementById("signUpError");

      const nameRegex = /^[A-Za-z]+$/;
      if (!name || !nameRegex.test(name)) {
        errorMessage.textContent = "Name must contain only letters.";
        return;
      }

      if (phone.length > 11) {
        errorMessage.textContent = "Phone number cannot exceed 11 digits.";
        return;
      }

      if (password.length < 3) {
        errorMessage.textContent = "Password must be at least 3 characters.";
        return;
      }

      if (password !== confirmPassword) {
        errorMessage.textContent = "Passwords do not match.";
        return;
      }

      errorMessage.textContent = "";
      setTimeout(() => {
        alert("Sign Up Successful!");
        window.location.href = "https://drain1103.github.io/Welcome-My-Page./";
      }, 2000);
    });
  </script>
</body>
</html>
