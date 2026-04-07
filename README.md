[index.html](https://github.com/user-attachments/files/26529713/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>旷野营记 | Glamping露营生活</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+SC:wght@400;600;700&family=Noto+Sans+SC:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #2C3E2D;
            --secondary: #8B7355;
            --accent: #D4A574;
            --light: #F5F1EB;
            --cream: #FAF8F5;
            --text: #333333;
            --text-light: #666666;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Noto Sans SC', sans-serif;
            background-color: var(--cream);
            color: var(--text);
            line-height: 1.8;
        }

        h1, h2, h3, h4 {
            font-family: 'Noto Serif SC', serif;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.2rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            background: rgba(250, 248, 245, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0,0,0,0.05);
        }

        .logo {
            font-family: 'Noto Serif SC', serif;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
            letter-spacing: 2px;
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text);
            font-size: 0.9rem;
            font-weight: 400;
            letter-spacing: 1px;
            transition: color 0.3s;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 1px;
            background: var(--accent);
            transition: width 0.3s;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .mobile-menu-btn {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            padding: 5px;
        }

        .mobile-menu-btn span {
            width: 25px;
            height: 2px;
            background: var(--primary);
            transition: 0.3s;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            min-height: 700px;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=1920&q=80') center/cover;
            filter: brightness(0.6);
        }

        .hero-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, 
                rgba(44, 62, 45, 0.3) 0%, 
                rgba(44, 62, 45, 0.5) 50%,
                rgba(44, 62, 45, 0.7) 100%);
        }

        .hero-content {
            position: relative;
            z-index: 2;
            text-align: center;
            color: white;
            padding: 0 2rem;
        }

        .hero-subtitle {
            font-size: 0.9rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            margin-bottom: 1.5rem;
            opacity: 0.9;
        }

        .hero-title {
            font-size: clamp(2.5rem, 8vw, 5rem);
            font-weight: 700;
            line-height: 1.2;
            margin-bottom: 1.5rem;
            letter-spacing: 8px;
        }

        .hero-desc {
            font-size: 1.1rem;
            max-width: 600px;
            margin: 0 auto 2.5rem;
            opacity: 0.9;
            font-weight: 300;
        }

        .hero-btn {
            display: inline-block;
            padding: 1rem 2.5rem;
            background: transparent;
            border: 1px solid white;
            color: white;
            text-decoration: none;
            font-size: 0.9rem;
            letter-spacing: 2px;
            transition: all 0.3s;
        }

        .hero-btn:hover {
            background: white;
            color: var(--primary);
        }

        .scroll-indicator {
            position: absolute;
            bottom: 3rem;
            left: 50%;
            transform: translateX(-50%);
            color: white;
            font-size: 0.8rem;
            letter-spacing: 2px;
            opacity: 0.8;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
            40% { transform: translateX(-50%) translateY(-10px); }
            60% { transform: translateX(-50%) translateY(-5px); }
        }

        /* Section Common */
        section {
            padding: 8rem 5%;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-label {
            font-size: 0.8rem;
            letter-spacing: 3px;
            color: var(--accent);
            margin-bottom: 1rem;
            text-transform: uppercase;
        }

        .section-title {
            font-size: clamp(1.8rem, 4vw, 2.5rem);
            color: var(--primary);
            margin-bottom: 1rem;
        }

        .section-desc {
            max-width: 600px;
            margin: 0 auto;
            color: var(--text-light);
        }

        /* About Section */
        .about {
            background: white;
        }

        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            max-width: 1200px;
            margin: 0 auto;
            align-items: center;
        }

        .about-img {
            position: relative;
        }

        .about-img img {
            width: 100%;
            height: 500px;
            object-fit: cover;
        }

        .about-img::before {
            content: '';
            position: absolute;
            top: 2rem;
            left: 2rem;
            width: 100%;
            height: 100%;
            border: 1px solid var(--accent);
            z-index: -1;
        }

        .about-content {
            padding: 2rem 0;
        }

        .about-content h3 {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 1.5rem;
        }

        .about-content p {
            color: var(--text-light);
            margin-bottom: 1.5rem;
            font-size: 1rem;
        }

        .stats {
            display: flex;
            gap: 3rem;
            margin-top: 2rem;
        }

        .stat-item {
            text-align: center;
        }

        .stat-number {
            font-family: 'Noto Serif SC', serif;
            font-size: 2.5rem;
            color: var(--accent);
            font-weight: 700;
        }

        .stat-label {
            font-size: 0.85rem;
            color: var(--text-light);
        }

        /* Categories Section */
        .categories {
            background: var(--light);
        }

        .category-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .category-card {
            position: relative;
            height: 400px;
            overflow: hidden;
            cursor: pointer;
        }

        .category-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .category-card:hover img {
            transform: scale(1.1);
        }

        .category-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 2rem;
            background: linear-gradient(to top, rgba(0,0,0,0.7), transparent);
            color: white;
        }

        .category-name {
            font-family: 'Noto Serif SC', serif;
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .category-count {
            font-size: 0.85rem;
            opacity: 0.8;
        }

        /* Blog Section */
        .blog {
            background: white;
        }

        .blog-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .blog-card {
            background: var(--cream);
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .blog-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.08);
        }

        .blog-img {
            height: 220px;
            overflow: hidden;
        }

        .blog-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .blog-card:hover .blog-img img {
            transform: scale(1.1);
        }

        .blog-content {
            padding: 1.5rem;
        }

        .blog-tag {
            display: inline-block;
            padding: 0.3rem 0.8rem;
            background: var(--accent);
            color: white;
            font-size: 0.75rem;
            border-radius: 2px;
            margin-bottom: 1rem;
        }

        .blog-title {
            font-size: 1.2rem;
            color: var(--primary);
            margin-bottom: 0.8rem;
            line-height: 1.4;
        }

        .blog-excerpt {
            font-size: 0.9rem;
            color: var(--text-light);
            margin-bottom: 1rem;
        }

        .blog-meta {
            font-size: 0.8rem;
            color: #999;
            display: flex;
            gap: 1rem;
        }

        /* Article Modal */
        .article-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 3000;
            overflow-y: auto;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .article-modal.active {
            display: flex;
            opacity: 1;
        }

        .article-modal-content {
            max-width: 800px;
            margin: 5vh auto;
            background: white;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            animation: slideUp 0.4s ease;
        }

        @keyframes slideUp {
            from {
                transform: translateY(50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .article-modal-close {
            position: absolute;
            top: 1rem;
            right: 1.5rem;
            font-size: 2rem;
            color: var(--text-light);
            cursor: pointer;
            z-index: 10;
            background: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .article-modal-close:hover {
            color: var(--text);
        }

        .article-modal-img {
            width: 100%;
            height: 400px;
            object-fit: cover;
        }

        .article-modal-body {
            padding: 2rem 3rem 3rem;
        }

        .article-modal-body .blog-tag {
            margin-bottom: 1rem;
        }

        .article-modal-body h2 {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 1rem;
            line-height: 1.3;
        }

        .article-modal-meta {
            font-size: 0.85rem;
            color: #999;
            margin-bottom: 2rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid #eee;
        }

        .article-modal-body p {
            font-size: 1.05rem;
            line-height: 2;
            color: var(--text);
            margin-bottom: 1.5rem;
        }

        .article-modal-body h3 {
            font-size: 1.3rem;
            color: var(--primary);
            margin: 2rem 0 1rem;
        }

        .article-modal-body ul {
            margin: 1rem 0 1.5rem 1.5rem;
        }

        .article-modal-body li {
            margin-bottom: 0.8rem;
            line-height: 1.8;
        }

        .read-more-btn {
            display: inline-block;
            padding: 0.6rem 1.2rem;
            background: var(--primary);
            color: white;
            font-size: 0.85rem;
            border-radius: 4px;
            margin-top: 1rem;
            cursor: pointer;
            border: none;
        }

        .read-more-btn:hover {
            background: #1a2a1b;
        }

        /* Gallery Section */
        .gallery {
            background: var(--primary);
            padding: 8rem 5%;
        }

        .gallery .section-header {
            color: white;
        }

        .gallery .section-title {
            color: white;
        }

        .gallery .section-desc {
            color: rgba(255,255,255,0.7);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            aspect-ratio: 1;
        }

        .gallery-item:nth-child(1) {
            grid-column: span 2;
            grid-row: span 2;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .gallery-item:hover img {
            transform: scale(1.1);
        }

        .gallery-item::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(44, 62, 45, 0);
            transition: background 0.3s;
        }

        .gallery-item:hover::after {
            background: rgba(44, 62, 45, 0.3);
        }

        /* Video Section */
        .video-section {
            background: var(--light);
        }

        .video-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 2rem;
            max-width: 1000px;
            margin: 0 auto;
        }

        .video-card {
            background: white;
            overflow: hidden;
        }

        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%;
            height: 0;
        }

        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .video-info {
            padding: 1.5rem;
        }

        .video-title {
            font-size: 1.1rem;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .video-desc {
            font-size: 0.9rem;
            color: var(--text-light);
        }

        /* Gear Section */
        .gear {
            background: white;
        }

        .gear-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .gear-card {
            text-align: center;
        }

        .gear-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            margin-bottom: 1rem;
            border-radius: 4px;
        }

        .gear-name {
            font-size: 1rem;
            color: var(--primary);
            margin-bottom: 0.3rem;
        }

        .gear-brand {
            font-size: 0.85rem;
            color: var(--text-light);
        }

        /* Campsites Section */
        .campsites {
            background: var(--light);
        }

        .campsite-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .campsite-card {
            background: white;
            overflow: hidden;
        }

        .campsite-img {
            height: 200px;
            overflow: hidden;
        }

        .campsite-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .campsite-card:hover .campsite-img img {
            transform: scale(1.1);
        }

        .campsite-content {
            padding: 1.5rem;
        }

        .campsite-name {
            font-size: 1.2rem;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .campsite-location {
            font-size: 0.85rem;
            color: var(--accent);
            margin-bottom: 0.8rem;
        }

        .campsite-desc {
            font-size: 0.9rem;
            color: var(--text-light);
        }

        /* Newsletter Section */
        .newsletter {
            background: linear-gradient(rgba(44, 62, 45, 0.9), rgba(44, 62, 45, 0.9)),
                        url('https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=1920&q=80') center/cover fixed;
            padding: 6rem 5%;
            text-align: center;
            color: white;
        }

        .newsletter h3 {
            font-size: 2rem;
            margin-bottom: 1rem;
        }

        .newsletter p {
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .newsletter-form {
            display: flex;
            max-width: 500px;
            margin: 0 auto;
            gap: 1rem;
        }

        .newsletter-form input {
            flex: 1;
            padding: 1rem 1.5rem;
            border: 1px solid rgba(255,255,255,0.3);
            background: rgba(255,255,255,0.1);
            color: white;
            font-size: 1rem;
        }

        .newsletter-form input::placeholder {
            color: rgba(255,255,255,0.7);
        }

        .newsletter-form button {
            padding: 1rem 2rem;
            background: var(--accent);
            border: none;
            color: white;
            cursor: pointer;
            font-size: 0.9rem;
            letter-spacing: 1px;
            transition: background 0.3s;
        }

        .newsletter-form button:hover {
            background: #c49660;
        }

        /* Footer */
        footer {
            background: var(--primary);
            color: white;
            padding: 4rem 5% 2rem;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 3rem;
            max-width: 1200px;
            margin: 0 auto 3rem;
        }

        .footer-brand h4 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .footer-brand p {
            font-size: 0.9rem;
            opacity: 0.8;
            line-height: 1.8;
        }

        .footer-links h5 {
            font-size: 1rem;
            margin-bottom: 1rem;
            color: var(--accent);
        }

        .footer-links ul {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.8rem;
        }

        .footer-links a {
            color: rgba(255,255,255,0.8);
            text-decoration: none;
            font-size: 0.9rem;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: white;
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-links a {
            width: 40px;
            height: 40px;
            border: 1px solid rgba(255,255,255,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-decoration: none;
            transition: all 0.3s;
        }

        .social-links a:hover {
            background: var(--accent);
            border-color: var(--accent);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid rgba(255,255,255,0.1);
            font-size: 0.85rem;
            opacity: 0.7;
        }

        /* Mobile Responsive */
        @media (max-width: 1024px) {
            .category-grid,
            .blog-grid,
            .campsite-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .gear-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .gallery-grid {
                grid-template-columns: repeat(2, 1fr);
            }

            .gallery-item:nth-child(1) {
                grid-column: span 2;
                grid-row: span 1;
            }

            .footer-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu-btn {
                display: flex;
            }

            .nav-links.active {
                display: flex;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: white;
                flex-direction: column;
                padding: 2rem;
                gap: 1.5rem;
                box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            }

            .about-grid {
                grid-template-columns: 1fr;
            }

            .about-img {
                order: -1;
            }

            .about-img::before {
                display: none;
            }

            .category-grid,
            .blog-grid,
            .campsite-grid,
            .gear-grid,
            .video-grid {
                grid-template-columns: 1fr;
            }

            .gallery-grid {
                grid-template-columns: 1fr 1fr;
            }

            .stats {
                justify-content: center;
            }

            .newsletter-form {
                flex-direction: column;
            }

            .footer-grid {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .social-links {
                justify-content: center;
            }
        }

        /* Animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s, transform 0.6s;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Lightbox */
        .lightbox {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }

        .lightbox.active {
            display: flex;
        }

        .lightbox img {
            max-width: 90%;
            max-height: 90%;
            object-fit: contain;
        }

        .lightbox-close {
            position: absolute;
            top: 2rem;
            right: 2rem;
            color: white;
            font-size: 2rem;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="navbar">
        <a href="#" class="logo">旷野营记</a>
        <ul class="nav-links">
            <li><a href="#about">关于我们</a></li>
            <li><a href="#categories">营地分类</a></li>
            <li><a href="#blog">攻略分享</a></li>
            <li><a href="#gallery">摄影图集</a></li>
            <li><a href="#video">视频专区</a></li>
            <li><a href="#gear">装备推荐</a></li>
            <li><a href="#contact">联系我们</a></li>
        </ul>
        <div class="mobile-menu-btn" onclick="toggleMenu()">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-bg"></div>
        <div class="hero-overlay"></div>
        <div class="hero-content">
            <p class="hero-subtitle">Welcome to the Wilderness</p>
            <h1 class="hero-title">旷野营记</h1>
            <p class="hero-desc">在星空下入眠，在晨雾中醒来。<br>探索精致露营的每一种可能。</p>
            <a href="#about" class="hero-btn">开始探索</a>
        </div>
        <div class="scroll-indicator">SCROLL</div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="about-grid">
            <div class="about-img fade-in">
                <img src="https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?w=800&q=80" alt="露营场景">
            </div>
            <div class="about-content fade-in">
                <p class="section-label">About Us</p>
                <h3>我们相信<br>露营是一种生活方式</h3>
                <p>「旷野营记」由一群热爱自然的露营爱好者创立。我们追求的不是征服自然，而是与自然和谐共处——在精致的装备中感受野外的气息，在篝火旁聆听风声与虫鸣。</p>
                <p>无论你是刚开始接触露营的新手，还是追求品质的资深玩家，这里都有属于你的内容：装备评测、营地推荐、技巧分享，以及最美的露营时刻。</p>
                <div class="stats">
                    <div class="stat-item">
                        <div class="stat-number">50+</div>
                        <div class="stat-label">精选营地</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">200+</div>
                        <div class="stat-label">装备评测</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-number">30+</div>
                        <div class="stat-label">攻略文章</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Categories Section -->
    <section class="categories" id="categories">
        <div class="section-header">
            <p class="section-label">Categories</p>
            <h2 class="section-title">探索不同的露营方式</h2>
            <p class="section-desc">从荒野探险到精致Glamping，找到最适合你的露营体验</p>
        </div>
        <div class="category-grid">
            <div class="category-card fade-in">
                <img src="https://images.unsplash.com/photo-1537905569824-f89f14cceb68?w=800&q=80" alt="Glamping">
                <div class="category-overlay">
                    <h4 class="category-name">精致露营 Glamping</h4>
                    <p class="category-count">奢华与自然的完美结合</p>
                </div>
            </div>
            <div class="category-card fade-in">
                <img src="https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=800&q=80" alt="Forest Camping">
                <div class="category-overlay">
                    <h4 class="category-name">森林露营</h4>
                    <p class="category-count">在林间听风入眠</p>
                </div>
            </div>
            <div class="category-card fade-in">
                <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=800&q=80" alt="Lakeside">
                <div class="category-overlay">
                    <h4 class="category-name">湖畔露营</h4>
                    <p class="category-count">水面如镜，星空倒映</p>
                </div>
            </div>
            <div class="category-card fade-in">
                <img src="https://images.unsplash.com/photo-1517824806704-9040b037703b?w=800&q=80" alt="Mountain">
                <div class="category-overlay">
                    <h4 class="category-name">山顶露营</h4>
                    <p class="category-count">一览众山小的壮阔</p>
                </div>
            </div>
            <div class="category-card fade-in">
                <img src="https://images.unsplash.com/photo-1510312305653-8ed496efae75?w=800&q=80" alt="Beach">
                <div class="category-overlay">
                    <h4 class="category-name">海边露营</h4>
                    <p class="category-count">聆听海浪的节拍</p>
                </div>
            </div>
            <div class="category-card fade-in">
                <img src="https://images.unsplash.com/photo-1486915309615-73ca5dfc3fc4?w=800&q=80" alt="Winter">
                <div class="category-overlay">
                    <h4 class="category-name">冬季露营</h4>
                    <p class="category-count">挑战冰雪的浪漫</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Blog Section -->
    <section class="blog" id="blog">
        <div class="section-header">
            <p class="section-label">Latest Articles</p>
            <h2 class="section-title">最新攻略</h2>
            <p class="section-desc">实用的露营技巧、深入的装备评测、最美的营地推荐</p>
        </div>
        <div class="blog-grid">
            <!-- 新手入门 -->
            <div class="blog-card fade-in" onclick="openArticle('article-1')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1542652735873-fb2825bac6e2?w=600&q=80" alt="新手入门">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">新手入门</span>
                    <h4 class="blog-title">第一次露营需要准备什么？完整清单来了</h4>
                    <p class="blog-excerpt">很多新手第一次露营不知道该带什么，这篇为你整理了从帐篷到灯具的完整装备清单...</p>
                    <div class="blog-meta">
                        <span>2024.03.15</span>
                        <span>阅读 2.3k</span>
                    </div>
                </div>
            </div>
            <!-- 帐篷评测 -->
            <div class="blog-card fade-in" onclick="openArticle('article-2')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?w=600&q=80" alt="帐篷推荐">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">装备评测</span>
                    <h4 class="blog-title">2024年最值得入手的5款帐篷推荐</h4>
                    <p class="blog-excerpt">从轻量化到家庭款，从专业级到入门级，我们测评了市面上主流帐篷...</p>
                    <div class="blog-meta">
                        <span>2024.03.10</span>
                        <span>阅读 3.8k</span>
                    </div>
                </div>
            </div>
            <!-- 营地推荐 -->
            <div class="blog-card fade-in" onclick="openArticle('article-3')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1478827536114-da961b7f86d2?w=600&q=80" alt="营地推荐">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">营地推荐</span>
                    <h4 class="blog-title">京郊5个绝美露营地，距离近风景美</h4>
                    <p class="blog-excerpt">不想跑太远？这5个京郊露营地开车2小时内可达，风景却不输远方...</p>
                    <div class="blog-meta">
                        <span>2024.03.05</span>
                        <span>阅读 5.1k</span>
                    </div>
                </div>
            </div>
            <!-- 春季攻略 -->
            <div class="blog-card fade-in" onclick="openArticle('article-4')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1418065460487-3e41a6c84dc5?w=600&q=80" alt="春季露营">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">季节攻略</span>
                    <h4 class="blog-title">春季露营完全指南：赏花踏青两不误</h4>
                    <p class="blog-excerpt">春天是露营的黄金季节，这篇告诉你春季露营的最佳时机、注意事项和必去目的地...</p>
                    <div class="blog-meta">
                        <span>2024.02.28</span>
                        <span>阅读 1.8k</span>
                    </div>
                </div>
            </div>
            <!-- 睡袋选购 -->
            <div class="blog-card fade-in" onclick="openArticle('article-5')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=600&q=80" alt="睡袋选购">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">装备评测</span>
                    <h4 class="blog-title">睡袋选购指南：温标、填充物、品牌全解析</h4>
                    <p class="blog-excerpt">睡袋是露营最重要的装备之一，如何选择合适的温标？羽绒和棉睡袋哪个好？...</p>
                    <div class="blog-meta">
                        <span>2024.02.20</span>
                        <span>阅读 2.6k</span>
                    </div>
                </div>
            </div>
            <!-- 营地美食 -->
            <div class="blog-card fade-in" onclick="openArticle('article-6')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?w=600&q=80" alt="营地美食">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">露营食谱</span>
                    <h4 class="blog-title">野外也能吃得好：10道简单美味的营地食谱</h4>
                    <p class="blog-excerpt">露营不是只能吃泡面！分享10道在营地就能做的简单又美味的料理...</p>
                    <div class="blog-meta">
                        <span>2024.02.15</span>
                        <span>阅读 4.2k</span>
                    </div>
                </div>
            </div>
            <!-- 夏季攻略 -->
            <div class="blog-card fade-in" onclick="openArticle('article-4')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=600&q=80" alt="夏季露营">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">季节攻略</span>
                    <h4 class="blog-title">夏季露营全攻略：防暑防虫防雨一篇搞定</h4>
                    <p class="blog-excerpt">夏天露营最怕热和蚊虫，这篇分享实用的防暑、防虫、防突然降雨技巧...</p>
                    <div class="blog-meta">
                        <span>2024.06.01</span>
                        <span>阅读 3.1k</span>
                    </div>
                </div>
            </div>
            <!-- 安全须知 -->
            <div class="blog-card fade-in" onclick="openArticle('article-1')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1486915309615-73ca5dfc3fc4?w=600&q=80" alt="露营安全">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">安全须知</span>
                    <h4 class="blog-title">露营安全手册：这些知识关键时刻能救命</h4>
                    <p class="blog-excerpt">户外安全无小事！这篇整理了露营常见的危险及应对方法，建议收藏...</p>
                    <div class="blog-meta">
                        <span>2024.01.25</span>
                        <span>阅读 6.5k</span>
                    </div>
                </div>
            </div>
            <!-- 秋季攻略 -->
            <div class="blog-card fade-in" onclick="openArticle('article-4')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1517824806704-9040b037703b?w=600&q=80" alt="秋季露营">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">季节攻略</span>
                    <h4 class="blog-title">秋天是露营的最佳季节：赏枫叶观星河</h4>
                    <p class="blog-excerpt">秋高气爽的秋季是公认最适合露营的季节，推荐几个赏枫观星的绝佳目的地...</p>
                    <div class="blog-meta">
                        <span>2024.09.15</span>
                        <span>阅读 4.8k</span>
                    </div>
                </div>
            </div>
            <!-- 炉具评测 -->
            <div class="blog-card fade-in" onclick="openArticle('article-2')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1510312305653-8ed496efae75?w=600&q=80" alt="炉具推荐">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">装备评测</span>
                    <h4 class="blog-title">便携炉具横评：气炉、油炉、酒精炉哪个好？</h4>
                    <p class="blog-excerpt">露营做饭离不开炉子，气炉方便但怕低温，油炉火力强但维护复杂...</p>
                    <div class="blog-meta">
                        <span>2024.01.10</span>
                        <span>阅读 2.9k</span>
                    </div>
                </div>
            </div>
            <!-- 江浙沪推荐 -->
            <div class="blog-card fade-in" onclick="openArticle('article-3')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1537905569824-f89f14cceb68?w=600&q=80" alt="江浙沪营地">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">目的地</span>
                    <h4 class="blog-title">江浙沪周边8个宝藏露营地，周末说走就走</h4>
                    <p class="blog-excerpt">不想长假出行？这8个江浙沪周边的宝藏露营地，开车2-4小时即达...</p>
                    <div class="blog-meta">
                        <span>2024.01.05</span>
                        <span>阅读 7.2k</span>
                    </div>
                </div>
            </div>
            <!-- 冬季攻略 -->
            <div class="blog-card fade-in" onclick="openArticle('article-4')" style="cursor:pointer;">
                <div class="blog-img">
                    <img src="https://images.unsplash.com/photo-1486915309615-73ca5dfc3fc4?w=600&q=80" alt="冬季露营">
                </div>
                <div class="blog-content">
                    <span class="blog-tag">季节攻略</span>
                    <h4 class="blog-title">冬季露营入门：保暖技巧与装备清单</h4>
                    <p class="blog-excerpt">冬天的星空更璀璨，雪地露营别有风情，但这也是最具挑战的季节...</p>
                    <div class="blog-meta">
                        <span>2023.12.20</span>
                        <span>阅读 3.4k</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Gallery Section -->
    <section class="gallery" id="gallery">
        <div class="section-header">
            <p class="section-label">Gallery</p>
            <h2 class="section-title">摄影图集</h2>
            <p class="section-desc">用镜头记录每一次与大自然的相遇</p>
        </div>
        <div class="gallery-grid">
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=1200&q=80" alt="露营全景">
            </div>
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=600&q=80" alt="帐篷">
            </div>
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?w=600&q=80" alt="篝火">
            </div>
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=600&q=80" alt="星空">
            </div>
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1517824806704-9040b037703b?w=600&q=80" alt="日出">
            </div>
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?w=600&q=80" alt="山景">
            </div>
            <div class="gallery-item fade-in" onclick="openLightbox(this)">
                <img src="https://images.unsplash.com/photo-1537905569824-f89f14cceb68?w=600&q=80" alt="Glamping">
            </div>
        </div>
    </section>

    <!-- Video Section -->
    <section class="video-section" id="video">
        <div class="section-header">
            <p class="section-label">Video</p>
            <h2 class="section-title">视频专区</h2>
            <p class="section-desc">用视频带你身临其境感受露营的魅力</p>
        </div>
        <div class="video-grid">
            <div class="video-card fade-in">
                <div class="video-wrapper">
                    <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
                </div>
                <div class="video-info">
                    <h4 class="video-title">如何搭建完美的帐篷营地</h4>
                    <p class="video-desc">从选址到搭建，手把手教你搭建一个既舒适又安全的帐篷营地</p>
                </div>
            </div>
            <div class="video-card fade-in">
                <div class="video-wrapper">
                    <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
                </div>
                <div class="video-info">
                    <h4 class="video-title">Glamping 精致露营体验</h4>
                    <p class="video-desc">探访山野间的精致露营地，感受不一样的户外美学</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Gear Section -->
    <section class="gear" id="gear">
        <div class="section-header">
            <p class="section-label">Gear</p>
            <h2 class="section-title">装备推荐</h2>
            <p class="section-desc">精挑细选的露营好物，让你的每一次出发更加完美</p>
        </div>
        <div class="gear-grid">
            <div class="gear-card fade-in">
                <img src="https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=400&q=80" alt="帐篷" class="gear-img">
                <h4 class="gear-name">轻量化隧道帐</h4>
                <p class="gear-brand">MSR / NEMO / Big Agnes</p>
            </div>
            <div class="gear-card fade-in">
                <img src="https://images.unsplash.com/photo-1510312305653-8ed496efae75?w=400&q=80" alt="睡袋" class="gear-img">
                <h4 class="gear-name">羽绒睡袋</h4>
                <p class="gear-brand">Western Mountaineering</p>
            </div>
            <div class="gear-card fade-in">
                <img src="https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?w=400&q=80" alt="炉具" class="gear-img">
                <h4 class="gear-name">便携野营炉</h4>
                <p class="gear-brand">Jetboil / MSR / Snow Peak</p>
            </div>
            <div class="gear-card fade-in">
                <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=400&q=80" alt="椅子" class="gear-img">
                <h4 class="gear-name">折叠营地椅</h4>
                <p class="gear-brand">Helinox / REI Co-op</p>
            </div>
        </div>
    </section>

    <!-- Campsites Section -->
    <section class="campsites" id="campsites">
        <div class="section-header">
            <p class="section-label">Campsites</p>
            <h2 class="section-title">精选营地</h2>
            <p class="section-desc">亲自踩点评测的优质营地，值得信赖</p>
        </div>
        <div class="campsite-grid">
            <div class="campsite-card fade-in">
                <div class="campsite-img">
                    <img src="https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=600&q=80" alt="营地1">
                </div>
                <div class="campsite-content">
                    <h4 class="campsite-name">松鸣森林营地</h4>
                    <p class="campsite-location">北京 · 密云</p>
                    <p class="campsite-desc">位于原始松林间，生态环境极佳，提供水电接入，适合家庭露营</p>
                </div>
            </div>
            <div class="campsite-card fade-in">
                <div class="campsite-img">
                    <img src="https://images.unsplash.com/photo-1504280390367-361c6d9f38f4?w=600&q=80" alt="营地2">
                </div>
                <div class="campsite-content">
                    <h4 class="campsite-name">星河湖畔营地</h4>
                    <p class="campsite-location">浙江 · 莫干山</p>
                    <p class="campsite-desc">湖畔草地视野开阔，夜晚星空璀璨，有专业的营位和设施</p>
                </div>
            </div>
            <div class="campsite-card fade-in">
                <div class="campsite-img">
                    <img src="https://images.unsplash.com/photo-1517824806704-9040b037703b?w=600&q=80" alt="营地3">
                </div>
                <div class="campsite-content">
                    <h4 class="campsite-name">云顶山野营地</h4>
                    <p class="campsite-location">四川 · 成都</p>
                    <p class="campsite-desc">位于山顶平台，可观日出云海，适合有一定经验的露营者</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Newsletter Section -->
    <section class="newsletter" id="contact">
        <h3>加入露营社区</h3>
        <p>获取最新攻略、装备评测和营地推荐</p>
        <form class="newsletter-form" onsubmit="handleSubscribe(event)">
            <input type="email" placeholder="输入你的邮箱" required>
            <button type="submit">订阅</button>
        </form>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-grid">
            <div class="footer-brand">
                <h4>旷野营记</h4>
                <p>探索精致露营的每一种可能。<br>在星空下入眠，在晨雾中醒来。</p>
                <div class="social-links">
                    <a href="#">微</a>
                    <a href="#">小</a>
                    <a href="#">知</a>
                    <a href="#">B站</a>
                </div>
            </div>
            <div class="footer-links">
                <h5>内容</h5>
                <ul>
                    <li><a href="#blog">攻略分享</a></li>
                    <li><a href="#gear">装备评测</a></li>
                    <li><a href="#campsites">营地推荐</a></li>
                    <li><a href="#gallery">摄影图集</a></li>
                </ul>
            </div>
            <div class="footer-links">
                <h5>分类</h5>
                <ul>
                    <li><a href="#categories">Glamping</a></li>
                    <li><a href="#categories">森林露营</a></li>
                    <li><a href="#categories">湖畔露营</a></li>
                    <li><a href="#categories">山顶露营</a></li>
                </ul>
            </div>
            <div class="footer-links">
                <h5>联系</h5>
                <ul>
                    <li><a href="#">关于我们</a></li>
                    <li><a href="#">商务合作</a></li>
                    <li><a href="#">投稿入口</a></li>
                    <li><a href="#">联系邮箱</a></li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>© 2024 旷野营记. 探索自然，享受生活</p>
        </div>
    </footer>

    <!-- Article Modal -->
    <div class="article-modal" id="articleModal">
        <span class="article-modal-close" onclick="closeArticle()">×</span>
        <div class="article-modal-content">
            <img src="" alt="" id="articleModalImg" class="article-modal-img">
            <div class="article-modal-body">
                <span class="blog-tag" id="articleModalTag"></span>
                <h2 id="articleModalTitle"></h2>
                <p class="article-modal-meta" id="articleModalMeta"></p>
                <div id="articleModalContent"></div>
            </div>
        </div>
    </div>

    <!-- Lightbox -->
    <div class="lightbox" id="lightbox" onclick="closeLightbox()">
        <span class="lightbox-close">×</span>
        <img src="" alt="放大图片" id="lightbox-img">
    </div>

    <script>
        // Navigation scroll effect
        window.addEventListener('scroll', function() {
            const nav = document.getElementById('navbar');
            if (window.scrollY > 50) {
                nav.classList.add('scrolled');
            } else {
                nav.classList.remove('scrolled');
            }
        });

        // Mobile menu toggle
        function toggleMenu() {
            document.querySelector('.nav-links').classList.toggle('active');
        }

        // Fade in animation on scroll
        const fadeElements = document.querySelectorAll('.fade-in');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });

        fadeElements.forEach(el => observer.observe(el));

        // Article Modal Functions
        const articles = {
            'article-1': {
                title: '第一次露营需要准备什么？完整清单来了',
                tag: '新手入门',
                date: '2024.03.15',
                views: '2.3k',
                image: 'https://images.unsplash.com/photo-1542652735873-fb2825bac6e2?w=1200&q=80',
                content: `
                    <p>第一次露营总是既兴奋又紧张？不用担心，这篇为你整理了从帐篷到灯具的完整装备清单，确保你不会遗漏任何重要物品。</p>
                    
                    <h3>一、基础装备</h3>
                    <ul>
                        <li><strong>帐篷</strong>：根据人数选择合适尺寸，建议新手选择自动开合的款式</li>
                        <li><strong>睡袋</strong>：根据季节选择合适的温标，夏季可选薄款，冬季需要温标更低的</li>
                        <li><strong>防潮垫/充气垫</strong>：必备！隔热防潮还能增加舒适度</li>
                        <li><strong>营地灯/头灯</strong>：夜间活动必备，头灯可以解放双手</li>
                    </ul>
                    
                    <h3>二、烹饪装备</h3>
                    <ul>
                        <li><strong>便携炉具</strong>：气炉最方便，适合新手</li>
                        <li><strong>锅具</strong>：带一个煎锅和一个汤锅就够用</li>
                        <li><strong>餐具</strong>：户外专用的不易碎材质</li>
                        <li><strong>保温水壶</strong>：随时喝到热水</li>
                    </ul>
                    
                    <h3>三、服装建议</h3>
                    <ul>
                        <li><strong>保暖层</strong>：抓绒或轻薄羽绒服，昼夜温差大时必备</li>
                        <li><strong>防水外套</strong>：山区天气多变，防雨防风很重要</li>
                        <li><strong>舒适的鞋子</strong>：登山鞋或防滑运动鞋</li>
                        <li><strong>备用衣物</strong>：多带一套换洗衣物</li>
                    </ul>
                    
                    <h3>四、安全与急救</h3>
                    <ul>
                        <li><strong>急救包</strong>：创可贴、消毒酒精、止血带等基础用品</li>
                        <li><strong>防晒霜</strong>：高SPF值，山区紫外线更强</li>
                        <li><strong>驱蚊液</strong>：夏季露营必备</li>
                        <li><strong>地图/指南针</strong>：即使有手机也要备一份</li>
                    </ul>
                    
                    <h3>新手小贴士</h3>
                    <p>第一次露营建议选择有基础设施的正规营地，水电供应充足，安全性更高。等经验丰富后再尝试野外露营。</p>
                `
            },
            'article-2': {
                title: '2024年最值得入手的5款帐篷推荐',
                tag: '装备评测',
                date: '2024.03.10',
                views: '3.8k',
                image: 'https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?w=1200&q=80',
                content: `
                    <p>帐篷是露营的核心装备，一顶好的帐篷能让你的露营体验提升好几个档次。我们测评了市面上的主流帐篷，为你精选了以下5款。</p>
                    
                    <h3>1. MSR Hubba Hubba NX 2</h3>
                    <p><strong>类型：</strong>轻量化隧道帐</p>
                    <p><strong>适用场景：</strong>徒步露营、2人使用</p>
                    <p>这款帐篷是轻量化露营的首选，前后双门设计，重量仅1.5kg左右。搭建简单，防雨性能出色。</p>
                    
                    <h3>2. NEMO Hornet 2P</h3>
                    <p><strong>类型：</strong>自立式帐篷</p>
                    <p><strong>适用场景：</strong>通用</p>
                    <p>超轻设计，1.2kg的自重让它成为背包客的最爱。内部空间利用率高，配备了LED挂灯环。</p>
                    
                    <h3>3. Big Agnes Copper Spur HV UL3</h3>
                    <p><strong>类型：</strong>家庭帐篷</p>
                    <p><strong>适用场景：</strong>3-4人家庭露营</p>
                    <p>空间宽敞，重量控制得当。网布占比大，通风性能优秀，夏季使用很舒适。</p>
                    
                    <h3>4. Snow Peak Land Double</h3>
                    <p><strong>类型：</strong>Glamping帐篷</p>
                    <p><strong>适用场景：</strong>精致露营</p>
                    <p>日本品牌，设计感极强。极简风格搭配高级面料，非常适合追求品质的Glamping爱好者。</p>
                    
                    <h3>5. 牧高笛 冷山2</h3>
                    <p><strong>类型：</strong>入门级帐篷</p>
                    <p><strong>适用场景：</strong>新手入门</p>
                    <p>国产品牌性价比之选，价格实惠，防护性能可靠。适合预算有限的新手露营者。</p>
                `
            },
            'article-3': {
                title: '京郊5个绝美露营地，距离近风景美',
                tag: '营地推荐',
                date: '2024.03.05',
                views: '5.1k',
                image: 'https://images.unsplash.com/photo-1478827536114-da961b7f86d2?w=1200&q=80',
                content: `
                    <p>不想跑太远？这5个京郊露营地开车2小时内可达，风景却不输远方。是周末出逃的绝佳选择。</p>
                    
                    <h3>1. 密云 · 云蒙山营地</h3>
                    <p>位于云蒙山国家森林公园内，海拔较高，夜晚星空璀璨。营地有水电接入，适合家庭露营。</p>
                    <p><strong>距离：</strong>北京城区约90公里</p>
                    <p><strong>特色：</strong>森林、溪流、星空</p>
                    
                    <h3>2. 怀柔 · 慕田峪脚下营地</h3>
                    <p>在长城脚下安营扎寨，早起还能看长城日出。营地设施完善，周边可游览多个长城景点。</p>
                    <p><strong>距离：</strong>北京城区约70公里</p>
                    <p><strong>特色：</strong>长城、日出、古迹</p>
                    
                    <h3>3. 延庆 · 海坨山谷</h3>
                    <p>位于北京第二高峰海坨山脚下，生态环境极佳。有专业的帐篷营地和木屋住宿可选。</p>
                    <p><strong>距离：</strong>北京城区约120公里</p>
                    <p><strong>特色：</strong>高山草甸、云海、野生花卉</p>
                    
                    <h3>4. 门头沟 · 清水尖营地</h3>
                    <p>相对小众的野营地，需要徒步才能到达。适合追求清静的原生态露营体验。</p>
                    <p><strong>距离：</strong>北京城区约80公里</p>
                    <p><strong>特色：</strong>清静、原生态、挑战性</p>
                    
                    <h3>5. 平谷 · 金海湖营地</h3>
                    <p>依傍金海湖，景色开阔。可以划船、钓鱼，夏季还能玩水上项目。</p>
                    <p><strong>距离：</strong>北京城区约100公里</p>
                    <p><strong>特色：</strong>湖泊、水上活动、家庭友好</p>
                `
            },
            'article-4': {
                title: '春季露营完全指南：赏花踏青两不误',
                tag: '季节攻略',
                date: '2024.02.28',
                views: '1.8k',
                image: 'https://images.unsplash.com/photo-1418065460487-3e41a6c84dc5?w=1200&q=80',
                content: `
                    <p>春天是露营的黄金季节，天气渐暖、万物复苏，是出门露营的最佳时机。这篇指南帮你规划一次完美的春季露营。</p>
                    
                    <h3>最佳露营时间</h3>
                    <p>北方地区建议3月下旬至5月中旬为最佳时期，此时气温适宜、百花盛开。南方地区可以提前到2月底开始。</p>
                    
                    <h3>春季露营装备重点</h3>
                    <ul>
                        <li><strong>保暖依然重要</strong>：春季昼夜温差大，夜间温度可能降至零下，睡袋温标建议在-5°C至5°C之间</li>
                        <li><strong>防雨装备</strong>：春季多雨，务必带上防水地垫和备用防雨罩</li>
                        <li><strong>透气服装</strong>：白天活动量大，建议穿排汗透气的速干衣</li>
                    </ul>
                    
                    <h3>春季露营地推荐</h3>
                    <p>春季推荐选择有花景的营地：</p>
                    <ul>
                        <li>婺源 — 油菜花海中的帐篷营地</li>
                        <li>西藏林芝 — 桃花盛开的雪山营地</li>
                        <li>伊犁 — 野花遍地的草原露营</li>
                    </ul>
                    
                    <h3>注意事项</h3>
                    <p>春季户外活动要特别注意花粉过敏，随身携带抗过敏药物。另外，春季是森林防火期，用火要格外小心。</p>
                `
            },
            'article-5': {
                title: '睡袋选购指南：温标、填充物、品牌全解析',
                tag: '装备评测',
                date: '2024.02.20',
                views: '2.6k',
                image: 'https://images.unsplash.com/photo-1478131143081-80f7f84ca84d?w=1200&q=80',
                content: `
                    <p>睡袋是露营最重要的装备之一，直接影响睡眠质量。选择合适的睡袋需要考虑温标、填充物、款式等多个因素。</p>
                    
                    <h3>温标解读</h3>
                    <p>睡袋温标通常标注三个数值：</p>
                    <ul>
                        <li><strong>极限温度</strong>：勉强可以保暖的温度</li>
                        <li><strong>舒适温度</strong>：大多数人感到舒适的温度</li>
                        <li><strong>上限温度</strong>：感到热的温度</li>
                    </ul>
                    <p>建议选择舒适温度等于或略低于预期最低温度的睡袋。</p>
                    
                    <h3>填充物对比</h3>
                    <p><strong>羽绒睡袋：</strong></p>
                    <ul>
                        <li>优点：轻便、可压缩、保暖性强、寿命长</li>
                        <li>缺点：价格较高、潮湿后保暖性大幅下降</li>
                        <li>适合：追求轻量化、专业露营、干燥环境</li>
                    </ul>
                    <p><strong>棉/化纤睡袋：</strong></p>
                    <ul>
                        <li>优点：价格实惠、耐潮湿、清洗方便</li>
                        <li>缺点：重、压缩性差、保暖性随时间下降</li>
                        <li>适合：新手入门、潮湿环境、频繁清洗</li>
                    </ul>
                    
                    <h3>款式选择</h3>
                    <p><strong>木乃伊式：</strong>包裹性好、保暖效率高、重量轻，是户外露营首选。</p>
                    <p><strong>信封式：</strong>空间宽敞、可展开当被子用、方便拼接，适合家庭或营地露营。</p>
                `
            },
            'article-6': {
                title: '野外也能吃得好：10道简单美味的营地食谱',
                tag: '露营食谱',
                date: '2024.02.15',
                views: '4.2k',
                image: 'https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?w=1200&q=80',
                content: `
                    <p>露营不是只能吃泡面！分享10道在营地就能做的简单又美味的料理，让你的野外生活也有美食相伴。</p>
                    
                    <h3>早餐篇</h3>
                    <p><strong>1. 培根煎蛋配烤面包</strong></p>
                    <p>经典中的经典，用煎锅就能搞定。培根的油脂煎蛋，格外香。</p>
                    
                    <p><strong>2. 燕麦粥配坚果果干</strong></p>
                    <p>前一晚用保温杯泡好，早上直接吃。加点坚果和蔓越莓干，营养又饱腹。</p>
                    
                    <h3>午餐篇</h3>
                    <p><strong>3. 营地三明治</strong></p>
                    <p>提前一晚准备食材，午餐简单组合即可。火腿、芝士、生菜、番茄，层次丰富。</p>
                    
                    <p><strong>4. 蔬菜肉片炒饭</strong></p>
                    <p>用剩米饭加上火腿肠、蔬菜丁，大火快炒，是最实用的营地快手菜。</p>
                    
                    <h3>晚餐篇</h3>
                    <p><strong>5. 营地火锅</strong></p>
                    <p>带上底料和食材，大家围在一起涮，气氛满分。推荐鸳鸯锅底，照顾不同口味。</p>
                    
                    <p><strong>6. 煎牛排配芦笋</strong></p>
                    <p>露营也要吃好！提前腌制好的牛排，煎至五分熟，配上烤芦笋，仪式感拉满。</p>
                    
                    <p><strong>7. 番茄肉丸意面</strong></p>
                    <p>速食意面酱加上现做的肉丸，简单快手，却能慰藉一天的疲惫。</p>
                    
                    <h3>甜点篇</h3>
                    <p><strong>8. 棉花糖烤夹心饼干</strong></p>
                    <p>两片饼干夹着棉花糖，用营火慢慢烤至融化，童年回忆杀！</p>
                    
                    <p><strong>9. 香蕉巧克力船</strong></p>
                    <p>香蕉剖开塞入巧克力块，烤至巧克力融化，简单却惊艳。</p>
                    
                    <p><strong>10. 热红酒</strong></p>
                    <p>肉桂、橙子、丁香加红酒，小火加热。星空下的一杯暖酒，是露营夜晚最好的结尾。</p>
                `
            }
        };

        // Open article modal
        function openArticle(id) {
            const article = articles[id];
            if (!article) return;
            
            document.getElementById('articleModalImg').src = article.image;
            document.getElementById('articleModalTag').textContent = article.tag;
            document.getElementById('articleModalTitle').textContent = article.title;
            document.getElementById('articleModalMeta').textContent = article.date + ' · 阅读 ' + article.views;
            document.getElementById('articleModalContent').innerHTML = article.content;
            
            document.getElementById('articleModal').classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeArticle() {
            document.getElementById('articleModal').classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        // Close modal on escape key
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                closeArticle();
                closeLightbox();
            }
        });

        // Close modal on click outside
        document.getElementById('articleModal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeArticle();
            }
        });

        // Lightbox
        function openLightbox(element) {
            const img = element.querySelector('img');
            document.getElementById('lightbox-img').src = img.src;
            document.getElementById('lightbox').classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeLightbox() {
            document.getElementById('lightbox').classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        // Newsletter form
        function handleSubscribe(e) {
            e.preventDefault();
            const email = e.target.querySelector('input').value;
            alert('感谢订阅！我们会定期发送露营攻略到 ' + email);
            e.target.reset();
        }

        // Close mobile menu when clicking a link
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                document.querySelector('.nav-links').classList.remove('active');
            });
        });
    </script>
</body>
</html>
