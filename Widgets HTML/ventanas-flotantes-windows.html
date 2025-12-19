<!-- 
  ============================================
  VENTANA FLOTANTE - VERSIÓN FINAL CORREGIDA
  ============================================
  
  ✅ Drag sin saltos
  ✅ Resize sin saltos - HEIGHT DINÁMICO
  ✅ Taskbar (minimizar, restaurar, cerrar)
  ✅ Animaciones suaves estilo Windows 11
  ✅ Estado preservado al minimizar/restaurar
  ✅ Scroll funcional en contenido interno
-->

<style>
/* ===== OCULTAR VENTANA POR DEFECTO ===== */
.app-window {
  display: none !important;
  visibility: hidden;
  opacity: 0;
}

.app-window.show {
  display: flex !important;
  visibility: visible;
  opacity: 1;
}

/* Snap overlays */
.snap-overlay {
  position: fixed;
  top: 0;
  pointer-events: none;
  background: rgba(255, 255, 255, 0.15);
  border: 3px solid rgba(255, 255, 255, 0.5);
  border-radius: 15px;
  opacity: 0;
  transition: opacity 0.2s ease;
  z-index: 99999; /* Muy alto para estar sobre todo */
  margin: 6px;
  box-sizing: border-box;
}

.snap-overlay.active { 
  opacity: 1; 
  display: block;
}

/* Snap izquierda - 50% width */
.snap-overlay.left { 
  left: 0; 
  width: calc(50vw - 9px); 
  height: calc(100vh - 48px - 12px); /* Restar taskbar y margins */
}

/* Snap derecha - 50% width */
.snap-overlay.right { 
  right: 0; 
  left: auto;
  width: calc(50vw - 9px); 
  height: calc(100vh - 48px - 12px); 
}

/* Snap superior - 100% (maximizar) */
.snap-overlay.top { 
  top: 0;
  left: 0; 
  width: calc(100vw - 12px); 
  height: calc(100vh - 48px - 12px); 
}

/* Ventana - estilos base */
.app-window {
  position: fixed;
  width: 1552px;
  height: 748px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #121212;
  border-radius: 8px;
  box-shadow: 0 10px 40px rgba(0,0,0,0.5);
  z-index: 1000;
  flex-direction: column;
  overflow: hidden;
  /* CRUCIAL: Aísla el layout para mejorar rendimiento */
  contain: layout style;
  /* IMPORTANTE: Flexbox para que el contenido se estire */
  display: flex; 
}

/* ==============================================
   FIX CRÍTICO ELEMENTOR (CSS RESET PARA VENTANA)
   ============================================== */

/* 1. Forzar que el contenedor principal de Elementor ocupe el 100% de la ventana */
.window-content > .elementor {
  height: 100% !important;
  width: 100% !important;
}

/* 2. Corregir los wrappers internos de Elementor que colapsan la altura */
.window-content .elementor-section-wrap,
.window-content .elementor-inner,
.window-content .elementor-container,
.window-content .elementor-column-wrap, 
.window-content .elementor-widget-wrap {
  height: 100% !important;
  display: flex !important;
  flex-direction: column !important;
  flex: 1 !important;
}

/* 3. OVERRIDE MAESTRO: Anular el 100vh de Elementor */
.window-content .elementor-section.elementor-section-height-full,
.window-content .elementor-section.elementor-section-height-min-height {
  height: 100% !important; /* Usa % del padre, no vh del navegador */
  min-height: 0 !important; /* Permite encogerse */
  flex: 1 !important;
}

/* 4. Asegurar que el widget HTML dentro de Elementor se expanda */
.window-content .elementor-widget-html {
  height: 100% !important;
  flex: 1 !important;
}
.window-content .elementor-widget-container {
  height: 100% !important;
  display: flex !important;
  flex-direction: column !important;
}

/* ============================================== */

/* Animaciones (Mantener igual que antes) */
@keyframes windowOpen {
  from { opacity: 0; transform: translate(-50%, -50%) scale(0.95); }
  to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
}
.app-window.opening { animation: windowOpen 0.2s cubic-bezier(0.1, 0.9, 0.2, 1) forwards; }

.app-window.closing { opacity: 0; transition: opacity 0.2s; pointer-events: none; }
.app-window.minimizing { opacity: 0; transform: scale(0.8) translateY(200px); transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); }

