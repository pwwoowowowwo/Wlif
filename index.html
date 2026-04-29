<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>شاهي وليف - نظام السلة المؤكد</title>
    <style>
        :root { 
            --primary: #4f46e5; --dark: #111827; --bg: #e5e7eb;
            --shadow-out: 6px 6px 12px #bebebe, -6px -6px 12px #ffffff;
            --shadow-in: inset 5px 5px 10px #bebebe, inset -5px -5px 10px #ffffff;
        }
        
        body { margin: 0; font-family: 'Segoe UI', sans-serif; background: var(--bg); height: 100vh; display: flex; flex-direction: column; overflow: hidden; }

        /* الهيدر */
        .topbar { display: flex; justify-content: space-between; align-items: center; background: var(--dark); color: white; padding: 0 20px; height: 50px; flex-shrink: 0; }

        .main-content { display: flex; flex: 1; overflow: hidden; padding: 15px; gap: 15px; }

        /* قسم الأصناف (اليمين) */
        .pos-container { flex: 2; display: flex; flex-direction: column; background: var(--bg); border-radius: 20px; box-shadow: var(--shadow-out); padding: 15px; overflow: hidden; }
        .products-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(110px, 1fr)); gap: 12px; overflow-y: auto; padding: 10px; flex: 1; }
        .product { background: var(--bg); padding: 20px 10px; border-radius: 18px; text-align: center; cursor: pointer; box-shadow: var(--shadow-out); transition: 0.1s; }
        .product:active { box-shadow: var(--shadow-in); transform: scale(0.96); }

        /* قسم السلة (اليسار) - هنا التأكيد */
        .cart-section { 
            width: 350px; background: var(--bg); border-radius: 20px; 
            display: flex; flex-direction: column; box-shadow: var(--shadow-out); padding: 20px; 
        }
        
        .cart-header { font-weight: bold; margin-bottom: 15px; color: var(--dark); border-bottom: 2px solid var(--primary); padding-bottom: 5px; }

        /* حاوية قائمة الطلبات */
        .cart-items { 
            flex: 1; overflow-y: auto; margin-bottom: 15px; border-radius: 15px; 
            box-shadow: var(--shadow-in); padding: 10px; background: rgba(255,255,255,0.2);
        }

        /* شكل الطلب الواحد داخل السلة */
        .cart-row { 
            background: white; padding: 12px; border-radius: 12px; margin-bottom: 8px; 
            display: flex; justify-content: space-between; align-items: center; 
            box-shadow: 2px 2px 5px rgba(0,0,0,0.05); animation: slideIn 0.2s ease;
        }

        @keyframes slideIn { from { opacity: 0; transform: translateX(-10px); } to { opacity: 1; transform: translateX(0); } }

        .btn-cancel-item { 
            background: #fee2e2; color: #ef4444; border: none; width: 28px; height: 28px; 
            border-radius: 50%; cursor: pointer; font-weight: bold; transition: 0.2s;
        }
        .btn-cancel-item:active { transform: scale(0.8); background: #fca5a5; }

        .summary-box { background: var(--bg); padding: 15px; border-radius: 18px; text-align: center; box-shadow: var(--shadow-in); margin-bottom: 15px; }
        .btn-pay { padding: 14px; border: none; border-radius: 15px; color: white; font-weight: bold; cursor: pointer; box-shadow: var(--shadow-out); transition: 0.1s; }
        .btn-pay:active { box-shadow: var(--shadow-in); transform: scale(0.97); }
    </style>
</head>
<body>

    <div class="topbar">
        <h3 style="margin:0;">🍃 شاهي وليف</h3>
        <span>نظام الكاشير الذكي</span>
    </div>

    <div class="main-content">
        <div class="pos-container">
            <div class="products-grid" id="products-list">
                </div>
        </div>

        <div class="cart-section">
            <div class="cart-header">🛒 قائمة الطلبات فالسلة</div>
            
            <div id="cart-display" class="cart-items">
                </div>
            
            <div class="summary-box">
                <small>الإجمالي (شامل الضريبة)</small>
                <div id="total-price" style="font-size: 1.8rem; font-weight: 900; color: var(--dark);">0.00</div>
            </div>

            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
                <button class="btn-pay" style="background:var(--success)" onclick="processPay('كاش')">💵 كاش</button>
                <button class="btn-pay" style="background:var(--primary)" onclick="processPay('شبكة')">💳 شبكة</button>
                <button class="btn-pay" style="background:var(--danger); grid-column: span 2;" onclick="clearAll()">✖ كنسلة الطلب بالكامل</button>
            </div>
        </div>
    </div>

<script>
    // بيانات تجريبية
    let products = [
        { name: "شاي كرك", price: 3 },
        { name: "شاي نعناع", price: 2 },
        { name: "فطيرة جبن", price: 5 },
        { name: "جاكارو", price: 10 }
    ];

    let currentCart = [];

    // 1. عرض الأصناف في اليمين
    function renderProducts() {
        const list = document.getElementById('products-list');
        list.innerHTML = products.map((p, index) => `
            <div class="product" onclick="addToCart(${index})">
                <strong>${p.name}</strong><br>
                <b>${p.price} ر.س</b>
            </div>
        `).join('');
    }

    // 2. إضافة صنف للسلة (تأكيد الظهور)
    function addToCart(index) {
        const item = { ...products[index], cartId: Date.now() };
        currentCart.push(item);
        updateCartUI();
    }

    // 3. حذف صنف واحد من السلة (الكنسلة الجزئية)
    function removeItem(cartId) {
        currentCart = currentCart.filter(item => item.cartId !== cartId);
        updateCartUI();
    }

    // 4. تحديث شكل السلة (هذا الجزء المسؤول عن ظهور الطلبات)
    function updateCartUI() {
        const display = document.getElementById('cart-display');
        const totalDisplay = document.getElementById('total-price');
        
        if (currentCart.length === 0) {
            display.innerHTML = '<p style="text-align:center; color:#999; margin-top:20px;">السلة فارغة..</p>';
        } else {
            display.innerHTML = currentCart.map(item => `
                <div class="cart-row">
                    <span>${item.name}</span>
                    <div style="display:flex; align-items:center; gap:10px;">
                        <b>${item.price} ر.س</b>
                        <button class="btn-cancel-item" onclick="removeItem(${item.cartId})">✕</button>
                    </div>
                </div>
            `).join('');
        }

        // حساب الإجمالي
        let subtotal = currentCart.reduce((sum, item) => sum + item.price, 0);
        let totalWithTax = subtotal * 1.15;
        totalDisplay.innerText = totalWithTax.toFixed(2);
    }

    function clearAll() {
        if(currentCart.length > 0 && confirm("هل تريد حذف كل الطلبات؟")) {
            currentCart = [];
            updateCartUI();
        }
    }

    function processPay(type) {
        if(currentCart.length > 0) {
            alert("تم تنفيذ طلبك بقيمة " + document.getElementById('total-price').innerText + " ر.س عبر " + type);
            currentCart = [];
            updateCartUI();
        }
    }

    window.onload = renderProducts;
</script>
</body>
</html>
