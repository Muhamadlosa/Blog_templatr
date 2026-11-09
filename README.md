<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Foodie Express Ordering System</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background: #fff7ed;
    color: #333;
}

header {
    background: #e85d04;
    color: white;
    padding: 22px;
    text-align: center;
}

header h1 {
    margin-bottom: 10px;
}

nav {
    background: #333;
    display: flex;
    justify-content: center;
    gap: 15px;
    padding: 15px;
}

nav button {
    background: transparent;
    color: white;
    border: 1px solid white;
    padding: 10px 20px;
    border-radius: 6px;
    cursor: pointer;
}

nav button.active,
nav button:hover {
    background: #e85d04;
    border-color: #e85d04;
}

.container {
    width: 90%;
    max-width: 1100px;
    margin: 30px auto;
}

.page {
    display: none;
}

.page.active {
    display: block;
}

h2 {
    color: #d9480f;
    margin-bottom: 20px;
}

.menu {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
    gap: 20px;
}

.item {
    background: white;
    padding: 20px;
    text-align: center;
    border-radius: 12px;
    box-shadow: 0 3px 10px #0001;
}

.food-image {
    font-size: 65px;
    margin-bottom: 12px;
}

.item h3 {
    margin-bottom: 8px;
}

.description {
    color: #777;
    font-size: 13px;
}

.price {
    color: #e85d04;
    font-size: 20px;
    font-weight: bold;
    margin: 12px;
}

button {
    cursor: pointer;
}

.add-btn,
.checkout-btn,
.back-btn {
    background: #e85d04;
    color: white;
    border: none;
    padding: 11px 18px;
    border-radius: 6px;
}

.add-btn:hover,
.checkout-btn:hover,
.back-btn:hover {
    background: #c2410c;
}

.cart-box {
    background: white;
    padding: 22px;
    border-radius: 12px;
    box-shadow: 0 3px 10px #0001;
}

.cart-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
    padding: 15px 0;
    border-bottom: 1px solid #ddd;
}

.quantity {
    display: flex;
    align-items: center;
    gap: 10px;
}

.quantity button,
.remove-btn {
    background: #333;
    color: white;
    border: none;
    padding: 7px 11px;
    border-radius: 5px;
}

.remove-btn {
    background: #dc2626;
}

.total {
    text-align: right;
    color: #e85d04;
    font-size: 24px;
    font-weight: bold;
    margin: 25px 0;
}

.customer {
    margin-top: 25px;
}

input, select {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border: 1px solid #ccc;
    border-radius: 6px;
}

.checkout-btn {
    width: 100%;
    padding: 14px;
    font-size: 16px;
    margin-top: 12px;
}

.back-btn {
    margin-top: 15px;
}

.empty {
    color: #777;
    padding: 20px 0;
}

footer {
    background: #333;
    color: white;
    text-align: center;
    padding: 18px;
    margin-top: 40px;
}

@media(max-width: 600px) {
    .cart-row {
        align-items: flex-start;
        flex-direction: column;
    }
}
</style>
</head>

<body>

<header>
    <h1>🍔 FOODIE EXPRESS</h1>
    <p>Delicious Food at Affordable Prices!</p>
</header>

<nav>
    <button id="menuTab" class="active" onclick="showPage('menuPage')">
        🍔 Food Menu
    </button>

    <button id="cartTab" onclick="showPage('cartPage')">
        🛒 Shopping Cart (<span id="cartCount">0</span>)
    </button>
</nav>

<div class="container">

    <!-- PAGE 1: FOOD MENU -->
    <section id="menuPage" class="page active">

        <h2>Our Food Menu</h2>

        <div class="menu" id="menu"></div>

        <button class="back-btn" onclick="showPage('cartPage')">
            Go to Shopping Cart →
        </button>

    </section>


    <!-- PAGE 2: SHOPPING CART -->
    <section id="cartPage" class="page">

        <h2>🛒 Your Shopping Cart</h2>

        <div class="cart-box">

            <div id="cartItems">
                <p class="empty">Your shopping cart is empty.</p>
            </div>

            <div class="total">
                Total: ₱<span id="total">0.00</span>
            </div>

            <button class="back-btn" onclick="showPage('menuPage')">
                ← Back to Food Menu
            </button>

        </div>

        <div class="cart-box customer">

            <h2>Customer Information</h2>

            <input type="text" id="customerName"
                   placeholder="Enter your full name">

            <input type="text" id="address"
                   placeholder="Enter your address">

            <input type="tel" id="phone"
                   placeholder="Enter your phone number">

            <select id="payment">
                <option value="">Select Payment Method</option>
                <option value="Cash on Delivery">Cash on Delivery</option>
                <option value="GCash (Demo Only)">GCash (Demo Only)</option>
            </select>

            <button class="checkout-btn" onclick="checkout()">
 
