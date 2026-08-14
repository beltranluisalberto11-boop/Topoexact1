<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TOPO EXACT | Servicios Topográficos y Geomática de Precisión</title>
    <!-- Carga de íconos FontAwesome -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        /* Variables de color corporativo (Estilo Premium Oscuro) */
        :root {
            --primary-bg: #0f172a;
            --secondary-bg: #1e293b;
            --accent: #EAB308;
            --text-light: #f8fafc;
            --text-muted: #cbd5e1;
            --white: #ffffff;
            --dark: #000000;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Helvetica Neue', Arial, sans-serif; }
        html { scroll-behavior: smooth; }
        body { background-color: var(--primary-bg); color: var(--text-light); line-height: 1.6; }
        a { text-decoration: none; color: var(--text-light); transition: color 0.3s; }

        /* Encabezado y Menú de Navegación */
        header {
            background-color: rgba(15, 23, 42, 0.95);
            border-bottom: 2px solid var(--accent);
            padding: 0.8rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .logo-container img {
            height: 55px;
            width: auto;
            object-fit: contain;
            background: rgba(255, 255, 255, 0.9);
            padding: 5px 15px;
            border-radius: 4px;
        }

        nav { display: flex; align-items: center; gap: 1.2rem; }
        nav a { font-weight: 600; padding: 0.5rem; text-transform: uppercase; font-size: 14px; }
        nav a:hover { color: var(--accent); }

        /* Menú Desplegable de Procesos */
        .dropdown { position: relative; display: inline-block; }
        .dropdown-button { color: var(--text-light); font-weight: 600; padding: 0.5rem; cursor: pointer; text-transform: uppercase; font-size: 14px; transition: color 0.3s;}
        .dropdown-button:hover { color: var(--accent); }
        .dropdown-content {
            display: none;
            position: absolute;
            background-color: var(--secondary-bg);
            min-width: 280px;
            box-shadow: 0px 8px 16px rgba(0,0,0,0.5);
            border-radius: 6px;
            border-top: 3px solid var(--accent);
            top: 100%;
            left: 0;
            overflow: hidden;
        }
        .dropdown-content a { color: var(--text-light); padding: 12px 16px; display: block; font-size: 0.9rem; border-bottom: 1px solid rgba(255,255,255,0.05); text-transform: none; }
        .dropdown-content a:hover { background-color: rgba(255,255,255,0.05); color: var(--accent); }
        .dropdown:hover .dropdown-content { display: block; }

        /* Portada / Hero */
        .hero {
            background: linear-gradient(rgba(15, 23, 42, 0.85), rgba(15, 23, 42, 0.95)), url('img/Paginaweb\ (1).jpg') center/cover no-repeat;
            color: var(--white);
            text-align: center;
            padding: 150px 20px 100px;
            margin-top: 60px;
        }

        .hero-logo-box { margin-bottom: 1.5rem; }
        .hero-logo-box img {
            max-width: 240px;
            background: rgba(255, 255, 255, 0.95);
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
            border: 2px solid var(--accent);
        }

        .hero h1 { font-size: 2.8rem; margin-bottom: 0.5rem; font-weight: 800; letter-spacing: 1px; }
        .hero p.slogan { font-size: 1.3rem; color: var(--accent); font-weight: 700; margin-bottom: 2.5rem; letter-spacing: 1px; font-style: italic; }

        .btn-whatsapp {
            display: inline-block;
            background-color: #25d366;
            color: var(--dark);
            padding: 1rem 2rem;
            border-radius: 50px;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
            transition: transform 0.2s, background 0.3s;
        }
        .btn-whatsapp:hover { transform: translateY(-3px); background-color: #20b858; color: var(--dark); }

        /* Estructura Contenedora */
        .container { max-width: 1200px; margin: 4rem auto; padding: 0 20px; }
        .section-title { text-align: center; margin-bottom: 3rem; color: var(--accent); font-size: 2.2rem; text-transform: uppercase; }

        /* Sección Quiénes Somos / Historia */
        .about-section {
            background: var(--secondary-bg);
            border-radius: 10px;
            padding: 3rem;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
            margin-bottom: 4rem;
            border-left: 5px solid var(--accent);
        }

        .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 3rem; align-items: center; }
        .about-text h2 { color: var(--accent); margin-bottom: 1.5rem; font-size: 1.8rem; }
        .about-text p { margin-bottom: 1rem; text-align: justify; color: var(--text-muted); }

        .about-img img {
            width: 100%;
            height: 400px;
            object-fit: cover;
            border-radius: 8px;
            border: 2px solid rgba(255,255,255,0.1);
        }

        /* Línea de Tiempo (Trayectoria Corporativa) */
        .timeline { margin-top: 2.5rem; position: relative; border-left: 3px solid var(--accent); padding-left: 1.5rem; }
        .timeline-item { margin-bottom: 2rem; position: relative; }
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -1.82rem;
            top: 5px;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: var(--primary-bg);
            border: 3px solid var(--accent);
        }
        .timeline-item h4 { color: var(--white); font-size: 1.1rem; margin-bottom: 0.3rem; }
        .timeline-item p { font-size: 0.95rem; color: var(--text-muted); }

        /* Misión y Visión */
        .mv-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; margin-top: 3rem; }
        .mv-card { background: rgba(0,0,0,0.2); padding: 2rem; border-radius: 8px; border-top: 3px solid var(--accent); }
        .mv-card h3 { color: var(--accent); margin-bottom: 1rem; display: flex; align-items: center; gap: 10px; font-size: 1.4rem; }
        .mv-card p { color: var(--text-muted); text-align: justify; }

        /* Portafolio por Mercados (Estrategia Comercial) */
        .market-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 2rem; margin-bottom: 5rem; }
        .market-card {
            background-color: var(--secondary-bg);
            padding: 2rem;
            border-radius: 8px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: transform 0.3s, border-color 0.3s;
        }
        .market-card:hover { transform: translateY(-5px); border-color: var(--accent); }
        .market-card h3 { color: var(--accent); border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 10px; margin-bottom: 1.5rem; font-size: 1.3rem; }
        .market-card ul { list-style: none; padding: 0; }
        .market-card ul li { margin-bottom: 15px; padding-left: 20px; position: relative; color: var(--text-muted); font-size: 0.95rem;}
        .market-card ul li::before { content: "▹"; color: var(--accent); position: absolute; left: 0; font-weight: bold; }

        /* Servicios / Procesos Técnicos (Tarjetas con Imágenes) */
        .services-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 2rem; }
        .card {
            background: var(--secondary-bg);
            border-radius: 8px;
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.05);
            border-top: 4px solid var(--accent);
            transition: transform 0.3s;
        }
        .card:hover { transform: translateY(-6px); box-shadow: 0 10px 20px rgba(0,0,0,0.4); }
        .card-img { height: 220px; width: 100%; object-fit: cover; border-bottom: 2px solid rgba(255,255,255,0.05); }
        .card-body { padding: 1.8rem; }
        .card-body h3 { color: var(--white); margin-bottom: 1rem; font-size: 1.2rem; text-transform: uppercase; letter-spacing: 1px;}
        .card-body ul { list-style: none; padding: 0; }
        .card-body ul li { font-size: 0.95rem; color: var(--text-muted); margin-bottom: 0.6rem; position: relative; padding-left: 1.5rem; }
        .card-body ul li::before { content: "✔"; position: absolute; left: 0; color: var(--accent); font-size: 0.8rem; top: 3px;}

        /* Galería Fotográfica de Campo */
        .gallery-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.5rem; margin-top: 2rem; }
        .gallery-item {
            position: relative;
            height: 280px;
            border-radius: 8px;
            overflow: hidden;
            border: 2px solid rgba(255,255,255,0.05);
        }
        .gallery-item img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s; }
        .gallery-item:hover img { transform: scale(1.1); }
        .gallery-caption {
            position: absolute;
            bottom: 0;
            background: linear-gradient(transparent, rgba(15, 23, 42, 0.95));
            color: var(--accent);
            width: 100%;
            padding: 20px 15px 10px;
            font-size: 0.95rem;
            text-align: center;
            font-weight: bold;
        }

        /* Banner Cobertura */
        .coverage-banner {
            background: linear-gradient(to right, rgba(15, 23, 42, 0.9), rgba(30, 41, 59, 0.9));
            color: var(--text-light);
            text-align: center;
            padding: 3rem 2rem;
            border-radius: 8px;
            margin: 5rem 0 2rem 0;
            border: 1px solid rgba(255,255,255,0.1);
            border-left: 6px solid var(--accent);
        }
        .coverage-banner h3 { color: var(--accent); font-size: 1.8rem; margin-bottom: 1rem; text-transform: uppercase; }
        .coverage-banner p { font-size: 1.1rem; color: var(--text-muted); max-width: 800px; margin: 0 auto;}

        /* Pie de Página */
        footer {
            background: var(--dark);
            text-align: center;
            padding: 4rem 20px 2rem;
            margin-top: 4rem;
            border-top: 3px solid var(--accent);
        }
        .footer-logo img {
            max-width: 280px;
            background: rgba(255,255,255,0.9);
            padding: 10px 15px;
            border-radius: 6px;
            margin-bottom: 1.5rem;
        }
        .social-links a { color: var(--text-muted); font-size: 1.8rem; margin: 0 1rem; transition: color 0.3s; display: inline-block;}
        .social-links a:hover { color: var(--accent); transform: translateY(-3px);}
        .footer-text { color: var(--text-muted); margin-bottom: 0.5rem; font-size: 1rem;}
        .footer-accent { color: var(--accent); font-weight: bold; }

        /* Adaptación para Celulares */
        @media (max-width: 768px) {
            header { flex-direction: column; padding: 1rem; }
            nav { margin-top: 1rem; flex-wrap: wrap; justify-content: center; }
            .hero { padding: 120px 20px 60px; margin-top: 100px; }
            .hero h1 { font-size: 2rem; }
            .about-grid { grid-template-columns: 1fr; }
            .dropdown-content { position: static; box-shadow: none; display: none; width: 100%;}
            .dropdown:hover .dropdown-content { display: block; }
        }
    </style>
