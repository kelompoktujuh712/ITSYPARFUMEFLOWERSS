
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flowerss Parfum - Wangi Bikin Menarik</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@300;400;500;600;700&family=Pacifico&family=Quicksand:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            pink: '#FF9EB5',
                            darkPink: '#FF7597',
                            soft: '#FFF0F5',
                            purple: '#D4A5FF',
                            yellow: '#FFF59D'
                        }
                    },
                    fontFamily: {
                        'cute': ['Fredoka', 'sans-serif'],
                        'script': ['Pacifico', 'cursive'],
                        'body': ['Quicksand', 'sans-serif']
                    },
                    animation: {
                        'float': 'float 6s ease-in-out infinite',
                        'wiggle': 'wiggle 1s ease-in-out infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-20px)' },
                        },
                        wiggle: {
                            '0%, 100%': { transform: 'rotate(-3deg)' },
                            '50%': { transform: 'rotate(3deg)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        body {
            font-family: 'Quicksand', sans-serif;
            overflow-x: hidden;
            background: linear-gradient(135deg, #FFF0F5 0%, #E0F7FA 100%);
        }

        /* Flower Animation Background */
        .flower-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            overflow: hidden;
        }

        .flower {
            position: absolute;
            top: -10%;
            animation: fall linear infinite;
        }

        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }

        /* Glassmorphism Card */
        .glass-card {
            background: rgba(255, 255, 255, 0.75);
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.5);
            border-radius: 20px;
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.15);
        }

        h1, h2, h3, .nav-item, .btn-cute {
            font-family: 'Fredoka', sans-serif;
        }

        .footer-logo {
            font-family: 'Pacifico', cursive;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1; 
        }
        ::-webkit-scrollbar-thumb {
            background: #FF9EB5; 
            border-radius: 5px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #FF7597; 
        }

        /* Toast Notification */
        #toast {
            visibility: hidden;
            min-width: 250px;
            background-color: #333;
            color: #fff;
            text-align: center;
            border-radius: 50px;
            padding: 16px;
            position: fixed;
            z-index: 100;
            left: 50%;
            bottom: 30px;
            transform: translateX(-50%);
            font-size: 17px;
            opacity: 0;
            transition: opacity 0.3s, bottom 0.3s;
        }
        #toast.show {
            visibility: visible;
            opacity: 1;
            bottom: 50px;
        }
    </style>
