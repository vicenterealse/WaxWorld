<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WaxWorld - Experiencia Wax Premium</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --color-primary: #364b8b;
            --color-secondary: #2f56cc;
            --color-background: #1a2035;
            --color-accent: #6a5acd;
            --color-text: #e0e0e0;
            --transition-speed: 0.3s;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', 'Trebuchet MS', sans-serif;
        }

        body {
            background-color: var(--color-background);
            color: var(--color-text);
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Modernized Navigation */
        .tab-container {
            display: flex;
            justify-content: center;
            background-color: rgba(54, 75, 139, 0.2);
            padding: 10px;
            border-radius: 50px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .tab {
            color: var(--color-text);
            padding: 12px 25px;
            margin: 0 10px;
            cursor: pointer;
            border-radius: 30px;
            transition: all var(--transition-speed) ease;
            font-weight: 600;
            position: relative;
            overflow: hidden;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .tab::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(120deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: all var(--transition-speed) ease;
        }

        .tab:hover::before {
            left: 100%;
        }

        .tab.active {
            background-color: var(--color-accent);
            color: white;
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(106, 90, 205, 0.4);
        }

        /* Tab Content Transitions */
        .tab-content {
            display: none;
            opacity: 0;
            visibility: hidden;
            transform: translateY(20px);
            transition: all 0.5s ease;
        }

        .tab-content.active {
            display: block;
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        /* Product Card Redesign */
        .productos {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 30px;
        }

        .producto {
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: all var(--transition-speed) ease;
            border: 1px solid rgba(255,255,255,0.1);
            position: relative;
            overflow: hidden;
        }

        .producto::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            transform: rotate(-45deg);
            opacity: 0;
            transition: all 0.5s ease;
        }

        .producto:hover::before {
            opacity: 1;
        }

        .producto:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(106, 90, 205, 0.2);
        }

        .producto img {
            max-width: 200px;
            height: 250px;
            object-fit: cover;
            border-radius: 10px;
            transition: transform 0.5s ease;
        }

        .producto:hover img {
            transform: scale(1.1);
        }

        .producto h3 {
            color: var(--color-text);
            margin-top: 15px;
        }

        .producto .overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(to bottom, transparent, var(--color-primary));
            overflow: hidden;
            width: 100%;
            height: 0;
            transition: 0.5s ease;
        }

        .producto:hover .overlay {
            height: 70px;
        }

        .overlay-text {
            color: white;
            font-size: 16px;
            position: absolute;
            bottom: 10px;
            left: 0;
            right: 0;
            text-align: center;
        }

        /* Gallery Improvements */
        .galeria {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .galeria-item {
            position: relative;
            border-radius: 15px;
            overflow: hidden;
            height: 350px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .galeria-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.7s ease;
        }

        .galeria-item:hover img {
            transform: scale(1.1) rotate(3deg);
        }

        /* Location Section */
        .ubicacion {
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 40px;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .ubicacion-detalles {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        /* Responsive Adjustments */
        @media (max-width: 768px) {
            .tab-container {
                flex-wrap: wrap;
            }

            .tab {
                margin: 5px;
            }

            .ubicacion-detalles {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="tab-container">
            <div class="tab active" data-tab="productos">
                <i class="fas fa-tags"></i> Deleite
            </div>
            <div class="tab" data-tab="galeria">
                <i class="fas fa-images"></i> Galería
            </div>
            <div class="tab" data-tab="ubicacion">
                <i class="fas fa-map-marker-alt"></i> Ubicación
            </div>
        </div>

        <!-- Productos Section -->
        <div id="productos" class="tab-content active">
            <div class="productos">
                <div class="producto">
                    <img src="/api/placeholder/200/250" alt="Pro Wax 2gr">
                    <div class="overlay">
                        <div class="overlay-text">Pro Wax 2gr - $89.50</div>
                    </div>
                    <h3>Pro Wax 2gr</h3>
                </div>
                <div class="producto">
                    <img src="/api/placeholder/200/250" alt="Pacman Wax 1gr">
                    <div class="overlay">
                        <div class="overlay-text">Pacman Wax 1gr - $89.50</div>
                    </div>
                    <h3>Pacman Wax 1gr</h3>
                </div>
                <div class="producto">
                    <img src="/api/placeholder/200/250" alt="Jungle Boys Wax">
                    <div class="overlay">
                        <div class="overlay-text">Jungle Boys Wax - $89.50</div>
                    </div>
                    <h3>Jungle Boys 2gr Wax</h3>
                </div>
                <div class="producto">
                    <img src="/api/placeholder/200/250" alt="Forest Wax 1gr">
                    <div class="overlay">
                        <div class="overlay-text">Forest Wax 1gr - $94.99</div>
                    </div>
                    <h3>Forest Wax 1gr</h3>

                </div>
            </div>
        </div>

        <!-- Gallery Section -->
        <div id="galeria" class="tab-content">
            <h2 style="text-align: center; margin: 20px 0; color: var(--color-text);">Nuestra Galería</h2>
            <div class="galeria">
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 1">
                </div>
                <!-- Rest of the gallery items remain the same -->
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
                <div class="galeria-item">
                    <img src="/api/placeholder/400/350" alt="Galería Wax 9">
                </div>
            </div>
        </div>

        <!-- Location Section -->
        <div id="ubicacion" class="tab-content">
            <div class="ubicacion">
                <h2 style="text-align: center; margin-bottom: 30px;">Nuestra Ubicación</h2>
                <div class="ubicacion-detalles">
                    <div>
                        <h3><i class="fas fa-map-marker-alt"></i> Dirección</h3>
                        <p>Centro Tulancingo Hidalgo Mexico</p>
                        <h3><i class="fas fa-phone"></i> Teléfono</h3>
                        <p>+52 932 202 42 06</p>
                        <h3><i class="fas fa-clock"></i> Horarios</h3>
                        <p>Lunes a Viernes: 10:00 - 20:00</p>
                        <p>Sábados: 11:00 - 18:00</p>
                        <h3><i class="fab fa-facebook"></i> Facebook</h3>
                        <a href="https://www.facebook.com/share/16ye36qvtE/?mibextid=LQQJ4d" 
                           target="_blank" 
                           style="color: var(--color-accent); text-decoration: none; display: inline-block; margin-top: 10px; padding: 8px 15px; background-color: rgba(106, 90, 205, 0.2); border-radius: 20px; transition: all 0.3s ease;">
                            Visita nuestra página
                        </a>
                    </div>
                    <iframe 
                        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d59952.02610743203!2d-98.3623626!3d20.09221865!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x85d055d656404d61%3A0x337451ab23113186!2sTulancingo%2C%20Hgo.!5e0!3m2!1ses-419!2smx!4v1732659515963!5m2!1ses-419!2smx" 
                        width="100%" 
                        height="450" 
                        style="border-radius: 15px; filter: grayscale(30%) brightness(70%);"
                        allowfullscreen="" 
                        loading="lazy" 
                        referrerpolicy="no-referrer-when-downgrade">
                    </iframe>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Enhanced Tab Functionality
        const tabs = document.querySelectorAll('.tab');
        const tabContents = document.querySelectorAll('.tab-content');

        tabs.forEach(tab => {
            tab.addEventListener('click', () => {
                const target = tab.getAttribute('data-tab');

                // Remove active class from all tabs and contents
                tabs.forEach(t => t.classList.remove('active'));
                tabContents.forEach(tc => tc.classList.remove('active'));

                // Add active class to selected tab and content
                tab.classList.add('active');
                document.getElementById(target).classList.add('active');

                // Optional: Add sound effect or subtle animation
                tab.style.transform = 'scale(1.05)';
                setTimeout(() => {
                    tab.style.transform = 'scale(1)';
                }, 200);
            });
        });
    </script>
</body>
</html>
