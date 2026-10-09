# SISTEG-Site — Entrega comercial (staging)

Rama: `feature/commercial-positioning-2026`
Destino cPanel: `https://www.sisteg.net/newsite/`
Producción principal: NO modificar hasta aprobación.

## Alcance implementado
- Sección de cuatro soluciones comerciales: asistentes IA y búsqueda, registro/acreditación de eventos, Microsoft 365, automatización e integraciones.
- Navegación y CTA hacia soluciones y contacto.
- Copys en español e inglés, con sobrescritura de las claves anteriores.
- Formulario existente: se preserva el webhook n8n y se amplía el selector de servicios.
- Se eliminan porcentajes y velocidades de supuestos casos sin evidencia.
- Meta robots `noindex, nofollow` en staging. **Retirar esta etiqueta solo cuando se apruebe publicación en la raíz de producción.**
- Se preservan logos, CSS y assets existentes.

## Pruebas manuales antes de aprobar
1. En cPanel: Update from Remote > Deploy HEAD Commit para esta rama.
2. Abrir /newsite/ en escritorio y móvil. Verificar logo, imágenes, estilos y anclas.
3. Cambiar ES/EN y comprobar hero, tarjetas, opciones del formulario, metadatos y navegación.
4. Enviar solicitud de prueba con etiqueta inequívoca y confirmar su recepción en n8n; comprobar errores de CORS si aparecen.
5. Confirmar que el HTML de /newsite/ incluye `noindex, nofollow` y que no se ha alterado /.
6. Revisar accesibilidad por teclado, contraste, formularios y errores de consola.
7. Confirmar los textos comerciales y la autorización de cualquier referencia a clientes.

## Producción
Antes de publicar en /: quitar `noindex, nofollow`, validar canonical y Open Graph para URL definitiva, verificar sitemap y Search Console, asegurar HTTPS, y revisar redirects. No publicar automáticamente por cambiar de rama.

## Notas
La rama conserva el sitio estático en un único `index.html`; no se ha migrado a framework ni se han añadido dependencias. La comprobación de extremo a extremo depende de ejecutar el despliegue en cPanel y probar el webhook real.
