<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Los Santos RP — Лучший Role Play сервер GTA 5</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #0a0a0a;
            color: #fff;
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Видео-фон */
        .video-background {
            position: fixed;
            right: 0;
            bottom: 0;
            min-width: 100%;
            min-height: 100%;
            z-index: -1;
            filter: brightness(0.3);
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1920 1080"><rect fill="%231a1a2e" width="1920" height="1080"/><circle fill="%23e94560" cx="200" cy="300" r="3"/><circle fill="%23e94560" cx="1800" cy="400" r="2"/><circle fill="%230f3460" cx="1600" cy="200" r="4"/></svg>') center/cover;
        }

        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(233, 69, 96, 0.1), rgba(15, 52, 96, 0.2));
            z-index: -1;
            backdrop-filter: blur(2px);
        }

        /* Навигация */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 50px;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 2px solid #e94560;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .logo {
            font-size: 28px;
            font-weight: 800;
            color: #e94560;
            text-transform: uppercase;
            letter-spacing: 3px;
            text-shadow: 2px 2px 10px rgba(233, 69, 96, 0.7);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            font-size: 16px;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .nav-links a:hover {
            color: #e94560;
            text-shadow: 0 0 15px rgba(233, 69, 96, 0.5);
        }

        /* Главный блок */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            margin-top: 60px;
            position: relative;
            z-index: 2;
        }

        .hero-content {
            background: rgba(0, 0, 0, 0.7);
            padding: 50px;
            border-radius: 15px;
            border: 1px solid rgba(233, 69, 96, 0.3);
            backdrop-filter: blur(10px);
            box-shadow: 0 0 50px rgba(233, 69, 96, 0.2);
        }

        .hero h1 {
            font-size: 60px;
            color: #e94560;
            text-transform: uppercase;
            letter-spacing: 5px;
            margin-bottom: 20px;
            text-shadow: 0 0 30px rgba(233, 69, 96, 0.7);
        }

        .hero .subtitle {
            font-size: 24px;
            color: #fff;
            margin-bottom: 30px;
            letter-spacing: 2px;
        }

        .cta-button {
            display: inline-block;
            padding: 15px 40px;
            background: linear-gradient(45deg, #e94560, #c23152);
            color: white;
            text-decoration: none;
            font-weight: 700;
            font-size: 18px;
            border-radius: 8px;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            box-shadow: 0 5px 25px rgba(233, 69, 96, 0.5);
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 40px rgba(233, 69, 96, 0.8);
            background: linear-gradient(45deg, #c23152, #e94560);
        }

        /* Статистика сервера */
        .server-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin: 30px 0;
            flex-wrap: wrap;
        }

        .stat-item {
            background: rgba(233, 69, 96, 0.1);
            padding: 20px 30px;
            border-radius: 10px;
            border: 1px solid #e94560;
            text-align: center;
            transition: all 0.3s ease;
        }

        .stat-item:hover {
            background: rgba(233, 69, 96, 0.2);
            transform: scale(1.05);
        }

        .stat-number {
            font-size: 32px;
            font-weight: 800;
            color: #e94560;
            display: block;
        }

        .stat-label {
            font-size: 14px;
            color: #ccc;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Разделы */
        .section {
            padding: 80px 20px;
            position: relative;
            z-index: 2;
        }

        .section h2 {
            font-size: 42px;
            text-align: center;
            color: #e94560;
            margin-bottom: 50px;
            text-transform: uppercase;
            letter-spacing: 3px;
            text-shadow: 0 0 20px rgba(233, 69, 96, 0.3);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Карточки фракций */
        .faction-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .faction-card {
            background: rgba(20, 20, 30, 0.9);
            padding: 30px;
            border-radius: 12px;
            text-align: center;
            border: 1px solid rgba(233, 69, 96, 0.2);
            transition: all 0.3s ease;
            backdrop-filter: blur(5px);
        }

        .faction-card:hover {
            border-color: #e94560;
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(233, 69, 96, 0.2);
        }

        .faction-icon {
            font-size: 50px;
            margin-bottom: 20px;
        }

        .faction-card h3 {
            color: #e94560;
            margin-bottom: 15px;
            font-size: 24px;
            text-transform: uppercase;
        }

        /* Правила */
        .rules-list {
            background: rgba(20, 20, 30, 0.9);
            padding: 40px;
            border-radius: 15px;
            border: 1px solid rgba(233, 69, 96, 0.2);
            backdrop-filter: blur(5px);
        }

        .rule-item {
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: flex-start;
            gap: 20px;
        }

        .rule-number {
            font-size: 28px;
            font-weight: 800;
            color: #e94560;
            min-width: 40px;
        }

        /* Форма заявки */
        .application-form {
            background: rgba(20, 20, 30, 0.9);
            padding: 40px;
            border-radius: 15px;
            border: 1px solid rgba(233, 69, 96, 0.2);
            backdrop-filter: blur(10px);
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            color: #e94560;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .form-group input, .form-group textarea, .form-group select {
            width: 100%;
            padding: 12px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(233, 69, 96, 0.3);
            border-radius: 5px;
            color: white;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
            outline: none;
            border-color: #e94560;
            box-shadow: 0 0 15px rgba(233, 69, 96, 0.3);
            background: rgba(255, 255, 255, 0.1);
        }

        .form-group textarea {
            height: 100px;
            resize: vertical;
        }

        .submit-btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(45deg, #e94560, #c23152);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 18px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 2px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .submit-btn:hover {
            background: linear-gradient(45deg, #c23152, #e94560);
            box-shadow: 0 10px 30px rgba(233, 69, 96, 0.5);
        }

        /* Футер */
        footer {
            background: rgba(0, 0, 0, 0.9);
            text-align: center;
            padding: 30px;
            border-top: 2px solid #e94560;
            color: #ccc;
            position: relative;
            z-index: 2;
        }

        .social-links {
            margin: 20px 0;
        }

        .social-links a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            font-size: 24px;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            color: #e94560;
            text-shadow: 0 0 15px rgba(233, 69, 96, 0.5);
        }

        /* Анимации */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        /* Мобильная адаптация */
        @media (max-width: 768px) {
            nav {
                flex-direction: column;
                padding: 15px;
            }
            .nav-links {
                gap: 15px;
                margin-top: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            .hero h1 {
                font-size: 36px;
            }
            .server-stats {
                gap: 15px;
            }
            .section h2 {
                font-size: 30px;
            }
        }
    </style>
</head>
<body>
    <div class="video-background"></div>
    <div class="overlay"></div>

    <!-- Навигация -->
    <nav>
        <div class="logo">Los Santos RP</div>
        <ul class="nav-links">
            <li><a href="#home">Главная</a></li>
            <li><a href="#factions">Фракции</a></li>
            <li><a href="#rules">Правила</a></li>
            <li><a href="#apply">Подать заявку</a></li>
            <li><a href="#contact">Контакты</a></li>
        </ul>
    </nav>

    <!-- Главный экран -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Los Santos Role Play</h1>
            <p class="subtitle">Погрузись в мир криминала и возможностей</p>
            <div class="server-stats">
                <div class="stat-item">
                    <span class="stat-number" id="onlineCount">247</span>
                    <span class="stat-label">Игроков онлайн</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">5</span>
                    <span class="stat-label">Фракций</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">24/7</span>
                    <span class="stat-label">Аптайм</span>
                </div>
            </div>
            <a href="#apply" class="cta-button pulse">Начать играть</a>
            <div style="margin-top: 20px; color: #ccc; font-size: 14px;">
                IP: play.lossantosrp.ru | Discord: discord.gg/ls-rp
            </div>
        </div>
    </section>

    <!-- Фракции -->
    <section id="factions" class="section">
        <div class="container">
            <h2>Фракции сервера</h2>
            <div class="faction-grid">
                <div class="faction-card">
                    <div class="faction-icon">👮</div>
                    <h3>LSPD</h3>
                    <p>Полиция Лос-Сантоса. Защищайте закон и порядок на улицах города.</p>
                </div>
                <div class="faction-card">
                    <div class="faction-icon">🏥</div>
                    <h3>EMS</h3>
                    <p>Скорая помощь. Спасайте жизни и помогайте гражданам.</p>
                </div>
                <div class="faction-card">
                    <div class="faction-icon">🔧</div>
                    <h3>Механики</h3>
                    <p>Автосервис по всему городу. Чините и тюнингуйте автомобили.</p>
                </div>
                <div class="faction-card">
                    <div class="faction-icon">💰</div>
                    <h3>Мафия</h3>
                    <p>Криминальная организация. Контролируйте бизнес и территорию.</p>
                </div>
                <div class="faction-card">
                    <div class="faction-icon">📰</div>
                    <h3>Weazel News</h3>
                    <p>Новости города. Освещайте события и берите интервью.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Правила -->
    <section id="rules" class="section">
        <div class="container">
            <h2>Правила сервера</h2>
            <div class="rules-list">
                <div class="rule-item">
                    <span class="rule-number">1</span>
                    <div>
                        <h3>Role Play (RP) режим</h3>
                        <p>Всегда находитесь в роли своего персонажа. NonRP поведение строго запрещено.</p>
                    </div>
                </div>
                <div class="rule-item">
                    <span class="rule-number">2</span>
                    <div>
                        <h3>Запрещены читы и моды</h3>
                        <p>Использование стороннего ПО карается перманентным баном без права разбана.</p>
                    </div>
                </div>
                <div class="rule-item">
                    <span class="rule-number">3</span>
                    <div>
                        <h3>Уважение к игрокам</h3>
                        <p>Оскорбления, токсичное поведение и дискриминация строго запрещены.</p>
                    </div>
                </div>
                <div class="rule-item">
                    <span class="rule-number">4</span>
                    <div>
                        <h3>Реалистичное поведение</h3>
                        <p>Все действия должны быть приближены к реальной жизни. Никаких нереалистичных трюков.</p>
                    </div>
                </div>
                <div class="rule-item">
                    <span class="rule-number">5</span>
                    <div>
                        <h3>Запрет метагейминга</h3>
                        <p>Использование информации из реального мира в игре строго запрещено.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Форма заявки -->
    <section id="apply" class="section">
        <div class="container">
            <h2>Подать заявку на вступление</h2>
            <div class="application-form">
                <form id="applyForm">
                    <div class="form-group">
                        <label>Ваш никнейм</label>
                        <input type="text" placeholder="Например: John_Doe" required>
                    </div>
                    <div class="form-group">
                        <label>Возраст</label>
                        <input type="number" placeholder="Минимум 16 лет" min="16" required>
                    </div>
                    <div class="form-group">
                        <label>Опыт в RP</label>
                        <select required>
                            <option value="">Выберите...</option>
                            <option>Нет опыта</option>
                            <option>Менее 100 часов</option>
                            <option>100-500 часов</option>
                            <option>Более 500 часов</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Желаемая фракция</label>
                        <select required>
                            <option value="">Выберите фракцию...</option>
                            <option>LSPD</option>
                            <option>EMS</option>
                            <option>Механики</option>
                            <option>Мафия</option>
                            <option>Weazel News</option>
                            <option>Гражданский</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Расскажите о себе</label>
                        <textarea placeholder="Опишите свой опыт, почему хотите играть у нас..." required></textarea>
                    </div>
                    <button type="submit" class="submit-btn">Отправить заявку</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Футер -->
    <footer id="contact">
        <div class="container">
            <h3 style="color: #e94560; font-size: 24px;">Los Santos RP</h3>
            <p>Лучший Role Play сервер GTA 5 в СНГ</p>
            <div class="social-links">
                <a href="#" title="Discord">💬</a>
                <a href="#" title="YouTube">▶️</a>
                <a href="#" title="ВКонтакте">📱</a>
                <a href="#" title="Telegram">✈️</a>
            </div>
            <p style="margin-top: 20px;">© 2024 Los Santos Role Play. Все права защищены.</p>
            <p style="color: #888; font-size: 12px;">Данный сайт является фанатским проектом и не связан с Rockstar Games.</p>
        </div>
    </footer>

    <script>
        // Анимация счетчика игроков
        function updateOnlineCount() {
            const countElement = document.getElementById('onlineCount');
            if (countElement) {
                const baseCount = 200;
                const randomAddition = Math.floor(Math.random() * 100);
                countElement.textContent = baseCount + randomAddition;
                countElement.style.transform = 'scale(1.1)';
                setTimeout(() => {
                    countElement.style.transform = 'scale(1)';
                }, 200);
            }
        }

        // Обновляем счетчик каждые 10 секунд
        setInterval(updateOnlineCount, 10000);

        // Плавный скролл для навигации
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Обработка формы заявки
        document.getElementById('applyForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Простая валидация
            const inputs = this.querySelectorAll('input, textarea, select');
            let isValid = true;
            
            inputs.forEach(input => {
                if (!input.value) {
                    isValid = false;
                    input.style.borderColor = '#ff4444';
                } else {
                    input.style.borderColor = 'rgba(233, 69, 96, 0.3)';
                }
            });
            
            if (isValid) {
                // Имитация отправки
                const submitBtn = this.querySelector('.submit-btn');
                const originalText = submitBtn.textContent;
                submitBtn.textContent = 'Отправка...';
                submitBtn.disabled = true;
                
                setTimeout(() => {
                    alert('✅ Заявка успешно отправлена! Мы рассмотрим её в течение 24 часов. Проверьте Discord для связи.');
                    submitBtn.textContent = originalText;
                    submitBtn.disabled = false;
                    this.reset();
                }, 1500);
            } else {
                alert('❌ Пожалуйста, заполните все обязательные поля!');
            }
        });

        // Эффект появления при скролле
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.faction-card, .rule-item, .stat-item').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
