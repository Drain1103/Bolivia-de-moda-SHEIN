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
          <img src="https://i.postimg.cc/FK1Z5ZRT/htet.jpg" alt="Product 1" class="product-img">
          <h3 class="product-name">Product 1</h3>
          <p class="price">Price: $25.00</p>
          <p class="commission">Commission: $5.00</p>
        </div>

        <!-- Product 2 -->
        <div class="product-card pale-2">
          <img src="https://i.postimg.cc/6ppVn0dB/bag.jpg" alt="Product 2" class="product-img">
          <h3 class="product-name">Product 2</h3>
          <p class="price">Price: MMK 50000</p>
          <p class="commission">Commission: MMK 10000</p>
        </div>

        <!-- Product 3 -->
        <div class="product-card pale-3">
          <img src="https://i.postimg.cc/43rzCRj3/baggy.jpg" alt="Product 3" class="product-img">
          <h3 class="product-name">Product 3</h3>
          <p class="price">Price: $30.00</p>
          <p class="commission">Commission: $6.00</p>
        </div>

        <!-- Product 4 -->
        <div class="product-card pale-4">
          <img src="https://i.postimg.cc/44vp0MPJ/jaket.jpg" alt="Product 4" class="product-img">
          <h3 class="product-name">Product 4</h3>
          <p class="price">Price: $35.00</p>
          <p class="commission">Commission: $7.00</p>
        </div>

        <!-- Product 5 -->
        <div class="product-card pale-5">
          <img src="https://i.postimg.cc/KYgMDs4h/chain.jpg" alt="Product 5" class="product-img">
          <h3 class="product-name">Product 5</h3>
          <p class="price">Price: $40.00</p>
          <p class="commission">Commission: $8.00</p>
        </div>

        <!-- Product 6 -->
        <div class="product-card pale-6">
          <img src="https://i.postimg.cc/gJHrM9WQ/photo-2025-05-02-07-30-04.jpg" alt="Product 6" class="product-img">
          <h3 class="product-name">Product 6</h3>
          <p class="price">Price: MMK 60000</p>
          <p class="commission">Commission: MMK 12000</p>
        </div>

        <!-- Product 7 -->
        <div class="product-card pale-7">
          <img src="https://i.postimg.cc/zvqH5z7q/chain2.jpg" alt="Product 7" class="product-img">
          <h3 class="product-name">Product 7</h3>
          <p class="price">Price: $28.00</p>
          <p class="commission">Commission: $5.60</p>
        </div>

        <!-- Product 8 -->
        <div class="product-card pale-8">
          <img src="https://i.postimg.cc/1ts3VWqH/glass.jpg" alt="Product 8" class="product-img">
          <h3 class="product-name">Product 8</h3>
          <p class="price">Price: MMK 45000</p>
          <p class="commission">Commission: MMK 9000</p>
        </div>

        <!-- Product 9 -->
        <div class="product-card pale-9">
          <img src="https://i.postimg.cc/6qQ6Yyz4/watch.jpg" alt="Product 9" class="product-img">
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
