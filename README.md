<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CORTEZ - المافيا</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            background: #0a0a0a;
            color: #fff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
        }

        /* ===== LANDING PAGE ===== */
        .landing-page {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a0a1a 50%, #0a0a0a 100%);
            position: relative;
            overflow: hidden;
        }
        .landing-page::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(233,30,99,0.1) 0%, transparent 70%);
            animation: pulse 4s ease-in-out infinite;
        }
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.5; }
            50% { transform: scale(1.1); opacity: 0.8; }
        }
        .landing-content {
            position: relative;
            z-index: 1;
            text-align: center;
            padding: 40px;
        }
        .landing-logo {
            width: 150px;
            height: 150px;
            border-radius: 20px;
            overflow: hidden;
            margin: 0 auto 30px;
            border: 3px solid #e91e63;
            box-shadow: 0 0 40px rgba(233,30,99,0.5), 0 0 80px rgba(156,39,176,0.3);
            animation: float 3s ease-in-out infinite;
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        .landing-logo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .landing-title {
            font-size: 56px;
            font-weight: 900;
            background: linear-gradient(135deg, #e91e63, #9c27b0, #e91e63);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 8px;
            margin-bottom: 10px;
            text-shadow: 0 0 30px rgba(233,30,99,0.3);
        }
        .landing-subtitle {
            color: #888;
            font-size: 18px;
            letter-spacing: 10px;
            margin-bottom: 50px;
            text-transform: uppercase;
        }
        .landing-btn {
            background: linear-gradient(135deg, #e91e63, #9c27b0);
            color: #fff;
            border: none;
            padding: 20px 80px;
            font-size: 24px;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            letter-spacing: 3px;
            transition: all 0.3s;
            box-shadow: 0 10px 40px rgba(233,30,99,0.4);
            position: relative;
            overflow: hidden;
        }
        .landing-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }
        .landing-btn:hover::before {
            left: 100%;
        }
        .landing-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 60px rgba(233,30,99,0.6);
        }
        .landing-footer {
            position: absolute;
            bottom: 30px;
            color: #444;
            font-size: 12px;
            letter-spacing: 3px;
        }

        /* ===== SHOP PAGE (Hidden by default) ===== */
        .shop-page {
            display: none;
        }
        .shop-page.active {
            display: block;
        }
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }
        .header {
            text-align: center;
            padding: 30px 0;
            border-bottom: 2px solid #e91e63;
            margin-bottom: 30px;
        }
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 10px;
        }
        .logo-icon {
            width: 60px;
            height: 60px;
            border-radius: 12px;
            overflow: hidden;
            border: 2px solid #e91e63;
        }
        .logo-icon img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .logo-text {
            font-size: 42px;
            font-weight: 900;
            background: linear-gradient(135deg, #e91e63, #9c27b0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 3px;
        }
        .subtitle {
            color: #888;
            font-size: 14px;
            letter-spacing: 5px;
        }
        .back-btn {
            background: #333;
            color: #fff;
            border: none;
            padding: 10px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            margin-bottom: 20px;
            transition: all 0.2s;
        }
        .back-btn:hover {
            background: #e91e63;
        }
        .category {
            margin-bottom: 25px;
            background: #111;
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid #222;
        }
        .category-header {
            background: linear-gradient(135deg, #e91e63, #9c27b0);
            padding: 15px 20px;
            font-size: 18px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .category-header::before { content: "▸"; }
        .items-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 10px;
            padding: 15px;
        }
        .item {
            background: #1a1a1a;
            border: 1px solid #333;
            border-radius: 8px;
            padding: 12px 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s;
        }
        .item:hover {
            border-color: #e91e63;
            background: #1f1f1f;
        }
        .item-info { flex: 1; }
        .item-name {
            font-weight: 600;
            font-size: 14px;
            margin-bottom: 3px;
        }
        .item-price {
            color: #e91e63;
            font-size: 13px;
            font-weight: bold;
        }
        .item-controls {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .qty-btn {
            width: 28px;
            height: 28px;
            border: none;
            background: #333;
            color: #fff;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s;
        }
        .qty-btn:hover { background: #e91e63; }
        .qty-input {
            width: 45px;
            text-align: center;
            background: #0a0a0a;
            border: 1px solid #444;
            color: #fff;
            padding: 5px;
            border-radius: 6px;
            font-size: 14px;
        }
        .add-btn {
            background: linear-gradient(135deg, #e91e63, #9c27b0);
            border: none;
            color: #fff;
            padding: 6px 15px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 12px;
            transition: all 0.2s;
        }
        .add-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(233, 30, 99, 0.4);
        }
        .cart-section {
            background: #111;
            border: 2px solid #e91e63;
            border-radius: 12px;
            padding: 25px;
            margin-top: 30px;
        }
        .cart-title {
            font-size: 24px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #e91e63;
        }
        .cart-items { margin-bottom: 20px; }
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px;
            background: #1a1a1a;
            border-radius: 8px;
            margin-bottom: 8px;
            border-right: 3px solid #e91e63;
        }
        .cart-item-info { flex: 1; }
        .cart-item-name { font-weight: 600; }
        .cart-item-qty {
            color: #888;
            font-size: 13px;
        }
        .cart-item-total {
            color: #e91e63;
            font-weight: bold;
            font-size: 16px;
        }
        .cart-item-remove {
            background: #ff4444;
            border: none;
            color: #fff;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            cursor: pointer;
            margin-right: 10px;
            font-size: 12px;
        }
        .cart-empty {
            text-align: center;
            color: #666;
            padding: 30px;
            font-style: italic;
        }
        .total-section {
            border-top: 2px solid #333;
            padding-top: 20px;
            margin-top: 20px;
        }
        .total-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            font-size: 16px;
        }
        .total-row.final {
            font-size: 28px;
            font-weight: 900;
            color: #e91e63;
            border-top: 2px solid #e91e63;
            padding-top: 15px;
            margin-top: 15px;
        }
        .buttons {
            display: flex;
            gap: 15px;
            margin-top: 25px;
            flex-wrap: wrap;
        }
        .btn {
            flex: 1;
            min-width: 150px;
            padding: 15px 25px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        .btn-print {
            background: linear-gradient(135deg, #e91e63, #9c27b0);
            color: #fff;
        }
        .btn-print:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(233, 30, 99, 0.4);
        }
        .btn-clear {
            background: #333;
            color: #fff;
        }
        .btn-clear:hover { background: #ff4444; }
        @media print {
            body {
                background: #fff;
                color: #000;
            }
            .landing-page, .back-btn { display: none !important; }
            .category, .items-grid, .buttons, .qty-btn, .add-btn, .cart-item-remove {
                display: none !important;
            }
            .cart-section {
                border: 2px solid #000;
                background: #fff;
                color: #000;
            }
            .cart-item {
                background: #f5f5f5;
                border-right: 3px solid #000;
            }
            .total-row.final {
                color: #000;
                border-top: 2px solid #000;
            }
            .header { border-bottom: 2px solid #000; }
            .logo-text {
                -webkit-text-fill-color: #000;
                background: none;
            }
            .cart-title { color: #000; }
            .cart-item-total { color: #000; }
            .logo-icon { display: none; }
        }
        @media (max-width: 600px) {
            .landing-title { font-size: 36px; }
            .landing-logo { width: 120px; height: 120px; }
            .landing-btn { padding: 15px 50px; font-size: 20px; }
            .items-grid { grid-template-columns: 1fr; }
            .logo-text { font-size: 28px; }
            .btn { width: 100%; }
        }
        .receipt-info {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        .info-field {
            background: #1a1a1a;
            border: 1px solid #333;
            border-radius: 8px;
            padding: 12px;
        }
        .info-field label {
            display: block;
            color: #888;
            font-size: 12px;
            margin-bottom: 5px;
        }
        .info-field input {
            width: 100%;
            background: transparent;
            border: none;
            color: #fff;
            font-size: 16px;
            font-weight: 600;
            outline: none;
        }
        @media print {
            .info-field {
                background: #f5f5f5;
                border: 1px solid #ccc;
            }
            .info-field input { color: #000; }
        }
    </style>
<base target="_blank">
</head>
<body>
    <!-- ===== LANDING PAGE ===== -->
    <div class="landing-page" id="landingPage">
        <div class="landing-content">
            <div class="landing-logo">
                <img src="https://i.postimg.cc/6ps2Jz9G/2b24b75f-8ceb-4b83-96a0-61eae328458b.jpg" alt="CORTEZ MAFIA">
            </div>
            <div class="landing-title">CORTEZ</div>
            <div class="landing-subtitle">MAFIA RP</div>
            <button class="landing-btn" onclick="showShop()">عرض</button>
        </div>
        <div class="landing-footer">© 2026 CORTEZ MAFIA</div>
    </div>

    <!-- ===== SHOP PAGE ===== -->
    <div class="shop-page" id="shopPage">
        <div class="container">
            <button class="back-btn" onclick="showLanding()">← رجوع</button>
            <div class="header">
                <div class="logo">
                    <div class="logo-icon">
                        <img src="https://i.postimg.cc/6ps2Jz9G/2b24b75f-8ceb-4b83-96a0-61eae328458b.jpg" alt="CORTEZ">
                    </div>
                    <div class="logo-text">CORTEZ</div>
                </div>
                <div class="subtitle">MAFIA RP - فاتورة الطلبية</div>
            </div>
            <div class="receipt-info">
                <div class="info-field">
                    <label>اسم العميل / Client Name</label>
                    <input type="text" id="clientName" placeholder="اكتب اسمك...">
                </div>
                <div class="info-field">
                    <label>التاريخ / Date</label>
                    <input type="text" id="dateField" readonly>
                </div>
            </div>
            <div class="category">
                <div class="category-header">🔫 الأسلحة / WEAPONS</div>
                <div class="items-grid" id="weapons"></div>
            </div>
            <div class="category">
                <div class="category-header">💊 المخدرات / DRUGS</div>
                <div class="items-grid" id="drugs"></div>
            </div>
            <div class="category">
                <div class="category-header">🛠️ المعدات / TOOLS</div>
                <div class="items-grid" id="tools"></div>
            </div>
            <div class="category">
                <div class="category-header">💎 المجوهرات / JEWELRY</div>
                <div class="items-grid" id="jewelry"></div>
            </div>
            <div class="category">
                <div class="category-header">⚗️ المختبر / LAB</div>
                <div class="items-grid" id="lab"></div>
            </div>
            <div class="cart-section">
                <div class="cart-title">🧾 الفاتورة / INVOICE</div>
                <div id="cartItems" class="cart-items">
                    <div class="cart-empty">السلة فارغة - اختر الأصناف من الأعلى</div>
                </div>
                <div class="total-section">
                    <div class="total-row final">
                        <span>المجموع الكلي / TOTAL:</span>
                        <span id="total">$0</span>
                    </div>
                </div>
                <div class="buttons">
                    <button class="btn btn-print" onclick="printInvoice()">🖨️ طباعة الفاتورة</button>
                    <button class="btn btn-clear" onclick="clearCart()">🗑️ مسح الكل</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Page switching
        function showShop() {
            document.getElementById('landingPage').style.display = 'none';
            document.getElementById('shopPage').classList.add('active');
        }
        function showLanding() {
            document.getElementById('shopPage').classList.remove('active');
            document.getElementById('landingPage').style.display = 'flex';
        }

        const products = {
            weapons: [
                { name: "COMBAT PISTOL", price: 109000 },
                { name: "PISTOL MK II", price: 100000 },
                { name: "MINI SMG", price: 105000 },
                { name: "MICRO SMG", price: 115000 },
                { name: "COMPACT PDW", price: 135000 },
                { name: "MACHINE PISTOL (GLOCK C-18)", price: 100000 },
                { name: "SAWED OFF SHOTGUN", price: 110000 },
                { name: "PISTOL AMMO", price: 6900 },
                { name: "SMG AMMO", price: 4025 },
                { name: "RIFLE AMMO", price: 5750 },
                { name: "SHOTGUN AMMO", price: 4025 },
                { name: "ARMOR", price: 5750 }
            ],
            drugs: [
                { name: "LYKA BOX (910-990 piece)", price: 650000 },
                { name: "HEROIN (1000 piece)", price: 650000 },
                { name: "COKE (1000 piece)", price: 500000 },
                { name: "MARIJUANA (1000 piece)", price: 260000 }
            ],
            tools: [
                { name: "BAG", price: 5750 },
                { name: "ELECTRIC CUTTER", price: 3450 },
                { name: "X CIRCUIT TESTER", price: 3450 },
                { name: "MXC KEY", price: 3450 },
                { name: "DEVICE", price: 3450 },
                { name: "FINGERPRINT BAG", price: 5175 },
                { name: "FINGERPRINT TAPE", price: 5175 },
                { name: "THERMITE", price: 5750 },
                { name: "PLIERS", price: 3450 },
                { name: "PICTURES", price: 7500 },
                { name: "LAPTOP NEW", price: 5000 },
                { name: "LAPTOP", price: 5750 },
                { name: "SMOKE GRENADE", price: 3500 },
                { name: "DECRYPTO", price: 4000 },
                { name: "HACKCARD", price: 4500 },
                { name: "PHONE", price: 4500 },
                { name: "C4", price: 4025 },
                { name: "DRILL", price: 7000 },
                { name: "HUMAN LABS KEYCARD", price: 46000 },
                { name: "PACIFIC KEY", price: 4025 },
                { name: "PACIFIC CARD", price: 7000 },
                { name: "PACIFIC CRACK DEVICE", price: 34500 },
                { name: "FLEECA CRACKED DEVICE", price: 13800 },
                { name: "BLAIN COUNTY CRACKED DEVICE", price: 46000 },
                { name: "MATÉRIEL FLEECA", price: 38000 },
                { name: "MATÉRIEL PALITO", price: 52000 },
                { name: "MATÉRIEL BANK CENTRALE", price: 350000 }
            ],
            jewelry: [
                { name: "MARKED GOLD BAR", price: 5000 },
                { name: "MARKED SILVER BAR", price: 4500 },
                { name: "GOLD BAR", price: 8000 },
                { name: "SILVER BAR", price: 5500 },
                { name: " khwatm wsnasl", price: 750 },
                { name: "X PANTHER GEM", price: 15000 },
                { name: "GIANT GEM", price: 15000 },
                { name: "GEM NECKLACE", price: 15000 },
                { name: "GIANT GEM GREEN", price: 15000 },
                { name: "SAPPHIRE NECKLACE", price: 15000 },
                { name: "EMERALD NECKLACE", price: 15000 },
                { name: "BOX OF JEWELRY", price: 3000 }
            ],
            lab: [
                { name: "LABO CHEMICAL", price: 350000 }
            ]
        };

        let cart = [];

        function formatPrice(price) {
            return "$" + price.toLocaleString();
        }

        function renderItems() {
            for (const [category, items] of Object.entries(products)) {
                const container = document.getElementById(category);
                items.forEach((item, index) => {
                    const div = document.createElement('div');
                    div.className = 'item';
                    div.innerHTML = `
                        <div class="item-info">
                            <div class="item-name">${item.name}</div>
                            <div class="item-price">${formatPrice(item.price)}</div>
                        </div>
                        <div class="item-controls">
                            <button class="qty-btn" onclick="changeQty('${category}', ${index}, -1)">-</button>
                            <input type="number" class="qty-input" id="qty-${category}-${index}" value="1" min="1">
                            <button class="qty-btn" onclick="changeQty('${category}', ${index}, 1)">+</button>
                            <button class="add-btn" onclick="addToCart('${category}', ${index})">إضافة</button>
                        </div>
                    `;
                    container.appendChild(div);
                });
            }
        }

        function changeQty(category, index, delta) {
            const input = document.getElementById(`qty-${category}-${index}`);
            let val = parseInt(input.value) + delta;
            if (val < 1) val = 1;
            input.value = val;
        }

        function addToCart(category, index) {
            const item = products[category][index];
            const qty = parseInt(document.getElementById(`qty-${category}-${index}`).value);
            const existing = cart.find(c => c.name === item.name);
            if (existing) {
                existing.qty += qty;
            } else {
                cart.push({ ...item, qty });
            }
            renderCart();
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            renderCart();
        }

        function renderCart() {
            const container = document.getElementById('cartItems');
            if (cart.length === 0) {
                container.innerHTML = '<div class="cart-empty">السلة فارغة - اختر الأصناف من الأعلى</div>';
                updateTotal();
                return;
            }
            container.innerHTML = cart.map((item, i) => `
                <div class="cart-item">
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-qty">${item.qty} × ${formatPrice(item.price)}</div>
                    </div>
                    <div style="display:flex;align-items:center;">
                        <div class="cart-item-total">${formatPrice(item.price * item.qty)}</div>
                        <button class="cart-item-remove" onclick="removeFromCart(${i})">✕</button>
                    </div>
                </div>
            `).join('');
            updateTotal();
        }

        function updateTotal() {
            const total = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);
            document.getElementById('total').textContent = formatPrice(total);
        }

        function clearCart() {
            cart = [];
            renderCart();
        }

        function printInvoice() {
            if (cart.length === 0) {
                alert('السلة فارغة! أضف أصناف أولاً');
                return;
            }
            window.print();
        }

        document.getElementById('dateField').value = new Date().toLocaleDateString('ar-SA');
        renderItems();
    </script>
</body>
</html>