</head>
<body class="text-gray-700">

    <!-- Falling Flowers Container -->
    <div id="flower-container" class="flower-bg"></div>

    <!-- Toast Notification -->
    <div id="toast">Berhasil ditambahkan ke keranjang! 🌸</div>

    <!-- Navigation -->
    <nav class="fixed w-full z-50 transition-all duration-300 glass-card m-2 w-[calc(100%-1rem)] top-0">
        <div class="container mx-auto px-6 py-3 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-brand-darkPink flex items-center gap-2 footer-logo">
                <i class="fas fa-spray-can"></i> Flowerss
            </a>
            
            <div class="hidden md:flex space-x-8">
                <a href="#home" class="nav-item text-gray-600 hover:text-brand-darkPink font-medium transition">Beranda</a>
                <a href="#about" class="nav-item text-gray-600 hover:text-brand-darkPink font-medium transition">Tentang Kami</a>
                <a href="#catalogue" class="nav-item text-gray-600 hover:text-brand-darkPink font-medium transition">Katalog</a>
                <a href="#reviews" class="nav-item text-gray-600 hover:text-brand-darkPink font-medium transition">Ulasan</a>
            </div>

            <button onclick="toggleCart()" class="relative p-2 text-brand-darkPink hover:scale-110 transition">
                <i class="fas fa-shopping-basket text-2xl"></i>
                <span id="cart-count" class="absolute -top-1 -right-1 bg-brand-purple text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center animate-bounce">0</span>
            </button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="pt-32 pb-20 px-6">
        <div class="container mx-auto text-center">
            <div class="animate-float mb-6 inline-block">
                <span class="text-6xl">🌸</span>
            </div>
            <h1 class="text-4xl md:text-6xl font-bold text-brand-darkPink mb-4 leading-tight">
                Wangi kan badan mu dengan <br><span class="text-brand-purple">Parfum Roll</span>
            </h1>
            <p class="text-xl md:text-2xl text-gray-600 mb-8 font-cute italic">
                "Parfum roll dengan wangi bikin menarik!!" ✨
            </p>
            <a href="#catalogue" class="inline-block bg-brand-darkPink text-white px-8 py-4 rounded-full font-bold text-lg shadow-lg hover:bg-brand-pink transform hover:-translate-y-1 transition duration-300">
                Beli Sekarang <i class="fas fa-arrow-right ml-2"></i>
            </a>
            
            <!-- Decor elements -->
            <div class="mt-12 flex justify-center gap-4 flex-wrap">
                <div class="glass-card p-4 rounded-xl transform rotate-3 hover:rotate-0 transition">
                    <span class="text-3xl">🍬</span> Sweet
                </div>
                <div class="glass-card p-4 rounded-xl transform -rotate-3 hover:rotate-0 transition">
                    <span class="text-3xl">🍰</span> Vanilla
                </div>
                <div class="glass-card p-4 rounded-xl transform rotate-2 hover:rotate-0 transition">
                    <span class="text-3xl">👸</span> Elegant
                </div>
            </div>
        </div>
    </section>

    <!-- About Us -->
    <section id="about" class="py-16 bg-white/50">
        <div class="container mx-auto px-6">
            <div class="flex flex-col md:flex-row items-center gap-10">
                <div class="w-full md:w-1/2">
                    <div class="relative">
                        <div class="absolute -top-4 -left-4 w-full h-full bg-brand-pink rounded-2xl transform rotate-3"></div>
                        <!-- New Image URL for About Us -->
                        <img src="https://p16-oec-sg.ibyteimg.com/tos-alisg-i-aphluv4xwc-sg/8392d6af60d04badaf9ca60f9f1fb587~tplv-aphluv4xwc-resize-webp:732:732.webp?dr=15592&t=555f072d&ps=933b5bde&shp=8dbd94bf&shcp=e1be8f53&idc=my2&from=2378011839" alt="Koleksi Flowerss Parfum" class="relative rounded-2xl shadow-xl w-full object-cover h-80">
                    </div>
                </div>
                <div class="w-full md:w-1/2">
                    <h2 class="text-3xl font-bold text-brand-darkPink mb-4">Tentang Flowerss Parfum</h2>
                    <p class="text-lg text-gray-600 mb-4 leading-relaxed">
                        Kami percaya bahwa wangi adalah bagian dari identitasmu. Flowerss Parfum hadir dengan kemasan roll-on yang praktis, mudah dibawa kemana saja, dan tentunya dengan harga yang super ramah di kantong!
                    </p>
                    <p class="text-lg text-gray-600 leading-relaxed">
                        Dibuat dengan bibit parfum berkualitas, wangi kami tahan lama dan bikin kamu tampil lebih percaya diri seharian. Yuk, temukan wangi favoritmu! 💖
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- Catalogue Section -->
    <section id="catalogue" class="py-20 px-6">
        <div class="container mx-auto">
            <div class="text-center mb-16">
                <h2 class="text-4xl font-bold text-gray-800 mb-2">Katalog Wangi</h2>
                <div class="h-1 w-24 bg-brand-darkPink mx-auto rounded-full"></div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Product 1 (Nagita Roll - Updated with Image) -->
                <div class="glass-card p-6 relative group hover:shadow-2xl transition duration-300">
                    <!-- Gambar Foto -->
                    <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-white p-1 rounded-full shadow-md animate-float w-32 h-32 border-4 border-white" style="animation-delay: 0s;">
                        <img src="https://p16-oec-sg.ibyteimg.com/tos-alisg-i-aphluv4xwc-sg/b5744b6837bc45c0a55b1d1bc6c88183~tplv-aphluv4xwc-resize-webp:800:800.webp?dr=15584&t=555f072d&ps=933b5bde&shp=6ce186a1&shcp=607f11de&idc=my2&from=1826719393" alt="Nagita Roll" class="w-full h-full object-cover rounded-full">
                    </div>
                    <div class="mt-20 text-center">
                        <h3 class="text-2xl font-bold text-gray-800 mb-2">Nagita Roll</h3>
                        <p class="text-brand-darkPink font-bold text-xl mb-4">Rp 7.000</p>
                        <p class="text-gray-500 mb-6 text-sm">Wangi elegan nan mewah ala sultan, memberikan kesan berkelas namun tetap lembut. Cocok untuk acara spesial!</p>
                        <button onclick="addToCart(1, 'Nagita Roll', 7000)" class="w-full bg-brand-purple text-white py-3 rounded-xl font-bold hover:bg-purple-400 transition flex justify-center items-center gap-2">
                            <i class="fas fa-cart-plus"></i> Tambah Keranjang
                        </button>
                    </div>
                </div>

                <!-- Product 2 (Sweet Boo Roll - Updated with Image) -->
                <div class="glass-card p-6 relative group hover:shadow-2xl transition duration-300 border-brand-pink">
                    <div class="absolute top-4 right-4 bg-brand-darkPink text-white text-xs px-2 py-1 rounded-full">Best Seller</div>
                    <!-- Gambar Foto -->
                    <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-white p-1 rounded-full shadow-md animate-float w-32 h-32 border-4 border-white" style="animation-delay: 1s;">
                        <img src="https://p16-oec-sg.ibyteimg.com/tos-alisg-i-aphluv4xwc-sg/574dcbdc5aed48c39d0c98cd36f0f6c7~tplv-aphluv4xwc-resize-webp:800:800.webp?dr=15584&t=555f072d&ps=933b5bde&shp=6ce186a1&shcp=607f11de&idc=my2&from=1826719393" alt="Sweet Boo Roll" class="w-full h-full object-cover rounded-full">
                    </div>
                    <div class="mt-20 text-center"> <!-- Margin top disesuaikan agar tidak tertutup foto -->
                        <h3 class="text-2xl font-bold text-gray-800 mb-2">Sweet Boo Roll</h3>
                        <p class="text-brand-darkPink font-bold text-xl mb-4">Rp 7.500</p>
                        <p class="text-gray-500 mb-6 text-sm">Aroma manis permen karet yang ceria dan energik. Wangi yang bikin mood naik seharian, super cute!</p>
                        <button onclick="addToCart(2, 'Sweet Boo Roll', 7500)" class="w-full bg-brand-darkPink text-white py-3 rounded-xl font-bold hover:bg-brand-pink transition flex justify-center items-center gap-2">
                            <i class="fas fa-cart-plus"></i> Tambah Keranjang
                        </button>
                    </div>
                </div>

                <!-- Product 3 (Vanilla Cake Roll - Updated with Image) -->
                <div class="glass-card p-6 relative group hover:shadow-2xl transition duration-300">
                    <!-- Gambar Foto -->
                    <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-white p-1 rounded-full shadow-md animate-float w-32 h-32 border-4 border-white" style="animation-delay: 2s;">
                        <img src="https://p16-oec-sg.ibyteimg.com/tos-alisg-i-aphluv4xwc-sg/72a664625a6d427da876d23c1c1c6ca0~tplv-aphluv4xwc-resize-webp:800:800.webp?dr=15584&t=555f072d&ps=933b5bde&shp=6ce186a1&shcp=607f11de&idc=my2&from=1826719393" alt="Vanilla Cake Roll" class="w-full h-full object-cover rounded-full">
                    </div>
                    <div class="mt-20 text-center"> <!-- Margin top ditambah agar tidak tertutup foto -->
                        <h3 class="text-2xl font-bold text-gray-800 mb-2">Vanilla Cake Roll</h3>
                        <p class="text-brand-darkPink font-bold text-xl mb-4">Rp 8.000</p>
                        <p class="text-gray-500 mb-6 text-sm">Wangi kue vanilla yang creamy dan hangat. Seperti pelukan hangat yang menenangkan dan bikin kangen.</p>
                        <button onclick="addToCart(3, 'Vanilla Cake Roll', 8000)" class="w-full bg-yellow-400 text-white py-3 rounded-xl font-bold hover:bg-yellow-300 transition flex justify-center items-center gap-2">
                            <i class="fas fa-cart-plus"></i> Tambah Keranjang
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Reviews Section -->
    <section id="reviews" class="py-16 bg-brand-soft">
        <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center text-gray-800 mb-12">Kata Mereka 💬</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="bg-white p-6 rounded-2xl shadow-sm">
                    <div class="flex text-yellow-400 mb-2">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p class="text-gray-600 mb-4">"Suka banget sama Sweet Boo! Wanginya manis tapi nggak bikin pusing. Kemasannya juga imut banget buat dibawa sekolah."</p>
                    <p class="font-bold text-brand-darkPink">- Putri A.</p>
                </div>
                <div class="bg-white p-6 rounded-2xl shadow-sm">
                    <div class="flex text-yellow-400 mb-2">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p class="text-gray-600 mb-4">"Vanilla Cake beneran kayak kue! Tahan lama juga wanginya walaupun seharian aktivitas. Recommended!"</p>
                    <p class="font-bold text-brand-darkPink">- Rina S.</p>
                </div>
                <div class="bg-white p-6 rounded-2xl shadow-sm">
                    <div class="flex text-yellow-400 mb-2">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star-half-alt"></i>
                    </div>
                    <p class="text-gray-600 mb-4">"Nagita Roll wanginya mewah banget dengan harga segini. Pengiriman juga cepet, adminnya ramah."</p>
                    <p class="font-bold text-brand-darkPink">- Bella K.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-white pt-16 pb-8 border-t-4 border-brand-pink">
        <div class="container mx-auto px-6 text-center">
            <h2 class="footer-logo text-4xl text-brand-darkPink mb-4">Isty parfum — Teman Wangi mu!</h2>
            <div class="flex justify-center gap-4 mb-8">
                <a href="#" class="w-10 h-10 rounded-full bg-brand-soft flex items-center justify-center text-brand-darkPink hover:bg-brand-darkPink hover:text-white transition"><i class="fab fa-instagram"></i></a>
                <a href="#" class="w-10 h-10 rounded-full bg-brand-soft flex items-center justify-center text-brand-darkPink hover:bg-brand-darkPink hover:text-white transition"><i class="fab fa-tiktok"></i></a>
                <a href="#" class="w-10 h-10 rounded-full bg-brand-soft flex items-center justify-center text-brand-darkPink hover:bg-brand-darkPink hover:text-white transition"><i class="fab fa-whatsapp"></i></a>
            </div>
            <p class="text-gray-400 text-sm">© 2024 Flowerss Parfum. All rights reserved.</p>
        </div>
    </footer>

    <!-- Cart Modal -->
    <div id="cart-modal" class="fixed inset-0 z-[100] hidden">
        <div class="absolute inset-0 bg-black bg-opacity-50 backdrop-blur-sm" onclick="toggleCart()"></div>
        <div class="absolute right-0 top-0 h-full w-full md:w-[450px] bg-white shadow-2xl transform transition-transform duration-300 translate-x-full flex flex-col" id="cart-panel">
            <div class="p-6 bg-brand-pink text-white flex justify-between items-center">
                <h3 class="text-2xl font-bold font-cute">Keranjang Wangi 🛍️</h3>
                <button onclick="toggleCart()" class="text-white hover:text-gray-200"><i class="fas fa-times text-2xl"></i></button>
            </div>
            
            <div id="cart-items" class="flex-1 overflow-y-auto p-6 space-y-4">
                <!-- Items will be injected here -->
                <div class="text-center text-gray-400 mt-10">
                    <i class="fas fa-shopping-basket text-4xl mb-4"></i>
                    <p>Keranjangmu masih kosong nih.</p>
                </div>
            </div>

            <div class="p-6 bg-gray-50 border-t border-gray-200">
                <div class="flex justify-between mb-4 text-lg font-bold">
                    <span>Total:</span>
                    <span id="cart-total" class="text-brand-darkPink">Rp 0</span>
                </div>
                <button onclick="openCheckout()" id="btn-checkout" class="w-full bg-brand-darkPink text-white py-3 rounded-xl font-bold hover:bg-brand-pink transition disabled:opacity-50 disabled:cursor-not-allowed" disabled>
                    Lanjut Pembayaran <i class="fas fa-arrow-right ml-2"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div id="checkout-modal" class="fixed inset-0 z-[110] hidden flex items-center justify-center p-4">
        <div class="absolute inset-0 bg-black bg-opacity-60 backdrop-blur-sm" onclick="closeCheckout()"></div>
        <div class="bg-white rounded-2xl w-full max-w-lg relative z-10 max-h-[90vh] overflow-y-auto">
            <div class="p-6">
                <h3 class="text-2xl font-bold text-center text-brand-darkPink mb-6 font-cute">Formulir Pemesanan ✨</h3>
                
                <form id="order-form" onsubmit="processOrder(event)">
                    <div class="space-y-4">
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">Nama Lengkap</label>
                            <input type="text" id="cust-name" required class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-brand-pink" placeholder="Nama Kakak">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">Alamat Lengkap</label>
                            <textarea id="cust-address" required rows="3" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-brand-pink" placeholder="Jalan, RT/RW, Kelurahan..."></textarea>
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm font-bold mb-2">Metode Pembayaran</label>
                            <select id="payment-method" onchange="handlePaymentChange()" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-brand-pink">
                                <option value="COD">Cash / Bayar di Tempat (COD)</option>
                                <option value="QRIS">QRIS (DANA/Gopay/Shopee)</option>
                                <option value="DANA">Transfer DANA</option>
                                <option value="OVO">Transfer OVO</option>
                                <option value="GOPAY">Transfer GoPay</option>
                            </select>
                        </div>

                        <!-- QRIS Display Area -->
                        <div id="qris-area" class="hidden text-center bg-gray-50 p-4 rounded-xl border-2 border-dashed border-brand-pink">
                            <p class="text-sm font-bold text-gray-600 mb-2">Scan QRIS DANA di bawah ini:</p>
                            <!-- Generating QR Code from API based on provided link -->
                            <img src="https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=https://qr.dana.id/v1/281012012024110773006713" alt="QRIS DANA" class="mx-auto rounded-lg shadow-md mb-2">
                            <p class="text-xs text-gray-500">Atau klik link: <a href="https://link.dana.id/minta?full_url=https://qr.dana.id/v1/281012012024110773006713" target="_blank" class="text-blue-500 underline">Buka Aplikasi DANA</a></p>
                            <p class="text-xs text-red-500 mt-2">*Mohon screenshot bukti bayar & kirim ke WA setelah pesan.</p>
                        </div>
                    </div>

                    <div class="mt-8 flex gap-3">
                        <button type="button" onclick="closeCheckout()" class="flex-1 px-4 py-2 bg-gray-200 text-gray-700 rounded-lg font-bold hover:bg-gray-300">Batal</button>
                        <button type="submit" class="flex-1 px-4 py-2 bg-green-500 text-white rounded-lg font-bold hover:bg-green-600 flex justify-center items-center gap-2">
                            <i class="fab fa-whatsapp"></i> Pesan Sekarang
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <!-- JavaScript Logic -->
    <script>
        // 1. Flower Animation Generator
        function createFlowers() {
            const container = document.getElementById('flower-container');
            const flowers = ['🌸', '🌺', '🌼', '🌷', '✨', '🍃'];
            const numberOfFlowers = 20;

            for (let i = 0; i < numberOfFlowers; i++) {
                const flower = document.createElement('div');
                flower.classList.add('flower');
                flower.innerText = flowers[Math.floor(Math.random() * flowers.length)];
                flower.style.left = Math.random() * 100 + 'vw';
                flower.style.animationDuration = (Math.random() * 5 + 5) + 's';
                flower.style.animationDelay = Math.random() * 5 + 's';
                flower.style.fontSize = (Math.random() * 20 + 20) + 'px';
                container.appendChild(flower);
            }
        }
        createFlowers();

        // 2. Shopping Cart Logic
        let cart = [];

        function addToCart(id, name, price) {
            const existingItem = cart.find(item => item.id === id);
            
            if (existingItem) {
                existingItem.qty++;
            } else {
                cart.push({ id, name, price, qty: 1 });
            }
            
            updateCartUI();
            showToast();
        }

        function removeFromCart(id) {
            cart = cart.filter(item => item.id !== id);
            updateCartUI();
        }

        function changeQty(id, change) {
            const item = cart.find(item => item.id === id);
            if (item) {
                item.qty += change;
                if (item.qty <= 0) {
                    removeFromCart(id);
                } else {
                    updateCartUI();
                }
            }
        }

        function updateCartUI() {
            const cartItemsContainer = document.getElementById('cart-items');
            const cartCount = document.getElementById('cart-count');
            const cartTotal = document.getElementById('cart-total');
            const btnCheckout = document.getElementById('btn-checkout');

            // Update Badge
            const totalQty = cart.reduce((sum, item) => sum + item.qty, 0);
            cartCount.innerText = totalQty;
            
            // Enable/Disable Checkout
            if (cart.length > 0) {
                btnCheckout.disabled = false;
                btnCheckout.classList.remove('opacity-50', 'cursor-not-allowed');
            } else {
                btnCheckout.disabled = true;
                btnCheckout.classList.add('opacity-50', 'cursor-not-allowed');
            }

            // Render Items
            if (cart.length === 0) {
                cartItemsContainer.innerHTML = `
                    <div class="text-center text-gray-400 mt-10">
                        <i class="fas fa-shopping-basket text-4xl mb-4"></i>
                        <p>Keranjangmu masih kosong nih.</p>
                    </div>
                `;
                cartTotal.innerText = 'Rp 0';
                return;
            }

            let html = '';
            let grandTotal = 0;

            cart.forEach(item => {
                const subtotal = item.price * item.qty;
                grandTotal += subtotal;
                html += `
                    <div class="flex items-center justify-between bg-gray-50 p-3 rounded-lg border border-gray-100">
                        <div>
                            <h4 class="font-bold text-gray-700">${item.name}</h4>
                            <p class="text-brand-darkPink text-sm">@ Rp ${item.price.toLocaleString('id-ID')}</p>
                        </div>
                        <div class="flex items-center gap-3">
                            <button onclick="changeQty(${item.id}, -1)" class="w-6 h-6 bg-gray-200 rounded-full text-gray-600 hover:bg-gray-300">-</button>
                            <span class="font-bold w-4 text-center">${item.qty}</span>
                            <button onclick="changeQty(${item.id}, 1)" class="w-6 h-6 bg-brand-pink text-white rounded-full hover:bg-brand-darkPink">+</button>
                        </div>
                    </div>
                `;
            });

            cartItemsContainer.innerHTML = html;
            cartTotal.innerText = 'Rp ' + grandTotal.toLocaleString('id-ID');
        }

        // 3. UI Interactions (Modals & Toasts)
        function toggleCart() {
            const modal = document.getElementById('cart-modal');
            const panel = document.getElementById('cart-panel');
            
            if (modal.classList.contains('hidden')) {
                modal.classList.remove('hidden');
                setTimeout(() => {
                    panel.classList.remove('translate-x-full');
                }, 10);
            } else {
                panel.classList.add('translate-x-full');
                setTimeout(() => {
                    modal.classList.add('hidden');
                }, 300);
            }
        }

        function showToast() {
            const toast = document.getElementById("toast");
            toast.className = "show";
            setTimeout(function(){ toast.className = toast.className.replace("show", ""); }, 3000);
        }

        function openCheckout() {
            toggleCart(); // Close cart drawer
            document.getElementById('checkout-modal').classList.remove('hidden');
        }

        function closeCheckout() {
            document.getElementById('checkout-modal').classList.add('hidden');
        }

        function handlePaymentChange() {
            const method = document.getElementById('payment-method').value;
            const qrisArea = document.getElementById('qris-area');
            
            if (method === 'QRIS') {
                qrisArea.classList.remove('hidden');
            } else {
                qrisArea.classList.add('hidden');
            }
        }

        // 4. Order Processing (WhatsApp)
        function processOrder(e) {
            e.preventDefault();
            
            const name = document.getElementById('cust-name').value;
            const address = document.getElementById('cust-address').value;
            const payment = document.getElementById('payment-method').value;
            
            // Calculate Total
            let grandTotal = 0;
            let itemsText = "";
            
            cart.forEach((item, index) => {
                const subtotal = item.price * item.qty;
                grandTotal += subtotal;
                itemsText += `${index + 1}. ${item.name} (${item.qty}x) = Rp ${subtotal.toLocaleString('id-ID')}%0A`;
            });

            const totalFormatted = 'Rp ' + grandTotal.toLocaleString('id-ID');

            // Construct Message
            let message = `Halo Isty Parfum! 🌸%0A`;
            message += `Saya mau pesan parfum dong:%0A%0A`;
            message += `---------------------------%0A`;
            message += itemsText;
            message += `---------------------------%0A`;
            message += `*Total: ${totalFormatted}*%0A%0A`;
            message += `*Data Pemesan:*%0A`;
            message += `Nama: ${name}%0A`;
            message += `Alamat: ${address}%0A`;
            message += `Metode Pembayaran: ${payment}%0A`;
            
            if(payment === 'QRIS') {
                message += `(Bukti transfer akan saya lampirkan segera)`;
            }

            // WhatsApp API Link
            const adminPhone = "6285891693186";
            const whatsappUrl = `https://wa.me/${adminPhone}?text=${message}`;

            // Open WhatsApp
            window.open(whatsappUrl, '_blank');
            
            // Reset Cart
            cart = [];
            updateCartUI();
            closeCheckout();
            
            // Show Thanks Alert (Custom)
            // Using small timeout so it appears after window switch
            setTimeout(() => {
                // You can add a success modal here if desired, 
                // but usually user is redirected to WA.
            }, 1000);
        }
    </script>
</body>
</html>
