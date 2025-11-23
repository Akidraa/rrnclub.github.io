<!doctype html>
<html lang="ru">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>RRNCLUB - AI Digital Creator</title>
  <script src="/_sdk/element_sdk.js"></script>
  <style>
    body {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: #000000;
      color: #ffffff;
      overflow-x: hidden;
    }
    
    *, *::before, *::after {
      box-sizing: border-box;
    }
    
    html, body {
      height: 100%;
    }
    
    /* Hero Section */
    .hero {
      position: relative;
      min-height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 80px 24px;
      overflow: hidden;
    }
    
    .hero-bg {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
    }
    
    .ai-grid {
      position: absolute;
      width: 100%;
      height: 100%;
      background: 
        linear-gradient(90deg, rgba(99, 102, 241, 0.25) 1px, transparent 1px),
        linear-gradient(rgba(99, 102, 241, 0.25) 1px, transparent 1px);
      background-size: 50px 50px;
      animation: gridMove 20s linear infinite;
      opacity: 0.5;
    }
    
    @keyframes gridMove {
      0% { transform: translate(0, 0); }
      100% { transform: translate(50px, 50px); }
    }
    
    .ai-orbs {
      position: absolute;
      width: 100%;
      height: 100%;
    }
    
    .orb {
      position: absolute;
      border-radius: 50%;
      filter: blur(60px);
      animation: float 8s ease-in-out infinite;
    }
    
    .orb1 {
      width: 300px;
      height: 300px;
      background: radial-gradient(circle, rgba(99, 102, 241, 0.4), transparent);
      top: 20%;
      left: 10%;
      animation-delay: 0s;
    }
    
    .orb2 {
      width: 250px;
      height: 250px;
      background: radial-gradient(circle, rgba(168, 85, 247, 0.4), transparent);
      bottom: 20%;
      right: 15%;
      animation-delay: 2s;
    }
    
    .orb3 {
      width: 200px;
      height: 200px;
      background: radial-gradient(circle, rgba(59, 130, 246, 0.3), transparent);
      top: 50%;
      right: 30%;
      animation-delay: 4s;
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0) scale(1); }
      50% { transform: translateY(-30px) scale(1.1); }
    }
    
    /* Animated Particles Canvas */
    #particles-canvas {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
    }
    
    /* AI Neural Lines */
    .neural-network {
      position: absolute;
      width: 100%;
      height: 100%;
      z-index: 2;
      pointer-events: none;
    }
    
    .neural-line {
      position: absolute;
      background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.8), transparent);
      height: 2px;
      box-shadow: 0 0 10px rgba(99, 102, 241, 0.6);
      animation: neuralPulse 4s ease-in-out infinite;
    }
    
    @keyframes neuralPulse {
      0%, 100% { 
        opacity: 0.2;
        transform: scaleX(0.8);
      }
      50% { 
        opacity: 0.6;
        transform: scaleX(1);
      }
    }
    
    /* 3D AI Brain */
    .ai-brain-container {
      position: absolute;
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      perspective: 1000px;
      z-index: 0;
      opacity: 0.6;
    }
    
    .ai-brain {
      position: relative;
      width: 400px;
      height: 400px;
      transform-style: preserve-3d;
      animation: brainRotate 20s linear infinite;
    }
    
    @keyframes brainRotate {
      0% { transform: rotateX(0deg) rotateY(0deg); }
      100% { transform: rotateX(360deg) rotateY(360deg); }
    }
    
    .brain-node {
      position: absolute;
      width: 12px;
      height: 12px;
      background: radial-gradient(circle, rgba(99, 102, 241, 1), rgba(168, 85, 247, 0.6));
      border-radius: 50%;
      box-shadow: 
        0 0 20px rgba(99, 102, 241, 0.8),
        0 0 40px rgba(99, 102, 241, 0.4);
      animation: nodePulse 2s ease-in-out infinite;
    }
    
    @keyframes nodePulse {
      0%, 100% { 
        transform: scale(1);
        opacity: 1;
      }
      50% { 
        transform: scale(1.3);
        opacity: 0.7;
      }
    }
    
    .brain-connection {
      position: absolute;
      height: 1px;
      background: linear-gradient(90deg, 
        rgba(99, 102, 241, 0.6), 
        rgba(168, 85, 247, 0.6));
      transform-origin: left center;
      box-shadow: 0 0 5px rgba(99, 102, 241, 0.6);
      animation: connectionPulse 3s ease-in-out infinite;
    }
    
    @keyframes connectionPulse {
      0%, 100% { opacity: 0.3; }
      50% { opacity: 0.8; }
    }
    
    .hero-content {
      position: relative;
      z-index: 1;
      max-width: 900px;
    }
    
    .hero h1 {
      font-size: 96px;
      font-weight: 800;
      margin: 0 0 24px 0;
      background: linear-gradient(135deg, #ffffff 0%, #a855f7 50%, #6366f1 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: -2px;
      position: relative;
      display: inline-block;
    }
    
    .hero h1::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(135deg, #ffffff 0%, #a855f7 50%, #6366f1 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      filter: blur(20px);
      opacity: 0.8;
      animation: neonPulse 2s ease-in-out infinite;
    }
    
    .hero h1::after {
      content: '';
      position: absolute;
      right: -4px;
      top: 0;
      width: 4px;
      height: 100%;
      background: linear-gradient(to bottom, transparent, #6366f1, transparent);
      animation: blink 1s step-end infinite, fadeOutCursor 0.5s ease-in-out 3.5s forwards;
    }
    
    .typing-text {
      overflow: hidden;
      white-space: nowrap;
      border-right: 4px solid #6366f1;
      animation: typing 2.5s steps(7) 0.5s forwards, removeBorder 0s 3s forwards;
      width: 0;
    }
    
    @keyframes typing {
      from { width: 0; }
      to { width: 100%; }
    }
    
    @keyframes blink {
      50% { opacity: 0; }
    }
    
    @keyframes fadeOutCursor {
      to { opacity: 0; }
    }
    
    @keyframes removeBorder {
      to { border-right: none; }
    }
    
    @keyframes neonPulse {
      0%, 100% { 
        filter: blur(20px) brightness(1);
        opacity: 0.6;
      }
      50% { 
        filter: blur(25px) brightness(1.5);
        opacity: 0.9;
      }
    }
    
    .hero p {
      font-size: 24px;
      margin: 0 0 48px 0;
      color: #d1d5db;
      font-weight: 300;
      line-height: 1.6;
      opacity: 0;
      animation: fadeInUp 1s ease-out 3s forwards;
    }
    
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    .cta-button {
      display: inline-block;
      padding: 18px 48px;
      font-size: 18px;
      font-weight: 600;
      color: #ffffff;
      background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
      border: none;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s ease;
      text-decoration: none;
      box-shadow: 0 8px 32px rgba(99, 102, 241, 0.3);
      opacity: 0;
      animation: fadeInUp 1s ease-out 3.5s forwards;
      position: relative;
      overflow: hidden;
    }
    
    .cta-button::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
      transition: left 0.5s ease;
    }
    
    .cta-button:hover::before {
      left: 100%;
    }
    
    .cta-button:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 48px rgba(99, 102, 241, 0.5);
    }
    
    /* Section Styles */
    section {
      padding: 120px 24px;
      max-width: 1200px;
      margin: 0 auto;
    }
    
    .section-title {
      font-size: 56px;
      font-weight: 700;
      margin: 0 0 64px 0;
      text-align: center;
      background: linear-gradient(135deg, #ffffff 0%, #6366f1 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    
    /* About Section */
    .about-content {
      display: flex;
      align-items: center;
      gap: 64px;
      flex-wrap: wrap;
    }
    
    .avatar-container {
      flex: 0 0 200px;
      margin: 0 auto;
    }
    
    .avatar {
      width: 200px;
      height: 200px;
      border-radius: 50%;
      background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 80px;
      box-shadow: 0 16px 64px rgba(99, 102, 241, 0.4);
      animation: avatarPulse 3s ease-in-out infinite;
    }
    
    @keyframes avatarPulse {
      0%, 100% { box-shadow: 0 16px 64px rgba(99, 102, 241, 0.4); }
      50% { box-shadow: 0 16px 64px rgba(168, 85, 247, 0.6); }
    }
    
    .about-text {
      flex: 1;
      min-width: 300px;
    }
    
    .about-text p {
      font-size: 20px;
      line-height: 1.8;
      color: #d1d5db;
      margin: 0;
    }
    
    /* Services Section */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 32px;
    }
    
    .service-card {
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(99, 102, 241, 0.2);
      border-radius: 16px;
      padding: 40px 32px;
      text-align: center;
      transition: all 0.3s ease;
      backdrop-filter: blur(10px);
    }
    
    .service-card:hover {
      background: rgba(255, 255, 255, 0.05);
      border-color: rgba(99, 102, 241, 0.5);
      transform: translateY(-8px);
      box-shadow: 0 16px 48px rgba(99, 102, 241, 0.2);
    }
    
    .service-icon {
      width: 80px;
      height: 80px;
      margin: 0 auto 24px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 40px;
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.2) 0%, rgba(168, 85, 247, 0.2) 100%);
      border-radius: 16px;
    }
    
    .service-card h3 {
      font-size: 24px;
      margin: 0 0 16px 0;
      color: #ffffff;
    }
    
    .service-card p {
      font-size: 16px;
      color: #9ca3af;
      margin: 0;
      line-height: 1.6;
    }
    
    /* Portfolio Section */
    .portfolio-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 32px;
    }
    
    .portfolio-item {
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(99, 102, 241, 0.2);
      border-radius: 16px;
      overflow: hidden;
      transition: all 0.3s ease;
    }
    
    .portfolio-item:hover {
      border-color: rgba(99, 102, 241, 0.5);
      transform: translateY(-8px);
      box-shadow: 0 16px 48px rgba(99, 102, 241, 0.2);
    }
    
    .portfolio-image {
      width: 100%;
      height: 200px;
      background: linear-gradient(135deg, #1e1b4b 0%, #312e81 50%, #4c1d95 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 64px;
      position: relative;
      overflow: hidden;
    }
    
    .portfolio-image::before {
      content: '';
      position: absolute;
      width: 100%;
      height: 100%;
      background: 
        repeating-linear-gradient(
          0deg,
          transparent,
          transparent 2px,
          rgba(99, 102, 241, 0.1) 2px,
          rgba(99, 102, 241, 0.1) 4px
        );
      animation: scanline 8s linear infinite;
    }
    
    @keyframes scanline {
      0% { transform: translateY(0); }
      100% { transform: translateY(20px); }
    }
    
    .portfolio-content {
      padding: 24px;
    }
    
    .portfolio-content h3 {
      font-size: 20px;
      margin: 0 0 12px 0;
      color: #ffffff;
    }
    
    .portfolio-content p {
      font-size: 14px;
      color: #9ca3af;
      margin: 0;
      line-height: 1.6;
    }
    
    /* Contact Section */
    .contact-content {
      max-width: 600px;
      margin: 0 auto;
      text-align: center;
    }
    
    .contact-methods {
      display: flex;
      flex-direction: column;
      gap: 24px;
      margin-bottom: 48px;
    }
    
    .contact-item {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 16px;
      padding: 24px;
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(99, 102, 241, 0.2);
      border-radius: 12px;
      transition: all 0.3s ease;
    }
    
    .contact-item:hover {
      background: rgba(255, 255, 255, 0.05);
      border-color: rgba(99, 102, 241, 0.5);
    }
    
    .contact-icon {
      font-size: 32px;
    }
    
    .contact-item span {
      font-size: 20px;
      color: #d1d5db;
    }
    
    .order-form {
      margin-top: 48px;
      padding: 40px;
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(99, 102, 241, 0.2);
      border-radius: 16px;
      backdrop-filter: blur(10px);
    }
    
    .method-button {
      padding: 14px 32px;
      background: rgba(255, 255, 255, 0.05);
      border: 2px solid rgba(99, 102, 241, 0.3);
      border-radius: 8px;
      color: #d1d5db;
      font-size: 16px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.3s ease;
      font-family: inherit;
    }
    
    .method-button:hover {
      background: rgba(255, 255, 255, 0.08);
      border-color: rgba(99, 102, 241, 0.5);
    }
    
    .method-button.active {
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.3) 0%, rgba(168, 85, 247, 0.3) 100%);
      border-color: #6366f1;
      color: #ffffff;
    }
    
    /* Navigation */
    nav {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      background: rgba(0, 0, 0, 0.8);
      backdrop-filter: blur(10px);
      padding: 20px 24px;
      z-index: 100;
      border-bottom: 1px solid rgba(99, 102, 241, 0.2);
    }
    
    nav ul {
      list-style: none;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      gap: 48px;
      flex-wrap: wrap;
    }
    
    nav a {
      color: #d1d5db;
      text-decoration: none;
      font-size: 16px;
      font-weight: 500;
      transition: color 0.3s ease;
    }
    
    nav a:hover {
      color: #6366f1;
    }
    
    /* Responsive */
    @media (max-width: 768px) {
      .hero h1 {
        font-size: 56px;
      }
      
      .hero p {
        font-size: 18px;
      }
      
      .section-title {
        font-size: 40px;
      }
      
      section {
        padding: 80px 24px;
      }
      
      .about-content {
        flex-direction: column;
        text-align: center;
      }
      
      nav ul {
        gap: 24px;
      }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <nav>
   <ul>
    <li><a href="#hero">Главная</a></li>
    <li><a href="#about">Обо мне</a></li>
    <li><a href="#services">Услуги</a></li>
    <li><a href="#portfolio">Портфолио</a></li>
    <li><a href="#contact">Контакты</a></li>
   </ul>
  </nav>
  <section id="hero" class="hero">
   <div class="hero-bg">
    <div class="ai-brain-container" id="ai-brain-container"></div>
    <canvas id="particles-canvas"></canvas>
    <div class="neural-network" id="neural-network"></div>
    <div class="ai-grid"></div>
    <div class="ai-orbs">
     <div class="orb orb1"></div>
     <div class="orb orb2"></div>
     <div class="orb orb3"></div>
    </div>
   </div>
   <div class="hero-content">
    <h1 id="hero-title" class="typing-text">RRNCLUB</h1>
    <p id="hero-subtitle">Создаю визуалы, тексты и мини-программы на базе ИИ</p><a href="#contact" class="cta-button">Связаться</a>
   </div>
  </section>
  <section id="about">
   <h2 class="section-title" id="about-title">Обо мне</h2>
   <div class="about-content">
    <div class="avatar-container">
     <div class="avatar">
      🤖
     </div>
    </div>
    <div class="about-text">
     <p id="about-description">Я создаю проекты с использованием искусственного интеллекта: визуалы, текстовые материалы, автоматизации и мини-приложения, включая Telegram-ботов</p>
    </div>
   </div>
  </section>
  <section id="services">
   <h2 class="section-title" id="services-title">Услуги</h2>
   <div class="services-grid">
    <div class="service-card">
     <div class="service-icon">
      🎨
     </div>
     <h3>Создание AI-визуалов</h3>
     <p>Уникальные изображения и графика, созданные с помощью нейросетей</p>
    </div>
    <div class="service-card">
     <div class="service-icon">
      📝
     </div>
     <h3>Генерация текстов</h3>
     <p>Качественный контент для ваших проектов и социальных сетей</p>
    </div>
    <div class="service-card">
     <div class="service-icon">
      💻
     </div>
     <h3>Создание мини-программ</h3>
     <p>Автоматизация процессов и разработка полезных инструментов</p>
    </div>
    <div class="service-card">
     <div class="service-icon">
      🤖
     </div>
     <h3>Разработка Telegram-ботов</h3>
     <p>Умные боты для автоматизации бизнеса и общения</p>
    </div>
   </div>
  </section>
  <section id="portfolio">
   <h2 class="section-title" id="portfolio-title">Портфолио</h2>
   <div class="portfolio-grid">
    <div class="portfolio-item">
     <div class="portfolio-image">
      🎨
     </div>
     <div class="portfolio-content">
      <h3>AI-визуалы для соцсетей</h3>
      <p>Серия уникальных изображений для Instagram и других платформ</p>
     </div>
    </div>
    <div class="portfolio-item">
     <div class="portfolio-image">
      💬
     </div>
     <div class="portfolio-content">
      <h3>Telegram-бот поддержки</h3>
      <p>Автоматизированная система обработки запросов клиентов</p>
     </div>
    </div>
    <div class="portfolio-item">
     <div class="portfolio-image">
      📊
     </div>
     <div class="portfolio-content">
      <h3>Мини-приложение аналитики</h3>
      <p>Инструмент для анализа данных и визуализации результатов</p>
     </div>
    </div>
    <div class="portfolio-item">
     <div class="portfolio-image">
      🎬
     </div>
     <div class="portfolio-content">
      <h3>AI-контент для видео</h3>
      <p>Генерация сценариев и визуальных концепций для видеопроектов</p>
     </div>
    </div>
   </div>
  </section>
  <section id="contact">
   <h2 class="section-title" id="contact-title">Контакты</h2>
   <div class="contact-content">
    <div class="contact-methods"><a href="https://t.me/RRNCLUB" target="_blank" rel="noopener noreferrer" style="text-decoration: none;">
      <div class="contact-item">
       <div class="contact-icon">
        📱
       </div><span id="contact-telegram">RRNCLUB</span>
      </div></a> <a href="mailto:rrnclub@gmail.com" style="text-decoration: none;">
      <div class="contact-item">
       <div class="contact-icon">
        📧
       </div><span id="contact-email">rrnclub@gmail.com</span>
      </div></a>
    </div>
    <div class="order-form" id="orderForm">
     <h3 style="margin: 0 0 32px 0; color: #ffffff; font-size: 28px; text-align: center;">Заказать проект</h3>
     <div style="margin-bottom: 24px;"><label for="clientName" style="display: block; margin-bottom: 8px; color: #d1d5db; font-size: 14px; font-weight: 500;">Ваше имя</label> <input type="text" id="clientName" placeholder="Как к вам обращаться?" style="width: 100%; padding: 14px 16px; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(99, 102, 241, 0.3); border-radius: 8px; color: #ffffff; font-size: 16px; font-family: inherit;">
     </div>
     <div style="margin-bottom: 24px;"><label style="display: block; margin-bottom: 8px; color: #d1d5db; font-size: 14px; font-weight: 500;">Тип проекта</label> <select id="projectType" style="width: 100%; padding: 14px 16px; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(99, 102, 241, 0.3); border-radius: 8px; color: #ffffff; font-size: 16px; font-family: inherit; cursor: pointer;"> <option value="">Выберите тип проекта</option> <option value="AI-визуалы">🎨 AI-визуалы</option> <option value="Генерация текстов">📝 Генерация текстов</option> <option value="Мини-программа">💻 Мини-программа</option> <option value="Telegram-бот">🤖 Telegram-бот</option> <option value="Комплексный проект">💼 Комплексный проект</option> <option value="Другое">💡 Другое</option> </select>
     </div>
     <div style="margin-bottom: 24px;"><label for="projectDescription" style="display: block; margin-bottom: 8px; color: #d1d5db; font-size: 14px; font-weight: 500;">Описание проекта</label> <textarea id="projectDescription" rows="5" placeholder="Расскажите подробнее о вашем проекте, задачах и желаемом результате..." style="width: 100%; padding: 14px 16px; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(99, 102, 241, 0.3); border-radius: 8px; color: #ffffff; font-size: 16px; font-family: inherit; resize: vertical; line-height: 1.5;"></textarea>
     </div>
     <div style="margin-bottom: 24px;"><label style="display: block; margin-bottom: 8px; color: #d1d5db; font-size: 14px; font-weight: 500;">Сроки выполнения</label> <select id="projectDeadline" style="width: 100%; padding: 14px 16px; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(99, 102, 241, 0.3); border-radius: 8px; color: #ffffff; font-size: 16px; font-family: inherit; cursor: pointer;"> <option value="">Выберите желаемые сроки</option> <option value="Срочно (1-3 дня)">⚡ Срочно (1-3 дня)</option> <option value="Быстро (3-7 дней)">🚀 Быстро (3-7 дней)</option> <option value="Стандартно (1-2 недели)">📅 Стандартно (1-2 недели)</option> <option value="Не срочно (2-4 недели)">⏰ Не срочно (2-4 недели)</option> <option value="Обсудим">💬 Обсудим</option> </select>
     </div>
     <div style="margin-bottom: 24px;"><label style="display: block; margin-bottom: 8px; color: #d1d5db; font-size: 14px; font-weight: 500;">Бюджет проекта</label> <select id="projectBudget" style="width: 100%; padding: 14px 16px; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(99, 102, 241, 0.3); border-radius: 8px; color: #ffffff; font-size: 16px; font-family: inherit; cursor: pointer;"> <option value="">Выберите примерный бюджет</option> <option value="До 5000₽">💰 До 5000₽</option> <option value="5000-15000₽">💵 5000-15000₽</option> <option value="15000-30000₽">💸 15000-30000₽</option> <option value="30000-50000₽">💎 30000-50000₽</option> <option value="Свыше 50000₽">👑 Свыше 50000₽</option> <option value="Обсудим">💬 Обсудим</option> </select>
     </div>
     <div style="margin-bottom: 32px; padding: 20px; background: rgba(99, 102, 241, 0.1); border: 1px solid rgba(99, 102, 241, 0.3); border-radius: 8px;"><label style="display: block; margin-bottom: 12px; color: #ffffff; font-size: 16px; font-weight: 600;">Способ связи:</label>
      <div style="display: flex; gap: 12px; flex-wrap: wrap;"><button class="method-button active" data-method="telegram" onclick="selectMethod('telegram')"> 📱 Telegram </button> <button class="method-button" data-method="email" onclick="selectMethod('email')"> 📧 Email </button>
      </div>
     </div><button class="cta-button" onclick="sendOrder()" style="width: 100%;"> Отправить заказ </button>
    </div>
   </div>
  </section>
  <script>
    const defaultConfig = {
      hero_title: "RRNCLUB",
      hero_subtitle: "Создаю визуалы, тексты и мини-программы на базе ИИ",
      about_title: "Обо мне",
      about_description: "Я создаю проекты с использованием искусственного интеллекта: визуалы, текстовые материалы, автоматизации и мини-приложения, включая Telegram-ботов",
      services_title: "Услуги",
      portfolio_title: "Портфолио",
      contact_title: "Контакты",
      contact_telegram: "RRNCLUB",
      contact_email: "rrnclub@gmail.com",
      background_color: "#000000",
      accent_color: "#6366f1",
      text_color: "#ffffff",
      font_family: "Inter",
      font_size: 16
    };

    async function onConfigChange(config) {
      const heroTitle = config.hero_title || defaultConfig.hero_title;
      const heroSubtitle = config.hero_subtitle || defaultConfig.hero_subtitle;
      const aboutTitle = config.about_title || defaultConfig.about_title;
      const aboutDescription = config.about_description || defaultConfig.about_description;
      const servicesTitle = config.services_title || defaultConfig.services_title;
      const portfolioTitle = config.portfolio_title || defaultConfig.portfolio_title;
      const contactTitle = config.contact_title || defaultConfig.contact_title;
      const contactTelegram = config.contact_telegram || defaultConfig.contact_telegram;
      const contactEmail = config.contact_email || defaultConfig.contact_email;
      const customFont = config.font_family || defaultConfig.font_family;
      const baseSize = config.font_size || defaultConfig.font_size;
      const baseFontStack = 'Inter, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif';
      
      document.getElementById('hero-title').textContent = heroTitle;
      document.getElementById('hero-subtitle').textContent = heroSubtitle;
      document.getElementById('about-title').textContent = aboutTitle;
      document.getElementById('about-description').textContent = aboutDescription;
      document.getElementById('services-title').textContent = servicesTitle;
      document.getElementById('portfolio-title').textContent = portfolioTitle;
      document.getElementById('contact-title').textContent = contactTitle;
      document.getElementById('contact-telegram').textContent = contactTelegram;
      document.getElementById('contact-email').textContent = contactEmail;
      
      document.body.style.fontFamily = `${customFont}, ${baseFontStack}`;
      document.getElementById('hero-title').style.fontSize = `${baseSize * 6}px`;
      document.getElementById('hero-subtitle').style.fontSize = `${baseSize * 1.5}px`;
      document.querySelectorAll('.section-title').forEach(el => {
        el.style.fontSize = `${baseSize * 3.5}px`;
      });
      document.querySelectorAll('.about-text p').forEach(el => {
        el.style.fontSize = `${baseSize * 1.25}px`;
      });
      document.querySelectorAll('.service-card h3').forEach(el => {
        el.style.fontSize = `${baseSize * 1.5}px`;
      });
      document.querySelectorAll('.service-card p').forEach(el => {
        el.style.fontSize = `${baseSize}px`;
      });
      document.querySelectorAll('.portfolio-content h3').forEach(el => {
        el.style.fontSize = `${baseSize * 1.25}px`;
      });
      document.querySelectorAll('.portfolio-content p').forEach(el => {
        el.style.fontSize = `${baseSize * 0.875}px`;
      });
      document.querySelectorAll('.contact-item span').forEach(el => {
        el.style.fontSize = `${baseSize * 1.25}px`;
      });
      document.querySelectorAll('nav a').forEach(el => {
        el.style.fontSize = `${baseSize}px`;
      });
      document.querySelectorAll('.cta-button').forEach(el => {
        el.style.fontSize = `${baseSize * 1.125}px`;
      });
    }

    let selectedMethod = 'telegram';
    
    function selectMethod(method) {
      selectedMethod = method;
      document.querySelectorAll('.method-button').forEach(btn => {
        btn.classList.remove('active');
      });
      document.querySelector(`[data-method="${method}"]`).classList.add('active');
    }
    
    function sendOrder() {
      const name = document.getElementById('clientName').value.trim();
      const projectType = document.getElementById('projectType').value;
      const description = document.getElementById('projectDescription').value.trim();
      const deadline = document.getElementById('projectDeadline').value;
      const budget = document.getElementById('projectBudget').value;
      
      if (!description) {
        showNotification('Пожалуйста, опишите ваш проект');
        return;
      }
      
      let message = '📋 ЗАКАЗ ПРОЕКТА\n\n';
      
      if (name) {
        message += `👤 Имя: ${name}\n`;
      }
      
      if (projectType) {
        message += `📦 Тип проекта: ${projectType}\n`;
      }
      
      if (deadline) {
        message += `⏱️ Сроки: ${deadline}\n`;
      }
      
      if (budget) {
        message += `💰 Бюджет: ${budget}\n`;
      }
      
      message += `\n📝 Описание:\n${description}`;
      
      if (selectedMethod === 'telegram') {
        const telegramUrl = `https://t.me/RRNCLUB?text=${encodeURIComponent(message)}`;
        window.open(telegramUrl, '_blank', 'noopener,noreferrer');
      } else {
        const emailSubject = 'Заказ проекта' + (projectType ? `: ${projectType}` : '');
        const emailBody = message.replace(/\n/g, '\r\n');
        const mailtoUrl = `mailto:rrnclub@gmail.com?subject=${encodeURIComponent(emailSubject)}&body=${encodeURIComponent(emailBody)}`;
        window.location.href = mailtoUrl;
      }
      
      showNotification('Переход к выбранному способу связи...');
      
      document.getElementById('clientName').value = '';
      document.getElementById('projectType').value = '';
      document.getElementById('projectDescription').value = '';
      document.getElementById('projectDeadline').value = '';
      document.getElementById('projectBudget').value = '';
    }
    
    function showNotification(text) {
      const notification = document.createElement('div');
      notification.textContent = text;
      notification.style.cssText = `
        position: fixed;
        bottom: 32px;
        left: 50%;
        transform: translateX(-50%);
        background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
        color: white;
        padding: 16px 32px;
        border-radius: 8px;
        font-size: 16px;
        z-index: 1000;
        box-shadow: 0 8px 32px rgba(99, 102, 241, 0.4);
        animation: slideUp 0.3s ease;
      `;
      document.body.appendChild(notification);
      
      setTimeout(() => {
        notification.style.animation = 'slideDown 0.3s ease';
        setTimeout(() => notification.remove(), 300);
      }, 3000);
    }
    
    const style = document.createElement('style');
    style.textContent = `
      @keyframes slideUp {
        from { transform: translateX(-50%) translateY(100px); opacity: 0; }
        to { transform: translateX(-50%) translateY(0); opacity: 1; }
      }
      @keyframes slideDown {
        from { transform: translateX(-50%) translateY(0); opacity: 1; }
        to { transform: translateX(-50%) translateY(100px); opacity: 0; }
      }
    `;
    document.head.appendChild(style);
    
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                config.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => config.accent_color || defaultConfig.accent_color,
              set: (value) => {
                config.accent_color = value;
                window.elementSdk.setConfig({ accent_color: value });
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                config.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => config.font_family || defaultConfig.font_family,
            set: (value) => {
              config.font_family = value;
              window.elementSdk.setConfig({ font_family: value });
            }
          },
          fontSizeable: {
            get: () => config.font_size || defaultConfig.font_size,
            set: (value) => {
              config.font_size = value;
              window.elementSdk.setConfig({ font_size: value });
            }
          }
        }),
        mapToEditPanelValues: (config) => new Map([
          ["hero_title", config.hero_title || defaultConfig.hero_title],
          ["hero_subtitle", config.hero_subtitle || defaultConfig.hero_subtitle],
          ["about_title", config.about_title || defaultConfig.about_title],
          ["about_description", config.about_description || defaultConfig.about_description],
          ["services_title", config.services_title || defaultConfig.services_title],
          ["portfolio_title", config.portfolio_title || defaultConfig.portfolio_title],
          ["contact_title", config.contact_title || defaultConfig.contact_title],
          ["contact_telegram", config.contact_telegram || defaultConfig.contact_telegram],
          ["contact_email", config.contact_email || defaultConfig.contact_email]
        ])
      });
    }
    
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
          target.scrollIntoView({ behavior: 'smooth' });
        }
      });
    });
    
    // Particle System
    const canvas = document.getElementById('particles-canvas');
    const ctx = canvas.getContext('2d');
    
    function resizeCanvas() {
      canvas.width = canvas.offsetWidth;
      canvas.height = canvas.offsetHeight;
    }
    
    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);
    
    const particles = [];
    const particleCount = 50;
    
    class Particle {
      constructor() {
        this.reset();
      }
      
      reset() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.vx = (Math.random() - 0.5) * 0.5;
        this.vy = (Math.random() - 0.5) * 0.5;
        this.size = Math.random() * 3 + 2;
        this.opacity = Math.random() * 0.5 + 0.4;
      }
      
      update() {
        this.x += this.vx;
        this.y += this.vy;
        
        if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
        if (this.y < 0 || this.y > canvas.height) this.vy *= -1;
      }
      
      draw() {
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(99, 102, 241, ${this.opacity * 2})`;
        ctx.shadowBlur = 10;
        ctx.shadowColor = 'rgba(99, 102, 241, 0.8)';
        ctx.fill();
        ctx.shadowBlur = 0;
      }
    }
    
    for (let i = 0; i < particleCount; i++) {
      particles.push(new Particle());
    }
    
    function connectParticles() {
      for (let i = 0; i < particles.length; i++) {
        for (let j = i + 1; j < particles.length; j++) {
          const dx = particles[i].x - particles[j].x;
          const dy = particles[i].y - particles[j].y;
          const distance = Math.sqrt(dx * dx + dy * dy);
          
          if (distance < 150) {
            ctx.beginPath();
            ctx.strokeStyle = `rgba(99, 102, 241, ${0.6 * (1 - distance / 150)})`;
            ctx.lineWidth = 1.5;
            ctx.moveTo(particles[i].x, particles[i].y);
            ctx.lineTo(particles[j].x, particles[j].y);
            ctx.stroke();
          }
        }
      }
    }
    
    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      
      particles.forEach(particle => {
        particle.update();
        particle.draw();
      });
      
      connectParticles();
      requestAnimationFrame(animateParticles);
    }
    
    animateParticles();
    
    // Neural Network Lines
    const neuralNetwork = document.getElementById('neural-network');
    const lineCount = 8;
    
    for (let i = 0; i < lineCount; i++) {
      const line = document.createElement('div');
      line.className = 'neural-line';
      line.style.width = `${Math.random() * 300 + 200}px`;
      line.style.top = `${Math.random() * 100}%`;
      line.style.left = `${Math.random() * 100}%`;
      line.style.transform = `rotate(${Math.random() * 360}deg)`;
      line.style.animationDelay = `${Math.random() * 4}s`;
      neuralNetwork.appendChild(line);
    }
    
    // 3D AI Brain
    const brainContainer = document.getElementById('ai-brain-container');
    const brain = document.createElement('div');
    brain.className = 'ai-brain';
    brainContainer.appendChild(brain);
    
    const nodePositions = [];
    const nodeCount = 30;
    const radius = 150;
    
    // Create brain nodes in 3D sphere
    for (let i = 0; i < nodeCount; i++) {
      const phi = Math.acos(-1 + (2 * i) / nodeCount);
      const theta = Math.sqrt(nodeCount * Math.PI) * phi;
      
      const x = radius * Math.cos(theta) * Math.sin(phi);
      const y = radius * Math.sin(theta) * Math.sin(phi);
      const z = radius * Math.cos(phi);
      
      nodePositions.push({ x, y, z });
      
      const node = document.createElement('div');
      node.className = 'brain-node';
      node.style.left = `${200 + x}px`;
      node.style.top = `${200 + y}px`;
      node.style.transform = `translateZ(${z}px)`;
      node.style.animationDelay = `${Math.random() * 2}s`;
      brain.appendChild(node);
    }
    
    // Create connections between nearby nodes
    for (let i = 0; i < nodePositions.length; i++) {
      for (let j = i + 1; j < nodePositions.length; j++) {
        const dx = nodePositions[j].x - nodePositions[i].x;
        const dy = nodePositions[j].y - nodePositions[i].y;
        const dz = nodePositions[j].z - nodePositions[i].z;
        const distance = Math.sqrt(dx * dx + dy * dy + dz * dz);
        
        if (distance < 120) {
          const connection = document.createElement('div');
          connection.className = 'brain-connection';
          
          const angle = Math.atan2(dy, dx);
          const avgZ = (nodePositions[i].z + nodePositions[j].z) / 2;
          
          connection.style.left = `${200 + nodePositions[i].x}px`;
          connection.style.top = `${200 + nodePositions[i].y}px`;
          connection.style.width = `${distance}px`;
          connection.style.transform = `translateZ(${avgZ}px) rotate(${angle}rad)`;
          connection.style.animationDelay = `${Math.random() * 3}s`;
          
          brain.appendChild(connection);
        }
      }
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a2f9127f57dfe93',t:'MTc2Mzg4OTM3OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
