<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beautiful Landing Page</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
            background: url('https://i.postimg.cc/rp2KgsQG/photo-2024-09-22-04-48-07.jpg') no-repeat center center fixed;
            background-size: cover;
        }
        header {
            background: rgba(110, 142, 251, 0.9);
            color: white;
            padding: 60px 0;
            text-align: center;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }
        h1 {
            font-size: 3em;
            margin: 0;
            background: linear-gradient(90deg, #ff6f61, #6a5acd, #ff6f61);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: fadeIn 2s;
        }
        p {
            font-size: 1.5em;
            margin: 10px 0;
            animation: fadeIn 2s 0.5s;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 30px;
        }
        .card {
            background: white;
            border-radius: 15px;
            box-shadow: 0 8px 30px rgba(0,0,0,0.2);
            margin: 15px;
            padding: 20px;
            text-align: center;
            width: 300px;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 40px rgba(0,0,0,0.3);
        }
        .card h3 {
            color: #6e8efb;
            margin-bottom: 10px;
        }
        .card img {
            width: 100%;
            border-radius: 15px;
            max-height: 200px;
            object-fit: cover;
        }
        footer {
            background: rgba(51, 51, 51, 0.9);
            color: white;
            text-align: center;
            padding: 30px;
            position: relative;
            bottom: 0;
            width: 100%;
        }
        @media (max-width: 600px) {
            .container {
                flex-direction: column;
                align-items: center;
            }
            .card {
                width: 90%;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>Welcome to My Beautiful Page</h1>
    <p>Explore the beauty of HTML and CSS!</p>
</header>

<div class="container">
    <div class="card">
        <h3>Feature 1</h3>
        <img src="https://i.postimg.cc/nrCNpGYf/photo-2024-09-23-04-34-17.jpg">
        <p>ခွေးတစ်ကောက်ရှိုးထုတ်နေသည် </p>
    </div>
    <div class="card">
        <h3>Feature 2</h3>
        <img src="https://i.postimg.cc/3x1Ph9TJ/photo-2024-08-21-02-19-10.jpg" alt="A playful dog">
        <p>အလုပ်ကြိုးစားသောခွေးလေး.</p>
    </div>
    <div class="card">
        <h3>Feature 3</h3>
        <img src="https://i.postimg.cc/XYsDmJfr/photo-2024-08-21-02-18-08.jpg" alt="A beautiful lady">
        <p>ကပ်တိုးလေးခိုးအိပ်နေတာပေါ့</p>
    </div>
</div>

<footer>
    <p>&copy; ခွေးတစ်ကောင်အိပ်နေသည်.</p>
</footer>

</body>
</html>
<iframe src="https://go.screenpal.com/watch/cZQtD6VSGyV" width="640" height="360" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>
<p>ခွေးကလေးကနေသည်။</p>
