# backend-seguro-node-express
📘 Proyecto: Plataforma Web con Acceso Controlado a Biografía Multimedia

Esta aplicación es una plataforma ligera para mostrar contenido multimedia privado (texto, imágenes, música y videos).
El frontend está construido con HTML, CSS y JavaScript, y el backend utiliza Node.js + Express desplegado en Vercel.

El sistema permite mostrar imágenes, un slider dinámico (Ninja Slider), texto y enlaces de YouTube, solo después de superar un filtro de acceso. Para proteger el contenido, se implementan diversas medidas orientadas al control de rutas, validación y seguridad entre cliente y servidor.

🎯 Características Principales

🔹 Frontend (HTML, CSS y JS)

 • Consumo del backend mediante fetch().

 • Validación de entradas del usuario (sanitización y restricciones).

 • Control de intentos con espera progresiva.

 • Manejo dinámico del DOM para mostrar contenido protegido.

 • Sanitización estricta con DOMPurify antes de renderizar HTML.

 • Integración de Ninja Slider cargado dinámicamente.

 • Carga de imágenes mediante URLs firmadas y temporales.

🔹 Backend (Node.js + Express)
<p align="left">
<img src="https://img.shields.io/badge/STATUS-EN%20DESAROLLO-green">
</p>
Estructura del backend en la carpeta /api:

 • ´/validarRespuesta.js´ – valida el acceso e inicia el flujo seguro.
<code data-start="1591" data-end="1613">/validarRespuesta.js</code>
 • /obtenerImagenes.js – genera URLs temporales con JWT.

 • /urlSeguraImagenes.js – sirve imágenes solo si el token es válido y coincide la IP.

 • /csrf-token.js – genera token CSRF mediante cookies HTTP-Only.

 • /protectedimages/ – carpeta privada donde se almacenan las imágenes.

Medidas implementadas:

 • Tokens temporales JWT vinculados a IP.

 • Rate limiting y manejo de errores.

 • Protección CSRF por cookie segura.

 • Verificación de Referer y anti-hotlinking.

 • Headers de seguridad configurados mediante vercel.json.

 • Acceso exclusivo por método POST en rutas críticas.

 • Evita exponer rutas reales o nombres directos de archivos.

🔐 Seguridad Aplicada

El proyecto incluye varias prácticas de seguridad que permiten controlar el acceso a contenido y proteger rutas backend:

 • Validación de formularios y sanitización de entradas.

 • Rutas backend con restricciones de método (solo POST).

 • Generación y verificación de tokens CSRF.

 • Cookies HTTP-Only y SameSite estricto.

 • JWT con expiración para enlaces privados.

 • Bloqueo por IP y limitación de intentos.

 • Limpieza del HTML recibido antes de imprimirlo en el DOM.

 • Ocultación estructural de archivos privados.

 • Content Security Policy estricta para scripts, imágenes e iframes.

Estas técnicas permiten construir formularios seguros, manejar datos de usuario con restricciones, proteger rutas, evitar ejecuciones no autorizadas y controlar la entrega de archivos privados.

🧩 Posibles Usos

 • La arquitectura permite adaptar este sistema a diferentes contextos:

 • Formularios que requieren validaciones fuertes entre frontend y backend.

 • Plataformas con acceso controlado antes de mostrar contenido.

 • Galerías privadas o catálogos que no deben exponerse directamente.

 • Portafolios o presentaciones personalizadas con protección de archivos.

 • Sistemas que necesiten rutas temporales o firmadas antes de entregar archivos.

 • Módulos que requieren sanitización estricta de HTML o validación de entradas.

📝 Conocimientos Aplicados en el Proyecto

Validación y sanitización de formularios del lado del cliente.

Manejo de peticiones seguras entre frontend y backend.

Control de flujo con tokens (CSRF, JWT).

Implementación de headers de seguridad y restricciones CSP.

Protección de rutas API y archivos privados.

Diseño de mecanismos para evitar scraping básico y hotlinking.

Integración de contenido multimedia de forma controlada.

📄 Licencia / Repositorio

(Aquí puedes agregar la licencia, tecnologías del stack, comandos de instalación, o instrucciones si lo deseas.)
