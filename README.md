<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crust & Crumbs - Bakery & Pastry Shop</title>
    <style>
        /* CSS RESET & VARIABLES */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary-color: #d4a373;
            --primary-hover: #bc8a5f;
            --bg-color: #faf9f6;
            --card-bg: #ffffff;
            --text-color: #333333;
            --accent-color: #e63946;
            --staff-color: #4a6fa5;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
        }

        /* HEADER & NAVBAR */
        header {
            background-color: var(--card-bg);
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--primary-color);
            text-decoration: none;
        }

        .nav-controls {
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .mode-toggle-btn {
            background-color: #333;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.85rem;
            transition: background 0.3s;
        }

        .mode-toggle-btn:hover {
            background-color: #555;
        }

        .cart-icon-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            position: relative;
        }

        .cart-badge {
            position: absolute;
            top: -8px;
            right: -10px;
            background-color: var(--accent-color);
            color: white;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 0.75rem;
            font-weight: bold;
        }

        /* HERO SECTION */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), 
                        url('https://images.unsplash.com/photo-1509440159596-0249088772ff?auto=format&fit=crop&w=1200&q=80') center/cover;
            height: 60vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            text-align: center;
            padding: 0 1rem;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
        }

        .btn {
            background-color: var(--primary-color);
            color: white;
            padding: 0.8rem 1.8rem;
            border: none;
            border-radius: 25px;
            font-size: 1rem;
            cursor: pointer;
            transition: background 0.3s ease;
            text-decoration: none;
        }

        .btn:hover {
            background-color: var(--primary-hover);
        }

        /* VIEW TOGGLE STYLES */
        .view-section {
            display: none;
        }

        .view-section.active {
            display: block;
        }

        /* MENU SECTION */
        .container {
            max-width: 1200px;
            margin: 3rem auto;
            padding: 0 2rem;
        }

        .section-title {
            text-align: center;
            font-size: 2.2rem;
            margin-bottom: 1.5rem;
            color: var(--primary-color);
        }

        .filter-buttons {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            background: white;
            border: 1px solid var(--primary-color);
            color: var(--primary-color);
            padding: 0.5rem 1.2rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .filter-btn.active, .filter-btn:hover {
            background: var(--primary-color);
            color: white;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background: var(--card-bg);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            transition: transform 0.3s ease;
            display: flex;
            flex-direction: column;
        }

        .product-card:hover {
            transform: translateY(-5px);
        }

        .product-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .product-info {
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .product-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
        }

        .product-desc {
            font-size: 0.9rem;
            color: #666;
            margin-bottom: 1rem;
            flex-grow: 1;
        }

        .product-price-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .product-price {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--primary-color);
        }

        .add-to-cart-btn {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            cursor: pointer;
        }

        .add-to-cart-btn:hover {
            background-color: var(--primary-hover);
        }

        /* STAFF DASHBOARD STYLES */
        .kpi-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .kpi-card {
            background: white;
            padding: 1.2rem 1.5rem;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            border-left: 5px solid var(--staff-color);
        }

        .kpi-card h4 {
            font-size: 0.85rem;
            color: #666;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 0.5rem;
        }

        .kpi-card .kpi-value {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--text-color);
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 2rem;
        }

        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
        }

        .dashboard-card {
            background: white;
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            margin-bottom: 2rem;
        }

        .dashboard-card h3 {
            margin-bottom: 1rem;
            color: var(--staff-color);
            border-bottom: 2px solid #f0f0f0;
            padding-bottom: 0.5rem;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.3rem;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 0.6rem;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 0.9rem;
        }

        .form-btn {
            background-color: var(--staff-color);
            color: white;
            border: none;
            padding: 0.7rem 1.2rem;
            border-radius: 6px;
            cursor: pointer;
            width: 100%;
            font-size: 1rem;
        }

        .form-btn:hover {
            background-color: #3b5984;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
        }

        .data-table th, .data-table td {
            padding: 0.8rem;
            text-align: left;
            border-bottom: 1px solid #eee;
            vertical-align: middle;
        }

        .data-table th {
            background-color: #f8f9fa;
            color: #555;
        }

        .delete-btn {
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 0.3rem 0.6rem;
            border-radius: 4px;
            cursor: pointer;
            margin-left: 4px;
        }

        .action-btn {
            background-color: #e0e0e0;
            color: #333;
            border: none;
            padding: 0.3rem 0.6rem;
            border-radius: 4px;
            cursor: pointer;
        }

        .action-btn:hover {
            background-color: #ccc;
        }

        .status-select {
            padding: 0.3rem 0.5rem;
            border-radius: 6px;
            font-size: 0.85rem;
            font-weight: bold;
            border: 1px solid #ccc;
            cursor: pointer;
        }

        .status-Received { background-color: #e3f2fd; color: #0d47a1; }
        .status-Preparing { background-color: #fff3e0; color: #e65100; }
        .status-Ready { background-color: #e8f5e9; color: #1b5e20; }
        .status-Completed { background-color: #eceff1; color: #37474f; }
        .status-Cancelled { background-color: #ffebee; color: #b71c1c; }

        /* CART DRAWER */
        .cart-drawer {
            position: fixed;
            top: 0;
            right: -400px;
            width: 350px;
            height: 100%;
            background-color: white;
            box-shadow: -2px 0 10px rgba(0,0,0,0.1);
            z-index: 200;
            transition: right 0.3s ease;
            display: flex;
            flex-direction: column;
        }

        .cart-drawer.open {
            right: 0;
        }

        .cart-header {
            padding: 1.5rem;
            background: var(--primary-color);
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .close-cart {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .cart-items {
            flex-grow: 1;
            overflow-y: auto;
            padding: 1rem;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            border-bottom: 1px solid #eee;
            padding-bottom: 0.5rem;
        }

        .cart-item-info h4 {
            font-size: 0.95rem;
        }

        .cart-item-info p {
            font-size: 0.85rem;
            color: #666;
        }

        .cart-item-remove {
            background: none;
            border: none;
            color: var(--accent-color);
            cursor: pointer;
            font-size: 0.9rem;
        }

        .cart-footer {
            padding: 1.5rem;
            border-top: 1px solid #eee;
        }

        .cart-total {
            display: flex;
            justify-content: space-between;
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 1rem;
        }

        .checkout-btn {
            width: 100%;
            padding: 0.8rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 6px;
            font-size: 1rem;
            cursor: pointer;
        }

        /* OVERLAY */
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.4);
            z-index: 150;
            display: none;
        }

        .overlay.active {
            display: block;
        }

        /* --- NEW ADDED CSS STYLES --- */
        .search-container {
            max-width: 500px;
            margin: 0 auto 1.5rem auto;
        }

        .search-input {
            width: 100%;
            padding: 0.7rem 1.2rem;
            border: 2px solid var(--primary-color);
            border-radius: 25px;
            font-size: 0.95rem;
            outline: none;
        }

        .qty-controls {
            display: flex;
            align-items: center;
            gap: 0.4rem;
            margin-top: 0.3rem;
        }

        .qty-btn {
            background: #eee;
            border: 1px solid #ccc;
            width: 24px;
            height: 24px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .qty-btn:hover {
            background: #ddd;
        }

        .custom-modal {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 5px 25px rgba(0,0,0,0.2);
            z-index: 300;
            display: none;
            width: 90%;
            max-width: 480px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .custom-modal.active {
            display: block;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.2rem;
            border-bottom: 1px solid #eee;
            padding-bottom: 0.5rem;
        }

        .modal-header h3 {
            color: var(--primary-color);
        }

        .close-modal-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #888;
        }

        .qr-box {
            text-align: center;
            background: #f8f9fa;
            padding: 1rem;
            border-radius: 8px;
            border: 1px dashed var(--primary-color);
            margin-bottom: 1rem;
        }

        .receipt-stub {
            background: #fff;
            border: 1px solid #ddd;
            padding: 1rem;
            font-family: monospace;
            border-radius: 6px;
            margin-bottom: 1rem;
        }

        .receipt-number {
            font-size: 1.8rem;
            font-weight: bold;
            text-align: center;
            color: var(--primary-color);
            margin: 0.5rem 0;
        }

        @media print {
            body * {
                visibility: hidden;
            }
            #receiptModal, #receiptModal * {
                visibility: visible;
            }
            #receiptModal {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                box-shadow: none;
            }
            .no-print {
                display: none !important;
            }
        }
    </style>
</head>
<body>

    <!-- NAVIGATION -->
    <header>
        <nav>
            <a href="#" class="logo">🥐 Crust & Crumbs</a>
            <div class="nav-controls">
                <button class="mode-toggle-btn" id="viewToggleBtn">Switch to Staff Dashboard</button>
                <button class="cart-icon-btn" id="cartBtn">
                    🛒 <span class="cart-badge" id="cartBadge">0</span>
                </button>
            </div>
        </nav>
    </header>

    <!-- CUSTOMER VIEW SECTION -->
    <main id="customerView" class="view-section active">
        <!-- HERO SECTION -->
        <section class="hero">
            <h1>Freshly Baked Every Day</h1>
            <p>Delicious handcrafted cakes, pastries, and artisanal breads.</p>
            <a href="#menu" class="btn">Explore Menu</a>
        </section>

        <!-- MENU SECTION -->
        <div class="container" id="menu">
            <h2 class="section-title">Our Menu</h2>

            <!-- NEW: Search Bar -->
            <div class="search-container">
                <input type="text" id="searchInput" class="search-input" placeholder="🔍 Search pastries, cakes, breads...">
            </div>

            <div class="filter-buttons">
                <button class="filter-btn active" data-category="all">All</button>
                <button class="filter-btn" data-category="cakes">Cakes</button>
                <button class="filter-btn" data-category="pastries">Pastries</button>
                <button class="filter-btn" data-category="breads">Breads</button>
            </div>

            <div class="products-grid" id="productsGrid">
                <!-- Products rendered dynamically by JS -->
            </div>
        </div>
    </main>

    <!-- UPDATED STAFF DASHBOARD VIEW SECTION -->
    <main id="staffView" class="view-section">
        <div class="container">
            <h2 class="section-title" style="color: var(--staff-color);">Staff Operations Dashboard</h2>

            <!-- KPI Summary Cards -->
            <div class="kpi-cards">
                <div class="kpi-card">
                    <h4>Total Sales Today</h4>
                    <div class="kpi-value" id="kpiTotalSales">₱0.00</div>
                </div>
                <div class="kpi-card" style="border-left-color: #2a9d8f;">
                    <h4>Active Orders</h4>
                    <div class="kpi-value" id="kpiActiveOrders">0</div>
                </div>
                <div class="kpi-card" style="border-left-color: #e76f51;">
                    <h4>Total Menu Items</h4>
                    <div class="kpi-value" id="kpiTotalProducts">0</div>
                </div>
            </div>

            <div class="dashboard-grid">
                <!-- FORM: Add New Product -->
                <div>
                    <div class="dashboard-card">
                        <h3>Add New Product</h3>
                        <form id="addProductForm">
                            <div class="form-group">
                                <label for="prodName">Product Name</label>
                                <input type="text" id="prodName" required placeholder="e.g. Cheese Ensaymada">
                            </div>
                            <div class="form-group">
                                <label for="prodCategory">Category</label>
                                <select id="prodCategory">
                                    <option value="pastries">Pastries</option>
                                    <option value="cakes">Cakes</option>
                                    <option value="breads">Breads</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="prodPrice">Price (₱)</label>
                                <input type="number" step="0.01" min="0.01" id="prodPrice" required placeholder="150.00">
                            </div>
                            <div class="form-group">
                                <label for="prodStock">Initial Stock Quantity</label>
                                <input type="number" id="prodStock" required value="20" min="1">
                            </div>
                            <div class="form-group">
                                <label for="prodDesc">Description</label>
                                <textarea id="prodDesc" rows="2" placeholder="Short description..."></textarea>
                            </div>
                            <div class="form-group">
                                <label for="prodImage">Image URL</label>
                                <input type="url" id="prodImage" required placeholder="https://...">
                            </div>
                            <button type="submit" class="form-btn">Add Product to Menu</button>
                        </form>
                    </div>
                </div>

                <!-- TABLES: Menu Management & Customer Orders -->
                <div>
                    <!-- Customer Orders Table with Status Management -->
                    <div class="dashboard-card">
                        <h3>Recent Orders Received</h3>
                        <div style="overflow-x: auto;">
                            <table class="data-table">
                                <thead>
                                    <tr>
                                        <th>Order ID</th>
                                        <th>Items</th>
                                        <th>Total</th>
                                        <th>Order Status</th>
                                    </tr>
                                </thead>
                                <tbody id="ordersTableBody">
                                    <!-- Orders rendered dynamically -->
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- Manage Menu Inventory & Stock Control Table -->
                    <div class="dashboard-card">
                        <h3>Manage Inventory & Stock</h3>
                        <div style="overflow-x: auto;">
                            <table class="data-table">
                                <thead>
                                    <tr>
                                        <th>Item</th>
                                        <th>Category</th>
                                        <th>Price</th>
                                        <th>Stock</th>
                                        <th>Action</th>
                                    </tr>
                                </thead>
                                <tbody id="staffProductTable">
                                    <!-- Inventory rendered dynamically -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- CART SLIDING DRAWER -->
    <div class="cart-drawer" id="cartDrawer">
        <div class="cart-header">
            <h3>Your Order</h3>
            <button class="close-cart" id="closeCart">&times;</button>
        </div>
        <div class="cart-items" id="cartItems">
            <!-- Cart items added dynamically -->
        </div>
        <div class="cart-footer">
            <div class="cart-total">
                <span>Total:</span>
                <span id="cartTotal">₱0.00</span>
            </div>
            <button class="checkout-btn" onclick="checkout()">Checkout</button>
        </div>
    </div>

    <!-- NEW: IN-SHOP CHECKOUT MODAL -->
    <div class="custom-modal" id="checkoutModal">
        <div class="modal-header">
            <h3>In-Shop Order Details</h3>
            <button class="close-modal-btn" onclick="closeModal('checkoutModal')">&times;</button>
        </div>
        <form id="checkoutDetailsForm">
            <div class="form-group">
                <label for="custName">Customer Name</label>
                <input type="text" id="custName" required placeholder="Enter customer name">
            </div>
            <div class="form-group">
                <label for="orderType">Order Type</label>
                <select id="orderType" onchange="toggleTableNo()">
                    <option value="Dine-In">Dine-In</option>
                    <option value="Take-Out">Take-Out</option>
                </select>
            </div>
            <div class="form-group" id="tableNoGroup">
                <label for="tableNo">Table Number (Optional)</label>
                <input type="text" id="tableNo" placeholder="e.g. Table 4">
            </div>
            <div class="form-group">
                <label for="paymentMethod">Payment Method</label>
                <select id="paymentMethod" onchange="togglePaymentFields()">
                    <option value="Cash">Cash</option>
                    <option value="GCash">GCash</option>
                </select>
            </div>

            <!-- Cash Payment Details -->
            <div id="cashFields">
                <div class="form-group">
                    <label for="amountTendered">Amount Tendered (₱)</label>
                    <input type="number" id="amountTendered" step="0.01" placeholder="0.00" oninput="calculateChange()">
                </div>
                <div class="form-group">
                    <label>Change: <strong id="changeDisplay" style="color: green;">₱0.00</strong></label>
                </div>
            </div>

            <!-- GCash Payment Details -->
            <div id="gcashFields" style="display: none;">
                <div class="qr-box">
                    <p style="font-weight: bold; margin-bottom: 0.5rem;">Scan GCash QR Code at Counter</p>
                    <img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=GCash-CrustAndCrumbs-09171234567" alt="GCash QR" style="width: 140px; height: 140px;">
                    <p style="font-size: 0.85rem; color: #555; margin-top: 0.5rem;">Account: Crust & Crumbs Bakery<br>Number: 0917-123-4567</p>
                </div>
                <div class="form-group">
                    <label for="gcashRef">GCash Reference No.</label>
                    <input type="text" id="gcashRef" placeholder="e.g. 100293847">
                </div>
            </div>

            <button type="submit" class="form-btn" style="background-color: var(--primary-color);">Confirm & Place Order</button>
        </form>
    </div>

    <!-- NEW: IN-SHOP ORDER RECEIPT / SUMMARY MODAL -->
    <div class="custom-modal" id="receiptModal">
        <div class="modal-header no-print">
            <h3>Order Summary & Claim Stub</h3>
            <button class="close-modal-btn" onclick="closeModal('receiptModal')">&times;</button>
        </div>
        <div class="receipt-stub" id="receiptContent">
            <!-- Dynamically injected receipt details -->
        </div>
        <div class="no-print" style="display: flex; gap: 1rem;">
            <button class="form-btn" onclick="window.print()" style="background-color: #333;">🖨️ Print Receipt (POS)</button>
            <button class="form-btn" onclick="closeModal('receiptModal')" style="background-color: var(--primary-color);">Done</button>
        </div>
    </div>

    <div class="overlay" id="overlay"></div>

    <!-- JAVASCRIPT -->
    <script>
        // Default Sample Products
        const defaultProducts = [
            {
                id: 1,
                name: 'Butter Croissant',
                category: 'pastries',
                price: 217.51,
                stock: 15,
                isAvailable: true,
                desc: 'Flaky, buttery, traditional French croissant.',
                image: 'https://images.unsplash.com/photo-1555507036-ab1f4038808a?auto=format&fit=crop&w=500&q=80'
            },
            {
                id: 2,
                name: 'Chocolate Lava Cake',
                category: 'cakes',
                price: 372.88,
                stock: 8,
                isAvailable: true,
                desc: 'Rich chocolate cake with a molten chocolate center.',
                image: 'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?auto=format&fit=crop&w=500&q=80'
            },
            {
                id: 3,
                name: 'Artisanal Sourdough',
                category: 'breads',
                price: 341.81,
                stock: 10,
                isAvailable: true,
                desc: 'Naturally fermented bread with a crispy crust.',
                image: 'https://fareisle.com/wp-content/uploads/2020/04/sourdough-bread-ecourse-06-2.jpg'
            },
            {
                id: 4,
                name: 'Strawberry Macaron',
                category: 'pastries',
                price: 155.37,
                stock: 25,
                isAvailable: true,
                desc: 'Sweet almond meringue cookie filled with jam.',
                image: 'https://images.unsplash.com/photo-1569864358642-9d1684040f43?auto=format&fit=crop&w=500&q=80'
            },
            {
                id: 5,
                name: 'Red Velvet Slice',
                category: 'cakes',
                price: 310.74,
                stock: 12,
                isAvailable: true,
                desc: 'Classic red velvet layered with cream cheese frosting.',
                image: 'https://images.unsplash.com/photo-1586788680434-30d324b2d46f?auto=format&fit=crop&w=500&q=80'
            },
            {
                id: 6,
                name: 'Cinnamon Roll',
                category: 'pastries',
                price: 248.59,
                stock: 18,
                isAvailable: true,
                desc: 'Warm roll spiced with cinnamon and glazed with icing.',
                image: 'https://images.unsplash.com/photo-1509365465985-25d11c17e812?auto=format&fit=crop&w=500&q=80'
            }
        ];

        // NEW: Persistent Storage via LocalStorage
        let products = JSON.parse(localStorage.getItem('cnc_products')) || defaultProducts;
        let orders = JSON.parse(localStorage.getItem('cnc_orders')) || [
            { id: '#1001', items: '2x Butter Croissant', total: 435.02, status: 'Preparing', custName: 'Walk-In Customer', type: 'Take-Out', payment: 'Cash' }
        ];

        let cart = [];
        let activeCategory = 'all';

        // DOM Elements
        const customerView = document.getElementById('customerView');
        const staffView = document.getElementById('staffView');
        const viewToggleBtn = document.getElementById('viewToggleBtn');
        const productsGrid = document.getElementById('productsGrid');
        const cartDrawer = document.getElementById('cartDrawer');
        const cartBtn = document.getElementById('cartBtn');
        const closeCart = document.getElementById('closeCart');
        const overlay = document.getElementById('overlay');
        const cartItemsContainer = document.getElementById('cartItems');
        const cartTotalDisplay = document.getElementById('cartTotal');
        const cartBadge = document.getElementById('cartBadge');
        const filterBtns = document.querySelectorAll('.filter-btn');
        const addProductForm = document.getElementById('addProductForm');
        const staffProductTable = document.getElementById('staffProductTable');
        const ordersTableBody = document.getElementById('ordersTableBody');
        const searchInput = document.getElementById('searchInput');

        // Helper: Save state to localStorage
        function saveState() {
            localStorage.setItem('cnc_products', JSON.stringify(products));
            localStorage.setItem('cnc_orders', JSON.stringify(orders));
        }

        // Initialize Page
        function init() {
            renderProducts(products);
            renderStaffTables();
            setupEventListeners();
        }

        // View Switcher Handler
        viewToggleBtn.addEventListener('click', () => {
            if (customerView.classList.contains('active')) {
                customerView.classList.remove('active');
                staffView.classList.add('active');
                viewToggleBtn.textContent = 'Switch to Customer View';
            } else {
                staffView.classList.remove('active');
                customerView.classList.add('active');
                viewToggleBtn.textContent = 'Switch to Staff Dashboard';
            }
        });

        // Render Customer Products Grid
        function renderProducts(items) {
            const availableItems = items.filter(p => p.isAvailable && p.stock > 0);
            
            if (availableItems.length === 0) {
                productsGrid.innerHTML = '<p style="grid-column: 1/-1; text-align: center;">No products available right now.</p>';
                return;
            }

            productsGrid.innerHTML = availableItems.map(product => `
                <div class="product-card">
                    <img src="${product.image}" alt="${product.name}" class="product-img">
                    <div class="product-info">
                        <h3 class="product-title">${product.name}</h3>
                        <p class="product-desc">${product.desc}</p>
                        <div class="product-price-row">
                            <span class="product-price">₱${product.price.toFixed(2)}</span>
                            <button class="add-to-cart-btn" onclick="addToCart(${product.id})">Add to Cart</button>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // Search Bar Event Handler
        if (searchInput) {
            searchInput.addEventListener('input', (e) => {
                const query = e.target.value.toLowerCase().trim();
                const filtered = products.filter(p => {
                    const matchesCategory = (activeCategory === 'all' || p.category === activeCategory);
                    const matchesQuery = p.name.toLowerCase().includes(query) || p.desc.toLowerCase().includes(query);
                    return matchesCategory && matchesQuery;
                });
                renderProducts(filtered);
            });
        }

        // Filter Products
        filterBtns.forEach(btn => {
            btn.addEventListener('click', (e) => {
                filterBtns.forEach(b => b.classList.remove('active'));
                e.target.classList.add('active');

                activeCategory = e.target.dataset.category;
                const query = searchInput ? searchInput.value.toLowerCase().trim() : '';
                
                const filtered = products.filter(p => {
                    const matchesCategory = (activeCategory === 'all' || p.category === activeCategory);
                    const matchesQuery = p.name.toLowerCase().includes(query) || p.desc.toLowerCase().includes(query);
                    return matchesCategory && matchesQuery;
                });
                renderProducts(filtered);
            });
        });

        // Add to Cart
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const cartItem = cart.find(item => item.id === productId);

            if (cartItem) {
                if (cartItem.quantity >= product.stock) {
                    alert(`Sorry, only ${product.stock} pcs available in stock.`);
                    return;
                }
                cartItem.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }

            updateCart();
            openCartDrawer();
        }

        // NEW: Quantity adjustment in cart drawer
        function updateCartQty(productId, change) {
            const cartItem = cart.find(item => item.id === productId);
            const product = products.find(p => p.id === productId);

            if (cartItem) {
                if (change > 0 && cartItem.quantity >= product.stock) {
                    alert(`Sorry, only ${product.stock} pcs available in stock.`);
                    return;
                }
                cartItem.quantity += change;
                if (cartItem.quantity <= 0) {
                    removeFromCart(productId);
                    return;
                }
            }
            updateCart();
        }

        // Remove from Cart
        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        // Update Cart UI
        function updateCart() {
            if (cart.length === 0) {
                cartItemsContainer.innerHTML = '<p style="text-align:center; color:#888;">Your cart is empty.</p>';
            } else {
                cartItemsContainer.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <h4>${item.name}</h4>
                            <p>₱${item.price.toFixed(2)} x ${item.quantity}</p>
                            <div class="qty-controls">
                                <button class="qty-btn" onclick="updateCartQty(${item.id}, -1)">-</button>
                                <span>${item.quantity}</span>
                                <button class="qty-btn" onclick="updateCartQty(${item.id}, 1)">+</button>
                            </div>
                        </div>
                        <button class="cart-item-remove" onclick="removeFromCart(${item.id})">Remove</button>
                    </div>
                `).join('');
            }

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const itemCount = cart.reduce((sum, item) => sum + item.quantity, 0);

            cartTotalDisplay.textContent = `₱${total.toFixed(2)}`;
            cartBadge.textContent = itemCount;
        }

        // NEW: Open Checkout Form Modal
        function checkout() {
            if (cart.length === 0) {
                alert('Your cart is empty!');
                return;
            }
            closeCartDrawer();
            document.getElementById('checkoutModal').classList.add('active');
            overlay.classList.add('active');
            togglePaymentFields();
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
            overlay.classList.remove('active');
        }

        function toggleTableNo() {
            const type = document.getElementById('orderType').value;
            document.getElementById('tableNoGroup').style.display = type === 'Dine-In' ? 'block' : 'none';
        }

        function togglePaymentFields() {
            const method = document.getElementById('paymentMethod').value;
            if (method === 'Cash') {
                document.getElementById('cashFields').style.display = 'block';
                document.getElementById('gcashFields').style.display = 'none';
            } else {
                document.getElementById('cashFields').style.display = 'none';
                document.getElementById('gcashFields').style.display = 'block';
            }
        }

        function calculateChange() {
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const tendered = parseFloat(document.getElementById('amountTendered').value) || 0;
            const change = tendered - total;
            document.getElementById('changeDisplay').textContent = `₱${change >= 0 ? change.toFixed(2) : '0.00'}`;
        }

        // Handle Checkout Submission & Modal Order Summary Receipt Generation
        document.getElementById('checkoutDetailsForm').addEventListener('submit', (e) => {
            e.preventDefault();

            const custName = document.getElementById('custName').value.trim() || 'Walk-In Customer';
            const orderType = document.getElementById('orderType').value;
            const tableNo = document.getElementById('tableNo').value.trim();
            const paymentMethod = document.getElementById('paymentMethod').value;
            const gcashRef = document.getElementById('gcashRef').value.trim();
            const tendered = parseFloat(document.getElementById('amountTendered').value) || 0;

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);

            if (paymentMethod === 'Cash' && tendered < total) {
                alert(`Amount tendered (₱${tendered.toFixed(2)}) is less than total amount (₱${total.toFixed(2)})!`);
                return;
            }

            const orderId = `#${Math.floor(1000 + Math.random() * 9000)}`;
            const orderItemsSummary = cart.map(i => `${i.quantity}x ${i.name}`).join(', ');

            // Deduct Stocks
            cart.forEach(cartItem => {
                const prod = products.find(p => p.id === cartItem.id);
                if (prod) {
                    prod.stock -= cartItem.quantity;
                }
            });

            // Add Order to List
            const newOrder = {
                id: orderId,
                custName: custName,
                type: orderType + (tableNo ? ` (${tableNo})` : ''),
                payment: paymentMethod + (gcashRef ? ` Ref:${gcashRef}` : ''),
                items: orderItemsSummary,
                total: total,
                status: 'Received'
            };

            orders.unshift(newOrder);
            saveState();

            // Render Updates
            renderProducts(products);
            renderStaffTables();

            // Generate Digital Receipt HTML
            const changeVal = tendered - total;
            const dateStr = new Date().toLocaleString();
            
            document.getElementById('receiptContent').innerHTML = `
                <div style="text-align: center; margin-bottom: 0.5rem;">
                    <h2>🥐 CRUST & CRUMBS</h2>
                    <p style="font-size: 0.8rem;">Bakery & Pastry Shop</p>
                    <p style="font-size: 0.75rem;">${dateStr}</p>
                </div>
                <hr style="border-top: 1px dashed #ccc; margin: 0.5rem 0;">
                <p style="font-size: 0.85rem;"><strong>Order Claim Stub:</strong></p>
                <div class="receipt-number">${orderId}</div>
                <p style="font-size: 0.85rem;"><strong>Customer:</strong> ${custName}</p>
                <p style="font-size: 0.85rem;"><strong>Option:</strong> ${newOrder.type}</p>
                <p style="font-size: 0.85rem;"><strong>Payment:</strong> ${newOrder.payment}</p>
                <hr style="border-top: 1px dashed #ccc; margin: 0.5rem 0;">
                <div style="font-size: 0.85rem; margin-bottom: 0.5rem;">
                    ${cart.map(i => `<div style="display:flex; justify-content:space-between;"><span>${i.quantity}x ${i.name}</span><span>₱${(i.price * i.quantity).toFixed(2)}</span></div>`).join('')}
                </div>
                <hr style="border-top: 1px dashed #ccc; margin: 0.5rem 0;">
                <div style="display:flex; justify-content:space-between; font-weight:bold; font-size: 1rem;">
                    <span>Total:</span><span>₱${total.toFixed(2)}</span>
                </div>
                ${paymentMethod === 'Cash' ? `
                <div style="display:flex; justify-content:space-between; font-size: 0.85rem;">
                    <span>Tendered:</span><span>₱${tendered.toFixed(2)}</span>
                </div>
                <div style="display:flex; justify-content:space-between; font-size: 0.85rem;">
                    <span>Change:</span><span>₱${changeVal.toFixed(2)}</span>
                </div>` : ''}
                <hr style="border-top: 1px dashed #ccc; margin: 0.5rem 0;">
                <p style="text-align:center; font-size: 0.8rem; margin-top: 0.5rem;">Please present this stub at the counter.<br>Thank you for your order!</p>
            `;

            // Reset Form and Cart State
            cart = [];
            updateCart();
            closeModal('checkoutModal');

            // Open Receipt Modal
            document.getElementById('receiptModal').classList.add('active');
            overlay.classList.add('active');

            // Reset Checkout form fields
            document.getElementById('checkoutDetailsForm').reset();
            document.getElementById('changeDisplay').textContent = '₱0.00';
        });

        // STAFF DASHBOARD FUNCTIONS
        function renderStaffTables() {
            // Update KPI Cards
            const totalSales = orders
                .filter(o => o.status !== 'Cancelled')
                .reduce((sum, o) => sum + o.total, 0);
            const activeOrders = orders.filter(o => o.status === 'Received' || o.status === 'Preparing').length;

            document.getElementById('kpiTotalSales').textContent = `₱${totalSales.toFixed(2)}`;
            document.getElementById('kpiActiveOrders').textContent = activeOrders;
            document.getElementById('kpiTotalProducts').textContent = products.length;

            // Render Inventory Table
            staffProductTable.innerHTML = products.map(product => `
                <tr>
                    <td><strong>${product.name}</strong></td>
                    <td style="text-transform: capitalize;">${product.category}</td>
                    <td>₱${product.price.toFixed(2)}</td>
                    <td>${product.stock} pcs</td>
                    <td>
                        <button class="action-btn" onclick="toggleAvailability(${product.id})">
                            ${product.isAvailable ? 'Disable' : 'Enable'}
                        </button>
                        <button class="action-btn" onclick="editPrice(${product.id})">Edit Price</button>
                        <button class="delete-btn" onclick="deleteProduct(${product.id})">Delete</button>
                    </td>
                </tr>
            `).join('');

            // Render Orders Table
            if (orders.length === 0) {
                ordersTableBody.innerHTML = '<tr><td colspan="4" style="text-align:center;">No orders received yet.</td></tr>';
            } else {
                ordersTableBody.innerHTML = orders.map(order => `
                    <tr>
                        <td>
                            <strong>${order.id}</strong><br>
                            <small style="color:#666;">${order.custName || 'Walk-In'} (${order.type || 'In-Shop'})</small>
                        </td>
                        <td>${order.items}</td>
                        <td>
                            ₱${order.total.toFixed(2)}<br>
                            <small style="color:#888;">${order.payment || 'Cash'}</small>
                        </td>
                        <td>
                            <select class="status-select status-${order.status}" onchange="updateOrderStatus('${order.id}', this.value)">
                                <option value="Received" ${order.status === 'Received' ? 'selected' : ''}>Received</option>
                                <option value="Preparing" ${order.status === 'Preparing' ? 'selected' : ''}>Preparing</option>
                                <option value="Ready" ${order.status === 'Ready' ? 'selected' : ''}>Ready for Pickup</option>
                                <option value="Completed" ${order.status === 'Completed' ? 'selected' : ''}>Completed</option>
                                <option value="Cancelled" ${order.status === 'Cancelled' ? 'selected' : ''}>Cancelled</option>
                            </select>
                        </td>
                    </tr>
                `).join('');
            }
        }

        // Order Status Change Handler
        function updateOrderStatus(orderId, newStatus) {
            const order = orders.find(o => o.id === orderId);
            if (order) {
                order.status = newStatus;
                saveState();
                renderStaffTables();
            }
        }

        // Toggle Product Availability
        function toggleAvailability(productId) {
            const product = products.find(p => p.id === productId);
            if (product) {
                product.isAvailable = !product.isAvailable;
                saveState();
                renderProducts(products);
                renderStaffTables();
            }
        }

        // Edit Product Price
        function editPrice(productId) {
            const product = products.find(p => p.id === productId);
            if (product) {
                const newPrice = prompt(`Enter new price for ${product.name}:`, product.price);
                if (newPrice !== null && !isNaN(parseFloat(newPrice)) && parseFloat(newPrice) > 0) {
                    product.price = parseFloat(newPrice);
                    saveState();
                    renderProducts(products);
                    renderStaffTables();
                }
            }
        }

        // Add New Product Form Handler (with Input Validation)
        addProductForm.addEventListener('submit', (e) => {
            e.preventDefault();

            const priceVal = parseFloat(document.getElementById('prodPrice').value);
            const stockVal = parseInt(document.getElementById('prodStock').value);

            if (priceVal <= 0 || stockVal < 0) {
                alert('Please enter valid positive values for price and stock!');
                return;
            }

            const newProduct = {
                id: Date.now(),
                name: document.getElementById('prodName').value.trim(),
                category: document.getElementById('prodCategory').value,
                price: priceVal,
                stock: stockVal,
                isAvailable: true,
                desc: document.getElementById('prodDesc').value.trim() || 'Freshly baked goodness.',
                image: document.getElementById('prodImage').value.trim()
            };

            products.push(newProduct);
            saveState();

            renderProducts(products);
            renderStaffTables();

            addProductForm.reset();
            document.getElementById('prodStock').value = 20;
            alert('New product added to menu and inventory!');
        });

        // Delete Product Handler
        function deleteProduct(productId) {
            if (confirm('Are you sure you want to delete this product?')) {
                products = products.filter(p => p.id !== productId);
                saveState();
                renderProducts(products);
                renderStaffTables();
            }
        }

        // Drawer Controls
        function openCartDrawer() {
            cartDrawer.classList.add('open');
            overlay.classList.add('active');
        }

        function closeCartDrawer() {
            cartDrawer.classList.remove('open');
            overlay.classList.remove('active');
        }

        function setupEventListeners() {
            cartBtn.addEventListener('click', openCartDrawer);
            closeCart.addEventListener('click', closeCartDrawer);
            overlay.addEventListener('click', () => {
                closeCartDrawer();
                closeModal('checkoutModal');
                closeModal('receiptModal');
            });
        }

        // Run on page load
        init();
    </script>
</body>
</html>
