# 📱 TikTok App Desktop - Documentación Completa

## 🎯 Descripción General

Esta documentación cubre la implementación completa de una aplicación TikTok para escritorio, diseñada para funcionar dentro de un sistema de ventanas flotantes estilo Windows en WordPress con Elementor.

---

## 📁 Estructura de Archivos

```
TikTokApp-Desktop/
├── tiktok-app-completa.html          # Widget principal (sidebar + header + navegación)
├── seccion-parati.html               # Widget para la sección "Para Ti"
├── seccion-explorar.html             # Widget para la sección "Explorar"
├── seccion-siguiendo.html            # Widget para la sección "Siguiendo"
├── integrar-ventanaflotante-tiktokapp.html  # Integración con ventanas flotantes
└── DOCUMENTACION.md                  # Este archivo
```

---

## 🏗️ Arquitectura del Sistema

### Estructura en Elementor

```
📄 Página Lobby (Principal)
├── 📦 Contenedor 1: Escritorio
│   └── 🔧 apps-escritorio.html
│       └── Icono TikTok (data-window-id="tiktok-window")
│
├── 📦 Contenedor 2: Taskbar
│   └── 🔧 taskbar-inteligente.html
│
└── 📦 Contenedor 3: Widgets del Sistema
    ├── 🔧 ventanas-flotantes-windows.html
    ├── 🔧 gestion-ventanas-y-taskbar.html
    └── 🔧 integrar-ventanaflotante-tiktokapp.html

📄 Template Elementor: "TikTok App" [ID: XXXX]
└── 📦 Contenedor Principal
    └── 🔧 tiktok-app-completa.html
        └── [mi_plantilla id="ID_PARA_TI"]   (Para Ti)
        └── [mi_plantilla id="ID_EXPLORAR"]  (Explorar)
        └── [mi_plantilla id="ID_SIGUIENDO"] (Siguiendo)

📄 Template Elementor: "Para Ti" [ID: ID_PARA_TI]
└── 🔧 seccion-parati.html

📄 Template Elementor: "Explorar" [ID: ID_EXPLORAR]
└── 🔧 seccion-explorar.html

📄 Template Elementor: "Siguiendo" [ID: ID_SIGUIENDO]
└── 🔧 seccion-siguiendo.html

📄 Template Elementor: "Comentarios Video X" [ID: ID_COMENTARIOS_X]
└── Diseño de comentarios en Elementor Site Builder

📄 Template Elementor: "Reseñas" [ID: ID_RESENAS]
└── Diseño de reseñas en Elementor Site Builder
```

---

## 🎨 Personalización del UI

### 1. tiktok-app-completa.html

#### Variables CSS (líneas 180-210)

```css
:root {
  /* 📏 DIMENSIONES */
  --tiktok-header-height: 40px;        /* Altura del header */
  --tiktok-sidebar-width: 240px;       /* Ancho del sidebar */
  --tiktok-sidebar-collapsed: 72px;    /* Ancho colapsado (responsive) */
  
  /* 🎨 COLORES */
  --tiktok-bg-primary: #000000;        /* Fondo principal */
  --tiktok-bg-secondary: #121212;      /* Fondo secundario */
  --tiktok-bg-sidebar: #121212;        /* Fondo del sidebar */
  --tiktok-bg-hover: #1f1f1f;          /* Hover en items */
  --tiktok-bg-active: #2f2f2f;         /* Item activo */
  
  --tiktok-text-primary: #ffffff;      /* Texto principal */
  --tiktok-text-secondary: #a0a0a0;    /* Texto secundario */
  --tiktok-text-muted: #5a5a5a;        /* Texto apagado */
  
  --tiktok-accent: #fe2c55;            /* Rojo TikTok */
  --tiktok-accent-hover: #ff3b5c;      /* Hover del acento */
  
  --tiktok-border: rgba(255,255,255,0.1); /* Bordes */
}
```

#### Configuración JavaScript (líneas 415-435)

```javascript
const CONFIG = {
  logoSrc: 'URL_DE_TU_LOGO',      // Logo en el sidebar
  defaultSection: 'para-ti',       // Sección inicial
  transitionDuration: 300,         // Duración animaciones (ms)
  
  templates: {
    'para-ti': 'ID_PARA_TI',
    'explorar': 'ID_EXPLORAR',
    'siguiendo': 'ID_SIGUIENDO',
    'live': 'ID_LIVE',
    'cargar': 'ID_CARGAR',
    'perfil': 'ID_PERFIL'
  }
};
```

#### Navegación del Sidebar (líneas 55-120)

Para añadir/modificar opciones del menú:

```html
<div class="nav-item" data-section="nueva-seccion" data-template-id="ID_TEMPLATE">
  <div class="nav-icon">
    <!-- SVG del icono -->
  </div>
  <span class="nav-label">Nombre de Sección</span>
</div>
```

---

### 2. seccion-parati.html

