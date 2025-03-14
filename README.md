<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>موقعي الشخصي | root</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@700;900&family=Amiri:wght@400;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }

        body {
            background: #1a1a1a;
            color: #e0e0e0;
            line-height: 1.6;
            overflow-x: hidden;
            position: relative;
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
            opacity: 0.15;
            width: 100%;
            height: 100%;
        }

        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(0, 0, 0, 0.9);
            padding: 15px 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(255, 64, 64, 0.3);
        }

        header nav ul {
            list-style: none;
            display: flex;
            gap: 20px;
        }

        header nav ul li a {
            color: #ff4040;
            text-decoration: none;
            font-weight: bold;
            font-size: 18px;
            padding: 8px 15px;
            transition: color 0.3s, transform 0.3s;
            border-radius: 20px;
        }

        header nav ul li a:hover {
            color: #fff;
            transform: scale(1.1);
        }

        .auth-menu {
            position: fixed;
            top: 70px;
            z-index: 999;
            padding: 10px;
            cursor: pointer;
        }

        html[dir="rtl"] .auth-menu {
            right: 20px;
        }

        html[dir="ltr"] .auth-menu {
            left: 20px;
        }

        .auth-menu .menu-btn {
            width: 30px;
            height: 4px;
            background: #ff4040;
            margin: 6px 0;
            border-radius: 2px;
            transition: background 0.3s;
        }

        .auth-menu .menu-btn:hover {
            background: #ff8080;
        }

        .hero {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 100px 50px 50px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .hero-image {
            flex: 1;
            max-width: 30%;
            position: relative;
        }

        .hero-image img, .hero-image canvas {
            width: 100%;
            height: auto;
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(255, 64, 64, 0.5);
            border: 3px solid #ff4040;
            object-fit: cover;
            aspect-ratio: 1 / 1;
            transition: opacity 0.3s ease;
        }

        #waveCanvas {
            position: absolute;
            top: 0;
            left: 0;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .hero-content {
            flex: 2;
            text-align: center;
            padding: 0 20px;
        }

        .hero-content h2 {
            font-size: 48px;
            color: #ff4040;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 10px rgba(255, 64, 64, 0.7);
        }

        .hero-content h3 {
            font-size: 28px;
            color: #ff8080;
            margin-bottom: 20px;
        }

        .hero-content p {
            font-family: 'Amiri', serif;
            font-size: 18px;
            color: #e0e0e0;
            line-height: 1.8;
            letter-spacing: 1px;
            margin-bottom: 30px;
        }

        .hero .social {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .hero .social a {
            color: #ff4040;
            font-size: 24px;
            transition: color 0.3s, transform 0.3s;
            text-decoration: none;
            padding: 8px;
            border-radius: 50%;
        }

        .hero .social a:hover {
            color: #fff;
            transform: scale(1.2);
        }

        .container {
            min-height: 100vh;
            padding-top: 200px;
            width: 100%;
        }

        .content {
            padding: 60px;
            background: rgba(10, 10, 10, 0.6);
            border-radius: 20px;
            box-shadow: 0 0 30px rgba(255, 64, 64, 0.2);
        }

        .section {
            margin-bottom: 80px;
            position: relative;
        }

        .section h2 {
            font-size: 42px;
            color: #ff4040;
            margin-bottom: 30px;
            text-transform: uppercase;
            letter-spacing: 5px;
            animation: glitch 2s linear infinite;
            text-align: center;
            text-shadow: 0 0 10px rgba(255, 64, 64, 0.7);
        }

        .section p {
            font-size: 20px;
            color: #e0e0e0;
            text-align: center;
            max-width: 800px;
            margin: 0 auto 30px;
            background: rgba(255, 64, 64, 0.05);
            padding: 10px;
            border-radius: 10px;
        }

        .divider {
            width: 80%;
            height: 2px;
            background: linear-gradient(to right, transparent, #ff4040, transparent);
            margin: 40px auto;
            box-shadow: 0 0 10px rgba(255, 64, 64, 0.5);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
            padding: 0 20px;
        }

        .skill-card {
            background: rgba(255, 64, 64, 0.15);
            padding: 25px;
            border-radius: 20px;
            text-align: center;
            cursor: pointer;
            transition: transform 0.4s, box-shadow 0.4s;
            border: 1px solid rgba(255, 64, 64, 0.3);
            position: relative;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(255, 64, 64, 0.2);
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255, 64, 64, 0.05), transparent);
            transition: transform 0.5s;
            z-index: 0;
        }

        .skill-card:hover::before {
            transform: scale(1.2);
        }

        .skill-card i, .skill-card h4 {
            position: relative;
            z-index: 1;
        }

        .skill-card:hover {
            transform: translateY(-15px) rotate(2deg);
            box-shadow: 0 15px 30px rgba(255, 64, 64, 0.4);
        }

        .skill-card i {
            font-size: 50px;
            color: #ff4040;
            margin-bottom: 20px;
            transition: transform 0.3s;
        }

        .skill-card:hover i {
            transform: scale(1.1) rotate(10deg);
        }

        .skill-card h4 {
            font-size: 22px;
            color: #ff8080;
            text-shadow: 0 0 5px rgba(255, 64, 64, 0.5);
        }

        .popup {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0.8);
            background: linear-gradient(135deg, #1a1a1a, #2a2a2a);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 0 40px rgba(255, 64, 64, 0.6);
            z-index: 2000;
            max-width: 450px;
            text-align: center;
            opacity: 0;
            transition: transform 0.3s ease, opacity 0.3s ease;
            border: 1px solid #ff4040;
        }

        .popup.active {
            display: block;
            transform: translate(-50%, -50%) scale(1);
            opacity: 1;
        }

        .popup h4 {
            color: #ff4040;
            margin-bottom: 20px;
            font-size: 26px;
            text-shadow: 0 0 5px rgba(255, 64, 64, 0.5);
        }

        .popup p {
            color: #e0e0e0;
            font-size: 18px;
            background: rgba(255, 64, 64, 0.05);
            padding: 10px;
            border-radius: 10px;
        }

        .popup .close-btn {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 24px;
            color: #ff4040;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .popup .close-btn:hover {
            transform: rotate(90deg);
            color: #fff;
        }

        .auth-popup {
            max-width: 400px;
            width: 90%;
        }

        .profile-popup {
            max-width: 600px;
            width: 90%;
            overflow-y: auto;
            max-height: 80vh;
        }

        .ticket-list {
            margin-top: 20px;
            max-height: 300px;
            overflow-y: auto;
        }

        .ticket-item {
            background: rgba(255, 64, 64, 0.1);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .ticket-item img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-left: 10px;
        }

        .ticket-actions button {
            padding: 5px 10px;
            margin: 0 5px;
            background: #ff4040;
            border: none;
            border-radius: 5px;
            color: #fff;
            cursor: pointer;
        }

        .ticket-actions button:hover {
            background: #ff8080;
        }

        .admin-reply {
            background: rgba(64, 255, 64, 0.1);
            padding: 10px;
            border-radius: 5px;
            margin-top: 10px;
        }

        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .contact-form input, .contact-form textarea {
            padding: 10px;
            border: 1px solid #ff4040;
            border-radius: 5px;
            background: rgba(255, 64, 64, 0.05);
            color: #e0e0e0;
            font-size: 16px;
            transition: border-color 0.3s, box-shadow 0.3s;
        }

        .contact-form input:focus, .contact-form textarea:focus {
            outline: none;
            border-color: #ff8080;
            box-shadow: 0 0 10px rgba(255, 64, 64, 0.5);
        }

        .contact-form button {
            padding: 10px;
            background: #ff4040;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s, transform 0.3s;
        }

        .contact-form button:hover {
            background: #ff8080;
            transform: scale(1.05);
        }

        .success-message {
            display: none;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .success-message i {
            font-size: 60px;
            color: #ff4040;
            animation: pulse 1.5s infinite;
        }

        .success-message p {
            font-size: 20px;
            color: #e0e0e0;
            max-width: 400px;
            line-height: 1.8;
        }

        footer {
            background: #000;
            padding: 60px 20px;
            text-align: center;
            border-top: 4px solid #ff4040;
            position: relative;
            box-shadow: 0 -5px 20px rgba(255, 64, 64, 0.3);
        }

        footer p {
            font-size: 20px;
            margin-bottom: 20px;
            color: #e0e0e0;
            text-shadow: 0 0 5px rgba(255, 64, 64, 0.5);
        }

        footer .social {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 25px;
        }

        footer .social a, footer .social .contact-btn {
            color: #ff4040;
            font-size: 32px;
            transition: color 0.3s, transform 0.5s;
            cursor: pointer;
            text-decoration: none;
            background: rgba(255, 64, 64, 0.05);
            padding: 8px;
            border-radius: 50%;
        }

        footer .social a:hover, footer .social .contact-btn:hover {
            color: #fff;
            transform: scale(1.2) rotate(360deg);
            box-shadow: 0 0 8px rgba(255, 64, 64, 0.3);
        }

        @keyframes glitch {
            2%, 64% { transform: translate(2px, 0) skew(0deg); }
            4%, 60% { transform: translate(-2px, 0) skew(0deg); }
            62% { transform: translate(0, 0) skew(5deg); }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        @media (max-width: 768px) {
            .container { width: 100%; }
            .content { padding: 30px; }
            .skills-grid { 
                grid-template-columns: 1fr;
                padding: 0 10px;
            }
            .hero {
                flex-direction: column;
                padding: 100px 20px 20px;
            }
            .hero-image {
                max-width: 50%;
                margin-bottom: 20px;
            }
            header nav ul { gap: 10px; }
            header nav ul li { margin-left: 10px; }
            footer .social { gap: 15px; }
        }
    </style>
</head>
<body>
    <canvas id="bgCanvas"></canvas>

    <header>
        <nav>
            <ul>
                <li><a href="#home" data-en="Home" data-ar="الرئيسية">الرئيسية</a></li>
                <li><a href="#about" data-en="About" data-ar="نبذة">نبذة</a></li>
                <li><a href="#skills" data-en="Skills" data-ar="مهاراتي">مهاراتي</a></li>
                <li><a href="#contact" data-en="Contact" data-ar="تواصل">تواصل</a></li>
            </ul>
        </nav>
    </header>

    <div class="auth-menu" id="authMenu">
        <div class="menu-btn"></div>
        <div class="menu-btn"></div>
        <div class="menu-btn"></div>
    </div>

    <div class="hero">
        <div class="hero-image">
            <img src="https://b.top4top.io/p_3353ggllu0.jpeg" alt="Anime-style profile" id="profileImg">
            <canvas id="waveCanvas" style="display: none;"></canvas>
            <audio id="clockSound" src="https://ephemeral-concha-441660.netlify.app/3B365C16-A020-45CD-9461-537C5ECA5455.mp4" preload="auto"></audio>
        </div>
        <div class="hero-content">
            <h2 data-en="Hello, I'm root" data-ar="مرحباً، أنا root">مرحباً، أنا root</h2>
            <h3 data-en="Creative Tech Developer" data-ar="مطور تقني ">مطور تقني </h3>
            <p class="about-text" data-en="I'm a tech enthusiast who thrives on solving complex problems with innovative and creative coding solutions." data-ar="أنا عاشق للتكنولوجيا، أزدهر بحل المشكلات المعقدة باستخدام حلول برمجية مبتكرة وإبداعية.">أنا عاشق للتكنولوجيا، أزدهر بحل المشكلات المعقدة باستخدام حلول برمجية مبتكرة وإبداعية.</p>
            <div class="social">
                <a href="#"><i class="fab fa-github"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-snapchat"></i></a>
                <a href="#" id="languageToggle"><i class="fas fa-globe"></i></a>
                <a href="#" id="heroContactBtn"><i class="fas fa-envelope"></i></a>
            </div>
        </div>
    </div>

    <div class="container">
        <div class="content">
            <div class="section" id="about">
                <h2 data-en="About Me" data-ar="نبذة عني">نبذة عني</h2>
                <p class="about-text" data-en="I'm a passionate developer and tech enthusiast dedicated to crafting innovative digital solutions that blend creativity with cutting-edge technology." data-ar="أنا مطور شغوف وعاشق للتكنولوجيا، أكرس جهودي لصياغة حلول رقمية مبتكرة تجمع بين الإبداع والتكنولوجيا المتطورة.">أنا مطور شغوف وعاشق للتكنولوجيا، أكرس جهودي لصياغة حلول رقمية مبتكرة تجمع بين الإبداع والتكنولوجيا المتطورة.</p>
            </div>
            <div class="divider"></div>
            <div class="section" id="skills">
                <h2 data-en="My Skills" data-ar="مهاراتي">مهاراتي</h2>
                <div class="skills-grid">
                    <div class="skill-card" data-popup="popup1">
                        <i class="fas fa-code"></i>
                        <h4 data-en="Programming" data-ar="البرمجة">البرمجة</h4>
                    </div>
                    <div class="skill-card" data-popup="popup2">
                        <i class="fas fa-paint-brush"></i>
                        <h4 data-en="Design" data-ar="التصميم">التصميم</h4>
                    </div>
                    <div class="skill-card" data-popup="popup3">
                        <i class="fas fa-server"></i>
                        <h4 data-en="System Administration" data-ar="إدارة الأنظمة">إدارة الأنظمة</h4>
                    </div>
                    <div class="skill-card" data-popup="popup4">
                        <i class="fas fa-terminal"></i>
                        <h4 data-en="Automation" data-ar="الأتمتة">الأتمتة</h4>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Skill Popups -->
    <div class="popup" id="popup1">
        <span class="close-btn">×</span>
        <h4 data-en="Programming" data-ar="البرمجة">البرمجة</h4>
        <p data-en="Developing high-performance applications using Python and JavaScript with a focus on quality and efficiency." data-ar="تطوير تطبيقات عالية الأداء باستخدام Python وJavaScript مع التركيز على الجودة والكفاءة.">تطوير تطبيقات عالية الأداء باستخدام Python وJavaScript مع التركيز على الجودة والكفاءة.</p>
    </div>
    <div class="popup" id="popup2">
        <span class="close-btn">×</span>
        <h4 data-en="Design" data-ar="التصميم">التصميم</h4>
        <p data-en="Creating interactive and appealing user interfaces using CSS and modern design tools." data-ar="إنشاء واجهات مستخدم تفاعلية وجذابة باستخدام CSS وأدوات التصميم الحديثة.">إنشاء واجهات مستخدم تفاعلية وجذابة باستخدام CSS وأدوات التصميم الحديثة.</p>
    </div>
    <div class="popup" id="popup3">
        <span class="close-btn">×</span>
        <h4 data-en="System Administration" data-ar="إدارة الأنظمة">إدارة الأنظمة</h4>
        <p data-en="Configuring and optimizing advanced operating systems like Linux for peak performance." data-ar="تكوين وتحسين أنظمة تشغيل متقدمة مثل Linux لتحقيق أعلى مستويات الأداء.">تكوين وتحسين أنظمة تشغيل متقدمة مثل Linux لتحقيق أعلى مستويات الأداء.</p>
    </div>
    <div class="popup" id="popup4">
        <span class="close-btn">×</span>
        <h4 data-en="Automation" data-ar="الأتمتة">الأتمتة</h4>
        <p data-en="Writing smart scripts for process automation using Bash and Python." data-ar="كتابة سكربتات ذكية لأتمتة العمليات باستخدام Bash وPython.">كتابة سكربتات ذكية لأتمتة العمليات باستخدام Bash وPython.</p>
    </div>

    <!-- Contact Popup -->
    <div class="popup" id="contactPopup">
        <span class="close-btn">×</span>
        <h4 data-en="Contact Us" data-ar="راسلنا">راسلنا</h4>
        <form class="contact-form" id="contactForm" name="contact" method="POST" data-netlify="true" data-netlify-honeypot="bot-field">
            <input type="hidden" name="form-name" value="contact">
            <input type="text" name="name" placeholder="الاسم" data-en-placeholder="Name" data-ar-placeholder="الاسم" required>
            <input type="email" name="email" placeholder="البريد الإلكتروني" data-en-placeholder="Email" data-ar-placeholder="البريد الإلكتروني" required>
            <textarea name="message" placeholder="رسالتك" data-en-placeholder="Your Message" data-ar-placeholder="رسالتك" rows="5" required></textarea>
            <button type="submit" data-en="Send" data-ar="إرسال">إرسال</button>
        </form>
        <div class="success-message" id="successMessage">
            <i class="fas fa-check-circle"></i>
            <p data-en="Your message has been sent successfully! Thank you for contacting us, and we’ll get back to you soon." data-ar="تم إرسال رسالتك بنجاح! نشكرك على تواصلك معنا، وسيتم الرد عليك في أقرب وقت ممكن.">تم إرسال رسالتك بنجاح! نشكرك على تواصلك معنا، وسيتم الرد عليك في أقرب وقت ممكن.</p>
        </div>
    </div>

    <!-- Auth Popups -->
    <div class="popup auth-popup" id="loginPopup">
        <span class="close-btn">×</span>
        <h4 data-en="Login" data-ar="تسجيل الدخول">تسجيل الدخول</h4>
        <form id="loginForm" class="contact-form">
            <input type="email" name="email" placeholder="البريد الإلكتروني" required>
            <input type="password" name="password" placeholder="كلمة المرور" required>
            <button type="submit" data-en="Login" data-ar="دخول">دخول</button>
            <p style="margin-top: 10px;"><a href="register.html" data-en="Register" data-ar="تسجيل جديد">تسجيل جديد</a></p>
        </form>
    </div>

    <div class="popup auth-popup" id="registerPopup">
        <span class="close-btn">×</span>
        <h4 data-en="Register" data-ar="تسجيل جديد">تسجيل جديد</h4>
        <form id="registerForm" class="contact-form">
            <input type="text" name="username" placeholder="اسم المستخدم" required>
            <input type="email" name="email" placeholder="البريد الإلكتروني" required>
            <input type="password" name="password" placeholder="كلمة المرور" required>
            <input type="text" name="phone" placeholder="رقم الجوال" required>
            <button type="submit" data-en="Register" data-ar="تسجيل">تسجيل</button>
            <p style="margin-top: 10px;"><a href="#" onclick="showLoginPopup(event)" data-en="Login" data-ar="تسجيل الدخول">تسجيل الدخول</a></p>
        </form>
    </div>

    <div class="popup profile-popup" id="profilePopup">
        <span class="close-btn">×</span>
        <h4 data-en="Your Profile" data-ar="ملفك الشخصي">ملفك الشخصي</h4>
        <div id="profileInfo"></div>
        <form id="updateProfileForm" class="contact-form">
            <input type="text" name="phone" id="phoneInput" placeholder="رقم الجوال">
            <button type="submit" data-en="Update" data-ar="تحديث">تحديث</button>
        </form>
        <p style="margin-top: 20px;"><a href="tickets.html" data-en="Go to Tickets" data-ar="الذهاب إلى التذاكر">الذهاب إلى التذاكر</a></p>
    </div>

    <div class="popup profile-popup" id="adminPopup">
        <span class="close-btn">×</span>
        <h4 data-en="Admin Panel" data-ar="لوحة الإدارة">لوحة الإدارة</h4>
        <div class="ticket-list" id="adminTicketList"></div>
    </div>

    <footer id="contact">
        <p data-en="All Rights Reserved © 2025 | root" data-ar="جميع الحقوق محفوظة © 2025 | root">جميع الحقوق محفوظة © 2025 | root</p>
        <div class="social">
            <a href="#"><i class="fab fa-github"></i></a>
            <a href="#"><i class="fab fa-linkedin"></i></a>
            <a href="#"><i class="fab fa-snapchat"></i></a>
            <i class="fas fa-envelope contact-btn" id="contactBtn"></i>
        </div>
    </footer>

    <script>
        // Animated Background
        const bgCanvas = document.getElementById('bgCanvas');
        const bgCtx = bgCanvas.getContext('2d');
        bgCanvas.width = window.innerWidth * 1.5;
        bgCanvas.height = window.innerHeight;

        const code = ['0', '1', 'if', 'else', 'function', 'var', 'let', '{', '}', ';', '<', '>'];
        const particles = [];

        class Particle {
            constructor() {
                this.x = Math.random() * bgCanvas.width;
                this.y = Math.random() * bgCanvas.height;
                this.text = code[Math.floor(Math.random() * code.length)];
                this.size = Math.random() * 20 + 10;
                this.speedX = (Math.random() - 0.5) * 0.5;
                this.speedY = Math.random() * 0.7 + 0.3;
            }

            draw() {
                bgCtx.fillStyle = 'rgba(255, 64, 64, 0.4)';
                bgCtx.font = `${this.size}px 'Cairo', sans-serif`;
                bgCtx.fillText(this.text, this.x, this.y);
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.y > bgCanvas.height) {
                    this.y = 0 - this.size;
                    this.x = Math.random() * bgCanvas.width;
                }
                if (this.x < 0 || this.x > bgCanvas.width) {
                    this.x = Math.random() * bgCanvas.width;
                }
                this.draw();
            }
        }

        for (let i = 0; i < 100; i++) {
            particles.push(new Particle());
        }

        function animateBackground() {
            bgCtx.clearRect(0, 0, bgCanvas.width, bgCanvas.height);
            particles.forEach(p => p.update());
            requestAnimationFrame(animateBackground);
        }
        animateBackground();

        window.addEventListener('resize', () => {
            bgCanvas.width = window.innerWidth * 1.5;
            bgCanvas.height = window.innerHeight;
        });

        // Sound Wave Functionality
        let audioContext = null;
        let analyser = null;
        let dataArray = null;
        const profileImg = document.getElementById('profileImg');
        const waveCanvas = document.getElementById('waveCanvas');
        const waveCtx = waveCanvas.getContext('2d');
        const clockSound = document.getElementById('clockSound');
        let isWaveActive = false;

        waveCanvas.width = profileImg.clientWidth;
        waveCanvas.height = profileImg.clientHeight;
        waveCanvas.style.position = 'absolute';
        waveCanvas.style.top = '0';
        waveCanvas.style.left = '0';

        function initializeAudio() {
            if (!audioContext) {
                audioContext = new (window.AudioContext || window.webkitAudioContext)();
                analyser = audioContext.createAnalyser();
                analyser.fftSize = 256;
                const bufferLength = analyser.frequencyBinCount;
                dataArray = new Uint8Array(bufferLength);

                const source = audioContext.createMediaElementSource(clockSound);
                source.connect(analyser);
                analyser.connect(audioContext.destination);
            }
            if (audioContext.state === 'suspended') {
                audioContext.resume();
            }
        }

        function drawWave() {
            if (isWaveActive && !clockSound.paused) {
                analyser.getByteFrequencyData(dataArray);
                waveCtx.clearRect(0, 0, waveCanvas.width, waveCanvas.height);
                const barWidth = (waveCanvas.width / dataArray.length) * 2.5;
                let x = 0;

                for (let i = 0; i < dataArray.length; i++) {
                    const barHeight = (dataArray[i] / 255) * (waveCanvas.height / 4);
                    waveCtx.fillStyle = `rgba(255, 64, 64, 0.7)`;
                    waveCtx.fillRect(waveCanvas.width / 2 - x, waveCanvas.height / 2 - barHeight / 2, barWidth, barHeight);
                    waveCtx.fillRect(waveCanvas.width / 2 + x, waveCanvas.height / 2 - barHeight / 2, barWidth, barHeight);
                    x += barWidth + 1;
                }
                requestAnimationFrame(drawWave);
            } else if (!isWaveActive) {
                waveCtx.clearRect(0, 0, waveCanvas.width, waveCanvas.height);
            }
        }

        function toggleWave() {
            if (!isWaveActive) {
                initializeAudio();
                waveCanvas.style.display = 'block';
                waveCanvas.style.opacity = '1';
                profileImg.style.opacity = '0.2';
                isWaveActive = true;

                clockSound.currentTime = 0;
                clockSound.play()
                    .then(() => {
                        drawWave();
                    })
                    .catch(error => {
                        console.error('Error playing audio:', error);
                    });
            } else {
                profileImg.style.opacity = '1';
                waveCanvas.style.opacity = '0';
                waveCanvas.style.display = 'none';
                clockSound.pause();
                clockSound.currentTime = 0;
                isWaveActive = false;
            }
        }

        profileImg.addEventListener('click', toggleWave);

        window.addEventListener('resize', () => {
            waveCanvas.width = profileImg.clientWidth;
            waveCanvas.height = profileImg.clientHeight;
            if (isWaveActive) {
                drawWave();
            }
        });

        // Language Toggle
        const languageToggle = document.getElementById('languageToggle');
        let currentLang = localStorage.getItem('lang') || 'ar';
        document.documentElement.lang = currentLang;
        document.documentElement.dir = currentLang === 'ar' ? 'rtl' : 'ltr';

        function updateLanguage() {
            document.querySelectorAll('[data-en][data-ar]').forEach(el => {
                el.textContent = el.getAttribute(`data-${currentLang}`);
            });
            document.querySelectorAll('[data-en-placeholder][data-ar-placeholder]').forEach(el => {
                el.placeholder = el.getAttribute(`data-${currentLang}-placeholder`);
            });
        }

        languageToggle.addEventListener('click', () => {
            currentLang = currentLang === 'ar' ? 'en' : 'ar';
            localStorage.setItem('lang', currentLang);
            document.documentElement.lang = currentLang;
            document.documentElement.dir = currentLang === 'ar' ? 'rtl' : 'ltr';
            updateLanguage();
        });

        updateLanguage();

        // Skill Popup Functionality
        const skillCards = document.querySelectorAll('.skill-card');
        const popups = document.querySelectorAll('.popup');
        const closeBtns = document.querySelectorAll('.close-btn');

        skillCards.forEach(card => {
            card.addEventListener('click', () => {
                const popupId = card.getAttribute('data-popup');
                const popup = document.getElementById(popupId);
                if (!popup.classList.contains('active')) {
                    popups.forEach(p => p.classList.remove('active'));
                    popup.classList.add('active');
                }
            });

            card.addEventListener('touchstart', (e) => {
                e.preventDefault();
                if (e.touches.length === 1 && e.targetTouches[0].force <= 0.5) {
                    const popupId = card.getAttribute('data-popup');
                    const popup = document.getElementById(popupId);
                    if (!popup.classList.contains('active')) {
                        popups.forEach(p => p.classList.remove('active'));
                        popup.classList.add('active');
                    }
                }
            });
        });

        closeBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                btn.parentElement.classList.remove('active');
            });

            btn.addEventListener('touchstart', (e) => {
                e.preventDefault();
                btn.parentElement.classList.remove('active');
            });
        });

        document.addEventListener('click', (e) => {
            const activePopup = document.querySelector('.popup.active');
            if (activePopup && !activePopup.contains(e.target) && !e.target.closest('.skill-card') && !e.target.closest('.contact-btn') && !e.target.closest('#heroContactBtn') && !e.target.closest('#authMenu')) {
                activePopup.classList.remove('active');
            }
        });

        // Contact Popup Functionality
        const contactBtn = document.getElementById('contactBtn');
        const heroContactBtn = document.getElementById('heroContactBtn');
        const contactPopup = document.getElementById('contactPopup');
        const contactForm = document.getElementById('contactForm');
        const successMessage = document.getElementById('successMessage');

        [contactBtn, heroContactBtn].forEach(btn => {
            if (btn) {
                btn.addEventListener('click', () => {
                    popups.forEach(p => p.classList.remove('active'));
                    contactPopup.classList.add('active');
                    contactForm.style.display = 'flex';
                    successMessage.style.display = 'none';
                });
            }
        });

        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const formData = new FormData(contactForm);
            fetch('/', {
                method: 'POST',
                headers: { "Content-Type": "application/x-www-form-urlencoded" },
                body: new URLSearchParams(formData).toString()
            })
            .then(() => {
                contactForm.style.display = 'none';
                successMessage.style.display = 'flex';
                setTimeout(() => {
                    contactPopup.classList.remove('active');
                }, 3000);
            })
            .catch(error => console.error('Error:', error));
        });

        // Smooth Scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Header Shrink on Scroll
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                document.querySelector('header').style.padding = '10px 20px';
            } else {
                document.querySelector('header').style.padding = '15px 20px';
            }
        });

        // Auth System with Persistent Login
        const authMenu = document.getElementById('authMenu');
        const loginPopup = document.getElementById('loginPopup');
        const registerPopup = document.getElementById('registerPopup');
        const profilePopup = document.getElementById('profilePopup');
        const adminPopup = document.getElementById('adminPopup');
        let currentUser = JSON.parse(localStorage.getItem('currentUser'));

        // Check if user is already logged in
        if (currentUser) {
            profilePopup.classList.add('active');
            loadProfile();
            if (currentUser.email === 'admin@admin.com') {
                adminPopup.classList.add('active');
                loadAdminTickets();
            }
        }

        authMenu.addEventListener('click', () => {
            popups.forEach(p => p.classList.remove('active'));
            if (currentUser) {
                profilePopup.classList.add('active');
                loadProfile();
            } else {
                loginPopup.classList.add('active');
            }
        });

        function showLoginPopup(e) {
            e.preventDefault();
            popups.forEach(p => p.classList.remove('active'));
            loginPopup.classList.add('active');
        }

        function saveUser(user) {
            let users = JSON.parse(localStorage.getItem('users')) || [];
            if (!users.find(u => u.email === user.email)) {
                users.push(user);
                localStorage.setItem('users', JSON.stringify(users));
            }
        }

        function findUser(email, password) {
            const users = JSON.parse(localStorage.getItem('users')) || [];
            return users.find(u => u.email === email && u.password === password);
        }

        document.getElementById('loginForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const email = e.target.email.value;
            const password = e.target.password.value;
            const user = findUser(email, password);
            if (user) {
                currentUser = user;
                localStorage.setItem('currentUser', JSON.stringify(user)); // Save current user
                loginPopup.classList.remove('active');
                profilePopup.classList.add('active');
                loadProfile();
                if (user.email === 'admin@admin.com') {
                    adminPopup.classList.add('active');
                    loadAdminTickets();
                }
            } else {
                alert('بيانات تسجيل الدخول غير صحيحة');
            }
        });

        document.getElementById('registerForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const user = {
                username: e.target.username.value,
                email: e.target.email.value,
                password: e.target.password.value,
                phone: e.target.phone.value,
                avatar: 'https://b.top4top.io/p_3353ggllu0.jpeg'
            };
            saveUser(user);
            currentUser = user;
            localStorage.setItem('currentUser', JSON.stringify(user)); // Save current user
            registerPopup.classList.remove('active');
            profilePopup.classList.add('active');
            loadProfile();
            e.target.reset();
        });

        function loadProfile() {
            const profileInfo = document.getElementById('profileInfo');
            profileInfo.innerHTML = `
                <p>اسم المستخدم: ${currentUser.username}</p>
                <p>البريد الإلكتروني: ${currentUser.email}</p>
                <p>رقم الجوال: ${currentUser.phone}</p>
                <img src="${currentUser.avatar}" alt="Avatar" style="width: 100px; border-radius: 50%;">
                <button onclick="logout()" style="margin-top: 10px; padding: 5px 10px; background: #ff4040; color: #fff; border: none; border-radius: 5px; cursor: pointer;">تسجيل الخروج</button>
            `;
            document.getElementById('phoneInput').value = currentUser.phone;
        }

        document.getElementById('updateProfileForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const newPhone = e.target.phone.value;
            let users = JSON.parse(localStorage.getItem('users')) || [];
            users = users.map(u => u.email === currentUser.email ? { ...u, phone: newPhone } : u);
            localStorage.setItem('users', JSON.stringify(users));
            currentUser.phone = newPhone;
            localStorage.setItem('currentUser', JSON.stringify(currentUser)); // Update current user
            loadProfile();
        });

        function logout() {
            localStorage.removeItem('currentUser');
            currentUser = null;
            profilePopup.classList.remove('active');
            adminPopup.classList.remove('active');
        }

        function loadAdminTickets() {
            const adminTicketList = document.getElementById('adminTicketList');
            let tickets = JSON.parse(localStorage.getItem('tickets')) || [];
            adminTicketList.innerHTML = tickets.map(t => `
                <div class="ticket-item">
                    <div>
                        <span>${t.userEmail}: ${t.content}</span>
                        ${t.reply ? `<div class="admin-reply">رد الإدارة: ${t.reply}</div>` : ''}
                    </div>
                    <div class="ticket-actions">
                        <button onclick="replyTicket('${t.id}')">رد</button>
                        <button onclick="editAdminTicket('${t.id}')">تعديل</button>
                        <button onclick="deleteAdminTicket('${t.id}')">حذف</button>
                        <button onclick="closeTicket('${t.id}')">${t.status === 'open' ? 'إغلاق' : 'فتح'}</button>
                    </div>
                </div>
            `).join('');
        }

        function replyTicket(id) {
            let tickets = JSON.parse(localStorage.getItem('tickets')) || [];
            const ticket = tickets.find(t => t.id === id);
            if (ticket) {
                const reply = prompt('اكتب ردك:', ticket.reply || '');
                if (reply) {
                    tickets = tickets.map(t => t.id === id ? { ...t, reply } : t);
                    localStorage.setItem('tickets', JSON.stringify(tickets));
                    loadAdminTickets();
                }
            }
        }

        function editAdminTicket(id) {
            let tickets = JSON.parse(localStorage.getItem('tickets')) || [];
            const ticket = tickets.find(t => t.id === id);
            if (ticket) {
                const newContent = prompt('عدل التذكرة:', ticket.content);
                if (newContent) {
                    tickets = tickets.map(t => t.id === id ? { ...t, content: newContent } : t);
                    localStorage.setItem('tickets', JSON.stringify(tickets));
                    loadAdminTickets();
                }
            }
        }

        function deleteAdminTicket(id) {
            if (confirm('هل تريد حذف التذكرة؟')) {
                let tickets = JSON.parse(localStorage.getItem('tickets')) || [];
                tickets = tickets.filter(t => t.id !== id);
                localStorage.setItem('tickets', JSON.stringify(tickets));
                loadAdminTickets();
            }
        }

        function closeTicket(id) {
            let tickets = JSON.parse(localStorage.getItem('tickets')) || [];
            tickets = tickets.map(t => t.id === id ? { ...t, status: t.status === 'open' ? 'closed' : 'open' } : t);
            localStorage.setItem('tickets', JSON.stringify(tickets));
            loadAdminTickets();
        }
    </script>
</body>
</html>