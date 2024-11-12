<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sobre SHEIN - E-Commerce Global de Moda</title>
    <style>
        /* General Body Styles */
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #f7b7d7, #f0b7c6); /* Soft pink gradient background */
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Header Styles */
        header {
            background-color: #fff;
            padding: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            border-bottom: 2px solid #f4b2b2;
        }

        header .logo img {
            height: 120px; /* Increased size of the logo */
        }

        header .navbar {
            display: flex;
            gap: 30px;
            list-style-type: none;
            margin: 0;
            padding: 0;
        }

        header .navbar li {
            font-size: 1.2em;
            padding: 10px;
            background-color: #ff7eb9;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        header .navbar li:hover {
            background-color: #ff5a8f;
        }

        /* Search Bar Hidden */
        .search-bar {
            display: none; /* Hide the search bar */
        }

        /* Main Section Styles */
        .main-section {
            padding: 30px;
            background: #fff;
            margin: 20px auto;
            border-radius: 10px;
            width: 90%;
            max-width: 1000px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            background: linear-gradient(to right, #fff7f0, #ffe4e1);
        }

        .main-section h1 {
            color: #ff5a8f;
            font-size: 2.5em;
            text-align: center;
            margin-bottom: 20px;
        }

        .main-section p {
            font-size: 1.2em;
            line-height: 1.8;
            color: #333;
            margin-bottom: 20px;
        }

        .main-section ul {
            font-size: 1.1em;
            color: #333;
            line-height: 1.8;
        }

        .main-section ul li {
            margin-bottom: 15px;
            list-style-type: none;
            padding-left: 20px;
            background: url('https://img.icons8.com/ios/50/000000/long-arrow-right.png') no-repeat left center;
            background-size: 20px;
        }

        /* Section Visibility */
        .content-section {
            display: none; /* Initially hidden */
        }

        .active {
            display: block; /* Show active section */
        }

    </style>
</head>
<body>

<!-- Header with Logo, Search Bar, and Navbar -->
<header>
    <div class="logo">
        <img src="https://cdn.techinasia.com/cloudinary/transformations/wp-content/uploads/2024/03/1711082850_98ea7479bdec87b2c3bb1e4da55dc956_v1711082850_large.webp" alt="Logo SHEIN">
    </div>
    <!-- Search bar is hidden now -->
    <input class="search-bar" type="text" placeholder="Buscar información sobre SHEIN">
    <ul class="navbar">
        <li onclick="showSection('about')">Sobre SHEIN</li>
        <li onclick="showSection('mission')">Misión</li>
        <li onclick="showSection('global')">Presencia Global</li>
        <li onclick="showSection('products')">Productos</li>
        <li onclick="showSection('impact')">Impacto</li>
        <li onclick="showSection('sustainability')">Sostenibilidad</li>
        <li onclick="showSection('careers')">Carreras</li>
    </ul>
</header>

<!-- Main Section About SHEIN -->
<div class="main-section">
    <h1>Bienvenido a SHEIN</h1>

    <!-- About SHEIN Section -->
    <div id="about" class="content-section">
        <p>SHEIN es una plataforma de comercio electrónico global líder que se especializa en moda y productos de estilo de vida. Conocida por ofrecer productos de moda asequibles, modernos y de alta calidad, SHEIN se ha convertido en uno de los minoristas de moda en línea más grandes del mundo, sirviendo a millones de clientes en todo el mundo.</p>
    </div>

    <!-- Mission Section -->
    <div id="mission" class="content-section">
        <h2>Misión y Valores:</h2>
        <p>La misión de SHEIN es hacer que la moda sea accesible para todos, ofreciendo productos de alta calidad y de moda a precios asequibles. La empresa valora la inclusividad, la sostenibilidad y la responsabilidad social. SHEIN está comprometida a reducir su impacto ambiental mediante prácticas sostenibles y una fuente ética de materiales.</p>
    </div>

    <!-- Global Presence Section -->
    <div id="global" class="content-section">
        <h2>Presencia Global:</h2>
        <p>SHEIN opera en más de 150 países en todo el mundo, llevando la moda directamente a tu puerta. Con almacenes dedicados en mercados clave y una infraestructura de comercio electrónico robusta, SHEIN garantiza que los clientes de diferentes partes del mundo tengan acceso a sus últimos estilos y colecciones exclusivas.</p>
    </div>

    <!-- Products Section -->
    <div id="products" class="content-section">
        <h2>Características Clave de los Productos de SHEIN:</h2>
        <ul>
            <li><strong>Alcance Global:</strong> SHEIN ofrece una amplia variedad de productos enviados globalmente.</li>
            <li><strong>Precios Asequibles:</strong> Artículos modernos y elegantes a precios competitivos.</li>
            <li><strong>Tamaños Inclusivos:</strong> SHEIN se adapta a una variedad de tamaños para todos los tipos de cuerpo.</li>
            <li><strong>Compras Personalizadas:</strong> Recibe recomendaciones basadas en el comportamiento de compra.</li>
        </ul>
    </div>

    <!-- Impact Section -->
    <div id="impact" class="content-section">
        <h2>Impacto y Sostenibilidad:</h2>
        <p>SHEIN está comprometido con la sostenibilidad y se esfuerza por hacer un impacto positivo en el medio ambiente. La empresa ha introducido diversas iniciativas para reducir su huella de carbono, incluyendo envases ecológicos y el uso de materiales reciclados. SHEIN también apoya diversas organizaciones benéficas e iniciativas comunitarias a nivel mundial.</p>
    </div>

    <!-- Sustainability Section -->
    <div id="sustainability" class="content-section">
        <h2>Esfuerzos de Sostenibilidad:</h2>
        <p>SHEIN se enfoca en reducir su huella ambiental. A través de iniciativas como el uso de materiales sostenibles, la mejora de los procesos de producción y la oferta de empaques ecológicos, SHEIN está contribuyendo activamente a la lucha contra el cambio climático.</p>
    </div>

    <!-- Careers Section -->
    <div id="careers" class="content-section">
        <h2>Carreras en SHEIN:</h2>
        <p>SHEIN ofrece diversas oportunidades de carrera en campos diversos. Únete a un equipo que prospera en innovación y creatividad. Si estás buscando una carrera emocionante en tecnología de moda, comercio electrónico o marketing, SHEIN podría ser el lugar para ti.</p>
    </div>

</div>

<script>
    // Function to show the selected section
    function showSection(sectionId) {
        // Hide all sections
        var sections = document.querySelectorAll('.content-section');
        sections.forEach(function(section) {
            section.classList.remove('active');
        });

        // Show the selected section
        var selectedSection = document.getElementById(sectionId);
        selectedSection.classList.add('active');
    }
</script>

</body>
</html>
