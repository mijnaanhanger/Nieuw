<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PartsWorld.nl - Auto Onderdelen Webshop</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <h1><a href="/">PartsWorld.nl</a></h1>
            <nav>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#producten">Producten</a></li>
                    <li><a href="#zoeken">Zoeken</a></li>
                    <li><a href="#winkelwagen">Winkelwagen (0)</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Hero Image -->
    <section id="home" class="hero">
        <div class="container">
            <h2>Welkom bij PartsWorld.nl</h2>
            <p>De beste onderdelen voor je auto, altijd snel geleverd.</p>
        </div>
    </section>

    <!-- Zoekbalk -->
    <section id="zoeken" class="container">
        <input type="text" id="search-bar" placeholder="Zoek naar onderdelen..." onkeyup="searchProducts()">
    </section>

    <!-- Producten -->
    <section id="producten" class="container">
        <h2>Onze Populaire Producten</h2>
        <div class="product-container">
            <!-- Product 1 -->
            <div class="product">
                <img src="https://via.placeholder.com/250" alt="Product 1">
                <h3>Auto Onderdeel 1</h3>
                <p>Prijs: €50,00</p>
                <button class="btn-buy" onclick="addToCart('Auto Onderdeel 1', 50)">In Winkelwagen</button>
            </div>

            <!-- Product 2 -->
            <div class="product">
                <img src="https://via.placeholder.com/250" alt="Product 2">
                <h3>Auto Onderdeel 2</h3>
                <p>Prijs: €75,00</p>
                <button class="btn-buy" onclick="addToCart('Auto Onderdeel 2', 75)">In Winkelwagen</button>
            </div>

            <!-- Product 3 -->
            <div class="product">
                <img src="https://via.placeholder.com/250" alt="Product 3">
                <h3>Auto Onderdeel 3</h3>
                <p>Prijs: €100,00</p>
                <button class="btn-buy" onclick="addToCart('Auto Onderdeel 3', 100)">In Winkelwagen</button>
            </div>
        </div>
    </section>

    <!-- Winkelwagen -->
    <section id="winkelwagen" class="container">
        <h2>Jouw Winkelwagen</h2>
        <div id="cart-items">Geen producten in winkelwagen.</div>
        <button id="checkout-btn">Afrekenen</button>
    </section>

    <!-- Contact -->
    <section id="contact" class="container">
        <h2>Neem Contact Op</h2>
        <form>
            <input type="text" placeholder="Naam" required>
            <input type="email" placeholder="E-mail" required>
            <textarea placeholder="Bericht" required></textarea>
            <button type="submit">Verstuur</button>
        </form>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2024 PartsWorld.nl | Alle rechten voorbehouden</p>
        </div>
    </footer>

    <!-- Scripts -->
    <script src="script.js"></script>
</body>
</html>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Roboto', sans-serif;
    background-color: #f4f4f4;
}

.container {
    width: 80%;
    margin: 0 auto;
}

header {
    background-color: #1f3a63;
    color: white;
    padding: 20px 0;
    text-align: center;
}

header h1 a {
    text-decoration: none;
    color: white;
    font-size: 2.5em;
}

nav ul {
    list-style-type: none;
    padding: 0;
    margin-top: 20px;
}

nav ul li {
    display: inline;
    margin: 0 20px;
}

nav ul li a {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

nav ul li a:hover {
    text-decoration: underline;
}

.hero {
    background-color: #34495e;
    color: white;
    padding: 60px 0;
    text-align: center;
}

h2 {
    font-size: 2.5em;
    margin-bottom: 20px;
}

.product-container {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
}

.product {
    background-color: white;
    padding: 20px;
    margin: 15px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 30%;
    text-align: center;
}

.product img {
    width: 100%;
    height: auto;
    border-radius: 5px;
}

.product h3 {
    font-size: 1.2em;
    margin-top: 15px;
}

.product p {
    color: #333;
}

.btn-buy {
    background-color: #28a745;
    color: white;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    margin-top: 10px;
}

.btn-buy:hover {
    background-color: #218838;
}

form input, form textarea {
    margin: 10px 0;
    padding: 12px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

form button {
    background-color: #1f3a63;
    color: white;
    padding: 12px 20px;
    border: none;
    cursor: pointer;
    border-radius: 5px;
}

form button:hover {
    background-color: #34495e;
}

footer {
    background-color: #1f3a63;
    color: white;
    padding: 20px;
    text-align: center;
}

/* Mobile Styles */
@media (max-width: 768px) {
    .product-container {
        flex-direction: column;
        align-items: center;
    }

    .product {
        width: 80%;
        margin: 10px 0;
    }
}

let cart = [];

function addToCart(productName, price) {
    cart.push({ productName, price });
    updateCart();
}

function updateCart() {
    const cartItemsDiv = document.getElementById('cart-items');
    if (cart.length === 0) {
        cartItemsDiv.innerHTML = 'Geen producten in winkelwagen.';
    } else {
        cartItemsDiv.innerHTML = '';
        cart.forEach((item, index) => {
            const itemDiv = document.createElement('div');
            itemDiv.innerHTML = `${item.productName} - €${item.price}`;
            cartItemsDiv.appendChild(itemDiv);
        });
    }
}

document.getElementById('checkout-btn').addEventListener('click', () => {
    alert('Afrekenen - Hier kan je je betaalpagina integreren!');
});