/* Estados de ventana */
.app-window.maximized {
  width: 100vw !important;
  height: calc(100vh - 48px) !important; /* Restar taskbar */
  top: 0 !important;
  left: 0 !important;
  transform: none !important;
  border-radius: 0;
}

/* Animación snap */
.app-window.animating-snap {
  transition: all 0.2s ease;
}

.app-window.snapped-left {
  width: 50vw !important;
  height: calc(100vh - 48px) !important;
  top: 0 !important;
  left: 0 !important;
  transform: none !important;
  border-radius: 0;
}

.app-window.snapped-right {
  width: 50vw !important;
  height: calc(100vh - 48px) !important;
  top: 0 !important;
  right: 0 !important;
  left: auto !important;
  transform: none !important;
  border-radius: 0;
}

/* Snap superior = Maximizar con snap */
.app-window.snapped-top {
  width: 100vw !important;
  height: calc(100vh - 48px) !important;
  top: 0 !important;
  left: 0 !important;
  transform: none !important;
  border-radius: 0;
}

.app-window.minimized {
  display: none !important;
}

/* Área draggable - Ahora es solo visual para mostrar cursor */
/* El drag real se maneja escuchando en la ventana directamente */
.window-drag-area {
  position: absolute;
  top: 0; 
  left: 0; 
  right: 0; 
  height: 64px; /* Altura del header de Spotify */
  z-index: 1; /* Bajo, solo para cursor */
  cursor: move;
  pointer-events: none; /* No captura eventos, solo muestra cursor */
}

/* Los elementos interactivos del header Spotify deben tener z-index mayor */
.spotify-header .header-left,
.spotify-header .header-center,
.spotify-header .header-right,
.spotify-header .header-btn,
.spotify-header .search-container,
.spotify-header .search-input,
.spotify-header button,
.spotify-header input {
  position: relative;
  z-index: 20 !important; /* Mayor que window-drag-area */
  pointer-events: auto !important;
}

/* Cursor move para el header de Spotify (área draggable) */
.spotify-header {
  cursor: move;
}

/* Cursor normal para elementos interactivos dentro del header */
.spotify-header button,
.spotify-header input,
.spotify-header a,
.spotify-header .header-btn,
.spotify-header .search-input,
.spotify-header .search-container {
  cursor: pointer;
}
.spotify-header input[type="text"],
.spotify-header .search-input {
  cursor: text;
}

