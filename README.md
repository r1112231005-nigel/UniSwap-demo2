<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title id="pageTitle">UniSwap | Sàn Trao Đổi Du Học Sinh</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Load Lucide Icons for aesthetic appeal -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        /* Define custom font - Inter is used by default in Tailwind, ensuring clear readability */
        body {
            font-family: "Inter", sans-serif;
            background-color: #f7f9fb; /* Light background for a clean feel */
        }
        .card-shadow {
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -2px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .card-shadow:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
        }
        /* Custom style for the main CTA color (Teal/Green, representing growth/finance) */
        .primary-bg {
            background-color: #0d9488; /* Teal-700 */
        }
        /* Custom styles for chatbox */
        #chat-window {
            height: 450px;
            max-height: 80vh;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col">

    <!-- Header & Navigation -->
    <header class="bg-white shadow-lg sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- Logo -->
                <a href="#" class="flex items-center space-x-2">
                    <div class="primary-bg p-1 rounded-md">
                        <i data-lucide="handshake" class="text-white w-6 h-6"></i>
                    </div>
                    <span class="text-xl font-bold text-gray-800 tracking-tight">UniSwap</span>
                    <span id="logo-tag" class="hidden sm:inline text-sm font-light text-gray-500">| Sàn Trao Đổi Du Học Sinh</span>
                </a>

                <!-- Search Bar (Centered on desktop) -->
                <div class="flex-1 max-w-lg mx-4 hidden md:block">
                    <div class="relative">
                        <i data-lucide="search" class="w-4 h-4 text-gray-400 absolute left-3 top-1/2 transform -translate-y-1/2"></i>
                        <input type="text" id="search-placeholder" placeholder="Tìm kiếm Sách, Điện thoại, Đồ dùng..." class="w-full py-2 pl-10 pr-4 border border-gray-200 rounded-full focus:ring-2 focus:ring-teal-500 focus:border-teal-500 transition duration-150" />
                    </div>
                </div>

                <!-- Auth/Action Buttons & Language Switcher -->
                <nav class="flex items-center space-x-3">
                    <!-- Language Switcher -->
                    <select id="language-switcher" onchange="switchLanguage(this.value)" class="p-1.5 border border-gray-300 rounded-lg text-sm bg-white text-gray-700">
                        <option value="vi">🇻🇳 Tiếng Việt</option>
                        <option value="en">🇺🇸 English</option>
                        <option value="zh-TW">🇹🇼 繁體中文</option>
                    </select>
                    
                    <button onclick="showPostModal()" id="post-button" class="primary-bg text-white px-3 py-1.5 rounded-full text-sm font-semibold hover:bg-teal-700 transition duration-150 flex items-center shadow-md">
                        <i data-lucide="plus" class="w-4 h-4 mr-1"></i>
                        Đăng Tin
                    </button>
                    <a href="#" id="login-link" class="text-gray-600 hover:text-teal-600 text-sm hidden md:block">Đăng nhập</a>
                    <a href="#" id="register-link" class="text-gray-600 hover:text-teal-600 text-sm hidden md:block">Đăng ký</a>
                </nav>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">

            <!-- Hero Section & Call to Action -->
            <section class="primary-bg text-white rounded-xl p-8 md:p-12 mb-8 shadow-xl">
                <div class="md:flex md:items-center md:justify-between">
                    <div>
                        <h1 id="slogan-h1" class="text-3xl md:text-4xl font-extrabold mb-3 leading-tight">
                            Thanh lý đồ cũ, Đón đồ mới, Tiết kiệm Chi phí Du học!
                        </h1>
                        <p id="slogan-p" class="text-teal-100 text-lg md:text-xl font-light">
                            Cộng đồng mua bán đồ dùng tin cậy và tiện lợi dành riêng cho Du học sinh tại Đài Loan.
                        </p>
                    </div>
                    <div class="mt-6 md:mt-0 flex-shrink-0">
                        <button onclick="showPostModal()" id="cta-button" class="bg-white text-teal-600 px-6 py-3 rounded-full font-bold text-lg hover:bg-gray-100 transition duration-200 shadow-lg">
                            Bắt Đầu Giao Dịch
                        </button>
                    </div>
                </div>
            </section>

            <!-- Featured Categories -->
            <section class="mb-8">
                <h2 id="category-title" class="text-2xl font-bold text-gray-800 mb-4">Danh Mục Phổ Biến</h2>
                <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-4">
                    <!-- Category 1 -->
                    <a href="#" class="bg-white p-4 rounded-xl text-center card-shadow hover:border-teal-500 border border-transparent">
                        <i data-lucide="monitor" class="w-6 h-6 text-teal-600 mx-auto mb-2"></i>
                        <span id="cat1" class="text-sm font-semibold text-gray-700">Đồ Điện Tử</span>
                    </a>
                    <!-- Category 2 -->
                    <a href="#" class="bg-white p-4 rounded-xl text-center card-shadow hover:border-teal-500 border border-transparent">
                        <i data-lucide="couch" class="w-6 h-6 text-amber-600 mx-auto mb-2"></i>
                        <span id="cat2" class="text-sm font-semibold text-gray-700">Nội Thất & Gia Dụng</span>
                    </a>
                    <!-- Category 3 -->
                    <a href="#" class="bg-white p-4 rounded-xl text-center card-shadow hover:border-teal-500 border border-transparent">
                        <i data-lucide="book-open-text" class="w-6 h-6 text-blue-600 mx-auto mb-2"></i>
                        <span id="cat3" class="text-sm font-semibold text-gray-700">Sách Giáo Trình</span>
                    </a>
                    <!-- Category 4 -->
                    <a href="#" class="bg-white p-4 rounded-xl text-center card-shadow hover:border-teal-500 border border-transparent">
                        <i data-lucide="clipboard-list" class="w-6 h-6 text-pink-600 mx-auto mb-2"></i>
                        <span id="cat4" class="text-sm font-semibold text-gray-700">Đồ Dùng Học Tập</span>
                    </a>
                    <!-- Category 5 -->
                    <a href="#" class="bg-white p-4 rounded-xl text-center card-shadow hover:border-teal-500 border border-transparent bg-yellow-50">
                        <i data-lucide="plane-takeoff" class="w-6 h-6 text-red-600 mx-auto mb-2"></i>
                        <span id="cat5" class="text-sm font-bold text-red-600">Thanh Lý Gấp</span>
                    </a>
                </div>
            </section>

            <!-- Latest Listings -->
            <section>
                <h2 id="latest-title" class="text-2xl font-bold text-gray-800 mb-4">Tin Đăng Mới Nhất</h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                    <!-- Item Card 1: Laptop -->
                    <div class="bg-white rounded-xl overflow-hidden card-shadow">
                        <!-- Updated Image Placeholder: Laptop (dark blue, professional) -->
                        <img src="https://placehold.co/600x400/1e3a8a/ffffff?text=Modern+Laptop" alt="Laptop cũ" class="w-full h-48 object-cover">
                        <div class="p-4">
                            <h3 class="text-lg font-semibold text-gray-800 truncate">Laptop cũ (dùng học tập, pin tốt)</h3>
                            <p class="text-xl font-bold text-teal-600 mt-1">6,500 NTD</p>
                            <p class="text-sm text-gray-500 mt-1 flex items-center">
                                <i data-lucide="map-pin" class="w-4 h-4 mr-1"></i>
                                Đại học Quốc gia Đài Loan (NTU)
                            </p>
                            <button id="detail-button-1" class="w-full primary-bg text-white py-2 mt-3 rounded-lg text-sm font-semibold hover:bg-teal-700 transition">
                                Chi tiết & Chat
                            </button>
                        </div>
                    </div>

                    <!-- Item Card 2: Nồi cơm điện -->
                    <div class="bg-white rounded-xl overflow-hidden card-shadow">
                        <!-- Updated Image Placeholder: Rice Cooker (red/orange, appliance look) -->
                        <img src="https://placehold.co/600x400/ef4444/ffffff?text=Smart+Rice+Cooker" alt="Nồi cơm điện mini" class="w-full h-48 object-cover">
                        <div class="p-4">
                            <h3 class="text-lg font-semibold text-gray-800 truncate">Nồi cơm điện mini (còn BH)</h3>
                            <p class="text-xl font-bold text-teal-600 mt-1">450 NTD</p>
                            <p class="text-sm text-gray-500 mt-1 flex items-center">
                                <i data-lucide="map-pin" class="w-4 h-4 mr-1"></i>
                                Ký túc xá NCTU - Tân Trúc
                            </p>
                            <button id="detail-button-2" class="w-full primary-bg text-white py-2 mt-3 rounded-lg text-sm font-semibold hover:bg-teal-700 transition">
                                Chi tiết & Chat
                            </button>
                        </div>
                    </div>

                    <!-- Item Card 3: Sách Tiếng Trung -->
                    <div class="bg-white rounded-xl overflow-hidden card-shadow">
                        <!-- Updated Image Placeholder: Chinese Book (green, academic look) -->
                        <img src="https://placehold.co/600x400/059669/ffffff?text=Mandarin+Textbooks" alt="Combo Sách Hán Ngữ" class="w-full h-48 object-cover">
                        <div class="p-4">
                            <h3 class="text-lg font-semibold text-gray-800 truncate">Combo 3 cuốn Hán Ngữ Sơ Cấp</h3>
                            <p class="text-xl font-bold text-teal-600 mt-1">Đổi/ Trao Đổi</p>
                            <p class="text-sm text-gray-500 mt-1 flex items-center">
                                <i data-lucide="map-pin" class="w-4 h-4 mr-1"></i>
                                Đại học Chính Trị (NCCU)
                            </p>
                            <button id="swap-button" class="w-full bg-indigo-500 text-white py-2 mt-3 rounded-lg text-sm font-semibold hover:bg-indigo-600 transition">
                                Đổi/ Trao Đổi
                            </button>
                        </div>
                    </div>

                    <!-- Item Card 4: Ghế -->
                    <div class="bg-white rounded-xl overflow-hidden card-shadow">
                        <!-- Updated Image Placeholder: Office Chair (indigo, office look) -->
                        <img src="https://placehold.co/600x400/4f46e5/ffffff?text=Office+Chair" alt="Ghế xoay văn phòng" class="w-full h-48 object-cover">
                        <div class="p-4">
                            <h3 class="text-lg font-semibold text-gray-800 truncate">Ghế xoay văn phòng - Xả Kho</h3>
                            <p class="text-xl font-bold text-teal-600 mt-1">790 NTD</p>
                            <p class="text-sm text-gray-500 mt-1 flex items-center">
                                <i data-lucide="map-pin" class="w-4 h-4 mr-1"></i>
                                Đại học Khoa học Kỹ thuật N.T
                            </p>
                            <button id="detail-button-4" class="w-full primary-bg text-white py-2 mt-3 rounded-lg text-sm font-semibold hover:bg-teal-700 transition">
                                Chi tiết & Chat
                            </button>
                        </div>
                    </div>
                </div>
                <div class="mt-8 text-center">
                    <button id="view-more" class="border border-teal-500 text-teal-600 px-6 py-2 rounded-full font-semibold hover:bg-teal-50 transition">
                        Xem Thêm Tất Cả Tin Đăng
                    </button>
                </div>
            </section>

        </div>
    </main>

    <!-- Footer -->
    <footer class="bg-gray-800 text-white mt-10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 md:py-12">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
                <!-- Column 1: Logo & Mission -->
                <div>
                    <h4 class="text-xl font-bold primary-bg inline-block px-2 py-0.5 rounded-md">UniSwap</h4>
                    <p id="footer-mission" class="text-sm text-gray-400 mt-4">
                        Nền tảng giúp du học sinh tiết kiệm chi phí, giảm lãng phí tài nguyên và kết nối cộng đồng.
                    </p>
                </div>
                <!-- Column 2: Quick Links -->
                <div>
                    <h5 id="footer-info" class="font-semibold mb-3 text-teal-400">Thông Tin</h5>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" id="footer-about" class="hover:text-teal-300 transition">Về Chúng Tôi</a></li>
                        <li><a href="#" id="footer-guide" class="hover:text-teal-300 transition">Hướng Dẫn An Toàn</a></li>
                        <li><a href="#" id="footer-hiring" class="hover:text-teal-300 transition">Tuyển Dụng</a></li>
                    </ul>
                </div>
                <!-- Column 3: Support -->
                <div>
                    <h5 id="footer-support" class="font-semibold mb-3 text-teal-400">Hỗ Trợ</h5>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li><a href="#" id="footer-help" class="hover:text-teal-300 transition">Trung Tâm Trợ Giúp</a></li>
                        <li><a href="#" id="footer-policy" class="hover:text-teal-300 transition">Chính Sách Hoa Hồng</a></li>
                        <li><a href="#" id="footer-report" class="hover:text-teal-300 transition">Báo Cáo Vi Phạm</a></li>
                    </ul>
                </div>
                <!-- Column 4: Contact & Social -->
                <div>
                    <h5 id="footer-contact" class="font-semibold mb-3 text-teal-400">Liên Hệ</h5>
                    <p class="text-sm text-gray-400">Email: support@uniswap.tw</p>
                    <p class="text-sm text-gray-400 mt-2">Theo dõi chúng tôi:</p>
                    <div class="flex space-x-3 mt-2">
                        <i data-lucide="facebook" class="w-5 h-5 hover:text-teal-400 cursor-pointer transition"></i>
                        <i data-lucide="instagram" class="w-5 h-5 hover:text-teal-400 cursor-pointer transition"></i>
                    </div>
                </div>
            </div>
            <div class="mt-8 pt-6 border-t border-gray-700 text-center text-sm text-gray-500">
                <span id="footer-copyright">&copy; 2025 UniSwap. Made with ❤️ for DHS in Taiwan.</span>
            </div>
        </div>
    </footer>

    <!-- Modal for Posting an Item (Mockup) -->
    <div id="postModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-[9999] hidden">
        <div class="bg-white rounded-xl shadow-2xl p-6 w-11/12 max-w-lg">
            <div class="flex justify-between items-center mb-4">
                <h3 id="modal-title" class="text-xl font-bold text-gray-800">Đăng Tin Thanh Lý Mới</h3>
                <button onclick="hidePostModal()" class="text-gray-400 hover:text-gray-600 transition">
                    <i data-lucide="x" class="w-6 h-6"></i>
                </button>
            </div>
            <p id="modal-info" class="text-sm text-gray-600 mb-4 border-l-4 border-teal-500 pl-3 py-1 bg-teal-50 rounded-md">
                <i data-lucide="info" class="w-4 h-4 inline mr-1"></i>
                Bài đăng của bạn sẽ được kiểm duyệt và yêu cầu xác minh thẻ sinh viên!
            </p>
            <form>
                <div class="mb-4">
                    <label for="title" id="modal-label-title" class="block text-sm font-medium text-gray-700 mb-1">Tiêu đề sản phẩm</label>
                    <input type="text" id="title" class="w-full border border-gray-300 p-2 rounded-lg focus:ring-teal-500 focus:border-teal-500">
                </div>
                <div class="mb-4">
                    <label for="price" id="modal-label-price" class="block text-sm font-medium text-gray-700 mb-1">Giá mong muốn (NTD)</label>
                    <input type="number" id="price" class="w-full border border-gray-300 p-2 rounded-lg focus:ring-teal-500 focus:border-teal-500">
                </div>
                <div class="mb-6">
                    <label for="category" id="modal-label-category" class="block text-sm font-medium text-gray-700 mb-1">Danh mục</label>
                    <select id="category" class="w-full border border-gray-300 p-2 rounded-lg focus:ring-teal-500 focus:border-teal-500">
                        <option id="modal-option-1">Đồ Điện Tử</option>
                        <option id="modal-option-2">Nội Thất & Gia Dụng</option>
                        <option id="modal-option-3">Sách Giáo Trình</option>
                        <option id="modal-option-4">Đồ Dùng Học Tập</option>
                    </select>
                </div>
                <button type="button" onclick="alertSuccess()" id="modal-submit" class="w-full primary-bg text-white py-2 rounded-lg font-bold hover:bg-teal-700 transition">
                    Gửi Đăng Tin
                </button>
            </form>
        </div>
    </div>

    <!-- Chat Icon Button (Floating) -->
    <button id="chat-icon-button" onclick="openChat()" class="fixed bottom-6 right-6 primary-bg text-white p-4 rounded-full shadow-2xl hover:bg-teal-700 transition duration-300 z-50 transform hover:scale-105">
        <i data-lucide="messages-square" class="w-6 h-6"></i>
    </button>

    <!-- Chat Modal/Window -->
    <div id="chat-modal" class="fixed bottom-20 right-6 w-full max-w-sm bg-white rounded-xl shadow-2xl flex flex-col hidden z-50">
        <!-- Header -->
        <div class="primary-bg text-white p-4 rounded-t-xl flex justify-between items-center">
            <div class="flex items-center">
                <i data-lucide="bot" class="w-5 h-5 mr-2"></i>
                <h4 class="font-semibold text-lg" id="chat-title">Trợ Lý UniSwap AI</h4>
            </div>
            <button onclick="closeChat()" class="text-white hover:text-teal-200">
                <i data-lucide="minus" class="w-5 h-5"></i>
            </button>
        </div>

        <!-- Message Display Area -->
        <div id="chat-window" class="flex-grow p-4 overflow-y-auto space-y-4 bg-gray-50 border-b border-gray-200">
            <!-- Initial welcome message will be added by JS on load -->
        </div>

        <!-- Input Area -->
        <div class="p-4 border-t border-gray-200">
            <div class="flex space-x-2">
                <input type="text" id="chat-input" placeholder="Nhập tin nhắn của bạn..." class="flex-grow border border-gray-300 p-2 rounded-lg focus:ring-teal-500 focus:border-teal-500" onkeydown="handleChatInput(event)">
                <button id="chat-send-button" onclick="sendMessage()" class="primary-bg text-white p-2 rounded-lg font-semibold hover:bg-teal-700 transition flex items-center justify-center w-10 h-10">
                    <i data-lucide="send" class="w-5 h-5"></i>
                </button>
            </div>
            <div id="chat-loading" class="text-sm text-gray-500 mt-2 hidden">
                <i data-lucide="loader-2" class="w-4 h-4 animate-spin inline mr-1"></i>
                Đang phản hồi...
            </div>
        </div>
    </div>

    <!-- JavaScript for Icon Replacement and Language Switching and Chat Logic -->
    <script type="module">
        // Firebase Imports (MUST be type="module")
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Global variables for Firebase (required setup)
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
        let db, auth;

        // Initialize Firebase and Auth
        if (Object.keys(firebaseConfig).length > 0) {
            const app = initializeApp(firebaseConfig);
            db = getFirestore(app);
            auth = getAuth(app);

            // Authentication Setup
            onAuthStateChanged(auth, async (user) => {
                if (!user) {
                    try {
                        if (typeof __initial_auth_token !== 'undefined') {
                             await signInWithCustomToken(auth, __initial_auth_token);
                        } else {
                             await signInAnonymously(auth);
                        }
                        console.log("Firebase signed in successfully.");
                    } catch (error) {
                        console.error("Firebase Auth Error:", error);
                    }
                }
            });
        }
        
        // --- CHAT AI LOGIC START ---

        const CHAT_MODEL = "gemini-2.5-flash-preview-09-2025";
        const API_KEY = ""; // Use empty string for Canvas environment
        const API_URL = `https://generativelanguage.googleapis.com/v1beta/models/${CHAT_MODEL}:generateContent?key=${API_KEY}`;
        
        // Chat history storage
        let chatHistory = [];
        
        // Function to define the AI's persona based on the selected language
        function getLocalizedSystemInstruction(lang) {
            const instructions = {
                'vi': "Bạn là Trợ Lý UniSwap AI. Nhiệm vụ của bạn là hỗ trợ du học sinh tại Đài Loan về các vấn đề mua bán, trao đổi đồ cũ trên nền tảng UniSwap. Dựa trên thông tin về dự án UniSwap, hãy trả lời một cách thân thiện, chính xác, và hữu ích. Hãy trả lời BẰNG TIẾNG VIỆT.",
                'en': "You are the UniSwap AI Assistant. Your task is to assist international students in Taiwan with questions about buying, selling, exchanging used items, or platform policies on UniSwap. Based on the UniSwap project information, answer in a friendly, accurate, and helpful manner. Please respond STRICTLY IN ENGLISH.",
                'zh-TW': "您是 UniSwap AI 助理。您的任務是協助台灣留學生解決在 UniSwap 平台上買賣、交換二手物品或平台政策方面的問題。根據 UniSwap 項目信息，以友好、準確、有幫助的方式回答。請以 繁體中文 回應。",
            };
            return instructions[lang] || instructions['vi']; // Default to Vietnamese
        }

        // UI elements
        const chatWindow = document.getElementById('chat-window');
        const chatInput = document.getElementById('chat-input');
        const chatLoading = document.getElementById('chat-loading');
        const chatSendButton = document.getElementById('chat-send-button');

        // Function to scroll chat to bottom
        function scrollToBottom() {
            chatWindow.scrollTop = chatWindow.scrollHeight;
        }

        // Function to add a message to the UI
        function addMessage(text, isUser = false) {
            const messageContainer = document.createElement('div');
            messageContainer.className = `flex ${isUser ? 'justify-end' : 'justify-start'}`;
            
            const messageBubble = document.createElement('div');
            const bgColor = isUser ? 'bg-teal-600 text-white' : 'bg-gray-200 text-gray-800';
            const borderRadius = isUser ? 'rounded-xl rounded-tr-none' : 'rounded-xl rounded-tl-none';
            
            messageBubble.className = `${bgColor} p-3 ${borderRadius} max-w-[80%] shadow-sm whitespace-pre-wrap`;
            messageBubble.innerHTML = text;
            
            messageContainer.appendChild(messageBubble);
            chatWindow.appendChild(messageContainer);
            scrollToBottom();
        }

        // Function to handle sending the message (exposed globally)
        window.sendMessage = async function() {
            const userPrompt = chatInput.value.trim();
            if (userPrompt === "") return;

            // 1. Add user message to UI and history
            addMessage(userPrompt, true);
            chatHistory.push({ role: "user", parts: [{ text: userPrompt }] });

            // 2. Clear input and show loading
            chatInput.value = '';
            chatInput.disabled = true;
            chatSendButton.disabled = true;
            chatLoading.classList.remove('hidden');

            try {
                // 3. Call the Gemini API
                const botResponseText = await callGeminiAPI(userPrompt);
                
                // 4. Add bot response to UI and history
                addMessage(botResponseText, false);
                // NOTE: We only store the *text* content in history.
                chatHistory.push({ role: "model", parts: [{ text: botResponseText }] }); 
                
            } catch (error) {
                console.error("Gemini API Error:", error);
                const currentLang = document.getElementById('language-switcher').value;
                const errorMsg = currentLang === 'en' ? "Sorry, I encountered a connection issue. Please try again later." : (currentLang === 'zh-TW' ? "對不起，我遇到連線問題。請稍後再試。" : "Xin lỗi, tôi gặp sự cố kết nối. Vui lòng thử lại sau.");
                addMessage(errorMsg, false);
            } finally {
                // 5. Hide loading and re-enable input
                chatInput.disabled = false;
                chatSendButton.disabled = false;
                chatLoading.classList.add('hidden');
                chatInput.focus();
                scrollToBottom();
            }
        }
        
        // Function to call the Gemini API with exponential backoff
        async function callGeminiAPI(userPrompt, retryCount = 0) {
            const maxRetries = 5;
            const delay = Math.pow(2, retryCount) * 1000; // Exponential delay: 1s, 2s, 4s, 8s...

            const currentLang = document.getElementById('language-switcher').value;
            const dynamicSystemInstruction = getLocalizedSystemInstruction(currentLang);


            const contentsPayload = [
                ...chatHistory.slice(0, -1),
                { role: "user", parts: [{ text: userPrompt }] }
            ];

            const payload = {
                contents: contentsPayload,
                systemInstruction: {
                    parts: [{ text: dynamicSystemInstruction }]
                }
            };

            try {
                const response = await fetch(API_URL, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }

                const result = await response.json();
                const text = result.candidates?.[0]?.content?.parts?.[0]?.text;
                
                if (text) {
                    return text;
                } else {
                    throw new Error("Received empty response from AI.");
                }

            } catch (error) {
                if (retryCount < maxRetries) {
                    await new Promise(resolve => setTimeout(resolve, delay));
                    return callGeminiAPI(userPrompt, retryCount + 1);
                } else {
                    throw new Error(`Failed to call Gemini API after ${maxRetries} attempts.`);
                }
            }
        }

        // Handle Enter key press
        window.handleChatInput = function(event) {
            if (event.key === 'Enter') {
                event.preventDefault();
                sendMessage();
            }
        }
        
        // --- UI & LANGUAGE LOGIC START ---

        // Expose functions globally for HTML onclick (Fixes ReferenceError for all these functions)
        window.openChat = function() {
            document.getElementById('chat-modal').classList.remove('hidden');
            document.getElementById('chat-icon-button').classList.add('hidden');
            chatInput.focus();
            scrollToBottom();
        }

        window.closeChat = function() {
            document.getElementById('chat-modal').classList.add('hidden');
            document.getElementById('chat-icon-button').classList.remove('hidden');
        }

        window.showPostModal = function() {
            document.getElementById('postModal').classList.remove('hidden');
        }

        window.hidePostModal = function() {
            document.getElementById('postModal').classList.add('hidden');
        }

        // Mockup success function (Using a simple message box instead of alert())
        window.alertSuccess = function() {
            hidePostModal();
            const currentLang = document.getElementById('language-switcher').value;
            const successText = translations[currentLang].modal_success;

            const successMessage = document.createElement('div');
            successMessage.className = 'fixed top-4 right-4 bg-green-500 text-white px-6 py-3 rounded-xl shadow-lg font-semibold z-[10000]';
            successMessage.innerHTML = `<div class="flex items-center"><i data-lucide="check-circle" class="w-5 h-5 mr-2"></i>${successText}</div>`;
            document.body.appendChild(successMessage);
            lucide.createIcons();

            setTimeout(() => {
                successMessage.remove();
            }, 3000);
        }

        // Localization Data (same as before)
        const translations = {
            'vi': {
                pageTitle: 'UniSwap | Sàn Trao Đổi Du Học Sinh',
                logo_tag: '| Sàn Trao Đổi Du Học Sinh',
                slogan_h1: 'Thanh lý đồ cũ, Đón đồ mới, Tiết kiệm Chi phí Du học!',
                slogan_p: 'Cộng đồng mua bán đồ dùng tin cậy và tiện lợi dành riêng cho Du học sinh tại Đài Loan.',
                cta_button: 'Bắt Đầu Giao Dịch',
                post_button: 'Đăng Tin',
                login_link: 'Đăng nhập',
                register_link: 'Đăng ký',
                search_placeholder: 'Tìm kiếm Sách, Điện thoại, Đồ dùng...',
                category_title: 'Danh Mục Phổ Biến',
                cat1: 'Đồ Điện Tử',
                cat2: 'Nội Thất & Gia Dụng',
                cat3: 'Sách Giáo Trình',
                cat4: 'Đồ Dùng Học Tập',
                cat5: 'Thanh Lý Gấp',
                latest_title: 'Tin Đăng Mới Nhất',
                detail_button: 'Chi tiết & Chat',
                swap_button: 'Đổi/ Trao Đổi',
                view_more: 'Xem Thêm Tất Cả Tin Đăng',
                footer_mission: 'Nền tảng giúp du học sinh tiết kiệm chi phí, giảm lãng phí tài nguyên và kết nối cộng đồng.',
                footer_info: 'Thông Tin',
                footer_about: 'Về Chúng Tôi',
                footer_guide: 'Hướng Dẫn An Toàn',
                footer_hiring: 'Tuyển Dụng',
                footer_support: 'Hỗ Trợ',
                footer_help: 'Trung Tâm Trợ Giúp',
                footer_policy: 'Chính Sách Hoa Hồng',
                footer_report: 'Báo Cáo Vi Phạm',
                footer_contact: 'Liên Hệ',
                footer_copyright: '© 2025 UniSwap. Made with ❤️ for DHS in Taiwan.',
                modal_title: 'Đăng Tin Thanh Lý Mới',
                modal_info: 'Bài đăng của bạn sẽ được kiểm duyệt và yêu cầu xác minh thẻ sinh viên!',
                modal_label_title: 'Tiêu đề sản phẩm',
                modal_label_price: 'Giá mong muốn (NTD)',
                modal_label_category: 'Danh mục',
                modal_option_1: 'Đồ Điện Tử',
                modal_option_2: 'Nội Thất & Gia Dụng',
                modal_option_3: 'Sách Giáo Trình',
                modal_option_4: 'Đồ Dùng Học Tập',
                modal_submit: 'Gửi Đăng Tin',
                modal_success: 'Tin đăng đã được gửi đi. Cảm ơn bạn!',
                chat_title: 'Trợ Lý UniSwap AI',
                chat_welcome_message: 'Chào bạn! Tôi là Trợ Lý UniSwap AI. Tôi có thể giúp bạn giải đáp mọi thắc mắc về việc mua bán, thanh lý đồ dùng hoặc chính sách của nền tảng UniSwap.',
            },
            'en': {
                pageTitle: 'UniSwap | International Student Exchange',
                logo_tag: '| International Student Exchange',
                slogan_h1: 'Buy smart – Sell fast – Save more!',
                slogan_p: 'A trusted and convenient exchange platform dedicated to international students in Taiwan.',
                cta_button: 'Start Trading',
                post_button: 'Post Item',
                login_link: 'Login',
                register_link: 'Register',
                search_placeholder: 'Search Books, Electronics, Furniture...',
                category_title: 'Popular Categories',
                cat1: 'Electronics',
                cat2: 'Furniture & Household',
                cat3: 'Textbooks',
                cat4: 'Study Supplies',
                cat5: 'Urgent Clearance',
                latest_title: 'Latest Listings',
                detail_button: 'Details & Chat',
                swap_button: 'Trade/Swap',
                view_more: 'View All Listings',
                footer_mission: 'The platform helps students save costs, reduce resource waste, and connect the community.',
                footer_info: 'Information',
                footer_about: 'About Us',
                footer_guide: 'Safety Guidelines',
                footer_hiring: 'Hiring',
                footer_support: 'Support',
                footer_help: 'Help Center',
                footer_policy: 'Commission Policy',
                footer_report: 'Report Violation',
                footer_contact: 'Contact',
                footer_copyright: '© 2025 UniSwap. Made with ❤️ for Students in Taiwan.',
                modal_title: 'Post New Item for Sale',
                modal_info: 'Your post will be reviewed and requires student ID verification!',
                modal_label_title: 'Product Title',
                modal_label_price: 'Asking Price (NTD)',
                modal_label_category: 'Category',
                modal_option_1: 'Electronics',
                modal_option_2: 'Furniture & Household',
                modal_option_3: 'Textbooks',
                modal_option_4: 'Study Supplies',
                modal_submit: 'Submit Listing',
                modal_success: 'Listing submitted successfully. Thank you!',
                chat_title: 'UniSwap AI Assistant',
                chat_welcome_message: 'Hello! I am the UniSwap AI Assistant. I can help you with any questions about buying, selling, clearing items, or platform policies on UniSwap.',
            },
            'zh-TW': {
                pageTitle: 'UniSwap | 留學生交換平台',
                logo_tag: '| 留學生交換平台',
                slogan_h1: '聰明買 - 快速賣 - 省更多!',
                slogan_p: '專屬於台灣留學生的可信賴、便利的二手商品交換平台。',
                cta_button: '開始交易',
                post_button: '發佈商品',
                login_link: '登入',
                register_link: '註冊',
                search_placeholder: '搜尋 書籍、電子產品、傢俱...',
                category_title: '熱門分類',
                cat1: '電子產品',
                cat2: '傢俱與家用電器',
                cat3: '教科書',
                cat4: '學習用品',
                cat5: '緊急清倉',
                latest_title: '最新列表',
                detail_button: '詳情及聊天',
                swap_button: '交換/交易',
                view_more: '查看更多商品',
                footer_mission: '此平台幫助留學生節省費用、減少資源浪費並連結社群。',
                footer_info: '資訊',
                footer_about: '關於我們',
                footer_guide: '安全指南',
                footer_hiring: '招募人才',
                footer_support: '支援',
                footer_help: '幫助中心',
                footer_policy: '佣金政策',
                footer_report: '舉報違規',
                footer_contact: '聯絡我們',
                footer_copyright: '© 2025 UniSwap. Made with ❤️ for Taiwan Students.',
                modal_title: '發佈新商品',
                modal_info: '您的帖子將經過審核並需要學生證驗證！',
                modal_label_title: '商品標題',
                modal_label_price: '期望價格 (NTD)',
                modal_label_category: '商品分類',
                modal_option_1: '電子產品',
                modal_option_2: '傢俱與家用電器',
                modal_option_3: '教科書',
                modal_option_4: '學習用品',
                modal_submit: '提交列表',
                modal_success: '商品列表已成功提交。謝謝您！',
                chat_title: 'UniSwap AI 助理',
                chat_welcome_message: '您好！我是 UniSwap AI 助理。我可以協助您解答有關 UniSwap 平台上購買、出售、清倉物品或平台政策的任何問題。',
            }
        };

        // Function to switch language (exposed globally)
        window.switchLanguage = function(lang) {
            const t = translations[lang];

            // Update main titles and slogans
            document.getElementById('pageTitle').textContent = t.pageTitle;
            document.getElementById('logo-tag').textContent = t.logo_tag;
            document.getElementById('slogan-h1').textContent = t.slogan_h1;
            document.getElementById('slogan-p').textContent = t.slogan_p;
            document.getElementById('cta-button').textContent = t.cta_button;
            document.getElementById('post-button').textContent = t.post_button;
            document.getElementById('login-link').textContent = t.login_link;
            document.getElementById('register-link').textContent = t.register_link;
            document.getElementById('search-placeholder').placeholder = t.search_placeholder;

            // Update categories
            document.getElementById('category-title').textContent = t.category_title;
            document.getElementById('cat1').textContent = t.cat1;
            document.getElementById('cat2').textContent = t.cat2;
            document.getElementById('cat3').textContent = t.cat3;
            document.getElementById('cat4').textContent = t.cat4;
            document.getElementById('cat5').textContent = t.cat5;
            
            // Update listings (buttons only for simplicity)
            document.getElementById('latest-title').textContent = t.latest_title;
            document.getElementById('detail-button-1').textContent = t.detail_button;
            document.getElementById('detail-button-2').textContent = t.detail_button;
            document.getElementById('swap-button').textContent = t.swap_button;
            document.getElementById('detail-button-4').textContent = t.detail_button;
            document.getElementById('view-more').textContent = t.view_more;
            
            // Update Footer
            document.getElementById('footer-mission').textContent = t.footer_mission;
            document.getElementById('footer-info').textContent = t.footer_info;
            document.getElementById('footer-about').textContent = t.footer_about;
            document.getElementById('footer-guide').textContent = t.footer_guide;
            document.getElementById('footer-hiring').textContent = t.footer_hiring;
            document.getElementById('footer-support').textContent = t.footer_support;
            document.getElementById('footer-help').textContent = t.footer_help;
            document.getElementById('footer-policy').textContent = t.footer_policy;
            document.getElementById('footer-report').textContent = t.footer_report;
            document.getElementById('footer-contact').textContent = t.footer_contact;
            document.getElementById('footer-copyright').textContent = t.footer_copyright;

            // Update Modal
            document.getElementById('modal-title').textContent = t.modal_title;
            document.getElementById('modal-info').textContent = t.modal_info;
            document.getElementById('modal-label-title').textContent = t.modal_label_title;
            document.getElementById('modal-label-price').textContent = t.modal_label_price;
            document.getElementById('modal-label-category').textContent = t.modal_label_category;
            document.getElementById('modal-option-1').textContent = t.modal_option_1;
            document.getElementById('modal-option-2').textContent = t.modal_option_2;
            document.getElementById('modal-option-3').textContent = t.modal_option_3;
            document.getElementById('modal-option-4').textContent = t.modal_option_4;
            document.getElementById('modal-submit').textContent = t.modal_submit;

            // Update Chat UI (Title, Welcome, Placeholder)
            document.getElementById('chat-title').textContent = t.chat_title;
            document.getElementById('chat-input').placeholder = lang === 'vi' ? 'Nhập tin nhắn của bạn...' : (lang === 'en' ? 'Type your message...' : '輸入您的訊息...');

            // Clear chat history when switching language to prevent mixed-language context
            chatHistory = [];
            chatWindow.innerHTML = '';
            // Re-add the welcome message in the new language
            addMessage(t.chat_welcome_message, false);

            // Set HTML lang attribute
            document.documentElement.lang = lang;
        }

        // Hide modal when clicking outside (on the overlay)
        document.getElementById('postModal').addEventListener('click', (e) => {
            if (e.target === document.getElementById('postModal')) {
                hidePostModal();
            }
        });
        
        // Initialize everything on window load
        window.onload = () => {
             // 1. Replace Lucide icons
             lucide.createIcons();

             // 2. Initialize language to Vietnamese (default in HTML)
             const defaultLang = document.getElementById('language-switcher').value;
             // We call switchLanguage here to ensure the chat window gets its initial welcome message
             switchLanguage(defaultLang);
        };
    </script>
</body>
</html>
