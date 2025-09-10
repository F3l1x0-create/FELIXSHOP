<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FELIXSHOP - Tienda de Ropa</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f8f9fa;
            color: #333;
        }

        /* Header */
        header {
            background-color: #2c3e50;
            color: white;
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            letter-spacing: 1px;
        }

        .logo span {
            color: #e67e22;
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 25px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav ul li a:hover {
            color: #e67e22;
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
            font-size: 22px;
        }

        .cart-count {
            position: absolute;
            top: -10px;
            right: -10px;
            background-color: #e74c3c;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 12px;
            font-weight: bold;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url('https://images.unsplash.com/photo-1567401893414-76b7b1e5a7a5?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            height: 500px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            padding: 0 20px;
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 20px;
            margin-bottom: 30px;
            max-width: 700px;
        }

        .btn {
            background-color: #e67e22;
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 30px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: #d35400;
        }

        /* Products Section */
        .products {
            padding: 60px 5%;
        }

        .section-title {
            text-align: center;
            font-size: 32px;
            margin-bottom: 40px;
            color: #2c3e50;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 30px;
        }

        .product-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-10px);
        }

        .product-image {
            height: 200px;
            width: 100%;
            object-fit: cover;
            cursor: pointer;
        }

        .product-info {
            padding: 20px;
        }

        .product-title {
            font-size: 18px;
            margin-bottom: 10px;
        }

        .product-price {
            font-size: 20px;
            font-weight: bold;
            color: #e67e22;
            margin-bottom: 15px;
        }

        .add-to-cart {
            width: 100%;
            padding: 10px;
            background-color: #2c3e50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .add-to-cart:hover {
            background-color: #1a252f;
        }

        /* Contact Info */
        .contact-info {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #2c3e50;
            color: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            z-index: 100;
        }

        .contact-info a {
            display: block;
            color: white;
            text-decoration: none;
            margin: 8px 0;
            display: flex;
            align-items: center;
        }

        .contact-info i {
            margin-right: 10px;
            color: #e67e22;
        }

        /* Cart Modal */
        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            right: 0;
            width: 350px;
            height: 100%;
            background-color: white;
            box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            z-index: 1000;
            overflow-y: auto;
            padding: 20px;
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .close-cart {
            font-size: 24px;
            cursor: pointer;
        }

        .cart-items {
            margin-bottom: 20px;
        }

        .cart-item {
            display: flex;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }

        .cart-item-image {
            width: 80px;
            height: 80px;
            object-fit: cover;
            border-radius: 5px;
        }

        .cart-item-details {
            flex: 1;
            padding: 0 15px;
        }

        .cart-item-title {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .cart-item-price {
            color: #e67e22;
            font-weight: bold;
        }

        .cart-item-quantity {
            display: flex;
            align-items: center;
            margin-top: 5px;
        }

        .quantity-btn {
            width: 25px;
            height: 25px;
            background-color: #eee;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        .quantity-input {
            width: 40px;
            text-align: center;
            margin: 0 5px;
            border: 1px solid #ddd;
            border-radius: 3px;
            padding: 3px;
        }

        .remove-item {
            color: #e74c3c;
            cursor: pointer;
            background: none;
            border: none;
            font-size: 18px;
        }

        .cart-total {
            font-size: 20px;
            font-weight: bold;
            text-align: right;
            margin: 20px 0;
        }

        .checkout-btn {
            width: 100%;
            padding: 15px;
            background-color: #27ae60;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .checkout-btn:hover {
            background-color: #219653;
        }

        /* Product Modal */
        .product-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background-color: white;
            width: 90%;
            max-width: 800px;
            border-radius: 10px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        .modal-header {
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #2c3e50;
            color: white;
        }

        .close-modal {
            font-size: 24px;
            cursor: pointer;
        }

        .modal-body {
            display: flex;
            flex-direction: column;
        }

        .modal-image {
            width: 100%;
            height: 300px;
            object-fit: cover;
        }

        .modal-details {
            padding: 20px;
        }

        .modal-title {
            font-size: 24px;
            margin-bottom: 10px;
        }

        .modal-price {
            font-size: 24px;
            color: #e67e22;
            font-weight: bold;
            margin-bottom: 15px;
        }

        .modal-description {
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .modal-add-to-cart {
            padding: 12px 25px;
            background-color: #2c3e50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s;
        }

        .modal-add-to-cart:hover {
            background-color: #1a252f;
        }

        /* Footer */
        footer {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 30px 5%;
            margin-top: 60px;
        }

        /* Responsive */
        @media (min-width: 768px) {
            .modal-body {
                flex-direction: row;
            }
            
            .modal-image {
                width: 50%;
                height: auto;
            }
            
            .modal-details {
                width: 50%;
            }
        }

        @media (max-width: 768px) {
            nav ul {
                display: none;
            }
            
            .hero h1 {
                font-size: 36px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            .contact-info {
                bottom: 10px;
                right: 10px;
                padding: 10px;
                font-size: 14px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="logo">FELIX<span>SHOP</span></div>
        <nav>
            <ul>
                <li><a href="#">Inicio</a></li>
                <li><a href="#">Hombres</a></li>
                <li><a href="#">Mujeres</a></li>
                <li><a href="#">Niños</a></li>
                <li><a href="#">Ofertas</a></li>
            </ul>
        </nav>
        <div class="cart-icon" id="cartIcon">
            <i class="fas fa-shopping-cart"></i>
            <span class="cart-count" id="cartCount">0</span>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <h1>La moda que te define</h1>
        <p>Descubre las últimas tendencias en moda y encuentra tu estilo único con FELIXSHOP</p>
        <button class="btn">Ver Colección</button>
    </section>

    <!-- Products Section -->
    <section class="products">
        <h2 class="section-title">Nuestros Productos</h2>
        <div class="product-grid" id="productGrid">
            <!-- Products will be added dynamically with JavaScript -->
        </div>
    </section>

    <!-- Contact Info -->
    <div class="contact-info">
        <a href="tel:929725280">
            <i class="fas fa-phone"></i> 929 725 280
        </a>
        <a href="mailto:felixianojeje23177@gmail.com">
            <i class="fas fa-envelope"></i> felixianojeje23177@gmail.com
        </a>
    </div>

    <!-- Cart Modal -->
    <div class="cart-modal" id="cartModal">
        <div class="cart-header">
            <h3>Tu Carrito</h3>
            <span class="close-cart" id="closeCart">&times;</span>
        </div>
        <div class="cart-items" id="cartItems">
            <!-- Cart items will be added dynamically -->
        </div>
        <div class="cart-total" id="cartTotal">Total: $0.00</div>
        <button class="checkout-btn">Finalizar Compra</button>
    </div>

    <!-- Product Modal -->
    <div class="product-modal" id="productModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modalProductTitle">Producto</h3>
                <span class="close-modal" id="closeModal">&times;</span>
            </div>
            <div class="modal-body">
                <img src="" alt="Producto" class="modal-image" id="modalImage">
                <div class="modal-details">
                    <h4 class="modal-title" id="modalTitle"></h4>
                    <div class="modal-price" id="modalPrice"></div>
                    <p class="modal-description" id="modalDescription"></p>
                    <button class="modal-add-to-cart" id="modalAddToCart">Añadir al Carrito</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <p>&copy; 2023 FELIXSHOP - Todos los derechos reservados</p>
    </footer>

    <script>
        // Sample product data
        const products = [
            {
                id: 1,
                title: "Camiseta Básica",
                price: 29.99,
                image: "https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
                description: "Camiseta de algodón 100% de alta calidad. Disponible en varios colores y tallas. Perfecta para uso diario."
            },
            {
                id: 2,
                title: "Jeans Slim Fit",
                price: 59.99,
                image: "https://images.unsplash.com/photo-1542272604-787c3835535d?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
                description: "Jeans de corte slim fit con elastano para mayor comodidad. Disponible en varios lavados y tallas."
            },
            {
                id: 3,
                title: "Chaqueta Denim",
                price: 79.99,
                image: "https://images.unsplash.com/photo-1551028719-00167b16eac5?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
                description: "Chaqueta de denim clásica con detalles en costuras contrastantes. Ideal para completar tu look casual."
            },
            {
                id: 4,
                title: "Vestido Floral",
                price: 49.99,
                image: "https://images.unsplash.com/photo-1515372039744-b8f02a3ae446?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
                description: "Vestido floral con corte A. Tejido ligero y cómodo, perfecto para días soleados."
            },
            {
                id: 5,
                title: "Sudadera con Capucha",
                price: 45.99,
                image: "https://images.unsplash.com/photo-1562157873-818bc0726f68?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
                description: "Sudadera con capucha de felpa suave. Bolsillo tipo canguro y cordón ajustable."
            },
            {
                id: 6,
                title: "Zapatillas Urbanas",
                price: 89.99,
                image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80",
                description: "Zapatillas urbanas con suela de goma y plantilla acolchada. Diseño moderno y cómodo."
            }
        ];

        // DOM Elements
        const productGrid = document.getElementById('productGrid');
        const cartIcon = document.getElementById('cartIcon');
        const cartModal = document.getElementById('cartModal');
        const closeCart = document.getElementById('closeCart');
        const cartItems = document.getElementById('cartItems');
        const cartCount = document.getElementById('cartCount');
        const cartTotal = document.getElementById('cartTotal');
        const productModal = document.getElementById('productModal');
        const closeModal = document.getElementById('closeModal');
        const modalImage = document.getElementById('modalImage');
        const modalTitle = document.getElementById('modalTitle');
        const modalPrice = document.getElementById('modalPrice');
        const modalDescription = document.getElementById('modalDescription');
        const modalAddToCart = document.getElementById('modalAddToCart');

        // Cart array
        let cart = [];

        // Display products
        function displayProducts() {
            productGrid.innerHTML = '';
            products.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-card';
                productCard.innerHTML = `
                    <img src="${product.image}" alt="${product.title}" class="product-image" data-id="${product.id}">
                    <div class="product-info">
                        <h3 class="product-title">${product.title}</h3>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <button class="add-to-cart" data-id="${product.id}">Añadir al Carrito</button>
                    </div>
                `;
                productGrid.appendChild(productCard);
            });

            // Add event listeners to product images and buttons
            document.querySelectorAll('.product-image').forEach(img => {
                img.addEventListener('click', (e) => {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    openProductModal(productId);
                });
            });

            document.querySelectorAll('.add-to-cart').forEach(button => {
                button.addEventListener('click', (e) => {
                    const productId = parseInt(e.target.getAttribute('data-id'));
                    addToCart(productId);
                });
            });
        }

        // Open product modal
        function openProductModal(productId) {
            const product = products.find(p => p.id === productId);
            if (product) {
                modalImage.src = product.image;
                modalTitle.textContent = product.title;
                modalPrice.textContent = `$${product.price.toFixed(2)}`;
                modalDescription.textContent = product.description;
                
                modalAddToCart.setAttribute('data-id', productId);
                
                productModal.style.display = 'flex';
            }
        }

        // Add to cart
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            if (product) {
                const existingItem = cart.find(item => item.id === productId);
                if (existingItem) {
                    existingItem.quantity++;
                } else {
                    cart.push({
                        id: product.id,
                        title: product.title,
                        price: product.price,
                        image: product.image,
                        quantity: 1
                    });
                }
                updateCart();
            }
        }

        // Update cart
        function updateCart() {
            cartCount.textContent = cart.reduce((total, item) => total + item.quantity, 0);
            
            cartItems.innerHTML = '';
            let total = 0;
            
            cart.forEach(item => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                
                const cartItem = document.createElement('div');
                cartItem.className = 'cart-item';
                cartItem.innerHTML = `
                    <img src="${item.image}" alt="${item.title}" class="cart-item-image">
                    <div class="cart-item-details">
                        <div class="cart-item-title">${item.title}</div>
                        <div class="cart-item-price">$${item.price.toFixed(2)}</div>
                        <div class="cart-item-quantity">
                            <button class="quantity-btn decrease" data-id="${item.id}">-</button>
                            <input type="number" class="quantity-input" value="${item.quantity}" min="1" data-id="${item.id}">
                            <button class="quantity-btn increase" data-id="${item.id}">+</button>
                        </div>
                    </div>
                    <button class="remove-item" data-id="${item.id}">&times;</button>
                `;
                cartItems.appendChild(cartItem);
            });
            
            cartTotal.textContent = `Total: $${total.toFixed(2)}`;
            
            // Add event listeners to cart items
            document.querySelectorAll('.decrease').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const id = parseInt(e.target.getAttribute('data-id'));
                    decreaseQuantity(id);
                });
            });
            
            document.querySelectorAll('.increase').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const id = parseInt(e.target.getAttribute('data-id'));
                    increaseQuantity(id);
                });
            });
            
            document.querySelectorAll('.remove-item').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const id = parseInt(e.target.getAttribute('data-id'));
                    removeFromCart(id);
                });
            });
            
            document.querySelectorAll('.quantity-input').forEach(input => {
                input.addEventListener('change', (e) => {
                    const id = parseInt(e.target.getAttribute('data-id'));
                    const quantity = parseInt(e.target.value);
                    updateItemQuantity(id, quantity);
                });
            });
        }

        // Decrease quantity
        function decreaseQuantity(productId) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                if (item.quantity > 1) {
                    item.quantity--;
                } else {
                    removeFromCart(productId);
                    return;
                }
                updateCart();
            }
        }

        // Increase quantity
        function increaseQuantity(productId) {
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity++;
                updateCart();
            }
        }

        // Remove from cart
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        // Update item quantity
        function updateItemQuantity(productId, quantity) {
            if (quantity < 1) {
                removeFromCart(productId);
                return;
            }
            
            const item = cart.find(item => item.id === productId);
            if (item) {
                item.quantity = quantity;
                updateCart();
            }
        }

        // Event Listeners
        cartIcon.addEventListener('click', () => {
            cartModal.style.display = 'block';
        });

        closeCart.addEventListener('click', () => {
            cartModal.style.display = 'none';
        });

        closeModal.addEventListener('click', () => {
            productModal.style.display = 'none';
        });

        modalAddToCart.addEventListener('click', (e) => {
            const productId = parseInt(e.target.getAttribute('data-id'));
            addToCart(productId);
            productModal.style.display = 'none';
            
            // Show confirmation
            const product = products.find(p => p.id === productId);
            if (product) {
                alert(`¡${product.title} añadido al carrito!`);
            }
        });

        // Close modals when clicking outside
        window.addEventListener('click', (e) => {
            if (e.target === cartModal) {
                cartModal.style.display = 'none';
            }
            if (e.target === productModal) {
                productModal.style.display = 'none';
            }
        });

        // Initialize the page
        displayProducts();
    </script>
</body>
</html>