/* CONTENIDO DE LA VENTANA */
.window-content {
  flex: 1; /* Ocupa todo el espacio restante */
  position: relative;
  overflow: hidden; /* El scroll lo maneja el hijo */
  background: #121212;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

/* Scrollbar personalizada global dentro de la ventana */
.window-content *::-webkit-scrollbar { width: 6px; height: 6px; }
.window-content *::-webkit-scrollbar-track { background: transparent; }
.window-content *::-webkit-scrollbar-thumb { background: rgba(255,255,255,0.2); border-radius: 3px; }
.window-content *::-webkit-scrollbar-thumb:hover { background: rgba(255,255,255,0.4); }

/* Handles de redimensión (Mantener igual) */
.resize-handle { position: absolute; background: transparent; z-index: 100; }
.resize-handle.resize-right { top: 10px; bottom: 10px; right: -2px; width: 10px; cursor: ew-resize; }
.resize-handle.resize-left { top: 10px; bottom: 10px; left: -2px; width: 10px; cursor: ew-resize; }
.resize-handle.resize-bottom { bottom: -2px; left: 10px; right: 10px; height: 10px; cursor: ns-resize; }
.resize-handle.resize-top { top: -2px; left: 10px; right: 10px; height: 10px; cursor: ns-resize; }
.resize-handle.resize-bottom-right { bottom: -5px; right: -5px; width: 20px; height: 20px; cursor: nwse-resize; z-index: 101; }
/* ... resto de handles ... */

</style>

<!-- Snap overlays -->
<div class="snap-overlay left" id="snapOverlayLeft"></div>
<div class="snap-overlay right" id="snapOverlayRight"></div>
<div class="snap-overlay top" id="snapOverlayTop"></div>

<!-- VENTANA NOTEPAD -->
<div class="app-window" id="window-notepad">
  <div class="window-drag-area"></div>
  <div class="resize-handle resize-top-left"></div>
  <div class="resize-handle resize-top-right"></div>
  <div class="resize-handle resize-bottom-left"></div>
  <div class="resize-handle resize-bottom-right"></div>
  <div class="resize-handle resize-top"></div>
  <div class="resize-handle resize-bottom"></div>
  <div class="resize-handle resize-left"></div>
  <div class="resize-handle resize-right"></div>
  
  <div class="window-content" id="window-content-notepad">
    [mi_plantilla id="2899"]
  </div>
</div>

<!-- VENTANA CALCULATOR -->
<div class="app-window" id="window-calculator">
  <div class="window-drag-area"></div>
  <div class="resize-handle resize-top-left"></div>
  <div class="resize-handle resize-top-right"></div>
  <div class="resize-handle resize-bottom-left"></div>
  <div class="resize-handle resize-bottom-right"></div>
  <div class="resize-handle resize-top"></div>
  <div class="resize-handle resize-bottom"></div>
  <div class="resize-handle resize-left"></div>
  <div class="resize-handle resize-right"></div>
  
  <div class="window-content" id="window-content-calculator">
    [mi_plantilla id="TU_ID_CALCULATOR"]
  </div>
</div>

<!-- VENTANA EXPLORER -->
<div class="app-window" id="window-explorer">
  <div class="window-drag-area"></div>
  <div class="resize-handle resize-top-left"></div>
  <div class="resize-handle resize-top-right"></div>
  <div class="resize-handle resize-bottom-left"></div>
  <div class="resize-handle resize-bottom-right"></div>
  <div class="resize-handle resize-top"></div>
  <div class="resize-handle resize-bottom"></div>
  <div class="resize-handle resize-left"></div>
  <div class="resize-handle resize-right"></div>
  
  <div class="window-content" id="window-content-explorer">
    [mi_plantilla id="TU_ID_EXPLORER"]
  </div>
</div>

<script>
// ============================================
// SISTEMA DE VENTANAS - VERSIÓN MEJORADA
// Con altura dinámica y scroll robusto
// ============================================
(function() {
  
  // Configuración global
  const INITIAL_WIDTH = 1152;
  const INITIAL_HEIGHT = 648;
  
  // Función para inicializar una ventana
  function initWindow(windowId) {
    const windowElement = document.getElementById(windowId);
    if (!windowElement) return;
    
    const dragArea = windowElement.querySelector('.window-drag-area');
    const windowContent = windowElement.querySelector('.window-content');
    const resizeHandles = windowElement.querySelectorAll('.resize-handle');
    const snapOverlayLeft = document.getElementById('snapOverlayLeft');
    const snapOverlayRight = document.getElementById('snapOverlayRight');
    const snapOverlayTop = document.getElementById('snapOverlayTop');
    
    let isMaximized = false;
    let isSnapped = false;
    let isResizing = false;
    
    // Estado guardado para restaurar después de minimizar
    let beforeMaximize = { 
      width: INITIAL_WIDTH + 'px', 
      height: INITIAL_HEIGHT + 'px', 
      top: '50%', 
      left: '50%', 
      transform: 'translate(-50%, -50%)' 
    };
    
    // Estado antes de minimizar (para preservar posición exacta)
    let beforeMinimize = null;
    
    // ===== FUNCIÓN PARA FORZAR RECÁLCULO DE ALTURA =====
    function forceLayoutRecalc() {
      // Forzar recálculo del layout
      windowContent.style.display = 'none';
      windowContent.offsetHeight; // Force reflow
      windowContent.style.display = '';
      
      // Buscar contenedor spotify y forzar su recálculo
      const spotifyContainer = windowContent.querySelector('.spotify-app-container');
      if (spotifyContainer) {
        spotifyContainer.style.height = '100%';
        spotifyContainer.offsetHeight; // Force reflow
      }
      
      // Buscar elementos con scroll y refrescarlos
      refreshScrollElements();
    }
    
    // ===== FUNCIÓN PARA REFRESCAR ELEMENTOS CON SCROLL =====
    function refreshScrollElements() {
      const scrollables = windowContent.querySelectorAll('.spotify-content, .sidebar-lists-container, [style*="overflow"]');
      
      scrollables.forEach(function(el) {
        // Guardar posición de scroll
        const scrollTop = el.scrollTop;
        
        // Forzar recálculo de overflow
        const originalOverflow = el.style.overflow;
        el.style.overflow = 'hidden';
        el.offsetHeight; // Force reflow
        el.style.overflow = originalOverflow || '';
        
        // Restaurar posición de scroll
        el.scrollTop = scrollTop;
        
        // Asegurar que el scroll funcione
        if (el.scrollHeight > el.clientHeight) {
          el.style.overflowY = 'auto';
        }
      });
    }
    
    // ===== SCROLL MEJORADO =====
    // Manejar scroll en elementos internos, no en window-content
    function setupScrollHandling() {
      // El scroll lo manejan los elementos internos (.spotify-content, .sidebar-lists-container)
      // No bloquear eventos de wheel
      
      const scrollableElements = windowContent.querySelectorAll('.spotify-content, .sidebar-lists-container');
      
      scrollableElements.forEach(function(el) {
        // Remover listeners previos (si existen)
        el.removeEventListener('wheel', handleWheel);
        
        // Agregar listener de wheel
        el.addEventListener('wheel', handleWheel, { passive: false });
      });
    }
    
    function handleWheel(e) {
      const el = e.currentTarget;
      
      // Calcular si estamos en los límites
      const atTop = el.scrollTop <= 0;
      const atBottom = el.scrollTop + el.clientHeight >= el.scrollHeight - 1;
      
      // Si estamos en el límite y tratamos de seguir scrolleando, prevenir
      if ((atTop && e.deltaY < 0) || (atBottom && e.deltaY > 0)) {
        e.preventDefault();
        e.stopPropagation();
      } else {
        // Permitir scroll normal pero detener propagación
        e.stopPropagation();
      }
    }
    
    // Configurar scroll inicial y después de cambios
    setTimeout(setupScrollHandling, 100);
    setTimeout(setupScrollHandling, 500);
    setTimeout(setupScrollHandling, 1500);
    
    // Observer para detectar cuando se agregan nuevos elementos scrolleables
    const mutationObserver = new MutationObserver(function() {
      setTimeout(setupScrollHandling, 100);
    });
    
    mutationObserver.observe(windowContent, { 
      childList: true, 
      subtree: true 
    });
    
    // ResizeObserver para detectar cambios de tamaño
    const resizeObserver = new ResizeObserver(function() {
      refreshScrollElements();
    });
    resizeObserver.observe(windowContent);
    
    // ===== DRAG - CÓDIGO ORIGINAL SIN MODIFICAR =====
    makeDraggable(windowElement, dragArea);
    
    windowElement.addEventListener('mousedown', function() {
      if (!isResizing) {
        bringToFront(this);
      }
    });
    
    // ===== RESIZE - CÓDIGO ORIGINAL SIN MODIFICAR =====
    resizeHandles.forEach(handle => {
      handle.addEventListener('mousedown', function(e) {
        startResize(e, this);
      });
      
      handle.addEventListener('mouseenter', function() {
        if (!isMaximized && !isSnapped) {
          document.body.style.cursor = window.getComputedStyle(this).cursor;
        }
      });
      
      handle.addEventListener('mouseleave', function() {
        if (!isResizing) {
          document.body.style.cursor = 'default';
        }
      });
    });
    
    // ===== FUNCIÓN DRAG - REESCRITA PARA FUNCIONAR CON SPOTIFY =====
    // En lugar de usar un elemento separado window-drag-area (que es bloqueado por el contenido),
    // escuchamos directamente en la ventana y verificamos si el click fue en el área del header
    function makeDraggable(windowElement, handle) {
      let showingSnapZone = false;
      let isDragging = false;
      let dragOffsetX = 0;
      let dragOffsetY = 0;
      
      const DRAG_AREA_HEIGHT = 64; // Altura del header de Spotify
      
      // Escuchar en la VENTANA, no solo en el handle
      windowElement.addEventListener('mousedown', dragMouseDown);
      
      function dragMouseDown(e) {
        if (isResizing) return;
        
        // Obtener posición del click relativa a la ventana
        const rect = windowElement.getBoundingClientRect();
        const clickY = e.clientY - rect.top;
        
        // Solo permitir drag si el click fue en los primeros 64px (área del header)
        if (clickY > DRAG_AREA_HEIGHT) {
          return; // Click fuera del área de drag
        }
        
        // Verificar si el click fue en un elemento interactivo
        const target = e.target;
        
        // Lista de tags HTML interactivos
        const interactiveTags = ['BUTTON', 'INPUT', 'A', 'SELECT', 'TEXTAREA', 'LABEL', 'SVG', 'PATH'];
        
        // Lista de clases que indican elementos interactivos
        const interactiveClasses = [
          'header-btn', 'search-input', 'category-btn', 'sidebar-item',
          'control-btn', 'window-control', 'nav-btn', 'search-container'
        ];
        
        // Verificar si el elemento clickeado o algún padre es interactivo
        let checkElement = target;
        
        while (checkElement && checkElement !== windowElement) {
          // Verificar por tag name
          if (interactiveTags.includes(checkElement.tagName)) {
            return; // No iniciar drag, dejar que el elemento maneje el click
          }
          
          // Verificar por clase
          if (checkElement.classList) {
            for (let className of interactiveClasses) {
              if (checkElement.classList.contains(className)) {
                return; // No iniciar drag
              }
            }
          }
          
          // Verificar resize handles
          if (checkElement.classList && checkElement.classList.contains('resize-handle')) {
            return; // No iniciar drag en handles de resize
          }
          
          checkElement = checkElement.parentElement;
        }
        
        // ¡Podemos iniciar el drag!
        dragOffsetX = e.clientX - rect.left;
        dragOffsetY = e.clientY - rect.top;
        
        // Si está maximizado, restaurar primero
        if (windowElement.classList.contains('maximized')) {
          const mouseXPercent = dragOffsetX / rect.width;
          restoreFromMaximize();
          const newRect = windowElement.getBoundingClientRect();
          
          windowElement.style.left = (e.clientX - newRect.width * mouseXPercent) + 'px';
          windowElement.style.top = (e.clientY - dragOffsetY) + 'px';
          windowElement.style.transform = 'none';
          
          dragOffsetX = newRect.width * mouseXPercent;
          
        } else if (isSnapped) {
          // Si está en snap, restaurar primero
          restoreFromSnap();
          const newRect = windowElement.getBoundingClientRect();
          windowElement.style.left = (e.clientX - newRect.width / 2) + 'px';
          windowElement.style.top = (e.clientY - dragOffsetY) + 'px';
          windowElement.style.transform = 'none';
          
          dragOffsetX = newRect.width / 2;
        }
        
        // Prevenir selección de texto durante drag
        e.preventDefault();
        isDragging = true;
        
        // Cambiar cursor
        document.body.style.cursor = 'move';
        
        document.addEventListener('mouseup', closeDragElement);
        document.addEventListener('mousemove', elementDrag);
      }
      
      function elementDrag(e) {
        if (!isDragging) return;
        e.preventDefault();
        
        const newLeft = e.clientX - dragOffsetX;
        const newTop = e.clientY - dragOffsetY;
        
        windowElement.style.left = newLeft + "px";
        windowElement.style.top = newTop + "px";
        windowElement.style.transform = "none";
        
        // Snap zones - detectar cuando el cursor está cerca de los bordes
        const snapThreshold = 20;
        const mouseX = e.clientX;
        const mouseY = e.clientY;
        const windowWidth = window.innerWidth;
        
        // Función helper para limpiar todos los overlays
        function clearAllOverlays() {
          if (snapOverlayLeft) snapOverlayLeft.classList.remove('active');
          if (snapOverlayRight) snapOverlayRight.classList.remove('active');
          if (snapOverlayTop) snapOverlayTop.classList.remove('active');
        }
        
        // Prioridad: Superior > Izquierda > Derecha
        if (mouseY <= snapThreshold) {
          // Zona superior - Maximizar
          clearAllOverlays();
          if (snapOverlayTop) {
            snapOverlayTop.classList.add('active');
          }
          showingSnapZone = 'top';
        } else if (mouseX <= snapThreshold) {
          // Zona izquierda - 50%
          clearAllOverlays();
          if (snapOverlayLeft) {
            snapOverlayLeft.classList.add('active');
          }
          showingSnapZone = 'left';
        } else if (mouseX >= windowWidth - snapThreshold) {
          // Zona derecha - 50%
          clearAllOverlays();
          if (snapOverlayRight) {
            snapOverlayRight.classList.add('active');
          }
          showingSnapZone = 'right';
        } else {
          // Fuera de todas las zonas de snap
          clearAllOverlays();
          showingSnapZone = false;
        }
      }
      
      function closeDragElement() {
        if (!isDragging) return;
        
        isDragging = false;
        document.body.style.cursor = 'default';
        document.removeEventListener('mouseup', closeDragElement);
        document.removeEventListener('mousemove', elementDrag);
        
        // Aplicar snap si estamos en una zona de snap
        if (showingSnapZone === 'top') {
          snapWindow('top');
        } else if (showingSnapZone === 'left') {
          snapWindow('left');
        } else if (showingSnapZone === 'right') {
          snapWindow('right');
        }
        
        // Limpiar todos los overlays
        if (snapOverlayLeft) snapOverlayLeft.classList.remove('active');
        if (snapOverlayRight) snapOverlayRight.classList.remove('active');
        if (snapOverlayTop) snapOverlayTop.classList.remove('active');
        showingSnapZone = false;
      }
    }
    
    // ===== FUNCIÓN RESIZE - MEJORADA CON RECÁLCULO DE ALTURA =====
    function startResize(e, handle) {
      if (isMaximized || isSnapped) return;
      
      e.preventDefault();
      e.stopPropagation();
      
      isResizing = true;
      
      const computedStyle = window.getComputedStyle(windowElement);
      const transformValue = computedStyle.transform;
      
      if (transformValue && transformValue !== 'none') {
        const rect = windowElement.getBoundingClientRect();
        windowElement.style.left = rect.left + 'px';
        windowElement.style.top = rect.top + 'px';
        windowElement.style.transform = 'none';
      }
      
      const rect = windowElement.getBoundingClientRect();
      const startX = e.clientX;
      const startY = e.clientY;
      const startWidth = rect.width;
      const startHeight = rect.height;
      const startLeft = rect.left;
      const startTop = rect.top;
      
      const cursor = window.getComputedStyle(handle).cursor;
      document.body.style.cursor = cursor;
      document.body.style.userSelect = 'none';
      
      // Throttle para el resize
      let resizeRAF = null;
      
      function resize(e) {
        if (resizeRAF) return;
        
        resizeRAF = requestAnimationFrame(function() {
          const deltaX = e.clientX - startX;
          const deltaY = e.clientY - startY;
          
          let newWidth = startWidth;
          let newHeight = startHeight;
          let newLeft = startLeft;
          let newTop = startTop;
          
          if (handle.classList.contains('resize-right') || 
              handle.classList.contains('resize-top-right') || 
              handle.classList.contains('resize-bottom-right')) {
            newWidth = Math.max(400, startWidth + deltaX);
          }
          
          if (handle.classList.contains('resize-left') || 
              handle.classList.contains('resize-top-left') || 
              handle.classList.contains('resize-bottom-left')) {
            newWidth = Math.max(400, startWidth - deltaX);
            newLeft = startLeft + (startWidth - newWidth);
          }
          
          if (handle.classList.contains('resize-bottom') || 
              handle.classList.contains('resize-bottom-left') || 
              handle.classList.contains('resize-bottom-right')) {
            newHeight = Math.max(300, startHeight + deltaY);
          }
          
          if (handle.classList.contains('resize-top') || 
              handle.classList.contains('resize-top-left') || 
              handle.classList.contains('resize-top-right')) {
            newHeight = Math.max(300, startHeight - deltaY);
            newTop = startTop + (startHeight - newHeight);
          }
          
          // Aplicar dimensiones
          windowElement.style.width = newWidth + 'px';
          windowElement.style.height = newHeight + 'px';
          windowElement.style.left = newLeft + 'px';
          windowElement.style.top = newTop + 'px';
          
          // Notificar al contenido que la ventana cambió de tamaño
          windowElement.dispatchEvent(new CustomEvent('windowResize', { 
            detail: { 
              width: newWidth, 
              height: newHeight 
            } 
          }));
          
          resizeRAF = null;
        });
      }
      
      function stopResize() {
        if (resizeRAF) {
          cancelAnimationFrame(resizeRAF);
        }
        
        document.removeEventListener('mousemove', resize);
        document.removeEventListener('mouseup', stopResize);
        document.body.style.cursor = 'default';
        document.body.style.userSelect = '';
        isResizing = false;
        
        // Forzar recálculo de layout después del resize
        forceLayoutRecalc();
        
        // Notificar que terminó el resize
        windowElement.dispatchEvent(new CustomEvent('windowResizeEnd', { 
          detail: { 
            width: windowElement.offsetWidth, 
            height: windowElement.offsetHeight 
          } 
        }));
      }
      
      document.addEventListener('mousemove', resize);
      document.addEventListener('mouseup', stopResize);
    }
    
    // ===== ACCIONES DE VENTANA =====
    function handleWindowAction(action) {
      switch(action) {
        case 'close':
          // Remover de taskbar primero
          if (window.removeFromTaskbarGlobal) {
            window.removeFromTaskbarGlobal(windowId);
          }
          
          windowElement.classList.add('closing');
          setTimeout(() => {
            // Ocultar ventana
            windowElement.style.display = 'none';
            
            // Limpiar TODAS las clases
            windowElement.classList.remove('show', 'closing', 'opening', 'minimizing', 'maximized', 'snapped-left', 'snapped-right', 'snapped-top', 'minimized');
            
            // Resetear estados internos
            isMaximized = false;
            isSnapped = false;
            beforeMinimize = null;
            
            // Resetear posición para próxima apertura
            windowElement.style.top = '50%';
            windowElement.style.left = '50%';
            windowElement.style.transform = 'translate(-50%, -50%)';
            windowElement.style.width = INITIAL_WIDTH + 'px';
            windowElement.style.height = INITIAL_HEIGHT + 'px';
            windowElement.style.zIndex = '1000';
          }, 250);
          break;
          
        case 'minimize':
          // Guardar estado COMPLETO antes de minimizar
          const rect = windowElement.getBoundingClientRect();
          
          // Detectar tipo de snap actual
          let snapType = null;
          if (windowElement.classList.contains('snapped-left')) snapType = 'left';
          else if (windowElement.classList.contains('snapped-right')) snapType = 'right';
          else if (windowElement.classList.contains('snapped-top')) snapType = 'top';
          
          beforeMinimize = {
            width: windowElement.style.width || rect.width + 'px',
            height: windowElement.style.height || rect.height + 'px',
            top: windowElement.style.top || rect.top + 'px',
            left: windowElement.style.left || rect.left + 'px',
            transform: windowElement.style.transform || 'none',
            isMaximized: isMaximized,
            isSnapped: isSnapped,
            snapType: snapType,
            zIndex: windowElement.style.zIndex
          };
          
          // Notificar a la taskbar
          if (window.minimizeWindowGlobal) {
            window.minimizeWindowGlobal(windowId);
          }
          
          // Animación de minimizado
          windowElement.classList.add('minimizing');
          setTimeout(() => {
            windowElement.classList.remove('show', 'minimizing', 'opening');
            windowElement.classList.add('minimized');
            windowElement.style.display = 'none';
          }, 250);
          break;
          
        case 'maximize':
          if (isMaximized) {
            restoreFromMaximize();
          } else {
            maximizeWindow();
          }
          break;
          
        case 'restore':
          // Restaurar desde minimizado
          if (beforeMinimize) {
            windowElement.classList.remove('minimized');
            windowElement.style.display = 'flex';
            windowElement.classList.add('opening');
            
            // Restaurar posición exacta
            windowElement.style.width = beforeMinimize.width;
            windowElement.style.height = beforeMinimize.height;
            windowElement.style.top = beforeMinimize.top;
            windowElement.style.left = beforeMinimize.left;
            windowElement.style.transform = beforeMinimize.transform;
            
            // Restaurar estado
            isMaximized = beforeMinimize.isMaximized;
            isSnapped = beforeMinimize.isSnapped;
            
            if (isMaximized) {
              windowElement.classList.add('maximized');
            }
            if (isSnapped && beforeMinimize.snapType) {
              // Restaurar el tipo de snap guardado
              windowElement.classList.add('snapped-' + beforeMinimize.snapType);
            }
            
            setTimeout(() => {
              windowElement.classList.add('show');
              windowElement.classList.remove('opening');
              forceLayoutRecalc();
            }, 10);
            
            bringToFront(windowElement);
            
            // Notificar a taskbar que ya no está minimizado
            if (window.setTaskbarItemActiveGlobal) {
              window.setTaskbarItemActiveGlobal(windowId, true);
            }
            
            beforeMinimize = null;
          }
          break;
      }
    }
    
    function maximizeWindow() {
      if (isSnapped) {
        restoreFromSnap();
      }
      
      const rect = windowElement.getBoundingClientRect();
      beforeMaximize = {
        width: windowElement.style.width || rect.width + 'px',
        height: windowElement.style.height || rect.height + 'px',
        top: windowElement.style.top,
        left: windowElement.style.left,
        transform: windowElement.style.transform
      };
      
      windowElement.classList.add('animating-maximize');
      windowElement.classList.add('maximized');
      isMaximized = true;
      
      setTimeout(() => {
        windowElement.classList.remove('animating-maximize');
        forceLayoutRecalc();
      }, 200);
    }
    
    function restoreFromMaximize() {
      windowElement.classList.add('animating-maximize');
      windowElement.classList.remove('maximized');
      
      windowElement.style.width = beforeMaximize.width;
      windowElement.style.height = beforeMaximize.height;
      windowElement.style.top = beforeMaximize.top;
      windowElement.style.left = beforeMaximize.left;
      windowElement.style.transform = beforeMaximize.transform;
      
      isMaximized = false;
      
      setTimeout(() => {
        windowElement.classList.remove('animating-maximize');
        forceLayoutRecalc();
      }, 200);
    }
    
    function snapWindow(side) {
      if (isMaximized) return;
      
      const rect = windowElement.getBoundingClientRect();
      beforeMaximize = {
        width: windowElement.style.width || rect.width + 'px',
        height: windowElement.style.height || rect.height + 'px',
        top: windowElement.style.top,
        left: windowElement.style.left,
        transform: windowElement.style.transform
      };
      
      windowElement.classList.add('animating-snap');
      windowElement.classList.add('snapped-' + side);
      isSnapped = true;
      
      setTimeout(() => {
        windowElement.classList.remove('animating-snap');
        forceLayoutRecalc();
      }, 200);
    }
    
    function restoreFromSnap() {
      windowElement.classList.add('animating-snap');
      windowElement.classList.remove('snapped-left', 'snapped-right', 'snapped-top');
      
      windowElement.style.width = beforeMaximize.width;
      windowElement.style.height = beforeMaximize.height;
      windowElement.style.top = beforeMaximize.top;
      windowElement.style.left = beforeMaximize.left;
      windowElement.style.transform = beforeMaximize.transform;
      
      isSnapped = false;
      
      setTimeout(() => {
        windowElement.classList.remove('animating-snap');
        forceLayoutRecalc();
      }, 200);
    }
    
    function bringToFront(windowElement) {
      const allWindows = document.querySelectorAll('.app-window');
      let maxZ = 1000;
      allWindows.forEach(w => {
        const z = parseInt(window.getComputedStyle(w).zIndex) || 1000;
        if (z > maxZ) maxZ = z;
      });
      windowElement.style.zIndex = maxZ + 1;
    }
    
    // ===== FUNCIONES PÚBLICAS =====
    windowElement.openWindow = function() {
      // Caso 1: Ventana ya visible - traer al frente con shake
      if (windowElement.classList.contains('show') && windowElement.style.display !== 'none') {
        bringToFront(windowElement);
        windowElement.style.animation = 'shake 0.3s';
        setTimeout(() => {
          windowElement.style.animation = '';
        }, 300);
        return;
      }
      
      // Caso 2: Ventana minimizada - restaurar
      if (windowElement.classList.contains('minimized') && beforeMinimize) {
        handleWindowAction('restore');
        return;
      }
      
      // Caso 3: Ventana cerrada o estado inicial - abrir nueva
      // Limpiar TODAS las clases de estado
      windowElement.classList.remove('minimized', 'closing', 'minimizing', 'maximized', 'snapped-left', 'snapped-right', 'snapped-top');
      
      // Resetear estados internos
      isMaximized = false;
      isSnapped = false;
      beforeMinimize = null;
      
      // Resetear posición al centro
      windowElement.style.width = INITIAL_WIDTH + 'px';
      windowElement.style.height = INITIAL_HEIGHT + 'px';
      windowElement.style.top = '50%';
      windowElement.style.left = '50%';
      windowElement.style.transform = 'translate(-50%, -50%)';
      
      // Mostrar con animación
      windowElement.style.display = 'flex';
      windowElement.classList.add('opening');
      
      setTimeout(() => {
        windowElement.classList.add('show');
        windowElement.classList.remove('opening');
        forceLayoutRecalc();
        setupScrollHandling();
      }, 10);
      
      bringToFront(windowElement);
    };
    
    windowElement.closeWindow = function() {
      handleWindowAction('close');
    };
    
    windowElement.minimizeWindow = function() {
      handleWindowAction('minimize');
    };
    
    windowElement.maximizeWindow = function() {
      handleWindowAction('maximize');
    };
    
    windowElement.restoreWindow = function() {
      handleWindowAction('restore');
    };
  }
  
  // Inicializar todas las ventanas cuando el DOM esté listo
  function initAllWindows() {
    initWindow('window-notepad');
    initWindow('window-calculator');
    initWindow('window-explorer');
  }
  
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initAllWindows);
  } else {
    initAllWindows();
  }
})();
</script>
