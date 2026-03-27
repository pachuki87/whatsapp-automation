# Contributing to WhatsApp Automation Plugin

¡Gracias por tu interés en contribuir al plugin de WhatsApp Automation para Agent Zero!

## Cómo Contribuir

### Reportando Bugs

Antes de reportar un bug, por favor:
1. Busca en los [issues existentes](https://github.com/agent0ai/whatsapp-automation/issues)
2. Verifica si el problema ya fue reportado
3. Incluye detalles como:
   - Versión del plugin
   - Versión de Chrome
   - Sistema operativo
   - Pasos para reproducir el error
   - Mensajes de error completos

### Sugerencias de Mejoras

Para sugerencias de nuevas características:
1. Primero busca issues existentes
2. Abre un issue con la etiqueta `enhancement`
3. Describe el caso de uso claramente
4. Explica por qué sería útil

### Pull Requests

¡Los pull requests son bienvenidos!

#### Pasos para un PR:
1. Fork del repositorio
2. Crea una rama para tu cambio:
   ```bash
   git checkout -b feature/tu-mejora
   ```
3. Haz tus cambios con commits claros
4. Asegúrate de que los scripts sean ejecutables:
   ```bash
   chmod +x scripts/*.sh
   ```
5. Verifica que plugin.yaml cumple con las especificaciones
6. Push a tu fork
7. Abre un Pull Request

#### Estándares de Código:
- Scripts bash: usa `set -e` para manejo de errores
- Incluye comentarios en español e inglés
- Sigue las convenciones de estilo existentes
- Prueba tus cambios antes de enviar el PR

## Lanzamiento de Versiones

Las versiones siguen [Semantic Versioning](https://semver.org/):
- **MAJOR**: cambios incompatibles hacia atrás
- **MINOR**: nuevas funcionalidades compatibles
- **PATCH**: correcciones de errores compatibles

## Licencia

Todas las contribuciones estarán bajo la licencia MIT del proyecto.

## Contacto

Para preguntas o discusiones:
- Abre un issue en GitHub
- Contacta al equipo de Agent Zero

---

¡Gracias por contribuir! 🎉
