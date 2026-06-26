<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Euryops Store | ايروبس ستور</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary-color: #D4AF37;
            --secondary-color: #111111;
            --accent-color: #e91e63;
            --bg-light: #f4f6f9;
            --text-color: #333;
            --white: #ffffff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Cairo', sans-serif; }
        body { background-color: var(--bg-light); color: var(--text-color); padding-bottom: 40px; }

        .top-bar {
            background-color: #1b1b1b; color: #ccc; font-size: 13px;
            padding: 8px 5%; display: flex; justify-content: space-between; align-items: center;
        }
        .currency-select {
            background: transparent; color: var(--white); border: 1px solid #444;
            padding: 3px 8px; border-radius: 4px; cursor: pointer;
        }

        header {
            background-color: var(--secondary-color); color: var(--white);
            padding: 15px 5%; position: sticky; top: 0; z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }
        .nav-container { display: flex; justify-content: space-between; align-items: center; }
        .logo { font-size: 24px; font-weight: 700; color: var(--primary-color); }
        .nav-icons { display: flex; gap: 20px; font-size: 20px; align-items: center; }
        .nav-icons i { cursor: pointer; position: relative; transition: color 0.2s; }
        .nav-icons i:hover { color: var(--primary-color); }
        .badge {
            position: absolute; top: -10px; right: -10px; background-color: var(--accent-color);
            color: white; font-size: 11px; font-weight: bold; padding: 2px 6px; border-radius: 50%;
        }

        .hero-banner {
            position: relative; width: 100%; height: 260px; 
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1441986300917-64674bd600d8?q=80&w=1200') center/cover no-repeat;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            text-align: center; color: var(--white); padding: 20px;
        }
        .hero-banner h1 {
            font-size: 28px; font-weight: 700; color: var(--primary-color);
            margin-bottom: 8px; text-shadow: 2px 2px 4px rgba(0,0,0,0.6);
        }
        .hero-banner p { font-size: 14px; max-width: 600px; color: #eee; }

        .search-container { padding: 15px 5% 5px 5%; display: flex; justify-content: center; }
        .search-wrapper { position: relative; width: 100%; max-width: 500px; }
        .search-input {
            width: 100%; padding: 12px 45px 12px 15px; border-radius: 30px;
            border: 1px solid #ddd; font-size: 14px; box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            outline: none; transition: all 0.3s;
        }
        .search-input:focus { border-color: var(--primary-color); }
        .search-icon { position: absolute; top: 50%; right: 18px; transform: translateY(-50%); color: #888; font-size: 16px; }

        .categories-bar {
            display: flex; gap: 10px; padding: 12px 5%; overflow-x: auto;
            background: var(--white); border-bottom: 1px solid #e0e0e0;
            scrollbar-width: none; -webkit-overflow-scrolling: touch;
        }
        .categories-bar::-webkit-scrollbar { display: none; }
        .category-tab {
            padding: 8px 18px; background: #f0f2f5; border-radius: 25px;
            font-size: 13px; font-weight: 600; color: #555; cursor: pointer;
            white-space: nowrap; transition: all 0.3s ease;
        }
        .category-tab.active {
            background: var(--secondary-color); color: var(--primary-color);
            border: 1px solid var(--primary-color);
        }

        .products-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 20px; padding: 20px 5%; margin-bottom: 30px; }
        .product-card { background: var(--white); border-radius: 12px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.05); display: flex; flex-direction: column; justify-content: space-between; position: relative; }
        
        .wishlist-btn {
            position: absolute; top: 12px; left: 12px; z-index: 10;
            background: rgba(255, 255, 255, 0.95); border: none;
            width: 38px; height: 38px; border-radius: 50%; display: flex;
            align-items: center; justify-content: center; cursor: pointer;
            box-shadow: 0 3px 10px rgba(0,0,0,0.12);
        }
        .wishlist-btn i { color: #ccc; font-size: 20px; }
        .wishlist-btn.active i { color: #ff2a74; }

        .img-wrapper { width: 100%; height: 260px; overflow: hidden; background-color: #fff; cursor: pointer; }
        .product-img { width: 100%; height: 100%; object-fit: contain; }
        .product-info { padding: 15px; display: flex; flex-direction: column; gap: 8px; }
        .product-name { font-size: 14px; font-weight: 600; height: 40px; overflow: hidden; }
        .product-price { color: var(--accent-color); font-weight: 700; font-size: 16px; }
        .btn-add-cart { background-color: var(--secondary-color); color: var(--white); border: none; padding: 10px; border-radius: 6px; cursor: pointer; font-weight: 600; width: 100%; }

        .store-reviews-section { background: var(--white); padding: 30px 5%; margin: 20px 0; border-top: 1px solid #e0e0e0; }
        .section-title { font-size: 18px; font-weight: 700; margin-bottom: 20px; color: var(--secondary-color); border-right: 4px solid var(--primary-color); padding-right: 10px; }
        .store-reviews-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 15px; }
        .store-review-card { background: #f9fbfd; border: 1px solid #eef2f7; padding: 15px; border-radius: 10px; }
        .six-stars { color: #ffb300; font-size: 13px; margin-bottom: 5px; }

        footer { background-color: #111; color: #fff; padding: 40px 5% 20px 5%; text-align: center; font-size: 14px; border-top: 3px solid var(--primary-color); position: relative; }
        .footer-socials { display: flex; justify-content: center; gap: 15px; margin-bottom: 25px; }
        .social-btn { display: flex; align-items: center; gap: 8px; padding: 10px 18px; border-radius: 25px; color: #fff; text-decoration: none; font-weight: bold; font-size: 13px; }
        .btn-insta { background: linear-gradient(45deg, #f09433 0%, #e6683c 25%, #dc2743 50%, #cc2366 75%, #bc1888 100%); }
        .btn-wa-footer { background-color: #25D366; }
        .btn-cs { background-color: #0088cc; }

        .payment-section-title { font-size: 13px; color: #aaa; margin-bottom: 15px; font-weight: bold; }
        .payment-badges-container { display: flex; justify-content: center; gap: 10px; flex-wrap: wrap; margin-bottom: 25px; }
        .payment-badge { background: #222; border: 1px solid #333; border-radius: 6px; padding: 6px 12px; font-size: 11px; font-weight: 700; color: #ddd; display: flex; align-items: center; gap: 6px; }
        .payment-badge i { color: var(--primary-color); }

        .secret-admin-trigger { position: absolute; bottom: 15px; left: 15px; color: #222; font-size: 10px; cursor: pointer; transition: color 0.3s; opacity: 0.3; }
        .secret-admin-trigger:hover { color: var(--primary-color); opacity: 1; }

        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); z-index: 2000; justify-content: center; align-items: flex-end; }
        @media(min-width: 768px) { .modal { align-items: center; } }
        .modal-content { background: var(--white); border-radius: 20px 20px 0 0; width: 100%; max-width: 500px; max-height: 92vh; overflow-y: auto; position: relative; padding-bottom: 80px; }
        @media(min-width: 768px) { .modal-content { border-radius: 16px; } }
        .close-btn { font-size: 28px; cursor: pointer; color: #555; position: absolute; top: 15px; left: 20px; z-index: 2010; background: rgba(255,255,255,0.8); width: 36px; height: 36px; display: flex; align-items: center; justify-content: center; border-radius: 50%; }

        .slider-container { width: 100%; height: 380px; position: relative; overflow: hidden; background: #fff; }
        .slider-wrapper { display: flex; width: 100%; height: 100%; overflow-x: auto; scroll-snap-type: x mandatory; scroll-behavior: smooth; scrollbar-width: none; }
        .slider-wrapper::-webkit-scrollbar { display: none; }
        .slide { min-width: 100%; width: 100%; height: 100%; scroll-snap-align: start; display: flex; justify-content: center; align-items: center; }
        .slide img { width: 100%; height: 100%; object-fit: contain; }
        
        .slider-dots { position: absolute; bottom: 15px; left: 50%; transform: translateX(-50%); display: flex; gap: 6px; z-index: 10; }
        .dot { width: 8px; height: 8px; background: rgba(0,0,0,0.3); border-radius: 50%; }
        .dot.active { background: var(--accent-color); width: 18px; border-radius: 4px; }

        .details-wrapper { padding: 20px; }
        .details-title { font-size: 22px; font-weight: 700; color: #111; }
        .rating-box { display: flex; align-items: center; gap: 5px; margin-bottom: 12px; }
        .stars { color: #FFD700; }
        .details-price { font-size: 24px; color: var(--accent-color); font-weight: 700; margin-bottom: 15px; }
        .status-badge { background-color: #e8f5e9; color: #2e7d32; padding: 8px 12px; border-radius: 8px; font-size: 14px; display: flex; align-items: center; gap: 8px; font-weight: 600; border: 1px solid #c8e6c9; margin-bottom: 15px; }

        .color-group { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 20px; }
        .color-badge { padding: 6px 16px; border: 1px solid #ddd; border-radius: 20px; font-size: 13px; cursor: pointer; background: #fff; font-weight: 600; }
        .color-badge.active { background: var(--secondary-color); color: #fff; border-color: var(--secondary-color); }

        .sticky-actions { position: fixed; bottom: 0; left: 50%; transform: translateX(-50%); width: 100%; max-width: 500px; background: #fff; padding: 12px 20px; box-shadow: 0 -4px 10px rgba(0,0,0,0.08); display: flex; gap: 10px; z-index: 2050; border-top: 1px solid #eee; }
        .btn-action-buy { flex: 2; background-color: var(--accent-color); color: white; border: none; padding: 12px; border-radius: 8px; font-weight: bold; cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 8px; }
        .qty-controls { flex: 1; display: flex; align-items: center; background: #f5f5f5; border-radius: 8px; overflow: hidden; height: 45px; border: 1px solid #ddd; }
        .qty-btn { width: 35px; height: 100%; border: none; background: transparent; font-size: 18px; font-weight: bold; cursor: pointer; }
        .qty-val { flex: 1; text-align: center; font-weight: bold; }

        .cart-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); z-index: 2000; justify-content: flex-start; }
        .cart-content { background: var(--white); width: 100%; max-width: 400px; height: 100%; padding: 25px; display: flex; flex-direction: column; }
        .cart-items-list { flex: 1; overflow-y: auto; }
        .cart-item { display: flex; gap: 15px; align-items: center; margin-bottom: 15px; background: #fdfdfd; padding: 10px; border-radius: 8px; border: 1px solid #eee; }
        .cart-item-img { width: 60px; height: 60px; object-fit: cover; border-radius: 4px; }
        .cart-total-box { border-top: 2px dashed #ddd; padding-top: 15px; font-size: 18px; font-weight: 700; display: flex; justify-content: space-between; margin-bottom: 15px; }
        .btn-whatsapp-send { background-color: #25D366; color: white; border: none; padding: 12px; width: 100%; border-radius: 6px; font-weight: bold; cursor: pointer; text-align: center; text-decoration: none; }

        .form-group { margin-bottom: 10px; display: flex; flex-direction: column; gap: 3px; }
        .form-group label { font-weight: 600; font-size: 13px; color: #444; }
        .form-group input, .form-group select { padding: 8px; border: 1px solid #ddd; border-radius: 6px; }
        .images-panel { background: #f8f9fa; padding: 10px; border-radius: 8px; border: 1px solid #eee; margin-bottom: 10px; }
        .admin-prod-item { display: flex; justify-content: space-between; align-items: center; padding: 10px; background: #fdfdfd; margin-top: 6px; border-radius: 6px; font-size: 12px; border: 1px solid #ddd; }
        .admin-actions-btns { display: flex; gap: 5px; }
        .btn-edit { background: #0288d1; color: white; border: none; padding: 4px 10px; border-radius: 4px; cursor: pointer; }
        .btn-delete { background: #d32f2f; color: white; border: none; padding: 4px 10px; border-radius: 4px; cursor: pointer; }
        
        .loading-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(255,255,255,0.8); z-index: 9999; justify-content: center; align-items: center; font-weight: bold; font-size: 18px; color: var(--secondary-color); }
    </style>
</head>
<body>

    <div class="loading-overlay" id="loadingOverlay">⏳ جاري تحديث البيانات السحابية الحية...</div>

    <div class="top-bar">
        <div><i class="fas fa-truck"></i> توصيل مجاني داخل صنعاء ورمزي للمحافظات والسعودية</div>
        <div>
            <select class="currency-select" id="currencySelector" onchange="changeCurrency()">
                <option value="YER">ريال يمني (YER)</option>
                <option value="SAR">ريال سعودي (SAR)</option>
                <option value="USD">دولار أمريكي (USD)</option>
            </select>
        </div>
    </div>

    <header>
        <div class="nav-container">
            <div class="logo">Euryops Store</div>
            <div class="nav-icons">
                <i class="fas fa-heart" onclick="toggleWishlistModal()"><span class="badge" id="wishlistCount">0</span></i>
                <i class="fas fa-shopping-bag" onclick="toggleCartModal()"><span class="badge" id="cartCount">0</span></i>
            </div>
        </div>
    </header>

    <section class="hero-banner">
        <h1>مرحباً بكم في ايروبس ستور ✨</h1>
        <p>وجهتكم الأولى لأحدث صيحات الموضة، الفساتين الفاخرة، والحقائب الراقية بجودة استثنائية وتوصيل فوري.</p>
    </section>

    <div class="search-container">
        <div class="search-wrapper">
            <i class="fas fa-search search-icon"></i>
            <input type="text" class="search-input" id="storeSearchInput" placeholder="ابحثي عن فستان، حقيبة، عطر أو مكياج..." oninput="handleSearch()">
        </div>
    </div>

    <div class="categories-bar">
        <div class="category-tab active" onclick="filterCategory(this, 'الكل')">الكل</div>
        <div class="category-tab" onclick="filterCategory(this, 'فساتين')">👗 الفساتين</div>
        <div class="category-tab" onclick="filterCategory(this, 'حقائب')">👜 الحقائب</div>
        <div class="category-tab" onclick="filterCategory(this, 'مكياج')">💄 المكياج</div>
        <div class="category-tab" onclick="filterCategory(this, 'عناية')">✨ العناية بالبشرة</div>
        <div class="category-tab" onclick="filterCategory(this, 'عطور')">🌸 العطور</div>
        <div class="category-tab" onclick="filterCategory(this, 'عروض')">🔥 العروض</div>
        <div class="category-tab" onclick="filterCategory(this, 'أكثر مبيعاً')">⭐ الأكثر مبيعًا</div>
        <div class="category-tab" onclick="filterCategory(this, 'جديد')">🆕 وصل حديثًا</div>
    </div>

    <section class="products-grid" id="productsContainer"></section>

    <section class="store-reviews-section">
        <div class="section-title">✨ تجارب ورسائل زبوناتنا في اليمن والخليج</div>
        <div class="store-reviews-grid">
            <div class="store-review-card">
                <div class="six-stars">⭐⭐⭐⭐⭐⭐</div>
                <div style="font-weight:700; font-size:14px; margin-bottom:5px;">أم جود الحاشدي (صنعاء)</div>
                <p style="font-size:13px; color:#444; line-height:1.5;">"وقسماً بالله الفستان يجنننن خيرات! قماشته فخمة والخياطة نظيفة ونفس الصورة تماماً. وزد وصلوا لي المطلب بنفس اليوم لوسط صنعاء، الصدق متجر يبيض الوجه وسعره حالي قوي.. يستاهلوا 6 نجوم مش بس خمس!"</p>
            </div>
            <div class="store-review-card">
                <div class="six-stars">⭐⭐⭐⭐⭐⭐</div>
                <div style="font-weight:700; font-size:14px; margin-bottom:5px;">روان الهويدي (عدن)</div>
                <p style="font-size:13px; color:#444; line-height:1.5;">"وصلت الشنطة اليوم تجنن فدوة لقلبكم، التغليف يفتح النفس والذوق والتعامل معكم راقي جداً.. هذي ثاني مرة أطلب من ايروبس ستور ورب البيت إنكم أطلق وأضمن متجر تعاملت معه."</p>
            </div>
            <div class="store-review-card">
                <div class="six-stars">⭐⭐⭐⭐⭐⭐</div>
                <div style="font-weight:700; font-size:14px; margin-bottom:5px;">ندى العبسي (مغتربة بالرياض)</div>
                <p style="font-size:13px; color:#444; line-height:1.5;">"كنت خايفة من التوصيل للسعودية بس ما شاء الله وصل المطلب سريع وبحالة ممتازة والمكياج أصلي 100% وثابت.. شكراً للمتجر على الأمانة وحُسن التعامل."</p>
            </div>
        </div>
    </section>

    <footer>
        <div class="payment-section-title">🔒 وسائل الدفع والمحافظ الإلكترونية اليمنية المتاحة</div>
        <div class="payment-badges-container">
            <div class="payment-badge"><i class="fas fa-wallet"></i> محفظة جيب Jeeb</div>
            <div class="payment-badge"><i class="fas fa-money-bill-wave"></i> الدفع عند الاستلام</div>
            <div class="payment-badge"><i class="fas fa-wallet"></i> فلوسك MFloos</div>
            <div class="payment-badge"><i class="fas fa-mobile-alt"></i> جوالي Jawaly</div>
            <div class="payment-badge"><i class="fas fa-money-bill-wave"></i> كاش Cash</div>
            <div class="payment-badge"><i class="fas fa-credit-card"></i> محفظة حاسب</div>
            <div class="payment-badge"><i class="fas fa-paper-plane"></i> النجم للصرافة</div>
            <div class="payment-badge"><i class="fas fa-university"></i> الكريمي للتمويل</div>
        </div>

        <div class="payment-section-title">📱 تواصلوا معنا مباشرة</div>
        <div class="footer-socials">
            <a href="https://instagram.com/" target="_blank" class="social-btn btn-insta"><i class="fab fa-instagram"></i> إنستغرام المتجر</a>
            <a href="https://wa.me/967778004131" target="_blank" class="social-btn btn-wa-footer"><i class="fab fa-whatsapp"></i> واتساب الطلبات</a>
            <a href="https://wa.me/967778004131?text=استفسار+خدمة+العملاء" target="_blank" class="social-btn btn-cs"><i class="fas fa-headset"></i> خدمة العملاء</a>
        </div>

        <p style="color:#777; font-size:12px;">جميع الحقوق محفوظة © 2026 لدى يمن سوفت للبرمجيات</p>
        
        <div class="secret-admin-trigger" onclick="handleSecretAdminUnlock()">⚙️</div>
    </footer>

    <div class="modal" id="viewModal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeViewModal()">&times;</span>
            <div class="slider-container">
                <div class="slider-wrapper" id="sliderWrapper" onscroll="updateSliderDots()"></div>
                <div class="slider-dots" id="sliderDots"></div>
            </div>
            <div class="details-wrapper">
                <div id="productMainDetails"></div>
            </div>
            <div class="sticky-actions">
                <div class="qty-controls">
                    <button class="qty-btn" onclick="adjustModalQty(-1)">-</button>
                    <div class="qty-val" id="modalQtyVal">1</div>
                    <button class="qty-btn" onclick="adjustModalQty(1)">+</button>
                </div>
                <button class="btn-action-buy" id="modalAddBtn"><i class="fas fa-shopping-cart"></i> أضف إلى العربة</button>
            </div>
        </div>
    </div>

    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:20px;">
                <h2>سلة المشتريات 🛍️</h2>
                <span style="font-size:30px; cursor:pointer;" onclick="toggleCartModal()">&times;</span>
            </div>
            <div class="cart-items-list" id="cartItemsContainer"></div>
            <div class="cart-total-box">
                <span>الإجمالي:</span>
                <span id="cartTotalText">0 ر.ي</span>
            </div>
            <button class="btn-whatsapp-send" onclick="sendOrderToWhatsApp()">إرسال عبر الواتساب لتأكيد الشراء</button>
        </div>
    </div>

    <div class="cart-modal" id="wishlistModal">
        <div class="cart-content">
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:20px;">
                <h2>المنتجات المفضلة ❤️</h2>
                <span style="font-size:30px; cursor:pointer;" onclick="toggleWishlistModal()">&times;</span>
            </div>
            <div class="cart-items-list" id="wishlistItemsContainer"></div>
        </div>
    </div>

    <div class="modal" id="adminModal" style="align-items:center;">
        <div class="modal-content" style="border-radius:12px; padding:20px; max-width:550px;">
            <span class="close-btn" onclick="toggleAdminModal()">&times;</span>
            <h2 id="adminPanelTitle" style="margin-bottom:15px; font-size:17px; color:var(--secondary-color);">إضافة منتج جديد للـ Cloud 🛠️</h2>
            
            <input type="hidden" id="editProductId" value="">

            <div class="form-group">
                <label>اسم المنتج</label>
                <input type="text" id="prodName" placeholder="مثال: فستان سهرة مخمل فاخر">
            </div>
            <div class="form-group">
                <label>القسم</label>
                <select id="prodCategory">
                    <option value="فساتين">👗 الفساتين</option>
                    <option value="حقائب">👜 الحقائب</option>
                    <option value="مكياج">💄 المكياج</option>
                    <option value="عناية">✨ العناية بالبشرة</option>
                    <option value="عطور">🌸 العطور</option>
                    <option value="عروض">🔥 العروض</option>
                    <option value="أكثر مبيعاً">⭐ الأكثر مبيعًا</option>
                    <option value="جديد">🆕 وصل حديثًا</option>
                </select>
            </div>
            <div class="form-group">
                <label>السعر بالريال اليمني (YER)</label>
                <input type="number" id="prodPrice" placeholder="مثال: 45000">
            </div>
            <div class="form-group">
                <label>الألوان المتوفرة (افصل بفاصلة)</label>
                <input type="text" id="prodColors" placeholder="عنابي, أسود, رمادي">
            </div>
            <div class="images-panel">
                <p style="font-weight:bold; font-size:12px; margin-bottom:5px; color:var(--accent-color);">روابط صور المنتج السحابية:</p>
                <div style="display:grid; grid-template-columns: 1fr 1fr; gap:5px;">
                    <input type="text" id="img1" placeholder="رابط الصورة 1 (الأساسية)">
                    <input type="text" id="img2" placeholder="رابط الصورة 2">
                    <input type="text" id="img3" placeholder="رابط الصورة 3">
                    <input type="text" id="img4" placeholder="رابط الصورة 4">
                    <input type="text" id="img5" placeholder="رابط الصورة 5">
                </div>
            </div>
            
            <button style="background:var(--accent-color); color:white; width:100%; padding:12px; border-radius:6px; border:none; font-weight:bold; cursor:pointer;" onclick="saveProductData()">حفظ ونشر مباشر للسحاب ☁️</button>
            <button id="btnCancelEdit" style="background:#777; color:white; width:100%; padding:8px; border-radius:6px; border:none; font-weight:bold; cursor:pointer; margin-top:5px; display:none;" onclick="resetAdminForm()">إلغاء التعديل</button>

            <h3 style="margin-top:20px; font-size:14px; border-top:1px solid #eee; padding-top:10px;">إدارة وحذف المنتجات الحالية في السحاب:</h3>
            <div style="margin-top:5px; max-height:180px; overflow-y:auto;" id="adminProductsContainer"></div>
        </div>
    </div>

    <script>
        const BIN_ID = "65ca3a88dc74654018b10bb9"; 
        const API_KEY = "$2a$10$X7vB6Vw4X5wz3y786G/O.e1eUf8SzeV5jV1K3M8Y9p7pGz6FpIeCq"; 

        // بصمات التشفير الرقمية الفريدة للرموز الجديدة (SHA-256 Hashes) لغرض التمويه والأمان
        const h1 = "3977c3904599ef96dd45bbcb1b30560d652ee412329e378cb97dc83e19bf87b3";
const h2 = "98c8701a33a85cbf938931f750d9c509d86db4c72a1bd5b9595d252d658b0c1e";

        let products = [];
        let cart = [];
        let wishlist = [];
        
        let currentCurrency = "YER";
        let selectedCategory = "الكل";
        let searchQuery = "";
        let currentModalQty = 1;
        let currentSelectedColor = "";

        const exchangeRates = { YER: 1, SAR: (1 / 139.80), USD: (1 / 531) };
        const currencySymbols = { YER: "ر.ي", SAR: "ر.س", USD: "$" };

        // دالة سريعة ومحمية داخل المتصفح لتوليد تشفير ومطابقة الرموز دون كشف النصوص الأصلية
        async function sha256(str) {
            const buf = new TextEncoder().encode(str);
            const hash = await crypto.subtle.digest('SHA-256', buf);
            return Array.from(new Uint8Array(hash)).map(b => b.toString(16).padStart(2, '0')).join('');
        }

        async function loadCloudProducts() {
            document.getElementById('loadingOverlay').style.display = "flex";
            try {
                const response = await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}/latest`, {
                    headers: { "X-Master-Key": API_KEY }
                });
                const data = await response.json();
                products = data.record.products || [];
                displayProducts();
            } catch (error) {
                console.error("خطأ التزامن:", error);
                products = [
                    { id: 101, name: "حقيبة ديور كلاسيك الفاخرة المبطنة", category: "حقائب", priceYER: 58410, img: "https://images.unsplash.com/photo-1584917865442-de89df76afd3?q=80&w=500", images: ["https://images.unsplash.com/photo-1584917865442-de89df76afd3?q=80&w=500"], colors: ["أسود", "أحمر"] }
                ];
                displayProducts();
            } finally {
                document.getElementById('loadingOverlay').style.display = "none";
            }
        }

        async function updateCloudProducts() {
            document.getElementById('loadingOverlay').style.display = "flex";
            try {
                await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}`, {
                    method: "PUT",
                    headers: {
                        "Content-Type": "application/json",
                        "X-Master-Key": API_KEY
                    },
                    body: JSON.stringify({ products: products })
                });
            } catch (error) {
                alert("تعذر الحفظ في السحاب.");
            } finally {
                document.getElementById('loadingOverlay').style.display = "none";
            }
        }

        // تحصين الدالة لتعمل بمطابقة البصمة المشفرة تماماً منعاً للقراءة المباشرة للرموز 🔒
        async function handleSecretAdminUnlock() {
            let p1 = prompt("أدخل رمز الأمان الأول للدخول:");
            if (p1) {
                let check1 = await sha256(p1);
                if (check1 === h1) {
                    let p2 = prompt("🔒 ممتاز! أدخل الرمز السري الثاني لفتح لوحة التحكم بالكامل:");
                    if (p2) {
                        let check2 = await sha256(p2);
                        if (check2 === h2) {
                            toggleAdminModal();
                            return;
                        }
                    }
                    alert("رمز الأمان الثاني خاطئ!");
                } else {
                    alert("عذراً، الرمز خاطئ.");
                }
            }
        }

        function handleSearch() {
            searchQuery = document.getElementById('storeSearchInput').value.trim().toLowerCase();
            displayProducts();
        }

        function filterCategory(element, catName) {
            selectedCategory = catName;
            document.querySelectorAll('.category-tab').forEach(tab => tab.classList.remove('active'));
            element.classList.add('active');
            displayProducts();
        }

        function displayProducts() {
            const container = document.getElementById('productsContainer');
            container.innerHTML = "";
            
            let filtered = products.filter(p => {
                const matchesCategory = (selectedCategory === "الكل" || p.category === selectedCategory);
                const matchesSearch = p.name.toLowerCase().includes(searchQuery);
                return matchesCategory && matchesSearch;
            });
            
            if(filtered.length === 0) {
                container.innerHTML = `<div style="grid-column: 1/-1; text-align:center; color:#888; padding:40px;">عذراً، لم نجد أي منتج يطابق بحثك حالياً 🛍️</div>`;
                return;
            }

            filtered.forEach(prod => {
                const convertedPrice = (prod.priceYER * exchangeRates[currentCurrency]).toFixed(1);
                const isWish = wishlist.includes(prod.id) ? "active" : "";
                
                container.innerHTML += `
                    <div class="product-card">
                        <button class="wishlist-btn ${isWish}" onclick="toggleWishlist(${prod.id}, event)">
                            <i class="fas fa-heart"></i>
                        </button>
                        <div class="img-wrapper" onclick="openProductModal(${prod.id})">
                            <img src="${prod.img}" class="product-img" onerror="this.src='https://images.unsplash.com/photo-1531403009284-440f080d1e12?q=80&w=500'">
                        </div>
                        <div class="product-info">
                            <div class="product-name" onclick="openProductModal(${prod.id})">${prod.name}</div>
                            <div class="product-price">${convertedPrice} ${currencySymbols[currentCurrency]}</div>
                            <button class="btn-add-cart" onclick="openProductModal(${prod.id})">تصفح وتفحص المنتج</button>
                        </div>
                    </div>
                `;
            });
            updateAdminProductsList();
            document.getElementById('wishlistCount').innerText = wishlist.length;
        }

        function toggleWishlist(id, event) {
            if(event) event.stopPropagation();
            if (wishlist.includes(id)) { wishlist = wishlist.filter(itemId => itemId !== id); } else { wishlist.push(id); }
            displayProducts();
        }

        function openProductModal(id) {
            const prod = products.find(p => p.id === id);
            if(!prod) return;

            currentModalQty = 1;
            document.getElementById('modalQtyVal').innerText = currentModalQty;
            currentSelectedColor = prod.colors && prod.colors.length > 0 ? prod.colors[0] : "الافتراضي";

            let allImgs = [prod.img];
            if(prod.images && prod.images.length > 0) { allImgs = prod.images.filter(img => img.trim() !== ""); }

            const wrapper = document.getElementById('sliderWrapper');
            const dotsContainer = document.getElementById('sliderDots');
            wrapper.innerHTML = ""; dotsContainer.innerHTML = "";

            allImgs.forEach((imgUrl, index) => {
                wrapper.innerHTML += `<div class="slide"><img src="${imgUrl}" onerror="this.src='https://images.unsplash.com/photo-1531403009284-440f080d1e12?q=80&w=500'"></div>`;
                dotsContainer.innerHTML += `<div class="dot ${index === 0 ? 'active' : ''}"></div>`;
            });

            const convertedPrice = (prod.priceYER * exchangeRates[currentCurrency]).toFixed(1);
            let colorsHtml = "";
            if(prod.colors && prod.colors.length > 0) {
                prod.colors.forEach((col, idx) => { colorsHtml += `<span class="color-badge ${idx===0?'active':''}" onclick="selectColor(this, '${col}')">${col}</span>`; });
            }

            document.getElementById('productMainDetails').innerHTML = `
                <h1 class="details-title">${prod.name}</h1>
                <div class="rating-box"><span class="stars">⭐⭐⭐⭐⭐⭐</span></div>
                <div class="details-price">${convertedPrice} ${currencySymbols[currentCurrency]}</div>
                <div class="status-badge"><i class="fas fa-check-circle"></i> المنتج متوفر وجاهز للتسليم الفوري</div>
                ${prod.colors && prod.colors.length > 0 ? `<div class="options-title">الألوان المتاحة:</div><div class="color-group">${colorsHtml}</div>` : ''}
            `;

            document.getElementById('modalAddBtn').onclick = function() { addFromModalToCart(prod); };
            document.getElementById('viewModal').style.display = "flex";
            wrapper.scrollLeft = 0;
        }

        function updateSliderDots() {
            const wrapper = document.getElementById('sliderWrapper');
            const index = Math.round(wrapper.scrollLeft / wrapper.offsetWidth);
            document.querySelectorAll('.dot').forEach((dot, idx) => {
                if(idx === index) dot.classList.add('active'); else dot.classList.remove('active');
            });
        }

        function selectColor(element, color) {
            currentSelectedColor = color;
            document.querySelectorAll('.color-badge').forEach(b => b.classList.remove('active'));
            element.classList.add('active');
        }

        function adjustModalQty(amt) {
            currentModalQty += amt; if(currentModalQty < 1) currentModalQty = 1;
            document.getElementById('modalQtyVal').innerText = currentModalQty;
        }

        function addFromModalToCart(prod) {
            const exists = cart.find(item => item.id === prod.id && item.chosenColor === currentSelectedColor);
            if(exists) { exists.qty += currentModalQty; } else { cart.push({ ...prod, qty: currentModalQty, chosenColor: currentSelectedColor }); }
            updateCartUI(); closeViewModal(); toggleCartModal();
        }

        function changeQty(id, color, amt) {
            const item = cart.find(i => i.id === id && i.chosenColor === color);
            if(item) { item.qty += amt; if(item.qty <= 0) { cart = cart.filter(i => !(i.id === id && i.chosenColor === color)); } }
            updateCartUI();
        }

        function updateCartUI() {
            document.getElementById('cartCount').innerText = cart.reduce((sum, item) => sum + item.qty, 0);
            const container = document.getElementById('cartItemsContainer'); container.innerHTML = "";
            let totalYER = 0;

            cart.forEach(item => {
                const convertedPrice = (item.priceYER * exchangeRates[currentCurrency]).toFixed(1);
                totalYER += (item.priceYER * item.qty);
                container.innerHTML += `
                    <div class="cart-item">
                        <img src="${item.img}" class="cart-item-img">
                        <div style="flex:1;">
                            <div style="font-size:14px; font-weight:600;">${item.name}</div>
                            <div style="font-size:11px; color:#666;">اللون: ${item.chosenColor}</div>
                            <div style="color:var(--accent-color); font-weight:bold; font-size:13px;">${convertedPrice} ${currencySymbols[currentCurrency]}</div>
                            <div style="margin-top:4px;">
                                <button style="padding:1px 6px;" onclick="changeQty(${item.id}, '${item.chosenColor}', -1)">-</button>
                                <span style="margin:0 8px; font-weight:bold;">${item.qty}</span>
                                <button style="padding:1px 6px;" onclick="changeQty(${item.id}, '${item.chosenColor}', 1)">+</button>
                            </div>
                        </div>
                    </div>`;
            });
            document.getElementById('cartTotalText').innerText = `${(totalYER * exchangeRates[currentCurrency]).toFixed(1)} ${currencySymbols[currentCurrency]}`;
        }

        function sendOrderToWhatsApp() {
            if(cart.length === 0) return;
            let message = "مرحباً *Euryops Store*، أود طلب التالي:\n\n";
            let totalYER = 0;
            cart.forEach((item, index) => {
                totalYER += (item.priceYER * item.qty);
                message += `${index + 1}) *${item.name}* (اللون: ${item.chosenColor}) [الكمية: ${item.qty}]\n`;
            });
            message += `\n💰 *الإجمالي:* ${(totalYER * exchangeRates[currentCurrency]).toFixed(1)} ${currencySymbols[currentCurrency]}`;
            window.open(`https://wa.me/967778004131?text=${encodeURIComponent(message)}`, '_blank');
        }

        async function saveProductData() {
            const idValue = document.getElementById('editProductId').value;
            const name = document.getElementById('prodName').value.trim();
            const category = document.getElementById('prodCategory').value;
            const price = parseFloat(document.getElementById('prodPrice').value);
            const colorsInput = document.getElementById('prodColors').value;

            let imagesArray = [];
            for (let i = 1; i <= 5; i++) {
                let url = document.getElementById(`img${i}`).value.trim(); if(url) imagesArray.push(url);
            }

            if(!name || !price || imagesArray.length === 0) { alert("يرجى إدخال البيانات والروابط كاملة!"); return; }
            let colorsArray = colorsInput ? colorsInput.split(',').map(c => c.trim()).filter(c => c !== "") : [];

            if (idValue) {
                const idx = products.findIndex(p => p.id == idValue);
                if (idx !== -1) {
                    products[idx] = { ...products[idx], name, category, priceYER: price, img: imagesArray[0], images: imagesArray, colors: colorsArray };
                }
            } else {
                products.push({ id: Date.now(), name, category, priceYER: price, img: imagesArray[0], images: imagesArray, colors: colorsArray });
            }

            await updateCloudProducts();
            displayProducts(); resetAdminForm(); toggleAdminModal();
            alert("تم التحديث السحابي بنجاح! ☁️");
        }

        async function deleteProduct(id) {
            if(confirm("هل تريد حذف هذا المنتج نهائياً من السحاب؟")) {
                products = products.filter(p => p.id !== id);
                await updateCloudProducts();
                displayProducts();
            }
        }

        function startEditProduct(id) {
            const prod = products.find(p => p.id === id); if(!prod) return;
            document.getElementById('adminPanelTitle').innerText = "تعديل منتج في السحاب ✏️";
            document.getElementById('editProductId').value = prod.id;
            document.getElementById('prodName').value = prod.name;
            document.getElementById('prodCategory').value = prod.category;
            document.getElementById('prodPrice').value = prod.priceYER;
            document.getElementById('prodColors').value = prod.colors ? prod.colors.join(', ') : "";
            for (let i = 1; i <= 5; i++) document.getElementById(`img${i}`).value = prod.images && prod.images[i-1] ? prod.images[i-1] : "";
            document.getElementById('btnCancelEdit').style.display = "block";
        }

        function resetAdminForm() {
            document.getElementById('adminPanelTitle').innerText = "إضافة منتج جديد للـ Cloud 🛠️";
            document.getElementById('editProductId').value = ""; document.getElementById('prodName').value = "";
            document.getElementById('prodPrice').value = ""; document.getElementById('prodColors').value = "";
            for (let i = 1; i <= 5; i++) document.getElementById(`img${i}`).value = "";
            document.getElementById('btnCancelEdit').style.display = "none";
        }

        function updateAdminProductsList() {
            const container = document.getElementById('adminProductsContainer'); container.innerHTML = "";
            products.forEach(p => {
                container.innerHTML += `
                    <div class="admin-prod-item">
                        <span>${p.name}</span>
                        <div class="admin-actions-btns">
                            <button class="btn-edit" onclick="startEditProduct(${p.id})">تعديل</button>
                            <button class="btn-delete" onclick="deleteProduct(${p.id})">حذف</button>
                        </div>
                    </div>`;
            });
        }

        function changeCurrency() { currentCurrency = document.getElementById('currencySelector').value; displayProducts(); updateCartUI(); }
        function closeViewModal() { document.getElementById('viewModal').style.display = "none"; }
        function toggleCartModal() { const m = document.getElementById('cartModal'); m.style.display = m.style.display === "flex" ? "none" : "flex"; }
        function toggleWishlistModal() { const m = document.getElementById('wishlistModal'); m.style.display = m.style.display === "flex" ? "none" : "flex"; }
        function toggleAdminModal() { const m = document.getElementById('adminModal'); m.style.display = m.style.display === "flex" ? "none" : "flex"; }

        window.onload = loadCloudProducts;
    </script>
</body>
</html>
