<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tienda de Repostería</title>
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background: linear-gradient(135deg, #f7c4d6, #e0f7fa);
            animation: gradientAnimation 15s ease infinite;
            margin: 0;
            padding: 0;
            color: #333;
            overflow-x: hidden;
        }

        .container {
            width: 85%;
            margin: 0 auto;
            padding: 50px 0;
        }

        h1 {
            text-align: center;
            font-size: 3rem;
            color: #d34e5b;
            margin-bottom: 30px;
            animation: fadeIn 1.5s ease-in-out;
        }

        h2 {
            color: #4b4b4b;
            font-size: 1.8rem;
            margin-bottom: 20px;
            opacity: 0;
            animation: fadeIn 1.5s ease-in-out 0.3s forwards;
        }

        .product-list {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            justify-content: center;
            opacity: 0;
            animation: fadeIn 1.5s ease-in-out 0.5s forwards;
        }

        .product {
            background-color: #fff;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            padding: 20px;
            width: 240px;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            opacity: 0;
            animation: fadeInUp 1.5s ease-in-out 0.6s forwards;
        }

        .product:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 18px rgba(0, 0, 0, 0.1);
        }

        .product img {
            max-width: 100%;
            border-radius: 12px;
            transition: transform 0.3s ease;
        }

        .product img:hover {
            transform: scale(1.1);
        }

        .product h3 {
            font-size: 1.4rem;
            color: #d34e5b;
            margin: 15px 0;
        }

        .product p {
            color: #777;
            font-size: 1rem;
        }

        .product button {
            background-color: #f8b400;
            border: none;
            border-radius: 6px;
            color: white;
            font-size: 1.1rem;
            padding: 12px 18px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .product button:hover {
            background-color: #ff8f00;
        }

        .cart-summary {
            background-color: #fff;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            margin-top: 50px;
            text-align: center;
            opacity: 0;
            animation: fadeIn 1.5s ease-in-out 0.8s forwards;
        }

        .cart-summary h2 {
            color: #d34e5b;
            font-size: 2rem;
            margin-bottom: 20px;
        }

        .cart-summary button {
            background-color: #28a745;
            padding: 12px 20px;
            font-size: 1.2rem;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .cart-summary button:hover {
            background-color: #218838;
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0, 0, 0, 0.5);
            padding-top: 60px;
            animation: fadeInModal 0.5s ease-in-out forwards;
        }

        .modal-content {
            background-color: #fff;
            margin: 5% auto;
            padding: 30px;
            border-radius: 12px;
            width: 80%;
            max-width: 500px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            transform: translateY(-20px);
            animation: slideUp 0.5s ease-in-out forwards;
        }

        .close {
            color: #aaa;
            font-size: 28px;
            font-weight: bold;
            position: absolute;
            top: 15px;
            right: 25px;
            font-size: 35px;
        }

        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }

        #credit-card-details {
            display: none;
        }

        select, input {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border-radius: 6px;
            border: 1px solid #ccc;
            font-size: 1rem;
        }

        label {
            font-weight: bold;
            font-size: 1.1rem;
        }

        @keyframes fadeIn {
            0% {
                opacity: 0;
            }
            100% {
                opacity: 1;
            }
        }

        @keyframes fadeInUp {
            0% {
                opacity: 0;
                transform: translateY(30px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInModal {
            0% {
                opacity: 0;
            }
            100% {
                opacity: 1;
            }
        }

        @keyframes slideUp {
            0% {
                transform: translateY(-20px);
            }
            100% {
                transform: translateY(0);
            }
        }

        @keyframes gradientAnimation {
            0% {
                background: linear-gradient(135deg, #f7c4d6, #e0f7fa);
            }
            50% {
                background: linear-gradient(135deg, #f1c6b4, #d2f2e8);
            }
            100% {
                background: linear-gradient(135deg, #f7c4d6, #e0f7fa);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Bienvenido a YOGUIBITE</h1>

        <h2>Productos</h2>
        <div class="product-list">
            <!-- Productos -->
            <div class="product">
                <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQdqLHWeBc1pWoKQGrP3bdjwpnDJo4v2_OzuxAUsi6H4dbt_pnTzibvXcuH3KVLv0Z1CMQ&usqp=CAU" alt="Pastel de Chocolate">
                <h3>Tableta de almendras </h3>
                <p>$50.00</p>
                <input type="number" id="quantity-1" value="1" min="1">
                <button onclick="addToCart(1, 'Tableta de yogurt', 50)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="https://thepounddropper.com/wp-content/uploads/2020/06/image-22-scaled.jpg" alt="Galletas Decoradas">
                <h3>Tableta de mora azul</h3>
                <p>$30.00</p>
                <input type="number" id="quantity-2" value="1" min="1">
                <button onclick="addToCart(2, 'Galletas Decoradas', 30)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="https://rachlmansfield.com/wp-content/uploads/2022/05/IMG_4129-scaled-285x380.jpg" alt="Tableta de ">
                <h3>Tableta de arandano con granola</h3>
                <p>$25.00</p>
                <input type="number" id="quantity-3" value="1" min="1">
                <button onclick="addToCart(3, 'Magdalenas', 25)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="https://thejunetable.com/wp-content/uploads/2022/05/BF7C2641-FF24-4794-A62C-0BCD988B0B30-1544x2048.jpeg">
                <h3>Tableta de oreo</h3>
                <p>$45.00</p>
                <input type="number" id="quantity-4" value="1" min="1">
                <button onclick="addToCart(4, 'Tartas de Frutas', 45)">Agregar al Carrito</button>
            </div>
            <!-- Yogurt de helado -->
            <div class="product">
                <img src="https://feelgoodfoodie.net/wp-content/uploads/2021/06/frozen-yogurt-bark-07.jpg" alt="Yogurt de helado">
                <h3>Tableta de frambuesa</h3>
                <p>$35.00</p>
                <input type="number" id="quantity-5" value="1" min="1">
                <button onclick="addToCart(5, 'Yogurt de Helado con Frutas', 35)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="http://www.myfussyeater.com/wp-content/uploads/2016/03/Chocolate-Banana-Frozen-Yogurt-Bark_01.jpg" alt="Yogurt de helado vainilla">
                <h3>Tableta de banana</h3>
                <p>$30.00</p>
                <input type="number" id="quantity-6" value="1" min="1">
                <button onclick="addToCart(6, 'Yogurt de Helado Sabor Vainilla', 30)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="https://fitmencook.com/wp-content/uploads/2023/07/mango-yogurt-bark-8.jpg" alt="Yogurt de helado chocolate">
                <h3>Tableta de mango</h3>
                <p>$40.00</p>
                <input type="number" id="quantity-7" value="1" min="1">
                <button onclick="addToCart(7, 'Yogurt de Helado Con Choco', 40)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="https://i0.wp.com/vegetarianbaker.com/wp-content/uploads/2015/12/DSC_0198.jpg?w=640" alt="Yogurt de helado fresa">
                <h3>Tableta de kiwi y fresa</h3>
                <p>$35.00</p>
                <input type="number" id="quantity-8" value="1" min="1">
                <button onclick="addToCart(8, 'Yogurt de Helado Fresa', 35)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="https://www.washingtonpost.com/wp-apps/imrs.php?src=https://arc-anglerfish-washpost-prod-washpost.s3.amazonaws.com/public/5QR7I5ASVUI63BECA3A4QTHI6I.jpg&w=860" alt="Yogurt de helado litchi">
                <h3>Tableta de durazno</h3>
                <p>$38.00</p>
                <input type="number" id="quantity-9" value="1" min="1">
                <button onclick="addToCart(9, 'Yogurt de Helado Litchi', 38)">Agregar al Carrito</button>
            </div>
            <div class="product">
                <img src="http://irepo.primecp.com/2018/06/376267/apple-bark_ExtraLarge1000_ID-2785240.jpg?v=2785240" alt="Yogurt de helado banana">
                <h3>Tableta de manzana</h3>
                <p>$35.00</p>
                <input type="number" id="quantity-10" value="1" min="1">
                <button onclick="addToCart(10, 'Yogurt de Helado Banana', 35)">Agregar al Carrito</button>
            </div>
        </div>

        <div class="cart-summary">
            <h2>Resumen del Carrito</h2>
            <p id="cart-items">No hay productos en el carrito.</p>
            <p id="total-price">Total: $0.00</p>
            <button onclick="checkout()">Comprar</button>
        </div>
    </div>

    <div id="myModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <h2>Detalles de la compra</h2>
            <form id="credit-card-form">
                <label for="card-number">Número de Tarjeta:</label>
                <input type="text" id="card-number" required placeholder="XXXX-XXXX-XXXX-XXXX">
                <label for="exp-date">Fecha de Expiración:</label>
                <input type="month" id="exp-date" required>
                <label for="cvv">CVV:</label>
                <input type="text" id="cvv" required placeholder="XXX">
                <button type="submit">Confirmar Pago</button>
            </form>
        </div>
    </div>

    <script>
        let cart = [];
        function addToCart(id, name, price) {
            let quantity = document.getElementById('quantity-' + id).value;
            cart.push({ id, name, price, quantity });
            updateCartSummary();
        }

        function updateCartSummary() {
            let cartItems = document.getElementById('cart-items');
            let totalPrice = 0;
            let cartHTML = '';
            cart.forEach(item => {
                cartHTML += `<p>${item.name} - $${item.price} x ${item.quantity}</p>`;
                totalPrice += item.price * item.quantity;
            });
            cartItems.innerHTML = cartHTML || 'No hay productos en el carrito.';
            document.getElementById('total-price').innerHTML = `Total: $${totalPrice.toFixed(2)}`;
        }

        function checkout() {
            document.getElementById('myModal').style.display = "block";
        }

        const modal = document.getElementById('myModal');
        const close = document.getElementsByClassName("close")[0];
        close.onclick = function() {
            modal.style.display = "none";
        }

        window.onclick = function(event) {
            if (event.target == modal) {
                modal.style.display = "none";
            }
        }

        document.getElementById('credit-card-form').addEventListener('submit', function(event) {
            event.preventDefault();
            alert('Pago exitoso. ¡Gracias por tu compra!');
            cart = [];
            updateCartSummary();
            modal.style.display = "none";
        });
    </script>
</body>
</html>
        <div class="contact-us">
            <h2>Contáctanos</h2>
            <p>Si tienes alguna pregunta o inquietud, ¡no dudes en escribirnos!</p>
            <form action="mailto:tu_correo@ejemplo.com" method="post" enctype="text/plain">
                <label for="name">Nombre:</label>
                <input type="text" id="name" name="name" required placeholder="Tu nombre">

                <label for="email">Correo Electrónico:</label>
                <input type="email" id="email" name="email" required placeholder="Tu correo electrónico">

                <label for="message">Mensaje:</label>
                <textarea id="message" name="message" required placeholder="Escribe tu mensaje aquí..." rows="4"></textarea>

                <button type="submit">Enviar</button>
            </form>
        </div>

    <style>
        .contact-us {
            background-color: #fff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            margin-top: 50px;
            text-align: center;
        }

        .contact-us h2 {
            font-size: 2rem;
            color: #d34e5b;
            margin-bottom: 20px;
        }

        .contact-us p {
            color: #4b4b4b;
            font-size: 1.1rem;
            margin-bottom: 20px;
        }

        .contact-us label {
            font-weight: bold;
            font-size: 1.1rem;
            margin-bottom: 10px;
            display: block;
        }

        .contact-us input, .contact-us textarea {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border-radius: 6px;
            border: 1px solid #ccc;
            font-size: 1rem;
        }

        .contact-us button {
            background-color: #f8b400;
            border: none;
            border-radius: 6px;
            color: white;
            font-size: 1.1rem;
            padding: 12px 18px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .contact-us button:hover {
            background-color: #ff8f00;
        }
    </style>


