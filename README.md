<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TOPO EXACT | Servicios Topográficos y Geomática de Precisión</title>
    <!-- Carga de íconos FontAwesome -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary: #1e3a8a;    /* Azul corporativo */
            --secondary: #f59e0b;  /* Naranja/Amarillo topográfico */
            --dark: #1f2937;       /* Gris oscuro profesional */
            --light: #f3f4f6;      /* Fondo claro */
            --white: #ffffff;
            --gray: #4b5563;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        html { scroll-behavior: smooth; }
        body { background-color: var(--light); color: var(--dark); line-height: 1.6; }

        /* Encabezado y Menú de Navegación */
        header {
            background-color: var(--white);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 0.8rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-container img {
            height: 55px;
            width: auto;
            object-fit: contain;
        }

        nav { display: flex; align-items: center; gap: 1.2rem; }
        nav a { color: var(--dark); text-decoration: none; font-weight: 600; padding: 0.5rem; transition: color 0.3s; }
        nav a:hover { color: var(--secondary); }

        /* Menú Desplegable de Procesos */
        .dropdown { position: relative; display: inline-block; }
        .dropdown-button { color: var(--dark); text-decoration: none; font-weight: 600; padding: 0.5rem; cursor: pointer; }
        .dropdown-content {
            display: none;
            position: absolute;
            background-color: var(--white);
            min-width: 270px;
            box-shadow: 0px 8px 16px rgba(0,0,0,0.15);
            border-radius: 6px;
            top: 100%;
            left: 0;
            overflow: hidden;
        }
        .dropdown-content a { color: var(--dark); padding: 12px 16px; text-decoration: none; display: block; font-size: 0.9rem; border-bottom: 1px solid #f0f0f0; }
        .dropdown-content a:hover { background-color: var(--light); color: var(--primary); }
        .dropdown:hover .dropdown-content { display: block; }

        /* Portada / Hero */
        .hero {
            background: linear-gradient(rgba(30, 58, 138, 0.85), rgba(31, 41, 55, 0.85)), url('img/IMG-20240708-WA0017.jpg') center/cover no-repeat;
            color: var(--white);
            text-align: center;
            padding: 5rem 1rem;
        }

        .hero-logo-box { margin-bottom: 1.5rem; }
        .hero-logo-box img {
            max-width: 280px;
            height: auto;
            background: rgba(255, 255, 255, 0.95);
            padding: 10px 18px;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        .hero h1 { font-size: 2.5rem; margin-bottom: 0.5rem; font-weight: 800; }
        .hero p.slogan { font-size: 1.3rem; color: var(--secondary); font-weight: 700; margin-bottom: 2rem; letter-spacing: 1px; }

        .btn-whatsapp {
            display: inline-block;
            background-color: #25d366;
            color: white;
            padding: 0.9rem 1.8rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.05rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            transition: transform 0.2s, background 0.3s;
        }
        .btn-whatsapp:hover { transform: translateY(-3px); background-color: #128c7e; }

        /* Estructura Contenedora */
        .container { max-width: 1150px; margin: 3rem auto; padding: 0 1rem; }
        .section-title { text-align: center; margin-bottom: 2.5rem; color: var(--primary); font-size: 2rem; }

        /* Sección Quiénes Somos / Historia */
        .about-section {
            background: var(--white);
            border-radius: 10px;
            padding: 2.5rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            margin-bottom: 4rem;
        }

        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            align-items: center;
        }

        .about-text h2 { color: var(--primary); margin-bottom: 1rem; font-size: 1.8rem; }
        .about-text p { margin-bottom: 1rem; text-align: justify; color: var(--dark); }

        .about-img img {
            width: 100%;
            height: 350px;
            object-fit: cover;
            border-radius: 8px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.15);
        }

        /* Línea de Tiempo (Trayectoria Corporativa) */
        .timeline { margin-top: 2rem; position: relative; border-left: 4px solid var(--primary); padding-left: 1.5rem; }
        .timeline-item { margin-bottom: 1.5rem; position: relative; }
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -1.85rem;
            top: 5px;
            width: 15px;
            height: 15px;
            border-radius: 50%;
            background: var(--secondary);
            border: 3px solid var(--white);
        }
        .timeline-item h4 { color: var(--primary); font-size: 1.1rem; }

        /* Misión y Visión */
        .mv-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.5rem; margin-top: 2rem; }
        .mv-card { background: var(--light); padding: 1.5rem; border-radius: 8px; border-top: 4px solid var(--secondary); }
        .mv-card h3 { color: var(--primary); margin-bottom: 0.5rem; display: flex; align-items: center; gap: 8px; }

        /* Servicios / Procesos */
        .services-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.8rem; }
        
        .card {
            background: var(--white);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0,0,0,0.06);
            border-top: 4px solid var(--primary);
            transition: transform 0.3s;
        }
        .card:hover { transform: translateY(-6px); }

        .card-img { height: 200px; width: 100%; object-fit: cover; }
        .card-body { padding: 1.5rem; }
        .card-body h3 { color: var(--primary); margin-bottom: 0.8rem; font-size: 1.2rem; }
        .card-body ul { list-style: none; padding: 0; }
        .card-body ul li { font-size: 0.95rem; color: var(--gray); margin-bottom: 0.4rem; position: relative; padding-left: 1.2rem; }
        .card-body ul li::before { content: "✔"; position: absolute; left: 0; color: var(--secondary); }

        /* Galería Fotográfica de Campo */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.2rem;
            margin-top: 1.5rem;
        }

        .gallery-item {
            position: relative;
            height: 250px;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 8px rgba(0,0,0,0.12);
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s;
        }
        .gallery-item:hover img { transform: scale(1.08); }
        .gallery-caption {
            position: absolute;
            bottom: 0;
            background: rgba(30, 58, 138, 0.85);
            color: white;
            width: 100%;
            padding: 8px 12px;
            font-size: 0.85rem;
            text-align: center;
        }

        /* Banner Cobertura */
        .coverage-banner {
            background: var(--primary);
            color: var(--white);
            text-align: center;
            padding: 2.5rem 1rem;
            border-radius: 8px;
            margin: 4rem 0 2rem 0;
        }
        .coverage-banner h3 { color: var(--secondary); font-size: 1.6rem; margin-bottom: 0.5rem; }

        /* Pie de Página */
        footer {
            background: var(--dark);
            color: var(--white);
            text-align: center;
            padding: 3rem 1rem 1.5rem 1rem;
            margin-top: 4rem;
        }
        .footer-logo img {
            max-width: 220px;
            background: white;
            padding: 8px;
            border-radius: 6px;
            margin-bottom: 1rem;
        }
        .social-links a { color: var(--white); font-size: 1.6rem; margin: 0 0.8rem; transition: color 0.3s; }
        .social-links a:hover { color: var(--secondary); }

        /* Adaptación para Celulares */
        @media (max-width: 768px) {
            header { flex-direction: column; text-align: center; }
            nav { margin-top: 1rem; flex-wrap: wrap; justify-content: center; }
            .hero h1 { font-size: 1.8rem; }
            .about-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- Encabezado Principal con Logo -->
    <header>
        <div class="logo-container">
            <a href="#">
                <img src="img/Captura de pantalla 2023-11-21 215348.png" alt="Logo TOPO EXACT">
            </a>
        </div>
        <nav>
            <a href="#">Inicio</a>
            <a href="#nosotros">Quiénes Somos</a>
            <div class="dropdown">
                <span class="dropdown-button">Procesos <i class="fas fa-caret-down"></i></span>
                <div class="dropdown-content">
                    <a href="#procesos">Control de Obra & Infraestructura</a>
                    <a href="#procesos">Nivelación & Altimetría</a>
                    <a href="#procesos">Geodesia Satelital & GNSS RTK</a>
                    <a href="#procesos">Agrimensura & Catastro</a>
                    <a href="#procesos">Sistemas SIG & Fotogrametría</a>
                </div>
            </div>
            <a href="#galeria">Trabajos en Terreno</a>
            <a href="#contacto">Contacto</a>
        </nav>
    </header>

    <!-- Portada Principal (Hero) -->
    <section class="hero">
        <div class="hero-logo-box">
            <img src="img/Captura de pantalla 2023-11-21 215348.png" alt="TOPO EXACT Marca Oficial">
        </div>
        <h1>Servicios Topográficos y Geomática de Precisión</h1>
        <p class="slogan">"TOPO EXACT, TE BRINDA TRABAJO DE CALIDAD"</p>
        <a href="https://wa.me/573205405716?text=Hola,%20deseo%20cotizar%20un%20servicio%20topográfico%20con%20TOPO%20EXACT" class="btn-whatsapp" target="_blank">
            <i class="fab fa-whatsapp"></i> Contactar por WhatsApp
        </a>
    </section>

    <div class="container">

        <!-- Sección Quiénes Somos -->
        <section id="nosotros" class="about-section">
            <div class="about-grid">
                <div class="about-text">
                    <h2>Nuestra Historia y Evolución</h2>
                    <p>
                        Desde nuestra titulación en topografía en 2016, hemos construido una sólida trayectoria en agrimensura (destacando 4 años de gestión en el Ingenio Risaralda), obras viales, urbanismo y rectificación de áreas.
                    </p>
                    <p>
                        En 2023 alcanzamos un hito clave con la titulación en <strong>Administración de Negocios</strong>, consolidando un perfil integral que combina la precisión técnica con la eficiencia gerencial. Tras participar activamente en procesos de restitución de tierras en el Caquetá, evolucionamos hacia <strong>Topo Exact</strong>: una firma radicada en Florencia que pone a disposición del Caquetá y Huila casi una década de experiencia, rigor administrativo y tecnología de vanguardia.
                    </p>

                    <!-- Línea de Tiempo -->
                    <div class="timeline">
                        <div class="timeline-item">
                            <h4>2016 — Cimientos Técnicos y Experiencia en Campo</h4>
                            <p style="font-size: 0.9rem;">Adecuación de tierras, canales de riego y control fotogramétrico en el Ingenio Risaralda, obras viales y urbanismo.</p>
                        </div>
                        <div class="timeline-item">
                            <h4>2023 — Visión Gerencial y Perfil Administrativo</h4>
                            <p style="font-size: 0.9rem;">Titulación en Administración de Negocios para la optimización de recursos y gestión eficiente de proyectos.</p>
                        </div>
                        <div class="timeline-item">
                            <h4>Presente — Especialización Catastral y Nacer de Topo Exact</h4>
                            <p style="font-size: 0.9rem;">Georreferenciación y análisis espacial en Restitución de Tierras. Sede principal en Florencia para el Caquetá y gran parte del Huila.</p>
                        </div>
                    </div>
                </div>

                <div class="about-img">
                    <img src="img/IMG-20240708-WA0018.jpg" alt="Levantamiento Topográfico en Canal Agroindustrial">
                </div>
            </div>

            <!-- Misión y Visión -->
            <div class="mv-grid">
                <div class="mv-card">
                    <h3><i class="fas fa-bullseye" style="color:var(--secondary);"></i> Misión</h3>
                    <p>
                        Somos una empresa de origen quindiano radicada en Florencia, dedicada a brindar servicios de topografía e ingeniería de precisión en el departamento del Caquetá y gran parte del Huila. Nos comprometemos con el desarrollo de la región ofreciendo soluciones técnicas confiables y de alta calidad, respaldadas por tecnología a la vanguardia y el rigor profesional de nuestro equipo.
                    </p>
                </div>
                <div class="mv-card">
                    <h3><i class="fas fa-eye" style="color:var(--secondary);"></i> Visión</h3>
                    <p>
                        Seremos una empresa líder en el sur del país que, desde nuestra sede en Florencia, impulsará el desarrollo regional aplicando soluciones técnicas de vanguardia y nuevas tecnologías que nos permitan perfeccionar cada uno de nuestros procesos y entregar resultados eficientes, exactos y confiables.
                    </p>
                </div>
            </div>
        </section>

        <!-- Sección de Procesos y Servicios -->
        <section id="procesos">
            <h2 class="section-title">Nuestros Procesos de Ingeniería</h2>
            
            <div class="services-grid">

                <!-- Proceso 1 -->
                <div class="card">
                    <img src="img/IMG-20240708-WA0017.jpg" alt="Control de Obra" class="card-img">
                    <div class="card-body">
                        <h3>Control de Obra & Infraestructura</h3>
                        <ul>
                            <li>Replanteo de ejes, niveles y cimentaciones.</li>
                            <li>Control de excavaciones y movimiento de tierras.</li>
                            <li>Monitoreo estructural, aplomados y asentamientos.</li>
                            <li>Seguimiento en tiempo real con Estación Total.</li>
                        </ul>
                    </div>
                </div>

                <!-- Proceso 2 -->
                <div class="card">
                    <img src="img/IMG-20240708-WA0014.jpg" alt="Nivelación y Altimetría" class="card-img">
                    <div class="card-body">
                        <h3>Nivelación & Altimetría de Precisión</h3>
                        <ul>
                            <li>Nivelación geométrica con nivel óptico/digital.</li>
                            <li>Perfiles longitudinales y transversales.</li>
                            <li>Modelado digital de terrenos (redes TIN) y curvas.</li>
                            <li>Control de flujo de aguas en canales y acueductos.</li>
                        </ul>
                    </div>
                </div>

                <!-- Proceso 3 -->
                <div class="card">
                    <img src="img/IMG-20240708-WA0020.jpg" alt="Geodesia y Vías" class="card-img">
                    <div class="card-body">
                        <h3>Geodesia Satelital & GNSS RTK</h3>
                        <ul>
                            <li>Posicionamiento milimétrico en tiempo real (RTK).</li>
                            <li>Amarrado oficial a la red nacional MAGNA-SIRGAS (IGAC).</li>
                            <li>Georreferenciación de fincas y predios rurales.</li>
                            <li>Puntos de Control Terrestre (GCPs) para drones.</li>
                        </ul>
                    </div>
                </div>

                <!-- Proceso 4 -->
                <div class="card">
                    <img src="img/IMG-20240708-WA0018.jpg" alt="Agrimensura y Catastro" class="card-img">
                    <div class="card-body">
                        <h3>Agrimensura & Gestión Catastral</h3>
                        <ul>
                            <li>Definición física y legal de linderos (deslindes).</li>
                            <li>Diseño geométrico de loteos y subdivisiones.</li>
                            <li>Elaboración de planos catastrales e informes.</li>
                            <li>Memorias técnicas para el IGAC y notarías.</li>
                        </ul>
                    </div>
                </div>

                <!-- Proceso 5 -->
                <div class="card">
                    <img src="img/IMG-20240708-WA0022.jpg" alt="SIG y Fotogrametría" class="card-img">
                    <div class="card-body">
                        <h3>Sistemas SIG & Fotogrametría</h3>
                        <ul>
                            <li>Análisis espacial en ArcGIS Pro y QGIS.</li>
                            <li>Procesamiento de imágenes con Drones (UAS).</li>
                            <li>Mapas temáticos de ordenamiento territorial.</li>
                            <li>Estructuración de geodatabases catastrales.</li>
                        </ul>
                    </div>
                </div>

            </div>
        </section>

        <!-- Galería Fotográfica de Trabajos en Terreno -->
        <section id="galeria" style="margin-top: 5rem;">
            <h2 class="section-title">Registro Fotográfico en Terreno</h2>
            <div class="gallery-grid">
                <div class="gallery-item">
                    <img src="img/IMG-20240708-WA0017.jpg" alt="Control de excavación y obra civil">
                    <div class="gallery-caption">Control de Obra y Maquinaria en Terreno</div>
                </div>
                <div class="gallery-item">
                    <img src="img/IMG-20240708-WA0014.jpg" alt="Levantamiento altimétrico cerca de agua">
                    <div class="gallery-caption">Altimetría y Nivelación Alrededor de Cuerpos de Agua</div>
                </div>
                <div class="gallery-item">
                    <img src="img/IMG-20240708-WA0020.jpg" alt="Topografía en vía principal AUXG3">
                    <div class="gallery-caption">Trazado y Control Geométrico Vial (AUXG3)</div>
                </div>
                <div class="gallery-item">
                    <img src="img/IMG-20240708-WA0018.jpg" alt="Adecuación de canales y cultivos">
                    <div class="gallery-caption">Agrimensura y Canales de Drenaje/Riego</div>
                </div>
                <div class="gallery-item">
                    <img src="img/IMG-20240708-WA0022.jpg" alt="Estación total en carretera pavimentada">
                    <div class="gallery-caption">Georreferenciación de Corredores Viales</div>
                </div>
            </div>
        </section>

        <!-- Cobertura Territorial -->
        <div class="coverage-banner">
            <h3><i class="fas fa-map-marker-alt"></i> Cobertura Regional</h3>
            <p>Sede Principal: <strong>Florencia, Caquetá</strong> — Prestando servicios técnicos y consultoría especializada en todo el departamento del <strong>Caquetá</strong> y gran parte del <strong>Huila</strong>.</p>
        </div>

    </div>

    <!-- Pie de Página y Contacto -->
    <footer id="contacto">
        <div class="footer-logo">
            <img src="img/Captura de pantalla 2023-11-21 215348.png" alt="TOPO EXACT Logo Pie">
        </div>
        <p style="font-weight: bold; color: var(--secondary); font-size: 1.1rem; margin-bottom: 0.5rem;">"TOPO EXACT, TE BRINDA TRABAJO DE CALIDAD"</p>
        <p><strong>Luis A. Beltrán B.</strong> | Administrador de Negocios & Topógrafo Profesional</p>

        <div class="social-links" style="margin: 1.5rem 0;">
            <a href="https://wa.me/573205405716" target="_blank" title="WhatsApp"><i class="fab fa-whatsapp"></i></a>
            <a href="mailto:beltranluis30@hotmail.com" title="Correo Electrónico"><i class="fas fa-envelope"></i></a>
        </div>

        <p><i class="fas fa-phone"></i> +57 320 540 5716 | <i class="fas fa-envelope"></i> beltranluis30@hotmail.com</p>
        <p><i class="fas fa-map-marker-alt"></i> Florencia, Caquetá — Cobertura en Caquetá y Huila</p>
        <p style="font-size: 0.8rem; margin-top: 1.5rem; color: #9ca3af;">&copy; 2026 TOPO EXACT. Todos los derechos reservados.</p>
    </footer>

</body>
</html>