</head>
<body>

    <!-- Encabezado Principal con Logo -->
    <header>
        <div class="logo-container">
            <a href="#">
                <img src="img/logo2.png" alt="Logo TOPO EXACT">
            </a>
        </div>
        <nav>
            <a href="#">Inicio</a>
            <a href="#nosotros">Perfil</a>
            <div class="dropdown">
                <span class="dropdown-button">Servicios Técnicos <i class="fas fa-caret-down"></i></span>
                <div class="dropdown-content">
                    <a href="#procesos">Control de Obra & Infraestructura</a>
                    <a href="#procesos">Nivelación & Altimetría</a>
                    <a href="#procesos">Geodesia Satelital & GNSS RTK</a>
                    <a href="#procesos">Agrimensura & Catastro</a>
                    <a href="#procesos">Sistemas SIG & Fotogrametría</a>
                </div>
            </div>
            <a href="#mercados">Mercados</a>
            <a href="#galeria">Trabajos en Terreno</a>
            <a href="#contacto">Contacto</a>
        </nav>
    </header>

    <!-- Portada Principal (Hero) -->
    <section class="hero">
        <div class="hero-logo-box">
            <img src="img/imglogo.png" alt="TOPO EXACT Marca Oficial">
        </div>
        <h1>Servicios Topográficos y Geomática de Precisión</h1>
        <p class="slogan">"TOPO EXACT, TE BRINDA TRABAJO DE CALIDAD"</p>
        <a href="https://wa.me/573218626306?text=Hola,%20deseo%20cotizar%20un%20servicio%20topográfico%20con%20TOPO%20EXACT" class="btn-whatsapp" target="_blank">
            <i class="fab fa-whatsapp"></i> Contactar por WhatsApp
        </a>
    </section>

    <div class="container">

        <!-- Sección Quiénes Somos / Historia -->
        <section id="nosotros" class="about-section">
            <div class="about-grid">
                <div class="about-text">
                    <h2>Nuestra Historia y Evolución</h2>
                    <p>
                        Desde nuestra titulación técnica en topografía en 2016, hemos construido una sólida trayectoria en agrimensura, destacando 4 años de gestión rigurosa en el Ingenio Risaralda, así como en proyectos de obras viales, urbanismo y rectificación de áreas.
                    </p>
                    <p>
                        En 2023 alcanzamos un hito clave con la titulación profesional en <strong>Administración de Negocios</strong>, consolidando un perfil integral que combina la exactitud técnica en campo con la eficiencia gerencial. Tras participar activamente en procesos de restitución de tierras en la región, evolucionamos hacia <strong>TOPO EXACT</strong>: una firma que pone a disposición del sur de Colombia casi una década de experiencia, rigor administrativo y tecnología de vanguardia.
                    </p>

                    <!-- Línea de Tiempo -->
                    <div class="timeline">
                        <div class="timeline-item">
                            <h4>2016 — Cimientos Técnicos y Experiencia en Campo</h4>
                            <p>Adecuación de tierras, canales de riego y control fotogramétrico en el Ingenio Risaralda, obras viales y urbanismo.</p>
                        </div>
                        <div class="timeline-item">
                            <h4>2023 — Visión Gerencial y Perfil Administrativo</h4>
                            <p>Titulación como Administrador de Negocios para la optimización de recursos y gestión transparente de proyectos técnicos.</p>
                        </div>
                        <div class="timeline-item">
                            <h4>Presente — Especialización Catastral y Topo Exact</h4>
                            <p>Georreferenciación y análisis espacial en Restitución de Tierras. Consolidación de TOPO EXACT como referente de calidad en el Sur de Colombia.</p>
                        </div>
                    </div>
                </div>

                <div class="about-img">
                    <img src="img/station (6).jpg" alt="Levantamiento Topográfico en Terreno">
                </div>
            </div>

            <!-- Misión y Visión -->
            <div class="mv-grid">
                <div class="mv-card">
                    <h3><i class="fas fa-bullseye"></i> Misión</h3>
                    <p>
                        Somos una empresa de origen quindiano radicada en Florencia, dedicada a brindar servicios de topografía e ingeniería de precisión en el departamento del Caquetá y gran parte del Huila. Nos comprometemos con el desarrollo de la región ofreciendo soluciones técnicas confiables, respaldadas por tecnología de punta y el rigor profesional de nuestro equipo.
                    </p>
                </div>
                <div class="mv-card">
                    <h3><i class="fas fa-eye"></i> Visión</h3>
                    <p>
                        Seremos una empresa líder en el sur del país que impulsará el desarrollo regional aplicando soluciones técnicas de vanguardia y nuevas tecnologías. Buscamos perfeccionar continuamente nuestros procesos para entregar resultados eficientes, exactos y legalmente confiables a cada uno de nuestros clientes.
                    </p>
                </div>
            </div>
        </section>

        <!-- Portafolio Estratégico (Por Mercados) -->
        <section id="mercados">
            <h2 class="section-title">Soluciones Especializadas por Sector</h2>
            <div class="market-grid">
                <div class="market-card">
                    <h3>🚜 Sector Agropecuario</h3>
                    <ul>
                        <li><strong>Agricultura 4.0:</strong> Mapas de salud vegetal (NDVI/SAVI) y topografía para diseño de riegos.</li>
                        <li><strong>Diseño de Predios:</strong> Trazado geométrico de potreros para ganadería sustentable y loteos rurales.</li>
                        <li><strong>Adecuación:</strong> Diseño de canales y perfiles para control de aguas.</li>
                    </ul>
                </div>
                <div class="market-card">
                    <h3>⚖️ Sector Jurídico & Inmobiliario</h3>
                    <ul>
                        <li><strong>Agrimensura Legal:</strong> Deslindes, aclaración de linderos y peritajes técnicos certificados.</li>
                        <li><strong>Gestión Catastral:</strong> Memorias técnicas para IGAC, notarías y procesos de Restitución de Tierras.</li>
                        <li><strong>Urbanismo:</strong> Diseño y estructuración de loteos listos para procesos de escrituración.</li>
                    </ul>
                </div>
                <div class="market-card">
                    <h3>🏗️ Construcción & Civil</h3>
                    <ul>
                        <li><strong>Fotogrametría Aérea:</strong> Modelos Digitales (MDT/MDE), ortoimágenes y mapas de teselas con drones.</li>
                        <li><strong>Control Estructural:</strong> Replanteo, verticalidad, aplomados y control de movimiento de tierras.</li>
                        <li><strong>Geodesia Vial:</strong> Trazado y control geométrico de vías (RTK/Estación Total).</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Sección de Procesos y Servicios Técnicos (Con Imágenes del Cliente) -->
        <section id="procesos">
            <h2 class="section-title">Nuestros Procesos de Ingeniería</h2>
            <div class="services-grid">

                <div class="card">
                    <img src="img/station (5).jpg" alt="Control de Obra y Maquinaria" class="card-img">
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

                <div class="card">
                    <img src="img/station (1).jpg" alt="Nivelación en Canales" class="card-img">
                    <div class="card-body">
                        <h3>Nivelación & Altimetría</h3>
                        <ul>
                            <li>Nivelación geométrica con nivel óptico/digital.</li>
                            <li>Perfiles longitudinales y transversales.</li>
                            <li>Modelado digital de terrenos (redes TIN) y curvas.</li>
                            <li>Control de flujo de aguas en canales y acueductos.</li>
                        </ul>
                    </div>
                </div>

                <div class="card">
                    <img src="img/station (2).jpg" alt="Geodesia en Vías" class="card-img">
                    <div class="card-body">
                        <h3>Geodesia Satelital & GNSS RTK</h3>
                        <ul>
                            <li>Posicionamiento milimétrico en tiempo real (RTK).</li>
                            <li>Amarrado oficial a la red nacional MAGNA-SIRGAS.</li>
                            <li>Georreferenciación de fincas y predios rurales.</li>
                            <li>Puntos de Control Terrestre (GCPs) para drones.</li>
                        </ul>
                    </div>
                </div>

                <div class="card">
                    <img src="img/station (3).jpg" alt="Agrimensura y Catastro" class="card-img">
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

                <div class="card">
                    <img src="img/ftgrmtia.jpg" alt="SIG y Fotogrametría Aérea" class="card-img">
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
        <section id="galeria" style="margin-top: 6rem;">
            <h2 class="section-title">Registro Fotográfico en Terreno</h2>
            <div class="gallery-grid">
                <div class="gallery-item">
                    <img src="img/station (5).jpg" alt="Control de excavación y obra civil">
                    <div class="gallery-caption">Control de Obra y Maquinaria en Terreno</div>
                </div>
                <div class="gallery-item">
                    <img src="img/station (4).jpg" alt="Levantamiento altimétrico cerca de agua">
                    <div class="gallery-caption">Altimetría y Nivelación en Cuerpos de Agua</div>
                </div>
                <div class="gallery-item">
                    <img src="img/station (2).jpg" alt="Topografía en vía principal pavimentada">
                    <div class="gallery-caption">Georreferenciación de Corredores Viales</div>
                </div>
                <div class="gallery-item">
                    <img src="img/station (1).jpg" alt="Adecuación de canales y cultivos">
                    <div class="gallery-caption">Agrimensura y Control de Canales</div>
                </div>
                <div class="gallery-item">
                    <img src="img/station (3).jpg" alt="Estación total en camino rural">
                    <div class="gallery-caption">Levantamientos Topográficos Rurales</div>
                </div>
                <div class="gallery-item">
                    <img src="img/station (6).jpg" alt="Topografía en campo de cultivo">
                    <div class="gallery-caption">Levantamientos en Cultivos y Cañaduzales</div>
                </div>
            </div>
        </section>

        <!-- Cobertura Territorial -->
        <div class="coverage-banner">
            <h3><i class="fas fa-map-marked-alt"></i> Cobertura Operativa</h3>
            <p>Sede Principal en <strong>Florencia, Caquetá</strong> — Prestando servicios técnicos, topografía de precisión y consultoría especializada en <strong>Quindío, Caquetá, Huila</strong> y todo el <strong>Sur de Colombia</strong>.</p>
        </div>

    </div>

    <!-- Pie de Página y Contacto -->
    <footer id="contacto">
        <div class="footer-logo">
            <img src="img/logo2.png" alt="TOPO EXACT Logo Pie">
        </div>
        <p style="font-weight: bold; color: var(--accent); font-size: 1.2rem; margin-bottom: 1rem; font-style: italic;">"Te brinda trabajo de calidad"</p>
        
        <p class="footer-text" style="font-size: 1.1rem; color: var(--white);"><strong>Luis A. Beltrán B.</strong></p>
        <p class="footer-text" style="margin-bottom: 2rem;">Topógrafo Profesional | Administrador de Negocios</p>

        <div class="social-links">
            <a href="https://wa.me/573218626306" target="_blank" title="Escríbenos por WhatsApp"><i class="fab fa-whatsapp"></i></a>
            <a href="https://instagram.com/topoexact" target="_blank" title="Síguenos en Instagram"><i class="fab fa-instagram"></i></a>
            <a href="https://facebook.com/topoexact" target="_blank" title="Síguenos en Facebook"><i class="fab fa-facebook"></i></a>
            <a href="mailto:contacto@topoexact.com" title="Envíanos un Correo"><i class="fas fa-envelope"></i></a>
        </div>

        <p class="footer-text" style="margin-top: 1.5rem;"><i class="fas fa-phone footer-accent"></i> (+57) 321 862 6306</p>
        <p class="footer-text"><i class="fas fa-envelope footer-accent"></i> contacto@topoexact.com</p>
        <p class="footer-text"><i class="fas fa-map-marker-alt footer-accent"></i> Cobertura: Quindío, Caquetá, Huila & Sur de Colombia</p>
        
        <p style="font-size: 0.85rem; margin-top: 3rem; color: #64748b; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 20px;">
            &copy; 2026 TOPO EXACT Ingeniería Topográfica & Gestión Territorial. Todos los derechos reservados.
        </p>
    </footer>

</body>
</html>
