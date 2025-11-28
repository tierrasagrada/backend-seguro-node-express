# Proyecto de Biografía Multimedia con Acceso Seguro

Este proyecto es una aplicación web ligera basada en **HTML, CSS y JavaScript** en el frontend, y un backend construido en **Node.js + Express**, diseñada para presentar una biografía multimedia (texto, imágenes y videos) de forma controlada y segura. Todo el contenido se libera únicamente cuando el usuario responde correctamente una **pregunta de validación**.

## 🔐 Seguridad Aplicada

El proyecto implementa múltiples capas de seguridad para proteger el contenido, evitando acceso directo, scraping o exposición de rutas internas:

* **Validación previa obligatoria** antes de acceder al contenido (control de intentos + espera progresiva).
* **Protección de imágenes con URLs firmadas mediante JWT** con expiración.
* **Verificación de IP** para evitar reutilización de tokens.
* **Entrega de contenido desde rutas controladas**, sin exponer archivos reales ni rutas internas.
* **Sanitización estricta (DOMPurify)** del contenido dinámico enviado desde el backend.
* **Cookies HTTP-Only seguras** para tokens de autenticación.
* **Token CSRF** entregado desde el backend para cada sesión.
* **Rate-limiting** en validación y acceso a imágenes.
* **CORS restringido**, anti-hotlinking y headers de seguridad.

## 📁 Estructura del Proyecto

```
/api
  ├── csrf-token.js           // Entrega el token CSRF vía cookie HTTP-Only
  ├── validarRespuesta.js     // Valida la respuesta del usuario y controla el acceso
  ├── obtenerImagenes.js      // Lista imágenes y genera URLs firmadas
  ├── urlSeguraImagenes.js    // Entrega imágenes tras validar el token
  └── /protectedimages        // Imágenes privadas del sistema

/assets
  ├── /css                    // Estilos del frontend
  └── /js
      ├── funcionesfrontend.js // Lógica del cliente, fetch, validaciones, UI
      └── ninja-slider.js      // Slider dinámico cargado de forma diferida

vercel.json                    // Configuración de headers, CORS y seguridad
index.html                     // Interfaz principal
```

## 🎯 Posibles usos del sistema

La arquitectura permite adaptarse a diversos escenarios donde el acceso debe ser controlado:

* Formularios que requieren validación segura entre frontend y backend.
* Módulos de autenticación ligera.
* Rutas protegidas para archivos o recursos privados.
* Galerías o catálogos privados sin exponer archivos reales.
* Presentaciones multimedia con acceso condicionado.
* Perfiles o biografías digitales con contenido restringido.

## 📌 Nota final

Este proyecto integra prácticas habituales en sistemas que necesitan:

* Control de acceso avanzado
* Protección de archivos en servidor
* Validación en frontend y backend
* Envío seguro de formularios
* Gestión de tokens, cookies y cabeceras de seguridad

La implementación sirve como base reutilizable para cualquier módulo o sistema que deba manejar contenido sensible o rutas privadas con un enfoque más robusto que un flujo web tradicional.
