```html
<!DOCTYPE html>
<html lang="es-MX">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Yucatalog | Catálogo</title>
  <meta name="description" content="Yucatalog — Catálogo en línea de pequeños accesorios prácticos: fundas para llave de auto, espejos portátiles LED, soportes magnéticos y gadgets USB." />

  <!-- Fuente Inter desde Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />

  <!-- Tailwind CSS vía CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'system-ui', '-apple-system', 'sans-serif'],
          },
          colors: {
            surface: '#FAFAFA',
            ink: '#18181B',
            muted: '#71717A',
          },
          boxShadow: {
            'card': '0 1px 3px rgba(0, 0, 0, 0.04), 0 6px 18px rgba(0, 0, 0, 0.03)',
            'card-hover': '0 14px 32px -12px rgba(0, 0, 0, 0.14)',
            'modal': '0 25px 65px -15px rgba(0, 0, 0, 0.28)',
          }
        }
      }
    };
  </script>

  <!-- Estilos mínimos complementarios para barras ocultas y animación sutil -->
  <style>
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(8px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    .animate-fade-up {
      animation: fadeUp 0.28s ease-out forwards;
    }
  </style>
</head>

<body class="bg-surface text-ink font-sans antialiased selection:bg-zinc-900 selection:text-white overflow-x-hidden min-h-screen flex flex-col">

  <!-- ===================================================================== -->
  <!-- 1. ENCABEZADO STICKY (MARCA, BUSCADOR Y FILTROS DE CATEGORÍA)         -->
  <!-- ===================================================================== -->
  <header class="sticky top-0 z-40 bg-white/90 backdrop-blur-md border-b border-zinc-200/80">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">

      <!-- Fila superior: Identidad Yucatalog + Buscador en tiempo real -->
      <div class="py-3.5 sm:py-4 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-3 sm:gap-6">
        <div class="flex items-center justify-between">
          <a href="#" id="brand-link" class="group inline-flex items-baseline gap-2.5 focus:outline-none">
            <span id="store-name" class="text-xl sm:text-2xl font-bold tracking-tight text-zinc-900">
              Yucatalog
            </span>
            <span class="text-zinc-300 font-light select-none" aria-hidden="true">|</span>
            <span id="store-subtitle" class="text-xs sm:text-sm font-medium text-zinc-500 tracking-wide uppercase">
              Catálogo
            </span>
          </a>

          <!-- Contador de artículos visible en móvil -->
          <span id="mobile-count" class="sm:hidden text-xs font-medium text-zinc-500 bg-zinc-100 px-2.5 py-1 rounded-full">
            6 productos
          </span>
        </div>

        <!-- Buscador por nombre o características -->
        <div class="relative w-full sm:max-w-xs md:max-w-sm">
          <label for="search-input" class="sr-only">Buscar productos por nombre o características</label>
          <span class="pointer-events-none absolute inset-y-0 left-0 flex items-center pl-3.5 text-zinc-400">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35m0 0A7.5 7.5 0 1010.5 18a7.5 7.5 0 006.15-3.35z" />
            </svg>
          </span>
          <input
            id="search-input"
            type="text"
            autocomplete="off"
            placeholder="Buscar funda, espejo LED, soporte, USB..."
            class="w-full rounded-full bg-zinc-100/90 border border-transparent py-2.5 pl-10 pr-10 text-sm text-zinc-900 placeholder:text-zinc-400 focus:bg-white focus:border-zinc-300 focus:outline-none focus:ring-2 focus:ring-zinc-900/10 transition-all"
          />
          <button
            id="clear-search-btn"
            type="button"
            aria-label="Limpiar búsqueda"
            class="hidden absolute inset-y-0 right-0 flex items-center pr-3 text-zinc-400 hover:text-zinc-700 transition-colors"
          >
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>

      <!-- Fila inferior: Pills de filtro por categoría -->
      <nav aria-label="Filtrar por categoría" class="pb-3 sm:pb-3.5 flex items-center justify-between gap-4">
        <div id="category-filters" class="flex items-center gap-2 overflow-x-auto no-scrollbar py-0.5 w-full sm:w-auto">
          <!-- Botones de categoría generados por JavaScript -->
        </div>
        <span id="desktop-count" class="hidden sm:inline-block text-xs font-medium text-zinc-500 whitespace-nowrap">
          Mostrando 6 productos
        </span>
      </nav>

    </div>
  </header>

  <!-- ===================================================================== -->
  <!-- 2. CONTENIDO PRINCIPAL: CUADRÍCULA DE PRODUCTOS                       -->
  <!-- ===================================================================== -->
  <main class="flex-1 w-full max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-6 sm:py-10">
    <section aria-label="Productos disponibles en Yucatalog">
      <!-- Cuadrícula limpia: 2 columnas en móvil, 3 en pantallas medianas/grandes -->
      <div id="catalog-grid" class="grid grid-cols-2 md:grid-cols-3 gap-3.5 sm:gap-6 lg:gap-8">
        <!-- Tarjetas generadas dinámicamente -->
      </div>

      <!-- Estado vacío cuando la búsqueda no encuentra resultados -->
      <div id="empty-state" class="hidden py-16 sm:py-24 text-center max-w-md mx-auto">
        <div class="w-14 h-14 mx-auto mb-4 rounded-2xl bg-zinc-100 flex items-center justify-center text-zinc-400">
          <svg class="w-7 h-7" fill="none" stroke="currentColor" stroke-width="1.6" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35M17 10.5a6.5 6.5 0 11-13 0 6.5 6.5 0 0113 0z" />
          </svg>
        </div>
        <h2 class="text-base sm:text-lg font-semibold text-zinc-900">No encontramos coincidencias</h2>
        <p class="mt-1.5 text-sm text-zinc-500">
          Prueba con otra palabra clave o vuelve a explorar todas las categorías de Yucatalog.
        </p>
        <button
          id="reset-filters-btn"
          type="button"
          class="mt-5 inline-flex items-center justify-center rounded-full bg-zinc-900 px-5 py-2.5 text-sm font-medium text-white hover:bg-zinc-800 active:scale-[0.98] transition-all"
        >
          Ver todos los productos
        </button>
      </div>
    </section>
  </main>

  <!-- ===================================================================== -->
  <!-- 3. PIE DE PÁGINA MINIMALISTA (YUCATALOG + WHATSAPP DIRECTO)           -->
  <!-- ===================================================================== -->
  <footer class="mt-12 border-t border-zinc-200/80 bg-white">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-8 flex flex-col sm:flex-row items-center justify-between gap-4">
      <div class="text-center sm:text-left">
        <p id="footer-brand" class="text-base font-bold tracking-tight text-zinc-900">Yucatalog</p>
        <p id="footer-rights" class="text-xs text-zinc-500 mt-1">
          © 2026 Yucatalog. Precios en pesos mexicanos (MXN).
        </p>
      </div>

      <a
        id="footer-whatsapp-btn"
        href="https://wa.me/5215540130621"
        target="_blank"
        rel="noopener noreferrer"
        class="inline-flex items-center gap-2.5 rounded-full bg-emerald-600 hover:bg-emerald-700 active:scale-[0.98] text-white px-5 py-2.5 text-sm font-medium transition-all shadow-sm"
      >
        <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M20.52 3.48A11.86 11.86 0 0012.06 0C5.47 0 .11 5.36.11 11.95c0 2.1.55 4.16 1.6 5.98L0 24l6.24-1.64a11.92 11.92 0 005.82 1.49h.01c6.59 0 11.95-5.36 11.95-11.95 0-3.19-1.24-6.19-3.5-8.42zM12.07 21.84h-.01a9.9 9.9 0 01-5.04-1.38l-.36-.21-3.7.97.99-3.61-.24-.37a9.87 9.87 0 01-1.52-5.29c0-5.46 4.44-9.9 9.9-9.9 2.64 0 5.13 1.03 7 2.9a9.84 9.84 0 012.89 7.01c0 5.46-4.44 9.88-9.91 9.88zm5.43-7.42c-.3-.15-1.76-.87-2.03-.97-.27-.1-.47-.15-.67.15-.2.3-.77.97-.94 1.17-.17.2-.35.22-.64.07-.3-.15-1.26-.46-2.4-1.48-.89-.79-1.49-1.77-1.66-2.07-.17-.3-.02-.46.13-.61.13-.13.3-.35.45-.52.15-.17.2-.3.3-.5.1-.2.05-.37-.02-.52-.07-.15-.67-1.61-.92-2.21-.24-.58-.49-.5-.67-.51h-.57c-.2 0-.52.07-.79.37-.27.3-1.04 1.02-1.04 2.48 0 1.46 1.07 2.88 1.21 3.08.15.2 2.1 3.2 5.08 4.49.71.31 1.26.49 1.69.63.71.23 1.36.2 1.87.12.57-.09 1.76-.72 2.01-1.41.25-.69.25-1.29.17-1.41-.07-.12-.27-.2-.57-.35z"/>
        </svg>
        <span>WhatsApp 55 4013 0621</span>
      </a>
    </div>
  </footer>

  <!-- ===================================================================== -->
  <!-- 4. MODAL INTERACTIVO DE DETALLE (CARRUSEL + ESPECIFICACIONES)         -->
  <!-- ===================================================================== -->
  <div
    id="product-modal"
    role="dialog"
    aria-modal="true"
    aria-labelledby="modal-product-title"
    class="fixed inset-0 z-50 hidden items-center justify-center p-0 sm:p-4 md:p-6"
  >
    <!-- Fondo oscuro con desenfoque -->
    <div
      id="modal-backdrop"
      class="fixed inset-0 bg-zinc-950/60 backdrop-blur-sm transition-opacity duration-200 opacity-0"
    ></div>

    <!-- Panel del modal -->
    <div
      id="modal-panel"
      class="relative z-10 w-full h-full sm:h-auto sm:max-h-[92vh] sm:max-w-4xl bg-white sm:rounded-3xl shadow-modal overflow-hidden flex flex-col md:grid md:grid-cols-12 transition-all duration-200 opacity-0 scale-95"
    >
      <!-- Botón cerrar (Escape o clic) -->
      <button
        id="modal-close-btn"
        type="button"
        aria-label="Cerrar detalles del producto"
        class="absolute top-3.5 right-3.5 z-30 w-10 h-10 rounded-full bg-white/95 hover:bg-zinc-100 text-zinc-700 hover:text-zinc-950 border border-zinc-200/80 shadow-sm flex items-center justify-center transition-all active:scale-95"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>

      <!-- Contenedor deslizable en móvil / 2 columnas en escritorio -->
      <div class="flex-1 overflow-y-auto md:overflow-visible md:contents">

        <!-- COLUMNA IZQUIERDA: Carrusel interactivo -->
        <div class="md:col-span-6 bg-zinc-50 border-b md:border-b-0 md:border-r border-zinc-200/75 p-4 sm:p-6 flex flex-col justify-between">
          <div>
            <!-- Escenario de imagen principal con soporte táctil swipe -->
            <div
              id="carousel-stage"
              class="relative aspect-square w-full rounded-2xl bg-white border border-zinc-200/75 overflow-hidden select-none touch-pan-y shadow-sm"
            >
              <div id="carousel-main-media" class="w-full h-full flex items-center justify-center">
                <!-- Imagen real o ilustración SVG activa -->
              </div>

              <!-- Etiqueta descriptiva de la vista -->
              <div class="absolute bottom-3 left-3 right-16 pointer-events-none">
                <span id="carousel-caption" class="inline-block max-w-full truncate rounded-full bg-white/92 backdrop-blur-sm border border-zinc-200/70 px-3 py-1 text-[11px] font-medium text-zinc-700 shadow-sm">
                  Vista principal
                </span>
              </div>

              <!-- Indicador numérico de posición (1 / 3) -->
              <div class="absolute bottom-3 right-3 pointer-events-none">
                <span id="carousel-counter" class="inline-block rounded-full bg-zinc-900/85 backdrop-blur-sm px-2.5 py-1 text-[11px] font-medium text-white tabular-nums">
                  1 / 3
                </span>
              </div>

              <!-- Flecha Anterior -->
              <button
                id="carousel-prev-btn"
                type="button"
                aria-label="Imagen anterior"
                class="absolute left-2.5 top-1/2 -translate-y-1/2 w-10 h-10 rounded-full bg-white/92 hover:bg-white text-zinc-800 border border-zinc-200/80 shadow-sm flex items-center justify-center transition-all active:scale-95 focus:outline-none focus:ring-2 focus:ring-zinc-900/20"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
                </svg>
              </button>

              <!-- Flecha Siguiente -->
              <button
                id="carousel-next-btn"
                type="button"
                aria-label="Imagen siguiente"
                class="absolute right-2.5 top-1/2 -translate-y-1/2 w-10 h-10 rounded-full bg-white/92 hover:bg-white text-zinc-800 border border-zinc-200/80 shadow-sm flex items-center justify-center transition-all active:scale-95 focus:outline-none focus:ring-2 focus:ring-zinc-900/20"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
                </svg>
              </button>
            </div>

            <!-- Indicadores de puntos (dots) -->
            <div id="carousel-dots" class="mt-3 flex items-center justify-center gap-1.5" aria-label="Indicadores de imagen">
              <!-- Puntos renderizados dinámicamente -->
            </div>
          </div>

          <!-- Tira de miniaturas clicables -->
          <div class="mt-3.5">
            <div id="carousel-thumbnails" class="grid grid-cols-3 gap-2.5">
              <!-- Miniaturas generadas dinámicamente -->
            </div>
            <p class="mt-2.5 text-center text-[11px] text-zinc-400">
              Desliza en pantalla táctil o usa las flechas del teclado
            </p>
          </div>
        </div>

        <!-- COLUMNA DERECHA: Detalles, Especificaciones y Botón WhatsApp -->
        <div class="md:col-span-6 md:overflow-y-auto md:max-h-[92vh] p-5 sm:p-7 flex flex-col justify-between gap-6">
          <div>
            <!-- Categoría -->
            <div class="flex items-center gap-2 pr-10">
              <span id="modal-category" class="inline-flex items-center rounded-full bg-zinc-100 px-3 py-1 text-xs font-medium text-zinc-700">
                Categoría
              </span>
            </div>

            <!-- Título y Precio destacado -->
            <h2 id="modal-product-title" class="mt-3 text-xl sm:text-2xl font-semibold tracking-tight text-zinc-900 leading-snug">
              Nombre del producto
            </h2>
            <p id="modal-product-price" class="mt-2 text-2xl sm:text-[26px] font-bold tracking-tight text-zinc-900">
              $0 MXN
            </p>

            <!-- Descripción breve -->
            <p id="modal-product-description" class="mt-3 text-sm leading-relaxed text-zinc-600">
              Descripción breve del producto.
            </p>

            <!-- Bloque estructurado: ESPECIFICACIONES TÉCNICAS -->
            <div class="mt-6">
              <h3 class="text-xs font-semibold uppercase tracking-wider text-zinc-500 mb-3">
                Especificaciones técnicas
              </h3>
              <div class="rounded-2xl border border-zinc-200/80 bg-zinc-50/75 divide-y divide-zinc-200/75 text-sm">
                <!-- Medidas -->
                <div class="px-4 py-2.5 flex items-start justify-between gap-4">
                  <span class="text-zinc-500 shrink-0">Medidas</span>
                  <span id="spec-medidas" class="font-medium text-zinc-900 text-right">—</span>
                </div>
                <!-- Material -->
                <div class="px-4 py-2.5 flex items-start justify-between gap-4">
                  <span class="text-zinc-500 shrink-0">Material</span>
                  <span id="spec-material" class="font-medium text-zinc-900 text-right">—</span>
                </div>
                <!-- Contenido del paquete -->
                <div class="px-4 py-2.5 flex items-start justify-between gap-4">
                  <span class="text-zinc-500 shrink-0">Contenido del paquete</span>
                  <span id="spec-contenido" class="font-medium text-zinc-900 text-right">—</span>
                </div>
                <!-- Colores / Variantes disponibles -->
                <div class="px-4 py-3 flex flex-col gap-2">
                  <div class="flex items-center justify-between gap-2">
                    <span class="text-zinc-500">Colores / Variantes disponibles</span>
                    <span id="selected-variant-label" class="text-xs font-semibold text-zinc-800">—</span>
                  </div>
                  <div id="spec-variantes" class="flex flex-wrap items-center gap-2">
                    <!-- Variantes seleccionables -->
                  </div>
                </div>
              </div>
            </div>

            <!-- Lista de CARACTERÍSTICAS PRINCIPALES -->
            <div class="mt-6">
              <h3 class="text-xs font-semibold uppercase tracking-wider text-zinc-500 mb-3">
                Características principales
              </h3>
              <ul id="modal-features" class="space-y-2 text-sm text-zinc-700">
                <!-- Viñetas renderizadas por JavaScript -->
              </ul>
            </div>
          </div>

          <!-- Botón principal de compra/pedido por WhatsApp -->
          <div class="pt-4 border-t border-zinc-100 sticky bottom-0 bg-white/95 backdrop-blur-sm pb-1">
            <a
              id="modal-whatsapp-btn"
              href="https://wa.me/5215540130621"
              target="_blank"
              rel="noopener noreferrer"
              class="w-full inline-flex items-center justify-center gap-2.5 rounded-2xl bg-emerald-600 hover:bg-emerald-700 active:scale-[0.99] text-white px-6 py-3.5 text-sm sm:text-base font-semibold shadow-sm transition-all"
            >
              <svg class="w-5 h-5 fill-current" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M20.52 3.48A11.86 11.86 0 0012.06 0C5.47 0 .11 5.36.11 11.95c0 2.1.55 4.16 1.6 5.98L0 24l6.24-1.64a11.92 11.92 0 005.82 1.49h.01c6.59 0 11.95-5.36 11.95-11.95 0-3.19-1.24-6.19-3.5-8.42zM12.07 21.84h-.01a9.9 9.9 0 01-5.04-1.38l-.36-.21-3.7.97.99-3.61-.24-.37a9.87 9.87 0 01-1.52-5.29c0-5.46 4.44-9.9 9.9-9.9 2.64 0 5.13 1.03 7 2.9a9.84 9.84 0 012.89 7.01c0 5.46-4.44 9.88-9.91 9.88zm5.43-7.42c-.3-.15-1.76-.87-2.03-.97-.27-.1-.47-.15-.67.15-.2.3-.77.97-.94 1.17-.17.2-.35.22-.64.07-.3-.15-1.26-.46-2.4-1.48-.89-.79-1.49-1.77-1.66-2.07-.17-.3-.02-.46.13-.61.13-.13.3-.35.45-.52.15-.17.2-.3.3-.5.1-.2.05-.37-.02-.52-.07-.15-.67-1.61-.92-2.21-.24-.58-.49-.5-.67-.51h-.57c-.2 0-.52.07-.79.37-.27.3-1.04 1.02-1.04 2.48 0 1.46 1.07 2.88 1.21 3.08.15.2 2.1 3.2 5.08 4.49.71.31 1.26.49 1.69.63.71.23 1.36.2 1.87.12.57-.09 1.76-.72 2.01-1.41.25-.69.25-1.29.17-1.41-.07-.12-.27-.2-.57-.35z"/>
              </svg>
              <span>Pedir por WhatsApp</span>
            </a>
            <p class="mt-2 text-center text-[11px] text-zinc-400">
              Respuesta directa en WhatsApp · Yucatalog
            </p>
          </div>
        </div>

      </div>
    </div>
  </div>

  <!-- ===================================================================== -->
  <!-- 5. JAVASCRIPT: CONFIGURACIÓN, PRODUCTOS, CARRUSEL Y LÓGICA            -->
  <!-- ===================================================================== -->
  <script>
    /**
     * =========================================================================
     * CONFIGURACIÓN GENERAL DE LA TIENDA (EDITA AQUÍ TUS DATOS)
     * =========================================================================
     */
    const CONFIG = {
      nombreTienda: 'Yucatalog',
      subtitulo: 'Catálogo',
      // Número mexicano 5540130621 con lada internacional 521 para enlaces wa.me
      telefonoWhatsApp: '5215540130621',
      moneda: 'MXN',
      mensajeGeneralWhatsApp: 'Hola Yucatalog, me gustaría solicitar información sobre sus productos del catálogo.',
      categorias: ['Todos', 'Automóvil', 'Espejos LED', 'Accesorios']
    };

    /**
     * =========================================================================
     * CATÁLOGO DE PRODUCTOS (EDITA PRECIOS, TEXTOS O AGREGA TUS FOTOS AQUÍ)
     * =========================================================================
     * ¿CÓMO PONER TUS FOTOS REALES?
     * En cada objeto dentro de `imagenes`, pega el enlace directo o ruta local
     * de tu foto en el campo `url: ''` (por ejemplo: url: 'fotos/funda-1.jpg'
     * o url: 'https://tusitio.com/funda-1.jpg').
     *
     * Mientras `url` esté vacío ('') o si una imagen no logra cargarse, el sitio
     * mostrará automáticamente una ilustración SVG personalizada para esa vista.
     */
    const PRODUCTOS = [
      {
        id: 'funda-tpu-metal',
        nombre: 'Funda TPU con Borde Metálico para Llave de Auto',
        precio: 189,
        categoria: 'Automóvil',
        descripcion:
          'Protección elegante contra caídas, golpes y rayones diarios. Fabricada en TPU suave al tacto con un bisel metálico pulido que realza el diseño original de tu llave inteligente.',
        especificaciones: {
          medidas: '8.4 × 4.3 × 1.8 cm',
          material: 'TPU flexible de alta densidad con acabado borde metálico galvanizado',
          contenidoPaquete: '1 funda protectora TPU y 1 argolla metálica con broche',
          variantes: [
            { nombre: 'Negro / Dorado', hex: '#18181B' },
            { nombre: 'Blanco Perla / Plata', hex: '#F4F4F5' },
            { nombre: 'Verde Esmeralda / Oro', hex: '#14532D' }
          ]
        },
        caracteristicas: [
          'Cobertura envolvente 360° que protege botones y carcasa contra impactos.',
          'No bloquea ni reduce el alcance de la señal remota o de proximidad.',
          'Botones marcados en relieve para presionar cómodamente sin sacar la llave.',
          'Acabado brillante resistente a huellas y fácil de limpiar.'
        ],
        imagenes: [
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto principal
            etiquetaVista: 'Vista frontal — TPU y borde metálico',
            svgProducto: 'funda-tpu-metal',
            svgAngulo: 'front'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de detalle
            etiquetaVista: 'Detalle de acabado metálico y botones',
            svgProducto: 'funda-tpu-metal',
            svgAngulo: 'detail'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de medidas/escala
            etiquetaVista: 'Medidas y perfil ergonómico',
            svgProducto: 'funda-tpu-metal',
            svgAngulo: 'scale'
          }
        ]
      },
      {
        id: 'funda-silicon-carbono',
        nombre: 'Funda de Silicón Efecto Fibra de Carbono para Llave',
        precio: 159,
        categoria: 'Automóvil',
        descripcion:
          'Estilo deportivo y agarre antideslizante para tu llave automotriz. Su silicón de grado premium con relieve efecto fibra de carbono absorbe golpes y mantiene tu control como nuevo.',
        especificaciones: {
          medidas: '8.2 × 4.1 × 1.7 cm',
          material: 'Silicón líquido flexible con textura 3D efecto fibra de carbono',
          contenidoPaquete: '1 funda de silicón carbono y 1 correa llavero trenzada',
          variantes: [
            { nombre: 'Negro Carbono', hex: '#1F1F23' },
            { nombre: 'Gris Grafito', hex: '#52525B' },
            { nombre: 'Negro / Línea Roja', hex: '#991B1B' }
          ]
        },
        caracteristicas: [
          'Textura deportiva antideslizante agradable al tacto y fácil de instalar.',
          'Resistente a salpicaduras de agua, polvo y desgaste por uso continuo.',
          'Ultraligera (22 g) y flexible sin perder su forma original.',
          'Señal 100% libre de interferencias para apertura y encendido.'
        ],
        imagenes: [
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto principal
            etiquetaVista: 'Vista frontal — Textura fibra de carbono',
            svgProducto: 'funda-silicon-carbono',
            svgAngulo: 'front'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de detalle
            etiquetaVista: 'Acercamiento a trama 3D antideslizante',
            svgProducto: 'funda-silicon-carbono',
            svgAngulo: 'detail'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de medidas/escala
            etiquetaVista: 'Dimensiones y grosor flexible',
            svgProducto: 'funda-silicon-carbono',
            svgAngulo: 'scale'
          }
        ]
      },
      {
        id: 'espejo-plegable-led',
        nombre: 'Espejo Portátil Plegable con Luz LED Recargable',
        precio: 249,
        categoria: 'Espejos LED',
        descripcion:
          'Espejo de viaje tipo tableta con iluminación LED perimetral táctil y soporte plegable integrado. Ideal para maquillaje, skincare o retoques con luz uniforme en cualquier lugar.',
        especificaciones: {
          medidas: '18.5 × 13.0 × 1.4 cm (plegado)',
          material: 'Plástico ABS mate suave al tacto y cristal óptico HD',
          contenidoPaquete: '1 espejo plegable LED, 1 cable de carga USB-C y manual',
          variantes: [
            { nombre: 'Blanco Perla', hex: '#F4F4F5' },
            { nombre: 'Rosa Pastel', hex: '#F3D5D8' },
            { nombre: 'Negro Mate', hex: '#27272A' }
          ]
        },
        caracteristicas: [
          'Sensor táctil con 3 tonos de luz (cálida, neutra y blanca fría) y brillo regulable.',
          'Batería interna recargable USB-C para usar sin cables durante viajes.',
          'Cubierta protectora que funciona como soporte ajustable hasta 90°.',
          'Diseño ultradelgado y liviano que cabe en mochilas, bolsas o maletas.'
        ],
        imagenes: [
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto principal
            etiquetaVista: 'Vista frontal — Marco LED encendido',
            svgProducto: 'espejo-plegable-led',
            svgAngulo: 'front'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de detalle
            etiquetaVista: '3 temperaturas de luz y botón táctil',
            svgProducto: 'espejo-plegable-led',
            svgAngulo: 'detail'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de medidas/escala
            etiquetaVista: 'Medidas y perfil ultradelgado',
            svgProducto: 'espejo-plegable-led',
            svgAngulo: 'scale'
          }
        ]
      },
      {
        id: 'espejo-compacto-5x',
        nombre: 'Espejo Compacto de Bolsillo con Luz LED y Aumento 5x',
        precio: 179,
        categoria: 'Espejos LED',
        descripcion:
          'Elegante espejo circular de doble cara pensado para llevar siempre en el bolso. Combina vista normal 1x con espejo de aumento 5x iluminado por un aro LED de luz natural.',
        especificaciones: {
          medidas: 'Ø 9.0 × 1.8 cm',
          material: 'Policarbonato satinado y doble cristal espejo de alta definición',
          contenidoPaquete: '1 espejo compacto LED doble cara y 1 cable USB-C',
          variantes: [
            { nombre: 'Champagne', hex: '#E6D3B3' },
            { nombre: 'Rosa Cuarzo', hex: '#E8C5C8' },
            { nombre: 'Blanco Marfil', hex: '#FAF8F5' }
          ]
        },
        caracteristicas: [
          'Doble espejo: cara principal 1x y aumento 5x para detalles de precisión.',
          'Aro LED perimetral de luz natural suave que evita sombras en el rostro.',
          'Cierre magnético seguro y apertura práctica de hasta 120°.',
          'Recargable por USB-C con un peso pluma de solo 85 g.'
        ],
        imagenes: [
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto principal
            etiquetaVista: 'Vista frontal — Doble cara y aro LED',
            svgProducto: 'espejo-compacto-5x',
            svgAngulo: 'front'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de detalle
            etiquetaVista: 'Comparativa cristal 1x vs aumento 5x',
            svgProducto: 'espejo-compacto-5x',
            svgAngulo: 'detail'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de medidas/escala
            etiquetaVista: 'Diámetro compacto y grosor de bolsillo',
            svgProducto: 'espejo-compacto-5x',
            svgAngulo: 'scale'
          }
        ]
      },
      {
        id: 'soporte-magnetico-360',
        nombre: 'Soporte Magnético Plegable 360° para Celular en Auto',
        precio: 199,
        categoria: 'Automóvil',
        descripcion:
          'Mantén tu smartphone firme y en el ángulo perfecto mientras conduces. Su brazo metálico plegable y base giratoria 360° se adaptan al tablero sin estorbar la visibilidad.',
        especificaciones: {
          medidas: '5.8 × 5.8 × 2.3 cm (plegado) · 10.5 cm extendido',
          material: 'Aleación de zinc, aluminio anodizado y almohadilla de silicón suave',
          contenidoPaquete: '1 soporte magnético plegable 360°, 2 aros metálicos y adhesivo 3M extra',
          variantes: [
            { nombre: 'Negro Anodizado', hex: '#18181B' },
            { nombre: 'Gris Titanio', hex: '#52525B' }
          ]
        },
        caracteristicas: [
          'Potente matriz de imanes de neodimio N52 que sujeta con seguridad en baches.',
          'Brazo abatible de doble eje y base rotatoria 360° (vertical u horizontal).',
          'Diseño ultracompacto que se pliega por completo cuando no está en uso.',
          'Compatible con MagSafe y cualquier teléfono usando el aro metálico incluido.'
        ],
        imagenes: [
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto principal
            etiquetaVista: 'Vista frontal — Brazo plegable 360°',
            svgProducto: 'soporte-magnetico-360',
            svgAngulo: 'front'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de detalle
            etiquetaVista: 'Imanes N52 y articulación giratoria',
            svgProducto: 'soporte-magnetico-360',
            svgAngulo: 'detail'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de medidas/escala
            etiquetaVista: 'Medidas plegado y extendido',
            svgProducto: 'soporte-magnetico-360',
            svgAngulo: 'scale'
          }
        ]
      },
      {
        id: 'mini-aspiradora-usb',
        nombre: 'Mini Aspiradora / Soplador Portátil USB para Auto y Escritorio',
        precio: 329,
        categoria: 'Accesorios',
        descripcion:
          'Limpieza rápida sin cables en el interior de tu automóvil, teclado o escritorio. Combina succión de alta potencia y función soplador en un cuerpo ergonómico fácil de guardar en la guantera.',
        especificaciones: {
          medidas: '16.5 × 14.5 × 5.6 cm',
          material: 'ABS de alta resistencia y filtro HEPA lavable reutilizable',
          contenidoPaquete: '1 mini aspiradora/soplador, boquilla larga, cepillo, boquilla sopladora y cable USB-C',
          variantes: [
            { nombre: 'Negro Grafito', hex: '#18181B' },
            { nombre: 'Gris Plata', hex: '#71717A' },
            { nombre: 'Verde Olivo', hex: '#3F4E40' }
          ]
        },
        caracteristicas: [
          'Función 2 en 1: aspira migajas y polvo o sopla suciedad en rejillas y teclados.',
          'Motor compacto de gran succión (6000 Pa) con batería recargable USB-C.',
          'Filtro HEPA desmontable y lavable para mantener el rendimiento como nuevo.',
          'Diseño inalámbrico y ligero (310 g) ideal para guantera o cajón de oficina.'
        ],
        imagenes: [
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto principal
            etiquetaVista: 'Vista lateral — Cuerpo portátil inalámbrico',
            svgProducto: 'mini-aspiradora-usb',
            svgAngulo: 'front'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de detalle
            etiquetaVista: 'Sistema 2 en 1: Succión, Soplador y Filtro HEPA',
            svgProducto: 'mini-aspiradora-usb',
            svgAngulo: 'detail'
          },
          {
            url: '', // <-- Pega aquí la URL o ruta de tu foto de medidas/escala
            etiquetaVista: 'Dimensiones compactas y accesorios',
            svgProducto: 'mini-aspiradora-usb',
            svgAngulo: 'scale'
          }
        ]
      }
    ];

    /**
     * =========================================================================
     * GENERADOR DE ILUSTRACIONES SVG PERSONALIZADAS (RESPALDO AUTOMÁTICO)
     * =========================================================================
     * Crea gráficos vectoriales nítidos estilo estudio fotográfico para las 3
     * vistas de cada uno de los 6 productos. Usa un `uid` único por instancia.
     */
    function crearIlustracionSVG(productoKey, angulo, uid) {
      const id = (name) => `${name}-${uid}`;

      const studioBg = `
        <defs>
          <radialGradient id="${id('bg')}" cx="50%" cy="42%" r="68%">
            <stop offset="0%" stop-color="#FFFFFF"/>
            <stop offset="100%" stop-color="#F1F2F5"/>
          </radialGradient>
          <filter id="${id('shadow')}" x="-20%" y="-20%" width="140%" height="150%">
            <feDropShadow dx="0" dy="14" stdDeviation="12" flood-color="#18181B" flood-opacity="0.14"/>
          </filter>
        </defs>
        <rect width="400" height="400" fill="url(#${id('bg')})"/>
      `;

      const scaleBg = `
        <defs>
          <pattern id="${id('grid')}" width="24" height="24" patternUnits="userSpaceOnUse">
            <path d="M 24 0 L 0 0 0 24" fill="none" stroke="#E4E4E7" stroke-width="0.8"/>
          </pattern>
        </defs>
        <rect width="400" height="400" fill="#FAFAFA"/>
        <rect width="400" height="400" fill="url(#${id('grid')})"/>
      `;

      // ---------------- 1. FUNDA TPU CON BORDE METÁLICO ----------------
      if (productoKey === 'funda-tpu-metal') {
        if (angulo === 'front') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Funda TPU con borde metálico vista frontal">
            ${studioBg}
            <defs>
              <linearGradient id="${id('tpuBody')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#323238"/>
                <stop offset="55%" stop-color="#1F1F23"/>
                <stop offset="100%" stop-color="#111114"/>
              </linearGradient>
              <linearGradient id="${id('goldRim')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#F5E3B8"/>
                <stop offset="45%" stop-color="#D4AF6A"/>
                <stop offset="100%" stop-color="#9A783A"/>
              </linearGradient>
            </defs>
            <ellipse cx="200" cy="348" rx="76" ry="11" fill="#18181B" opacity="0.1"/>
            <g filter="url(#${id('shadow')})">
              <!-- Argolla y broche metálico dorado -->
              <circle cx="200" cy="76" r="23" fill="none" stroke="url(#${id('goldRim')})" stroke-width="7"/>
              <rect x="190" y="96" width="20" height="26" rx="6" fill="url(#${id('goldRim')})"/>
              <rect x="184" y="118" width="32" height="20" rx="6" fill="#27272A"/>
              <!-- Carcasa exterior con borde metálico pulido -->
              <rect x="128" y="134" width="144" height="200" rx="44" fill="url(#${id('goldRim')})"/>
              <!-- Interior TPU negro suave -->
              <rect x="137" y="143" width="126" height="182" rx="37" fill="url(#${id('tpuBody')})"/>
              <!-- Filete metálico interno -->
              <rect x="145" y="151" width="110" height="166" rx="31" fill="none" stroke="url(#${id('goldRim')})" stroke-width="1.4" opacity="0.6"/>
              <!-- 3 Botones en relieve -->
              <rect x="164" y="174" width="72" height="34" rx="12" fill="#27272A" stroke="#52525B" stroke-width="1"/>
              <path d="M194 191 V187 A6 6 0 0 1 206 187 V191 M192 191 H208 V200 H192 Z" fill="none" stroke="#F5E3B8" stroke-width="1.6" stroke-linecap="round"/>
              <rect x="164" y="218" width="72" height="34" rx="12" fill="#27272A" stroke="#52525B" stroke-width="1"/>
              <path d="M194 235 V230 A6 6 0 0 1 206 230 M192 235 H208 V244 H192 Z" fill="none" stroke="#F5E3B8" stroke-width="1.6" stroke-linecap="round"/>
              <rect x="164" y="262" width="72" height="32" rx="12" fill="#27272A" stroke="#52525B" stroke-width="1"/>
              <path d="M186 280 H214 L210 273 H192 Z" fill="none" stroke="#F5E3B8" stroke-width="1.6" stroke-linejoin="round"/>
            </g>
          </svg>`;
        }
        if (angulo === 'detail') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Detalle del borde metálico y TPU">
            ${studioBg}
            <defs>
              <linearGradient id="${id('rimZoom')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#FBF0D3"/>
                <stop offset="50%" stop-color="#D4AF6A"/>
                <stop offset="100%" stop-color="#8C6B30"/>
              </linearGradient>
            </defs>
            <g filter="url(#${id('shadow')})">
              <circle cx="200" cy="186" r="118" fill="#18181B" stroke="#FFFFFF" stroke-width="8"/>
              <clipPath id="${id('clipM')}"><circle cx="200" cy="186" r="110"/></clipPath>
              <g clip-path="url(#${id('clipM')})">
                <rect x="80" y="70" width="240" height="240" fill="#1F1F23"/>
                <!-- Curva del bisel dorado -->
                <path d="M80 218 Q200 165 320 228 L320 256 Q200 193 80 246 Z" fill="url(#${id('rimZoom')})"/>
                <path d="M80 246 Q200 193 320 256 L320 310 L80 310 Z" fill="#111114"/>
                <!-- Reflejo de brillo en TPU -->
                <path d="M100 120 Q190 95 290 135" fill="none" stroke="#FFFFFF" stroke-opacity="0.18" stroke-width="14" stroke-linecap="round"/>
              </g>
            </g>
            <rect x="48" y="328" width="142" height="34" rx="17" fill="#18181B"/>
            <text x="119" y="349" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">Bisel Galvanizado</text>
            <rect x="210" y="328" width="142" height="34" rx="17" fill="#FFFFFF" stroke="#E4E4E7"/>
            <text x="281" y="349" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">TPU Antichoque</text>
          </svg>`;
        }
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Medidas de funda TPU con borde metálico">
          ${scaleBg}
          <rect x="108" y="102" width="112" height="192" rx="34" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <rect x="120" y="114" width="88" height="168" rx="26" fill="none" stroke="#D4AF6A" stroke-width="2" stroke-dasharray="5 3"/>
          <rect x="268" y="102" width="38" height="192" rx="16" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <line x1="78" y1="102" x2="78" y2="294" stroke="#18181B" stroke-width="1.4"/>
          <rect x="52" y="185" width="52" height="24" rx="6" fill="#18181B"/>
          <text x="78" y="201" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">8.4 cm</text>
          <line x1="108" y1="322" x2="220" y2="322" stroke="#18181B" stroke-width="1.4"/>
          <text x="164" y="346" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">4.3 cm</text>
          <line x1="268" y1="322" x2="306" y2="322" stroke="#18181B" stroke-width="1.4"/>
          <text x="287" y="346" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">1.8 cm</text>
          <text x="200" y="62" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">MEDIDAS Y PERFIL</text>
        </svg>`;
      }

      // ---------------- 2. FUNDA SILICÓN EFECTO FIBRA DE CARBONO ----------------
      if (productoKey === 'funda-silicon-carbono') {
        if (angulo === 'front') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Funda silicón fibra de carbono vista frontal">
            ${studioBg}
            <defs>
              <pattern id="${id('carbon')}" width="12" height="12" patternUnits="userSpaceOnUse" patternTransform="rotate(45)">
                <rect width="6" height="6" fill="#2B2B31"/>
                <rect x="6" y="0" width="6" height="6" fill="#18181B"/>
                <rect x="0" y="6" width="6" height="6" fill="#121215"/>
                <rect x="6" y="6" width="6" height="6" fill="#323239"/>
              </pattern>
            </defs>
            <ellipse cx="200" cy="348" rx="76" ry="11" fill="#18181B" opacity="0.1"/>
            <g filter="url(#${id('shadow')})">
              <!-- Correa llavero trenzada -->
              <rect x="184" y="58" width="32" height="62" rx="16" fill="none" stroke="#27272A" stroke-width="8"/>
              <rect x="190" y="106" width="20" height="28" rx="4" fill="#3F3F46"/>
              <!-- Cuerpo de silicón flexible con trama fibra de carbono -->
              <rect x="130" y="132" width="140" height="202" rx="42" fill="url(#${id('carbon')})" stroke="#3F3F46" stroke-width="2.5"/>
              <!-- Franja deportiva superior -->
              <rect x="178" y="148" width="44" height="5" rx="2.5" fill="#DC2626"/>
              <!-- Zona de botones ergonómicos -->
              <rect x="158" y="172" width="84" height="132" rx="22" fill="#09090B" fill-opacity="0.62" stroke="#52525B" stroke-width="1.2"/>
              <circle cx="200" cy="200" r="11" fill="none" stroke="#E4E4E7" stroke-width="1.6"/>
              <line x1="176" y1="226" x2="224" y2="226" stroke="#3F3F46" stroke-width="1.2"/>
              <rect x="191" y="240" width="18" height="14" rx="4" fill="none" stroke="#E4E4E7" stroke-width="1.6"/>
              <line x1="176" y1="268" x2="224" y2="268" stroke="#3F3F46" stroke-width="1.2"/>
              <path d="M188 286 H212 L208 279 H192 Z" fill="none" stroke="#E4E4E7" stroke-width="1.6" stroke-linejoin="round"/>
            </g>
          </svg>`;
        }
        if (angulo === 'detail') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Detalle trama 3D fibra de carbono">
            ${studioBg}
            <defs>
              <pattern id="${id('carbonBig')}" width="22" height="22" patternUnits="userSpaceOnUse" patternTransform="rotate(45)">
                <rect width="11" height="11" fill="#32323A"/>
                <rect x="11" y="0" width="11" height="11" fill="#18181B"/>
                <rect x="0" y="11" width="11" height="11" fill="#111114"/>
                <rect x="11" y="11" width="11" height="11" fill="#3F3F46"/>
              </pattern>
            </defs>
            <g filter="url(#${id('shadow')})">
              <circle cx="200" cy="186" r="118" fill="#18181B" stroke="#FFFFFF" stroke-width="8"/>
              <clipPath id="${id('clipCB')}"><circle cx="200" cy="186" r="108"/></clipPath>
              <g clip-path="url(#${id('clipCB')})">
                <rect x="80" y="70" width="240" height="240" fill="url(#${id('carbonBig')})"/>
                <line x1="80" y1="226" x2="320" y2="164" stroke="#DC2626" stroke-width="5"/>
              </g>
            </g>
            <rect x="46" y="328" width="146" height="34" rx="17" fill="#18181B"/>
            <text x="119" y="349" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">Trama 3D Carbono</text>
            <rect x="208" y="328" width="146" height="34" rx="17" fill="#FFFFFF" stroke="#E4E4E7"/>
            <text x="281" y="349" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">Silicón Flexible</text>
          </svg>`;
        }
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Medidas funda silicón carbono">
          ${scaleBg}
          <rect x="110" y="104" width="110" height="190" rx="34" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <rect x="128" y="138" width="74" height="122" rx="16" fill="none" stroke="#A1A1AA" stroke-width="1.4" stroke-dasharray="4 4"/>
          <rect x="270" y="104" width="36" height="190" rx="15" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <line x1="78" y1="104" x2="78" y2="294" stroke="#18181B" stroke-width="1.4"/>
          <rect x="52" y="186" width="52" height="24" rx="6" fill="#18181B"/>
          <text x="78" y="202" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">8.2 cm</text>
          <line x1="110" y1="322" x2="220" y2="322" stroke="#18181B" stroke-width="1.4"/>
          <text x="165" y="346" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">4.1 cm</text>
          <line x1="270" y1="322" x2="306" y2="322" stroke="#18181B" stroke-width="1.4"/>
          <text x="288" y="346" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">1.7 cm</text>
          <text x="200" y="62" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">ESCALA Y GROSOR</text>
        </svg>`;
      }

      // ---------------- 3. ESPEJO PLEGABLE LED RECARGABLE ----------------
      if (productoKey === 'espejo-plegable-led') {
        if (angulo === 'front') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Espejo portátil plegable LED vista frontal">
            ${studioBg}
            <defs>
              <linearGradient id="${id('glass')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#F8FAFC"/>
                <stop offset="45%" stop-color="#E2E8F0"/>
                <stop offset="60%" stop-color="#FFFFFF"/>
                <stop offset="100%" stop-color="#CBD5E1"/>
              </linearGradient>
              <filter id="${id('glow')}" x="-20%" y="-20%" width="140%" height="140%">
                <feGaussianBlur stdDeviation="5" result="blur"/>
                <feMerge>
                  <feMergeNode in="blur"/>
                  <feMergeNode in="SourceGraphic"/>
                </feMerge>
              </filter>
            </defs>
            <ellipse cx="200" cy="340" rx="116" ry="13" fill="#18181B" opacity="0.09"/>
            <g filter="url(#${id('shadow')})">
              <path d="M132 318 L272 318 L296 334 H108 Z" fill="#E4E4E7" stroke="#D4D4D8" stroke-width="1.5"/>
              <rect x="108" y="64" width="184" height="258" rx="22" fill="#FFFFFF" stroke="#E4E4E7" stroke-width="2"/>
              <rect x="120" y="76" width="160" height="234" rx="15" fill="url(#${id('glass')})"/>
              <path d="M142 76 L176 76 L120 180 L120 138 Z" fill="#FFFFFF" opacity="0.65"/>
              <rect x="131" y="87" width="138" height="212" rx="11" fill="none" stroke="#FFFBEB" stroke-width="5" filter="url(#${id('glow')})"/>
              <rect x="131" y="87" width="138" height="212" rx="11" fill="none" stroke="#FFFFFF" stroke-width="2.5"/>
              <circle cx="200" cy="276" r="11" fill="#FFFFFF" fill-opacity="0.78" stroke="#94A3B8" stroke-width="1.5"/>
              <path d="M200 270 V275 M196 273 A5 5 0 1 0 204 273" fill="none" stroke="#475569" stroke-width="1.6" stroke-linecap="round"/>
            </g>
          </svg>`;
        }
        if (angulo === 'detail') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="3 tonos de luz LED y control táctil">
            ${studioBg}
            <text x="200" y="72" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">3 TEMPERATURAS DE LUZ LED</text>
            <g filter="url(#${id('shadow')})">
              <circle cx="102" cy="162" r="44" fill="#FEF3C7" stroke="#FFFFFF" stroke-width="6"/>
              <circle cx="200" cy="162" r="44" fill="#F8FAFC" stroke="#FFFFFF" stroke-width="6"/>
              <circle cx="298" cy="162" r="44" fill="#E0F2FE" stroke="#FFFFFF" stroke-width="6"/>
            </g>
            <text x="102" y="226" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">Cálida 3000K</text>
            <text x="200" y="226" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">Neutra 4500K</text>
            <text x="298" y="226" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">Fría 6000K</text>
            <rect x="82" y="264" width="236" height="72" rx="20" fill="#FFFFFF" stroke="#E4E4E7" stroke-width="1.5"/>
            <circle cx="124" cy="300" r="18" fill="#F4F4F5" stroke="#18181B" stroke-width="1.5"/>
            <path d="M124 292 V299 M118 296 A7 7 0 1 0 130 296" fill="none" stroke="#18181B" stroke-width="2" stroke-linecap="round"/>
            <text x="156" y="295" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">Sensor táctil + USB-C</text>
            <text x="156" y="313" font-family="Inter, sans-serif" font-size="11" fill="#71717A">Toca para tono · Mantén para brillo</text>
          </svg>`;
        }
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Medidas espejo plegable LED">
          ${scaleBg}
          <rect x="102" y="96" width="136" height="196" rx="16" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <rect x="114" y="108" width="112" height="172" rx="10" fill="none" stroke="#A1A1AA" stroke-width="1.3" stroke-dasharray="4 4"/>
          <rect x="282" y="96" width="24" height="196" rx="8" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <line x1="74" y1="96" x2="74" y2="292" stroke="#18181B" stroke-width="1.4"/>
          <rect x="46" y="182" width="56" height="24" rx="6" fill="#18181B"/>
          <text x="74" y="198" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">18.5 cm</text>
          <line x1="102" y1="322" x2="238" y2="322" stroke="#18181B" stroke-width="1.4"/>
          <text x="170" y="346" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">13.0 cm</text>
          <line x1="282" y1="322" x2="306" y2="322" stroke="#18181B" stroke-width="1.4"/>
          <text x="294" y="346" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">1.4 cm</text>
          <text x="200" y="62" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">MEDIDAS PLEGADO</text>
        </svg>`;
      }

      // ---------------- 4. ESPEJO COMPACTO 5X ----------------
      if (productoKey === 'espejo-compacto-5x') {
        if (angulo === 'front') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Espejo compacto de bolsillo con aro LED vista frontal">
            ${studioBg}
            <defs>
              <linearGradient id="${id('champagne')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#F5EAD6"/>
                <stop offset="55%" stop-color="#E3CCA8"/>
                <stop offset="100%" stop-color="#CBB086"/>
              </linearGradient>
              <linearGradient id="${id('mirrorC')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#FFFFFF"/>
                <stop offset="55%" stop-color="#E2E8F0"/>
                <stop offset="100%" stop-color="#CBD5E1"/>
              </linearGradient>
            </defs>
            <ellipse cx="200" cy="346" rx="102" ry="12" fill="#18181B" opacity="0.09"/>
            <g filter="url(#${id('shadow')})">
              <circle cx="200" cy="148" r="88" fill="url(#${id('champagne')})" stroke="#DFC7A0" stroke-width="2"/>
              <circle cx="200" cy="148" r="76" fill="url(#${id('mirrorC')})"/>
              <circle cx="200" cy="148" r="68" fill="none" stroke="#FFFFFF" stroke-width="6"/>
              <circle cx="200" cy="148" r="68" fill="none" stroke="#FEF3C7" stroke-width="2"/>
              <path d="M162 96 L184 90 L142 162 L134 140 Z" fill="#FFFFFF" opacity="0.6"/>
              <rect x="176" y="232" width="48" height="12" rx="6" fill="#C7AC82"/>
              <ellipse cx="200" cy="292" rx="92" ry="44" fill="url(#${id('champagne')})" stroke="#D6BC93" stroke-width="2"/>
              <ellipse cx="200" cy="288" rx="78" ry="34" fill="url(#${id('mirrorC')})" stroke="#FFFFFF" stroke-width="2.5"/>
              <rect x="180" y="278" width="40" height="20" rx="10" fill="#18181B" opacity="0.85"/>
              <text x="200" y="292" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="700" fill="#FFFFFF">5x</text>
            </g>
          </svg>`;
        }
        if (angulo === 'detail') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Comparativa espejo 1x y aumento 5x">
            ${studioBg}
            <text x="200" y="64" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">DOBLE CRISTAL ÓPTICO HD</text>
            <g filter="url(#${id('shadow')})">
              <circle cx="200" cy="196" r="108" fill="#FFFFFF" stroke="#E3CCA8" stroke-width="8"/>
              <clipPath id="${id('splitM')}"><circle cx="200" cy="196" r="98"/></clipPath>
              <g clip-path="url(#${id('splitM')})">
                <rect x="100" y="96" width="100" height="200" fill="#F1F5F9"/>
                <rect x="200" y="96" width="100" height="200" fill="#E2E8F0"/>
                <circle cx="152" cy="196" r="18" fill="none" stroke="#64748B" stroke-width="2"/>
                <circle cx="248" cy="196" r="42" fill="none" stroke="#18181B" stroke-width="2.5"/>
                <line x1="200" y1="96" x2="200" y2="296" stroke="#FFFFFF" stroke-width="4"/>
              </g>
              <circle cx="200" cy="196" r="96" fill="none" stroke="#FFFBEB" stroke-width="4" stroke-dasharray="12 6"/>
            </g>
            <rect x="58" y="330" width="130" height="32" rx="16" fill="#FFFFFF" stroke="#E4E4E7"/>
            <text x="123" y="350" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">1x Vista Natural</text>
            <rect x="212" y="330" width="130" height="32" rx="16" fill="#18181B"/>
            <text x="277" y="350" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">5x Alta Precisión</text>
          </svg>`;
        }
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Medidas espejo compacto 5x">
          ${scaleBg}
          <circle cx="156" cy="194" r="76" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <circle cx="156" cy="194" r="62" fill="none" stroke="#A1A1AA" stroke-width="1.3" stroke-dasharray="4 4"/>
          <rect x="280" y="118" width="26" height="152" rx="12" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <line x1="293" y1="126" x2="293" y2="262" stroke="#D4D4D8" stroke-width="1.5"/>
          <line x1="80" y1="306" x2="232" y2="306" stroke="#18181B" stroke-width="1.4"/>
          <rect x="126" y="294" width="60" height="24" rx="6" fill="#18181B"/>
          <text x="156" y="310" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">Ø 9.0 cm</text>
          <line x1="280" y1="306" x2="306" y2="306" stroke="#18181B" stroke-width="1.4"/>
          <text x="293" y="332" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">1.8 cm</text>
          <text x="200" y="62" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">DIÁMETRO DE BOLSILLO</text>
        </svg>`;
      }

      // ---------------- 5. SOPORTE MAGNÉTICO PLEGABLE 360° ----------------
      if (productoKey === 'soporte-magnetico-360') {
        if (angulo === 'front') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Soporte magnético plegable 360 vista frontal">
            ${studioBg}
            <defs>
              <linearGradient id="${id('alu360')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#52525B"/>
                <stop offset="50%" stop-color="#27272A"/>
                <stop offset="100%" stop-color="#09090B"/>
              </linearGradient>
              <linearGradient id="${id('bevel360')}" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" stop-color="#E4E4E7"/>
                <stop offset="50%" stop-color="#71717A"/>
                <stop offset="100%" stop-color="#D4D4D8"/>
              </linearGradient>
            </defs>
            <ellipse cx="200" cy="340" rx="100" ry="13" fill="#18181B" opacity="0.1"/>
            <g filter="url(#${id('shadow')})">
              <!-- Base giratoria 360° -->
              <ellipse cx="200" cy="316" rx="82" ry="22" fill="#18181B" stroke="#52525B" stroke-width="2"/>
              <ellipse cx="200" cy="310" rx="68" ry="15" fill="#27272A"/>
              <!-- Brazo metálico abatible -->
              <path d="M180 308 L192 224 H216 L224 308 Z" fill="url(#${id('alu360')})" stroke="#71717A" stroke-width="1.5"/>
              <circle cx="202" cy="296" r="7" fill="#A1A1AA"/>
              <!-- Cabezal magnético circular -->
              <circle cx="200" cy="166" r="88" fill="url(#${id('alu360')})"/>
              <circle cx="200" cy="166" r="80" fill="none" stroke="url(#${id('bevel360')})" stroke-width="5"/>
              <circle cx="200" cy="166" r="70" fill="#18181B"/>
              <!-- Anillo magnético tipo MagSafe -->
              <circle cx="200" cy="166" r="46" fill="none" stroke="#52525B" stroke-width="5" stroke-dasharray="14 6"/>
              <circle cx="200" cy="166" r="18" fill="none" stroke="#A1A1AA" stroke-width="1.5"/>
              <text x="200" y="170" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="700" fill="#E4E4E7">360°</text>
            </g>
          </svg>`;
        }
        if (angulo === 'detail') {
          return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Imanes N52 y brazo plegable 360">
            ${studioBg}
            <text x="200" y="64" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">ANILLO DE IMANES N52 + GIRO 360°</text>
            <g filter="url(#${id('shadow')})">
              <circle cx="200" cy="188" r="94" fill="#18181B" stroke="#D4D4D8" stroke-width="5"/>
              <!-- Anillo de 8 imanes -->
              <g fill="#E4E4E7">
                <circle cx="200" cy="128" r="11"/><circle cx="242" cy="146" r="11"/>
                <circle cx="260" cy="188" r="11"/><circle cx="242" cy="230" r="11"/>
                <circle cx="200" cy="248" r="11"/><circle cx="158" cy="230" r="11"/>
                <circle cx="140" cy="188" r="11"/><circle cx="158" cy="146" r="11"/>
              </g>
              <circle cx="200" cy="188" r="28" fill="#27272A" stroke="#71717A" stroke-width="1.5"/>
              <text x="200" y="193" text-anchor="middle" font-family="Inter, sans-serif" font-size="13" font-weight="700" fill="#FFFFFF">N52</text>
            </g>
            <rect x="48" y="324" width="142" height="34" rx="17" fill="#18181B"/>
            <text x="119" y="345" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">Brazo Plegable</text>
            <rect x="210" y="324" width="142" height="34" rx="17" fill="#FFFFFF" stroke="#E4E4E7"/>
            <text x="281" y="345" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#27272A">Apto MagSafe</text>
          </svg>`;
        }
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Medidas soporte magnético plegable">
          ${scaleBg}
          <!-- Vista plegada -->
          <rect x="86" y="216" width="108" height="38" rx="10" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <line x1="86" y1="236" x2="194" y2="236" stroke="#A1A1AA" stroke-width="1.4" stroke-dasharray="4 4"/>
          <text x="140" y="282" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#52525B">Plegado: 2.3 cm</text>
          <!-- Vista extendida -->
          <rect x="242" y="240" width="76" height="14" rx="5" fill="#FFFFFF" stroke="#27272A" stroke-width="2"/>
          <path d="M272 240 L292 146 L306 149 L288 240 Z" fill="#FFFFFF" stroke="#27272A" stroke-width="2"/>
          <rect x="248" y="114" width="64" height="38" rx="8" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
          <line x1="340" y1="114" x2="340" y2="254" stroke="#18181B" stroke-width="1.4"/>
          <rect x="310" y="172" width="60" height="24" rx="6" fill="#18181B"/>
          <text x="340" y="188" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">10.5 cm</text>
          <line x1="86" y1="316" x2="194" y2="316" stroke="#18181B" stroke-width="1.4"/>
          <text x="140" y="340" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">Base 5.8 cm</text>
          <text x="200" y="62" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">PLEGADO VS EXTENDIDO</text>
        </svg>`;
      }

      // ---------------- 6. MINI ASPIRADORA / SOPLADOR PORTÁTIL USB ----------------
      if (angulo === 'front') {
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Mini aspiradora soplador portátil USB vista lateral">
          ${studioBg}
          <defs>
            <linearGradient id="${id('vacBody')}" x1="0%" y1="0%" x2="100%" y2="100%">
              <stop offset="0%" stop-color="#3F3F46"/>
              <stop offset="55%" stop-color="#27272A"/>
              <stop offset="100%" stop-color="#111114"/>
            </linearGradient>
            <linearGradient id="${id('dustCup')}" x1="0%" y1="0%" x2="0%" y2="100%">
              <stop offset="0%" stop-color="#E4E4E7" stop-opacity="0.88"/>
              <stop offset="100%" stop-color="#A1A1AA" stop-opacity="0.55"/>
            </linearGradient>
          </defs>
          <ellipse cx="206" cy="342" rx="116" ry="12" fill="#18181B" opacity="0.1"/>
          <g filter="url(#${id('shadow')})">
            <!-- Boquilla fina de succión frontal -->
            <path d="M52 154 L126 146 V178 L52 170 Z" fill="#27272A"/>
            <!-- Depósito transparente con filtro HEPA interno -->
            <rect x="122" y="128" width="84" height="68" rx="12" fill="url(#${id('dustCup')})" stroke="#D4D4D8" stroke-width="2"/>
            <!-- Filtro HEPA plisado visible -->
            <rect x="156" y="138" width="40" height="48" rx="6" fill="#FFFFFF" stroke="#D4D4D8" stroke-width="1.5"/>
            <line x1="164" y1="142" x2="164" y2="182" stroke="#CBD5E1" stroke-width="2"/>
            <line x1="172" y1="142" x2="172" y2="182" stroke="#CBD5E1" stroke-width="2"/>
            <line x1="180" y1="142" x2="180" y2="182" stroke="#CBD5E1" stroke-width="2"/>
            <line x1="188" y1="142" x2="188" y2="182" stroke="#CBD5E1" stroke-width="2"/>
            <!-- Cuerpo motor principal -->
            <rect x="200" y="124" width="114" height="76" rx="22" fill="url(#${id('vacBody')})"/>
            <!-- Rejilla trasera de salida / soplador -->
            <line x1="302" y1="140" x2="302" y2="184" stroke="#71717A" stroke-width="3" stroke-linecap="round"/>
            <line x1="292" y1="138" x2="292" y2="186" stroke="#52525B" stroke-width="3" stroke-linecap="round"/>
            <!-- Mango ergonómico inclinado -->
            <path d="M236 196 H286 L304 316 C306 326 298 332 288 332 H256 C246 332 240 326 238 316 Z" fill="url(#${id('vacBody')})"/>
            <!-- Botón de encendido con aro LED -->
            <circle cx="248" cy="222" r="10" fill="#18181B" stroke="#10B981" stroke-width="2.5"/>
            <circle cx="248" cy="222" r="3" fill="#10B981"/>
            <!-- Detalle plateado en unión -->
            <rect x="198" y="124" width="8" height="76" rx="2" fill="#D4D4D8"/>
          </g>
        </svg>`;
      }
      if (angulo === 'detail') {
        return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Sistema 2 en 1 succión, soplador y filtro HEPA">
          ${studioBg}
          <text x="200" y="64" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">SISTEMA 2 EN 1 + FILTRO HEPA LAVABLE</text>
          <g filter="url(#${id('shadow')})">
            <!-- Tarjeta Succión -->
            <rect x="48" y="100" width="140" height="122" rx="22" fill="#18181B"/>
            <path d="M90 156 H146 M108 140 L90 156 L108 172" fill="none" stroke="#FFFFFF" stroke-width="3.2" stroke-linecap="round" stroke-linejoin="round"/>
            <text x="118" y="200" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#FFFFFF">Succión 6000 Pa</text>
            <!-- Tarjeta Soplador -->
            <rect x="212" y="100" width="140" height="122" rx="22" fill="#FFFFFF" stroke="#E4E4E7" stroke-width="2"/>
            <path d="M254 156 H310 M292 140 L310 156 L292 172" fill="none" stroke="#18181B" stroke-width="3.2" stroke-linecap="round" stroke-linejoin="round"/>
            <text x="282" y="200" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">Modo Soplador</text>
          </g>
          <!-- Módulo inferior Filtro HEPA y Carga USB-C -->
          <rect x="48" y="252" width="304" height="84" rx="20" fill="#FFFFFF" stroke="#E4E4E7" stroke-width="1.5"/>
          <rect x="74" y="274" width="44" height="40" rx="8" fill="#F4F4F5" stroke="#A1A1AA" stroke-width="1.5"/>
          <line x1="84" y1="278" x2="84" y2="310" stroke="#71717A" stroke-width="2"/>
          <line x1="96" y1="278" x2="96" y2="310" stroke="#71717A" stroke-width="2"/>
          <line x1="108" y1="278" x2="108" y2="310" stroke="#71717A" stroke-width="2"/>
          <text x="136" y="290" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">Filtro HEPA Lavable + USB-C</text>
          <text x="136" y="308" font-family="Inter, sans-serif" font-size="11" fill="#71717A">Incluye 3 boquillas para auto y teclado</text>
        </svg>`;
      }
      return `<svg viewBox="0 0 400 400" class="w-full h-full" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Medidas mini aspiradora portátil USB">
        ${scaleBg}
        <!-- Silueta técnica lateral -->
        <rect x="94" y="120" width="194" height="66" rx="18" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
        <path d="M214 186 H262 L274 282 H228 Z" fill="#FFFFFF" stroke="#27272A" stroke-width="2.2"/>
        <line x1="174" y1="120" x2="174" y2="186" stroke="#A1A1AA" stroke-width="1.5" stroke-dasharray="4 4"/>
        <!-- Cota horizontal 16.5 cm -->
        <line x1="94" y1="94" x2="288" y2="94" stroke="#18181B" stroke-width="1.4"/>
        <rect x="162" y="82" width="58" height="24" rx="6" fill="#18181B"/>
        <text x="191" y="98" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">16.5 cm</text>
        <!-- Cota vertical 14.5 cm -->
        <line x1="316" y1="120" x2="316" y2="282" stroke="#18181B" stroke-width="1.4"/>
        <rect x="288" y="190" width="58" height="24" rx="6" fill="#18181B"/>
        <text x="317" y="206" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" fill="#FFFFFF">14.5 cm</text>
        <!-- Nota de profundidad -->
        <text x="200" y="334" text-anchor="middle" font-family="Inter, sans-serif" font-size="12" font-weight="600" fill="#18181B">Ancho: 5.6 cm · Peso: 310 g</text>
        <text x="200" y="56" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" font-weight="600" letter-spacing="1.2" fill="#71717A">ESCALA COMPACTA PARA GUANTERA</text>
      </svg>`;
    }

    /**
     * =========================================================================
     * ESTADO DE LA APLICACIÓN Y REFERENCIAS AL DOM
     * =========================================================================
     */
    const state = {
      categoriaActiva: 'Todos',
      terminoBusqueda: '',
      productoActivo: null,
      indiceImagenActiva: 0,
      varianteSeleccionada: '',
      touchStartX: 0,
      touchEndX: 0
    };

    const dom = {
      storeName: document.getElementById('store-name'),
      storeSubtitle: document.getElementById('store-subtitle'),
      footerBrand: document.getElementById('footer-brand'),
      footerRights: document.getElementById('footer-rights'),
      footerWhatsappBtn: document.getElementById('footer-whatsapp-btn'),
      searchInput: document.getElementById('search-input'),
      clearSearchBtn: document.getElementById('clear-search-btn'),
      categoryFilters: document.getElementById('category-filters'),
      catalogGrid: document.getElementById('catalog-grid'),
      emptyState: document.getElementById('empty-state'),
      resetFiltersBtn: document.getElementById('reset-filters-btn'),
      mobileCount: document.getElementById('mobile-count'),
      desktopCount: document.getElementById('desktop-count'),
      // Modal y carrusel
      modal: document.getElementById('product-modal'),
      modalBackdrop: document.getElementById('modal-backdrop'),
      modalPanel: document.getElementById('modal-panel'),
      modalCloseBtn: document.getElementById('modal-close-btn'),
      carouselStage: document.getElementById('carousel-stage'),
      carouselMainMedia: document.getElementById('carousel-main-media'),
      carouselCaption: document.getElementById('carousel-caption'),
      carouselCounter: document.getElementById('carousel-counter'),
      carouselDots: document.getElementById('carousel-dots'),
      carouselPrevBtn: document.getElementById('carousel-prev-btn'),
      carouselNextBtn: document.getElementById('carousel-next-btn'),
      carouselThumbnails: document.getElementById('carousel-thumbnails'),
      modalCategory: document.getElementById('modal-category'),
      modalTitle: document.getElementById('modal-product-title'),
      modalPrice: document.getElementById('modal-product-price'),
      modalDescription: document.getElementById('modal-product-description'),
      specMedidas: document.getElementById('spec-medidas'),
      specMaterial: document.getElementById('spec-material'),
      specContenido: document.getElementById('spec-contenido'),
      specVariantes: document.getElementById('spec-variantes'),
      selectedVariantLabel: document.getElementById('selected-variant-label'),
      modalFeatures: document.getElementById('modal-features'),
      modalWhatsappBtn: document.getElementById('modal-whatsapp-btn')
    };

    /**
     * Formatea precios en pesos mexicanos (ej. $189 MXN)
     */
    function formatearPrecio(precio) {
      const numero = Number(precio).toLocaleString('es-MX', {
        minimumFractionDigits: 0,
        maximumFractionDigits: 2
      });
      return `$${numero} ${CONFIG.moneda}`;
    }

    /**
     * Genera enlaces wa.me con el número internacional de CONFIG y texto codificado
     */
    function crearEnlaceWhatsApp(mensaje) {
      const telefonoLimpio = String(CONFIG.telefonoWhatsApp).replace(/\D/g, '');
      return `https://wa.me/${telefonoLimpio}?text=${encodeURIComponent(mensaje)}`;
    }

    /**
     * Normaliza texto para buscar sin distinguir acentos ni mayúsculas
     */
    function normalizarTexto(texto) {
      return String(texto || '')
        .toLowerCase()
        .normalize('NFD')
        .replace(/[\u0300-\u036f]/g, '');
    }

    /**
     * Renderiza una foto real desde `imagenObj.url` y, si está vacía o falla,
     * muestra automáticamente la ilustración SVG personalizada de esa vista.
     */
    function renderizarMedio(contenedor, imagenObj, altText, uid) {
      contenedor.innerHTML = '';

      const fallbackSVG = crearIlustracionSVG(
        imagenObj.svgProducto,
        imagenObj.svgAngulo,
        uid
      );

      if (imagenObj.url && imagenObj.url.trim() !== '') {
        const img = document.createElement('img');
        img.src = imagenObj.url;
        img.alt = altText;
        img.loading = 'lazy';
        img.className = 'w-full h-full object-cover';
        img.onerror = () => {
          contenedor.innerHTML = `<div class="w-full h-full">${fallbackSVG}</div>`;
        };
        contenedor.appendChild(img);
      } else {
        contenedor.innerHTML = `<div class="w-full h-full">${fallbackSVG}</div>`;
      }
    }

    /**
     * =========================================================================
     * FILTROS Y CUADRÍCULA DEL CATÁLOGO
     * =========================================================================
     */
    function renderizarFiltros() {
      dom.categoryFilters.innerHTML = '';

      CONFIG.categorias.forEach((categoria) => {
        const activa = state.categoriaActiva === categoria;
        const btn = document.createElement('button');
        btn.type = 'button';
        btn.textContent = categoria;
        btn.setAttribute('aria-pressed', activa ? 'true' : 'false');
        btn.className = activa
          ? 'shrink-0 rounded-full bg-zinc-900 text-white px-4 py-2 text-xs sm:text-sm font-medium shadow-sm transition-all'
          : 'shrink-0 rounded-full bg-zinc-100 text-zinc-600 hover:bg-zinc-200/80 hover:text-zinc-900 px-4 py-2 text-xs sm:text-sm font-medium transition-all';

        btn.addEventListener('click', () => {
          state.categoriaActiva = categoria;
          renderizarFiltros();
          renderizarCatalogo();
        });

        dom.categoryFilters.appendChild(btn);
      });
    }

    function obtenerProductosFiltrados() {
      const consulta = normalizarTexto(state.terminoBusqueda.trim());

      return PRODUCTOS.filter((producto) => {
        const coincideCategoria =
          state.categoriaActiva === 'Todos' ||
          producto.categoria === state.categoriaActiva;

        if (!coincideCategoria) return false;
        if (!consulta) return true;

        const textoCompleto = normalizarTexto([
          producto.nombre,
          producto.categoria,
          producto.descripcion,
          producto.especificaciones.material,
          producto.especificaciones.medidas,
          producto.especificaciones.contenidoPaquete,
          ...producto.caracteristicas,
          ...producto.especificaciones.variantes.map((v) => v.nombre)
        ].join(' '));

        return textoCompleto.includes(consulta);
      });
    }

    function renderizarCatalogo() {
      const lista = obtenerProductosFiltrados();

      dom.mobileCount.textContent = lista.length === 1 ? '1 producto' : `${lista.length} productos`;
      dom.desktopCount.textContent =
        lista.length === 1 ? 'Mostrando 1 producto' : `Mostrando ${lista.length} productos`;

      dom.catalogGrid.innerHTML = '';

      if (lista.length === 0) {
        dom.emptyState.classList.remove('hidden');
        return;
      }

      dom.emptyState.classList.add('hidden');

      lista.forEach((producto, index) => {
        const card = document.createElement('article');
        card.setAttribute('tabindex', '0');
        card.setAttribute('role', 'button');
        card.setAttribute('aria-label', `Ver detalles de ${producto.nombre}, precio ${formatearPrecio(producto.precio)}`);
        card.className =
          'group cursor-pointer rounded-2xl bg-white border border-zinc-200/75 shadow-card hover:shadow-card-hover hover:-translate-y-0.5 hover:border-zinc-300 overflow-hidden flex flex-col transition-all duration-300 focus:outline-none focus:ring-2 focus:ring-zinc-900/25 animate-fade-up';
        card.style.animationDelay = `${Math.min(index * 40, 200)}ms`;

        // Marco cuadrado de imagen con zoom sutil al pasar el cursor
        const mediaWrapper = document.createElement('div');
        mediaWrapper.className = 'relative aspect-square w-full bg-zinc-50 overflow-hidden';

        const mediaBox = document.createElement('div');
        mediaBox.className = 'w-full h-full transition-transform duration-500 ease-out group-hover:scale-105';
        renderizarMedio(mediaBox, producto.imagenes[0], producto.nombre, `card-${producto.id}`);
        mediaWrapper.appendChild(mediaBox);

        // Aviso sutil en hover que invita a ver detalles
        const hoverCue = document.createElement('div');
        hoverCue.className =
          'pointer-events-none absolute inset-x-3 bottom-3 flex justify-center opacity-0 translate-y-1.5 group-hover:opacity-100 group-hover:translate-y-0 transition-all duration-200';
        hoverCue.innerHTML = `
          <span class="rounded-full bg-zinc-900/85 backdrop-blur-sm text-white text-[11px] font-medium px-3.5 py-1.5 shadow-sm">
            Ver detalles
          </span>
        `;
        mediaWrapper.appendChild(hoverCue);

        // Debajo de la imagen: ÚNICAMENTE nombre del producto y precio en MXN
        const body = document.createElement('div');
        body.className = 'p-3.5 sm:p-4 flex-1 flex flex-col justify-between gap-2';
        body.innerHTML = `
          <h2 class="text-[13px] sm:text-[15px] font-medium text-zinc-900 leading-snug line-clamp-2 group-hover:text-zinc-700 transition-colors">
            ${producto.nombre}
          </h2>
          <p class="text-sm sm:text-base font-bold text-zinc-900 tracking-tight">
            ${formatearPrecio(producto.precio)}
          </p>
        `;

        card.appendChild(mediaWrapper);
        card.appendChild(body);

        card.addEventListener('click', () => abrirModal(producto));
        card.addEventListener('keydown', (e) => {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            abrirModal(producto);
          }
        });

        dom.catalogGrid.appendChild(card);
      });
    }

    /**
     * =========================================================================
     * MODAL DE PRODUCTO Y CARRUSEL INTERACTIVO
     * =========================================================================
     */
    function abrirModal(producto) {
      try {
        state.productoActivo = producto;
        state.indiceImagenActiva = 0;
        state.varianteSeleccionada = producto.especificaciones.variantes[0]?.nombre || '';

        dom.modalCategory.textContent = producto.categoria;
        dom.modalTitle.textContent = producto.nombre;
        dom.modalPrice.textContent = formatearPrecio(producto.precio);
        dom.modalDescription.textContent = producto.descripcion;

        // Especificaciones técnicas
        dom.specMedidas.textContent = producto.especificaciones.medidas;
        dom.specMaterial.textContent = producto.especificaciones.material;
        dom.specContenido.textContent = producto.especificaciones.contenidoPaquete;

        renderizarVariantesModal(producto);

        // Características principales
        dom.modalFeatures.innerHTML = '';
        producto.caracteristicas.forEach((item) => {
          const li = document.createElement('li');
          li.className = 'flex items-start gap-2.5';
          li.innerHTML = `
            <span class="mt-0.5 shrink-0 w-4 h-4 rounded-full bg-zinc-900 text-white flex items-center justify-center">
              <svg class="w-2.5 h-2.5" fill="none" stroke="currentColor" stroke-width="3" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7"/>
              </svg>
            </span>
            <span class="leading-relaxed">${item}</span>
          `;
          dom.modalFeatures.appendChild(li);
        });

        actualizarBotonWhatsAppModal();
        renderizarCarrusel();

        dom.modal.classList.remove('hidden');
        dom.modal.classList.add('flex');
        document.body.style.overflow = 'hidden';

        requestAnimationFrame(() => {
          dom.modalBackdrop.classList.remove('opacity-0');
          dom.modalBackdrop.classList.add('opacity-100');
          dom.modalPanel.classList.remove('opacity-0', 'scale-95');
          dom.modalPanel.classList.add('opacity-100', 'scale-100');
        });

        dom.modalCloseBtn.focus();
      } catch (error) {
        console.error('Error al abrir el modal del producto:', error);
      }
    }

    function cerrarModal() {
      if (!state.productoActivo) return;

      dom.modalBackdrop.classList.remove('opacity-100');
      dom.modalBackdrop.classList.add('opacity-0');
      dom.modalPanel.classList.remove('opacity-100', 'scale-100');
      dom.modalPanel.classList.add('opacity-0', 'scale-95');

      setTimeout(() => {
        dom.modal.classList.add('hidden');
        dom.modal.classList.remove('flex');
        document.body.style.overflow = '';
        state.productoActivo = null;
      }, 180);
    }

    function renderizarVariantesModal(producto) {
      dom.specVariantes.innerHTML = '';
      dom.selectedVariantLabel.textContent = state.varianteSeleccionada;

      producto.especificaciones.variantes.forEach((variante) => {
        const activa = variante.nombre === state.varianteSeleccionada;
        const btn = document.createElement('button');
        btn.type = 'button';
        btn.setAttribute('aria-label', `Seleccionar variante ${variante.nombre}`);
        btn.className = activa
          ? 'inline-flex items-center gap-1.5 rounded-full bg-white border-2 border-zinc-900 px-2.5 py-1 text-xs font-medium text-zinc-900 shadow-sm transition-all'
          : 'inline-flex items-center gap-1.5 rounded-full bg-white border border-zinc-200 hover:border-zinc-400 px-2.5 py-1 text-xs font-medium text-zinc-600 transition-all';

        btn.innerHTML = `
          <span class="w-3.5 h-3.5 rounded-full border border-black/15 shrink-0" style="background-color: ${variante.hex};"></span>
          <span>${variante.nombre}</span>
        `;

        btn.addEventListener('click', () => {
          state.varianteSeleccionada = variante.nombre;
          renderizarVariantesModal(producto);
          actualizarBotonWhatsAppModal();
        });

        dom.specVariantes.appendChild(btn);
      });
    }

    function actualizarBotonWhatsAppModal() {
      if (!state.productoActivo) return;
      const p = state.productoActivo;
      const varianteTexto = state.varianteSeleccionada ? ` (${state.varianteSeleccionada})` : '';
      const mensaje = `Hola Yucatalog, me interesa pedir: "${p.nombre}"${varianteTexto} con precio de ${formatearPrecio(p.precio)}. ¿Lo tienen disponible?`;
      dom.modalWhatsappBtn.href = crearEnlaceWhatsApp(mensaje);
    }

    function renderizarCarrusel() {
      const producto = state.productoActivo;
      if (!producto) return;

      const imagenes = producto.imagenes;
      const total = imagenes.length;
      const actual = imagenes[state.indiceImagenActiva];

      renderizarMedio(
        dom.carouselMainMedia,
        actual,
        `${producto.nombre} - ${actual.etiquetaVista}`,
        `main-${producto.id}-${state.indiceImagenActiva}`
      );

      dom.carouselCaption.textContent = actual.etiquetaVista || 'Detalle del producto';
      dom.carouselCounter.textContent = `${state.indiceImagenActiva + 1} / ${total}`;

      // Indicadores de puntos (dots)
      dom.carouselDots.innerHTML = '';
      imagenes.forEach((_, idx) => {
        const esActiva = idx === state.indiceImagenActiva;
        const dot = document.createElement('button');
        dot.type = 'button';
        dot.setAttribute('aria-label', `Ir a la vista ${idx + 1}`);
        dot.className = esActiva
          ? 'h-1.5 w-6 rounded-full bg-zinc-900 transition-all'
          : 'h-1.5 w-1.5 rounded-full bg-zinc-300 hover:bg-zinc-400 transition-all';
        dot.addEventListener('click', () => {
          state.indiceImagenActiva = idx;
          renderizarCarrusel();
        });
        dom.carouselDots.appendChild(dot);
      });

      // Miniaturas clicables
      dom.carouselThumbnails.innerHTML = '';
      imagenes.forEach((imgObj, idx) => {
        const esActiva = idx === state.indiceImagenActiva;
        const thumbBtn = document.createElement('button');
        thumbBtn.type = 'button';
        thumbBtn.setAttribute('aria-label', `Ver vista ${idx + 1}: ${imgObj.etiquetaVista}`);
        thumbBtn.className = esActiva
          ? 'relative aspect-square rounded-xl overflow-hidden bg-white ring-2 ring-zinc-900 ring-offset-2 transition-all'
          : 'relative aspect-square rounded-xl overflow-hidden bg-white border border-zinc-200 opacity-70 hover:opacity-100 transition-all';

        renderizarMedio(
          thumbBtn,
          imgObj,
          imgObj.etiquetaVista,
          `thumb-${producto.id}-${idx}`
        );

        thumbBtn.addEventListener('click', () => {
          state.indiceImagenActiva = idx;
          renderizarCarrusel();
        });

        dom.carouselThumbnails.appendChild(thumbBtn);
      });
    }

    function navegarCarrusel(direccion) {
      if (!state.productoActivo) return;
      const total = state.productoActivo.imagenes.length;
      state.indiceImagenActiva = (state.indiceImagenActiva + direccion + total) % total;
      renderizarCarrusel();
    }

    /**
     * =========================================================================
     * EVENTOS DE INTERACCIÓN (BUSCADOR, TECLADO Y GESTOS SWIPE)
     * =========================================================================
     */
    function registrarEventos() {
      dom.searchInput.addEventListener('input', (e) => {
        state.terminoBusqueda = e.target.value;
        dom.clearSearchBtn.classList.toggle('hidden', state.terminoBusqueda.length === 0);
        renderizarCatalogo();
      });

      dom.clearSearchBtn.addEventListener('click', () => {
        state.terminoBusqueda = '';
        dom.searchInput.value = '';
        dom.clearSearchBtn.classList.add('hidden');
        dom.searchInput.focus();
        renderizarCatalogo();
      });

      dom.resetFiltersBtn.addEventListener('click', () => {
        state.categoriaActiva = 'Todos';
        state.terminoBusqueda = '';
        dom.searchInput.value = '';
        dom.clearSearchBtn.classList.add('hidden');
        renderizarFiltros();
        renderizarCatalogo();
      });

      dom.modalCloseBtn.addEventListener('click', cerrarModal);
      dom.modalBackdrop.addEventListener('click', cerrarModal);
      dom.carouselPrevBtn.addEventListener('click', () => navegarCarrusel(-1));
      dom.carouselNextBtn.addEventListener('click', () => navegarCarrusel(1));

      // Navegación por teclado (flechas izquierda/derecha y Escape)
      document.addEventListener('keydown', (e) => {
        if (!state.productoActivo) return;
        if (e.key === 'Escape') {
          cerrarModal();
        } else if (e.key === 'ArrowLeft') {
          e.preventDefault();
          navegarCarrusel(-1);
        } else if (e.key === 'ArrowRight') {
          e.preventDefault();
          navegarCarrusel(1);
        }
      });

      // Soporte táctil swipe (deslizar izquierda/derecha)
      dom.carouselStage.addEventListener('touchstart', (e) => {
        state.touchStartX = e.changedTouches[0].screenX;
      }, { passive: true });

      dom.carouselStage.addEventListener('touchend', (e) => {
        state.touchEndX = e.changedTouches[0].screenX;
        const deltaX = state.touchEndX - state.touchStartX;
        if (Math.abs(deltaX) >= 40) {
          navegarCarrusel(deltaX < 0 ? 1 : -1);
        }
      }, { passive: true });
    }

    /**
     * =========================================================================
     * INICIALIZACIÓN
     * =========================================================================
     */
    function inicializarTienda() {
      try {
        document.title = `${CONFIG.nombreTienda} | ${CONFIG.subtitulo}`;
        dom.storeName.textContent = CONFIG.nombreTienda;
        dom.storeSubtitle.textContent = CONFIG.subtitulo;
        dom.footerBrand.textContent = CONFIG.nombreTienda;

        const anioActual = new Date().getFullYear();
        dom.footerRights.textContent = `© ${anioActual} ${CONFIG.nombreTienda}. Todos los derechos reservados · Precios en ${CONFIG.moneda}.`;
        dom.footerWhatsappBtn.href = crearEnlaceWhatsApp(CONFIG.mensajeGeneralWhatsApp);

        renderizarFiltros();
        renderizarCatalogo();
        registrarEventos();
      } catch (error) {
        console.error('Error al inicializar Yucatalog:', error);
      }
    }

    document.addEventListener('DOMContentLoaded', inicializarTienda);
  </script>
</body>
</html>
```