#### Variables CSS (líneas 90-110)

```css
:root {
  --parati-comments-width: 400px;       /* Ancho panel comentarios */
  --parati-comments-min-width: 320px;
  --parati-header-height: 56px;
  
  --parati-bg: #000000;
  --parati-bg-comments: #1f1f1f;
  --parati-bg-input: #2f2f2f;
  --parati-text: #ffffff;
  --parati-text-secondary: #a0a0a0;
  --parati-accent: #fe2c55;
  --parati-border: rgba(255,255,255,0.1);
}
```

#### Configurar Videos (líneas 380-420)

```javascript
const VIDEOS = [
  {
    id: 'video-1',
    src: 'https://url-del-video.mp4',
    username: '@usuario',
    description: 'Descripción #hashtag',
    aspect: 'vertical',    // 'vertical' | 'square' | 'horizontal'
    likes: '1.2M',
    comments: '5.6K',
    shares: '12.3K',
    saves: '45.2K',
    commentsTemplateId: 'ID_COMENTARIOS_VIDEO_1'  // Plantilla Elementor
  },
  // Más videos...
];
```

#### Switch de Comentarios/Reseñas

El switch alterna entre dos plantillas de Elementor:
- **Comentarios**: Se actualiza según el video actual
- **Reseñas**: Plantilla fija para todos los videos

---

### 3. seccion-explorar.html

#### Variables CSS (líneas 80-100)

```css
:root {
  --explorar-columns: 6;              /* Columnas del grid */
  --explorar-gap: 12px;               /* Espacio entre cards */
  --explorar-card-radius: 8px;        /* Bordes redondeados */
}
```

#### Configurar Videos (líneas 330-380)

```javascript
const VIDEOS = [
  {
    id: 'video-exp-1',
    thumbnail: 'URL_THUMBNAIL',        // Imagen preview
    previewSrc: 'URL_VIDEO_5S',        // Video corto (5s) para hover
    fullSrc: 'URL_VIDEO_COMPLETO',     // Video completo para popup
    username: '@usuario',
    userAvatar: 'URL_AVATAR',
    displayName: 'Nombre',
    description: 'Descripción',
    likes: '666.4K',
    comments: '5.2K',
    date: 'Hace 5 días',
    sound: 'original sound - usuario',
    link: 'https://tiktok.com/@usuario/video/123',
    category: 'comedia',               // Para filtrar
    commentsTemplateId: 'ID_COMENTARIOS'
  },
];
```

#### Categorías

Edita las categorías en el HTML (líneas 25-40):

```html
<div class="category-tab" data-category="mi-categoria">Mi Categoría</div>
```

---

### 4. seccion-siguiendo.html

#### Configurar Creadores (líneas 280-340)

```javascript
const CREATORS = [
  {
    id: 'creator-1',
    username: '@usuario',
    displayName: 'Nombre Completo',
    avatar: 'URL_AVATAR',
    verified: true,
    following: '405',
    followers: '83.7M',
    likes: '4.2B',
    bio: 'Biografía del creador',
    link: 'milink.com',
    previewVideo: 'URL_VIDEO_PREVIEW',
    videos: [
      {
        id: 'video-1',
        thumbnail: 'URL_THUMB',
        src: 'URL_VIDEO',
        likes: '24.6M',
        comments: '120K',
        date: 'Hace 3 días',
        pinned: true,             // Mostrar badge "Anclado"
        commentsTemplateId: 'ID_COMENTARIOS'
      },
    ]
  },
];
```

---

## 🔧 Integración con Ventanas Flotantes

### Configuración (integrar-ventanaflotante-tiktokapp.html)

```javascript
const TIKTOK_WINDOW_CONFIG = {
  windowId: 'tiktok-window',
  appName: 'tiktok',
  defaultWidth: 1400,
  defaultHeight: 800,
  minWidth: 800,
  minHeight: 500,
  taskbarIcon: 'URL_ICONO',
  taskbarLabel: 'TikTok',
  contentTemplateId: 'ID_PLANTILLA_TIKTOK'
};
```

### Abrir la App desde Código

```javascript
// Método 1: Función global
window.openTikTokApp();

// Método 2: Evento
window.dispatchEvent(new Event('open-tiktok-app'));

// Método 3: Sistema de ventanas
window.openWindow('tiktok-window');
```

### Icono en el Escritorio

```html
<div class="desktop-icon" data-window-id="tiktok-window">
  <img src="icono-tiktok.png" alt="TikTok">
  <span>TikTok</span>
</div>
```

---

## 📋 Checklist de Implementación

### Paso 1: Crear Templates en Elementor

- [ ] Template "TikTok App" con `tiktok-app-completa.html`
- [ ] Template "Para Ti" con `seccion-parati.html`
- [ ] Template "Explorar" con `seccion-explorar.html`
- [ ] Template "Siguiendo" con `seccion-siguiendo.html`
- [ ] Templates de comentarios para cada video
- [ ] Template de reseñas general

