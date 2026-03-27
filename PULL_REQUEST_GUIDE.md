# 📝 Guía de Pull Request - WhatsApp Automation Plugin

## 🎯 Resumen
Este plugin proporciona automatización completa de WhatsApp Web con sesiones persistentes en Chrome headless para Agent Zero.

## 📋 Estructura de Archivos

### 1. Repositorio del Plugin (GitHub)
```
whatsapp_automation/
├── plugin.yaml           # Metadatos del plugin
├── README.md             # Documentación completa
├── CONTRIBUTING.md        # Guía de contribuciones
├── PULL_REQUEST_GUIDE.md # Este archivo
└── scripts/
    ├── install.sh                   # Script de instalación
    ├── start_whatsapp_persistent.sh  # Iniciar Chrome persistente
    ├── check_persistence.sh          # Verificar persistencia
    └── monitor_chrome.sh            # Monitorear Chrome
```

### 2. Directorio para PR a a0-plugins
```
a0-plugins-submit/
└── plugins/
    └── whatsapp_automation/
        └── index.yaml    # Metadatos para el índice
```

## ✅ Verificación de Especificaciones

### Cumplimiento de Requisitos a0-plugins:
- ✅ Nombre del plugin coincide entre carpeta y plugin.yaml: `whatsapp_automation`
- ✅ Título: "WhatsApp Automation" (20 caracteres, máximo 50)
- ✅ Descripción: clara y concisa (menos de 500 caracteres)
- ✅ GitHub URL: apunta al repositorio del plugin
- ✅ Tags: 5 etiquetas (máximo 5)
- ✅ index.yaml: 592 bytes (máximo 2000)
- ✅ Solo un plugin por PR

### Contenido del index.yaml:
```yaml
title: "WhatsApp Automation"
description: "Automatización completa de WhatsApp Web con sesiones persistentes en Chrome headless. Permite enviar mensajes, leer conversaciones y monitorear chats sin necesidad de escanear QR cada vez."
github: "https://github.com/agent0ai/whatsapp-automation"
tags:
  - whatsapp
  - automation
  - chrome
  - headless
  - persistence
```

## 🚀 Pasos para el Pull Request

### Paso 1: Crear el Repositorio del Plugin

1. Crear un nuevo repositorio en GitHub: `https://github.com/agent0ai/whatsapp-automation`
2. Subir todos los archivos del plugin:
   ```bash
   cd /a0/usr/workdir/whatsapp_automation_plugin/
   git init
   git add .
   git commit -m "Initial commit: WhatsApp Automation Plugin v1.0.0"
   git branch -M main
   git remote add origin https://github.com/agent0ai/whatsapp-automation.git
   git push -u origin main
   ```

### Paso 2: Fork del Repositorio a0-plugins

1. Ir a: https://github.com/agent0ai/a0-plugins
2. Hacer fork del repositorio

### Paso 3: Crear Estructura del PR

1. Clonar tu fork de a0-plugins:
   ```bash
   git clone https://github.com/TU_USUARIO/a0-plugins.git
   cd a0-plugins
   ```

2. Crear la estructura del plugin:
   ```bash
   mkdir -p plugins/whatsapp_automation
   cp /a0/usr/workdir/a0-plugins-submit/plugins/whatsapp_automation/index.yaml plugins/whatsapp_automation/
   ```

3. Verificar contenido:
   ```bash
   cat plugins/whatsapp_automation/index.yaml
   ```

### Paso 4: Commit y Push

```bash
git add plugins/whatsapp_automation/
git commit -m "Add WhatsApp Automation plugin"
git push origin main
```

### Paso 5: Crear Pull Request

1. Ir a: https://github.com/agent0ai/a0-plugins
2. Hacer click en "Pull Requests"
3. Hacer click en "New Pull Request"
4. Seleccionar tu fork y rama
5. Título del PR: `Add WhatsApp Automation Plugin`
6. Descripción:
   ```markdown
   ## Descripción
   
   Este plugin proporciona automatización completa de WhatsApp Web con sesiones persistentes en Chrome headless para Agent Zero.
   
   ## Características
   
   - Sesión persistente de WhatsApp Web (survive reinicios)
   - Compatible con contenedores Docker
   - Chrome headless sin interfaz gráfica
   - Scripts de instalación y mantenimiento
   - Integración con Chrome DevTools MCP
   
   ## Documentación
   
   - README.md con documentación completa
   - Scripts de automatización en /scripts/
   - Ejemplos de uso con Agent Zero
   - Troubleshooting detallado
   
   ## Validación
   
   - ✅ Nombre del plugin coincide: whatsapp_automation
   - ✅ Título < 50 caracteres
   - ✅ Descripción < 500 caracteres
   - ✅ GitHub URL válida
   - ✅ 5 tags (máximo permitido)
   - ✅ index.yaml < 2000 caracteres
   
   ## Enlaces
   
   - Repositorio del plugin: https://github.com/agent0ai/whatsapp-automation
   ```

7. Hacer click en "Create Pull Request"

## 🔍 Validación Automática

El CI de a0-plugins verificará automáticamente:
- Estructura de carpetas correcta
- Nombre del plugin coincide con plugin.yaml
- Campos requeridos presentes en index.yaml
- Límites de longitud cumplidos
- GitHub URL válida

## 📝 Revisión Humana

Después de pasar la validación automática, el PR será revisado por un maintainer de Agent Zero.

## ✨ Resultado Esperado

Si el PR es aprobado:
- El plugin aparecerá en el índice de a0-plugins
- Los usuarios podrán instalarlo fácilmente
- La comunidad de Agent Zero tendrá acceso a la automatización de WhatsApp

---

**¡Gracias por contribuir a la comunidad de Agent Zero! 🎉**