### Paso 2: Configurar IDs

- [ ] Reemplazar `ID_PARA_TI` con el ID real
- [ ] Reemplazar `ID_EXPLORAR` con el ID real
- [ ] Reemplazar `ID_SIGUIENDO` con el ID real
- [ ] Reemplazar `ID_COMENTARIOS` con los IDs reales
- [ ] Reemplazar `ID_RESENAS` con el ID real

### Paso 3: Añadir Videos

- [ ] Configurar array `VIDEOS` en `seccion-parati.html`
- [ ] Configurar array `VIDEOS` en `seccion-explorar.html`
- [ ] Configurar array `CREATORS` en `seccion-siguiendo.html`

### Paso 4: Integrar con Ventanas

- [ ] Añadir `integrar-ventanaflotante-tiktokapp.html` al Lobby
- [ ] Configurar `TIKTOK_WINDOW_CONFIG`
- [ ] Añadir icono de TikTok al escritorio

### Paso 5: Personalizar UI

- [ ] Cambiar logo del sidebar
- [ ] Ajustar colores si es necesario
- [ ] Modificar opciones del menú

---

## 🔌 API Global

### TikTokApp (tiktok-app-completa.html)

```javascript
window.TikTokApp.navigateTo('explorar');
window.TikTokApp.getCurrentSection();
window.TikTokApp.updateSectionContent('para-ti', htmlContent);
window.TikTokApp.getConfig();
```

### ParaTiPlayer (seccion-parati.html)

```javascript
window.ParaTiPlayer.navigateToVideo(2);
window.ParaTiPlayer.getCurrentVideo();
window.ParaTiPlayer.getCurrentIndex();
window.ParaTiPlayer.toggleMute();
```

### ExplorarSection (seccion-explorar.html)

```javascript
window.ExplorarSection.filterByCategory('comedia');
window.ExplorarSection.openVideoPopup(0);
window.ExplorarSection.closeVideoPopup();
window.ExplorarSection.getVideos();
window.ExplorarSection.addVideo(videoData);
```

### SiguiendoSection (seccion-siguiendo.html)

```javascript
window.SiguiendoSection.openCreatorView(creatorData);
window.SiguiendoSection.closeCreatorView();
window.SiguiendoSection.openVideoDetail(0);
window.SiguiendoSection.closeVideoDetail();
window.SiguiendoSection.getCreators();
window.SiguiendoSection.addCreator(creatorData);
```

---

## 🎨 Eventos Personalizados

### Escuchar cambios de sección

```javascript
window.addEventListener('tiktok-section-changed', (e) => {
  console.log('Sección actual:', e.detail.section);
});
```

### Escuchar cambios de video

```javascript
window.addEventListener('parati-video-changed', (e) => {
  console.log('Video actual:', e.detail.video);
});
```

### Escuchar acciones en videos

```javascript
window.addEventListener('parati-action', (e) => {
  console.log('Acción:', e.detail.action, 'Video:', e.detail.videoId);
});
```

---

## 💡 Tips y Mejores Prácticas

### Optimización de Videos

1. **Para previews en Explorar/Siguiendo**: Crea versiones de 5 segundos de tus videos
2. **Thumbnails**: Usa imágenes WebP de máximo 200KB
3. **Videos completos**: Usa formato MP4 H.264 para compatibilidad

### Comentarios Dinámicos

Para que cada video tenga sus propios comentarios:

1. Crea una plantilla Elementor por video con los comentarios diseñados
2. Asigna el ID de esa plantilla en `commentsTemplateId` del video
3. El sistema cargará automáticamente la plantilla correcta

### Responsive

- El sidebar se colapsa automáticamente en pantallas < 1200px
- Los grids de Explorar/Siguiendo ajustan columnas automáticamente
- Los popups se adaptan a pantallas pequeñas

---

## 🐛 Solución de Problemas

### El contenido no ocupa el 100%

Verifica que `integrar-ventanaflotante-tiktokapp.html` esté cargado después de `ventanas-flotantes-windows.html`.

### Los controles de ventana no funcionan

Asegúrate de que la ventana tenga `data-app="tiktok"` o `id="tiktok-window"`.

### Los videos no reproducen

1. Verifica que las URLs sean accesibles (CORS)
2. Asegúrate de que el formato sea MP4 H.264
3. Los navegadores requieren interacción del usuario para autoplay con sonido

### El switch de comentarios no cambia

Verifica que los `data-tab` y `data-content` coincidan exactamente.

---

## 📞 Soporte

Si tienes problemas con la implementación:

1. Revisa la consola del navegador (F12) para errores JavaScript
2. Usa los estilos de debug en `integrar-ventanaflotante-tiktokapp.html`
3. Verifica que todos los IDs de plantillas sean correctos

---

**Versión**: 1.0  
**Fecha**: Diciembre 2025  
**Compatibilidad**: WordPress + Elementor Pro
